# Research Progress — 2026-07-27

Two arXiv threads worth a Monday-morning read, plus one buyer-side signal that matters more than any single paper. **AgentGym2 (2026-07-06)** is the first widely-cited "de-idealized" agent benchmark — top model pass-rate drops **~40 points** vs. prior benches, and this becomes the framing every "agents don't work yet in prod" conversation will use next quarter. **Kimi K3's tech blog** is more than a launch post — the **MoE-with-router-gating recipe** is documented at unusual depth for a Chinese-lab release; it's the paper-to-read for anyone thinking about hosting or fine-tuning open MoE. And a broad **LLM agent eval survey** from May consolidates the 2023 → 2026 benchmark landscape into 44 papers — the survey to cite before designing your own eval.

Tags: `#arxiv #agents #benchmarks #moe #kimi #survey #sim-to-real #evaluation`

---

## 1. AgentGym2 — LLM agents in de-idealized real-world environments (arXiv 2607.05174, 2026-07-06) {#1-agentgym2}

**What the paper claims:** Prior LLM-agent benchmarks (WebArena, ToolBench, AgentBench, SWE-bench) evaluate in **simplified, idealized settings** — pre-packaged tool interfaces, clean inputs, single-shot success criteria. **AgentGym2** strips those assumptions:

- **Noisy inputs** — user prompts that are underspecified, ambiguous, or partially wrong.
- **No pre-packaged tool interfaces** — agent must **discover** available tools, read raw API docs, handle deprecated endpoints, deal with rate limits and transient failures.
- **Multi-step failure environments** — a task requires 12–40+ tool calls in sequence; a single mid-run failure requires recovery, not restart.
- **Broader domain spread** — customer-service, DevOps, legal-research, procurement, product-analytics, developer-workflow, embedded-hardware, healthcare-triage.

**Headline result:** Top frontier model (unnamed in paper, community consensus: GPT-5.6 Sol) achieves **~28% pass rate** on AgentGym2, versus ~71% on prior idealized benches. That's a **~40-point sim-to-real gap.**

**Second-order finding:** The gap is **not uniform**. On tool-*discovery*-heavy tasks, closed models with tool-use RLHF (Claude Opus 5, GPT-5.6 Sol) do better; on *long-horizon-recovery* tasks, models with explicit planning + verification loops (Opus 5 `effort=high`, GPT-5.6 Sol with deliberation) do better. **No single model dominates all axes**, which is itself a hiring/portfolio insight — the routing question is empirical, not architectural.

