# Practical Skills & Tools — 2026-05-23

Act-on-it-today, Saturday edition. The last two days set up the **agent team** (CLAUDE.md + subagents + MCP + hooks, [2026-05-21/03](../2026-05-21/03-practical-skills-and-tools.md)) and its **cost economics** (Opus-planner / Sonnet-workers, [2026-05-22/03](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)). Today's lever is the one that makes all of that **reusable and shippable: Claude Agent Skills.** A Skill is the unit that packages a workflow so Claude invokes it automatically — and, crucially for you, it's a **portfolio artifact you can publish.** This is a weekend you can spend turning the project you've been queuing into a *Skill*, not just a script.

Tags: `#playbook #claude-code #skills #agents #mcp #portfolio #cost`

---

## 1. Claude Agent Skills — the SKILL.md unit, and why it's the leverage now {#1-claude-skills}

**The mental model:** a **Skill** is a folder containing a **`SKILL.md`** (instructions + *when to trigger*) plus optional supporting files — templates, examples, helper scripts, data, images. Claude **reads the files, runs the scripts, and uses the contents to do real work.** Skills are now described as one of the **most-used features in Claude Code**, with Anthropic's own team running *hundreds* internally — they've moved from experimental to **production infrastructure.**

The handful of authoring rules that actually matter (from the practitioner write-ups):

| Rule | Why it matters |
|---|---|
| **The `description` is a *trigger*, not a summary** | Write *"use this skill when you need to X"* — not *"this skill does X."* Claude matches on the trigger to decide whether to load the Skill. A vague description = a Skill that never fires. |
| **Start small** | One Skill, one job. Build the smallest useful version, then grow it. |
| **Capture the first failure in a "gotchas" section** | The moment it goes wrong, write down why. That note is what makes the Skill reliable on run #2. |
| **Add one script that automates something annoying** | A Skill that *runs* a helper script beats one that only *describes* a process. |
| **Mind the context window** | Skills load into context; keep `SKILL.md` lean and push detail into files Claude opens *only when needed*. Performance degrades as context fills. |

How Skills relate to the rest of the stack you've built this week:
- **Subagents** (`.claude/agents/`) = *who* does the work (isolated context, scoped tools).
- **Skills** (`SKILL.md`) = *how* a recurring job gets done, packaged so it's invoked automatically.
- **MCP servers** = *what real tools* the work touches.
- **Hooks** = *guardrails* around all of it.

A Skill is the thing that makes your orchestration **repeatable and shareable** instead of a one-off prompt you re-type.

**Sources:**
- [Anthropic — Skill authoring best practices (official docs)](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) `[primary]`
- [Anthropic — Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Nimbalyst — Claude Code Skills: a practical 2026 guide](https://nimbalyst.com/blog/claude-code-skills-guide/) `[analysis]`
- [Medium (Tahir) — 9 tips for building Claude Agent Skills](https://medium.com/@tahirbalarabe2/9-tips-for-building-claude-agent-skills-3bca85c47a26) `[analysis]`
- [Knightli — 24 Claude Code tips: plan mode, rewind, CLAUDE.md, skills, agents, plugins](https://www.knightli.com/en/2026/05/08/claude-code-24-tips-plan-rewind-skills-agents/) `[analysis]`

### Why it matters to you

- **Job lens:** *"I packaged my agent workflow as a reusable Claude Skill — triggerable description, helper script, gotchas section, tested on N cases"* is a **concretely senior** thing to say. It shows you build *systems*, not prompts. It's also the literal FDE/Integration deliverable: clients don't want a clever chat, they want a **repeatable, hand-offable capability** — which is exactly what a Skill is.
- **Startup lens:** Skills are a **distribution surface.** A public, well-triggered Skill that solves a real workflow is discoverable and forkable — it's the AI-native equivalent of a popular open-source utility, and it's a top-of-funnel for a "Claude-for-X" product. The Skill *is* the demo *and* the lead-gen.
- **Insight:** The unit of value in agentic work is moving from **"a good prompt"** → **"a good Skill."** A prompt is consumed once; a Skill **compounds** (it gets reused, refined via its gotchas section, and shared). Invest your weekend building *Skills*, not prompts — same effort, durable asset.

---

## 2. This weekend's artifact: ship your project *as a Skill* (don't build a new thing) {#2-artifact}

You already have the **dual-model "sanitiser" / MCP mini-agent** queued ([2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact), and on today's [`ACTIONS.md`](../ACTIONS.md)). **Don't start over — repackage it as a publishable Claude Skill** so it's the artifact *and* the distribution:

1. **`SKILL.md` with a trigger description** — *"Use this skill when you need to run an agent against a real MCP server and verify it refuses injected instructions while logging per-step cost."* (Trigger, not summary.)
2. **One helper script** — the cost-logger that emits the **tokens-per-step, by-model** table (the Opus-planner / Sonnet-worker split from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)).
3. **A `gotchas.md`** — the first thing that broke when you ran it against a *real* MCP server (cite the MCP-Atlas / Toolathlon framing, [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)). This section is what makes it look *used*, not demoed.
4. **A 5-case eval** — discovers/uses the tool correctly (3 cases) + refuses an injected malicious instruction (2 cases).
5. **README one-liner:** *"How I'd wire this for a client, verify it against their real systems, keep the bill predictable — packaged so they can re-run it."*

That single Skill now answers **four** interview questions — orchestration, real-tool verification, cost-control, **and reusability/hand-off** — and it doubles as a [Workday × Anthropic Solopreneurship Accelerator](../2026-05-19/05-career-and-startup.md#5-workday-solopreneur) application asset (today's [`ACTIONS.md`](../ACTIONS.md) item).

**Sources:**
- [Anthropic — Skill authoring best practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) `[primary]`
- [Medium (unicodeveloper) — 10 must-have skills for Claude (and any coding agent) in 2026](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) `[analysis]`

### Why it matters to you

- **Job lens:** One weekend, one artifact, four interview answers, plus a program application — that's the **cadence-over-intensity** rule from [`ME.md`](../ME.md) working for you.
- **Startup lens:** A published Skill is a **zero-cost customer-discovery probe** — watch who forks/stars it; those are your first user conversations.
- **Insight:** Reframing beats rebuilding. You don't need a *new* project this weekend — you need the one you have **packaged so its value compounds.** Skill-ify what you already built.

→ Cross-link: [2026-05-22/03 §2 the same project, pre-Skill framing](../2026-05-22/03-practical-skills-and-tools.md#2-artifact) · [`05` §2 weekend execution plan](./05-career-and-startup.md#2-weekend-execution) · [`ACTIONS.md`](../ACTIONS.md).
