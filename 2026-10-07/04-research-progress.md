# Research Progress — 2026-10-07

Papers, benchmarks, and architectural moves worth tracking from the frontier.

---

## 1. Agent memory goes production-grade — four benchmarks landed in Oct {#1-memory-benchmarks}

**Why this cluster matters.** On **Sept 10 we flagged** "Memory in the Age of AI Agents" (arXiv 2512.13564) as thesis-level. By October, memory had moved from thesis to a cluster of **measurable benchmarks** — the signal that a research direction has crossed the chasm from idea to engineering practice. Four papers / benchmarks worth knowing by name:

### 1.1 `mem-agent` — Dria (Oct 9, 2025)

A **4B-parameter LLM agent** trained with **GSPO** (Group-wise Sequence Policy Optimization) using a scaffold that gives it:
- A **Python tool interface** for computation and I/O
- A **markdown-file-based memory layer** — the agent reads/writes `.md` files to its own long-term memory

Headline result: a small open-weights model with a disciplined memory layer **approaches big-model agent performance on long-horizon tasks**, because its memory is **inspectable, editable, and transferable** across sessions.

- **Why you care.** The "markdown as memory" primitive is production-shippable **today**. Pair it with Claude Skills (files are already how Skills work) and you have a reusable agent memory architecture that doesn't require your lab to re-train a model.
- **Source.** [analysis] [Hugging Face — mem-agent blog](https://huggingface.co/blog/driaforall/mem-agent-blog)

### 1.2 `MemoryAgentBench` — four core memory competencies

Explicitly designed to test **four axes** of memory in agents:
1. **Accurate retrieval** — can the agent find what it stored?
2. **Test-time learning** — can it update what it knows mid-task?
3. **Long-range understanding** — can it tie together information from distant parts of a long context?
4. **Conflict resolution** — when two memories disagree, which wins?

- **Why you care.** This is the **first widely-cited memory-benchmark framing** that gives you a four-row table to put on an interview whiteboard. Memorize it.

### 1.3 `MemoryArena` — human-crafted interdependent sub-tasks

Scenarios where agents must **learn from earlier actions and feedback within the same scenario**. Supports evaluation across:
- Web navigation
- Preference-constrained planning
- Progressive information searching
- Sequential formal reasoning

- **Why you care.** This is the eval you want to run against your own agent before you ship. The web-navigation axis in particular is immediately relevant to ChatGPT Atlas-style browser agents.

### 1.4 `Mem2ActBench` — inference-driven long-term memory utilization

Evaluates whether agents can **infer task-critical constraints from evolving interaction histories** and ground them in executable tool calls — i.e. can the agent *use* what it remembers, not just recall it.

- **Why you care.** The gap between "the agent recalls" and "the agent uses" is where production agents break. If your eval harness only measures retrieval, you're measuring the easier half.

**Umbrella sources.**
- [primary] [arXiv — mem-agent paper (via Hugging Face)](https://huggingface.co/blog/driaforall/mem-agent-blog)
- [primary] [arXiv — ActMem: Bridging Memory Retrieval and Reasoning](https://www.alphaxiv.org/abs/2603.00026)
- [primary] [arXiv — Mem2ActBench benchmark](https://arxiv.org/html/2601.19935v1)
- [analysis] [SOTA Verified — evaluating memory in LLM agents](https://sotaverified.org/papers/evaluating-memory-in-llm-agents-via)

**Why it matters to you (lens-tagged).**
- **Job.** The scarce question in any FDE / MLE loop is "**how would you measure your agent?**" If your answer invokes **MemoryAgentBench's four axes + Mem2ActBench's inference layer** by name, you are instantly a top-decile candidate.
- **Startup.** Any product with the phrase "**remembers your preferences**" or "**learns about you**" needs an eval loop like this one. Build it before you build the ML.
- **Insight.** The memory axis has moved into the **evaluation-primitives tier** — alongside correctness, latency, cost. Any agent not evaluated for memory is incomplete in Q4 2025.

`#arxiv #memory #agents #evals #benchmarks`

---

## 2. Agent reasoning + tool use — the ToolBrain + MARL cluster {#2-tool-brain}

**What landed in Oct 2025 arXiv.**

- **`ToolBrain`** — a flexible reinforcement learning framework for teaching LLM agents **when and how to call tools**. Distinct from "give the agent a tool list" by learning the tool-selection policy end-to-end.
- **"Learning to Lead Themselves: Agentic AI in MAS using MARL"** — multi-agent systems trained with multi-agent reinforcement learning for self-organization. The core question: can agents figure out who-does-what without a human orchestrator?

**Why this is a cluster, not two papers.** Both treat **tool/subtask selection as a learnable policy** rather than a prompt-engineered decision. If this direction keeps compounding, the "manual orchestrator written by a human" primitive (today's AgentKit visual builder, today's hand-written Agent SDK code) gets replaced by **learned orchestration** inside 18 months.

**Sources.**
- [analysis] [IntuitionLabs — Latest AI Research Dec 2025: GPT-5, Agents & Trends](https://intuitionlabs.ai/articles/latest-ai-research-trends-2025)
- [analysis] [DEV.to — Frontiers in ML: autonomous agents, scientific discovery](https://dev.to/khanali21/frontiers-in-machine-learning-advancements-in-autonomous-agents-scientific-discovery-and-501a)
- [aggregator] [Paper Digest — Most Influential ArXiv AI Papers 2025-09](https://resources.paperdigest.org/?p=7358)

**Why it matters to you.**
- **Job.** Expect "did you follow the ToolBrain / MARL line?" as a signal of research-adjacency. Not required for FDE roles, but a plus-signal for research-engineer / applied-research roles.
- **Startup.** If your startup wedge is **"the orchestration layer,"** your 24-month moat erodes against the learned-orchestration line. Pivot toward the **task-definition layer** (what jobs people want done, in what domains) — orchestration will commoditize.
- **Insight.** The research pipeline for 2026 is: **memory → learned orchestration → cross-agent collaboration**. Position accordingly.

`#arxiv #tool-use #marl #reinforcement-learning #agents`

---

## 3. CIIR search-agents + RL (COLM 2025) — RAG is dead; search-agents are the new thing {#3-rl-search}

**What happened.** CIIR (UMass Amherst) researchers presented work on the **next generation of AI search agents trained with reinforcement learning** at **COLM 2025**. The thesis: RAG as it was built in 2023–2024 (retrieve-then-generate) is being replaced by **search-agents** that **interleave retrieval and reasoning iteratively** — closer to how humans use the web.

**Sources.**
- [primary] [CIIR UMass — COLM 2025 paper](https://ciir.cs.umass.edu/node/854)

**Why it matters to you.**
- **Job.** Any role involving "**retrieval**" is now really an **agent-search** role in 2026. Update your résumé keywords: *RAG* → *search agents / retrieval agents*. Enterprise search is where the money is.
- **Startup.** The vertical-search wedge is **especially open** — build the search-agent that outperforms Google for one specific professional vertical (medical, legal, scientific, academic). Perplexity owns consumer; verticals are still open.
- **Insight.** Perplexity + CIIR work + ChatGPT Atlas is three independent signals that **search is being re-invented as an iterative agent task**, not a single-step query. The 1998 Google thesis (one query, one SERP) is officially legacy.

`#rag #search-agents #retrieval #rl #colm`

---

## 4. Watchlist seeds — three papers to re-read on the weekend {#4-reading-list}

Not deep-dived here, but worth a flagged weekend read:

- **"Learning to Lead Themselves"** (MARL agentic) — [arXiv 2025](https://arxiv.org/list/cs.AI/2025-10)
- **AI Scientist-v2** (workshop-level automated scientific discovery via agentic tree search) — [analysis](https://dev.to/khanali21/frontiers-in-machine-learning-advancements-in-autonomous-agents-scientific-discovery-and-501a)
- **"The Rise of AI Agents, MCP Servers and n8n"** (practitioner survey, not research) — [DEV](https://dev.to/manishtamang/the-rise-of-ai-agents-mcp-servers-and-n8n-what-you-need-to-know-in-2025-2eol) — useful for interview talk-track breadth

`#reading-list #arxiv #weekend`
