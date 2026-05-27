# Research Progress — 2026-05-25

Today's read is the bottleneck nobody markets but everybody hits: **agent memory.** A new survey ("Memory for Autonomous LLM Agents") maps the field and lands a sobering verdict — **no current system masters all four memory competencies, and most fail conspicuously on *selective forgetting.*** If you've ever watched an agent confidently use stale context or drown in its own history, this paper names why. And an unsolved, universal bottleneck is exactly what you want to point a wedge at.

Tags: `#research #memory #agents #evaluation #arxiv`

---

## 1. "Memory for Autonomous LLM Agents" — the four competencies, and the one everyone fails {#1-memory-survey}

**What it is:** A survey of memory mechanisms for autonomous LLM agents — spanning **simple context-based and RAG systems through agents with external memory modules and tool integration** — plus a unifying **four-competency framework** for *evaluating* agent memory:

1. **Accurate Retrieval** — pull the correct snippet for a query.
2. **Test-Time Learning** — incorporate new information mid-task.
3. **Long-Range Understanding** — reason over a long, multi-session history.
4. **Selective Forgetting** — *discard* what's stale, wrong, or irrelevant.

**The headline finding:** **no current system masters all four**, and **most fail conspicuously on selective forgetting** — agents are far better at *remembering* than at *deciding what to drop.* The field has also shifted its *evaluation* from static recall benchmarks to **multi-session agentic tests that interleave memory with decision-making** — i.e., memory is now graded by whether it helps the agent *act*, not whether it can recite.

Adjacent work in the same window pushes on the multi-agent angle — **AMA (Adaptive Memory via Multi-Agent Collaboration)** reports outperforming baselines while **cutting token consumption ~80% vs. full-context**, and **MemMA** coordinates memory construction + retrieval, turning utilization failures into repair signals (detailed in [2026-05-26/04](../2026-05-26/04-research-progress.md) once it lands).

**Sources:**
- [arXiv 2603.07670 — Memory for Autonomous LLM Agents: Mechanisms, Evaluation, and Emerging Frontiers](https://arxiv.org/abs/2603.07670) `[primary]`
- [arXiv 2602.11243 — Evaluating Memory Structure in LLM Agents](https://arxiv.org/pdf/2602.11243) `[primary]`
- [arXiv 2601.20352 — AMA: Adaptive Memory via Multi-Agent Collaboration (~80% token reduction)](https://arxiv.org/pdf/2601.20352) `[primary]`

### Why it matters to you

- **Job lens:** Memory is the single most common reason a slick agent demo fails in production — so "I understand the four memory competencies and that **selective forgetting** is the weak link" is a deployment-credible thing to say in an FDE/MLE interview. Bonus: the **~80% token cut** from adaptive memory ties straight to your cost-control narrative (better memory = fewer tokens = cheaper agent).
- **Startup lens:** **"Selective forgetting" is an open, universal wedge.** Everyone's building retrieval (competency 1); almost nobody's solving *forgetting* (competency 4). A product/library that gives agents principled forgetting — staleness detection, contradiction pruning, relevance decay — addresses a bottleneck *every* agent product hits, and it's the kind of substrate a frontier lab would rather buy than build ([2026-05-23/02 §1](../2026-05-23/02-new-emerging.md#1-consolidation)).
- **Insight:** The reliability frontier moved from **reasoning** to **memory.** We largely solved "can it think?"; the live question is "can it manage what it knows over time?" Bet your attention on the bottleneck that's *currently* breaking deployments — and right now that's memory, specifically the discipline of forgetting.

→ Cross-link: [2026-05-24/04 §1 test-time compute (the sibling efficiency lever)](../2026-05-24/04-research-progress.md#1-test-time-scaling) · [2026-05-22/04 §2 the agentic-reasoning taxonomy (memory = layer-2 self-evolving)](../2026-05-22/04-research-progress.md#2-agentic-reasoning-survey) · [`02` §1 the wedge angle](./02-new-emerging.md#1-openai-devtools).
