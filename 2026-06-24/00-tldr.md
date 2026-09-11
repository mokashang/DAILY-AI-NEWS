# TL;DR — 2026-06-24 (Wednesday)

Sixty-second skim. **Day after the Fable 5 cliff, day after Daybreak's full launch — and the labs each published a different kind of "this is what we're for" essay this morning. The competitive frame just clarified.** OpenAI dropped a science-use-case showpiece: **GPT-5 Pro helping immunologist Derya Unutmaz solve a 3-year-old T-cell puzzle** that had been stalled since 2022. Anthropic doubled down on the **Project Glasswing** thread — its critical-infrastructure security coalition (now ~150 organizations across 15+ countries, anchor partners AWS / Cisco / CrowdStrike / Google / JPMorganChase / Microsoft / NVIDIA / Palo Alto) — which CNBC framed today as the **answer to OpenAI Daybreak**. Net: the **AI-cybersecurity market split into Glasswing-vs-Daybreak** in 48 hours, and the **frontier-research positioning split into Anthropic Mythos/Glasswing (security)-vs-OpenAI GPT-5 Pro (science discovery)** in the same window. **T-2 to T-4 to the GPT-5.6 release window** ([prediction-market 83% for 06/22–06/28](https://www.geeky-gadgets.com/gpt-5-6-june-2026-release/) — every day from here the odds compress on a specific date). Day 1 of the post-Fable-cliff capacity squeeze: developer Discord cost-data is starting to land.

---

1. **OpenAI publishes the GPT-5 Pro + Derya Unutmaz immunology story TODAY (06/24).** The Jackson Lab immunologist used GPT-5 Pro to re-analyze a long-stalled T-cell / glucose-metabolism dataset (62 samples, ~28K genes), producing a mechanistic explanation + follow-up experiments his lab had been wrestling with since 2022. Read it as the **IPO-narrative-setting** counterpart to yesterday's Daybreak expansion — *"frontier AI makes scientists faster"* is the story OpenAI wants in the news cycle as it heads into Q4 IPO. → [`01` §1](./01-big-lab-moves.md#1-openai-immunology) `#openai #science #gpt-5 #ipo-narrative`

