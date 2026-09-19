# Research Progress — 2026-06-28

The Sunday research read is **SciAgentArena (arXiv 2606.12736, Jun 10)** — the cleanest answer yet to *"can a frontier agent do real science?"* — paired with this week's **distillation-attack disclosure** as an *empirical* research artifact (the largest documented natural experiment in adversarial query distribution against a frontier API ever assembled). Both speak to the same underlying shift: **the eval bar moved from synthetic benchmarks to real-world scientific tasks and real-world adversarial environments.**

Tags: `#research #arxiv #benchmarks #agents #science #adversarial #ai-for-science`

---

## 1. SciAgentArena — 200 real scientific tasks, stepwise verification, *agents are uneven* {#1-sciagentarena}

**What happened:** **arXiv:2606.12736** ("Benchmarking AI Agents for Addressing Scientific Challenges Across Scales," submitted Jun 10) ships **SciAgentArena**: ~200 real scientific tasks with **stepwise verification** and an **interactive, agent-agnostic environment**. Domain coverage is the most important part of the design:

- **Single-cell omics** (the dataset-handling pattern that defines modern computational biology)
- **Spatial omics** (the frontier of spatial-resolution gene expression)
- **Drug discovery** (small-molecule property prediction + screen design)
- **Electronic health records** (the dirtiest real-world tabular surface)
- **Genetics** (variant-calling, GWAS-adjacent workflows)

**The headline finding** is *not* "agents win" or "agents fail" — it's *unevenness*: agents can contribute effectively to **well-specified data-analysis workflows** when task structure + evaluation criteria are clear; they **struggle to generate novel insights, sustain self-directed exploration, and formulate robust solutions to open-ended research questions.** Tasks + data are public on Hugging Face.

