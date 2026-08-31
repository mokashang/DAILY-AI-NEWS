# Research Progress — 2026-08-01

arXiv · benchmarks · breakthroughs. What's moving the frontier this week.

---

## 1. Agents' Last Exam (ALE) — long-horizon, verifiable, economically valuable tasks {#1-agents-last-exam}

**What it is.** Benchmark designed to evaluate AI agents on **long-horizon, economically valuable, real-world tasks with verifiable outcomes.** Each task is a full-workflow scenario (~hours of expert time), evaluated by ground-truth artifacts rather than judged prose. Positioned as the successor rubric to Humanity's Last Exam (question-answering) — same "hardest thing we can grade" ambition, applied to *agents doing work* rather than *models answering questions*.

**Why it matters this weekend.** ALE is the first benchmark that gives you a defensible answer to the interview question "*how would you evaluate whether an agent is production-ready?*" The pattern — **long-horizon + verifiable outcome + economically-valuable-task selection** — is the eval-design vocabulary FDE hiring panels are converging on.

**Sources:**
- [Agents' Last Exam — Hugging Face paper page](https://huggingface.co/papers/2606.05405) [primary]
- [VoltAgent — Awesome AI Agent Papers 2026 repo](https://github.com/VoltAgent/awesome-ai-agent-papers) [aggregator]

**Why it matters to you.**
- **Job:** *"we ran our agent on ALE Task {N}, hit {X}% at {Y} steps, here's the trace"* — this is the exact three-line paragraph a Solutions Eng / FDE resume needs in Aug 2026. One weekend to have it.
- **Startup:** if your product is agent-shaped, publish an ALE score on your landing page. Even a bad number gives you a *credibility peg* against competitors who publish nothing.
- **Insight:** benchmarks that combine **long-horizon + verifiable + economically-valuable** are the ones that survive contamination pressure. This is the class of benchmark you want your agent scored on, because Sonnet 6 / GPT-5.7 / Opus 5.1 will all be scored on it too, and you'll be able to compare apples-to-apples.

`#arxiv #ale #agents #benchmarks #evaluation`

---

## 2. AgenticPay + 110-task multi-agent negotiation benchmark {#2-agenticpay}

**What it is.** A **multi-agent LLM negotiation system** paper introducing a **110+ task benchmark** for buyer-seller negotiation between LLM agents. Tasks cover price haggling, contract-clause negotiation, payment-term settling. Finding: current-generation single-model chains **collapse to "agree at seller ask" or "walk away"** in >60% of tasks that require sustained back-and-forth.

**Sources:** [VoltAgent 2026 papers](https://github.com/VoltAgent/awesome-ai-agent-papers), Awesome AI Agent Papers repo entry for AgenticPay.

**Why it matters to you.**
- **Job:** any Solutions Eng interview at Sierra / Decagon / Cresta / Rasa is going to ask about "agent-to-agent" scenarios in the next 90 days. Cite AgenticPay by name — most interviewers won't have read it.
- **Startup:** the >60% collapse rate is a **founder-fit signal for "adversarial guardrails as a service"** — a $99/mo product that stress-tests a customer's outbound-agent script against 20 canned buyer personae before it goes live.
- **Insight:** multi-agent systems where both sides are LLMs are the *newest failure mode* in the field. Every enterprise deployment of "agent talks to agent" (procurement, supply chain, customer↔vendor auto-resolution) is going to need a third-party sanity check.

`#arxiv #agents #multi-agent #negotiation #benchmarks`

---

## 3. ROMA — Recursive Open Meta-Agent Framework for long-horizon multi-agent systems {#3-roma}

**What it is.** Framework proposal that **breaks large tasks into a subtask tree**, recursively planned by a meta-agent, executed by sub-agents. Framing: "long-horizon multi-agent systems" — an alternative to flat-orchestrator + N-workers patterns that have been the industry default (Claude Code sub-agent split, LangGraph, AutoGen).

**Why it's worth 15 minutes this weekend.** The ROMA structure is philosophically close to `ultracode` (Claude Code's multi-agent JS orchestrator, up to 1000 subagents per run — see [2026-07-17/03](../2026-07-17/03-practical-skills-and-tools.md#5-mcp-spec)); reading the paper gives you the vocabulary to *justify* the pattern you're already using. Also compare to yesterday's **MemHarness (2026-07-30)** [`04` §1](../2026-07-31/04-research-progress.md#1-memharness) — ROMA supplies the *task-decomposition primitive* MemHarness assumes.

**Sources:** [VoltAgent Awesome AI Agent Papers 2026](https://github.com/VoltAgent/awesome-ai-agent-papers) — ROMA entry; [Mem0 State of AI Agent Memory 2026](https://mem0.ai/blog/state-of-ai-agent-memory-2026) for the memory-primitive companion.

**Why it matters to you.**
- **Job:** the interview question "*how would you architect an agent for a 4-hour customer workflow?*" now has a citable answer with a paper name. That's the difference between "sounds thoughtful" and "sounds current."
- **Startup:** a $49/mo dev-tool that inspects a subagent-tree run, flags where the tree got too deep, and suggests where to collapse — this is a wedge that only becomes viable *now* that recursive subagent orchestration is popular enough to have real failure modes.
- **Insight:** the field is quietly converging on **"trees, not chains"** as the default agent topology. Every framework that stayed chain-first is going to look dated by Q4.

`#arxiv #roma #multi-agent #recursive #agent-architecture`

---

## 4. Also worth logging (one-liners)

- **Mem0 State of AI Agent Memory 2026** report — [mem0.ai/blog](https://mem0.ai/blog/state-of-ai-agent-memory-2026); head-to-head comparison of ten memory approaches on LoCoMo benchmark, with a new token-efficient memory algorithm built on single-pass hierarchical extraction + multi-signal retrieval. Adds a citation option for "here's my memory architecture" interview answers.
- **Terminal-bench (July continuation)** — see yesterday's [`04` §2](../2026-07-31/04-research-progress.md); the CLI-agent benchmark suite quietly became the reference for terminal-native agent evals in Q3.
- **QUEST — training frontier deep-research agents with fully synthetic tasks** [arxiv 2605.24218] — evidence that synthetic-task training + tool-use can substitute for expert-authored eval data, cutting the eval-cost floor. Read alongside [AI2's harness-evolution critique (Jul 14)](../2026-07-17/04-research-progress.md#2-harness-evolution) — synthetic tasks are the only scalable way through the eval-hygiene bottleneck AI2 flagged.

`#arxiv #memory #terminal-bench #synthetic-tasks #eval-hygiene`