2. **Daybreak vs Glasswing is now the frame for AI-cybersecurity.** CNBC today: **OpenAI Daybreak (Mon 06/22 four-piece launch — [2026-06-23/01 §2](../2026-06-23/01-big-lab-moves.md#2-openai-daybreak))** vs **Anthropic Project Glasswing** (~150 critical-infrastructure orgs in 15+ countries, expanded 06/03). Daybreak = horizontal platform + partner program. Glasswing = vertical coalition + closed cohort. **Two different bets on how to monetize cybersecurity at the frontier** — and two different sets of *job postings*. → [`01` §2](./01-big-lab-moves.md#2-daybreak-vs-glasswing) `#cybersecurity #daybreak #glasswing #anthropic #openai`

3. **GPT-5.6 launch window is open — T-2 to T-4.** Polymarket prices ~83% odds in the **June 22–28** window. Codex backend "canary" routing for `gpt-5.6` was spotted **May 13**. Leaked patterns: **~1.5M-token context** (vs 400K on GPT-5.5, ~3.75×), FrontierMath-tier-4 reasoning gains. **The next two weekdays are the most likely drop days.** → [`02` §1](./02-new-emerging.md#1-gpt-56-window) `#openai #gpt-56 #model-release`

4. **Day 1 of the Fable 5 capacity squeeze — early developer cost-data starting to land.** Yesterday Fable 5 left subscription plan limits ([2026-06-23/01 §1](../2026-06-23/01-big-lab-moves.md#1-fable-5-plan-removal)); today is the first day of bills accruing at API list rates ($10/M in · $50/M out, 2× Opus 4.8). Watch your own Claude billing dashboard at noon today vs Monday — and re-default to Sonnet 4.6 / Opus 4.8 *before* you check, not after. → [`03` §1](./03-practical-skills-and-tools.md#1-day-one-of-the-cliff) `#claude-code #cost #routing`

5. **Gemini 3.5 Pro Day-2 of the 7-day GA window** (Sundar's "give us until next month" deadline closes **June 30**). Still in Vertex enterprise preview as of 06/23; **no public GA announcement yet**. Prediction-market consensus 50–55% for GA by month-end. Watch the **Google Cloud blog / Vertex release notes** between 9am–11am PT each day this week. → [`02` §2](./02-new-emerging.md#2-gemini-pro-window) `#google #gemini #release-window`

6. **Practical: install one Codex Security artifact this week before the Daybreak partner program closes the free-tier window.** The 30M-commits / 30K-codebases / 70K human-confirmed-fixed / 500K auto-fixed numbers from yesterday's launch are the benchmark; a single 1-project pilot on your own GitHub gets you a screenshot + write-up + LinkedIn keyword refresh inside an evening. → [`03` §2](./03-practical-skills-and-tools.md#2-codex-security-artifact) `#openai #codex-security #portfolio`

7. **Research: RetailBench / Agent Planning Benchmark / Nature meta-analysis / "Verifying the Verifiers"** — June arXiv has shifted the eval frontier from *real tools* (05/22's MCP-Atlas, Toolathlon) to **long-horizon enterprise workflows + verifier-of-verifiers**. Pair with [yesterday's StateGen (06/15)](../2026-06-23/04-research-progress.md#1-stategen) — the *synthetic-data* counterpart to this evaluation wave. → [`04` §1](./04-research-progress.md#1-june-eval-wave) `#arxiv #benchmarks #planning #verification`

8. **Career: today the cyber-lane has *two* job markets to apply into, not one.** Daybreak partner ecosystem (CrowdStrike / Wiz / Snyk and 10 fast-followers) **+** Glasswing coalition (AWS / Cisco / CrowdStrike / Google / JPMC / MSFT / NVIDIA / Palo Alto). **The Venn overlap (CrowdStrike, Google) is *richest* for an AI-Integration-Engineer profile** — both labs' technology lands inside one company; the FDE who can route either backend wins. → [`05` §1](./05-career-and-startup.md#1-two-cyber-markets) `#fde #cybersecurity #careers`

---

## One thing to DO this Wednesday

→ **Apply to one role at a Daybreak ∩ Glasswing partner** ([`05` §1](./05-career-and-startup.md#1-two-cyber-markets)) — the cleanest list is CrowdStrike (in both) and Google (in both via Daybreak partner + Glasswing coalition). The framing in your cover letter: *"I can build production agent harnesses that route between OpenAI Daybreak (GPT-5.5-Cyber + Codex Security) and Anthropic Glasswing (Mythos / Sonnet 4.6) per-task — and I have the [Patch-the-Planet-style portfolio artifact](./03-practical-skills-and-tools.md#2-codex-security-artifact) to prove it."* Two-lab-fluency is the FDE-shaped credential of the moment.

## Watchlist deltas

- 🆕 **Daybreak vs Glasswing as the AI-cybersecurity competitive frame:** new thread. Track partner-program revenue share at each (the leading indicator of which bet is working).
- 🆕 **OpenAI's IPO narrative-setting via science use-cases:** new thread. Watch for the next "GPT-5 helped Nobel-track researcher Y" story inside ~2 weeks. Pattern is now visible.
- ➡️ **GPT-5.6 launch window (06/22–06/28):** T-2 to T-4 today; prediction-market 83%. Watch openai.com/news 9–11am PT.
- ➡️ **Gemini 3.5 Pro GA window:** Day 2 of 7; closes 06/30. Watch cloud.google.com/blog and Vertex release notes.
- ⏬ **Fable 5 plan-cliff:** Day 1 post-event. Watch developer-Discord cost data and any Anthropic restoration date.
- ➡️ **Agent SDK metering — still paused** ([2026-06-21 watchlist](../2026-06-21/00-tldr.md)). Watch for the un-pause announcement.
- ➡️ **MCP `2026-07-28` Release Candidate** (Tasks · MCP Apps · OAuth RS); **35.5M weekly npm downloads** ([2026-06-23/00 §7](../2026-06-23/00-tldr.md#watchlist-deltas)).
- ➡️ **Anthropic + Google/Broadcom 3.5 GW** (TPUs starting 2027): supply-side relief story; still on track. ([2026-06-23/01 §3](../2026-06-23/01-big-lab-moves.md#3-anthropic-compute))
- ➡️ **OpenAI confidential S-1 (06/08) + Anthropic confidential S-1 (06/01):** both in SEC quiet period; first amendments are the next public signal.
- ➡️ **Karpathy → Anthropic pre-training** + **Shazeer → OpenAI architecture (06/18):** two largest talent flips of 2026, opposite poles.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §2 Daybreak vs Glasswing](./01-big-lab-moves.md#2-daybreak-vs-glasswing) |
| 20 min | [`05` §1 the two cyber job markets](./05-career-and-startup.md#1-two-cyber-markets) + [`02` §1 GPT-5.6 launch-window mechanics](./02-new-emerging.md#1-gpt-56-window) |
| Today | [`03` §1 day 1 cost-data triage](./03-practical-skills-and-tools.md#1-day-one-of-the-cliff) — set defaults *before* checking the dashboard |
| This week | [`03` §2 ship one Codex Security artifact](./03-practical-skills-and-tools.md#2-codex-security-artifact) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
