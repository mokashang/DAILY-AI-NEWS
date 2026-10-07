# TL;DR — 2026-06-13 (Saturday)

Sixty-second skim. **The frontier crossed three lines in the last 14 days, and you are now living on the other side of them.** (1) **Anthropic raised $65B at a $965B post-money on May 28, then filed a confidential S-1 days later** — overtaking OpenAI for the first time, with run-rate revenue at **~$47B** (3× since February). (2) **OpenAI followed with its own confidential S-1 on June 8** (Goldman + Morgan Stanley + JPMorgan; ~$1T target; Sept-or-Q4 listing). (3) **Anthropic shipped Claude Fable 5 (and the trusted-access-only Mythos 5) on June 9** — its most powerful publicly released model ever, **80.3% on SWE-Bench Pro** (vs Opus 4.8 at 69.2%, GPT-5.5 at 58.6%, Gemini 3.1 Pro at 54.2%), with hard-coded refusals in cyber/bio/chem. Underneath all three: **the IPO wave is becoming the public market itself** — SpaceX began trading on Nasdaq under SPCX on **June 12** at a ~$1.75T target. For you: **T-2 to Anthropic Agent SDK metering (Monday June 15)** — tonight is your last unmetered Saturday for Claude Code subagents. Toggle the credit, ship the artifact, route the cheap legs through Fable's tier.

---

