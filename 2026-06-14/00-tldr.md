# TL;DR — 2026-06-14 (Sunday)

Sixty-second skim. **The state finally took a frontier model OFFLINE — and it was the one you bet on.** On **Friday June 12** the Trump administration issued an export-control directive that forced Anthropic to **suspend global access to Claude Fable 5 + Mythos 5**, less than **72 hours after Fable 5 launched** (June 9) and **48 hours after Pliny the Liberator's viral jailbreak** (June 10). Anthropic disputes the jailbreak finding and complied only because the directive named "any foreign national, including Anthropic's own employees" — making partial restriction operationally impossible. The fallout: India treats it as a "sovereign-AI wake-up call" (Sridhar Vembu: "globalisation is dead"); enterprises scramble to Opus 4.8 fallback; the **June 2 executive order** ([the one postponed on May 22, then signed with 30-day not 90-day pre-release review](../2026-05-22/01-big-lab-moves.md#1-eo-postponed)) just had its first live invocation. This is the single biggest validation of your `WATCHLIST.md` "pre-deployment-eval / AI-assurance" career-lane thesis — and the single biggest hit to the Anthropic-stack focusing decision. For you, **today's edition is the one that reframes the May review.**

---

1. **Anthropic suspends Fable 5 + Mythos 5 globally — US export-control directive.** Trump-admin Commerce Dept directive (issued late June 11, effective ~22:00 PT June 12) cites cyber-jailbreak risk + "any foreign national, incl. Anthropic employees" — Anthropic disabled access for *all* customers (≠ just foreign) to comply. **Fable 5 was live for 3 days** (launch → shutdown). Anthropic statement disputes the directive's basis; **Opus 4.8 remains live and is the automatic fallback** in Claude Code / API. → [`01` §1](./01-big-lab-moves.md#1-fable-shutdown) `#anthropic #policy #export-controls #fable5 #mythos5`