**Sources:**
- [arXiv:2607.05174v1 — AgentGym2: Benchmarking Large Language Model Agents in De-Idealized Real-World Environments](https://arxiv.org/html/2607.05174v1) `[primary]`
- [Papers With Code — AgentGym2 (project + code)](https://paperswithcode.com/) `[primary]`
- [Hugging Face Papers (Trending)](https://huggingface.co/papers/trending) `[aggregator]`

### Why it matters to you

- **Job lens:** **AgentGym2 becomes the vocabulary** for the "why don't agents work in production yet" question at every applied AI interview this fall. Read the abstract + Section 4 (results); be able to quote the **~40-point sim-to-real gap** and one **specific failure mode** (tool-discovery-under-deprecation is the most quotable one). This is a **20-minute read that upgrades a whole class of interview answers.**
- **Startup lens:** If you're building an agent product, **run your own product's tasks against AgentGym2's evaluation harness** — it's open-source. Publishing "our agent scored X on AgentGym2 (vs. GPT-5.6 Sol's 28%)" is a credible objective performance claim for your seed deck. Do it in September when the community has settled on baselines.
- **Insight:** The sim-to-real gap on agents is what the **sim-to-real gap on self-driving** was in 2020: a **capability that looks close on benchmarks but is 3–5 years from broad production reliability.** The startup and career opportunity for the next 2 years is **closing this gap in one specific vertical** — the same shape as Waymo/Cruise in AV. Pick the vertical (see [`02` §2 the funded verticals list](./02-new-emerging.md#2-funding-roundup)) and go deep.

→ Cross-link: [`03` §1 use AgentGym2 tasks as your Kimi K3 smoke-test prompts](./03-practical-skills-and-tools.md#1-kimi-k3-run).

---

## 2. Kimi K3 tech blog — the sparse MoE recipe, documented in depth {#2-kimi-k3-recipe}

**What the blog covers:** Moonshot AI's tech blog for the K3 release is one of the more transparent frontier-model post-mortems of 2026. Concrete claims worth understanding as a builder:

- **Router-gating with expert-load balancing loss** — the specific loss term Moonshot uses to prevent "expert collapse" (where a small subset of experts absorb ~all traffic in production). This is the failure mode that killed most 2024–2025 open MoE deployments.
- **~8-of-256 expert activation per token** — sparser than most prior public MoEs (typically 2-of-N). More experts per token = less variance, less throughput; the trade Moonshot picked is closer to **quality over inference cost**.
- **Two-stage pretraining** — general-web corpus first, then a **10T-token "structured reasoning + tool-use" post-corpus** distilled from proprietary + partner data. This is the piece the community consensus attributes the closed-vs-open post-training gap to.
- **Native multimodal via early-fusion patches** — not a bolt-on vision adapter; image tokens interleave with text tokens through all layers. Similar to the Chameleon / Gemini 1.5 approach, unusual for an open release.
- **Context extension to 1M via YaRN + attention-sink** — the same recipe now used by Sonnet 5, Opus 5, and Gemini 3.6 Flash. Confirms the recipe is stable enough to be the default.

**What's missing (worth flagging):** The blog is silent on **safety post-training + red-team methodology**, which is exactly the domain the [FLI Summer 2026 Safety Index](./01-big-lab-moves.md#4-fli-safety-index) called out as under-documented for Chinese labs.

**Sources:**
- [Moonshot AI — Kimi K3 Tech Blog: Open Frontier Intelligence](https://www.kimi.com/blog/kimi-k3) `[primary]`
- [Nathan Lambert — Kimi K3: The open-weights escalation (Interconnects)](https://www.interconnects.ai/p/kimi-k3-the-open-weights-escalation) `[analysis]`
- [Eigent — Kimi K3: Moonshot AI's 2.8T Open-Weight Model](https://www.eigent.ai/blog/kimi-k3-open-weight-frontier-model) `[analysis]`

### Why it matters to you

- **Job lens:** MoE-router-gating and expert-load-balance are the **top interview questions at any inference-team hire in 2026** — Together AI, Fireworks, Groq, Anthropic Systems, OpenAI Inference. The Kimi blog is the freshest, most concrete reference. Read it before any inference-adjacent interview.
- **Startup lens:** If you're founding in **fine-tune-as-a-service** or **domain-specialized model** territory, the Kimi K3 recipe is a **fine-tuning target you can actually adapt** — unlike Opus 5 or Gemini which are closed. The wedge: **"we fine-tune Kimi K3 on your data, host on Together AI, price 30% below Opus 5 on your workload, comparable quality."** This isn't hypothetical anymore.
- **Insight:** **Chinese frontier labs are now shipping recipes at DeepMind-level transparency.** The information advantage US labs had circa 2023 — closed training recipes vs. open Chinese ones — has flipped. The competitive gap between US frontier and Chinese frontier will be defined by **post-training + safety RLHF + eval infrastructure**, not pre-training know-how, going forward. Your career should orient toward the parts of the stack where the US still has the moat.

→ Cross-link: [`01` §1 Kimi K3 release story](./01-big-lab-moves.md#1-kimi-k3) · [`03` §1 the smoke test to run tonight](./03-practical-skills-and-tools.md#1-kimi-k3-run).

---

## 3. Evaluation and Benchmarking of LLM Agents: A Survey (arXiv 2507.21504) {#3-eval-survey}

**What the paper covers:** A **44-paper systematic review** of LLM-agent benchmarks published **February 2023 → February 2026**. Structured by:

- **Domain** (web navigation, code repair, scientific research, customer service, embodied, etc.)
- **Modality** (text-only, multimodal, tool-augmented)
- **Success metric** (task completion, human eval, verifier-model eval, learned reward)
- **Failure taxonomy** (which failure modes each benchmark actually exercises)

**Key finding for a builder:** Most 2023–2024 benchmarks measure **task completion under idealized conditions**; most 2025–2026 benchmarks are **shifting toward failure-mode-aware evaluation** — matching the [AgentGym2 direction](#1-agentgym2). The paper argues the next wave of benchmarks (2026–2027) will be **VLM/multimodal-agent-native** rather than text-only-agent-with-image-adapter.

**Practical use of the survey:** if you're designing your own eval for a portfolio project or startup, **cite this survey**, **pick 2–3 benchmarks from the taxonomy that match your product's failure modes**, and **skip the ones that don't**. Building your own eval from scratch in 2026 is a red flag; adapting from the standard taxonomy is signal of research maturity.

**Sources:**
- [arXiv:2507.21504 — Evaluation and Benchmarking of LLM Agents: A Survey](https://arxiv.org/pdf/2507.21504) `[primary]`
- [Semantic Scholar — related-work graph](https://www.semanticscholar.org/) `[aggregator]`

### Why it matters to you

- **Job lens:** For any research-adjacent interview (Fellows, Applied Research, ML Research Engineer), **"I read the standard eval survey and I chose X because Y"** is a stronger answer than "I built an eval from scratch." Signals research literacy.
- **Startup lens:** In a pitch deck, **cited-benchmark eval > hand-rolled eval** — investors have been burned by too many "we made up our own eval and we're SOTA on it" claims. Use the taxonomy.
- **Insight:** The **eval survey landscape is the map of where the field is honest with itself.** If you want to know which agent-capability claim to trust, read the eval papers *first* and the model claims *second*. That's how research-mature engineers screen the news.

---

## 4. Watchlist — papers to read next {#4-watchlist}

Not deep-diving these yet; on the radar for future editions:

- **Terminal-bench** — command-line agents, harder than SWE-bench for tool-use realism. Preprint circulating; expect arXiv posting in August.
- **Dsgym** — data-science-agent evaluation & training. Same authors as WebArena; strong pedigree.
- **AgentBench 3** — the incumbent benchmark responds to AgentGym2; likely September preprint.
- **MANTRA (arXiv 2605.06334)** — SMT-validated compliance benchmarks for tool-using LLM agents; the *formal-verification-meets-agent-eval* angle for the [EU compliance conversation](./02-new-emerging.md#3-eu-omnibus).
- **Uncertainty Quantification in LLM Agents (arXiv 2602.05073)** — the theory paper that gives you a defensible way to answer "how confident is my agent" in a customer conversation.

**Sources:**
- [arXiv cs.AI daily](https://arxiv.org/list/cs.AI/current) `[primary]`
- [arXiv cs.LG recent](https://arxiv.org/list/cs.LG/recent) `[primary]`
- [Hugging Face Papers (Trending)](https://huggingface.co/papers/trending) `[aggregator]`
- [alphaXiv](https://www.alphaxiv.org/) `[aggregator]`
- [Papers With Code](https://paperswithcode.com/) `[aggregator]`
