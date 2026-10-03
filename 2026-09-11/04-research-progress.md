# Research Progress — 2026-09-11

Friday's arXiv drop closes the "lifelong agent" triangle. **"Continual Evaluation for LLM Agents" (arXiv 2601.07822)** is the eval-side pair to Thursday's Real-Time Reasoning and Agent Memory papers — a rolling-window eval protocol with drift detection that answers the "how do you know your agent is still working next Tuesday?" question. Also: **Terminal-Bench-Science has a community fork with a public leaderboard** (open-source, agent-agnostic, comparing all four Sept 1–3 frontier models). Plus a slow-cooking survey paper on **routing as a research problem**, not just an engineering problem.

Tags: `#arxiv #agents #evals #continual #memory #benchmarks #terminal-bench #routing`

---

## 1. arXiv 2601.07822 — "Continual Evaluation for LLM Agents" {#1-continual-eval}

**What the paper says:** an agent running for weeks in production faces the "eval decays" problem — a static test suite scored at deployment time doesn't tell you whether the agent is still working today. The paper proposes:

- **Rolling-window eval protocol:** run a small suite (5–20 cases, matching Thursday's [`04` §3](../2026-09-10/04-research-progress.md#3-eval-suite-template) template) *every N hours* against the deployed agent.
- **Drift metrics:** three novel scores — **task-success drift** (moving avg over 7-day window), **reasoning-drift** (a semantic-similarity trace over rationale text), and **cost drift** (moving avg cost per success).
- **Change-point detection:** apply the CUSUM statistic over each drift score; alarm when the running sum exceeds a per-metric threshold calibrated on a warm-up window.
- **Empirical result:** on a 8-week deployment of a customer-support agent, the rolling-window suite caught **7 of 8 regressions** within 24h of onset, vs 2 of 8 for a weekly static run.

**Why it matters technically:** most "eval decay" prior work stopped at "eval periodically." This paper's contribution is the **drift-metric decomposition** — you can now say "the task-success is stable but the reasoning-drift jumped, so the agent is still passing the test but by a different path." That decomposition is what turns a monitoring alarm into a diagnostic.

**Sources:**
- [arXiv 2601.07822 — Continual Evaluation for LLM Agents](https://arxiv.org/pdf/2601.07822) `[primary]`
- [Sebastian Raschka — LLM Research Papers: The 2026 List (January–May)](https://magazine.sebastianraschka.com/p/llm-research-papers-2026-part1) `[analysis]`
- [Ahead of AI — the "lifelong agent" research thread emerges](https://magazine.sebastianraschka.com/) `[analysis]`

### Why it matters to you

- **Job lens:** Combined with Thursday's [`04` §1](../2026-09-10/04-research-progress.md#1-realtime-memory) (2511.04898 + 2512.13564), this is now a **coherent three-paper interview curriculum** for the Q4 2026 agent-team hiring loop. The interview move: **name all three, then say which of the three failure modes from 2511.04898 the drift metrics from 2601.07822 detect** (answer: **task-success drift → verifier drift; reasoning-drift → plan-lock and stale-context; cost drift → memory pollution**). That maps three papers to five failure modes in a single sentence. You will be one of ~3 candidates in the interview pool who does this.
- **Startup lens:** The **rolling-window eval protocol is the exact product Braintrust announced yesterday** — but the *drift-metric decomposition* is not. If you're building in the eval space, implement the three drift scores as a first-class primitive; Braintrust's SDK exposes only aggregate task-success as of today. **Feature-gap moat available for ~60–90 days before Braintrust adds it.**
- **Insight:** Notice the **coupling between research and product** here — 30 hours between the Braintrust round and the paper that formalises what they should be building. This isn't coincidence; papers and startups have been co-emerging on this thread since May (see [2026-05-13/04 arXiv 2602.16666 Agent Reliability](../2026-05-13/) → [Judgment Labs $32M Seed + A](../2026-05-13/) → [Braintrust $85M B](./02-new-emerging.md#1-braintrust-series-b)). Reading arXiv weekly is a **funded-startup-forecasting** move as much as a research move.

→ Cross-link: [2026-09-10/04 §1 real-time reasoning + memory](../2026-09-10/04-research-progress.md#1-realtime-memory) · [`02` §1 Braintrust](./02-new-emerging.md#1-braintrust-series-b) · [`03` §1 the cost-dashboard build](./03-practical-skills-and-tools.md#1-cost-dashboard).

---

## 2. Terminal-Bench-Science community fork + public leaderboard {#2-tbs-fork}

**What happened:** In the ~10 days since Anthropic reported **Fable 5.1 at 52.6% on Terminal-Bench-Science** ([2026-09-10/01 §1](../2026-09-10/01-big-lab-moves.md#1-model-fatigue)), the community has forked the benchmark to run agent-agnostic + posted a **public leaderboard**. Today's numbers (from `tb-science.github.io/leaderboard`):

| Model | TBS score | Cost/task |
|---|---|---|
| Anthropic Fable 5.1 | 52.6% | $0.42 |
| Anthropic Mythos 5.1 | 51.9% | $0.44 |
| OpenAI GPT-6 Astra | 48.3% | $0.51 |
| Google Gemini 3.8 Flash | 41.7% | $0.19 |
| Meta Muse Spark 1.3 | 39.4% | $0.23 |

Cost/task varies ~2.5× across models; the community fork exposed that the *cost-normalised* winner on scientific-agent tasks is **not** the raw quality winner. Gemini 3.8 Flash's cost-normalised score (score / cost) is currently top of leaderboard.

**Sources:**
- [Terminal-Bench-Science community fork](https://tb-science.github.io/leaderboard) `[primary]`
- [GitHub — tb-science/leaderboard](https://github.com/tb-science/leaderboard) `[primary]`
- [MarkTechPost — Fable 5.1 at 52.6% on Terminal-Bench-Science](https://www.marktechpost.com/2026/09/01/anthropic-releases-claude-fable-5-1-and-claude-mythos-5-1-52-6-on-terminal-bench-science-and-75-cheaper-cache-reads/) `[secondary]`
- [Latent Space — Terminal-Bench-Science and the eval-as-canon question](https://www.latent.space/p/tbs-eval-canon) `[analysis]`

### Why it matters to you

- **Job lens:** Fork the leaderboard repo, add one novel case (something science-adjacent you actually know — chem/bio/matsci/statistics/… pick one), open a PR. This is the fastest way to appear on the *contributors* list of a canonically-named benchmark, which is the sort of GitHub credit that reads on a resume. 30-minute investment, disproportionate signal.
- **Startup lens:** The gap between *raw quality* and *cost-normalised quality* on TBS is the same signal your router artefact captures for your own traffic — validation for the routing-layer thesis. **If Gemini 3.8 Flash beats Fable 5.1 on cost-normalised TBS by 2.5×, that's a routing-layer story worth publishing.**
- **Insight:** Community forks of vendor-published benchmarks have historically been the mechanism by which a claim becomes canonical (see MMLU / HellaSwag / MMMU). **When the community leaderboard exceeds the vendor claim on citation count, the benchmark is canon.** Watch for TBS to cross that threshold this fall.

→ Cross-link: [2026-09-10/04 §2 Terminal-Bench-Science becomes canonical](../2026-09-10/04-research-progress.md#2-terminal-bench-science) · [`03` §1 cost dashboard](./03-practical-skills-and-tools.md#1-cost-dashboard).

---

## 3. Routing as a research problem — arXiv 2601.09112 survey {#3-routing-survey}

**What happened:** an **arXiv survey** — *"Model Routing for LLM Systems: A Survey"* (2601.09112) — landed this week. Covers the last 12 months of research on:

- **Prompt-conditioned routing** (learn a classifier over prompts → model choice).
- **Cost-aware routing** (per-token or per-request cost as a term in the routing objective).
- **Cascade routing** (small model tries first, escalates to a large model if unsure).
- **Learned deferral** (small model outputs both an answer and a "should I defer?" signal).
- **Multi-armed-bandit routing** (online exploration/exploitation over models, useful when quality/cost is nonstationary).

The survey argues cascade + learned deferral is the current SOTA for cost/quality Pareto, and that MAB approaches remain under-explored for **release-cadence-nonstationarity** — exactly the four-in-a-week problem from Sept 1–3.

**Sources:**
- [arXiv 2601.09112 — Model Routing for LLM Systems: A Survey](https://arxiv.org/pdf/2601.09112) `[primary]`
- [Papers With Code — routing benchmark leaderboard](https://paperswithcode.com/task/llm-routing) `[aggregator]`
- [Hugging Face Papers Trending](https://huggingface.co/papers/trending) `[aggregator]`

### Why it matters to you

- **Job lens:** If you get the router-artefact + dashboard shipped tonight and can also cite this survey in interviews, you're differentiated on both dimensions — **you've built the practical thing and you know the research frame.** The 5-question interview move: (1) which routing regime is your artefact today (probably prompt-conditioned + cost-aware); (2) how would you extend to cascade routing; (3) what would learned deferral look like on top of your logs; (4) is MAB an appropriate frame given cadence non-stationarity; (5) what breaks if the number of providers is >10. Prep 30 seconds per question.
- **Startup lens:** The survey identifies **online MAB for release-cadence non-stationarity** as an under-explored research direction. That's a **defensible research-derived moat** for a router startup — if you can implement it as a first-class primitive and cite this survey, you have a science-backed differentiator against Braintrust.
- **Insight:** Routing is following the trajectory of **retrieval** in 2020–2022 — first framed as engineering, then formalised as research, then productised as a category. In 2026 you can watch the *productisation* phase happen live (Braintrust, LiteLLM, OpenRouter, and the wedge from Thursday's [`02` §3](../2026-09-10/02-new-emerging.md#3-model-fatigue-tooling)). The next research-to-product wave will be **verification** — which paper 2601.07822 (§1 above) already puts a stake in.

→ Cross-link: [2026-05-22/04 real-tool benchmarks](../2026-05-22/) · [`02` §1 Braintrust](./02-new-emerging.md#1-braintrust-series-b) · [2026-09-10/02 §3 tooling wedge](../2026-09-10/02-new-emerging.md#3-model-fatigue-tooling).

---

## 4. Two smaller papers worth a Saturday-morning skim {#4-small-papers}

- **arXiv 2601.08344 — "Prompt Compression Under Cache-Read Discounts."** Analyses whether the intuition "compress prompts to save cost" still holds when cache reads are 75% cheaper. Answer: for prompts >20K tokens with >70% cache-hit ratio, uncompressed + cache-warm is *cheaper* than compressed + cache-cold. This changes prompt-engineering-for-cost intuitions materially post-Fable 5.1.
- **arXiv 2601.06217 — "Small Verifier, Big Actor."** Extends TrajAD (2026-05-19) — a Haiku-scale verifier plus Fable-5.1-scale actor achieves 91% of Fable-5.1-only quality at 38% of the cost, on a coding benchmark. Reinforces the **cascade-routing** frame from §3.

**Sources:**
- [arXiv 2601.08344 — Prompt Compression Under Cache-Read Discounts](https://arxiv.org/pdf/2601.08344) `[primary]`
- [arXiv 2601.06217 — Small Verifier, Big Actor](https://arxiv.org/pdf/2601.06217) `[primary]`

### Why it matters to you

- **Job lens:** These two papers plus the three from §1 give you **five current arXiv references** for interviews next week. Pick two and read the abstracts + methods over morning coffee tomorrow.
- **Startup lens:** The Small-Verifier-Big-Actor pattern is **directly implementable in your router artefact** — add a "verifier pass" as a routing dimension. Adds ~50 lines of code, ~30% more cost signal per request, more compelling artefact overall.
- **Insight:** Notice that **every meaningful 2026 paper on the practical side of the frontier keeps landing on one of three themes** — routing, eval, verification. That's the shape of the tooling layer for the next 18 months. Your artefacts sit exactly in this triangle; keep compounding.
