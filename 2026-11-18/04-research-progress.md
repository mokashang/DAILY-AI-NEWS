# Research Progress — 2026-11-18

Three research threads from this week converge: (1) **OpenAI's "High self-improvement" Preparedness rating** on GPT-6.2 Astra is the first formal release at that capability threshold — a watershed for the entire RSP/RSP-equivalent policy infrastructure; (2) **memory + eval as the agent bottleneck** continues (MEMOIR Nov 5, +11.9 pp on LoCoMo QA); (3) **planner/worker routing as a research pattern** — Google's Orchestrator is the second lab to productize the pattern and is forcing a rethink of "single-model" eval harnesses. Plus a note on **IHL-eval research as a new academic lane** following this week's Vals-AI-style red-team disclosures. All arXiv IDs below should be verified on arxiv.org before citing.

Tags: `#research #arxiv #preparedness #memory #agents #ihl`

---

## 1. OpenAI's "High on AI self-improvement" Preparedness threshold — crossed for the first time {#1-openai-high-self-improve}

**What happened:**
- **GPT-6.2 Astra** (released Nov 17) is **OpenAI's first model externally released at the "High" Preparedness threshold for AI self-improvement**, per the Preparedness Framework.
- Astra also ships at **Critical on cybersecurity** and **High on biological + chemical** — all three tracked capability categories in the current PF version.
- OpenAI says it added "protections and tighter restrictions on dual-use requests" before release; the deployment card details are to be published alongside the model.
- The Preparedness Framework itself is the public policy document OpenAI uses to decide whether to ship — the framework says High-threshold models require additional safeguards, but *does not* automatically block deployment. Astra is the first test case of that threshold being crossed and then shipped.

