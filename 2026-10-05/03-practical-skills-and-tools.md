# Practical Skills & Tools — 2026-10-05

Act on these today. The ratio of **time-to-ship** vs **recruiter-signal** has rarely been better than it is this October — because the deployment-surface primitives (mods, dots, Codex-cloud, Claude subagents, Sailboxes) all shipped inside a 10-day window, so **nobody has a 6-month-old artifact yet.** Everybody is a beginner this quarter. **Ship one artifact in each of the three categories below (mod · agent-as-direct-report · cost table) before Oct 12 and you are, measurably, in the top 5% of the applicant pool for every FDE / Applied AI / AI Engineer / Developer Tools role in the market.**

Tags: `#claude #claude-code #mods #plugins #dots #gpt-6 #codex #sol #cost #pricing #routing #evals`

---

## 1. Write and publish one Claude Code mod — tonight {#1-mods-tonight}

**What happened:** Oct 1 — Claude Code v2.1.287 shipped **mods** (see [`01` §2](./01-big-lab-moves.md#2-claude-code-mods)). A mod is a TypeScript plugin that can draw panes/bands, restyle the UI, intercept tool calls, forward requests to another model, and generally reshape the agent. **The directory is open, nobody has 10K installs yet, and the quality bar for "notable mod" this week is low.** This is a 90-day distribution-channel head start, exactly like the first weeks of the Chrome Web Store or the VS Code marketplace.

### The 2-hour MVP mod — your "cost-weather" badge

Specifications:
1. A **status-line band** in Claude Code showing **per-request cost + cumulative cost for this session**.
2. A **sparkline of cost per request over the last 12 turns** — same spatial pattern as Token Weather, cost-axis instead of context-axis.
3. **Alert band** when cache-hit-rate drops below 70% for 3 consecutive turns — the "your prompt is churning" diagnostic from [2026-09-10/03 §4](../2026-09-10/03-practical-skills-and-tools.md#4-habits).

That's it. ~150 lines of TypeScript, two API calls, one sparkline SVG. If it looks like the Token Weather mod, you're close.

### The 20-minute install + ship flow

1. Scaffold: `claude mod init cost-weather` (per the Oct 1 docs).
2. Point the mod at Claude Code's **request-trace hook** — the same hook mods use to inspect tool calls — and read `usage.input_tokens`, `usage.cache_read_input_tokens`, `usage.output_tokens` on every response.
3. Compute `cost_this_turn = f(model, usage)` from the pricing table in §3 below.
4. Render into a status band via the mod's **panes-and-bands API**.
5. Install locally: `/plugin install ./cost-weather`.
6. **Submit to the Claude directory** — the "Submit" link in the plugin page.
7. Push the repo to GitHub + record a 15-second gif of the sparkline updating. **This is the recruiter artifact.**

### Mod ideas, ranked by portfolio signal

| Mod | What it does | Why it signals |
|---|---|---|
| **cost-weather** (above) | Live per-turn cost + cache-hit health | You think about money + you can read the trace hook |
| **safety-review** | Blast-Radius-style preview before shell / git / rm commands; show the files touched + a one-line summary | You think about safety + you understand filesystem reasoning |
| **mcp-tracer** | Log every MCP tool call with latency, cost, success/failure; render into a tab | You understand MCP + you write real telemetry |
| **subagent-router** | On `/delegate`, open a picker: pick Opus/Sonnet/Haiku for the subagent based on the task | You understand model routing + agent delegation |
| **eval-runner** | Load a 5-case eval suite from `evals/*.jsonl` and run it on request | You own the eval-authoring narrative from [2026-09-10/04 §3](../2026-09-10/04-research-progress.md#3-eval-suite-template) |

### Safety-side gotcha

Anthropic's own advisory: *"Mods receive the same access to a user's machine as Claude Code; install only from trusted sources."* **Build and test only your own mods on your main machine until the trust model matures.** For installing other people's mods, use a disposable Dev Container or a cloud VM.

### Sources
- [The New Stack — Anthropic's mods let you change Claude Code's look and behavior](https://thenewstack.io/anthropic-claude-code-mods-plugins/) `[secondary]`
- [Crypto Briefing — Anthropic adds Claude Code mods for behavior and interface changes](https://cryptobriefing.com/anthropic-claude-code-mods-customization/) `[secondary]`
- [Cellcog.ai — Claude Code Mods: What They Can Do and What They Can Reach](https://cellcog.ai/blog/claude-code-mods/) `[analysis]`
- [SuperPower Daily — Claude Code Mods That Can Rewrite Prompts and Replace Built-in Features](https://superpowerdaily.com/posts/anthropic-adds-claude-code-mods-that-can-rewrite-prompts-and-replace-built-in-features) `[secondary]`

---

## 2. Run one agent as a direct report for seven days — "AADR" {#2-agent-direct-report}

**What happened:** With **dots** on ChatGPT, **Codex-in-the-cloud + voice** on OpenAI, and **Claude subagents + Managed Agents** on Anthropic, every CS grad can — this week — assign a real workflow to an *always-on agent on its own compute* and treat it like a direct report. **The portfolio artifact: a one-week log of running that agent, with Custom Rules, incident entries, and a weekly review.** Recruiters at Anthropic / OpenAI / FDE-track roles will read this before they read your resume.

### The 7-day AADR protocol

**Day 0 (today, 60 min):**
1. **Pick ONE repeatable workflow you own**: triage incoming GitHub issues on your personal repo; review a daily batch of arXiv abstracts and shortlist 3; summarize incoming email into a daily brief; auto-grade LeetCode submissions against a rubric. One, concrete, with a measurable success criterion.
2. **Scope the dot (or subagent): the Custom Rules.**
    - What may it do unattended? (e.g., post a comment on a GitHub issue, label it)
    - What must it ask first? (e.g., close the issue, add a milestone)
    - What must it never do? (e.g., modify code, create a PR, invite collaborators)
3. **Pick the surface:** OpenAI Dot (if you have Pro $100/mo), a Claude Code subagent + hook (free), or a Codex-cloud task triggered on a schedule.
4. **Instrumentation:** before the agent runs, write to a log the input context + prompt. After, write the agent's actions + outcome. **This log IS the artifact.**

**Days 1–7:**
- Let the agent run against the real workflow.
- Review its log every day for ~5 minutes.
- Write **two incident reports** when it does something unexpected — one on an action that was correct-but-surprising, one on an action that was outright wrong. Postmortem each in ~150 words.
- **Day 7:** Write a 400-word "my first week with an AI direct report" post — what the Custom Rules missed, what you'd write differently, what the agent is now trusted to do unattended.

**Publish:** repo + README + the two postmortems + the review post. **Tag it `agent-direct-report-week-01` on GitHub.** This is the exact artifact an FDE recruiter asks for in the first-round phone screen — "tell me about a time you deployed an agent in production."

### Why the postmortem is the signal

**Any CS grad can run an agent for a day.** Few will produce a written artifact that reasons about the agent's failure modes in production language. **That written artifact is the single highest-signal item in your 2026 portfolio** — because it demonstrates the exact skill the Frontier Academy residency ([`01` §4](./01-big-lab-moves.md#4-frontier-academy)) is being built to credential. **Beat the credential by shipping the behavior.**

### Sources
- [betanews — OpenAI launches dots, always-on ChatGPT agents](https://betanews.com/article/openai-dots-agents-chatgpt/) `[secondary]`
- [Axios — The 5 biggest announcements from OpenAI's blockbuster AI conference](https://www.axios.com/2026/09/29/openai-dev-day-2026-dots-space-sol) `[secondary]`
- [Anthropic Engineering — Claude Code hooks + subagents](https://www.anthropic.com/engineering?p=88) `[primary]`

---

## 3. The October cost table — Fable 5.1 vs GPT-6.1 Sol vs Gemini 3.8 Flash {#3-cost-table}

**What happened:** With **GPT-6.1 Sol** priced at **~20% of GPT-6 Astra**, and **Fable 5.1 cache reads at $0.25/1M** (see [2026-09-10/03 §1](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics)), **the mid-tier price floor has moved another ~40–50% in six weeks.** The practical implication: *every production stack built in Q2 2026 is now a cost-leak until rebuilt.* The compounding move is to rerun the cost dashboard this week and route the "cheap workhorse" layer to Sol or Fable-cached.

### The pricing table (as of 2026-10-05)

> All prices are approximate per-1M-token list for input / output. Caching discount applies on second+ use within a cache window. Confirm current pricing on the provider's own page before you run a live cost model.

| Model | Input | Output | Cache read | Notes |
|---|---|---|---|---|
| **Claude Fable 5.1** | ~$3.00 | ~$15.00 | **$0.25** | 75% cache-read cut vs predecessor; 52.6% on Terminal-Bench-Science |
| **Claude Mythos 5.1** | restricted | restricted | restricted | Red-team / vetted-access only |
| **GPT-6 Astra** | listed Sept 3 | listed Sept 3 | — | Frontier tier of GPT-6 |
| **GPT-6.1 Sol** | **~⅕ of Astra** | **~⅕ of Astra** | — | Near-Astra quality, workhorse tier, *coming soon* at DevDay |
| **Gemini 3.8 Flash** | low-tier | low-tier | $0.15 (May print) | 1M in / 65K out ctx |
| **Gemini 4 Argon** | frontier | frontier | — | 1M **output** ceiling, cyber-defense tilt |

### The routing rule-of-thumb for this week

| Workload | Primary | Secondary (cheap) | Reason |
|---|---|---|---|
| Agentic coding, long reasoning chains | **Fable 5.1** | GPT-6 Astra | Terminal-Bench-Science + cache-read cost |
| Doc-QA / RAG with 20K+ cached prompt | **Fable 5.1 cached** | Gemini 3.8 Flash | Cache-read $0.25 is dominant |
| Cheap bulk batch summarization | **Gemini 3.8 Flash** | **GPT-6.1 Sol** | Lowest tokens-per-dollar in each stack |
| 1M-token single-shot output | **Gemini 4 Argon** | (no alternative yet) | Only output-ceiling that fits |
| Tool-use agent / dots-style loop | **GPT-6 Astra (via dot)** or **Claude subagent** | — | Agent runtime quality > per-token cost |

### The 30-minute Monday update

1. Pull **last 7 days of model-cost rows** from your logs (if you don't have one, start today — see §1's cost-weather mod).
2. Replot by model + rank by $/task.
3. For the top-2 cost lines, **evaluate switching** one leg to Sol or Fable-cached (per the table above).
4. Push a **before / after cost graph** to your public artifact repo (same one as §1 and §2).

**That graph** — before/after, same workload, actual numbers — is a 10-minute conversation starter in any FDE interview. It also doubles as a design-partner conversation starter if you're on the startup track ([`02` §3](./02-new-emerging.md#3-agent-infra-category)).

### Sources
- [Axios — DevDay 2026: GPT-6.1 Sol priced ~20% of Astra](https://www.axios.com/2026/09/29/openai-dev-day-2026-dots-space-sol) `[secondary]`
- [BGR — Everything OpenAI Announced At DevDay 2026](https://www.bgr.com/2272332/openai-devday-2026-announcements/) `[secondary]`
- [MarkTechPost — Fable 5.1 cache-read 75% cut](https://www.marktechpost.com/2026/09/01/anthropic-releases-claude-fable-5-1-and-claude-mythos-5-1-52-6-on-terminal-bench-science-and-75-cheaper-cache-reads/) `[secondary]`
- [VentureBeat — Fable 5.1 cost reduction](https://venturebeat.com/technology/anthropics-claude-fable-5-1-and-mythos-5-1-arrive-with-a-75-cost-reduction-for-fable-cache-reads) `[secondary]`
- [Google Blog — September 2026 AI updates (Gemini 3.8 Flash + Argon)](https://blog.google/innovation-and-ai/technology/ai/google-ai-updates-september-2026/) `[primary]`

---

## 4. The agent-primitive weekend memo — pick one, 500 lines, publish {#4-primitive-memo}

**What happened:** [`02` §3](./02-new-emerging.md#3-agent-infra-category) names the three agent-infra sublayers. Sublayer 3 (**agent-to-agent protocols**) has **one funded primitive (payments → Natural; [2026-09-10/02 §2](../2026-09-10/02-new-emerging.md#2-natural-agent-payments)) and six unfunded ones** (identity, communication, authorization, reputation, dispute resolution, storage).

**The weekend protocol:**

1. **Pick ONE unfunded primitive.** Spend 15 minutes picking — the choice matters less than the shipping.
2. **Name 3 real payloads** that fail on today's human-primitive rails. E.g., for *agent-reputation*: Dot-at-company-A calling Dot-at-company-B — how does B's dot know whether to trust A's dot?
3. **Design 5 endpoints or fewer.** The constraint is the point.
4. **Ship a 500-line reference implementation** in your language of choice.
5. **Publish:** repo + 1-page memo + 10-line "why this is a venture-fundable wedge" closing paragraph.

### Why this works as a founder-path artifact

Even if you don't start the company, the memo is **the single highest-signal pre-seed artifact you can publish in October.** VCs read it, FDE recruiters read it (it signals "founder-track" first-engineer), and if you *are* the founder, it's a warm-intro currency.

### The reading list for the weekend

- [`02` §2 — Natural / Stripe-for-agents (2026-09-10)](../2026-09-10/02-new-emerging.md#2-natural-agent-payments) — the proof the thesis works for one primitive.
- [`04` §1 — Self-Organizing Agent Teams (today)](./04-research-progress.md#1-sat) — why reputation + role-assignment are not solved.
- [`04` §3 — eval-suite template (2026-09-10)](../2026-09-10/04-research-progress.md#3-eval-suite-template) — plug this shape into your primitive's test harness.

---

## 5. Habits worth keeping (September → October) {#5-habits}

- **Prompt caching stays on.** Fable 5.1 cache-reads are now the single highest-ROI line in a mixed-model stack ([2026-09-10/03 §1](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics)).
- **One mod per month.** This month: cost-weather or safety-review. Next month: an mcp-tracer or subagent-router.
- **The 4-primitive Claude Code decision tree** ([2026-09-10/03 §2](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree)) still holds: Hooks (enforcement) · Skills (contextual knowledge) · Subagents (delegation) · CLAUDE.md (always-on).
- **Public artifact weekly.** The pace is cumulative; the shape doesn't matter as much as the ship-every-week discipline.
- **"Address all notes, don't implement yet"** — the planning primitive from May still carries the highest reliability-per-minute of any 2026 workflow move.

### Sources
- [Anthropic Engineering — Claude Code primitives + hooks](https://www.anthropic.com/engineering?p=88) `[primary]`
- [SmartScope — Claude Code Advanced Best Practices (2026)](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[analysis]`
- [Obot — Claude Code Tips: Master Guide to Advanced Agent Workflows](https://obot.ai/blog/claude-code-tips-the-master-guide-to-advanced-agent-workflows/) `[analysis]`
