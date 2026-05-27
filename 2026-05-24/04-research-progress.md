# Research Progress — 2026-05-24

The weekend's research read is the one with the most direct line to your **deploy-time cost**: **test-time scaling for general agents.** Pre-training scaling laws are a lab problem; *inference-time* scaling — how much reasoning, how many tool calls, how many retries an agent should spend per task — is the knob *you* turn in production. The paper studies how to spend that budget well, and it sits inside the "agents that do research" cluster ([`02` §1](./02-new-emerging.md#1-agents-as-researchers)) that's forecasting the labs' next hiring wave.

Tags: `#research #test-time-compute #agents #cost #benchmarks #arxiv`

---

## 1. Test-Time Scaling of General LLM Agents — the cost knob you control {#1-test-time-scaling}

**What it is:** A benchmark/study of **how general LLM agents should spend inference-time compute** — planning depth, number of tool calls, retries, parallel attempts — when operating **under uncertain, evolving conditions** (i.e., real tasks, not static QA). The core question: given a fixed per-task budget, what's the *allocation* of test-time compute that maximizes success?

Why this is the practically important one of the cluster:

- **Pre-training scaling** is a lab decision you'll never make. **Test-time scaling is a deploy decision you make constantly** — every "let it think longer" or "give it three tries" or "add a verification pass" is a test-time-compute choice that trades **cost for reliability.**
- It connects two threads this archive keeps returning to: the **agent-team cost lever** ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) (which *model* in which seat) and **verification** ([2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)) (a verification pass *is* spending test-time compute on reliability).

**The sibling benchmarks** (the rest of the cluster — [`02` §1](./02-new-emerging.md#1-agents-as-researchers)): **PostTrainBench** (agents automate post-training, [2026-05-23/04 §1](../2026-05-23/04-research-progress.md#1-posttrainbench)) and **InnovatorBench** (agents conduct innovative research). All three frame the agent's competence as **"what can it do per unit of compute,"** not "what can it do at all."

**Sources:**
- [arXiv 2602.18998 — Benchmark Test-Time Scaling of General LLM Agents](https://arxiv.org/html/2602.18998v1) `[primary]`
- [arXiv 2603.08640 — PostTrainBench](https://arxiv.org/abs/2603.08640) `[primary]`
- [arXiv 2510.27598 — InnovatorBench](https://arxiv.org/pdf/2510.27598) `[primary]`

### Why it matters to you

- **Job lens:** "I tuned test-time compute — reasoning depth, retry budget, when to add a verification pass — to hit a target success rate at a target cost" is a **senior-sounding, FDE/MLE-grade** sentence, and this paper gives you the vocabulary to say it precisely. Add a small "success-vs-cost curve" to your dual-model artifact ([2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact)) and you've operationalized the paper.
- **Startup lens:** Test-time-compute allocation **is your unit economics.** For any agent product, the question "how much compute per task to hit acceptable reliability" *is* the gross-margin question. A tool that **auto-tunes test-time budget per task type** (spend more on hard tasks, less on easy ones) is a real cost-optimization wedge — adjacent to the model-router idea in your backlog.
- **Insight:** The frontier of "intelligence" is quietly becoming the frontier of **"intelligence per dollar."** Every benchmark this week prices capability *per unit of compute.* Orient your skill and product bets toward **efficiency**, not raw capability — efficiency is where the durable, defensible engineering lives once the models themselves are commoditized.

→ Cross-link: [2026-05-22/03 §1 the agent-team cost lever](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [2026-05-23/04 §1 PostTrainBench](../2026-05-23/04-research-progress.md#1-posttrainbench) · [`02` §1 the forming research-agent category](./02-new-emerging.md#1-agents-as-researchers).
