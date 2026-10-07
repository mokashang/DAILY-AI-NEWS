# Practical Skills & Tools — 2026-10-07

Hands-on workflows, tools, and patterns to deploy this week.

---

## 1. Claude Agent SDK vs OpenAI AgentKit — the one-page decision table {#1-sdk-comparison}

**Why it matters now.** Both stacks shipped within one week of each other: **Claude Agent SDK on Sept 29**, **OpenAI AgentKit on Oct 6**. Every production agent decision in Q4 2025 goes through this split. The internet is already flooded with hot takes; here is the honest comparison.

### The one-page table

| Axis | Claude Agent SDK | OpenAI AgentKit |
|---|---|---|
| **Philosophy** | Code-first; your infrastructure | Visual-first (Agent Builder); OpenAI-hosted or your infra |
| **Lineage** | Production evolution of **Claude Code** (shipped early 2025, battle-tested) | **New in Oct 2025**; built on existing OpenAI Assistants API lineage |
| **Model** | Claude Sonnet 4.5 (default), Opus, Haiku, external | GPT-5 Pro / GPT-5 / 4o |
| **Tools / integrations** | **MCP-first** — connect any tool via MCP server | Centralized tool registry + Apps SDK + MCP (as of Oct 6) |
| **UI builder** | None (code-first) | **Agent Builder** visual canvas (Altman: "like Canva") |
| **Embedding chat into your app** | Bring-your-own React/Next.js | **ChatKit** (official embeddable UI) |
| **Evals** | Your framework (`pytest`-style, open) | **Built-in evals + traces** |
| **Data sovereignty** | Full — run on your infra, no OpenAI/Anthropic data path | Managed infra default; BYO possible |
| **Price-to-ship a demo** | Higher (code + ops) | Lower (visual + managed) |
| **Price-to-ship production** | Lower (control costs, cache, route) | Higher (platform premium) |
| **Best fit** | Enterprise w/ data-sovereignty needs; coding/agent-ops teams | Prototypes, consumer-apps, product-eng teams w/o infra |

### The decision framework (one sentence)

> **AgentKit for prototypes, demos, and consumer apps. Claude Agent SDK for anything that goes to production with regulated data or needs cost control at scale.**

### What to actually ship this week

Pick **one wedge from your startup / portfolio idea** and build the **same agent in both stacks**. Publish a 1-page comparison with:

- Lines of code to a working v1
- Time to add a 3rd tool
- Per-request latency + cost
- Where each stack fought you

This single artifact is the **highest-leverage portfolio piece** for Q4 2025 — every FDE / AI-Integration-Engineer / Solutions-Engineer interview will ask the question and almost no one has a side-by-side writeup.

