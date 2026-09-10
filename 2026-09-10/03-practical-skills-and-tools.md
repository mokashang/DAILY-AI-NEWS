# Practical Skills & Tools — 2026-09-10

Act on these today. Two of the three are already worth doing tonight; the third is a weekend project that becomes a portfolio artifact you can hand to any recruiter. The theme: **the 2026 Claude Code stack has stabilized into four primitives (Hooks / Skills / Subagents / CLAUDE.md), the cost curve just dropped 75% on one line item, and the release-cadence collapse means the router artifact is now more valuable than any single-model benchmark.**

Tags: `#claude #claude-code #pricing #skills #hooks #subagents #routing #evals #cost`

---

## 1. Fable 5.1 economics — the 75% cache-read discount, and how to capture it tonight {#1-fable-51-economics}

**What happened:** Fable 5.1 dropped **cache reads from $1.00 → $0.25 per 1M tokens.** This is the biggest input-cost line-item cut of 2026, and it's automatic if you're already caching prompts (via [2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md)). If you're *not* caching yet, this is the highest-ROI evening of engineering you'll do this quarter.

**Ballpark:** an agent that reads a 20k-token system prompt on every step, running 200 steps/day across 50 users:
- Before caching: **200 M input tokens/day at $3/1M = ~$600/day = ~$18K/mo.**
- With caching (old price): **~$1.20/1M avg = ~$240/day = ~$7.2K/mo** — a 60% cut.
- With caching (Fable 5.1 price): **~$0.65/1M avg = ~$130/day = ~$3.9K/mo** — a further 45% cut.

Same feature, three price points. The delta between "no caching" and "Fable-5.1 caching" is **~$168K/yr of margin.**

### How to capture it tonight (60 minutes)

