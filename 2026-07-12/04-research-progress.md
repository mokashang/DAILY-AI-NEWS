# Research Progress — 2026-07-12

Two threads worth reading this weekend. **(1) Agent memory is the concept moving fastest on arXiv this quarter** — Mem0/EverMemOS-style *continuum memory architectures* (CMA), MAGMA multi-graph memory, and "Beyond RAG" as the durable framing. Read one paper, adopt one vocabulary word. **(2) Agentic-reasoning benchmarks are converging on a 3-layer taxonomy** (foundational · self-evolving · collective) — mostly downstream of the July 2025 arXiv survey, but now recurring in new-paper intros as the shared reference frame. Also below: MLGym, RefuteBench 2.0, AgenticPay, SYMPHONY, PaperBench — a scan of what's landing in the arXiv Awesome-AI-Agents list this quarter.

Tags: `#arxiv #research #memory #agents #benchmarks #reasoning #rag`

---

## 1. Memory architectures are the hot arXiv thread this quarter {#1-memory}

**What's happening:** The May–July arXiv volume in agent memory has decisively moved past "RAG + vector DB." Recurring themes across the papers:

- **Continuum Memory Architectures (CMA)** — a class of systems that maintain and update *internal state across interactions* through persistent storage, selective retention, associative routing, temporal chaining, and consolidation into higher-order abstractions. Explicit framing: memory is *not* a stateless lookup table.
- **Mem0 (ECAI 2025) + follow-ons** — the first broad head-to-head of ten memory approaches (RAG, full-context, OpenAI Memory, Zep, and open-source tools) on the **LoCoMo benchmark**. Since publication, referenced as the shared apples-to-apples baseline.
- **MAGMA** — multi-graph memory (semantic + temporal + episodic graphs stitched together, queried by an agent-side router).
- **"Beyond RAG for Agent Memory: Retrieval by Decoupling and Aggregation"** — argues for separating *what to retrieve* from *how to compose the retrieved into working memory.*
- **"Memory Matters More: Event-Centric Memory as a Logic Map"** — reframes memory as an event graph rather than a document store.
- **EverMemOS** — a self-organizing memory OS for structured long-horizon reasoning (referenced across multiple survey papers).

