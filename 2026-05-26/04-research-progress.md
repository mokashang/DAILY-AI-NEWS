# Research Progress — 2026-05-26

Yesterday's survey named the problem (no agent masters all four memory competencies, [2026-05-25/04 §1](../2026-05-25/04-research-progress.md#1-memory-survey)). Today's papers attack it from a surprising angle: **don't make one agent's memory smarter — coordinate memory *across* agents.** Two results — **AMA** and **MemMA** — show that multi-agent memory coordination both improves quality *and* cuts tokens ~80%, which makes memory a **cost lever, not just a reliability one.**

Tags: `#research #memory #multi-agent #self-evolution #cost #arxiv`

---

## 1. Multi-agent memory — AMA and MemMA (and the ~80% token cut) {#1-multi-agent-memory}

**AMA — Adaptive Memory via Multi-Agent Collaboration:** instead of one agent hoarding context, **multiple agents collaboratively construct and curate a shared memory**, adaptively deciding what to keep. The reported result is the eye-catching one: it **outperforms state-of-the-art baselines while reducing token consumption ~80% vs. full-context** methods. The insight: **full-context is wasteful**; a curated, collaboratively-maintained memory captures the signal at a fraction of the tokens.

**MemMA — Coordinating the Memory Cycle through Multi-Agent Reasoning and In-Situ Self-Evolution:** jointly coordinates **memory construction *and* iterative retrieval**, and — the clever part — **converts utilization failures into direct repair signals for the memory bank.** When the agent retrieves something useless, that failure is fed back to *fix the memory*, so the store **self-improves in situ** rather than just growing. This is layer-2 "self-evolving" reasoning ([2026-05-22/04 §2](../2026-05-22/04-research-progress.md#2-agentic-reasoning-survey)) applied specifically to memory.

Together with the survey's verdict that **selective forgetting** is the weakest competency, the through-line is clear: the frontier of agent memory is **curation and repair** (what to keep, what to drop, how to fix the store from its own failures) — not raw storage capacity.

**Sources:**
- [arXiv 2601.20352 — AMA: Adaptive Memory via Multi-Agent Collaboration](https://arxiv.org/pdf/2601.20352) `[primary]`
- [arXiv 2603.18718 — MemMA: Coordinating the Memory Cycle through Multi-Agent Reasoning and In-Situ Self-Evolution](https://arxiv.org/pdf/2603.18718) `[primary]`
- [arXiv 2603.07670 — Memory for Autonomous LLM Agents (the survey this answers)](https://arxiv.org/abs/2603.07670) `[primary]`

### Why it matters to you

- **Job lens:** The ~80% token-cut result is a **cost-and-reliability two-fer** — exactly the kind of finding you should be able to cite *and* approximate in your own work. "I applied the AMA/MemMA insight — curate-and-repair memory instead of full-context — and cut tokens ~X%" connects your portfolio to current research, which is rare in a candidate and disproportionately credible.
- **Startup lens:** The **"failures become repair signals"** idea (MemMA) is a genuinely defensible product mechanic: a memory system that **gets better the more it's used wrong** has a data-compounding moat (every misfire improves it). That's a layer-2 self-evolving wedge — the kind the [2026-05-22/04 §2](../2026-05-22/04-research-progress.md#2-agentic-reasoning-survey) taxonomy says is under-built and durable.
- **Insight:** Note the recurring 2026 shape: the big wins come from **coordination and curation**, not bigger single components. Multi-agent memory beats single-agent full-context; an Opus-planner/Sonnet-worker team beats all-Opus; summarize-and-prune beats infinite context. **The architecture is the alpha** — orient your skills toward *designing the system*, not tuning the model.

→ Cross-link: [2026-05-25/04 §1 the memory survey / four competencies](../2026-05-25/04-research-progress.md#1-memory-survey) · [2026-05-22/04 §2 layer-2 self-evolving reasoning](../2026-05-22/04-research-progress.md#2-agentic-reasoning-survey) · [`03` §1 the practical pattern](./03-practical-skills-and-tools.md#1-memory-pattern).
