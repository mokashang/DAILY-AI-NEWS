# Research Progress — 2026-09-21

Papers, benchmarks, breakthroughs. What's moving the frontier.

---

## 1. The 3-paper "recursive agent" reading list — ReasoningBank + Real-Time Reasoning Agents + Memory in the Age of AI Agents {#1-reasoning-bank}

**What happened.** Three papers landed or firmed up in the last month that together define the *recursive agent* research frontier — the shift from "agent completes a task" to "agent learns from its own trace and self-evolves over long horizons in changing environments":

**(a) ReasoningBank: Scaling Agent Self-Evolving with Reasoning Memory** (arXiv 2509.25140). Introduces a persistent, structured memory of *reasoning trajectories* that the agent reads-back and refines. Not "chat history"; not "vector store" — a memory keyed on reasoning steps that the agent can *retrieve to reason similarly next time*.

**(b) Real-Time Reasoning Agents in Evolving Environments** (arXiv 2511.04898). Formalizes the case where the environment itself changes underneath the agent — the eval bar moves from "static task completion" to "task completion while ground truth drifts." Anchor paper for the "the world doesn't wait" agent design pattern.

**(c) Memory in the Age of AI Agents** (arXiv 2512.13564). Survey. Introduces the *storage / recall / memory* trichotomy (foreshadowed in [2026-05-18 §research](../2026-05-18/04-research-progress.md)), taxonomizes 40+ memory architectures. Best single reference for anyone building agents that need to remember across sessions.

