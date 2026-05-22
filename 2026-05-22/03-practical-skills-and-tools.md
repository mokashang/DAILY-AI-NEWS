# Practical Skills & Tools — 2026-05-22

Act-on-it-today. Yesterday's edition set up the **orchestration stack** (CLAUDE.md + subagents + MCP + hooks). Today's is the **economics of running it**: with the June-15 Agent SDK metering **T-minus 24 days**, the single highest-leverage skill is **choosing which model does which job** inside an agent team — and a reliability loop that keeps a cheap-model team from going off the rails. Both are concrete and doable tonight.

Tags: `#playbook #claude-code #subagents #cost #orchestration #agents #portfolio`

---

## 1. The agent-team cost lever: Opus orchestrator + Sonnet workers (~40% cheaper) {#1-agent-team-cost}

The mental model from [2026-05-21/03](../2026-05-21/03-practical-skills-and-tools.md#1-orchestration): **a main agent owns planning + integration; bounded specialist subagents do the work.** The 2026 refinement is about *which model* sits in each seat:

**The lever:** an agent team with **one Opus-4.7 orchestrator + four Sonnet-4.6 workers** costs **~40% less than five Opus agents** — for most multi-step tasks, with little quality loss, because the expensive reasoning is concentrated in the *planner*, and the workers execute bounded, well-specified subtasks.

| Seat | Model | Why |
|---|---|---|
| **Orchestrator / planner** | Opus 4.7 | Owns the plan, integration, and judgment calls — where reasoning quality pays for itself |
| **Workers (review, tests, codegen, QA)** | Sonnet 4.6 | Bounded, well-scoped subtasks; cheaper per token, fast, parallelizable |
| **Verifier / guard (optional)** | Haiku 4.5 | Always-on checks (cf. the TrajAD verifier pattern, [2026-05-19/04](../2026-05-19/04-research-progress.md)) — cheap enough to run continuously |

**The reliability primitive that makes a cheap team safe — plan-first, then annotate:**
1. Ask the orchestrator to **draft a plan with *no implementation yet*.**
2. Open the plan in your editor, **annotate every spot it got wrong.**
3. Send it back with exactly: **"address all notes, don't implement yet."**
4. Only after the plan is right do you let the (cheaper) workers execute.

This is the production workflow that keeps a Sonnet-worker team from amplifying a bad plan at scale — the cheaper your executors, the more the *plan* has to be right before they run.

**Other levers from the same playbooks:** the `claude agents` **agent-view dashboard** (dispatch + monitor background sessions from one screen); subagents defined in **YAML** (custom prompt + scoped tools + independent permissions); **agent teams** for dependent work (e.g., API change → test update → consolidated PR, orchestrator sequencing the hand-offs).

**Sources:**
- [CloudZero — Claude Code agents in 2026: agent view, subagents, teams, and what parallel sessions actually cost](https://www.cloudzero.com/blog/claude-code-agents/) `[analysis]`
- [Tembo — Claude Code subagents: a 2026 practical guide](https://www.tembo.io/blog/claude-code-subagents) `[analysis]`
- [Developers Digest — Claude Code agent teams, subagents & MCP: the 2026 playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) `[analysis]`
- [Anthropic — Claude Code best practices (official docs)](https://code.claude.com/docs/en/best-practices) `[primary]`

### Why it matters to you

- **Job lens:** *"I architected an agent team — Opus planner, Sonnet workers, Haiku verifier — and cut task cost ~40% while holding quality"* is a far stronger line than "I used Claude Code." It's literally the FDE/Integration job: wire the agent into real work **and keep the client's bill predictable.** Pair it with a per-step cost table (below) and you have a portfolio artifact that screenshots beautifully.
- **Startup lens:** Model-routing-within-a-team **is** the margin lever for any "Claude-for-X" product. Your COGS is tokens; your gross margin is "how much of the work can a cheaper model do without quality loss." Build the muscle on your own projects now — it's the same skill that decides whether a vertical-agent startup is profitable.
- **Insight:** **June 15 metering (T-24) prices exactly this.** Subagents and parallel sessions multiply spend; the metering change makes that spend a line item. The people who treated "which model in which seat" as a real engineering decision *before* June 15 will look like they planned ahead; everyone else gets a surprise bill. Be the former.

---

## 2. This weekend's artifact: reframe the safety project around real-tool verification + cost {#2-artifact}

You already have the **dual-model "sanitiser"** safety project queued ([2026-05-20/05 §3](../2026-05-20/05-career-and-startup.md#3-safety-project)). Don't build a *new* thing — **upgrade the framing** so one artifact answers three interview questions:

1. **Orchestration:** Opus planner + Sonnet workers + a Haiku guard (the §1 team).
2. **Verification against *real* tools:** evaluate it the way [MCP-Atlas / Tool Decathlon](./04-research-progress.md#1-real-tool-benchmarks) do — run the agent against **one real MCP server** (not a mock), and show it discovering/using the tool correctly *and* refusing an injected malicious instruction.
3. **Cost:** log **tokens per step, by model**, and produce a small table — "what this task cost, and how the Opus/Sonnet split saved ~X%."

**Write (30 min):** a README section — *"How I'd wire this for a client, verify it against their real systems, and keep their bill predictable."* That single sentence is the FDE/Solutions/assurance interview in one line — and it lands on the **pre-deployment-evaluation** vocabulary the (delayed) EO will eventually demand ([`01` §1](./01-big-lab-moves.md#1-eo-postponed)).

→ Cross-link: [2026-05-21/03 §2 the orchestration artifact](../2026-05-21/03-practical-skills-and-tools.md#2-artifact) · [`04` §1 real-tool benchmarks](./04-research-progress.md#1-real-tool-benchmarks) · [`ACTIONS.md`](../ACTIONS.md).
