# TL;DR — 2026-06-19 (Friday)

Sixty-second skim. **Day 8 of Fable 5 dark. T-3 to the June 22 cliff. T-~7 to GPT-5.6.** The week wraps with all three threads still live and a fourth — the G7 Évian communiqué (signed June 17) — now on the desk to read. Anthropic's **Fable 5 + Mythos 5** remain globally suspended for an 8th consecutive day; Polymarket / Octagon now price restoration-by-July-1 at ~75% (down from 85% earlier in the week) and restoration-by-June-20 at ~5%. Whether or not Fable returns, the **June 22 pricing cliff still lands** — when access is restored, Fable 5 = $10/$50 per 1M tokens (the free-on-subscription window dies). **OpenAI shipped Deployment Simulation on June 16** ([`2026-06-18/01 §2`](../2026-06-18/01-big-lab-moves.md#2-deployment-sim)) as launch infra for **GPT-5.6, now consensus "next week"** (Polymarket ~83% by June 30). And **Anthropic Seoul Day 2** is showing the first APAC enterprise-deployment cadence — NAVER / Samsung SDS / LG CNS are publicly committing to Claude Code rollouts in a single news cycle. For you: this is the weekend to **finish the multi-vendor router shim** before Monday's billing window opens *with* a metering-priced bill *plus* a Fable 5 restoration / June 22 repricing event landing inside it.

---