1. **Instrument** — for each of your top-3 prompt patterns, log token counts, cache hit rate, per-request cost.
2. **Route** — keep your existing model for cases where quality matters most (long outputs, multi-step reasoning); switch cacheable read-heavy paths (RAG, doc-QA, code review) to Fable 5.1 with `cache_control: {type: "ephemeral"}` on the system prompt + long context.
3. **Verify** — run a 5-case eval before and after to confirm quality parity (5-case shown in [`04` §3](./04-research-progress.md#3-eval-suite-template) as a template).
4. **Publish** — put the cost graph on GitHub as a public repo. This is a resume-differentiator for FDE roles ([`05` §2](./05-career-and-startup.md#2-reprice)).

### Sources
- [Anthropic — Claude Fable 5 and Claude Mythos 5 announcement](https://www.anthropic.com/news/claude-fable-5-mythos-5) `[primary]`
- [Anthropic — Claude Mythos 5.1 platform docs](https://platform.claude.com/docs/en/models/mythos-5-1/overview) `[primary]`
- [VentureBeat — Fable 5.1 / Mythos 5.1 launch: 75% cost reduction for cache reads](https://venturebeat.com/technology/anthropics-claude-fable-5-1-and-mythos-5-1-arrive-with-a-75-cost-reduction-for-fable-cache-reads) `[secondary]`
- [MarkTechPost — 52.6% on Terminal-Bench-Science, 75% cheaper cache reads](https://www.marktechpost.com/2026/09/01/anthropic-releases-claude-fable-5-1-and-claude-mythos-5-1-52-6-on-terminal-bench-science-and-75-cheaper-cache-reads/) `[secondary]`

---

## 2. The 2026 Claude Code decision tree — Hooks / Skills / Subagents / CLAUDE.md {#2-decision-tree}

**What happened:** The 2026 best-practice guides (SmartScope, AgentsRoom, Chudi.dev, and Anthropic's own engineering blog) have converged on **one decision tree** for organizing your Claude Code project. It replaces the "everything in CLAUDE.md" pattern that was still fine at the start of 2026:

| If the rule is... | Put it in... | Why |
|---|---|---|
| **Enforcement — must run** | Hooks / permissions | Deterministic; runs even if the model forgets |
| **Contextual knowledge — expertise for one task** | Skills | Loads only when relevant; keeps context clean |
| **Delegation boundary — a different scope of work** | Subagents | Isolated context; specialized model choice |
| **Always-on project guidance** | CLAUDE.md (kept short) | Persistent; every session sees it |

**Corollary:** **if a rule "must be enforced", it does NOT belong in CLAUDE.md.** CLAUDE.md is soft — hooks are hard.

### Concrete refactor pattern (tonight, 45 minutes on one project)

1. Read your current CLAUDE.md. Highlight anything phrased as "always" or "never" or "before commit" or "must".
2. Each "must" line — move it to a **PreToolUse** or **PostToolUse hook** in `.claude/settings.json`. Example: `"before Bash tool use, run 'ruff check --fix'"` → a PreToolUse hook that blocks the tool if ruff fails.
3. Each "when doing X, use technique Y" line — move it to a **skill** in `.claude/skills/`.
4. Each "this file does Z" tribal-knowledge line — leave in CLAUDE.md; that's what CLAUDE.md is for.
5. Each "delegate the tests / delegate the review / delegate the migration" — build a **subagent** in `.claude/agents/`.

**Effect:** CLAUDE.md shrinks 50–70%, quality gates get more reliable, and your context stays clean during long agentic runs.

### Sources
- [SmartScope — Claude Code Advanced Best Practices: 11 Practical Techniques for Hooks, Subagents & Context Management (2026)](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[analysis]`
- [AgentsRoom — 50 Claude Code Tips & Tricks: Ship 10x Faster in 2026](https://agentsroom.dev/claude-code-tips) `[analysis]`
- [Chudi.dev — Claude Code Best Practices 2026: What the Official Docs Don't Cover](https://chudi.dev/blog/claude-code-complete-guide) `[analysis]`
- [Anthropic Engineering](https://www.anthropic.com/engineering?p=88) `[primary]`
- [Obot — Claude Code Tips: The Master Guide to Advanced Agent Workflows](https://obot.ai/blog/claude-code-tips-the-master-guide-to-advanced-agent-workflows/) `[analysis]`
- [Towards AI — Claude Code Productivity Tips I'd Actually Use in 2026](https://pub.towardsai.net/claude-code-productivity-tips-id-actually-use-in-2026-f4a965bd090c) `[analysis]`

---

## 3. The router artifact — a 30-line shim + 5-case eval suite = your H2 interview trump card {#3-router-artifact}

**What happened:** The four-frontier-models-in-one-week week ([`01` §1](./01-big-lab-moves.md#1-model-fatigue)) made **model-routing** an in-demand skill overnight. The good news: **the minimum-viable router is small enough to write in one evening.**

### What the artifact is

A public GitHub repo that:
1. Wraps 3+ providers (Anthropic Fable 5.1, OpenAI GPT-6 Astra, Google Gemini 3.8 Flash — or whatever your task allows).
2. Routes by task type — **{coding, long-context Q&A, cheap batch summary, tool-use / agent}** — via a config table, not hard-coded conditionals.
3. Logs per-request cost, latency, and token counts to a local SQLite / CSV.
4. Ships a **5-case eval suite** (see below) that runs on every model, so switching cost is measurable.
5. Publishes a **live leaderboard README** — updated by CI on push — with cost + quality per case per model.

### The 5-case eval suite template

Keep it small enough to run in 60 seconds:

1. **Cheap-summary case:** 5k tokens in → 200 tokens out. Optimizes for cost.
2. **Long-context case:** 100k tokens in → 500 tokens out with a factual retrieval question. Optimizes for accuracy at length.
3. **Coding case:** solve a leetcode-medium in Python; run the tests. Optimizes for correctness.
4. **Tool-use case:** an agentic loop calling 3+ MCP tools to answer a compound question. Optimizes for tool-selection + finish-condition.
5. **Refusal / safety case:** a genuinely ambiguous prompt where the right answer is "clarify." Optimizes for calibration.

Score each on **cost, latency, quality (binary or 0–3)** and store per-model.

### Why this is the artifact of the moment

- **Recruiter reads it in 20 seconds** — leaderboard chart is the hook.
- **Answers three interview questions at once**: (1) do you know the current model landscape? (yes — you route them); (2) do you write evals? (yes — public); (3) do you think about cost? (yes — logged).
- **Ages well.** When GPT-6.1 lands next month, you add one row. When Fable 5.2 lands, you add another. The artifact stays current while your competitors' "I built a chatbot with GPT-4o" repos rot.

### Sources
- [MacRumors — Fable 5.1 pricing / capabilities](https://www.macrumors.com/2026/09/01/anthropic-claude-fable-5-1/) `[secondary]`
- [Sunday Guardian — Claude Fable 5.1 launch: features, pricing, Mythos 5.1](https://sundayguardianlive.com/tech-news/anthropic-claude-fable-51-launch-september-2026-new-ai-model-vs-fable-5-smarter-coding-research-lower-costs-check-features-pricing-mythos-51-275079/) `[secondary]`
- [Zima Store — Top 10 AI Agent Skills for Claude Code in 2026](https://shop.zimaspace.com/blogs/tech-ai-hub/top-10-ai-agent-skills-for-claude-code-in-2026) `[analysis]`

→ Cross-link: [`05` §2 the skill re-price](./05-career-and-startup.md#2-reprice) · [`02` §3 model-fatigue tooling wedge](./02-new-emerging.md#3-model-fatigue-tooling).

---

## 4. One-line habits worth keeping this week {#4-habits}

- **Prompt caching on** for every long system prompt — check today whether cache-hit rate is >70%. If not, your prompt is churning; move the volatile bits to the *end* of the message.
- **"Address all notes, don't implement yet"** — the plan → annotate → then-implement pattern is still the highest reliability primitive in 2026. Use it for anything longer than 200 lines.
- **Public repo weekly cadence** — one shippable artifact/week is the compounding move. In September that's 4 artifacts by month-end; by year-end that's 16. That's a portfolio.
- **Two-gate quality control** — never mark a task done without (a) the check running and (b) evidence (screenshot, test output, deploy log). Non-negotiable in the 2026 hiring loop.

### Sources
- [The AI Corner — Claude best practices 2026: the complete power user guide](https://www.the-ai-corner.com/p/claude-best-practices-power-user-guide-2026) `[analysis]`
- [Obot — Claude Code Tips: Master Guide to Advanced Agent Workflows](https://obot.ai/blog/claude-code-tips-the-master-guide-to-advanced-agent-workflows/) `[analysis]`
