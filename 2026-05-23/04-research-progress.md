# Research Progress — 2026-05-23

One paper this weekend, but it's the **measurement layer under the week's biggest talent move.** When Karpathy joined Anthropic to build a "use Claude to accelerate Claude's training" team ([2026-05-22 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)), the obvious question was: *how would you even know if an agent is good at that?* **PostTrainBench** is the benchmark that asks exactly that — **can LLM agents automate LLM post-training, under a real compute budget?** Reading it is the cheapest way to sound credible about the recursive-self-improvement thread that's driving frontier hiring right now.

Tags: `#research #benchmarks #post-training #agents #self-improvement #arxiv`

---

## 1. PostTrainBench — can LLM agents automate LLM post-training? {#1-posttrainbench}

**What it is:** A benchmark evaluating how well **LLM agents can carry out the post-training of *other* LLMs autonomously** — i.e., the agent is handed the meta-task of improving a model (data curation, fine-tuning choices, eval, iteration) and must do it **under bounded compute constraints.** The "bounded compute" framing is what makes it realistic: in the real world, the constraint on automating ML research isn't whether an agent *can* run an experiment, but whether it can **spend a fixed GPU budget wisely** across many experiments.

This is the **layer-2 "self-evolving"** corner of the agentic-reasoning taxonomy ([2026-05-22/04 §2](../2026-05-22/04-research-progress.md#2-agentic-reasoning-survey)) made measurable — and it sits next to a small cluster of "agents-doing-ML-research" benchmarks (InnovatorBench, the test-time-scaling-of-agents work) that all appeared in the same window. The field is racing to *measure* the thing the labs are racing to *staff.*

**Sources:**
- [arXiv 2603.08640 — PostTrainBench: Can LLM Agents Automate LLM Post-Training?](https://arxiv.org/abs/2603.08640) `[primary]`
- [arXiv 2510.27598 — InnovatorBench: Evaluating Agents' Ability to Conduct Innovative LLM Research](https://arxiv.org/pdf/2510.27598) `[primary]`
- [arXiv 2602.18998 — Benchmark Test-Time Scaling of General LLM Agents](https://arxiv.org/html/2602.18998v1) `[primary]`

### Why it matters to you

- **Job lens:** This benchmark *is* the job Karpathy was hired to do, made legible. If you reference it correctly in an Anthropic/research-adjacent interview — "the pre-training-automation direction is the production form of what PostTrainBench measures: agents spending a bounded compute budget on post-training, not just running one experiment" — you've shown you read past the headline. That single sentence separates you from the applicant flood the Karpathy hire just created.
- **Startup lens:** "Bounded-compute" is the wedge word. The defensible products under "AI does ML R&D" aren't the agents themselves (the labs build those in-house) — they're the **experiment-orchestration, compute-budgeting, and eval/verification layers** that make a research-agent *cost-effective*. Same pattern as everywhere this month: the value is in **making the agent's spend predictable and its output verifiable**, not in the agent.
- **Insight:** Watch the **benchmark-precedes-product** rhythm. A capability gets a benchmark *just before* it gets industrialized — MCP-Atlas/Toolathlon preceded real-tool agents, PostTrainBench precedes self-improving training pipelines. Benchmarks are the **leading indicator of where the labs are about to hire**; read the new ones as a job-market forecast, not just as research.

→ Cross-link: [2026-05-22 §3 Karpathy / Claude-trains-Claude — the production form](../2026-05-22/01-big-lab-moves.md#3-karpathy) · [2026-05-22/04 §2 the layer-2 self-evolving taxonomy](../2026-05-22/04-research-progress.md#2-agentic-reasoning-survey) · [2026-05-21/04 §2 the live-benchmark wave](../2026-05-21/04-research-progress.md#2-benchmarks).
