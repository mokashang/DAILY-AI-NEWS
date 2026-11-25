# Research Progress — 2026-06-18

The eval frontier this month: **benchmarks for agents that have to *replicate research*, *do multimodal deep-research*, *operate in 1M-token real-world contexts*, and *get tested efficiently*.** Plus the most useful agent-engineering primitive of the week: **async subagents** as a non-blocking delegation pattern.

Tags: `#research #arxiv #benchmarks #agents #evals #multimodal #mcp`

---

## 1. Agent benchmarks that look more like production than like leaderboards {#1-benchmarks}

The arXiv signal this month: **a wave of agent benchmarks that all share one property — they're built to stress the gap between leaderboard performance and production usefulness.**

### 1a. PaperBench — can agents *replicate* AI research?

**The setup:** PaperBench evaluates AI agents on the task of **replicating a state-of-the-art ML research paper end-to-end** — from reading the PDF to reproducing the experimental results. The thesis: agents that can autonomously replicate ML research papers would accelerate ML progress (i.e., the recursive-self-improvement axis Karpathy went to Anthropic to staff).

**Source:** [arXiv 2504.01848 — PaperBench: Evaluating AI's Ability to Replicate AI Research](https://arxiv.org/pdf/2504.01848) `[primary]`

### 1b. MiroEval — multimodal deep-research agents, scored on process *and* outcome

**The setup:** MiroEval benchmarks **multimodal deep-research agents** — i.e., agents that gather + reason over text + image + video sources — and crucially evaluates both **process** (how the research was done) and **outcome** (whether the final answer is correct). Process scoring is the **anti-shortcut signal**: a model that lucks into the right answer doesn't get full credit.

**Source:** [arXiv 2603.28407 — MiroEval: Benchmarking Multimodal Deep Research Agents in Process and Outcome](https://arxiv.org/pdf/2603.28407) `[primary]`

### 1c. AgencyBench — autonomous agents in 1M-token real-world contexts

**The setup:** AgencyBench evaluates frontier autonomous agents on **real-world tasks at 1M-token context**, where the agent has to maintain state across long horizons (codebases, document corpora, multi-session workflows). It pairs with **BrowseComp** (browsing-agent benchmark) as the next-gen agent eval surface.

**Source:** [arXiv 2601.11044 — AgencyBench: Benchmarking the Frontiers of Autonomous Agents in 1M-Token Real-World Contexts](https://arxiv.org/pdf/2601.11044) `[primary]`

### 1d. Efficient Benchmarking of AI Agents — fewer tasks, same rank

**The setup:** This paper introduces an **Item Response Theory (IRT)-motivated mid-range difficulty filter** that reduces the number of evaluation tasks by **44–70%** while maintaining **high rank fidelity** — i.e., the same agent leaderboard ordering with a fraction of the compute. Practically: a tractable way to A/B providers without burning a research-cluster budget on every comparison.

**Source:** [arXiv 2603.23749 — Efficient Benchmarking of AI Agents](https://arxiv.org/abs/2603.23749) `[primary]`

### Why it matters to you

- **Job lens:** Eval-design is the most under-priced ML skill right now — and it's the **fastest path to a research-engineer or applied-AI-research role** at a frontier lab. Read **one** of these papers end-to-end this weekend (recommend Efficient Benchmarking — shortest, most directly useful), summarize it in a LinkedIn post, and cite it in your next application's cover letter. Bonus: implement the IRT-filter trick on your own multi-provider harness ([`03` §2](./03-practical-skills-and-tools.md#2-comparison-harness)) — that's a credible "I read recent research and applied it" claim.
- **Startup lens:** PaperBench is a wedge by itself — **"agents that replicate published ML research"** is a service you could sell to research labs, sovereign AI funds, and applied research divisions of consulting firms. Pricing: $20K/replication, $200K/year subscription, "we re-run the agent on every new top-conference paper and deliver a working repo." The supply side (cheap compute + good agents) and the demand side (research orgs swamped with reproduction debt) are both real.
- **Insight:** Notice the pattern: **every "real" benchmark of 2026 is engineering an *escape* from Goodhart's Law on the canonical benchmarks** (MMLU saturated, HumanEval saturated, etc.). Process scoring (MiroEval), real-tool calls (Toolathlon / MCP-Atlas from [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)), 1M-context real-world (AgencyBench), replication-as-task (PaperBench). The frontier of **measurement** is now ahead of the frontier of **capability** for the first time in 2 years. Internalize this — it changes how you talk about progress in interviews.

→ Cross-link: [2026-05-22/04 §1 MCP-Atlas + Toolathlon real-tool benchmarks](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) · [`03` §2 build your own harness](./03-practical-skills-and-tools.md#2-comparison-harness).

---

## 2. Engineering primitive of the week: async subagents (Hermes Agent, June 15)

**What shipped:** Nous Research's **Hermes Agent** added an `async_delegation` toolset on June 15. The previous `delegate` tool was sequential in practice — the parent agent froze while the child completed. The new model:

- Background subagents run as **in-process threads**, return a **task ID immediately**, and complete without holding the parent session hostage.
- Each subagent is **isolated**: own conversation, own terminal session, own toolset.
- **Only the final summary returns to the parent.** The parent context never sees the child's intermediate tool calls or reasoning — meaning the parent's context window stays clean for long-horizon work.

**Sources:**
- [MarkTechPost — Hermes Agent Adds Asynchronous Subagents (June 16)](https://www.marktechpost.com/2026/06/16/hermes-agent-adds-asynchronous-subagents-so-delegated-work-no-longer-blocks-the-parent-chat/) `[secondary]`
- [Future Signal News — Hermes Agent: Async Subagents Unlock Non-Blocking AI Workflows](https://futuresignalnews.com/hermes-agent-async-subagents/) `[secondary]`
- [TechTimes — Hermes Agent Ships Async Subagents](https://www.techtimes.com/articles/318549/20260617/hermes-agent-ships-async-subagents-delegated-work-no-longer-blocks-chat.htm) `[secondary]`

### Why it matters to you

- **Job lens:** This is the **single cleanest example of a context-engineering pattern** to talk about in an interview right now. "I prefer async delegation — parent fires the subagent, gets a task ID, keeps working. Parent context stays uncontaminated. The pattern decouples orchestration latency from work latency." That sentence demonstrates you think about agents as *systems*, not as a single chat thread.
- **Startup lens:** The async-subagent pattern is the foundation for **agent orchestrators that look more like job schedulers than chat sessions** (think Airflow for LLM agents). There's a category here.
- **Insight:** Asyc delegation + isolation + summary-return is the same architecture as **Erlang processes / actor model** — it's not new computer science, it's old computer science finally being applied to agents. Read the Erlang papers if you want to predict where agent orchestrators are headed (hint: supervisor trees, let-it-crash, message passing).

→ Cross-link: [`03` §2 use it in your harness](./03-practical-skills-and-tools.md#2-comparison-harness).

---

## 3. Adjacent surface to track: Moonshot AI's Kimi Work (300-subagent swarm, Kimi K2.6) — June 12

**What it is:** Moonshot AI launched **Kimi Work** — a local desktop agent reportedly running on **Kimi K2.6** with a **300-subagent swarm** architecture. Worth tracking as the **most aggressive concurrency play in the agent runtime category** (vs Anthropic's Managed Agents and Google's Antigravity 2.0).

**Source:**
- [MarkTechPost — Moonshot AI Launches Kimi Work, a Local Desktop Agent on Kimi K2.6 With a 300-Sub-Agent Swarm (June 12)](https://www.marktechpost.com/2026/06/12/moonshot-ai-launches-kimi-work-a-local-desktop-agent-reportedly-running-on-kimi-k2-6-with-a-300-sub-agent-agent-swarm/) `[secondary]`

### Why it matters to you

- **Insight:** "300 subagents on a local desktop" is the *upper bound* of the design space — most production systems will settle at 3–10. But the architecture details (how do you avoid token-cost blowups? how do you de-duplicate work across subagents?) are exactly the **interview-question fodder** for orchestration roles. Read for the patterns, not the headline number.

→ Cross-link: [WATCHLIST Moonshot AI thread](../WATCHLIST.md).
