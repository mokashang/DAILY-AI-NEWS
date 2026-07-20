# TL;DR — 2026-07-16 (Thursday)

Sixty-second skim. **The compute-buildout is ratified in real numbers, and Google is T-1 to its comeback shot.** **TSMC's Q2 earnings landed this morning** at a **record $40.2B in revenue** — HPC (i.e. AI) now **66% of total revenue** (up from 61% flagged in yesterday's [2026-07-15/00](../2026-07-15/00-tldr.md)), net profit **+77.4% YoY**, N3 sold out through year-end and 2026 capex raised. **The buildout is not decelerating — it is accelerating.** In the same 24 hours: **Gemini 3.5 Pro is T-1 to a targeted July 17 GA** (2M context + Deep Think reasoning, on the ground-up rebuild that delayed it a month), and **the DeepSeek deprecation clock is T-8** (migration deadline July 24 15:59 UTC — silent capability downgrade if you pick v4-pro instead of v4-flash). For you: **today is a publishing day** — the three-vendor cost table from your July-9 exercise now needs Gemini 3.5 Pro pricing added by Friday close to actually be useful.

---

1. **TSMC Q2 2026 earnings — $40.2B revenue (record), HPC = 66%, net profit +77.4%.** Beat the $40B street estimate; June alone was +67.9%; N3 sold out through year-end; **2026 capex raised to $52–56B**; full-year revenue guide raised to **>30% USD growth**. **HPC (AI) share stepped up from 61% → 66% in one quarter** — the buildout is *still accelerating*, not plateauing. Direct read-through: **NVIDIA Blackwell, AMD MI-series, and every hyperscaler custom accelerator all fab at TSMC**; supply cap has not moved. → [`01` §1](./01-big-lab-moves.md#1-tsmc-q2) `#tsmc #compute #chips #earnings`

2. **Gemini 3.5 Pro T-1 — July 17 GA target (2M ctx + Deep Think).** Public API still shows `gemini-3.5-flash` and `gemini-3.1-pro-preview` as of July 13; no `gemini-3.5-pro` endpoint yet. Expected pricing (enterprise preview leaks): **$12–15 / 1M input · $36–45 / 1M output**, with long-context surcharges above 200K. If it ships tomorrow as targeted, it is **Google's first frontier release since the DeepMind exodus** ([2026-07-10/01](../2026-07-10/01-big-lab-moves.md), [2026-07-11/01](../2026-07-11/01-big-lab-moves.md)); if it slips a second time, the "Google can't ship a flagship anymore" narrative hardens for Q3. → [`01` §2](./01-big-lab-moves.md#2-gemini-pro-t1) `#google #gemini #models #comeback`

3. **DeepSeek deprecation T-8 (deadline Fri July 24 15:59 UTC).** Migration mapping is **NOT symmetric** — `deepseek-reasoner` → `v4-flash`, **NOT `v4-pro`** (per [2026-07-13/00](../2026-07-13/00-tldr.md)'s flag). Choose `v4-pro` and you get a **silent capability downgrade** at the same billing. If you have anything running on DeepSeek: **audit and update the model string today**, not next Wednesday. → [`03` §4](./03-practical-skills-and-tools.md#4-deepseek-deprecation) `#deepseek #migration #deadline`

4. **FLI Summer 2026 AI Safety Index — Anthropic top at C+ (no A/B awarded).** Reference doc landed July 7. **Anthropic C+ (leads 5/6 domains), OpenAI + Google DeepMind C, Meta D+, xAI + DeepSeek + Mistral F.** The **"moving goalpost"** finding — top-4 labs weakened unilateral-pause pledges to be *competitor-contingent* — is the durable takeaway. The 37-indicator rubric is now the vocabulary your resume + LinkedIn should be using this week. → [`01` §3](./01-big-lab-moves.md#3-fli-safety-index) · [`05` §1](./05-career-and-startup.md#1-assurance-lane) `#safety #assurance #vocabulary #policy`

5. **Anthropic hiring / infra thread carries — Blomfield → Compute (announced Jul 13) + Samsung 2nm talks (Jul 2, tracked in [07-14/01 §2](../2026-07-14/01-big-lab-moves.md) + [07-14/01 §3](../2026-07-14/01-big-lab-moves.md)).** Today's marginal update: **read Blomfield's move as *sequenced* with the Samsung talks** — an operator-founder joining Compute *just after* the first custom-chip conversation started is not accidental. → [`01` §4](./01-big-lab-moves.md#4-anthropic-carry) `#anthropic #talent #compute #silicon`

6. **Claude Cowork on phone + Routines — the productization is done.** Cowork went cross-device / cloud-native on [2026-07-07](../2026-07-10/01-big-lab-moves.md) with iOS/Android on [2026-07-10](../2026-07-11/01-big-lab-moves.md). Today it is just *there* — and **doubled usage limits still run through Aug 5**. If you haven't wired a scheduled task yet, this weekend is the last cheap window. → [`03` §1](./03-practical-skills-and-tools.md#1-cowork-mobile) `#cowork #agents #scheduled-tasks`

7. **Practical of the week: the 4-vendor cost table + one scheduled task = one artifact answering four interview questions.** Refresh the [2026-07-09](../2026-07-09/03-practical-skills-and-tools.md) three-model routing table with **Gemini 3.5 Pro pricing** (add tomorrow morning if it ships), publish the delta by Friday close. Wire one Cowork scheduled task ([`03` §1](./03-practical-skills-and-tools.md#1-cowork-mobile)) that *runs* the routing benchmark weekly. One artifact answers **orchestration + cost + verification + scheduling** — every hire-signal of 2026, in one repo. → [`03` §1](./03-practical-skills-and-tools.md#1-cowork-mobile) `#claude-code #routing #cost #scheduled-tasks`

8. **Read of the week: today's TSMC + tomorrow's Gemini 3.5 Pro + this weekend's DeepSeek deadline are one story.** The compute-supply cap is *not* the bottleneck (TSMC beat + raised); the *model-supply cadence* is (Google's month-long delay was the outlier of Q3; DeepSeek's forced migration is the tail). This is the macro to price into every founder-wedge or job-target bet you make in the next 60 days: **it is a model-consumer's market**. → [`05` §4](./05-career-and-startup.md#4-macro-read) `#macro #compute #models`

---

## One thing to DO this Thursday

→ **Add today's TSMC print + tomorrow's Gemini 3.5 Pro line to your live cost-router table** ([2026-07-09](../2026-07-09/03-practical-skills-and-tools.md) baseline). Publish the updated 4-vendor table + one paragraph on "what the TSMC Q2 read-through means for 2026-H2 model pricing" by **Friday 5 PM local**. That post lands in every recruiter's search for "cost-aware routing" the following week. Cross-reference: [`03` §1 Cowork scheduled task](./03-practical-skills-and-tools.md#1-cowork-mobile) so the *table itself* runs weekly.

## Watchlist deltas

- 🆕 **TSMC Q2 2026 print (Jul 16):** $40.2B revenue record; **HPC 61% → 66% in one quarter**; capex 2026 → $52–56B; N3 sold out through year-end. Watch H2 CoWoS packaging capacity + N2 (2nm) yield ramp for 2027 supply.
- 🆕 **Gemini 3.5 Pro GA target Jul 17:** T-1. Watch (a) does it actually ship? (b) exact pricing vs the $12–15/$36–45 leak; (c) 2M-context practical performance vs. Sonnet 5's 1M / GPT-5.6 Terra; (d) Deep Think ROI vs. Anthropic's Extended Thinking. If it slips again the Google-frontier-comeback narrative dies.
- ⚠️ **DeepSeek deprecation Jul 24 15:59 UTC (T-8):** `reasoner` → `v4-flash` **not** `v4-pro` (silent capability downgrade). Audit + migrate today.
- ➡️ **FLI Summer 2026 Safety Index:** still the reference doc; use the 37-indicator vocabulary in resume + LinkedIn.
- ➡️ **Blomfield → Anthropic Compute (Jul 13):** carries from [2026-07-14/01 §2](../2026-07-14/01-big-lab-moves.md). Now read *sequenced with* the Samsung talks.
- ➡️ **Anthropic × Samsung 2nm SF2 custom chip:** carries; volume 2028+; today just adds "an operator now owns the roadmap decisions."
- ➡️ **Claude Cowork mobile + Routines:** carries; the productization is done, artifact-shipping window is now.
- ➡️ **OpenAI IPO slipping to 2027:** carries from [2026-07-10/01](../2026-07-10/01-big-lab-moves.md), [2026-07-11/01](../2026-07-11/01-big-lab-moves.md).
- ➡️ **Claude for Teachers (Jul 14 launch):** carries from [2026-07-15/00](../2026-07-15/00-tldr.md); 6th Anthropic vertical.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1 TSMC Q2 read](./01-big-lab-moves.md#1-tsmc-q2) — the *actual* number that priced the AI-buildout thesis |
| 20 min | [`01` §1–2 TSMC + Gemini T-1](./01-big-lab-moves.md) + [`04` §1 Self-Evolving Certificates](./04-research-progress.md#1-self-evolving-certs) — the compute story + the reliability story |
| Today | [`03` §4 DeepSeek migration](./03-practical-skills-and-tools.md#4-deepseek-deprecation) — 5-minute audit, T-8 to silent-downgrade risk |
| Tonight | [`03` §1 Cowork scheduled-task cookbook](./03-practical-skills-and-tools.md#1-cowork-mobile) — the artifact of the week |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