2. **The June 2 Trump executive order is the legal hook.** "Promoting Advanced AI Innovation and Security" — signed June 2 (12 days late vs the May 22 postponement), voluntary **30-day pre-release model share** (labs lobbied 14 days; original draft 90), Treasury-led cyber-clearinghouse, and a **"covered frontier model"** export-control trigger. The Fable 5 shutdown is the **first live invocation** of that trigger. → [`01` §2](./01-big-lab-moves.md#2-eo-signed-and-invoked) `#policy #eo #export-controls`

3. **OpenAI confidential S-1 filed June 8, Anthropic filed June 1 — the IPO wave is REAL.** OpenAI (Goldman + Morgan Stanley, $852B–$1T target, Sept–Nov 2026 window). Anthropic (Oct 2026 target, $380B). **But the Fable 5 shutdown lands on Anthropic's S-1 timing like a brick** — every "regulatory risk" disclosure just got an empirical example. → [`01` §3](./01-big-lab-moves.md#3-ipo-wave-vs-shutdown) `#openai #anthropic #ipo`

4. **TOMORROW: June 15 Agent SDK metering split goes live.** Programmatic Claude (Agent SDK, `claude -p`, GitHub Actions, third-party agents) leaves your $20/$100/$200 subscription bucket → **separate dollar-denominated credit pool at full API list rates**, **claim must be manually toggled** (silent failure if you skip). With Fable 5 unavailable, the cost-router decision collapses to **Opus 4.8 orchestrator + Sonnet 4.6 workers** (the Karpathy-team play for the next 90 days). → [`03` §1](./03-practical-skills-and-tools.md#1-jun15-setup) `#claude-code #billing #agents`

5. **Anthropic Bengaluru office formally opens; India = #2 market — and now the loudest pushback voice.** Bengaluru office opened (post-Feb 2026 announcement); India run-rate revenue **doubled since Oct '25**; partners include Air India (Claude Code for custom software), Cognizant (Claude deployed to 350K employees), Razorpay (risk systems). **And then the Fable 5 shutdown reframes the entire narrative as a sovereign-AI cautionary tale.** → [`01` §4](./01-big-lab-moves.md#4-india-office) `#anthropic #india #sovereign-ai`

6. **Funding: agentic-security category keeps printing — Pi Security $35M (Jun 10), Poetic $50M Series A (Jun 12), Trustap $10M.** Pi Security = agentic AI security (SF); pairs with the [Exaforce $125M (2026-05-22)](../2026-05-22/02-new-emerging.md#2-exaforce). **The pattern: every shutdown/incident → next funding round in agent-security.** → [`02` §1](./02-new-emerging.md#1-funding-week) `#funding #agentic-security`

7. **Practical: the 90-day "Anthropic-stack" hedge re-evaluation.** Anthropic-first stays correct on capability/depth — but the shutdown forces a **fallback discipline upgrade**. Concrete moves: (a) audit every `model=claude-fable-5` reference in your repos tonight; (b) add a 4-line model-router shim (`fable5 → opus-4.8`); (c) keep a **GPT-5.5 Codex + Gemini 3.5 Flash** parallel eval running for any prod-critical agent. Multi-vendor as production discipline = ME.md was right, just sooner than expected. → [`03` §2](./03-practical-skills-and-tools.md#2-anthropic-stack-hedge) `#focus #anthropic #portfolio`

8. **Research: τ²-Bench and ERL (Experiential Reflective Learning) are the two papers actually worth reading this weekend.** τ²-Bench (Sierra) — dual-control conversational agent eval (Telecom/Retail/Airline; agent + user both have tools; Dec-POMDP formalism). ERL (March arXiv, just clearing peer review) — agents that generate heuristics from trajectories at test time, +7.8% on Gaia2 over ReAct. These are the **measurement upgrades** that will show up in interviews by Aug 2026. → [`04` §1](./04-research-progress.md#1-tau2-erl) `#benchmarks #agents #arxiv #self-improvement`

---

## One thing to DO this Sunday (and one tomorrow morning)

→ **Tonight (60 min):** Run the **Fable-5 dependency audit**: `grep -rn "claude-fable-5\|fable-5\|claude-mythos-5" .` across your portfolio repos. Replace with `claude-opus-4-8` as default + a 4-line router shim (see [`03` §2](./03-practical-skills-and-tools.md#2-anthropic-stack-hedge)). Commit & push — this is the **resume-quality artifact** the shutdown just created for you ("shipped a multi-vendor fallback before the market reacted").

→ **Tomorrow 8:00 AM PT (T-0 to metering):** **Toggle the Agent SDK credit pool** in your Anthropic account settings ([`03` §1](./03-practical-skills-and-tools.md#1-jun15-setup)) **and** open `WATCHLIST.md` to convert the "Anthropic shutdown" thread into a new daily check — for the next 2 weeks, "is Fable 5 restored yet?" is the most important pricing/availability question in your stack.

## Watchlist deltas

- 🆕🚨 **Anthropic Fable 5 + Mythos 5 GLOBAL SHUTDOWN (Jun 12):** new top-priority thread — watch for (a) re-instatement timeline, (b) whether `claude-opus-4-8` itself gets retroactively covered, (c) whether the export-control list expands to GPT-5.5 / Gemini 3.5 Pro, (d) Anthropic's appeal / legal action.
- 🟢 **Trump AI executive order — SIGNED June 2** (was 🟡 STALLED on 2026-05-22). Status: now active and **already invoked once**. The 90-day pre-release review became **30-day voluntary share**; the cyber-clearinghouse survived; the "covered frontier model" export-control hook is the live policy lever.
- 🟢 **OpenAI confidential S-1 — FILED June 8** (was 🟡 NEW on 2026-05-22). Goldman + Morgan Stanley, Sept–Nov window, financials private until ~15 days pre-roadshow.
- 🟢 **Anthropic confidential S-1 — FILED June 1** (was 🟡 on 2026-05-22). October-2026 target firmer; Fable 5 shutdown is a fresh "regulatory-risk" disclosure event the public S-1 will have to address.
- 🆕 **India sovereign-AI thread:** new — Sridhar Vembu's "globalisation is dead" framing + Bengaluru office opening + 2× revenue growth = a real wedge for India-stack AI startups.
- 🆕 **Pi Security $35M (Jun 10) / Poetic $50M Series A (Jun 12):** agentic-security category continues to compound (now: Exaforce → Pi → next).
- ⬇️ **Anthropic Agent SDK metering (June 15):** T-MINUS 1 DAY — toggle the credit pool tomorrow morning.
- ➡️ **Gemini 3.5 Pro June launch (Jun 23 or 30 prediction markets):** still live; the shutdown opens a 2-week price-cut / "reliability narrative" window for Google.
- ➡️ **Grok 5 / SpaceXAI V9-Medium mid-June launch:** prediction markets give 33% by June 30; the 50+ researcher exits since Feb 2026 absorption are the real signal.
- ➡️ **Karpathy → Anthropic pre-training team:** thread continues from 2026-05-22; the team's first ship is now overdue.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-fable-shutdown) (the shutdown narrative end-to-end) |
| 20 min (recommended) | [`01` §1–4](./01-big-lab-moves.md) + [`04` §1](./04-research-progress.md#1-tau2-erl) — what happened + the measurement upgrade that will outlast the news cycle |
| Tonight | [`03` §2](./03-practical-skills-and-tools.md#2-anthropic-stack-hedge) — the dependency audit + router shim (60 min, ships an artifact) |
| Tomorrow 8 AM PT | [`03` §1](./03-practical-skills-and-tools.md#1-jun15-setup) — Agent SDK credit-pool toggle |
| Weekend | [`05` §1](./05-career-and-startup.md#1-focusing-reeval) — the focusing-decision re-evaluation (because today is when "Anthropic-stack" stopped being a no-brainer) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