**Sources:**
- [OpenAI — Preparedness Framework (original policy)](https://openai.com/safety/preparedness) `[primary]`
- [Unite.AI — Astra is OpenAI's first model released externally with High rating for AI self-improvement](https://www.unite.ai/?p=515159) `[secondary]`
- [UltraThink — OpenAI prints API prices, not a full scorecard (card gap analysis)](https://ultrathink.ai/news/openai-releases-gpt-6-2-astra-and-sol) `[analysis]`
- [DataCamp — GPT-6.2 Astra + Sol features + benchmarks](https://www.datacamp.com/blog/gpt-6-2-astra-and-sol) `[aggregator]`

### Why it matters to you

- **Research lens:** This is a **policy-operationalization datapoint** more than a capability datapoint. The empirical question going forward: **what evidence does a lab produce to justify "we crossed High on self-improvement but shipped anyway"?** If OpenAI publishes a thorough deployment card showing concrete mitigations (sandboxing, rate limits, dual-use refusal classifiers), this is the template. If it's a one-paragraph disclosure, the Preparedness Framework fails its first test.
- **Startup lens:** **The self-improvement threshold is the precise capability enterprise security teams will ask about in RFPs starting this quarter.** If you sell AI-agent infra (routing, sandboxing, policy engines, eval harnesses), add a **"self-improvement capability threshold" column** to your comparison matrix — it's the single most important enterprise-procurement question for Q4.
- **Insight:** "High" is not "Critical" in the Preparedness Framework hierarchy. OpenAI's framework reserves Critical for shipping-gating levels (and Astra ships at Critical on cyber). **The fact that OpenAI is willing to ship at High on self-improvement but not at Critical on self-improvement is the policy dial you should actually be tracking** — not whether the next model crosses High or not.

→ Cross-link: [`01` §4 — Astra + Sol deployment](./01-big-lab-moves.md#4-openai-gpt62-astra-sol)

---

## 2. MEMOIR + the "memory-eval-is-the-bottleneck" thread continues {#2-memoir}

**What happened:**
- **MEMOIR** (reported arXiv submission Nov 5, 2026) introduces a **training-free memory lifecycle for long-horizon LLM agents** — raises **evidence recall by 11.92 pp** over cosine-similarity baselines on the **LoCoMo QA** benchmark.
- Pairs with last week's cluster (Decision Context, SLATE, Knowing When to Intervene, Multi-Agent Judgment Aggregation) — all five converge on: **eval + memory is the bottleneck, not raw model capability**.
- Companion survey: **"Memory for Autonomous LLM Agents: Mechanisms, Evaluation, and Emerging Frontiers"** (arXiv 2603.07670) is the standard reference text for this literature.
- Open research questions: (a) does training-free memory scale past 10K-turn sessions; (b) does the LoCoMo QA benchmark transfer to real enterprise workloads; (c) where does memory stop and retrieval begin, operationally.

**Sources:**
- [Emergent.sh — MEMOIR lifts LLM agent recall +11.9 pp on LoCoMo](https://emergent.sh/news/memoir-lifts-llm-agent-recall-11-9pp-locomo) `[aggregator]`
- [arXiv — Memory for Autonomous LLM Agents survey (2603.07670)](https://arxiv.org/pdf/2603.07670) `[primary]`
- [arXiv — Evaluating Memory Structure in LLM Agents (2602.11243)](https://alphaxiv.org/abs/2602.11243) `[primary]`
- [OpenTrain — EvoArena memory-evolution benchmark](https://www.opentrain.ai/papers/evoarena-tracking-memory-evolution-for-robust-llm-agents-in-dynamic-environments--arxiv-2606.13681/) `[aggregator]`

### Why it matters to you

- **Research lens:** Memory-as-a-service is now a crowded academic lane. The marginal paper needs: (a) a **non-LoCoMo eval** to survive peer review, (b) a **production-workload citation**, (c) a **comparison to retrieval baselines** that isn't cosine-similarity-only. If you're writing a thesis or research paper, pick a benchmark that is *not* LoCoMo.
- **Job lens:** The practical takeaway for an MLE hiring pipeline: **"agent memory engineer"** is a durable job family at every lab + every agent-infra startup. If you can ship a working MEMOIR-like pipeline against your own agent, that's a staff-level portfolio artifact.
- **Insight:** The convergence of 5+ independent papers on "eval + memory beats capability" is the strongest **"vibe shift"** in agent research all year. Expect the **Q1 2027 arXiv wave to focus on production-grade memory lifecycles**, not raw capability jumps.

→ Cross-link: back to [2026-11-17/04](../2026-11-17/04-research-progress.md)

---

## 3. Planner/worker routing emerges as a research pattern (Antigravity Orchestrator formalizes it) {#3-planner-worker}

**What happened:**
- **Google's Antigravity Orchestrator (Nov 12)** operationalizes the pattern: **Carbon plans → Hydrogen executes → Carbon repairs the plan on executor failure**.
- Anthropic's internal Claude Code orchestrator uses a similar plan-execute split but has not published formal benchmarks.
- Research adjacent: **ReAct** (2022) is the ancestor; **Plan-and-Solve** (2023) and **AutoGPT/BabyAGI** (2023) are earlier full-loop variants; **ToolLLM / Reflexion** sit on the "repair" side.
- The formal research question MEMOIR + Orchestrator are opening together: **when should a planner re-plan vs. retry vs. escalate?** (This is a meta-eval question — "did the planner correctly diagnose the executor's failure").
- Expect ≥3 arXiv papers on this in the 2612 batch, especially on "when-to-replan" classifiers.

**Sources:**
- [Google Antigravity — Gemini 4 Hydrogen blog (Orchestrator)](https://antigravity.google/blog/gemini-4-hydrogen-in-google-antigravity) `[primary]`
- [Apidog — How Carbon plans + Hydrogen executes](https://apidog.com/blog/gemini-4-hydrogen-orchestrator/) `[analysis]`
- [arXiv — ReAct: Synergizing Reasoning + Acting (Yao et al., 2022)](https://arxiv.org/abs/2210.03629) `[primary]`

### Why it matters to you

- **Research lens:** **"When to re-plan" is the single most under-published open question in agent research.** If you are writing a thesis in agents, this is a 6-month lane with low competition. Benchmarks you can standardize on: Terminal-Bench 4.x, SWE-bench Verified, RLI.
- **Job lens:** See `03 §4` for the one-day portfolio artifact. "Router engineer" + "when-to-replan classifier" are both durable hiring categories.
- **Insight:** Google's **24% quota savings + 19% latency reduction** are the empirical floor. If your own implementation can beat those numbers on a domain-specific benchmark (your repo, your enterprise task suite), **that's a publishable result** and also a direct job-pipeline artifact.

→ Cross-link: [`02` §1 — Gemini 4 Hydrogen + Orchestrator](./02-new-emerging.md#1-gemini-4-hydrogen) · [`03` §4 — Turn on Orchestrator](./03-practical-skills-and-tools.md#4-turn-on-orchestrator)

---

## 4. IHL-eval as a new research lane (post-Vals + Frontier Red Team) {#4-ihl-eval-lane}

**What happened:**
- This week's Vals-AI-style investigation (medics / journalists / surrendering-soldier targeting) + Anthropic's **Sept 2026 Frontier Red Team targeting eval** + the Georgia-Tech-et-al **nuclear war-games 95% deployment** result together formalize a research lane: **IHL-compliant model evaluation**.
- Methodology questions: how do you simulate a battlefield-targeting workflow in a safe testbed; how do you score "would a model surrender-target" as an eval metric; how do you prevent dual-use leakage of the eval dataset itself.
- Policy context: the NY RAISE Act (Jan 1, 2027 compliance) does not yet mandate IHL eval but is widely expected to add it; EU AI Act Article 51 does cover military-adjacent categories.

**Sources:**
- [Anthropic Frontier Red Team — Intelligence Targeting / Conventional Weapons Capabilities](https://anthropic.com/research/intelligence-targeting-conventional-weapons-capabilities) `[primary]`
- [OpinioJuris — AI-Enabled Targeting, Model Evaluation + IHL](https://opiniojuris.org/2026/08/17/testing-the-limits-ai-enabled-targeting-model-evaluation-and-international-humanitarian-law/) `[analysis]`
- [The Decoder — Anthropic/OpenAI/Google models marked medics/journalists/surrender targets](https://the-decoder.com/anthropic-openai-and-google-models-readily-marked-medics-journalists-and-surrendering-soldiers-as-kamikaze-drone-targets/) `[secondary]`
- [Privacy International — When Algorithms Go to War (PAX report)](https://privacyinternational.org/sites/default/files/2026-06/PAX%20PI%20report%20when%20algorithms%20go%20to%20war%202026.pdf) `[analysis]`

### Why it matters to you

- **Research lens:** This is an **interdisciplinary lane with low technical competition** — most ML researchers don't know IHL, most lawyers don't know eval methodology. If you can co-author with a law/policy student, you have a 12-month publishing window before the frontier labs saturate the lane with internal papers.
- **Job lens:** **UK AISI, US CAISI (if it survives administration shifts), Anthropic Societal Impacts, OpenAI Policy Research**, and the GDM FSF teams all hire explicitly for this. Add a 1-page "IHL red-team case study" (even against an open-weight model, locally run) to your portfolio as a differentiator. For CS grad students with no law background, the fastest on-ramp is an **IHL summer intensive** (Red Cross, Harvard IHL summer, or free MOOCs).
- **Insight:** **"Can you measure whether a model would target a medic?"** is the single most concrete IHL-eval question — and is the single question every state AG, defense procurement officer, and compliance auditor will ask in 2027 RFPs. Build the eval; publish the eval; own the eval.

→ Cross-link: [`02` §2 — Humanitarian-targeting red-team evals](./02-new-emerging.md#2-humanitarian-targeting-redteam)