**Sources.**
- [ReasoningBank (arXiv 2509.25140)](https://arxiv.org/pdf/2509.25140) `[primary]`
- [Real-Time Reasoning Agents in Evolving Environments (arXiv 2511.04898)](https://arxiv.org/pdf/2511.04898) `[primary]`
- [Memory in the Age of AI Agents (arXiv 2512.13564)](https://arxiv.org/abs/2512.13564) `[primary]`
- [Agent-Memory-Paper-List (companion repo)](https://github.com/Shichun-Liu/Agent-Memory-Paper-List) `[primary]`
- [MemoryPapers.org — LLM & Agent Memory Research Library](https://memorypapers.org/) `[aggregator]`
- [mem0 — State of AI Agent Memory 2026](https://mem0.ai/blog/state-of-ai-agent-memory-2026) `[analysis]`

**Why it matters to you.**
- **Job.** Bring one paragraph on each of the three papers into your prep. Interviewers at Anthropic (given the [26%-Claude-led-R&D disclosure](./01-big-lab-moves.md#2-claude-r-and-d)), OpenAI, Google DeepMind, and Sierra will absolutely test the memory / self-evolving frontier — it's the natural follow-up to "have you shipped a Claude Code subagent?"
- **Startup.** The three papers together sketch the *durable-agent-runtime* wedge. Product primitives that map directly: reasoning-trace store, environment-drift detector, memory-consolidation service. This is the technical backbone of the [`02` §1](./02-new-emerging.md#1-funding-week) Temporal-shaped-but-agent wedge.
- **Insight.** The frontier moved this year from "agent that can" to "agent that keeps." *Keeping* is unglamorous — no one live-tweets a memory consolidation. But keeping is the axis where the next 12 months' evaluation vocabulary is being written.

`#arxiv #agents #memory #reasoning`

---

## 2. Reinforcement learning for LLM reasoning — Gradient-Aligned Rewards (EMNLP 2026) {#2-gradient-aligned-rewards}

**What happened.** Accepted at EMNLP 2026: *Gradients Know What Outcomes Don't: Unlocking Reinforcement Learning for LLM Reasoning with Gradient-Aligned Rewards.* Central claim: outcome-only rewards (correct/incorrect) are too sparse to shape multi-step reasoning; align the reward with the *gradient signal from the reasoning steps themselves* to get denser, more useful learning.

Companion work in the same neighborhood: **DyTopo** (Dynamic Topology Routing for Multi-Agent Reasoning via Semantic Matching) — dynamically rewires agent-to-agent connections each reasoning round; and **CommCP** (efficient multi-agent coordination via conformal prediction on messages).

**Sources.**
- [DailyArXiv issue lists — Sept 17–20](https://github.com/somewordstoolate/DailyArXiv/issues/332) `[aggregator]`
- [DailyArXiv — Sept 15](https://github.com/NeoFii/DailyArXiv/issues/158) `[aggregator]`
- [DailyArXiv — Sept 18](https://github.com/NeoFii/DailyArXiv/issues/161) `[aggregator]`
- [VoltAgent/awesome-ai-agent-papers — curated collection](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`

**Why it matters to you.**
- **Job.** If you're targeting MLE roles, especially ones with "post-training / RLHF / RLAIF" in the JD: this direction is the fastest-improving research thread you should be able to talk about. The "outcome rewards are too sparse for reasoning" framing is now table stakes.
- **Startup.** A wedge to watch — not to bet on yet: **reasoning-step reward shapers** as a hosted service. Too early for a startup, but worth a paper club at your school this month.
- **Insight.** RL-for-reasoning is where 2026's Q4 research energy is going. Read alongside the on-policy-distillation sweep from [2026-05-19](../2026-05-19/04-research-progress.md) — same class of "richer intermediate signal beats sparser end signal" idea, applied at different training stages.

`#arxiv #rl #post-training #reasoning`

---

## 3. Agent security & evals — Plug 'n' Pray (AISEC'26) and the eval-workshop wave {#3-agent-security}

**What happened.** *Plug 'n' Pray: Agentic LLM-based Detection of Potential Log File Exposures in Third-Party Content Management System Plugins* (AISEC'26, co-located with ACM CCS 2026) shows the current bar for agent-shaped defensive security research — real logs, real plugins, agentic scan-and-recommend, measurable false-positive rates.

Other notable Sept-2026 workshop-accepted work: *Reasoning through Evolution: Automatic Meta-path Discovery for LLM-based Fake News Detection* (dated 2026-09-16); *LLMs Interpret, Embeddings Organize, Graphs Emerge: Agent-Driven Compilation of Scientific Knowledge* — both examples of the *"agent + curated pipeline + measured outcome"* pattern that is winning at workshops this fall.

**Sources.**
- [DailyArXiv — Sept 17–20 issue lists](https://github.com/somewordstoolate/DailyArXiv/issues/332) `[aggregator]`
- [DailyArXiv — jyyang621](https://github.com/jyyang621/DailyArXiv/issues/414) `[aggregator]`
- [VoltAgent/awesome-ai-agent-papers](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`

**Why it matters to you.**
- **Job.** Agentic-security is a rising job category — see the Anthropic Verification / Google Fairwind / OpenAI Verified Defender programs from [`02` §4](./02-new-emerging.md#4-cyber-tier). Papers like Plug 'n' Pray are the kind of work these teams point to when they interview.
- **Startup.** Every plugin ecosystem (WordPress, Shopify, Chrome, ChatGPT extensions — cf. [`03` §2](./03-practical-skills-and-tools.md#2-chatgpt-extensions)) is a candidate market for an agent-driven security-scanner. This is a defensible-because-domain-specific wedge that a two-person team can ship.
- **Insight.** The AISEC and EMNLP workshop pipelines have become the leading indicator for "which agentic tasks are going to be productized in 12 months." Reading the workshop programs is a cheaper research-radar than trying to keep up with all of arXiv.

`#security #agents #workshops`

---

## 4. Reading order this week

If you have **90 minutes total** in the next 7 days, spend them like this:

1. **30 min** — skim §1's three papers (ReasoningBank abstract + intro; Real-Time Reasoning Agents abstract + evaluation setup; Memory survey table-of-contents). Goal: be able to summarize each in one sentence.
2. **30 min** — read §2 Gradient-Aligned Rewards from EMNLP through Section 4. Goal: understand *why* outcome-only rewards fail for reasoning.
3. **30 min** — pick one AISEC / workshop paper from §3 and read end-to-end. Goal: internalize how a good agentic-security paper is *structured* (setup → threat → agent → measurement).

`#reading-list`
