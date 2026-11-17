# Research Progress — 2026-07-09

Three arXiv-and-benchmark threads that moved this week. **MAS-Orchestra reframes multi-agent orchestration as RL** (with a controlled benchmark, MASBench). **Terminal-bench is emerging as the new gold-standard eval** for realistic CLI agents. **AgenticPay** measures buyer-seller negotiation across 110+ tasks — the first serious multi-agent economic-negotiation benchmark. Underneath: the **HAL Holistic Agent Leaderboard** and **PaperBench** (AI replicating AI research) are becoming the community's shared scoring rubrics.

Tags: `#research #arxiv #agents #benchmarks #multi-agent #rl`

---

## 1. MAS-Orchestra — multi-agent orchestration as function-calling RL {#1-mas-orchestra}

**The paper:** MAS-Orchestra reframes **multi-agent orchestration as function-calling reinforcement learning** with **holistic system-level reasoning**. The team introduces **MASBench** — a controlled evaluation for multi-agent workflows.

- **The core insight:** Instead of writing a router-and-workers pattern by hand (which is what most 2025 multi-agent stacks look like), **train the orchestrator with RL against function-calling traces** where the "functions" are calls to other agents. The system learns *which agent to call, when, with what context* as an RL policy rather than a hard-coded topology.
- **Why MASBench matters:** Prior multi-agent benchmarks measured whether the whole system solved a task. MASBench decomposes it into **per-decision quality** (was routing to Agent X the right call?), which is the harness you need to *train* an orchestrator, not just score one.
- **Practitioner take:** This is the **research version of what Claude Code's subagent architecture** ([`03` §3](./03-practical-skills-and-tools.md#3-claude-code-stack)) is doing at the tool level — the orchestrator is what you'd fine-tune, the workers are what you'd swap.

