# Research Progress — 2026-09-22

**Recursive self-improvement has become a research area.** The September arXiv wave takes the frame that was rhetorical in Amodei's pacing essay ([`01` §2](./01-big-lab-moves.md#2-amodei-pacing)) and turns it into economics, algorithms, and evaluation harnesses. In parallel, memory research went from "how much do we store" to "which controller decides what to remember, and can we interpret it?" — the [Interpretable Memory Decision Controller](https://github.com/zachysun/DailyArXiv/issues/565) paper (Sept 18) is the readable entry point. **The thread linking all of this to your work: eval design for evolving-environment agents is finally being papered up — cite it in interviews.**

Tags: `#arxiv #rsi #self-improvement #agents #memory #evaluation #interpretability`

---

## 1. The September RSI wave — four papers that changed the vocabulary {#1-rsi-papers}

**What happened:** Four papers landed on arXiv in the two weeks before Amodei's pacing essay ([`01` §2](./01-big-lab-moves.md#2-amodei-pacing)) that made **recursive self-improvement (RSI)** operational — not speculative. They map neatly onto Anthropic's disclosure that Claude leads 26% of the R&D producing the next Claude ([`01` §3](./01-big-lab-moves.md#3-claude-builds-claude)).

### 1a. The Economics of Recursive Self-Improvement (arXiv 2609.15802, Sept 14)

**What the paper says:** Tom Cunningham et al. model RSI as an economic system: **inputs** (compute, human-hours, prior model capability), **outputs** (next-generation model capability), **coupling coefficients** between them. Estimates the **elasticity of capability with respect to intra-loop AI labor** — i.e., when does adding another unit of "Claude-assisted-research" produce more capability than adding a human researcher? Finds an **inflection region** where the marginal-return curves cross, and argues the mainstream frontier labs are approaching that region *now.*

**Why this is the essay's spine:** Amodei's "we must pace the frontier" without a quantitative frame is a values statement. **This paper is the quantitative frame.** Any pacing policy that gets adopted will cite either this framework or a rewrite of it.

### 1b. Dream-RSI: Recursive Self-Improvement through Evolving Worlds (arXiv 2609.14858, Sept 14)

**What the paper says:** Combines the **evolving-environment agent** frame ([2026-09-10/04 §1](../2026-09-10/04-research-progress.md#1-realtime-memory)) with **RSI**. Trains an agent that improves itself by **generating harder versions of its own training environment** — the *dream* metaphor — and then re-training on them. Demonstrates capability lift on planning benchmarks without new human-labeled data.

**Why it matters:** Merges two research threads the community was tracking separately. The evolving-envs work said "the agent breaks when the world changes"; Dream-RSI says "the agent that *generates* the change can *stay ahead* of it." This is the shape of the next wave of agentic-training curricula.

### 1c. Self-Improvement via Fast Tree-Search (arXiv 2609.19526, Sept 17)

**What the paper says:** A **sample-efficient** self-improvement framework where the coding agent explores modifications of its own implementation via a tree-search over patches, evaluates each with a cheap verifier, and merges the best. Practical enough that the referenced repo runs on a single GPU.

**Why it matters:** The most-implementable of the four. If you want to prototype RSI-in-miniature (e.g., have Claude Code improve its own project scaffolding across N generations), this is the paper to steal from. The kind of thing you'd fork and turn into a portfolio artifact for an Anthropic Frontier-Red-Team application.

### 1d. The Last AI Built by Humans: Toward Genuine Recursive Self-Improvement (arXiv 2609.11873)

**What the paper says:** Position paper on the criteria for "genuine" (as opposed to bounded / superficial) RSI: **persistence** (changes stick across generations), **compounding** (improvements to the improvement process itself), **generality** (gains transfer across task domains). Argues most 2026 systems, Anthropic's disclosed 26% number included, are still in the *bounded* regime — human review gates and non-transferring improvements — but the trajectory into the *genuine* regime is measurable.

**Why it matters:** The vocabulary anchor. Every interview question about self-improvement in 2026-Q4 will use one of these three terms. Learn the definitions.

### Sources

- [arXiv 2609.15802 — The Economics of Recursive Self-Improvement](https://arxiv.org/html/2609.15802) `[primary]`
- [arXiv 2609.14858 — Dream-RSI: Recursive Self-Improvement through Evolving Worlds](https://arxiv.org/abs/2609.14858v1) `[primary]`
- [arXiv 2609.19526 — Self Improvement via Fast Tree-search](https://arxiv.org/abs/2609.19526) `[primary]`
- [arXiv 2609.11873 — The Last AI Built by Humans: Toward Genuine Recursive Self-Improvement](https://arxiv.org/abs/2609.11873v2) `[primary]`
- [arXiv 2607.07663 — Recursive Self-Improvement in AI: From Bounded Self-Refinement to Autonomous Research Loops](https://arxiv.org/abs/2607.07663) `[primary]`
- [arXiv 2609.13406 — Generalized Agent Iteration](https://arxiv.org/abs/2609.13406) `[primary]`
- [GitHub: VoltAgent — awesome-ai-agent-papers 2026 curated list](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`

### Why it matters to you

- **Job lens:** **These four papers are the interview conversation for every Anthropic / OpenAI / DeepMind safety-adjacent role in Q4.** Read them once each. When asked "what do you think about recursive self-improvement?", answer with (1) the Cunningham elasticity frame; (2) the Dream-RSI evolving-envs bridge; (3) the tree-search sample-efficient prototype; (4) the persistence / compounding / generality criteria. That's a **3-minute answer that separates you from the median candidate by an order of magnitude.**
- **Startup lens:** The gap between **bounded RSI** (where Anthropic's 26% figure is now) and **genuine RSI** is a **funded startup opportunity**. Concretely: **RSI-observability** — the platform that lets a lab (or a research team) track (a) which experiments were designed vs run vs interpreted by an agent, (b) improvement compounding across generations, (c) alignment invariants that must hold over the loop. Zero incumbents, and every lab's Preparedness / Frontier Red Team is a design partner. A working demo → any Seed VC with an existing agent-infra thesis.
- **Insight:** Notice the **timing coordination.** Four RSI papers in two weeks + Amodei's Sept 12 pacing essay + Anthropic's Sept 17 26% disclosure = a **coordinated normative-and-empirical moment** for the field. The frontier labs are laying the intellectual groundwork for a public conversation about capability-pacing that lets them keep shipping while claiming responsibility. **Read it as strategy, not just science.**

---

## 2. Interpretable memory decision controllers — the memory-agent research bottleneck moves again {#2-memory-controllers}

**What happened:** In the daily-arXiv issue for Sept 22 ([Latest 20 Papers issue #565](https://github.com/zachysun/DailyArXiv/issues/565)), a paper titled **"An Interpretable Memory Decision Controller for LLM Agents Based on Three-Signal Complementarity"** (dated 2026-09-18) landed. It's the operational follow-up to the [Memory in the Age of AI Agents](../2026-09-10/04-research-progress.md#1-realtime-memory) taxonomy paper from last edition.

**What the paper argues (per the arXiv abstract as tracked in the daily digest):**

- The **recall-filtering problem** (deciding what to bring into context) is now the memory research bottleneck, **not** storage volume.
- Proposes a **three-signal complementarity** controller: **recency**, **relevance**, and **utility-of-past-use** — combined via a small learnable head, producing an **interpretable memory decision** (i.e., you can read *why* the agent chose to recall a given fragment).
- On [Mem0's memory benchmarks](https://mem0.ai/blog/state-of-ai-agent-memory-2026), the three-signal controller matches larger neural retrievers at a fraction of the latency — a **latency-quality Pareto move**, not a raw-quality one.

**Cross-link with the Mem0 State-of-Agent-Memory 2026 landscape:** memory agents are now measured on **four core competencies** — accurate retrieval, test-time learning, long-range understanding, selective forgetting — and per-competency benchmarks exist for each. The three-signal controller is aimed squarely at the *selective forgetting* + *accurate retrieval* pair.

### Sources
- [GitHub — DailyArXiv Latest 20 Papers issue #565 (Sept 22, 2026)](https://github.com/zachysun/DailyArXiv/issues/565) `[aggregator]`
- [Mem0 — State of AI Agent Memory 2026: Benchmarks & Trends](https://mem0.ai/blog/state-of-ai-agent-memory-2026) `[analysis]`
- [arXiv 2603.07670 — Memory for Autonomous LLM Agents: Mechanisms, Evaluation, and Emerging Frontiers](https://arxiv.org/abs/2603.07670) `[primary]`
- [arXiv 2606.24775 — Are We Ready For An Agent-Native Memory System?](https://arxiv.org/pdf/2606.24775) `[primary]`
- [arXiv 2607.05690 — Memory in the Loop: In-Process Retrieval as Extended Working Memory for Language Agents](https://arxiv.org/pdf/2607.05690) `[primary]`
- [arXiv 2602.05665 — Graph-based Agent Memory: Taxonomy, Techniques, and Applications](https://arxiv.org/pdf/2602.05665) `[primary]`

### Why it matters to you

- **Job lens:** **Memory-agent** roles at Anthropic (Applied AI — Agent Memory), OpenAI (Codex / Agents SDK), Sierra (persistent CX agents), and any AI-first customer-support / assistant startup want to see the *four-competency* frame in your language. Ship a **memory-suite eval** as an add-on to your 5-case eval ([2026-09-10/04 §3](../2026-09-10/04-research-progress.md#3-eval-suite-template)) — 5 more cases, one per competency plus one for controller-interpretability — and cite the three-signal-controller paper in the README.
- **Startup lens:** **Interpretable memory controllers as a middleware.** Wrap the three-signal-controller pattern into a Python package that plugs into LangGraph, Claude Agent SDK, OpenAI Agents SDK; ship a hosted control plane that shows recruiters/engineers *why* their agents recall what they recall. Sub-$5M seed on a working demo + 2 open-source integrations.
- **Insight:** **Interpretability is quietly re-entering as a product requirement**, not just a research topic. When the pacing consensus asks for pre-deployment eval ([`01` §1](./01-big-lab-moves.md#1-red-lines)), *explainable recall* is one of the harder-to-fake evidence items. Watch for interpretability language showing up in enterprise procurement RFPs by Q4.

---

## 3. Terminal-Bench 4.0 refresh, and the eval landscape now that Astra and Fable are tied {#3-terminal-bench-4}

**What happened:** The **September 2026 refresh** of the community-run **Terminal-Bench 4.0 leaderboard** places **Codex (GPT-6 Astra) at 58.2%** and **Claude Code (Fable 5.1) at 57.9%** — essentially tied at #1 (per Turing College + Tech-Insider snapshots). This alongside the **Terminal-Bench-Science** measurement Anthropic quoted for Fable 5.1 (52.6%, [2026-09-10/04 §2](../2026-09-10/04-research-progress.md#2-terminal-bench-science)) means **there are now two sibling benchmarks that recruiters and buyers cite by name.** Fluency here is a filter.

**Sources:**
- [Turing College — Best AI Coding Agents in 2026](https://www.turingcollege.com/blog/best-ai-coding-agents-2026-claude-code-codex-cursor) `[analysis]`
- [Tech-Insider — Codex vs Cursor vs Claude Code: 88.6% vs $200 Cap](https://tech-insider.org/codex-vs-cursor-vs-claude-code-2026/) `[analysis]`
- [MarkTechPost — Fable 5.1 at 52.6% on Terminal-Bench-Science](https://www.marktechpost.com/2026/09/01/anthropic-releases-claude-fable-5-1-and-claude-mythos-5-1-52-6-on-terminal-bench-science-and-75-cheaper-cache-reads/) `[secondary]`

### Why it matters to you

- **Job lens:** **Fork Terminal-Bench 4.0**, run the 5-case subset of it that matters to your target role (coding, science-agent, tool-use), publish results per model on your own hardware. **This is the second-highest-return portfolio artifact** of Q4 — after the router+durable-execution artifact ([`03` §1](./03-practical-skills-and-tools.md#1-durable-execution)) — because it's a **reproducible independent measurement**, not a marketing claim.
- **Startup lens:** The **tied leaderboard** is the moment router+observability becomes revenue. Enterprise buyers can no longer justify single-vendor lock-in on quality grounds — the numbers are within noise. **Sell "how to be provider-independent"** as the product. Two founder wedges: (a) **enterprise routing observability with provable neutrality** (open source + optional hosted); (b) **automated regression benchmarking** — every time either lab ships, your product runs a full eval and emails a diff.
- **Insight:** The **community-run leaderboard trumping vendor benchmarks** is the healthiest sign for 2026 eval culture. Follow the pattern in your own work: **when you ship a portfolio artifact with numbers, publish the reproducer** — that's the differentiator vendors can't fake.

→ Cross-link: [`03` §1 router+durable-execution artifact](./03-practical-skills-and-tools.md#1-durable-execution) · [`05` §2 skill re-price](./05-career-and-startup.md#2-reprice).
