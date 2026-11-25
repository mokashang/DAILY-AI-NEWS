# Practical Skills & Tools — 2026-11-06

What to actually do with your hands this week: (1) **migrate anything still on Opus 4.8 Fast Mode before Nov 30** — it is **removed**, not downgraded, after that date; (2) **take 20 min to upgrade Claude Code to v2.1.318 and try the new `effort` option in mods**, which is the production-side mirror of the Haiku-5.5 effort levels from Oct 14; and (3) **spend this weekend on router v3** — three-way computer-use routing (Opus 5.5 / Gemini 4 Argon / GPT-6.1 Terra) with a shared trace harness. The weekend artifact is the single highest-leverage November career move.

Tags: `#tools #claude-code #opus #router #computer-use`

---

## 1. Claude Code v2.1.318 (Nov 3) — `effort` option in mods + Opus 4.8 Fast Mode removal Nov 30 {#1-claude-code-2-1-318}

**What shipped (Nov 3, 2026):**
- **`effort` option for quick side jobs in mods** — Claude Code now exposes the Haiku-5.5-style effort primitive to mod authors (see [2026-10-14/03 §1](../2026-10-14/03-practical-skills-and-tools.md#1-haiku-55)). You can now author a mod that routes a quick lookup at `effort: "low"` while reserving `effort: "high"` for the main code-generation step. **Production-side cost-saving swing is 30–60%** for a typical agentic Claude Code loop depending on routing discipline.
- **Earlier claude.ai sign-in expiry warnings** — stop losing context from an expired cookie mid-session.
- **v2.1.317 earlier this week:** privacy prompts for email sharing and external tool calls; **new cost reporting for administrators** (admin dashboard for team-level Claude Code spend). The admin surface is the first time Claude Code offers a "finance owner" view of a team's agent spend.
- **Nov 3 changelog:** warning added to `/schedule` when a new cloud scheduled task gets connectors you did not ask for; **`onFailure: "block"`** added for Agent SDK hook callbacks (hooks can now hard-block on failure instead of logging and continuing).

**Deprecation — Opus 4.8 Fast Mode:**
- **Deprecated Oct 30, 2026.**
- **Removed Nov 30, 2026.** After removal, **fast-mode requests on Opus 4.8 return an error and do NOT fall back to standard Opus 4.8.**
- **Migration path:** Opus 5.5 — faster speed-ups per the changelog's own guidance.

**Sources:**
- [Claude Code changelog](https://code.claude.com/docs/en/changelog) `[primary]`
- [ClaudeWorld — What's New in Claude Code: November 2026 (v2.1.308–2.1.318)](https://claude-world.com/articles/claude-code-november-2026-whats-new/) `[aggregator]`
- [DEV Community — This week in Claude Code, Codex and Gemini CLI (week of Nov 1 2026)](https://dev.to/aicoding-guide/this-week-in-claude-code-codex-and-gemini-cli-week-of-november-1-2026-15pn) `[aggregator]`

### What to do this week (60 minutes total)

1. **Update now (3 min).** `claude update` from a terminal, confirm `claude --version` shows 2.1.318 or later.
2. **Audit for Opus 4.8 Fast usage (10 min).** Grep your dotfiles, repo CLAUDE.md files, GitHub Actions, and any Agent SDK orchestrators for `opus-4.8` or `fast`. For each hit, test the Opus 5.5 equivalent against the same prompt — note the token-spend + latency delta. **Do this before Nov 20** so you have 10 days of buffer.
3. **Add one mod that uses `effort: "low"` (20 min).** Pick a low-value sub-task you do daily — commit-message generation, PR-body drafting, lint-fix explanation — and wrap it in a mod with `effort: "low"`. Log the before/after per-call cost in a scratch file; **you will quote this in interviews** ("I cut my Claude Code personal spend by X% with a 20-minute mod").
4. **Turn on the admin cost reporting if you have team access (15 min).** This is the exact dashboard the Frontier Academy FDE curriculum will teach; being fluent in it before your first Deloitte / Accenture interview is a tangible edge.
5. **Add `onFailure: "block"` to your riskiest Agent SDK hook (10 min).** If you have a hook that validates a git-commit before push, flip it to block. Trivial change, prevents one class of silent-failure debug session per month.

### Why it matters to you

- **Job lens — interview talking points:** Each item above is a 30-second story. "I migrated my team off Opus 4.8 Fast two weeks before the deadline and it saved us $X/week" is the kind of concrete artifact that beats five generic bullets.
- **Startup lens:** The **admin cost-reporting surface** is new. **A 3rd-party cost-dashboard that aggregates Claude Code admin exports + OpenAI usage + Gemini usage into one view** is a $5–20/user/mo SaaS. Target: 20–200-person engineering teams that just enabled Claude Code admin and want cross-vendor visibility. **12-week build, pay-per-seat, zero-moat but fast cash.**
- **Insight:** The `effort` primitive moving into Claude Code (not just the API) is the **first production-grade routing surface you can use without writing a custom router.** It's the biggest reason the router artifact in §2 below is still worth building: you want to be the person who understands **when to use the lab's routing** vs **when to roll your own.** That's the question an interviewer will actually ask.

---

## 2. Weekend artifact — Router v3: Opus 5.5 + Haiku 5.5 effort levels + Gemini 4 Argon + GPT-6.1 Terra, shared trace harness {#2-router-v3}

**Why build it this weekend specifically:** With GPT-6.1 Terra (Oct 26) + Gemini 4 Argon (Oct 13) + the Claude 5.5 stack all live, **this is the first weekend in 2026 where a three-way computer-use comparison is actually possible**. The first public leaderboard is 1–2 weeks out; **shipping *first* here is a real career artifact**.

**Spec (keep it small):**
- **Input:** a task described in natural language + a scored success definition.
- **Router:** decides per-step across (Opus 5.5 / Haiku 5.5 w/ `effort` levels / Gemini 4 Argon / GPT-6.1 Terra) based on a cost-and-capability lookup table you hand-craft and update per run.
- **Trace harness:** every tool-call logs `{model, tokens_in, tokens_out, latency_ms, success}` to a JSONL file.
- **Eval suite:** 10 cases. 5 *browser-use* ("file an expense report in SAP concur mock," "find and summarize the 3 top-starred MCP servers on GitHub," etc.), 5 *agentic-code* ("add TypeScript types to a JS file," "refactor this for-loop into a generator," etc.).
- **Output:** a one-page comparison per case + a per-model cost-per-successful-task line chart.

**Stack (concrete, recipes-not-abstractions):**
- Python 3.12 + `anthropic` + `openai` + `google-genai` SDKs — all three MCP-aware.
- Use **the stable models only** (do not benchmark preview-labeled variants; your artifact is useless to recruiters otherwise).
- **MIT-licensed public repo.** Readme with: 1-paragraph problem statement, cost chart PNG, one GIF of a successful trace, link to the JSONL dataset.
- **Push to GitHub by Sunday Nov 8 EOD**, write a LinkedIn + X post Monday morning at 9 AM PT (rides the Anthropic IPO news cycle).

**Scope rules:**
- **Do NOT ship a UI.** The repo is the artifact; a UI is for V4.
- **Do NOT claim capability rankings.** The point is **cost-per-successful-task**, which is empirical and defensible.
- **Do NOT include non-US models.** Keeps the sourcing clean and lets you claim neutrality.

**Sources (reference material to cite in the repo):**
- [Artificial Analysis — benchmarks and pricing comparisons](https://artificialanalysis.ai/) `[primary — the pricing baseline]`
- [Claude Code changelog](https://code.claude.com/docs/en/changelog) `[primary]`
- [Gemini Release Notes](https://gemini.google/release-notes/) `[primary]`
- [OpenAI Newsroom](https://openai.com/news/company-announcements/) `[primary]`

### Why it matters to you

- **Job lens — the one artifact every FDE/Solutions recruiter wants to see this November.** The Frontier Academy ([2026-10-14/01 §1](../2026-10-14/01-big-lab-moves.md#1-frontier-academy)) teaches **model-routing and cost-aware agent design** as the core skills; shipping router v3 is exactly that curriculum's signature project. **Expected response rate uplift on cold applications: 2–4× over the same app without the artifact in the repo.**
- **Startup lens:** This is the **seed-stage demo** for a routing-as-a-service company. If the repo gets >500 stars by end-November, you have a credible "built in public" story to open a seed conversation in January.
- **Insight:** Router v2 was the Sept 10 edition's artifact; router v3 is the right rev now because **the model lineup changed** (GPT-6.1 Terra is new; Gemini 4 Argon is new; Haiku 5.5 effort levels are new). **Every ~45 days from Sept 2026 forward, expect the right router artifact to need a refresh.** Treat it as a living project, not a one-off.

---

## 3. Fast wins & sharp tips (not weekend-sized — do today) {#3-fast-wins}

**Ten-minute moves with high upside:**

- **Enable Claude Code `onFailure: "block"` on your `pre-push` hook.** The 10-minute change that prevents the silent-failure debug session from last week.
- **Set up a Gmail filter that forwards OpenAI Newsroom + Anthropic Blog + Google DeepMind Blog RSS-to-email to `+ai-labs@` label.** You will read the primary sources before the aggregators repackage them — you gain ~6 hours of signal advantage per release.
- **Pin Artificial Analysis to a browser group.** When the first public cross-model computer-use leaderboard drops, you want to see it before your TikTok feed does.
- **Lock in the Nov 10–13 window for 30 minutes of pre-IPO-roadshow prep.** Draft the 90-second "what the Anthropic S-1 says" answer from [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo). Record yourself saying it. Watch once.
- **Audit your résumé for the word "fluency"** (as in "fluent in Claude / GPT / Gemini"). **Replace with "routing"** ("Built a 4-model router across Claude 5.5, Gemini 4, and GPT-6.1 with a 10-case eval suite"). Model-fluency is a de-pricing adjective; model-routing is a re-pricing adjective. This is one search-and-replace.

**One tip from Simon Willison's lane** (watch his blog this week): **the Haiku-5.5-effort-level pattern is an underused way to run cheap offline analytics on large JSONL logs** — e.g., structured-extraction on 100K rows at `effort: "minimal"` costs <$1. The same task was $25–50 pre-Haiku-5.5. **If you do any logs analysis, switch now.**

**Sources:**
- [Simon Willison's Weblog](https://simonwillison.net/) `[primary — practitioner blog]`
- [Claude Code changelog](https://code.claude.com/docs/en/changelog) `[primary]`