**Sources:**
- [GitHub — VoltAgent/awesome-ai-agent-papers (curated 2026 agent research)](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`
- [arXiv — Evolutionary Perspectives on the Evaluation of LLM-Based AI Agents: A Comprehensive Survey (2506.11102)](https://arxiv.org/pdf/2506.11102) `[primary]`
- [arXiv — Evaluation and Benchmarking of LLM Agents: A Survey (2507.21504)](https://arxiv.org/pdf/2507.21504) `[primary]`
- [arXiv — Efficient Agentic Reasoning Through Self-Regulated Simulative Planning (2605.22138)](https://arxiv.org/pdf/2605.22138) `[primary]`

### Why it matters to you

- **Job lens:** **Any research role at a frontier lab now expects fluency in "multi-agent as RL."** If you cannot describe the difference between (a) a hand-written orchestrator, (b) an RL-trained orchestrator over function calls, (c) a shared-memory multi-agent system with a critic, you are behind the interview bar. Read MAS-Orchestra's abstract before Monday.
- **Startup lens:** MAS-Orchestra + MASBench are the **research primitives** underneath any "agent-team observability" product. There's a founder wedge in **selling the training-time telemetry** — the traces that let a customer *fine-tune their own orchestrator against their own workflow*. Anchor comps: Braintrust, LangSmith, Weights & Biases Agents.
- **Insight:** Watch for the **orchestrator-as-a-service pattern**: a company sells you a *trained* orchestrator that routes across your MCP servers. That is not a 2027 story — it's a Q4 2026 story. Position now.

→ Cross-link: [`03` §3 Claude Code layered stack](./03-practical-skills-and-tools.md#3-claude-code-stack) · [2026-05-21 §5 PostTrainBench / agents-improve-models](../2026-05-21/04-research-progress.md).

---

## 2. Terminal-bench — the CLI-agent eval that's replacing SWE-Bench for many teams {#2-terminal-bench}

**The paper:** **Terminal-bench (arXiv 2601.11868)** benchmarks agents on **hard, realistic command-line tasks** — the closest public eval to "what a devops engineer actually does with an agent."

- **Why it's rising:** SWE-Bench Pro (and DeepSWE) measure *code patches* against known bug reports — a bounded task family. Terminal-bench measures **general command-line agency**: navigating a filesystem, installing dependencies, debugging failed processes, editing configs. Broader failure surface, closer to production use.
- **The benchmark on which Grok 4.5 beat Opus 4.8:** Terminal-Bench 2.1 is the same evaluation Musk pointed to. This is the *why* — Grok 4.5's Cursor-training-data advantage is *specifically* about CLI-and-editor-in-loop patterns, which is what Cursor's data captures.
- **Community adoption:** Included in **HAL — Holistic Agent Leaderboard** (a centralized, reproducible agent eval) as one of its named benchmarks.

**Sources:**
- [arXiv — Terminal-bench (2601.11868 in the awesome-ai-agent-papers list)](https://github.com/VoltAgent/awesome-ai-agent-papers) `[primary]`
- [Roo — Grok 4.5 launched today: what xAI's own benchmarks actually show vs Opus 4.8](https://roo.beehiiv.com/p/grok-4-5) `[analysis]`
- [arXiv — MLgym: A New Framework and Benchmark for Advancing AI Research Agents (2502.14499)](https://arxiv.org/pdf/2502.14499) `[primary]`

### Why it matters to you

- **Job lens:** **Run one Terminal-bench task tonight** and log the cost/latency across the three cheap models ([`03` §1](./03-practical-skills-and-tools.md#1-cheap-tier-routing)). Publish it. This is the fastest "I actually did the thing" credential you can add to your portfolio this week.
- **Startup lens:** Terminal-bench-adjacent tooling — **CLI agents that are safe to run against a real filesystem** — is under-served. Coding editors (Cursor, Windsurf) have gotten most of the attention; the *terminal itself* as a first-class agentic surface is open territory. Anchor comps: Warp, Fig (defunct), Bloop. Wedge: **an audit-logged agentic terminal** that a compliance officer can approve.
- **Insight:** Every benchmark shift is a hiring signal. **SWE-Bench dominated 2024–early-2026 hiring interviews. Terminal-bench will dominate late-2026 through 2027.** Interviewers ask about the benchmark whose leaderboard their team just moved on — track that.

→ Cross-link: [`01` §2 Grok 4.5's Terminal-Bench win](./01-big-lab-moves.md#2-grok-4-5) · [`03` §1 the routing exercise](./03-practical-skills-and-tools.md#1-cheap-tier-routing).

---

## 3. AgenticPay, PaperBench, HAL — the eval stack maturing {#3-eval-stack}

**Three benchmarks worth watching, all recent:**

- **AgenticPay** — 110+ tasks for **buyer-seller negotiation** across multi-agent LLM systems. First serious eval that measures whether agents can *negotiate value* rather than just execute a workflow. Applications: e-commerce agents, procurement, B2B sales assistants.
- **PaperBench** — evaluates **AI's ability to replicate AI research** end-to-end (read paper, implement, run experiments, match reported numbers). The most direct measurement of the "AI-that-improves-AI" thread from [Karpathy's Anthropic hire (2026-05-22)](../2026-05-22/01-big-lab-moves.md#3-karpathy).
- **HAL — Holistic Agent Leaderboard** — a **centralized, reproducible** scoring board for agent evals across the field. The intent: stop the fragmentation where every paper reports on a self-selected benchmark.

**Sources:**
- [arXiv — Evaluation and Benchmarking of LLM Agents: A Survey (2507.21504)](https://arxiv.org/pdf/2507.21504) `[primary]`
- [arXiv — Act As a Real Researcher: A Suite of Benchmarks (2606.07462)](https://arxiv.org/pdf/2606.07462) `[primary]`
- [arXiv — AlphaEval: Evaluating Agents in Production (2604.12162)](https://arxiv.org/pdf/2604.12162) `[primary]`
- [arXiv — From LLM Reasoning to Autonomous AI Agents: A Comprehensive Review (2504.19678)](https://arxiv.org/pdf/2504.19678) `[primary]`
- [Mem0 — State of AI Agent Memory 2026](https://mem0.ai/blog/state-of-ai-agent-memory-2026) `[analysis]`

### Why it matters to you

- **Job lens:** The **HAL leaderboard** is a legible credential surface. If you contribute a benchmark reproduction or a run against HAL, you have a citation-adjacent artifact that's more discoverable than a random blog post. This is *specifically* a good CS-grad-student move — you can do it as a weekend project and put it on the résumé.
- **Startup lens:** **AgenticPay** is a leading indicator that **negotiation-as-a-service** is coming — agent-to-agent commerce for procurement, sales, and matching markets. It is a wedge that assumes both sides of a market run agents; that assumption is 12–24 months from being real, but the tool-and-eval infra is the pre-work. If you want to be early, build a **buyer-agent that talks to seller-agents** and publish it against AgenticPay this quarter.
- **Insight:** **The eval bar sets the ceiling for what the labs can ship.** Watch the benchmarks whose numbers *the labs release against* — that's what they're actually targeting. **Right now: SWE-Bench Pro, Terminal-Bench 2.1, MASBench, HAL.** Ignore any benchmark not on that list unless you want to be arguing about last year's game.

→ Cross-link: [2026-05-22 §3 Karpathy pre-training + recursive-improvement thread](../2026-05-22/01-big-lab-moves.md#3-karpathy) · [ME.md — public MCP server artifact](../ME.md) · [`05` §1 the eval-fluency job lane](./05-career-and-startup.md#1-cheap-tier-lane).
