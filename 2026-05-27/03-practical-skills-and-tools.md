# Practical Skills & Tools — 2026-05-27

This is the **assembly** edition. Over the last week you've built three pieces in isolation — an Opus/Sonnet orchestration team, a Promptfoo eval suite, and a summarize-and-prune memory loop. Today they become **one artifact** that answers four interview questions and survives the **June-15 metering change (T-19).** No new tool to learn; just integration and a README.

Tags: `#playbook #portfolio #claude-code #eval #memory #cost #fde`

---

## 1. The four-skill capstone artifact — assemble + README {#1-capstone}

**The artifact:** one project — the dual-model sanitiser ([2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact)) — that now demonstrates the four skills the market repriced this month:

| Skill | The piece | From |
|---|---|---|
| **Orchestration** | Opus-4.7 planner + Sonnet-4.6 workers (+ optional Haiku guard) | [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) |
| **Eval / verification** | Versioned Promptfoo suite (tool-discovery, injection-resistance, cost ceiling) | [2026-05-25/03 §1](../2026-05-25/03-practical-skills-and-tools.md#1-promptfoo) |
| **Memory** | Summarize-and-prune loop with staleness tags + contradiction checks | [2026-05-26/03 §1](../2026-05-26/03-practical-skills-and-tools.md#1-memory-pattern) |
| **Cost** | Per-step token-by-model trace + before/after memory token delta | [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) |

**Today's work (the 10% that makes the 90% legible):**

1. **Wire them together** — the orchestrator plans, workers execute, the Promptfoo suite runs as the verification gate, the prune loop runs at each checkpoint, the cost trace logs throughout.
2. **Write the README headline paragraph:** *"How I'd wire this for a client, verify it against their real tools, manage its memory over a long task, and keep their bill predictable."* That sentence **is** the FDE / Integration / AI-assurance interview.
3. **Add three numbers:** eval pass-rate, cost-per-task (with the Opus/Sonnet split %), and the memory token-delta %. Numbers beat adjectives.
4. **Record a 30-second demo gif.**

**Why now:** **June-15 metering is T-19.** After it, subagent/parallel-session spend becomes a visible line item — so the cost-trace half of this artifact stops being a "nice extra" and becomes the *whole point.* Finishing it this week means you walk into June with the exact artifact the metering change makes valuable, instead of a surprise bill.

**Sources:**
- [Anthropic — Claude Code best practices (orchestration, subagents)](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Crunchbase News — OpenAI buys Promptfoo (why eval is strategic)](https://news.crunchbase.com/ma/data-openai-2023-2026-acquisitions-open-source-astral-promptfoo/) `[secondary]`
- [arXiv 2601.20352 — AMA (the ~80% memory token-cut to approximate)](https://arxiv.org/pdf/2601.20352) `[primary]`

### Why it matters to you

- **Job lens:** **One deep artifact > four shallow demos.** A single project that screenshots into "orchestration + eval + memory + cost, with three real numbers and a client-framed README" answers nearly every FDE/MLE/Integration question and proves you operate the 2026 stack end-to-end. This is the portfolio centerpiece — pin it.
- **Startup lens:** This artifact *is* a miniature of a real product (a reliable, cost-bounded, verified vertical agent). Building it is free validation of whether you'd enjoy — and could sell — the "Claude-for-X, done right" wedge. The README paragraph is also a **sales paragraph.**
- **Insight:** The compounding move all month was **extend one artifact with each week's most-repriced skill**, never restart. You now have the payoff: a four-skill piece built in four 1-2 hour sessions. Cadence over intensity, made concrete.

→ Cross-link: [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact) · [2026-05-25/03 §1](../2026-05-25/03-practical-skills-and-tools.md#1-promptfoo) · [2026-05-26/03 §1](../2026-05-26/03-practical-skills-and-tools.md#1-memory-pattern) · [`ACTIONS.md`](../ACTIONS.md).