**Sources.**
- [analysis] [eesel — OpenAI AgentKit vs Anthropic API 2025](https://www.eesel.ai/blog/agentkit-vs-anthropic-api)
- [analysis] [Monetizely — Claude Agent SDK vs OpenAI AgentKit for Pay-as-You-Go](https://www.getmonetizely.com/articles/which-ai-agent-platform-is-better-anthropic-claude-agent-sdk-vs-openai-agentkit-for-pay-as-you-go-builder-monetization)
- [analysis] [Context Studios — AI Agent SDK Landscape December 2025](https://www.contextstudios.ai/blog/ai-agent-sdk-landscape-december-2025-the-ultimate-comparison)
- [analysis] [Rick Hightower — Developer's Guide to Building AI Agents](https://rick-hightower.notion.site/Claude-Agent-SDK-vs-OpenAI-AgentKit-A-Developer-s-Guide-to-Building-AI-Agents-28ad6bbdbbea80eb9c1cd9d96315fc5a)

`#claude-code #agent-sdk #agentkit #comparison #portfolio`

---

## 2. Claude Skills — the primitive you should ship against tonight {#2-claude-skills}

**What a Skill is.** A **Skill** is a reusable, scoped-knowledge pack Claude loads **on demand** when the task matches its trigger. One Skill ≈ one domain workflow:

- A YAML frontmatter with `name`, `description`, trigger keywords, optional allowed tools
- A SKILL.md body with:
  - **When to invoke** (first-person description Claude reads to decide)
  - **The workflow steps** (what Claude does when invoked)
  - **Reference artifacts** (templates, example inputs, example outputs)
  - **Tool list** (which tools this Skill can call — MCP servers, Bash, Read, etc.)

Skills **do not clutter the main prompt**; Claude only loads one when the current task triggers it. This is the Oct 2025 upgrade to the "giant CLAUDE.md" pattern of 2024.

### The one-line meta-skill: `skill-creator`

Anthropic shipped `skill-creator` **as an official primitive**. Invoke it by asking: `/skill` or "create a skill for <X>". It writes the SKILL.md scaffold for you.

### The four-primitive decision tree (unchanged from Sept 10 — now official)

| Need | Primitive |
|---|---|
| **Enforcement** (always/never do X) | **Hooks** + permissions |
| **Contextual knowledge** (how to do X when needed) | **Skills** |
| **Delegation boundary** (long task in isolated context) | **Subagents** |
| **Project-wide guidance** (always loaded) | **CLAUDE.md** |

No overlap. Pick the primitive that matches the rule type, not the one you remember.

### Ship this tonight

A **public Skill** on GitHub. Candidate domains (pick the one closest to your weekly work):

- `resume-tailoring` — JD in, 1-page résumé out, keywords matched to the JD
- `cover-letter` — JD + your bio in, 1-page letter out, cites 3 concrete past projects
- `code-review-rubric` — PR diff in, review comments out, 7 checks (correctness, tests, naming, security, perf, docs, blast-radius)
- `arxiv-reader` — paper URL in, 1-page summary + "insight for your startup" out
- `recruiter-reply` — recruiter email in, 3-sentence reply + 2 calendar times out

**Push to GitHub. Add a 20-sec screencast gif. Link it from your portfolio README.**

The signal to recruiters: "On Sept 29, Anthropic shipped Skills as a primitive. On Oct 7, you shipped a Skill. You are a current practitioner."

**Sources.**
- [primary] [Anthropic — Claude Agent SDK & Skills (claude.com/docs or anthropic.com/news)](https://www.anthropic.com/news) (Sept 29, 2025)
- [analysis] [MLearning — Claude Agent Skills 50 Power Tips](https://mlearning.substack.com/p/claude-agent-skills-50-power-tips-tricks-guide-anthropic)
- [analysis] [Mejba.me — Claude Skills complete guide](https://www.mejba.me/claude-skills-complete-guide-ai-agent-capabilities)
- [analysis] [dev.to — The Ultimate Claude Code Tips Collection](https://dev.to/damogallagher/the-ultimate-claude-code-tips-collection-advent-of-claude-2025-5b73)
- [analysis] [Medium — 50 Claude Code Best Practices](https://medium.com/@sabita2025/50-claude-code-best-practices-every-ai-engineer-should-know-6ee3f2fdf669)

`#claude #claude-code #skills #hooks #subagents`

---

## 3. The `!` prefix — the single highest-leverage Claude Code tip of the quarter {#3-bang-prefix}

**What it is.** In Claude Code, prefixing a command with `!` runs it in Bash and **injects the stdout directly into the model's context** — without the token spend of asking Claude to run a command, waiting for the tool call round-trip, and re-reading the output. Example:

```
!git log --oneline -20
!wc -l src/**/*.ts
!pytest tests/test_router.py -v
```

The output is placed in the next prompt as if Claude had read it, with **no agent-loop overhead**. On a long session, this saves meaningful tokens and cuts latency on every status check.

### Pair it with these three habits

1. **Front-load the ask.** Put the most important instruction **at the top** of the prompt, not the bottom.
2. **Give Claude a way to verify.** Tests, screenshots, "run this command and show me the output" — the single highest-leverage move inside a session.
3. **Keep sessions scoped.** When context fills, start a new session with a 2-paragraph brief instead of letting the window compress.

**Sources.**
- [analysis] [dev.to — 24 Claude Code tips (ClaudeCodeAdventCalendar)](https://dev.to/oikon/24-claude-code-tips-claudecodeadventcalendar-52b5)
- [analysis] [Product Builder — Claude Code tips](https://productbuilder.net/learn/claude-code-tips)
- [analysis] [Medium — 50 Claude Code Best Practices Every AI Engineer Should Know](https://medium.com/@sabita2025/50-claude-code-best-practices-every-ai-engineer-should-know-6ee3f2fdf669)

**Why it matters to you.**
- **Job.** The `!` prefix is **a demo-ready trick** in a pairing interview. Dropping it correctly during a live Claude Code session signals practitioner, not reader.
- **Startup.** Any coding-agent product you build should mimic this pattern: let the human **inject** context without triggering a model round-trip. It's the easiest UX win.
- **Insight.** The Claude Code UX is converging on "**the IDE is the agent prompt**" — the keystrokes and keyboard shortcuts matter as much as the model. If you intend to compete here, out-UX before you out-model.

`#claude-code #tips #productivity #cli`

---

## 4. MCP has become a standard — and that changes what to ship {#4-mcp-standard}

**What changed.** With OpenAI's **Apps SDK built on MCP** (Oct 6) + **IBM i's MCP server for IBM-i workloads** (Oct 2025) + Anthropic / Google / Meta already shipping MCP integrations, **MCP is now a cross-vendor protocol**, not an Anthropic feature.

### Three immediate implications

1. **Every tool you integrate should expose an MCP server first.** A REST API without an MCP wrapper is now de-facto incomplete for agent consumption.
2. **The "MCP marketplace / registry" category is open.** Expect at least two VC-backed registry startups by end-of-year.
3. **"Can you build an MCP server?" is a baseline interview question** at any lab or application-AI company. If you don't have one on GitHub, build one this weekend. The simplest viable: a 3-tool server over your personal data (Google Calendar, Gmail, Notion — pick one).

**Sources.**
- [analysis] [TheNewStack — AI engineering trends 2025: agents, MCP, vibe coding](https://thenewstack.io/ai-engineering-trends-in-2025-agents-mcp-and-vibe-coding/)
- [analysis] [Splunk — Top 10 AI Trends 2025: How Agentic AI and MCP Changed IT](https://embargo.splunk.com/en_us/blog/artificial-intelligence/top-10-ai-trends-2025-how-agentic-ai-and-mcp-changed-it.html)
- [analysis] [IT Jungle — IBM i MCP server](https://www.itjungle.com/tag/anthropic)
- [analysis] [MCP Playground — AI Agent + MCP explained](https://mcpplaygroundonline.com/blog/ai-agent-mcp-explained.md)

`#mcp #agents #tools #standards`
