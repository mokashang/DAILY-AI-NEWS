# Research Progress — 2026-06-11

The May-22 thread — *the eval bar moved from mock tools to your actual stack* — is consolidating into a category this week. Four papers worth your time: **ToolMisuseBench** (offline-deterministic, scores *misuse* and *recovery* not just success), **MCPVerse** (real-world MCP servers at scale), **Test-Time Scaling of General LLM Agents** (when does more inference compute help?), and **"Agents Learn Their Runtime"** (interpreter persistence as training-time semantics — a quiet but deep idea). Plus one **survey** (Externalization in LLM Agents) that's the best single read this month.

Tags: `#arxiv #benchmarks #agents #tool-use #mcp #test-time-compute #memory #research`

---

## 1. Real-tool agent benchmarks consolidate — ToolMisuseBench, MCPVerse, Toolathlon, MCP-Atlas {#1-real-tool-evals}

**What happened:** Four benchmarks are now stable enough to use as reference evals. Together they triangulate **what "agent quality" empirically means** in 2026:

- **ToolMisuseBench** ([arXiv 2604.01508](https://arxiv.org/pdf/2604.01508)) — *offline-deterministic*. The novelty: it doesn't just score tool *success*; it scores **tool misuse and recovery**. An agent that invokes the wrong tool, notices, and recovers is rewarded. An agent that produces the right answer for the wrong reason is *penalised*. This is the closest thing to a production-fidelity eval today.
- **MCPVerse** ([arXiv 2508.16260](https://arxiv.org/html/2508.16260v2)) — large-scale, real-world MCP servers. Pairs with [MCP-Atlas (Scale, 2026-05-22)](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks). Together they cover the "discover-then-call" and "compose-across-services" axes.
- **Benchmark Test-Time Scaling of General LLM Agents** ([arXiv 2602.18998](https://arxiv.org/html/2602.18998v1)) — the question is no longer "does test-time compute help" but **"on which axes, and at what marginal cost?"**. Headline finding: scaling test-time compute helps **planning** and **error-recovery** materially more than it helps **direct execution**.
- **The Evolution of Tool Use in LLM Agents** ([arXiv 2603.22862](https://arxiv.org/pdf/2603.22862)) — survey-style: single-tool → multi-tool orchestration trajectory; includes a useful **MCP-Bench** subset for cross-comparison.

**Sources:**
- [arXiv 2604.01508 — ToolMisuseBench](https://arxiv.org/pdf/2604.01508) `[primary]`
- [arXiv 2508.16260v2 — MCPVerse](https://arxiv.org/html/2508.16260v2) `[primary]`
- [arXiv 2602.18998v1 — Test-Time Scaling of General LLM Agents](https://arxiv.org/html/2602.18998v1) `[primary]`
- [arXiv 2603.22862 — Evolution of Tool Use in LLM Agents](https://arxiv.org/pdf/2603.22862) `[primary]`

### Why it matters to you

- **Job lens:** Cite **ToolMisuseBench** in *exactly one place* in your portfolio README and you signal you understand the shift from "did it work" to "did it work *for the right reason, and can it recover when it didn't*." That distinction is the difference between a hire-able Solutions/FDE candidate and a "she used Claude in a project" applicant. Pair it with the Fable-5 router from [`03` §1](./03-practical-skills-and-tools.md#1-fable-5-router) and the dual-runtime MCP server from [`03` §2](./03-practical-skills-and-tools.md#2-codex-mcp): *one portfolio answers six interview questions*.
- **Startup lens:** **Recovery scoring is a wedge.** Most enterprise-AI procurement RFPs still ask "what's the accuracy on benchmark X?". The first vendor that responds with **"here's our misuse-and-recovery score, here's our reasoning under partial failure"** wins the trust deal. If your wedge in [STARTUPS.md](../STARTUPS.md) is anywhere near agent-orchestration, this is the language that converts.
- **Insight:** The whole eval category is moving **from accuracy → from accuracy *and* recovery → toward calibrated uncertainty**. Watch for the next paper that adds **per-step refusal/abstention scoring** to the recovery axis — that's the third leg, and it will land in the next 3–6 months. Calibration was the thread two months ago (Appier "Answer, Refuse, or Guess?", 2026-05-14); we're about to see it merged into the recovery line.

→ Cross-link: [2026-05-22/04 §1 MCP-Atlas / Toolathlon (the real-tool benchmark wave starts)](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) · [2026-05-14 Appier calibration](../2026-05-14/04-research-progress.md).

---

## 2. "Agents Learn Their Runtime" — interpreter persistence as training-time semantics {#2-agents-learn-runtime}

**What happened:** [arXiv 2603.01209 — Agents Learn Their Runtime: Interpreter Persistence as Training-Time Semantics](https://arxiv.org/pdf/2603.01209). Underrated paper.

**The idea (1-line):** When an agent's tool-use trajectory includes a *persistent interpreter* (a long-lived Python session, a stateful Jupyter kernel, a Postgres-with-temporary-tables), the *agent learns the runtime as part of its semantics* — i.e., the model's mental model of the world includes "variables persist between cells." Without persistence, the model trains itself to *re-derive state from scratch every call*, which is wasteful and brittle.

**Why this is deep:** It reframes the **runtime architecture** as a **training-time choice**, not a deployment-time afterthought. The right way to build a code-execution agent is to **make persistence visible to the model** from training, not patch it in via prompt-engineering at inference.

**Sources:**
- [arXiv 2603.01209 — Agents Learn Their Runtime](https://arxiv.org/pdf/2603.01209) `[primary]`

### Why it matters to you

- **Job lens:** *"The runtime is part of the model's semantics; persistence at inference doesn't help if the model wasn't trained against persistence"* — that one sentence in a Claude Code / Codex / agent-runtime interview signals you read past the headline. It's exactly the depth-of-understanding gap that separates SDE/MLE candidates from "AI Engineer" candidates in 2026.
- **Startup lens:** If you're building any **stateful agent** wedge (a coding agent that remembers your codebase between sessions, a research agent with a persistent workspace), this paper says: **train against the runtime, don't patch around it**. That informs whether you build on top of an existing API or eventually post-train a model. For most founders the answer is the former, but the *reason* now has a citation.
- **Insight:** Tie this back to **Karpathy's pre-training-automation team** ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)). The frontier-leverage move is "use the model to accelerate building the model." A runtime that the model has *trained against* is exactly the kind of artifact that compounds across iterations — it's the architectural complement to the recursive-self-improvement work.

---

## 3. Survey worth a Saturday morning — "Externalization in LLM Agents" {#3-externalization-survey}

**What happened:** [arXiv 2604.08224 — Externalization in LLM Agents: A Unified Review of Memory, Skills, Protocols and Harness Engineering](https://arxiv.org/pdf/2604.08224). The most useful single-read of June, especially if you're new to the agent stack or trying to consolidate your mental model after 18 months of fragmented papers.

**Why useful:** Surveys often re-tell stories you already know. This one **proposes a unified taxonomy** — memory, skills, protocols (MCP / tool schemas), and harness engineering — and **maps every major 2024–2026 paper onto it**. It's the cheapest 90-minute interview-prep read of the quarter.

**Sources:**
- [arXiv 2604.08224 — Externalization in LLM Agents](https://arxiv.org/pdf/2604.08224) `[primary]`

### Why it matters to you

- **Job lens:** Read it once; build a 5-bullet *taxonomy reference card* on a single page of your portfolio README. When asked "how do you think about agent architecture?" in an interview, your answer becomes structured (the four legs) instead of anecdotal — instant credibility.
- **Startup lens:** Use the taxonomy to *map your wedge to the gap.* If your wedge is in "skills" (reusable agent procedures) and most funded competition is in "memory," you have a defensible niche. Run the exercise this weekend on the top 5 entries in [STARTUPS.md](../STARTUPS.md).
- **Insight:** Whenever a field consolidates a taxonomy survey, the *next* breakout work usually comes from the intersection of two of its legs — e.g., **skills × harness** (skill cards that the harness can compose and revoke) was the under-explored cell in the 2024–25 literature, and it's exactly where the May-19 [Multimodal Procedural Knowledge](../2026-05-18/04-research-progress.md) paper landed. Use the taxonomy to *predict* the next interesting paper, not just to summarize the past.

---

## 4. Honorable mentions — what to glance at, not deep-read

- **Survey on Evaluation of LLM-based Agents** ([arXiv 2503.16416](https://arxiv.org/pdf/2503.16416)) — the older but most-cited evaluation survey; still a good reference if you're new to the eval literature.
- **In-depth Survey of LLM-based AI Agents** ([arXiv 2309.14365](https://arxiv.org/pdf/2309.14365)) — historical context; useful for "how we got here" framing in a cover letter.

→ Cross-link: [`03` §1 Fable 5 router (use these benchmarks to validate it)](./03-practical-skills-and-tools.md#1-fable-5-router) · [`03` §3 visible-safeguards eval harness (this is the recovery-scoring axis applied to safety)](./03-practical-skills-and-tools.md#3-visible-safeguards).
