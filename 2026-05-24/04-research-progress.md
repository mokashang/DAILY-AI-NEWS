# Research Progress — 2026-05-24 (Sunday)

arXiv papers, benchmarks, breakthroughs — weekend synthesis + one paper to read.

---

## 1. 2026 is the year agent *memory* became a system (and a precondition) {#1-memory-synthesis}

**The arc.** The "agent memory" thread (tracked since 2026-05-10's Mem0/EverMemOS note and 2026-05-18's *Storage Is Not Memory*) has consolidated into a **distinct subfield with its own surveys, systems, and threat model.** Memory is no longer "a vector store next to the LLM" — it's a **system with four requirements**:

1. **Mechanisms + in-session evaluation** — *Memory for Autonomous LLM Agents* (arXiv **2603.07670**): five mechanism families; benchmarks shift from *static recall* to **multi-session, decision-interleaved** tests.
2. **Coherence across agents** — *Multi-Agent Memory from a Computer Architecture Perspective* (arXiv **2603.10062**): hierarchy / coherence / bandwidth, borrowed from CPU memory design.
3. **Verifiability** — *PolarMem* (arXiv **2602.00415**) + *VerificAgent*: memory must be **grounded and checkable**, not just retrievable.
4. **Security** — *A Survey on the Security of Long-Term Memory in LLM Agents: Toward Mnemonic Sovereignty* (arXiv **2604.16548**): memory is **malleable, rewritable, socially propagating** → **poisoning is a named attack surface** with a lifecycle threat framework.

**Why this is the connective tissue.** The SaaSpocalypse ([`02` §1](./02-new-emerging.md#1-saaspocalypse)) asks enterprises to **replace systems of record** with agent workflows. You cannot rip out the database of truth unless the replacement's memory is **trustworthy, auditable, coherent, and poison-resistant.** Memory-as-a-system research is literally the *precondition* for the migration trade. It also pairs with yesterday's "verification of AI-generated output is the scarce skill" lesson from the math milestone + eval-convergence pieces ([2026-05-23/04 §1–2](../2026-05-23/04-research-progress.md#1-math-milestone)). Storage ≠ recall ≠ memory.

- **Sources:** [arXiv 2603.07670](https://arxiv.org/abs/2603.07670) `[primary]` · [arXiv 2603.10062](https://arxiv.org/abs/2603.10062) `[primary]` · [arXiv 2602.00415 — PolarMem](https://arxiv.org/pdf/2602.00415) `[primary]` · [arXiv 2604.16548 — memory security](https://arxiv.org/abs/2604.16548) `[primary]` · [VoltAgent — awesome-ai-agent-papers (2026 index)](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`

**Why it matters to you.**
- **Job:** "Design the memory layer for an enterprise agent + its threat model" is a high-signal interview prompt. The four-requirement frame is your structured answer.
- **Startup:** **Verifiable, audit-grade, poison-resistant agent memory** is the under-built infra layer the migration thesis demands. Pairs with the control-plane wedge in [STARTUPS.md](../STARTUPS.md).
- **Insight:** Watch whether **Mem0 / EverMemOS / Cognee / LangMem** adopt PolarMem-style verifiable grounding and the 2604.16548 threat model as standard features.

`#research #memory #agents #arxiv #verification #security`

---

## 2. Reasoning *stability* as a measured dimension — ReasonBench (+ one paper to read) {#2-read}

**What happened.** **ReasonBench** benchmarks **11 reasoning methods across 4 models and 7 tasks** with statistically reliable numbers, foregrounding **reproducibility / (in)stability** as a first-class metric rather than single-run leaderboard scores — complementing the contamination-resistant live-benchmark wave (LemmaBench / RepoReason / PostTrainBench) and yesterday's **test-time-scaling + single-vs-multi-agent** convergence ([2026-05-23/04 §2](../2026-05-23/04-research-progress.md#2-eval-convergence)). The field is converging on *"is the score real, and would it hold on a re-run?"*

- **Sources:** [arXiv 2512.07795 — ReasonBench](https://arxiv.org/pdf/2512.07795) `[primary]` · [Survey on Evaluation of LLM-based Agents (arXiv 2503.16416)](https://arxiv.org/html/2503.16416v2) `[primary]`

**One paper to read this week (~45 min):** **"A Survey on the Security of Long-Term Memory in LLM Agents"** (arXiv **2604.16548**). Take one paragraph of notes on the **memory-lifecycle threat framework** and post a single LinkedIn/X takeaway tying it to the SaaSpocalypse — *"you can't replace a system of record with an agent whose memory can be poisoned."* It's the least-crowded angle and the one most tied to enterprise trust; earning the right to use the vocabulary in interviews is the point.

**Why it matters to you.**
- **Job:** Evaluation design — *stability, contamination-resistance, real-tool, memory-security* — is the scarce, repriced-up skill. "I report variance, not just pass@1" is a credibility marker.
- **Insight:** As models reach parity ([`01` §2](./01-big-lab-moves.md#2-google-war)), *measurement* becomes the differentiator. Eval-as-a-service stays a fundable category.

`#research #benchmarks #evaluation #reasoning #memory #security #arxiv`

---

### Cross-links
- The migration trade memory enables: [`02` §1](./02-new-emerging.md#1-saaspocalypse)
- Yesterday's verification lesson (math milestone + eval convergence): [2026-05-23/04](../2026-05-23/04-research-progress.md#1-math-milestone)
- Prior thread — *Storage Is Not Memory*: [2026-05-18/04](../2026-05-18/04-research-progress.md)
