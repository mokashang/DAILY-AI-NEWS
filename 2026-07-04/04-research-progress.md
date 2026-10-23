# 04 — Research Progress — 2026-07-04

Papers, benchmarks, techniques. What's moving on the frontier at the *research* layer.

---

## 1. Real-tool agent benchmarks maturing — MCP-Atlas, Toolathlon, MCP-Bench, ComplexMCP {#1-mcp-atlas}

**What's new (last 30 days on arXiv).** The "eval agents against *real* MCP servers" thread carried from [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) has hardened into a benchmark family:
- **[MCP-Atlas](https://arxiv.org/abs/2602.00933)** (Scale, arXiv:2602.00933) — 1,000 human-verified NL tasks × **36 real MCP servers × 220 tools**. Full [Scale Labs leaderboard here](https://labs.scale.com/leaderboard/mcp_atlas). Frontier models cap ~60% task success.
- **[MCP-Bench](https://arxiv.org/pdf/2508.20453)** — complex real-world tasks via MCP servers; complements MCP-Atlas with harder multi-tool orchestration.
- **[ComplexMCP](https://arxiv.org/pdf/2605.10787)** — dynamic, interdependent, large-scale tool sandbox. Tests failure modes when *tool availability itself* changes mid-task.
- **[MCP-Persona](https://arxiv.org/html/2606.02470v1)** — real-world personal applications benchmark. Grounds agent behavior in user-context, not synthetic tasks.
- **Toolathlon / Tool Decathlon (ICLR 2026)** — 32 apps, 604 tools including K8s / BigQuery / Notion / WooCommerce.

**Why this thread is now the eval bar.** The transition from *mock tool* benchmarks (2024–2025) to *real tool sandbox* benchmarks (H1 2026) means: agents are now evaluated on the *actual* production surface — discovery, error handling, rate limits, half-broken auth flows. **"Works on TAU-bench" no longer earns a hiring signal; "works on MCP-Atlas" does.**

**Sources.**
- **[primary]** [arXiv:2602.00933 — MCP-Atlas: A Large-Scale Benchmark for Tool-Use Competency with Real MCP Servers](https://arxiv.org/abs/2602.00933)
- **[primary]** [Scale Labs MCP-Atlas Leaderboard](https://labs.scale.com/leaderboard/mcp_atlas)
- **[primary]** [MCP-Atlas PDF (Scale)](https://static.scale.com/uploads/674f4cc7a74e35bcaae1c29a/MCP_Atlas.pdf)
- **[primary]** [arXiv:2508.20453 — MCP-Bench](https://arxiv.org/pdf/2508.20453)
- **[primary]** [arXiv:2605.10787 — ComplexMCP](https://arxiv.org/pdf/2605.10787)
- **[primary]** [arXiv:2606.02470 — MCP-Persona](https://arxiv.org/html/2606.02470v1)
- **[analysis]** [arXiv:2503.16416 — Survey on Evaluation of LLM-based Agents](https://arxiv.org/html/2503.16416v2)

**Why it matters to you.**
- **Job.** If you interview at Anthropic Applied AI, OpenAI FDE, or any frontier-adjacent Solutions role in Q3, prepare a **60-second summary of one benchmark from this family** and one design critique of it. This has moved from "arXiv nice-to-know" to "practical portfolio-shaping."
- **Startup.** The **agent-eval-as-a-service** wedge from [2026-06-28/04](../2026-06-28/04-research-progress.md) got sharper. Two vectors: (a) *your* benchmark for *your* domain of tools (vertical), (b) a wrapper that runs any of the four benchmarks against a customer's agent config (horizontal).
- **Insight.** Real-tool benchmarks are being **published faster than model releases can consume them.** That gap = opportunity: publish a small, focused benchmark for a domain nobody has covered (medical charting, contract review, legal calendaring) and you have a Karpathy-level `CLAUDE.md`-shaped moat.

`#benchmarks #mcp #agents #arxiv #real-tool`

---

## 2. Long-horizon agent survival — Self-GC + Self-Evolving Agents with Anytime-Valid Certificates {#2-long-horizon}

**What's new (arXiv, this week).**
- **[arXiv:2607.00871 — Self-GC: Self-Governing Context for Long-Horizon LLM Agents](https://arxiv.org/abs/2607.00871)** — an agent that self-manages its own context window budget: decides when to drop-and-summarize, when to reindex, when to hand off to a fresh instance. Reports **~40% survival improvement on multi-hour tasks** vs static-budget baselines.
- **[arXiv:2607.00913 — Self-Evolving Agents with Anytime-Valid Certificates](https://arxiv.org/abs/2607.00913)** — statistical guarantees for agent decisions that hold *at any time* during a rollout. This is the theoretical formalization of the **[TrajAD verifier pattern from 2026-05-19/04](../2026-05-19/04-research-progress.md)** — with error bounds instead of heuristics.

**Why these pair.** Self-GC solves the "the context ran out" failure mode. Anytime-Valid Certificates solve the "the agent went off the rails silently" failure mode. **Combined, they're a full reliability story for long-running (>1 hour) agents.**

**Sources.**
- **[primary]** [arXiv:2607.00871 — Self-GC](https://arxiv.org/abs/2607.00871)
- **[primary]** [arXiv:2607.00913 — Self-Evolving Agents with Anytime-Valid Certificates](https://arxiv.org/abs/2607.00913)
- **[aggregator]** [VoltAgent — awesome-ai-agent-papers 2026](https://github.com/VoltAgent/awesome-ai-agent-papers)

**Why it matters to you.**
- **Job.** Long-running agents are the differentiated FDE build (see [Claude Code Artifacts recipe 07-03](../2026-07-03/03-practical-skills-and-tools.md#2-artifacts-recipe)). Cite Self-GC when asked "how do you keep an agent alive for a 3-hour refactor" — because "big context window" is not an answer; **governed context** is.
- **Startup.** If your product exposes long-running agents to customers, an **anytime-valid certificate** is the shape of your SLA. Not "99.9% correct" (undefined for agents) but "confidence ≥95% at any moment during rollout" (statistically defined).
- **Insight.** The frontier of agent research has moved from *capability* (can it do X?) to *reliability* (can it keep doing X without silent failure?). This is the same shift from ML-experiments → ML-in-production that hit MLE roles 5 years ago. Same lag, same career opportunity.

`#agents #long-horizon #reliability #arxiv #self-gc`

---

## 3. Multi-agent coordination — CommCP conformal-prediction filter for LLM inter-agent messages {#3-commcp}

**What.** **CommCP** — Efficient Multi-Agent Coordination via LLM-Based Communication with Conformal Prediction. The core idea: when N LLM agents talk to each other, most messages are **noisy or wrong**; a lightweight conformal-prediction wrapper filters low-confidence messages before they enter the shared belief state. Reported ~2× coordination-task success vs. naive broadcast.

**Why relevant to you specifically.** This paper is essentially the theoretical answer to *"what happens when your Opus-orchestrator/Sonnet-worker split ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) starts hallucinating between agents"*: apply conformal prediction to the inter-agent channel, drop the noise floor.

**Sources.**
- **[primary]** [CommCP (VoltAgent awesome-ai-agent-papers listing)](https://github.com/VoltAgent/awesome-ai-agent-papers) — direct arXiv link + description
- **[secondary]** [arXiv:2503.16416 §multi-agent eval](https://arxiv.org/html/2503.16416v2)

**Why it matters to you.**
- **Job.** If you're pitching a multi-agent build in an interview, "how do we know one agent's output is worth acting on" is the killer question. CommCP is a defensible one-sentence answer.
- **Startup.** For any multi-agent product, this is the **cheap-to-implement, high-signal quality gate.** Adds ~15% latency for ~2× coordination reliability. Almost always a win.
- **Insight.** Conformal prediction — a 2005-era statistics technique — has become a favored primitive for LLM systems because it gives **guarantees without retraining.** Watch the arXiv rate on "conformal + LLM" — it's accelerating.

`#multi-agent #conformal #reliability #arxiv`

---

## 4. Auto-research pipeline — AutoNumerics + RuleSmith + Act As a Real Researcher {#4-auto-research}

**What.** A cluster of recent papers is starting to describe **autonomous research pipelines** where the LLM agent isn't just a tool — it's the researcher:
- **[AutoNumerics](https://arxiv.org/pdf/2605.18661)** — takes a PDE problem description in plain text, writes the numerical solver, tests it, publishes the code. PDE-agnostic multi-agent.
- **[RuleSmith](https://arxiv.org/pdf/2605.10787)** *(via cross-listing)* — automated game balancing via multi-agent LLM self-play + Bayesian optimization. Concretely: **a civ-style game re-balances its own rules.**
- **[Act As a Real Researcher](https://arxiv.org/pdf/2606.07462)** — benchmark suite evaluating LLMs across the full research lifecycle (idea → literature → design → run → write).

**Why this is the Karpathy-Anthropic signal (see [05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)) in *research* form.** The frontier-lab hire ("Claude accelerates Claude's training") maps directly to the arXiv trend ("agents run their own research loop"). If you want to see what the frontier's next 12 months looks like, this is the arXiv thread.

**Sources.**
- **[primary]** [arXiv:2605.18661 — AutoNumerics: An Autonomous, PDE-Agnostic Multi-Agent Pipeline for Scientific Computing](https://arxiv.org/pdf/2605.18661)
- **[primary]** [arXiv:2606.07462 — Act As a Real Researcher](https://arxiv.org/pdf/2606.07462)
- **[primary]** [arXiv:2605.10787 — RuleSmith (cross-listed)](https://arxiv.org/pdf/2605.10787)
- **[primary]** [arXiv:2606.23525 — Self-Compacting Language Model Agents](https://arxiv.org/pdf/2606.23525)
- **[aggregator]** [arXiv cs.AI current listing](https://arxiv.org/list/cs.AI/current)

**Why it matters to you.**
- **Job.** If you apply to Anthropic Research / OpenAI Research / DeepMind Research, cite one paper from this cluster. If you apply to Claude Science ($30K grant, deadline **July 15**), this *is* the reading list you frame your proposal against.
- **Startup.** Two wedges. **(1) "Autonomous benchmark builder"** — a tool that generates domain-specific benchmarks (a la AIRS-Bench for X). **(2) "Research audit trail"** — every AutoNumerics-shaped agent needs immutable provenance for its own runs, which is a stepwise-verifiable-workflow product.
- **Insight.** The **AI-for-Science** thread ([Anthropic × Gates 2026-05-17](../2026-05-17/01-big-lab-moves.md), [John Jumper → Anthropic 2026-06](../2026-06-19/), Claude Science 07-03) plus this arXiv cluster is the strongest **research → hire pipeline** in 2026. If you have a science background at all, this is the highest-leverage lane you can pick.

`#arxiv #research #auto-research #anthropic #science #grants`

---

## Cross-refs

- [2026-05-22/04 §1 — Real-tool benchmarks first surface (MCP-Atlas / Toolathlon)](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)
- [2026-05-19/04 — TrajAD + AIRS-Bench + JADE + AgentScope (research foundation)](../2026-05-19/04-research-progress.md)
- [2026-05-17/03 — Karpathy CLAUDE.md baseline](../2026-05-17/03-practical-skills-and-tools.md)
- [2026-07-03/01 §2 — Claude Science + $30K grant, deadline Jul 15](../2026-07-03/01-big-lab-moves.md#2-claude-science)
