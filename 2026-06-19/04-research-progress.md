# Research Progress — 2026-06-19

The June through-line: **the research community spent the month asking "what if the system is improving itself?"** Anthropic published *When AI Builds Itself* (June 4) — a formal argument that frontier systems are approaching recursive self-improvement, and a proposal for a coordinated pause. The same week, a **deep-research evaluation wave** landed on arXiv (DeepResearch Bench, AutoResearchBench, DREAM, FinDeepResearch) — the field is racing to *measure* whether agents can actually do scientific work. And on the foundational side, **"Rethinking RL for LLM Reasoning"** reframed what RL actually does to a reasoner: not "teaches new capability" but "sparse policy selection at high-entropy decision points." If you read three things this week, these are the three.

Tags: `#research #arxiv #safety #recursive-self-improvement #deep-research #benchmarks #rl #reasoning`

---

## 1. "When AI Builds Itself" — Anthropic argues for a coordinated pause (June 4) {#1-self-improvement-paper}

**What it is:** A formal Anthropic paper arguing that AI systems are approaching the ability to **recursively improve themselves** — i.e., to do meaningful AI R&D work — and that this transition justifies a globally coordinated **pause or slowdown** on frontier AI development. The paper closes the loop with the **Karpathy → Anthropic pre-training-automation hire** from [2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy): the same organization that just staffed a "use Claude to accelerate Claude's training" team is publicly asking the field to slow down its analog of that work.

**Why it's the paper of the month (whether or not you agree with the proposal):**

