# 04 — Research Progress — 2026-10-06

Agent memory went from folklore to first-class architectural layer this quarter. Three benchmarks, three research threads, one taxonomy — all converging into "memory is a job description now."

---

## 1. Memory benchmarks consolidate — LoCoMo / LongMemEval / BEAM {#1-memory-benchmarks}

**What's new**
- Three memory benchmarks are now the **de facto evaluation triad** for agent memory architectures: **LoCoMo** (long-horizon conversations), **LongMemEval** (long-context + retrieval), **BEAM** (benchmarking episodic agent memory). Different memory architectures are directly comparable on the same evaluation set — first time this has been possible.
- A **unified taxonomy** has emerged from the recent surveys:
  - **By what memory stores:** `factual` / `experiential` / `working`.
  - **By how memory is realized:** `token-level` (context-window / retrieved snippets) / `parametric` (weight updates, fine-tuning) / `latent` (persistent embeddings, external memory stores).
- The **"hardest open problems"** named across surveys: **cross-session identity, temporal abstraction at scale, memory staleness**.

**Key papers to read this week**
- *A Survey of Agent Memory in the Second Half: Towards Self-Evolving and Long-Horizon Agents* — arXiv 2602.06052 [primary]
- *Memory for Autonomous LLM Agents: Mechanisms, Evaluation, and Emerging Frontiers* — arXiv 2603.07670 [primary]
- *Memory in the Age of AI Agents* — arXiv 2512.13564 (carried from 2026-09-10) [primary]
- *Exploring Cross-Scenario Generality of Agentic Memory Systems: Diagnostics and a Strong Baseline* — arXiv 2606.04315 [primary]
- *IterResearch* — maintains a working-set workspace preserving only the evolving report and immediate results to prevent context suffocation.
- *MirrorMind* — hierarchical architecture retrieving specific cognitive styles and knowledge bases; simulates collective-intelligence patterns.
- *Chain-of-memory* — lightweight memory construction with dynamic evolution for LLM agents.

**Sources**
- [A Survey of Agent Memory in the Second Half — arXiv 2602.06052](https://arxiv.org/pdf/2602.06052) [primary]
- [Memory for Autonomous LLM Agents — arXiv 2603.07670 (alphaxiv)](https://www.alphaxiv.org/abs/2603.07670) [primary]
- [Memory in the Age of AI Agents — HF Papers 2512.13564](https://huggingface.co/papers/2512.13564) [primary]
- [Cross-Scenario Generality of Agentic Memory Systems — arXiv 2606.04315](https://arxiv.org/pdf/2606.04315) [primary]
- [State of AI Agent Memory 2026 — mem0](https://mem0.ai/blog/state-of-ai-agent-memory-2026) [analysis]
- [Research Papers on Agent Memory — agentic-ai.readthedocs.io](https://agentic-ai.readthedocs.io/en/latest/AgentMemory/research-papers/) [aggregator]

**Why it matters to you**
- **Job:** "**Agent-memory engineer**" is appearing in frontier-lab and agentic-startup JDs as a sub-specialty of AI Engineering. The pitch: **you can design, build, and evaluate a memory layer** (not just "I use pgvector"). An artifact that runs a published agent over LoCoMo and reports results is a near-automatic phone-screen pass.
- **Startup:** The **memory layer is now a startup-able primitive** (mem0, Letta/MemGPT, Zep, EverMemOS, EVER-m, Chroma's agent-memory extension). The market is **not yet concentrated** — niche opportunities around: temporal reasoning (what happened when?), identity reconciliation (who said what across sessions?), redaction/forgetting at scale (GDPR right-to-forget for agents). Any of these three is a founder-fit wedge for a technical CS grad.
- **Insight:** **Memory is where the moat moves next.** 2024's moat: scale. 2025's moat: tool-use. 2026's moat: **memory + reasoning over time**. The reason: context windows got to 1M+ tokens and plateaued; the next asymmetry is which agents can **remember productively** across days, weeks, months. This is also where the Chinese room / "is this agent coherent?" question becomes an engineering problem rather than a philosophical one.

→ Cross-link: [2026-09-10 realtime+memory arxiv](../2026-09-10/04-research-progress.md#1-realtime-memory) · [2026-05-10 Mem0 + EverMemOS](../2026-05-10/04-research-progress.md)

**Tags:** `#research #memory #benchmarks #locomo #longmemeval #beam #agents`

---

## 2. Secondary research threads from Q3 (not re-expanded)

- **Real-tool agent benchmarks (from 2026-05-22):** MCP-Atlas, Tool Decathlon / Toolathlon — now joined by the memory triad above. The 2026 eval stack = real-tool + memory, not just task-success.
- **Agentic Reasoning survey (from 2026-05-22):** three-layer taxonomy — foundational / self-evolving / collective — still the useful mental model. Argon's "long-horizon" push is a collective-reasoning capability bet.
- **Live-benchmark wave (from 2026-05-21):** LemmaBench, RepoReason, PostTrainBench. Live benchmarks keep arriving; the news is **not** any single new one — it's that **"benchmarks become stale within 90 days"** is now the norm.
- **"Real-Time Reasoning Agents in Evolving Environments" (from 2026-09-10):** arXiv 2511.04898. Pair-read with the memory triad for the "lifelong agent" picture.
- **On-Policy Distillation sweep (from 2026-05-10, 05-12):** has entered the "mature technique" zone — in deployment at labs, no longer novel research. The follow-on: **continual distillation during inference** (watch for papers on this).

---

## 3. What to read vs skim this week

| Priority | Paper | Read vs Skim |
|---|---|---|
| **P0** | *Memory for Autonomous LLM Agents — Mechanisms, Evaluation, Emerging Frontiers* (2603.07670) | **Read** |
| **P0** | *A Survey of Agent Memory in the Second Half* (2602.06052) | **Read** |
| **P1** | *Memory in the Age of AI Agents* (2512.13564) | Skim |
| **P1** | IterResearch methodology paper | Skim |
| **P2** | MirrorMind | Skim |
| **P2** | Chain-of-memory | Skim |

Pair with practical artifact: **run a published open-source memory system over LoCoMo on your laptop this week.** The research is only valuable if you've touched it.

**Tags:** `#reading-list #arxiv #memory`
