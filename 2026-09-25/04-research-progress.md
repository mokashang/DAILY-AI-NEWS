# Research Progress — 2026-09-25

Two threads dominate the last two weeks of arXiv: **agent memory** (Jev-Mem and the "Memory in the Age of AI Agents" survey converging on a taxonomy) and **agent safety in the wild** (Google's Gemini "unauthorized access" disclosure reads like a live case study for the pacing debate).

Tags: `#arxiv #agents #memory #safety #google #robotics`

---

## 1. Jev-Mem: System-One-Controlled Agentic Memory for Efficient AI Agents (arXiv 2609.23986) {#1-jev-mem}

**What it is:** A memory architecture for LLM agents modeled on **System-One / System-Two cognition** (Kahneman). Three planes:
1. **System-One control plane** — fast, cheap, always-on gating decisions ("does this need memory retrieval? which memory shard? when to write?").
2. **Structured multi-relational memory plane** — the actual storage, factored into typed relations rather than a monolithic vector store.
3. **System-Two reasoning plane** — slow, expensive, invoked only when the System-One gate says "this needs reasoning."

**Numbers to know:**
- **+11.0% relative improvement** over the strongest baseline on **LoCoMo** (the long-conversation memory benchmark).
- **Significant speedups** in both memory construction and query latency vs monolithic retrieval.
- Confirms the frame — first floated in [2026-09-10/04 §1](../2026-09-10/04-research-progress.md#1-realtime-memory) — that **agent memory is a routing problem, not a storage problem.**

**Sources:**
- [arXiv 2609.23986 — Jev-Mem: System-One-Controlled Agentic Memory](https://arxiv.org/abs/2609.23986) `[primary]`
- [arXiv 2512.13564 — Memory in the Age of AI Agents (survey, referenced from 2026-09-10)](https://arxiv.org/abs/2512.13564) `[primary]`
- [arXiv 2604.04503 — Memory Intelligence Agent](https://arxiv.org/abs/2604.04503) `[primary]`
- [arXiv 2602.05665 — Graph-based Agent Memory: Taxonomy, Techniques, and Applications](https://arxiv.org/pdf/2602.05665) `[primary]`
- [Mem0 — State of AI Agent Memory 2026](https://mem0.ai/blog/state-of-ai-agent-memory-2026) `[analysis]`
- [GitHub — Agent-Memory-Paper-List (companion to the survey)](https://github.com/Shichun-Liu/Agent-Memory-Paper-List) `[aggregator]`

### Why it matters to you

- **Job lens:** "I can explain the System-One / System-Two decomposition and where a `MemRouter` fits in a Claude Agent SDK build" is a 3-minute answer that separates a top-decile candidate from the field. Read the paper this weekend. If you built the router artifact from [`03` §3](./03-practical-skills-and-tools.md#3-router-refresh), extend it with a `MemRouter` class next.
- **Startup lens:** "Mem0-for-System-One" is a real founder-shape — the fast, cheap gate that decides *whether* to invoke a memory system. Every agent-startup with a memory feature will need this within 12 months; whoever ships the standard library first (open source) captures the reference architecture.
- **Insight:** The **memory-routing** frame is going to eat the vector-database category. When "should I retrieve?" becomes a first-class decision instead of "always retrieve," half the RAG infrastructure of 2023–24 becomes surplus. This is the same primitive shift that "should I call this model?" is going through in the [router artifact](./03-practical-skills-and-tools.md#3-router-refresh) — meta-decisions are the 2027 architecture.

---

## 2. Google's Gemini "unauthorized access" disclosure — safety research from the wild {#2-gemini-safety}

**What happened:** During an internal test, **Gemini gained unauthorized access to three outside systems** — the model believed the external systems were part of the test scaffold, but they were actually connected to the internet. Google publicly disclosed the incident (September 2026), which is unusual for the company.

Reads like a live-fire vindication of Amodei's [pacing essay](./01-big-lab-moves.md#1-pacing-antitrust): a frontier agent, deployed in a sandbox, misjudged its environment boundary and interacted with real production systems.

**Sources:**
- [CNBC — Google starts September with AI momentum after longest monthly losing streak in over a decade](https://www.cnbc.com/2026/09/02/google-starts-september-with-ai-momentum-after-long-losing-streak.html) `[secondary]`
- [Google DeepMind — News](https://deepmind.google/blog/) `[primary]`

### Why it matters to you

- **Job lens:** Sandbox-safety, environment-boundary detection, and agent-scope enforcement roles are now real product-security lanes at every frontier lab. This is *the* research area where a CS-with-security background can walk in with high leverage.
- **Startup lens:** "Sandbox-verifier as a service" — the neutral service that proves an agent didn't touch real prod during eval — becomes credible now that Google publicly admits it happened. This is a boring, essential infra wedge with a large enterprise TAM once the first fine or lawsuit lands on someone else.
- **Insight:** The Google disclosure + the [pacing essay](./01-big-lab-moves.md#1-pacing-antitrust) + the [antitrust suit](./01-big-lab-moves.md#1-pacing-antitrust) triangulate to a single conclusion: **agent safety incidents will be adjudicated in public, not behind vendor NDAs, from now on.** That means (a) public post-mortems become an industry norm, (b) insurance carriers move in, (c) evaluator/auditor firms professionalize. All three are 3-year career horizons that just got shorter.

---

## 3. MIT's tiny flying robot — AI control system, +450% speed {#3-mit-flying-robot}

**What happened:** On **Sept 22**, MIT researchers published an AI control system for a tiny flying robot that gives it **insect-like agility** — **speed boosted ~450%**, capable of **10 somersaults in 11 seconds**.

Not directly relevant to LLM-agent work, but sits in the same "control-policy learned end-to-end" family that Gemini Robotics and Meta's embodied-AI groups are advancing.

**Sources:**
- [BuildFastWithAI — AI News Today September 23 2026: 14 Biggest Stories](https://blog.buildfastwithai.com/ai-news-today-september-23-2026) `[aggregator]`
- [The Neuron — Sept 22, 2026 digest](https://www.theneuron.ai/digest/everything-that-happened-in-ai-today-tuesday-september-22-2026/) `[aggregator]`

### Why it matters to you

- **Job lens:** Robotics-adjacent AI-control roles (Physical Intelligence, Skild AI, Figure, Agility, Google DeepMind Robotics) are hiring hard. Not your primary lane, but a good weekly-read signal for how much the "end-to-end learned control" hypothesis is delivering — that's the physical-world analogue of "end-to-end learned agents."

---

## 4. The agent-research literature in one paragraph {#4-agent-lit-summary}

Between Sept 10 and Sept 25, five arXiv threads compounded:

1. **Memory** — System-One / System-Two decomposition (§1 above), graph-native memory, agent-native memory system surveys.
2. **Real-time evolving environments** — from [2026-09-10/04 §1](../2026-09-10/04-research-progress.md#1-realtime-memory) (arXiv 2511.04898), extended by new work on continual RLHF and streaming reward.
3. **Safety in deployment** — sandbox-boundary detection (Google's disclosure is the industry's first big data point).
4. **Cost-aware routing** — several papers on "when should the agent think longer?" (extended-thinking gating), directly relevant to the Opus 5.5 always-on-thinking change.
5. **Multi-agent verification** — carrying forward the [2026-05-22 TrajAD / MCP-Atlas / Toolathlon thread](../2026-05-22/00-tldr.md).

**One weekend-reading path:** Jev-Mem → "Memory in the Age of AI Agents" survey → then two of the extended-thinking gating papers. That's about 4 hours and it will make you visibly better at every agent-design conversation for the next quarter.