1. **Claude Fable 5 GA + Mythos 5 trusted-access (June 9).** SOTA on nearly all tested benchmarks; **80.3% SWE-Bench Pro** (Opus 4.8 = 69.2%, GPT-5.5 = 58.6%, Gemini 3.1 Pro = 54.2%); **strongest cyber capability of any model in the world** — guarded by hard refusals in cyber/bio/chem (>95% of sessions unaffected, blocked queries fall back to Opus 4.8). Mythos 5 is the unrestricted variant for trusted researchers / Project Glasswing. → [`01` §1](./01-big-lab-moves.md#1-fable-5) `#anthropic #model-release #safety #swe-bench`

2. **Anthropic Series H — $65B at $965B post-money (May 28).** Altimeter + Dragoneer + Greenoaks + Sequoia; **3× the $380B Series G from February**; run-rate revenue **$47B** (was $14B in Feb). **First time Anthropic passes OpenAI in private valuation.** Followed by a **confidential S-1 within days** — October IPO path now firm. → [`01` §2](./01-big-lab-moves.md#2-anthropic-series-h) `#anthropic #funding #ipo #valuation`

3. **OpenAI confidential S-1 filed June 8 — they announced it themselves.** "We expect it to leak so we're just announcing it." Targeting **~$1T** with Goldman + Morgan Stanley + JPMorgan; listing **as early as September, potentially Q4 2026**. Q1 2026: ~$25B annualized revenue, but **lost $1.22 for every $1 earned**. → [`01` §3](./01-big-lab-moves.md#3-openai-s1) `#openai #ipo #s1`

4. **Apple WWDC 2026 — Siri AI rebuilt on Gemini ($1B/yr); EU + China carved out.** Tim Cook's final WWDC keynote, **June 8**. Siri AI is a ground-up rewrite that can read your email/messages/photos and act across apps; iOS 27 / macOS "Golden Gate" / watchOS 27 ship this fall. **The Apple-Gemini licensing deal explicitly excludes the EU's ~450M iPhone users** — sovereignty becomes a product surface, not just a policy thread. → [`01` §4](./01-big-lab-moves.md#4-apple-wwdc) `#apple #wwdc #gemini #siri #sovereignty`

5. **SpaceX began trading on Nasdaq (SPCX) June 12 — ~$1.75T target = largest IPO in history.** With OpenAI + Anthropic S-1s filed, **three of the most valuable private companies in the world are inside a 4-month public-market window.** This is no longer "an IPO wave" — it's a re-pricing of the entire frontier-AI asset class in front of every retail brokerage account. → [`02` §1](./02-new-emerging.md#1-ipo-cluster) `#ipo #public-markets #spacex #re-pricing`

6. **Anthropic ships Scheduled Tasks for AI agents (this week).** Claude can now run recurring agentic tasks on a timer — the consumer/SMB-side mirror of cron-for-agents. Pair with the **June 10 Code w/ Claude Tokyo** keynote and Anthropic's APAC push and you have *the* deployment shape Anthropic is selling: agents that run when you're asleep, on your data. → [`02` §2](./02-new-emerging.md#2-scheduled-tasks) `#anthropic #agents #scheduled #consumer-saas`

7. **Terminal-Bench 2.0 leaderboard (89 tasks, no model finishes all).** Current ranking: **GPT-5.5 = 82.0%, Gemini 3.5 Flash = 76.2%, Claude Opus 4.8 = 74.6%** (Fable 5 numbers landing this week). The new agent eval reality: *frontier models score 65–73% direct; only orchestration + scaffolding pushes them above 80%.* Scaffolding is now the scarce skill. → [`04` §1](./04-research-progress.md#1-terminal-bench-2) `#benchmarks #agents #scaffolding`

8. **Tonight's ONE thing: T-2 to Anthropic Agent SDK metering. Toggle the credit (still manual), re-route to Fable 5 + Sonnet 4.6 + Haiku 4.5, and ship the cost-aware portfolio piece.** → [`03` §1](./03-practical-skills-and-tools.md#1-t-2-metering) `#claude-code #cost #metering #portfolio`

---

## One thing to DO this Saturday

→ **Ship the *Fable-5-aware* version of the dual-model "sanitiser"** ([carried from 2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact)). Swap the orchestrator to **Fable 5** (SWE-Bench Pro 80.3% justifies the model line in the README), keep **Sonnet 4.6 workers** + **Haiku 4.5 verifier**, add a **per-step token-cost table** (now a metered line item Monday morning), and verify against **one real MCP server** the way **Terminal-Bench 2.0 / MCP-Atlas / Toolathlon** demand. **Also: toggle the Agent-SDK credit *before* you log off tonight** — it's still a manual switch in account settings, and Monday is too late.

## Watchlist deltas

- 🟢 **Anthropic $30–50B raise:** **CLOSED — at $65B / $965B post** (3 wks ahead of any consensus). Status flips 🟡→🟢. Watch which LPs got cut and which were anchored.
- 🟢 **Anthropic > OpenAI on business adoption (Ramp):** **superseded** by the valuation crossover — both adoption *and* valuation now lead.
- 🟡 **Anthropic confidential S-1 / October IPO:** **NEW — confirmed filed early June.** Watch the public-S-1 unredact window (~15 days pre-roadshow) and how the $1.25B/mo Colossus bill reads in a prospectus.
- 🟢 **OpenAI confidential S-1:** **FILED June 8.** OpenAI announced it itself. Watch the Sept-vs-Q4 timing call and whether Microsoft's terms get disclosed.
- 🟢 **Claude Opus 4.8 / next Anthropic flagship:** **SHIPPED as Claude Fable 5 + Mythos 5 (June 9).** Watch independent benchmarks (Terminal-Bench 2.0 row pending; Artificial Analysis numbers; SWE-Bench Pro independent re-runs).
- 🟢 **Code w/ Claude Tokyo:** **HELD June 10.** Watch APAC customer logo announcements + which Tokyo demo gets cloned by competitors first.
- 🟡 **Anthropic Agent SDK metering (June 15):** **T-2 days.** Final manual-toggle reminder window.
- 🆕 **SpaceX SPCX trading on Nasdaq:** new thread — the first frontier-adjacent mega-IPO post-prints. Watch first-day-to-first-earnings arc; sets the comp for OpenAI / Anthropic Day-1 pop pricing.
- 🆕 **Apple ↔ Gemini $1B/yr licensing deal (EU excluded):** new thread — sovereignty becomes a product surface; opens the **EU AI sovereignty / on-device / Mistral-as-Apple-fallback** sub-thread.
- 🆕 **Scheduled Tasks for AI Agents (Anthropic):** new thread — watch enterprise/SMB adoption + whether competitors ship "cron-for-agents" within 60 days.
- ⬇️ **Real-tool eval thread (MCP-Atlas / Toolathlon → Terminal-Bench 2.0):** continues; the benchmark is now an actual public leaderboard with frontier-model numbers on it.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Fable 5 release in [`01` §1](./01-big-lab-moves.md#1-fable-5) |
| 20 min | [`01` §2](./01-big-lab-moves.md#2-anthropic-series-h) (Anthropic Series H / S-1) + [`04` §1](./04-research-progress.md#1-terminal-bench-2) (Terminal-Bench 2.0) |
| Today | [`03` §1](./03-practical-skills-and-tools.md#1-t-2-metering) — toggle the credit + re-route |
| This weekend | [`03` §2](./03-practical-skills-and-tools.md#2-artifact) — ship the Fable-5-aware artifact |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