**Sources:**
- [Mem0 — State of AI Agent Memory 2026 (benchmark report)](https://mem0.ai/blog/state-of-ai-agent-memory-2026) `[analysis]`
- [arXiv — Beyond RAG for Agent Memory: Retrieval by Decoupling and Aggregation](https://arxiv.org/pdf/2602.02007) `[primary]`
- [arXiv — Continuum Memory Architectures for Long-Horizon LLM Agents (Jan 2026)](https://arxiv.org/html/2601.09913v1) `[primary]`
- [arXiv — Toward a Theory of Hierarchical Memory for Language Agents](https://arxiv.org/pdf/2603.21564) `[primary]`
- [arXiv — MemTrace: Probing What Final Accuracy Misses in Long-Term Memory](https://arxiv.org/pdf/2606.17328) `[primary]`
- [arXiv — MAGMA: A Multi-Graph based Agentic Memory Architecture for AI Agents](https://arxiv.org/html/2601.03236v2) `[primary]`
- [Memory Papers — AI Memory Research, Explained (curated list)](https://memorypapers.org/) `[aggregator]`
- [GitHub — Shichun-Liu/Agent-Memory-Paper-List (survey list)](https://github.com/Shichun-Liu/Agent-Memory-Paper-List) `[aggregator]`

### Why it matters to you

- **Job lens:** Memory is the *interview question of Q3 2026.* Two concrete phrasings you should be ready for: (1) *"When would you choose CMA over RAG in a production agent?"* — good answer: when the agent runs a long-horizon multi-session workflow with structured entity relationships (customer support, code-repo maintenance, ops on-call), not when you're doing one-shot Q&A over docs. (2) *"How would you evaluate agent memory in production?"* — reference **LoCoMo** and **MemTrace** (the "probing what final accuracy misses" paper), not just "we look at task success."
- **Startup lens:** If you're building an agent product with retention across sessions, the **cheap win** is going in this order: (a) name/adopt one of the CMA/MAGMA-style frames explicitly (users like knowing "our agent has *event memory*"), (b) instrument LoCoMo-style eval on your own workflow, (c) publish the eval numbers. The last step is the moat — very few competitors publish eval numbers, and buyers/investors will read that as depth.
- **Insight:** Long-context (2M Gemini) and CMA memory are **not the same solution to the same problem** — long-context scales the *window*, CMA scales the *lifetime*. Products that need "the model remembers me across weeks" don't get solved by a bigger context, and the deeper cost curve rewards CMA.

### Weekend read (choose one)

- **If you're an application-layer builder:** [Beyond RAG for Agent Memory](https://arxiv.org/pdf/2602.02007) — 20-min read, directly applicable.
- **If you're preparing for MLE / research interviews:** [Toward a Theory of Hierarchical Memory for Language Agents](https://arxiv.org/pdf/2603.21564) — heavier, cited by the survey papers.
- **If you're a startup founder pre-fundraise:** [Mem0 State of AI Agent Memory 2026](https://mem0.ai/blog/state-of-ai-agent-memory-2026) — 45-min read, gives you the vendor landscape.

→ Cross-link: [2026-05-18/04 §MemReread](../2026-05-18/04-research-progress.md) — memory-guided rereading for long-context — the same thread, one step earlier.

---

## 2. Agentic reasoning benchmarks: the recurring taxonomy {#2-taxonomy}

**What's happening:** New agentic-reasoning papers now consistently cite a shared taxonomy (originally from the "Agentic Reasoning for LLMs" survey, referenced in [2026-05-22/04](../2026-05-22/04-research-progress.md)):

- **Foundational reasoning** — single-agent, tool-augmented, evaluated at one point in time.
- **Self-evolving reasoning** — agent updates its own tools, prompts, or memory across turns.
- **Collective reasoning** — multi-agent coordination and consensus.

New / notable July arXiv landings that hang off this taxonomy:

- **MLGym** — framework + benchmark for advancing AI research agents (running the agent as an *ML researcher* over ~a dozen tasks). Sits under the "self-evolving" bucket.
- **RefuteBench 2.0** — agentic evaluation focused on how well an agent handles *refutation attempts* (adversarial follow-up). Sits under "foundational."
- **AgenticPay** — multi-agent LLM negotiation with a **110+ task benchmark** for buyer-seller transactions. Sits under "collective."
- **SYMPHONY** — a *pool of different LLM agents* used inside MCTS planning to improve multi-step reasoning. Sits between "collective" and "foundational."
- **PaperBench** — evaluates whether an AI can *replicate* AI research from a paper. The most direct benchmark of the Karpathy-thread (use-Claude-to-train-Claude) capability we've been tracking since May.
- **DataSciBench** — data-science agents on structured tabular tasks.
- **EmbodiedBench** — vision-driven embodied agents.

**Sources:**
- [arXiv — From LLM Reasoning to Autonomous AI Agents: A Comprehensive Review](https://arxiv.org/pdf/2504.19678) `[primary]`
- [arXiv — MLGym: A New Framework and Benchmark for Advancing AI Research Agents](https://arxiv.org/pdf/2504.19678) `[primary]`
- [arXiv — PaperBench: Evaluating AI's Ability to Replicate AI Research](https://arxiv.org/pdf/2504.01848) `[primary]`
- [arXiv — Act As a Real Researcher: Benchmarks Evaluating Frontier LLMs in the Research Lifecycle](https://arxiv.org/pdf/2606.07462) `[primary]`
- [arXiv — Evolutionary Perspectives on the Evaluation of LLM-Based AI Agents (Survey)](https://arxiv.org/pdf/2506.11102) `[primary]`
- [GitHub — VoltAgent/awesome-ai-agent-papers (2026)](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`
- [GitHub — weitianxin/Awesome-Agentic-Reasoning](https://github.com/weitianxin/Awesome-Agentic-Reasoning) `[aggregator]`

### Why it matters to you

- **Job lens:** The three-layer taxonomy is a *concise way to describe your own work* in interviews. Concrete rewrite: instead of *"I built an agent that uses tools,"* say *"I built a foundational-reasoning agent with a supervisor-driven self-evolving loop, evaluated on RefuteBench 2.0-style adversarial follow-ups."* Same substance; much better signal.
- **Startup lens:** **PaperBench** is worth deep attention. If AI can replicate arXiv papers from method sections, the "AI does AI R&D" thread (Karpathy hire, PostTrainBench) has a concrete measurement — track PaperBench score deltas quarter-over-quarter as your "recursive-improvement" leading indicator.
- **Insight:** The industry has stabilized on **three vocabulary terms for reasoning**. If a new paper doesn't fit those three, it's telling you something novel. If it *does* fit, it's telling you which bucket has the most competitive slack right now. Currently: *self-evolving* is the least-shipped and most-cited; that's the wedge with the widest research → product gap.

→ Cross-link: [2026-05-22/04 §1 real-tool benchmarks](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) — the "evaluation moved to real tools" thread continues here, one abstraction layer up.

---

## 3. Two shorter reads worth pinning

**"Interactive Evaluation Requires a Design Science"** ([arXiv](https://arxiv.org/pdf/2605.17829)) — an argument that current agent-evaluation practice is under-engineered, and needs a design-science framework (not just more benchmarks). Useful language for interviews where the question is "how did you know your agent was actually working?" `[primary]`

**"AI-Trader: Benchmarking Autonomous Agents in Real-Time Financial Markets"** ([arXiv](https://arxiv.org/pdf/2512.10971)) — real-time financial market as an eval harness. Fintech/quant-adjacent readers should skim; the eval harness (market data as ground truth) is portable to other high-stakes decisioning domains. `[primary]`

Both are on the [VoltAgent Awesome AI Agent Papers 2026 list](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`.