**Sources:**
- [arXiv 2606.12736 — Benchmarking AI Agents for Addressing Scientific Challenges Across Scales](https://arxiv.org/abs/2606.12736) `[primary]`
- [arXiv HTML rendering](https://arxiv.org/html/2606.12736) `[primary]`
- [SciAgentArena project page](https://sciagentarena.github.io/) `[primary]`
- (Companion / adjacent) [arXiv 2603.29139 — SciVisAgentBench](https://arxiv.org/pdf/2603.29139) `[primary]` — scientific data analysis + visualization
- (Survey context) [arXiv 2506.11102 — Evolutionary Perspectives on Evaluation of LLM-Based AI Agents](https://arxiv.org/pdf/2506.11102) `[primary]`

### Why it matters to you

- **Job lens:** SciAgentArena is the **eval substrate** for the AI-for-science hiring lane that just got renamed *Jumper + Adler + Pritzel team* ([`01` §1](./01-big-lab-moves.md#1-adler-pritzel)). Read the paper end-to-end before any Anthropic, DeepMind, or Isomorphic interview — it is the most likely benchmark either side will reference. Vocabulary to lift verbatim: *stepwise verification, agent-agnostic environment, task-structure-conditional performance.* The Hugging Face dataset is the right thing to *show* during a coding interview.
- **Startup lens:** The "agents are uneven" finding is the wedge map. The domains where agents *can* contribute (well-specified data-analysis workflows) are the **defensible vertical-AI markets right now** — they're real but bounded; the founder edge is **building the eval infra + the task-specification layer** rather than another foundation-model wrapper. Concretely: a startup that ships **"SciAgentArena-for-your-vertical"** — same architecture (stepwise verification, agent-agnostic, real datasets), but for, say, *quantitative finance research workflows* or *legal discovery* or *materials science* — is a 6-month MVP with a buyer (the vertical's research org) and a defensible moat (the dataset + eval, not the model).
- **Insight:** This pairs cleanly with the [Agent² RL-Bench (arXiv 2604.10547)](../2026-06-06/04-research-progress.md#1-agent2-rl-bench) thread from earlier this month: **measurement infra is the lead indicator for capability** in 2026. The labs *first* build the eval, then ship the model that pegs it. SciAgentArena landing in June → expect a *next-generation* Mythos-class scientific model from Anthropic in Q3 (probably Sep–Oct, around the IPO roadshow). Plan portfolio + applications accordingly.

→ Cross-link: [`05` §1 the Adler/Pritzel signal](./05-career-and-startup.md#1-talent-signal) · [2026-06-06/04 §1 Agent² RL-Bench](../2026-06-06/04-research-progress.md#1-agent2-rl-bench) · [2026-06-17/04 §1 trace-eval survey](../2026-06-17/04-research-progress.md#1-externalization-survey).

---

## 2. The Alibaba disclosure as an empirical adversarial-query dataset {#2-alibaba-as-research}

**What happened:** [Anthropic's Senate letter on Alibaba](./01-big-lab-moves.md#2-alibaba-distillation) is — accidentally or otherwise — **the largest publicly-acknowledged empirical study of coordinated distillation behavior against a frontier API ever made public**. The numbers are research-grade:

- **28.8M exchanges** is several orders of magnitude larger than any existing red-team or adversarial-prompts dataset.
- **~25K fraudulent accounts** across a **45-day window (Apr 22 – Jun 5)** gives a clean **account-level temporal signal** — exactly what's needed to study coordination, evasion, and account-rotation tactics.
- The detection signal Anthropic disclosed (*high-volume, low-diversity prompts across coordinated accounts*) is itself an empirical, falsifiable hypothesis about adversarial-distillation behavior that **any academic group can now test against their own logs**.

What's missing publicly — and where the **research opportunity** sits — is the **labeled query-completion distribution** (Anthropic hasn't published the dataset). But the *summary statistics* alone are enough to back-of-envelope **how much capability transfer 28.8M Claude exchanges actually buys a Qwen-class student** — which is the empirical question every frontier-API lab is now urgently asking.

**Sources:**
- [Anthropic — official Newsroom](https://www.anthropic.com/news) `[primary]` (look for the Jun 24 abuse-disclosure statement)
- [CNBC — Anthropic accuses Alibaba…](https://www.cnbc.com/2026/06/24/anthropic-alibaba-distillation-campaign.html) `[secondary]`
- [Tom's Hardware — 25K accounts, 28.8M exchanges](https://www.tomshardware.com/tech-industry/artificial-intelligence/anthropic-claims-that-chinas-alibaba-illicitly-distilled-its-models-from-april-to-june-2026-says-effort-involved-25-000-fake-accounts-and-28-8-million-exchanges-on-claude) `[secondary]`
- (Adjacent earlier-2026) [arXiv 2603.16416 — A Survey on Evaluation of LLM-based Agents](https://arxiv.org/abs/2503.16416) `[primary]` — for the trace-evaluation framing this dataset *would* unlock

### Why it matters to you

- **Job lens:** The most cited recent gap in T&S / Detection JDs at Anthropic and OpenAI is *"experience reasoning about adversarial-coordination patterns in API-scale data."* You don't have access to the 28.8M dataset — but you can write a **short technical blog post** that takes the *summary statistics* and **back-of-envelope-estimates the distillation efficiency** (queries-per-bit-of-capability-transfer). That blog post becomes interview chum: it shows you can reason *quantitatively* about adversarial ML *without* needing access. Lean on the [TrajAD](../2026-05-19/04-research-progress.md) and [trace-eval survey](../2026-06-17/04-research-progress.md#1-externalization-survey) vocabulary.
- **Startup lens:** Anthropic publishing the summary numbers but not the labels is a **call for an open-source adversarial-distillation benchmark** — exactly the gap a small research startup could fill in 4–6 months. Build it on synthetic-but-realistic prompts (generate them yourself), label them with a small T&S taxonomy, ship under a research license. The lab that *needs* this most is whichever non-OpenAI/Anthropic frontier player gets distilled next (statistically, Mistral or Cohere) — and they'll buy.
- **Insight:** 2026's measurement-first pattern keeps holding. Last quarter the "real-tool" benchmarks (MCP-Atlas, Toolathlon) made the eval question concrete; this quarter SciAgentArena does it for science; the Alibaba dataset *will* do it for adversarial-distillation as soon as someone reconstructs even a synthetic version. **The frontier moves to whichever capability gets measured first.** Pick the measurement worth being early on.

→ Cross-link: [`02` §2 abuse-detection wedge](./02-new-emerging.md#2-abuse-detection-wedge) · [`05` §2 distillation-detection lane](./05-career-and-startup.md#2-distillation-detection-lane).
