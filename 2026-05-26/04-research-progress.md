# Research Progress — 2026-05-26

The week's research throughline — *agents reasoning against reality* — reaches the **science** domain. A pair of benchmarks, **PaperArena** and **CLAIM-BENCH**, test whether an agent can **use tools to reason over real scientific literature** and trace a **claim back to its evidence.** It's the same demo-vs-deployment bar as [05-25's TerminalWorld/AI-Trader/HAL](../2026-05-25/04-research-progress.md#1-benchmarks) and [05-24's agent-memory-as-a-system](../2026-05-24/04-research-progress.md#1-memory-synthesis) threads — applied to the highest-stakes form of reasoning: deciding what's actually *supported.*

Tags: `#research #agents #benchmarks #science #grounding #arxiv`

---

## 1. PaperArena + CLAIM-BENCH — agents that reason over real literature {#1-paperarena}

**What they are:**
- **PaperArena** — a benchmark for **tool-augmented agentic reasoning over scientific papers**: the agent must use tools (search, retrieval, parsing) to answer questions spanning *real* papers, not a curated snippet. It measures whether an agent can **navigate and synthesize a literature**, not just summarize a passage.
- **CLAIM-BENCH** — evaluates **claim → evidence reasoning**: given a claim, can the model locate and correctly weigh supporting (or contradicting) evidence? This is the core competency behind trustworthy research assistance — and behind the **per-claim eval** wedge ([JADE, 2026-05-19/04 §2](../2026-05-19/04-research-progress.md#2-jade)).

Together they extend the real-tool theme into science: it's not enough to *reason* — the agent has to **ground each conclusion in retrievable evidence.** That's the missing piece that turns "fluent" into "trustworthy."

**Sources:**
- [arXiv cs.CL (recent listings)](https://arxiv.org/list/cs.CL/recent) `[primary]`
- [arXiv cs.AI (recent listings)](https://arxiv.org/list/cs.AI/recent) `[primary]`

> Confidence: **MEDIUM.** These are active recent benchmark threads, but arXiv listing pages blocked direct fetch, so exact IDs/dates aren't pinned. Treat the *capabilities measured* (literature-scale tool use; claim→evidence grounding) as the durable point; verify the specific paper/ID before citing a number in an interview.

### Why it matters to you

- **Job lens:** "Claim→evidence grounding" and "literature-scale agentic retrieval" are precise, current talking points for any role touching **research assistants, production RAG, or trustworthy AI** — and they map to the institution-backed **trust-&-safety / responsible-AI lane** that [05-25's encyclical](../2026-05-25/01-big-lab-moves.md#1-encyclical) just legitimized. An assurance engineer's job is partly "show me the evidence this output is grounded in."
- **Startup lens:** **Evidence-grounded reasoning** is the trust layer that vertical-AI in regulated domains (legal, medical, finance) *must* have — and it's hard, which makes it defensible. A harness that scores a customer's agent on claim→evidence fidelity is the [JADE/Judgment-Labs](../2026-05-19/04-research-progress.md#2-jade) wedge with a science-grade benchmark to anchor it. Note this is one of the two **hot seed themes** ([`05` §2](./05-career-and-startup.md#2-seed-premium)): agentic *retrieval*.
- **Insight:** The frontier of *useful* AI is increasingly about **grounding, not generation.** Models produce fluent claims trivially; the value — and the research action — is in *verifying* those claims against retrievable reality. Every domain (code, science, law) is converging on the same realization. Bet your reading and projects on the grounding/verification layer.

→ Cross-link: [2026-05-19/04 §2 JADE per-claim eval](../2026-05-19/04-research-progress.md#2-jade) · [2026-05-25/04 §1 reality-fleeing benchmarks](../2026-05-25/04-research-progress.md#1-benchmarks) · [2026-05-24/04 §1 trustworthy memory as a precondition](../2026-05-24/04-research-progress.md#1-memory-synthesis).

---

## 2. The week's research arc, in one line {#2-arc}

Five days, one shape. **Math milestone** ([2026-05-23/04](../2026-05-23/04-research-progress.md#1-math-milestone)): can a *general* model produce verified discovery? **Memory-as-a-system** ([2026-05-24/04](../2026-05-24/04-research-progress.md#1-memory-synthesis)): can agents *remember* trustworthily? **Reality-fleeing benchmarks** ([2026-05-25/04](../2026-05-25/04-research-progress.md#1-benchmarks)): can agents do *real* work (TerminalWorld, AI-Trader, HAL)? **PaperArena/CLAIM-BENCH** (today): can agents *ground* conclusions in evidence?

The common denominator: **the research center of gravity has moved off raw capability and onto reliability, memory, grounding, and trust** — the interface between a capable model and the messy real world.

### Why it matters to you
- **Job lens:** This is your reading list *and* your positioning — every item is the "reliability side" of the model, which is the side being hired and paid for.
- **Startup lens:** Each is a wedge (verified discovery, trustworthy memory, real-tool eval, evidence-grounding). The base model is the commodity; the reality-interface is the business.
- **Insight:** When a week of unrelated papers all describe the same gap, that's the field telling you where the next two years of value live. **Build on the reality-interface, not the reasoning core.**

→ Cross-link: [2026-05-23/04 §1 the math milestone](../2026-05-23/04-research-progress.md#1-math-milestone) · [2026-05-24/04 §1 memory synthesis](../2026-05-24/04-research-progress.md#1-memory-synthesis) · [2026-05-25/04 §1 benchmarks](../2026-05-25/04-research-progress.md#1-benchmarks).
