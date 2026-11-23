# TL;DR — 2026-09-11 (Friday)

Sixty-second skim. **The model-fatigue week ends with Anthropic filing.** Confirming Thursday's window-opens signal, **Anthropic filed its S-1 today** — bookrunners **Goldman Sachs / Morgan Stanley / JPMorgan**, target listing NYSE, filing discloses **Claude Code at ~46% of TTM revenue** ($46B annualised as of Aug close; **~$21B TTM attributable to Claude Code alone**) — the first hard number on the developer-tools business inside a frontier lab, and it decisively answers Thursday's `01` §2 open question. **OpenAI filed its Rule 26 response** in Apple v OpenAI ahead of the Oct 1 hearing — includes a limited admission that some Slack-channel logs were deleted per retention policy, still contests evidence-destruction framing. **Braintrust raised $85M Series B at $1.1B** for LLM-eval infrastructure — the first funded round on the model-fatigue wedge you saw in yesterday's [`02` §3](../2026-09-10/02-new-emerging.md#3-model-fatigue-tooling). For you: **the router artifact you shipped Thursday now has a category-consolidator on top of it. Extend it this weekend before Braintrust ships a competing OSS reference.**

---

1. **Anthropic S-1 filed — Claude Code = ~46% of ARR, ~$21B TTM.** Goldman / MS / JPM bookrunners; NYSE ticker (Anthropic reserved "ANTH"); ~4-week roadshow expected. First frontier-lab S-1 in market. **Confirms the Thursday thesis** — Claude Code IS the business — and repriches every developer-tools-adjacent role at the lab. → [`01` §1](./01-big-lab-moves.md#1-anthropic-s1) `#anthropic #ipo #s1 #claude-code`

2. **Apple v OpenAI — OpenAI's Rule 26 response includes a limited Slack-log admission.** Retention-policy deletion of channel logs (not documents / not code) — OpenAI will argue routine, Apple will argue selective. Judge Davila's Oct 1 hearing now has a concrete disputed fact, not just an allegation. Sanctions probability up. → [`01` §2](./01-big-lab-moves.md#2-apple-openai-response) `#openai #apple #litigation #hardware`

3. **OpenAI leadership: Chief Strategy Officer Jason Kwon departs; interim role for Sarah Friar.** Third named C-suite departure in six weeks. **Talent-loss + Anthropic-going-first = the labor market is more asymmetric this Friday than it was on Monday** — recruiter effort should tilt Anthropic-ward 60/40, per Thursday's `01` §4. → [`01` §3](./01-big-lab-moves.md#3-openai-departures) `#openai #talent`

4. **Braintrust $85M Series B at $1.1B — first funded eval-infra round of the fatigue era.** Sequoia + Greylock + Index; Braintrust now the front-runner in the eval / router / cost-observability category. Their public roadmap: **model-agnostic eval SDK, cost trace, 5-case-suite template.** They just commoditized the router artifact spec — **your differentiator now has to be verticalized cases + a live leaderboard**, not the shim. → [`02` §1](./02-new-emerging.md#1-braintrust-series-b) `#funding #evals #tooling #router`

5. **Meta acqui-hires eval startup Freeplay (~$180M).** The eval wedge is consolidating fast — Meta now has an internal-first eval stack, mirroring the Google/Vertex Evaluation SKU. Every big lab now has an eval offering; **the OSS reference implementation gap remains open, and that's where your weekend goes.** → [`02` §2](./02-new-emerging.md#2-meta-freeplay) `#meta #ma #evals`

6. **Practical: extend the router with a cost dashboard tonight — the "receipt" that beats Braintrust's demo.** The three-hour weekend build: SQLite log → daily aggregation → live public dashboard (Streamlit or Observable) → one screenshot / week on LinkedIn. **A public cost-savings receipt from real traffic is the one artifact Braintrust cannot fake.** → [`03` §1](./03-practical-skills-and-tools.md#1-cost-dashboard) `#claude-code #router #cost #evals`

7. **Practical: the S-1-informed job list — the 12 Anthropic reqs to apply to this week.** From the S-1's segment breakdowns, you can now read which teams are hiring at what pace. **Claude Code + Solutions + Applied AI absorb ~58% of open reqs.** Full list, with per-role prep note, in [`03` §2](./03-practical-skills-and-tools.md#2-anthropic-req-list) `#anthropic #hiring #fde #applied-ai`

8. **Research: arXiv 2601.07822 "Continual Evaluation for LLM Agents" — the missing eval piece for evolving-envs.** Answers the "how do you eval an agent that runs for weeks?" question by proposing a **rolling-window eval protocol** with drift-detection. Pairs with Thursday's 2511.04898 and 2512.13564 as the third leg of the "lifelong agent" research frame. → [`04` §1](./04-research-progress.md#1-continual-eval) `#arxiv #evals #agents #memory`

9. **Career: end-of-week checkpoint — 4 artifacts, 5 apps, 2 papers.** If you followed Thursday's plan: (a) router + eval suite shipped Tue; (b) cost dashboard shipped tonight; (c) 5 apps out (3 Anthropic + 2 startup); (d) two arXiv papers read. **If you're behind — do just tonight's cost dashboard.** That single move keeps the compounding intact. → [`05` §3](./05-career-and-startup.md#3-checkpoint) `#careers #artifacts #checkpoint`

10. **The re-price of Friday:** eval-authoring skills stayed up but got **crowded by Braintrust + Meta** — verticalized eval design (legal, finance, code, healthcare) is now the scarce version. **If your 5-case eval suite is generic, replace three cases this weekend with vertical-specific cases from a public workflow you actually use.** → [`05` §2](./05-career-and-startup.md#2-reprice-friday) `#skills #evals #vertical`

---

## One thing to DO this Friday

→ **Extend the router with a public cost dashboard — 3 hours.** SQLite table of per-request `(ts, model, task_type, input_toks, output_toks, cost_usd, latency_ms, quality_score)`, daily aggregation into `costs.csv`, one-page Observable / Streamlit dashboard reading that CSV, deployed to `<yourhandle>.github.io`. Post the screenshot to LinkedIn with **one caption sentence and the receipt**: "Router shaved $X/1K requests off Fable 5.1 for coding tasks vs Mythos 5.1 — data + dashboard here." That's a differentiator Braintrust's demo cannot replicate, because they can't show YOUR traffic. Details in [`03` §1](./03-practical-skills-and-tools.md#1-cost-dashboard).

## Watchlist deltas

- 🆕 **Anthropic S-1 filed (Sept 11):** the biggest disclosure event of 2026 for developer-tools comp bands and hiring-plan mapping. Watch: (a) the roadshow date, (b) whether Claude Code gets a segment-margin line, (c) OpenAI's counter-move.
- 🆕 **Braintrust $85M / $1.1B:** first funded eval-infra round. Watch: their OSS release cadence, whether Anthropic bundles a competing SKU.
- 🆕 **Meta acqui-hires Freeplay (~$180M):** eval wedge consolidating in-house at large labs.
- 🆕 **OpenAI Kwon departure + Friar interim:** third C-suite exit in six weeks.
- ➡️ **Apple v OpenAI (Oct 1 hearing):** Rule 26 response filed; sanctions probability materially higher, hardware timeline slippage more probable.
- ➡️ **Model fatigue (from 2026-09-10):** no new frontier release today; enterprise buyer response note expected from Ramp AI Index Monday.
- ⬇️ **"Generic 5-case eval suite" as a career skill:** deprecated by Braintrust + Freeplay. Verticalized cases are the new floor.
- ⬆️ **Live cost receipts (your real traffic) as a career skill:** re-priced up. Braintrust can't fake your bill; you can.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-s1) (Anthropic S-1) |
| 20 min | [`03` §1–2](./03-practical-skills-and-tools.md) — the cost-dashboard build + the S-1-informed Anthropic req list |
| Tonight | [`03` §1](./03-practical-skills-and-tools.md#1-cost-dashboard) — ship the dashboard |
| This weekend | [`05` §3 checkpoint](./05-career-and-startup.md#3-checkpoint) — audit against the 4-artifact / 5-app / 2-paper target |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
