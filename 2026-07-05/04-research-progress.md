# 04 — Research Progress — 2026-07-05

Sunday, so a light research file — one paper worth flagging plus a reminder about the arXiv threads carried in from the past week. The bigger point today: **the agent-eval literature is settling into three consistent themes**, and knowing them by name is the highest-ROI interview prep for Monday's applications.

---

## 1. "Efficient Benchmarking of AI Agents" — mid-difficulty task filter for cheaper eval (arXiv:2603.23749) {#1-efficient-bench}

**What the paper argues.** Evaluating agents on comprehensive benchmarks is expensive; the paper studies whether **small task subsets can preserve agent rankings at substantially lower cost.**

**Method.** 8 benchmarks × 33 agent scaffolds × 70+ model configurations.

**Findings.**
- **Absolute score prediction degrades under distribution shift** — you can't reliably predict an agent's raw score on a full benchmark from a subset when the underlying scaffolds or models shift.
- **Rank-order prediction remains stable** — you can reliably tell agent A > agent B on a subset, even when you can't tell exactly what score each one would get on the full benchmark.
- The **mid-range difficulty filter** — dropping trivially easy and hopelessly hard tasks, keeping only the middle band — **reduces evaluation tasks by 44–70%** while maintaining high rank fidelity under scaffold and temporal shifts.

**Sources.**
- **[primary]** [arXiv 2603.23749 — Efficient Benchmarking of AI Agents](https://arxiv.org/abs/2603.23749)
- **[primary]** [arXiv 2603.23749 — PDF](https://arxiv.org/pdf/2603.23749)

**Why it matters to you.**
- **Job.** Agent evaluation is one of the highest-paying skill niches right now. Referencing this paper by name — specifically the **rank-preserving mid-difficulty filter** — in an interview about "how would you set up eval for this agent system" is a very strong signal. Says you're current on the frontier of a scarce skill.
- **Startup.** The 44–70% cost reduction on agent eval is a real primitive for a wedge: **"we run your regression benchmark 3× cheaper by picking the right task subset."** Small but real business against the deep-agent-eval companies that focus on observability, not benchmark selection.
- **Insight.** The paper's honest finding — **absolute scores unreliable, ranks stable** — is the deeper takeaway. Every "our agent scored 87.3% on X-Bench" launch claim should be read with suspicion. What holds up is **relative ranking**. Ask for head-to-head numbers, not standalone scores.

`#research #arxiv #agents #eval #benchmarks`

---

## 2. Three consistent themes in the current agent-eval literature {#2-three-themes}

**Sunday synthesis: what to name in interviews.**

| Theme | Named in the recent literature | Career vocabulary |
|---|---|---|
| **Real-tool eval** (not mock tools) | [MCP-Atlas](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) · [Tool Decathlon / Toolathlon](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) | "Production-tool benchmarking" |
| **Cost-efficient eval** (subset selection, rank preservation) | [Efficient Benchmarking of AI Agents (2603.23749)](https://arxiv.org/abs/2603.23749) | "Rank-fidelity eval design" |
| **Harness-level, not model-level** eval | [Agentic Harness Engineering (2604.25850)](https://arxiv.org/abs/2604.25850) · [Holistic Agent Leaderboard (2510.11977)](https://arxiv.org/abs/2510.11977) · [Act As a Real Researcher (2606.07462)](https://arxiv.org/abs/2606.07462) | "Harness engineering / observability-driven scaffold evolution" |

**Why it matters to you.**
- **Job.** These three themes are the current agent-eval JD vocabulary at Anthropic, Sierra, Judgment Labs, and the Big-4 AI-assurance practices. Naming them fluently is a top-1% interview signal — most candidates still talk about "prompt engineering" and "model choice," which now reads as backwards-facing.
- **Startup.** The **infra layer** — Holistic Agent Leaderboard style, shared benchmarks that everyone compares against — is the ImageNet-for-agents category. Whoever ships the equivalent for MCP-backed agents wins a durable position. Small window.
- **Insight.** All three themes point at the same shift: **agent quality is measured at the harness level, not the model level.** Design your portfolio to demonstrate **harness quality**, not model choice.

`#research #agents #eval #vocabulary`

---

## 3. Carried threads

- [LLM-Agent benchmarks survey (arXiv 2507.21504)](../2026-07-03/04-research-progress.md#1-agent-eval-survey) from 2026-07-03 — read this week, cite 3 benchmarks per gap.
- [SciAgentArena](../2026-06-28/04-research-progress.md) — the science-agent eval substrate to cite in the Claude Science grant proposal.
- [AutoResearchBench](../2026-07-03/04-research-progress.md#3-autoresearch) — same grant application citation.

`#research #carried`
