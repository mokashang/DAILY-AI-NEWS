# TL;DR — 2026-07-12 (Sunday)

Sixty-second skim. **Three things this week: (1) Apple sued OpenAI on Friday — trade-secret theft over hardware. (2) OpenAI shipped the GPT-5.6 family (Sol/Terra/Luna) globally on Jul 10 after a 2-week government-requested trusted-partner-only window. (3) Anthropic's run-rate crossed $30B (from ~$9B end-of-2025), backed by a *3.5-gigawatt* Google+Broadcom TPU commitment that comes online in 2027.** Underneath: the *hardware fight moved to court*, the *compute-supply moat became a filed liability*, and the *nonprofit-fellowship pipeline* (Claude Corps, first cohort closes **this Friday July 17**) opened a real 12-month paid AI on-ramp that fits your ME.md. And Wednesday is a live event: **Gemini 3.5 Pro (2M context, Deep Think reasoning behind $250 Ultra) is scheduled for GA July 17** — the *same day* the Claude Corps cohort-1 window closes.

---

1. **Apple sues OpenAI in the Northern District of California — trade-secret theft, "at every level."** Filed Friday, July 10. Apple names ex-Apple hardware VP **Tang Tan** (now OpenAI hardware chief) and alleges OpenAI coached departing Apple employees on how to evade Apple's exit-security process, plus at least one stolen Apple laptop (ex-employee Chang Liu). Context: OpenAI bought Jony Ive's IO Products for $6.4B; the ChatGPT-in-iOS partnership is now unmistakably over. → [`01` §1](./01-big-lab-moves.md#1-apple-openai) `#apple #openai #hardware #lawsuit`

2. **OpenAI ships GPT-5.6 family globally (Sol / Terra / Luna) on Jul 10.** Two weeks after a US-government-requested "small trusted-partner group" preview; now GA. **Sol** = flagship, tuned for biology / chemistry / cybersecurity, **54% more token-efficient on coding** (per Altman). **Terra** = mid-cost. **Luna** = fastest / cheapest. Paired with **ChatGPT Work** — an agentic productivity surface merging Codex into ChatGPT desktop with a 15-integration plugin directory. → [`01` §2](./01-big-lab-moves.md#2-gpt56) · [`02` §3](./02-new-emerging.md#3-chatgpt-work) `#openai #gpt-56 #agents #chatgpt-work`

3. **Anthropic run-rate crosses $30B (up from ~$9B end-of-2025), backed by a 3.5-GW Google+Broadcom TPU commitment (Anthropic newsroom).** >1,000 customers now spending $1M+/yr annualized. The multi-gigawatt TPU deal comes online in 2027 and sits inside Anthropic's larger **$50B US-compute commitment**. This is the *supply side* of the "labs go public" thread from May — Anthropic is now *revenue-eligible* for a public listing without the growth story faltering. → [`01` §3](./01-big-lab-moves.md#3-anthropic-30b) `#anthropic #compute #tpu #revenue`

4. **Anthropic launched Claude Corps — 12-month paid fellowship, 1,000 fellows, $85K salary + $10K grant, $150M program.** Fellows are trained on Claude by Anthropic + CodePath, then placed **full-time in-person** at a US nonprofit. Anyone 18+ with **<2 years full-time work experience** and US work authorization can apply — **no degree requirement.** **First-cohort applications close July 17 (this Friday); cohort starts October 2026.** This is a directly viable path for the ME.md profile, and the resume signal ("trained on Claude in a paid AI-integration role") is exactly the FDE/Solutions-lane vocabulary. → [`05` §2](./05-career-and-startup.md#2-claude-corps) `#anthropic #fellowship #jobs #new-grad`

5. **Gemini 3.5 Pro GA scheduled for Wednesday July 17.** Ground-up architectural rebuild (not a 2.5 point release). **2M-token context** (2× the frontier), **Deep Think** extended-reasoning mode **gated behind the $250/mo Ultra tier**. Still "widely reported target," not officially posted by Google as of last check — treat as `[rumor]` **until Wednesday's stream lands**. Same day as the Claude Corps cohort-1 close — you'll want the comparison table ready. → [`01` §4](./01-big-lab-moves.md#4-gemini-35-pro) · [`03` §3](./03-practical-skills-and-tools.md#3-io-day-table) `#google #gemini #context #reasoning`

6. **Together AI $800M Series C at $8.3B, led by Aramco Ventures (Jul 1).** Bookings >$1.15B/qtr, open-weight usage 3×, enterprise-inference cost **up to 60× cheaper vs. closed models**, capacity plan **~50× over 5 years**. Signals: (a) *neoclouds* (Together, CoreWeave, Runware) are becoming the shadow AWS of AI; (b) *Aramco* leading a US AI infra round is the sovereign-compute thesis firming up; (c) *open-weight is not dead* — it's the cost floor. → [`02` §1](./02-new-emerging.md#1-together-800m) `#funding #neocloud #open-weights #sovereign`

7. **Claude Sonnet 5 is the practical winner this week (default in Claude Code, 1M context, $2/$10 promo through Aug 31).** Given Opus 4.7's premium and Sonnet 5's coding gains, the **Opus-orchestrator + Sonnet-5-worker split** carried from [2026-05-22/03](../2026-05-22/03-practical-skills-and-tools.md) still holds — but the *cost delta widened* enough that **Sonnet-5-only** now beats mixed for most refactors. → [`03` §1](./03-practical-skills-and-tools.md#1-sonnet5) `#claude-code #sonnet-5 #cost`

8. **Skill read of the week:** the three big stories share one shape. Apple v. OpenAI = *hardware is where the moat goes when models commoditize*. Anthropic $30B + 3.5 GW = *supply, not demand, is the current bottleneck*. Claude Corps = *the labs are training their own hiring pipeline*. If you can't do frontier research, you can *own the integration layer between a frontier model and a real-world workflow* — Claude Corps, FDE roles, and vertical-agent startups are all the same lane wearing three costumes. → [`05` §1](./05-career-and-startup.md#1-integration-layer) `#skills #careers #integration`

---

## One thing to DO this Sunday

→ **Apply to Claude Corps before Friday July 17** ([`05` §2](./05-career-and-startup.md#2-claude-corps)). Even if you don't want the placement, the application is a **structured statement of your Claude-integration thesis**, which is the same statement you'll write for FDE and Solutions applications for the next 12 months. The rubric doubles as your ME.md v2 outline. **Sunday afternoon: 90-minute drafting block.** Also: **prep the Gemini 3.5 Pro vs Claude Sonnet 5 vs GPT-5.6 Sol one-page comparison table**, ready to publish 12:30 PM PT Wednesday July 15 15 minutes after Google's stream ([`03` §3](./03-practical-skills-and-tools.md#3-io-day-table)) — same pattern as the May 20 I/O comparison, same career surface, higher LinkedIn signal because it's the *smaller* Wed-window audience.

## Watchlist deltas

- 🆕 **Apple × OpenAI (US Fed NDCA, trade-secret theft):** new thread — watch (a) whether OpenAI counterfiles (patent-troll defense playbook), (b) whether Sam Altman comments before earnings-quiet-period ties his hands, (c) whether Google/Anthropic quietly poach Apple hardware talent while the OpenAI door is closed.
- 🆕 **GPT-5.6 Sol/Terra/Luna GA (Jul 10):** new thread — pricing card + benchmarks vs Sonnet 5 and Fable 5 not yet compared head-to-head; expect first Artificial Analysis run this week.
- 🆕 **Anthropic $30B run-rate + 3.5-GW Google/Broadcom deal:** new thread — track (a) how the 2027 come-online lines up with the (previously rumored) October 2026 IPO window, (b) whether the "1,000 customers >$1M ARR" claim is validated by independent enterprise trackers (Ramp AI Index next drop).
- 🆕 **Claude Corps first cohort (application closes Jul 17):** new thread — action deadline this Friday; also track (a) how the $85K comp + no-degree gate reprices "AI fellowship" vs Anthropic AI Safety Fellowship, (b) which nonprofit hosts get named — those are next year's "Claude for [vertical]" wedges.
- 🆕 **Gemini 3.5 Pro GA (targeted Jul 17):** new thread — 2M-token context + Deep Think reasoning + $250/mo Ultra gate; still `[rumor]` until Wednesday.
- ➡️ **OpenAI S-1 / Sept 2026 IPO ($852B–$1T range):** carried from [2026-05-22/01 §2](../2026-05-22/01-big-lab-moves.md#2-openai-s1). New wrinkle: the Apple lawsuit is now a **material risk factor** the S-1 will have to disclose. Watch for the disclosure language.
- ➡️ **Anthropic October IPO thread:** carried; the $30B run-rate and 3.5-GW compute deal are the two data points that most bear on it.
- ➡️ **Karpathy → Anthropic pre-training (use-Claude-to-train-Claude group):** carried from [2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy); no public shipped-artifact yet — still watching.
- ➡️ **Together AI $8.3B + open-weight cost floor:** carried & upgraded — the 60× cost delta vs closed-model inference is the number to memorize for interviews.
- ⬇️ **Anthropic Agent SDK metering (moved to June 15, now baked-in):** archive-worthy — the June-15 threshold has already passed. Practical: your cost-audit habit is now the durable skill.
- ⬇️ **Trump AI executive order (was: "postponed"):** archive-worthy until re-scheduled; not on the reported docket this week.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This + Apple v. OpenAI + GPT-5.6 GA in [`01` §1–2](./01-big-lab-moves.md) |
| 20 min | [`01` §3](./01-big-lab-moves.md#3-anthropic-30b) (Anthropic $30B + 3.5 GW) + [`05` §2](./05-career-and-startup.md#2-claude-corps) (Claude Corps rubric) — the two most-actionable |
| Today | [`05` §2](./05-career-and-startup.md#2-claude-corps) — 90-min Claude Corps draft block |
| This week (Mon–Wed) | [`03` §3](./03-practical-skills-and-tools.md#3-io-day-table) — pre-stage the 3-model comparison table for Wed Jul 15 12:30 PM PT publish |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