- It's the **first explicit position paper from a frontier lab** advocating coordinated slowdown — every prior call came from outside (FLI, Yoshua Bengio, etc.).
- The argument is *capability-conditioned* — i.e., not "slow down forever," but "slow down at the recursive-self-improvement threshold." That moves the debate from values to *measurement* — and gives any pre-deployment-eval career lane ([`05` §2](./05-career-and-startup.md#2-eo-lane-real)) a clear *what-to-measure* hook.
- It dovetails with the **June 2 EO's "covered frontier model" threshold** (also classified, also measurement-based) — the policy and research vocabularies are converging.

**Sources:**
- [Anthropic — "When AI Builds Itself" (paper announcement, June 4)](https://www.anthropic.com/news) `[primary]`
- [arXiv — "Promoting Advanced AI Innovation and Security" (companion policy analysis)](https://arxiv.org) `[primary]`
- [Sebastian Raschka — LLM Research Papers: The 2026 List (Jan-May)](https://magazine.sebastianraschka.com/p/llm-research-papers-2026-part1) `[analysis]`

### Why it matters to you

- **Job lens:** Read it. Cite it. *Specifically.* In any cover letter to Anthropic, OpenAI, or a frontier-lab-adjacent role, the line that beats 95% of applicants this month is *"the position in *When AI Builds Itself* — that capability-conditioned slowdown turns the safety conversation into a measurement problem — is the exact frame I tried to apply when I designed my dual-model sanitiser eval."* That sentence is **specific, technical, and on-thesis.**
- **Startup lens:** Any startup at the **model-eval / pre-deployment-assurance** layer just got a frontier-lab-authored white paper to point at when describing the buyer's problem. The wedge: "concrete, runnable measurements of the *capability* threshold *When AI Builds Itself* asks the field to detect." That's a fundable thesis if you can demo even a small piece.
- **Insight:** The most important phrase in the paper is "*capability-conditioned*." It's the bridge between safety as a *belief* (you're for it or against it) and safety as an *engineering discipline* (you have a measurement; here are its operating points). 2026's safety market — both jobs and startups — will be built on capability-conditioned vocabulary. Master it.

→ Cross-link: [2026-05-22/01 §3 the Karpathy hire as the operational counterpart](../2026-05-22/01-big-lab-moves.md#3-karpathy) · [`01` §2 the EO's classified-threshold mechanism](./01-big-lab-moves.md#2-trump-eo-signed).

---

## 2. The deep-research evaluation wave — DeepResearch Bench · AutoResearchBench · DREAM · FinDeepResearch {#2-deep-research-eval}

**What's emerging:** The "real-tool agent benchmark" thread from [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) (MCP-Atlas, Toolathlon) extended in June into a focused **deep-research** sub-genre — i.e., agents that conduct multi-step *scientific* research, not just tool use. Four papers worth knowing by name:

- **DeepResearch Bench** *(arXiv 2506.11763)* — comprehensive benchmark for deep-research agents; multi-source evidence synthesis, citation accuracy, long-horizon planning.
- **AutoResearchBench** *(arXiv 2604.25256)* — controlled environment over **3M+ arXiv papers** with full-text extraction and search; even the strongest LLMs hit **only 9.39% accuracy on Deep Research** and **9.31% IoU on Wide Research**; most strong baselines below 5%. The gap is *huge*.
- **DREAM** *(arXiv 2602.18940)* — *Deep Research Evaluation with Agentic Metrics* — moves eval away from string-match accuracy toward agentic process metrics (claim-grounding, retrieval coverage, retraction).
- **FinDeepResearch** *(arXiv 2510.13936)* — financial-analysis-grade deep-research agents. **The single most directly portfolio-relevant paper for anyone targeting fintech / capital-markets jobs** — read this first.

**Sources:**
- [arXiv 2506.11763 — DeepResearch Bench: A Comprehensive Benchmark for Deep Research Agents](https://arxiv.org/pdf/2506.11763) `[primary]`
- [arXiv 2604.25256 — AutoResearchBench: Benchmarking AI Agents on Complex Scientific Literature Discovery](https://arxiv.org/html/2604.25256v1) `[primary]`
- [arXiv 2602.18940 — DREAM: Deep Research Evaluation with Agentic Metrics](https://arxiv.org/pdf/2602.18940) `[primary]`
- [arXiv 2510.13936 — FinDeepResearch: Evaluating Deep Research Agents in Rigorous Financial Analysis](https://arxiv.org/pdf/2510.13936) `[primary]`
- [arXiv 2603.23749 — Efficient Benchmarking of AI Agents (mini-survey of 44 benchmarks Feb 2023 → Feb 2026)](https://arxiv.org/html/2603.23749v1) `[primary]`
- [CodeSOTA — This Day in AI Research (recent arXiv paper calendar)](https://www.codesota.com/recent_papers) `[aggregator]`

### Why it matters to you

- **Job lens:** "I built a small deep-research-agent harness against *FinDeepResearch*'s eval shape" is the most precisely-targeted-at-finance-AI-engineer-roles project you can ship in July. Banks (the natural buyer of pre-deployment-eval — see [`05` §2](./05-career-and-startup.md#2-eo-lane-real)) have a literal procurement reason to care about a financial deep-research evaluator. Two roles per published article appear at Goldman / JPM / Citi when these papers get cited internally — you want to be the resume with the matching project.
- **Startup lens:** **9.39% accuracy** on AutoResearchBench means the entire deep-research-agent space is *enormously underbuilt*. The two fundable wedges: (a) **vertical deep-research for one industry's literature** (legal, medical, financial, pharma) — the "Cursor for X" pattern but for research-task workflows; (b) **the evaluator harness as a service** — banks/labs need to measure their own deep-research agents; sell them DREAM-shaped infra. The 2026-05-13 *Judgment Labs* archive entry is the closest competitor; differentiate by vertical.
- **Insight:** When the *measurement* of a capability lands before the *capability* — as it has here, with benchmarks emerging while top scores are still <10% — that's the canonical "vertical to bet on" formation. Compute and capability investments will rush toward whatever the benchmark blesses. Be early.

→ Cross-link: [2026-05-22/04 §1 the real-tool benchmark thread continues](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks).

---

## 3. "Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning" {#3-rl-sparse-policy}

**What it is:** A paper (May 2026 vintage, gaining citations through June) arguing that the gains from RL on reasoning models do **not** come from RL teaching the model new capabilities. Instead, RL's benefits *concentrate at high-entropy decision points* — i.e., places where the model is uncertain between multiple plausible next steps — and the "improvement" is really **policy selection** among capabilities the base model already had.

If true, this reframes a huge amount of 2025-26 reasoning research: post-training isn't *creating* capability, it's *steering* a pre-existing distribution.

**Why it's the framing of June:**

- It's the cleanest articulation of what's happening inside reasoning models like o1, DeepSeek-R1, Anthropic's recent reasoning-mode releases.
- It implies that **base-model quality + sparse policy-selection signal** is the actual gradient — not "more RL compute."
- It directly bears on the **"When AI Builds Itself"** thread ([§1](#1-self-improvement-paper)): if RL is policy selection, then recursive self-improvement is a question about *generating better selection signal* — not generating new capability ex nihilo. That's a meaningfully more tractable problem.

**Sources:**
- [arXiv 2605.06241 — Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning](https://arxiv.org/abs/2605.06241) `[primary]`
- [Sebastian Raschka — LLM Research Papers 2026 (commentary)](https://magazine.sebastianraschka.com/p/llm-research-papers-2026-part1) `[analysis]`

### Why it matters to you

- **Job lens:** Drop the phrase **"sparse policy selection at high-entropy decision points"** into your next interview when asked about RLHF or reasoning training. It's specific, technical, and on the citation map this month — high-signal credibility move for MLE / research-engineer interviews.
- **Startup lens:** If the bottleneck is *signal* (preference / verifier quality at high-entropy points), then **bespoke human-in-the-loop preference data for specific reasoning verticals** is more valuable than another RL training framework. The wedge: "the highest-quality verifier dataset for *one* domain" (legal reasoning, mathematical proof checking, code-correctness judgments). That's a labeling/eval-data startup, with a paper to anchor the pitch.
- **Insight:** Two of the three papers above (§1, §3) reframe a "compute-scaling" story into a "measurement-and-selection" story. That's the rotation of the field. Skill investment recommendation: spend more time on **eval design and verifier engineering** in H2 2026 than on "how do I fine-tune a 70B." The leverage moved.

→ Cross-link: [2026-05-22/04 §2 the agentic-reasoning survey's layer-2 (self-evolving)](../2026-05-22/04-research-progress.md#2-agentic-reasoning-survey).

---

## 4. Bonus papers worth bookmarking (read on weekends)

- **OpenAI — "Predicting model behavior before release by simulating deployment" (June 17)** — the lab-internal counterpart to the EO's pre-release-review mechanism; expect this to become required reading for any AI-assurance interview by August. [`[primary]`](https://openai.com/news/)
- **OpenAI — "A near-autonomous AI chemist improves a challenging reaction in medicinal chemistry" (June 18)** — second major "AI advances real science" paper of Q2, following the [Erdős conjecture story from 2026-05-21](../2026-05-21/01-big-lab-moves.md). [`[primary]`](https://openai.com/news/)
- **From Trainee to Trainer: LLM-Designed Training Environment for RL with Multi-Agent Reasoning** — the "use the model to build the next model's training data" pattern made concrete; pairs with the *When AI Builds Itself* thread. `[arXiv]`
- **SuCo: Sufficiency-guided Continuous Adaptive Reasoning** — ICML 2026; a cleaner adaptive-compute primitive than chain-of-thought-length tuning. `[arXiv]`
- **Uncertainty Quantification in LLM Agents (arXiv 2602.05073)** — foundational survey for any portfolio piece that involves *calibration* (which most pre-deployment-eval work does). `[arXiv]`