1. **Fable 5 / Mythos 5 — Day 8 dark; ~75% restored by July 1; ~5% by June 20.** Anthropic's official line: "a misunderstanding, working to restore." Polymarket / Octagon prices have **softened** through the week (85% → 75% by-July-1). What's not in question: **the June 22 cliff lands regardless** ($10/$50 per 1M tokens once restored), so Monday opens with a second cost shock on top of metering. → [`01` §1](./01-big-lab-moves.md#1-fable-day8) `#anthropic #export-control #cliff #risk`

2. **GPT-5.6 launch window opens Monday-ish.** OpenAI chief scientist Jakub Pachocki called it a "meaningful improvement" on June 10–11; testing of the Pro variant (longer processing times) was confirmed June 17–18; Deployment Simulation (1.3M user-replay) is the launch-day safety harness. **Watch benchmarks Mon AM PT:** SWE-bench Verified, Terminal-Bench 2.0, FrontierMath T4, deep-research evals. → [`01` §2](./01-big-lab-moves.md#2-gpt56-imminent) `#openai #gpt-5-6 #launch`

3. **G7 Évian communiqué (June 17) — what actually landed.** AI section reaffirmed the Hiroshima Process, formalized **voluntary frontier-model deployment codes**, named **child safety + biosecurity (synthetic DNA)** as priority risks, dodged binding export-control language. Stress-test of the international AI governance scaffolding under live use; **the bio-threats letter to Congress was the unified industry ask** to come out of the working lunch. → [`01` §3](./01-big-lab-moves.md#3-g7-communique) `#policy #g7 #governance #biosecurity`

4. **Anthropic Seoul Day 2 — enterprise commitments stack.** Following yesterday's office-opening + MOU news ([`2026-06-18/01 §1`](../2026-06-18/01-big-lab-moves.md#1-seoul)), today's confirmations: NAVER Claude-Code rollout to its full eng org; Samsung SDS + LG CNS on Bedrock-in-region; Hanwha private deployment; Channel Corp distribution to 230K Korean SMBs. **APAC is a hiring map now**, not a sales tour. → [`02` §1](./02-new-emerging.md#1-seoul-day2) `#anthropic #apac #integration-eng`

5. **Agent SDK metering Day 5 — billing shapes settle.** First-week reports converge: **12×–175× realized cost increases per workload class** depending on whether subagents-spawn-subagents was throttled. The 5-line `fallbackModel` fix ([`03` §1](./03-practical-skills-and-tools.md#1-router-shim)) is now load-bearing — without it, Monday's bill on Fable 5's $10/$50 tier becomes a wholly different conversation. → [`03` §1](./03-practical-skills-and-tools.md#1-router-shim) `#claude-code #cost #metering`

6. **Practical: ship the 4-line multi-vendor router shim before Monday open.** Opus 4.8 (planner) → Sonnet 4.6 (workers) → Haiku 4.5 (verifier) → GPT-5.5 (fallback) → Gemini 3.5 Flash (cheap leg). With `fallbackModel` configured. With a 30-prompt eval harness. **One weekend, three FDE-interview answers (orchestration · cost · verification).** → [`03` §1](./03-practical-skills-and-tools.md#1-router-shim) `#playbook #portfolio #weekend-artifact`

7. **Research: deep-research benchmark wave + RL-as-sparse-policy-selection.** **DeepResearch Bench · AutoResearchBench · DREAM · FinDeepResearch** — top LLMs hit only **9.39%** on AutoResearchBench's Deep Research task (huge gap = huge wedge). **"Rethinking RL for LLM Reasoning: Sparse Policy Selection, Not Capability Learning"** reframes the entire reasoning-RL field. → [`04` §1](./04-research-progress.md#1-deep-research-eval) `#research #benchmarks #rl #deep-research`

8. **Skill read of the week:** the value of a CS-grad-student portfolio in Q3-2026 is **"I can run a multi-vendor agent team safely, cheaply, and verifiably *during a regulatory disruption*."** Fable 5 + metering + GPT-5.6 launch in the same week is the live drill. Use it. → [`05` §1](./05-career-and-startup.md#1-week-summary) `#skills #careers`

---

## One thing to DO this Friday

→ **Set Sunday-night aside (3 hours, no calls) for the router-shim weekend sprint.** Goal: one repo, one demo gif, four lines of routing config, one 30-prompt eval harness, one cost table. Push it Sunday 10 PM PT so it's already live before **Monday's GPT-5.6 launch news cycle / metering second-week bill / potential Fable 5 restoration event** all land. The Monday-morning narrative is going to be loud; you want your artifact in the index *before* the narrative, not after.

## Watchlist deltas

- 🟡-stalled **Fable 5 / Mythos 5 export-control restoration:** Day 8 dark; restoration odds *softened* this week (85% → 75% by July 1). Plan around it not coming back before Monday.
- 🆕 **June 22 cliff (T-3):** $10/$50 per 1M tokens on Fable 5 the moment it returns. Pre-budget every existing Fable-5-targeting agent script.
- 🆕 **GPT-5.6 launch (consensus next week, ~Polymarket 83% by June 30):** publish your comparison table within **48 hours of GA** to catch the news cycle. Pre-stage the benchmarks list this weekend.
- ➡️ **G7 Évian communiqué (signed June 17):** read the AI section + biosecurity clause; map them onto your pre-deployment-eval position paper.
- ➡️ **Anthropic Seoul / APAC build-out:** Day 2 today; the Friday weekly rollup ([`weeks/`](../weeks/)) will index the first week of new APAC postings — set a saved search on **Anthropic Seoul / Bengaluru / Tokyo Solutions Engineer**.
- ➡️ **Agent SDK metering Day 5:** the cost-routing playbook is now load-bearing; if you haven't redone the [2026-05-22 cost trace](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) against the new bill, this is the weekend.
- ➡️ **Karpathy → Anthropic team (Day ~31):** still no public artifact; watch for a first paper or eval drop in the next 1–2 weeks.
- ➡️ **OpenAI / Anthropic S-1 amended-filing window:** Aug-1 EO-framework deadline + Aug-8-ish OpenAI quiet-window exit; both labs in the public-prep run-up.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1 Fable 5 Day 8](./01-big-lab-moves.md#1-fable-day8) + [`01` §2 GPT-5.6 launch window](./01-big-lab-moves.md#2-gpt56-imminent) |
| 20 min | [`03` §1 router-shim sprint plan](./03-practical-skills-and-tools.md#1-router-shim) — set up tonight, execute Sunday |
| Today | [`05` §3 weekend-artifact plan](./05-career-and-startup.md#3-weekend-sprint) |
| Weekend | Ship the router shim + read one of DeepResearch Bench / FinDeepResearch / "Rethinking RL" ([`04`](./04-research-progress.md)) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
