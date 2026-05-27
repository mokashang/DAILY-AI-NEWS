# Practical Skills & Tools — 2026-05-24

A meta-practical Sunday: the single workflow that makes a daily-news habit actually *pay off* is the **weekly compression ritual** — using an agent to turn seven days of arXiv + lab news into a one-page personal brief. You're already running the input side of this (this repo). Today, build the **output side**, and package it as a reusable Agent Skill so it runs itself every Sunday.

Tags: `#playbook #claude-code #skills #workflow #productivity`

---

## 1. The weekly-review ritual — compress the week with one Skill {#1-weekly-review}

**The problem:** daily news is a firehose; without weekly compression it becomes noise you can't act on. **The fix:** a repeatable "week-in-review" workflow — exactly the kind of *sometimes-needed procedure* that belongs in a **Skill** ([2026-05-23/03 §1](../2026-05-23/03-practical-skills-and-tools.md#1-five-layer-stack)), not in CLAUDE.md.

**The workflow (build it as `weekly-review/SKILL.md`):**

1. **Input:** point it at the week's daily folders (`2026-05-DD/00-tldr.md`) + a short arXiv search.
2. **Compress:** prompt it to produce **5 bullets of "what materially changed for my goals,"** one decision, and next week's single artifact — written *to* ME.md, not generically.
3. **Verify:** require **a source link per bullet** (no claim without a citation — the same discipline this repo enforces). Have it flag anything it couldn't source.
4. **Output:** write `WEEK-YYYY-MM-DD.md` + a 3-line LinkedIn-ready paragraph.

**Why a Skill and not a one-off prompt:** triggers (`"do my weekly review"`), bundled resources (your ME.md goals, the source-tier legend), and on-demand loading mean it's **reusable and shareable** — and it's a clean, *useful-to-you* portfolio artifact (the rare project you'd actually keep running).

**Sources:**
- [Anthropic — Equipping agents for the real world with Agent Skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) `[primary]`
- [Nimbalyst — Claude Code Skills: a practical 2026 guide](https://nimbalyst.com/blog/claude-code-skills-guide/) `[analysis]`
- [duet.so — Claude Code Skills complete guide: SKILL.md, MCP, subagents & teams (2026)](https://duet.so/guides/claude-code-skills-complete-guide) `[analysis]`

### Why it matters to you

- **Job lens:** "I built a Skill that auto-compresses my field's weekly research into a sourced one-pager" is a portfolio piece that demonstrates **Skills + retrieval + the verify-with-citations discipline** in a single artifact — and it's visibly *useful*, which beats a toy demo in an interview every time.
- **Startup lens:** This is a **micro-version of a real wedge**: "AI that turns a domain firehose into a sourced, personalized weekly brief" is a product (newsletters, analyst tools, internal-comms summarizers). Building it for yourself is free customer discovery for whether the workflow is worth selling.
- **Insight:** The highest-ROI personal AI workflow is almost always **compression of something you already consume**, not generation of something new. You don't need more inputs; you need a reliable way to turn inputs into *decisions.* Automate the compression, keep the judgment.

→ Cross-link: [2026-05-23/03 §1 the 5-layer stack (why this is a Skill)](../2026-05-23/03-practical-skills-and-tools.md#1-five-layer-stack) · [`05` §2 the ritual on the career side](./05-career-and-startup.md#2-weekly-ritual) · [`ME.md`](../ME.md).
