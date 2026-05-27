# Practical Skills & Tools — 2026-05-26

The research caught up to a pain you've already felt: agents that remember everything get expensive and confused. Today's edition turns the multi-agent-memory results ([`04` §1](./04-research-progress.md#1-multi-agent-memory)) — which report **~80% token reductions** — into a pattern you can add to your own project this afternoon, no research budget required. The trick isn't fancier retrieval; it's **disciplined forgetting.**

Tags: `#playbook #memory #cost #claude-code #agents #portfolio`

---

## 1. Give your agent memory *and* forgetting — the summarize-and-prune pattern {#1-memory-pattern}

**The problem (from [2026-05-25/04 §1](../2026-05-25/04-research-progress.md#1-memory-survey)):** agents are good at *remembering* and bad at *selective forgetting* — so context bloats, cost climbs, and stale facts poison reasoning. **The fix is a loop, not a database.**

**The pattern (add to the dual-model artifact, [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact)):**

1. **Summarize-and-prune at checkpoints.** After each completed sub-task, have a cheap model (Haiku/Sonnet) compress the working context into a short "state summary," then **drop the raw transcript.** You carry the *conclusion*, not the 4,000 tokens that produced it. (This is the subagent token-amortization idea, [2026-05-23/03 §1](../2026-05-23/03-practical-skills-and-tools.md#1-five-layer-stack), applied to memory.)
2. **Tag facts with staleness.** Store memory items with a timestamp + a "still-valid?" flag. Before reuse, cheaply re-check anything past a freshness threshold instead of trusting it blindly.
3. **Contradiction check before write.** When new info conflicts with stored memory, *resolve and overwrite* rather than appending both — appending two contradictory facts is how agents end up confidently wrong.
4. **Measure the token delta.** Log total tokens *with* vs *without* the prune loop. The research suggests big wins are available; **your number is the portfolio artifact.**

**Why this is the right level of effort:** you're not implementing a research system — you're adding a **summarize → prune → re-check** loop around context you already manage. It's an afternoon, and it produces a concrete "cut cost ~X% with principled memory" result.

**Sources:**
- [arXiv 2601.20352 — AMA: Adaptive Memory via Multi-Agent Collaboration (~80% token reduction)](https://arxiv.org/pdf/2601.20352) `[primary]`
- [arXiv 2603.18718 — MemMA: Coordinating the Memory Cycle through Multi-Agent Reasoning and In-Situ Self-Evolution](https://arxiv.org/pdf/2603.18718) `[primary]`
- [arXiv 2603.07670 — Memory for Autonomous LLM Agents (the four competencies)](https://arxiv.org/abs/2603.07670) `[primary]`

### Why it matters to you

- **Job lens:** "I added principled memory management — summarize-and-prune with staleness tags and contradiction checks — and cut agent cost ~X% while improving consistency" is a **senior-grade** sentence that hits *three* repriced skills at once: cost-control, verification, and now memory. It's the single highest-value addition to your in-flight artifact this week.
- **Startup lens:** Memory management *is* a margin lever and a reliability lever simultaneously — the rare feature that makes your product both cheaper and better. If "selective forgetting" is the open wedge ([2026-05-25/04 §1](../2026-05-25/04-research-progress.md#1-memory-survey)), building the pattern yourself is the cheapest way to learn whether it's a sellable library.
- **Insight:** The cheap, durable wins in agent engineering are almost always about **subtraction** (prune context, drop stale facts, route to a cheaper model) rather than addition (bigger context, more tools). Train the instinct to ask "what can this agent *forget*?" before "what else can it know?"

→ Cross-link: [`04` §1 the multi-agent memory results](./04-research-progress.md#1-multi-agent-memory) · [2026-05-25/04 §1 the four competencies](../2026-05-25/04-research-progress.md#1-memory-survey) · [2026-05-22/03 §1 the cost lever this stacks with](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [`ACTIONS.md`](../ACTIONS.md).
