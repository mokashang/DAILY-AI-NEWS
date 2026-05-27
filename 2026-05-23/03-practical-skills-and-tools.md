# Practical Skills & Tools — 2026-05-23

Weekend = build day. The orchestration stack ([2026-05-21/03](../2026-05-21/03-practical-skills-and-tools.md#1-orchestration)) and the cost lever ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) are in place; the missing piece for most people is the **layer above prompting** — the five Claude Code primitives and *when to reach for each.* Get the decision rule right and your agent setup stops being a pile of prompts and starts being a system. Today's artifact: ship **one Agent Skill.**

Tags: `#playbook #claude-code #skills #mcp #hooks #subagents #portfolio`

---

## 1. The Claude Code 5-layer stack — and the one-line rule for each {#1-five-layer-stack}

The 2026 setup has **five layers**. Most people only use one or two; the leverage is in knowing which problem each solves.

| Layer | What it is | Reach for it when… |
|---|---|---|
| **CLAUDE.md** | Project rules, always loaded | The instruction must be true on **every** turn (conventions, do-nots, architecture) |
| **MCP servers** | Connections to real tools/data | The agent must **operate your actual workflow** (issue tracker, DB, browser, internal API) — not just edit files |
| **Skills** | Reusable instruction packs (`SKILL.md`) with optional resources + triggers | It's a **procedure you only need sometimes** (deploy checklist, docs refresh, eval run, debugging playbook) |
| **Hooks** | Scripts that fire on tool/session events | It's a script that should run **automatically** (tests before stop, block edits to generated files, lint before commit, security scan after dep change) |
| **Subagents** | Isolated sessions that return only a report | The work would **flood the main context** (read docs, inspect big files, compare alternatives) — 20 reads + 12 greps stay in the subagent |

**The decision rule, in one breath:** *Every-turn → CLAUDE.md. Real tools → MCP. Sometimes-procedure → Skill. Auto-run script → Hook. Context-flooding → Subagent.*

The single highest-leverage move for keeping main context small is **delegating noisy research to subagents** — they amortize tokens, so your planner sees the conclusion, not the 4,000 lines that produced it.

**Sources:**
- [Anthropic — Equipping agents for the real world with Agent Skills (official)](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) `[primary]`
- [Anthropic — Claude Code best practices (official docs)](https://code.claude.com/docs/en/best-practices) `[primary]`
- [alexop.dev — Understanding Claude Code's full stack: MCP, Skills, Subagents & Hooks explained](https://alexop.dev/posts/understanding-claude-code-full-stack/) `[analysis]`
- [Developers Digest — Claude Code agent teams, subagents & MCP: the 2026 playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) `[analysis]`
- [okhlopkov.com — My Claude Code setup: MCP servers, hooks, skills and agents (2026)](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) `[analysis]`

### Why it matters to you

- **Job lens:** "I structured CLAUDE.md / MCP / Skills / Hooks / subagents around the *right* problem each" is the literal job description of an **AI Integration Engineer**. Most candidates can prompt; few can say *why a Skill and not a hook here.* The decision rule above **is** the interview answer.
- **Startup lens:** For a "Claude-for-X" product, these five layers are your **product surface**: Skills are your reusable verticalized workflows (the thing you actually sell), MCP is your integration moat, hooks are your guardrails, subagents are your margin (token amortization). Design the product as a *Skill library on top of MCP*, not a chat wrapper.
- **Insight:** The skill ladder moved up again: 2024 was "write a good prompt," 2025 was "write a good CLAUDE.md," 2026 is **"compose the five layers."** Each rung commoditizes the one below. Invest at the top rung.

---

## 2. This weekend's artifact: ship one Agent Skill {#2-skill-artifact}

Don't start something new — **package something you already repeat.** Pick one recurring workflow and turn it into a `SKILL.md`:

1. **Choose a repeatable procedure** you do by hand today. Best candidates from your own backlog: the **MCP-server eval run** ([2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)) or the **personal Claude billing-audit report** ([ME.md](../ME.md) portfolio list).
2. **Write `SKILL.md`** — a short instruction pack: the trigger ("when asked to audit token spend…"), the steps, and any resource files it needs. Keep it tight; Skills load on demand, so verbosity is wasted context.
3. **Test the trigger** — start a fresh session, describe the task in plain language, confirm Claude *discovers and invokes* the Skill without you naming it (the same "tool discovery" property MCP-Atlas measures, [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)).
4. **Publish it** with a 3-line README + a demo gif.

**Why this artifact, this weekend:** it's a **1–2 hour build** that produces grep-able proof you operate the post-`CLAUDE.md` layer, and it **composes** with the dual-model sanitiser already queued ([2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact)) — the Skill becomes the reusable "run my eval" step inside that project.

→ Cross-link: [2026-05-22/03 §2 the dual-model artifact this plugs into](../2026-05-22/03-practical-skills-and-tools.md#2-artifact) · [2026-05-17/03 the CLAUDE.md install this builds on](../2026-05-17/03-practical-skills-and-tools.md) · [`ACTIONS.md`](../ACTIONS.md).
