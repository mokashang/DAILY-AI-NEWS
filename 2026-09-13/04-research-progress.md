# Research Progress — 2026-09-13

Two research threads worth pulling on this weekend, both directly load-bearing for the artifacts in [`03`](./03-practical-skills-and-tools.md). **Sakana's Fugu Technical Report is the paper of the moment** — it operationalizes orchestration as a language-modeling problem, and the Sept-11 Ultra v2 release is empirical proof it scales. **The 2026 memory-benchmark class (MemoryArena, AMA-Bench, agent-native memory)** is the other side of the same shift: research has moved from "bigger model" to "better *system around the model*" — orchestration and memory being the two biggest surfaces.

Tags: `#arxiv #agents #orchestration #memory #evals #sakana`

---

## 1. The Fugu Technical Report — orchestration as a language-modeling problem {#1-fugu-orchestration}

**The paper:** [arXiv 2606.21228 — Sakana Fugu Technical Report](https://arxiv.org/abs/2606.21228) `[primary]` (submitted Jun 19, 2026; v2 Jun 23; Ultra v2 shipped Sept 11 on the same architecture line).

**The claim in one sentence:** Fugu treats *task routing across a fixed pool of sub-models* as a language-modeling task — the Fugu orchestrator is itself an LLM trained to output structured routing decisions, and can recursively invoke instances of itself for nested subtasks.

**What's actually novel:**

1. **Recursive self-invocation.** Prior "mixture-of-agents" or "router-LLM" work stopped at "pick a sub-model, run it." Fugu can spawn a *nested Fugu* for a subtask that itself benefits from orchestration. This turns orchestration into a tree, not a flat decision.
2. **Trained routing, not prompted.** The orchestrator is fine-tuned on structured (task, sub-model, outcome) tuples — not just prompted with "here are the sub-models, pick one." This is the difference between compilers (learned optimization) and hand-tuned decision trees (heuristic).
3. **Open-weight + specialized sub-model pool.** Sakana treats each sub-model as a specialized worker — some open-weight (Llama-class), some in-house specialized (chart interpretation, math, code). The orchestrator learns which worker is best for which sub-task shape.

**The Sept-11 empirical result:** Fugu Ultra v2 = **48.3 on Chartography** vs. Opus 5 = 27.3 and Fable 5 = 29.5. First non-frontier lab to top a visual reasoning benchmark against frontier models.

**Why this is the paper of the moment:**

- If it holds under adversarial evaluation, it changes what "state of the art" *means*. The frontier moves from "who has the biggest model" to "who has the best orchestrator + sub-model pool."
- It's the research-side proof of the router thesis you're already implementing: [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) is the practitioner version; Fugu is the trained/scaled version.
- It has an OSS repo — you can read the actual routing policy and steal ideas for your own trusted-agent starter ([`03` §3](./03-practical-skills-and-tools.md#3-hardening-checklist)).

**Read this weekend (60 min):**

- Intro + method sections (20 min) — enough to understand recursive self-invocation
- Section on training data + evaluation (20 min) — enough to name-drop competently in interviews
- Skim the GitHub — read the routing policy definition + one example sub-model integration (20 min)

**Sources:**
- [arXiv 2606.21228 — Sakana Fugu Technical Report](https://arxiv.org/abs/2606.21228) `[primary]`
- [Sakana AI — Sakana Fugu (Multi-agent System as A Model)](https://sakana.ai/fugu/) `[primary]`
- [GitHub — SakanaAI/fugu](https://github.com/SakanaAI/fugu) `[primary]`
- [Pondero — Sakana AI ships Fugu Max and Fugu Ultra v2](https://pondero.ai/news/2026-09-12-sakana-fugu-max-ultra-v2/) `[analysis]`

### Why it matters to you

- **Job lens:** Read + summarize this paper in a 500-word LinkedIn or GitHub-README post this week. That single post is worth 10 job applications: it demonstrates paper-reading fluency, gets you noticed by recruiters (Sakana is hiring, so is every lab thinking about orchestration), and gives you the language to answer "what's the most interesting AI paper you've read this month" in an interview.
- **Startup lens:** The Fugu architecture is *itself* a founder wedge — see [`02` §1 startup lens](./02-new-emerging.md#1-fugu). Build the OSS orchestrator on top of commodity API models (not open-weights — you don't need to train sub-models, just orchestrate over Anthropic/OpenAI/Gemini APIs) and you have a real product with a plausible funding path.
- **Insight:** The paper's biggest quiet claim is that **language modeling generalizes to orchestration decisions.** That's a huge philosophical bet: if it holds, every "planning + tool use + routing" problem can eventually be replaced by fine-tuning a small LLM on the domain's decision data. This is the research equivalent of the "compiler eats the assembler" bet from the 1970s.

→ Cross-link: [`02` §1 Fugu emergence](./02-new-emerging.md#1-fugu) · [`03` §3 how Fugu shapes the trusted-agent starter](./03-practical-skills-and-tools.md#3-hardening-checklist).

---

## 2. The 2026 agent-memory benchmark class — MemoryArena, AMA-Bench, agent-native memory {#2-memory-benchmarks} 

**What's happening:** Through Q2–Q3 2026, a coherent research thread has emerged: **memory** is the *other* half of the "systems around the model" frontier. A few benchmarks and surveys worth knowing:

- **[arXiv 2603.07670 — Memory for Autonomous LLM Agents: Mechanisms, Evaluation, and Emerging Frontiers](https://arxiv.org/html/2603.07670v1)** — the field-defining survey. Names five mechanism families: context-resident compression, retrieval-augmented stores, reflective self-improvement, hierarchical virtual context, and policy-learned management.
- **[arXiv 2507.05257 — Evaluating Memory in LLM Agents via Incremental Multi-Turn Interactions](https://arxiv.org/abs/2507.05257)** — the standard-setting benchmark for multi-turn memory. Four core competencies: **accurate retrieval, test-time learning, long-range understanding, selective forgetting.**
- **[arXiv 2602.22769 — AMA-Bench: Evaluating Long-Horizon Memory for Agentic Applications](https://arxiv.org/html/2602.22769)** — long-horizon memory eval where later subtasks depend on what the agent learned from earlier ones.
- **[arXiv 2606.24775 — Are We Ready For An Agent-Native Memory System?](https://arxiv.org/pdf/2606.24775)** — argues for memory systems designed for agents (not retrofitted from RAG). Companion to Fugu in framing "systems around the model" as the frontier.
- **[Mem0 — State of AI Agent Memory 2026](https://mem0.ai/blog/state-of-ai-agent-memory-2026)** — the industry-side benchmark & trends report.

**The empirical picture:** current memory systems fail on at least one of the four core competencies. Selective forgetting is the hardest. Long-range understanding is the second hardest. Nobody has a general solution yet — which is the founder / research opportunity.

**Sources:**
- [arXiv 2603.07670 — Memory for Autonomous LLM Agents](https://arxiv.org/html/2603.07670v1) `[primary]`
- [arXiv 2507.05257 — Evaluating Memory in LLM Agents via Incremental Multi-Turn Interactions](https://arxiv.org/abs/2507.05257) `[primary]`
- [arXiv 2602.22769 — AMA-Bench](https://arxiv.org/html/2602.22769) `[primary]`
- [arXiv 2606.24775 — Are We Ready For An Agent-Native Memory System?](https://arxiv.org/pdf/2606.24775) `[primary]`
- [Mem0 — State of AI Agent Memory 2026: Benchmarks & Trends Report](https://mem0.ai/blog/state-of-ai-agent-memory-2026) `[analysis]`

### Why it matters to you

- **Job lens:** Memory is currently *under-hired* relative to its research importance. Every major lab has one or two memory people; the rest of the org treats it as "someone else's problem." A CS grad who ships a **memory eval suite** (see §3 below) that covers the four competencies is one of maybe 500 candidates worldwide with that portfolio piece. Extremely competitive edge for any research-adjacent role.
- **Startup lens:** "Memory-as-a-service" is a real wedge — Mem0 has already fundraised into it, but the category still has 10+ funding-shaped companies. **Selective forgetting** is the wedge where nobody has a real product yet (compliance-driven "forget everything about user X in these contexts, keep in these others"). This one intersects [`02` §2 agent trust infra](./02-new-emerging.md#2-agent-trust-funding) directly.
- **Insight:** Fugu is orchestration; the memory-benchmark class is memory. **These are the two pillars of "systems around the model."** In interviews, use that framing — it makes you sound one level up from candidates who talk about specific models.

---

## 3. Weekend eval template — extend the router with a memory eval and an orchestration eval {#3-eval-suite-template}

**What to add to your trusted-agent starter this weekend ([`03` §3](./03-practical-skills-and-tools.md#3-hardening-checklist)):**

Two new eval families beyond the base 5-case suite:

### A. Memory eval (4 cases, one per competency from arXiv 2507.05257)

| # | Test | What it measures |
|---|---|---|
| M1 | Ingest 3 facts turn 1; ask about fact 2 turn 5 | **Accurate retrieval** |
| M2 | Provide a corrected rule turn 3; check turn 8 uses corrected rule | **Test-time learning** |
| M3 | 30-turn conversation; ask about turn 2 detail | **Long-range understanding** |
| M4 | User asks agent to "forget X"; verify X does not surface later | **Selective forgetting** |

### B. Orchestration eval (3 cases, Fugu-style)

| # | Test | What it measures |
|---|---|---|
| O1 | Compound task requiring 3 sub-model calls | **Task decomposition** |
| O2 | Budget-constrained task (must complete under $0.05) | **Cost-aware routing** |
| O3 | Task that benefits from recursive orchestration | **Recursive orchestration** |

Add these to `evals/memory_suite.py` and `evals/orchestration_suite.py` alongside your base 5-case suite. Include in your PILLAR_MAP.md — memory + orchestration are load-bearing for **Trusted Context** and **Trusted Action**.

**Sources:**
- [`03` §3 the trusted-agent starter this extends](./03-practical-skills-and-tools.md#3-hardening-checklist)
- [arXiv 2507.05257 — the four memory competencies](https://arxiv.org/abs/2507.05257) `[primary]`
- [arXiv 2606.21228 — Fugu orchestration framing](https://arxiv.org/abs/2606.21228) `[primary]`
- [Mem0 — State of AI Agent Memory 2026](https://mem0.ai/blog/state-of-ai-agent-memory-2026) `[analysis]`

### Why it matters to you

- **Job lens:** A publicly-shipped 5+4+3 = 12-case eval suite covering routing, memory, and orchestration is a résumé-differentiator that most senior-hires-at-frontier-labs would still recognize as strong. It's ~200 more lines of Python on top of what you already have.
- **Insight:** The reason to build memory and orchestration evals *now* is that the research is still moving. In 6 months, one will be commoditized (probably orchestration, given Fugu is OSS-releasing). Being early on the eval side means you can *name* the regression when a new model breaks memory, which is the specific superpower that gets you into research-adjacent teams.

→ Cross-link: [`03` §3 trusted-agent starter](./03-practical-skills-and-tools.md#3-hardening-checklist) · [`05` §2 skill re-price](./05-career-and-startup.md#2-reprice).
