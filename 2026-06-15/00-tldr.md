# TL;DR — 2026-06-15 (Monday)

Sixty-second skim. **The metering split is live. Fable 5 is still dark. The two calendar pivots converged on the same day** — so today is the cleanest "before vs after" line in the Anthropic-stack cost model you'll have all year. The **Agent SDK credit pool** went live at 00:01 PT this morning: programmatic Claude now bills against a separate dollar-denominated pool at full API list rates, **claim-to-activate** (silent failure if you skipped the toggle). Meanwhile, **Claude Fable 5 + Mythos 5 remain offline** — Day 4 of the export-control suspension; Anthropic's official statement reframed the directive as "a misunderstanding"; **prediction markets price restoration before July 1 at ~85%**, restoration by June 20 at ~5%. There's also a tail event most coverage missed: even when Fable 5 returns, **the free-on-subscription window ends June 22** — after that, Fable 5 moves into the new credit pool at $10/$50 per 1M tokens. Today is also **WWDC 2026 keynote eve** (Jun 9 was the original WWDC; Apple's "Extensions" SDK demos run through this week — watch for the iOS 27 multi-AI picker reveal).

---

1. **AGENT SDK METERING IS LIVE.** Pro $20 / Max-5x $100 / Max-20x $200 — dollar-denominated, expires monthly, full Anthropic API list rates. **If you didn't toggle the credit pool, your `claude -p` / GitHub Actions / Agent SDK calls are failing right now.** Fix: [yesterday's checklist](../2026-06-14/03-practical-skills-and-tools.md#1-jun15-setup), step 1. → [`03` §1](./03-practical-skills-and-tools.md#1-metering-live) `#agent-sdk #billing #claude-code`

2. **Fable 5 Day 4 offline. Prediction markets pricing the restoration.** Polymarket / Octagon both have **restoration-before-July-1 ~85%, by-June-20 ~5%.** Anthropic's official line is "misunderstanding; working to restore." `isfable5back.com` exists. The S-1 amendment window for the public Anthropic filing will have to address whatever the resolution looks like. → [`01` §1](./01-big-lab-moves.md#1-fable-day4) `#anthropic #fable5 #policy`

3. **The June 22 cliff most outlets missed.** Even when Fable 5 returns: **on June 23 it leaves the bundled Pro/Max/Team/Enterprise plans** and moves into the metered credit pool at $10/$50 per 1M tokens. **Two cost shocks in 8 days.** Adjust your portfolio cost forecast for both. → [`03` §2](./03-practical-skills-and-tools.md#2-jun22-cliff) `#pricing #anthropic`

4. **OpenAI confidential S-1 entering the SEC-comment phase; Anthropic likewise.** Standard 30–60-day quiet-comment window. **Expect ~2 weeks of relative product-side quiet from both labs** as legal capacity gets redirected. → [`01` §2](./01-big-lab-moves.md#2-quiet-window) `#openai #anthropic #ipo`

5. **Practical: the post-metering, post-shutdown 3-line cost rule.** (a) **Opus 4.8 only for orchestration / planning** turns. (b) **Sonnet 4.6 for worker turns** + tool I/O. (c) **Anything you can run locally or on Gemini 3.5 Flash, do.** This single rule is worth roughly a 50–65% bill reduction vs all-Opus tonight — based on the Opus/Sonnet ratio in the [2026-05-22 practical playbook](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) re-priced against the new metering. → [`03` §1](./03-practical-skills-and-tools.md#1-metering-live) `#cost #routing`

6. **WWDC 2026 / iOS 27 multi-AI Extensions SDK.** Apple's June keynote arc (WWDC25 was Jun 9; the developer-breakouts wave continues through this week) is the **second-largest** consumer-AI surface area after I/O — and the **Anthropic-stack hedge story** got a free PR boost from the Fable 5 narrative *exactly* when Apple wants to pitch multi-vendor by design. → [`02` §1](./02-new-emerging.md#1-wwdc) `#apple #extensions #ios27 #multi-ai`

7. **Carry: τ²-Bench + ERL weekend reads** (from yesterday's [`04` §1](../2026-06-14/04-research-progress.md#1-tau2-erl)). If you did the dependency audit + router shim last night per [yesterday's `03` §2](../2026-06-14/03-practical-skills-and-tools.md#2-anthropic-stack-hedge), today is the day to layer the **τ²-style eval surface** onto it. The 20-min upgrade is in [`04` §1](./04-research-progress.md#1-tau2-applied). → [`04` §1](./04-research-progress.md#1-tau2-applied) `#tau2 #benchmarks #applied`

---

## One thing to DO this Monday

→ **8:00–8:10 AM PT — verify the metering toggle landed.** Run `claude api cost --since=24h` (or your account-settings panel). If you see the new "Agent SDK Credits — Available: $X" line, you're in. If the call errors with `credit_pool_not_claimed`, go back to yesterday's checklist step 1. **Take 5 minutes; this is your morning's most expensive non-action if missed.**

→ **(Carryover from yesterday)** — finish the multi-vendor router shim from [2026-06-14/03 §2](../2026-06-14/03-practical-skills-and-tools.md#2-anthropic-stack-hedge) if you didn't ship it last night. Today's commit message: `"metering-live: shim verified against new Agent SDK billing"`.

## Watchlist deltas

- 🟡 **Anthropic Fable 5 / Mythos 5 shutdown:** Day 4. Prediction markets: by-July-1 ~85%, by-June-20 ~5%. New angle: the June 22 free-on-subscription cliff still happens regardless of restoration status.
- 🟢 **Anthropic Agent SDK metering: LIVE** (was 🟡 T-MINUS 1 yesterday). Watch for: (a) percent of programmatic users who missed the toggle and broke this morning, (b) router-SDK community responses, (c) Zed / Cursor / GitHub Actions vendor-side updates.
- ➡️ **OpenAI confidential S-1 (filed Jun 8) / Anthropic confidential S-1 (filed Jun 1):** entering quiet SEC-comment windows. Expect 2–4 weeks of relative product silence.
- 🆕 **June 22 Fable 5 subscription cliff:** new sub-thread — when Fable 5 returns to bundled Pro/Max/Team/Enterprise, it leaves them on June 23.
- ➡️ **WWDC 2026 / iOS 27 Extensions SDK:** developer-breakout week is live; watch for multi-vendor framing references in the Apple AI-narrative.
- ➡️ **Gemini 3.5 Pro launch window (Jun 23 / Jun 30):** prediction-market favorite remains late June; the Fable 5 outage shortens Google's window for the cheapest competitive-narrative moment.
- ➡️ **Grok 5 / SpaceXAI V9-Medium mid-June:** still 33% probability of shipping by June 30; talent departures continue to be the structural concern.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. |
| 5 min | This file + [`03` §1](./03-practical-skills-and-tools.md#1-metering-live) (verify the toggle) |
| 20 min | Add [`04` §1](./04-research-progress.md#1-tau2-applied) (the τ²-Bench-applied-to-your-shim upgrade) |
| Tonight | [`05` §1](./05-career-and-startup.md#1-week-execution) — the Mon→Fri 5-application + 3-DM execution plan |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
