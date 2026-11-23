# Career & Startup — 2026-09-11

Friday's story is compression. **The Anthropic S-1 tells you which reqs are on the aggressive pace; Braintrust's Series B tells you what layer of the stack is consolidating; the end-of-week checkpoint tells you whether your compounding is on track.** Below: the S-1-informed hiring map update, the Friday skill re-price, and the end-of-week checkpoint against Thursday's plan.

Tags: `#careers #salary #startups #anthropic #openai #s1 #artifacts #checkpoint #hiring #fde #applications`

---

## 1. Hiring map — S-1-updated {#1-hiring-map-friday}

**What happened:** two updates to Thursday's [`05` §1](../2026-09-10/05-career-and-startup.md#1-hiring-map) hiring map now that the S-1 has landed and the OpenAI + Meta moves have played out:

**Anthropic (S-1-inferred hiring plan, next 90 days):**
- ~750–900 net new hires across the org disclosed as a growth-plan-of-use-of-proceeds line.
- **~58% of open reqs** concentrated in **Claude Code + Solutions + Applied AI** (per S-1 org-chart + live careers page cross-reference).
- **~14%** in Research (including Evaluations — [`03` §2 role #11](./03-practical-skills-and-tools.md#2-anthropic-req-list)).
- **~11%** in Deployment / Field / Onboarding — the S-1's fastest-growing hiring category YoY.
- **~9%** in Legal-Ops-Eng / Compliance — net-new roles per [`02` §3](./02-new-emerging.md#3-audit-log-wedge).
- **~8%** in DX + MCP + Ecosystem.

**OpenAI (post-departures, next 90 days):**
- Continuing leadership churn ([`01` §3](./01-big-lab-moves.md#3-openai-departures)) — probability of individual req slipping into Q1 2027 is meaningfully higher.
- Deployment Company + FDE reqs still active per the [2026-05-19 launch note](../2026-05-19/00-tldr.md).
- **Apply to multiple functions in parallel** — the org is fluid enough that lateral pickups happen.

**Well-funded startups hiring right now (per Vinit Shahdeo tracker + AI Funding Tracker Friday note):**
- 160+ still open; Braintrust ([`02` §1](./02-new-emerging.md#1-braintrust-series-b)) adds 40–70 more over 12 months.
- Metronome AI + audit-log wedge companies ([`02` §3](./02-new-emerging.md#3-audit-log-wedge), [`02` §4](./02-new-emerging.md#4-friday-rounds)) each add ~15–30 reqs by Q1 2027.

**Salary anchors (Recruiting from Scratch, updated Q3):**
- **ML Engineer (AI startup, all levels):** 25th $184K · median $200K · 75th $249K.
- **AI Engineers:** ~15–25% above MLE at same level.
- **LLM specialists:** $220–280K base.
- **New: Litigation-Response Engineering / Records-Retention roles:** $240–340K base at frontier labs.

**Sources:**
- [SEC EDGAR — Anthropic PBC S-1](https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&CIK=0002012354&type=S-1) `[primary]`
- [Anthropic Careers](https://www.anthropic.com/careers) `[primary]`
- [OpenAI Careers](https://openai.com/careers/) `[primary]`
- [Axial Search — AI Engineering Jobs in 2026](https://axialsearch.com/insights/ai-engineering-jobs) `[analysis]`
- [Vinit Shahdeo — AI Startups Hiring 2026: 160+ Funded Companies](https://vinitshahdeo.substack.com/p/ai-startups-hiring-engineers-2026) `[aggregator]`
- [Recruiting from Scratch — ML Engineer Salary at AI Startups 2026](https://www.recruitingfromscratch.com/blog/ml-engineer-salary-at-ai-startups-in-2026) `[analysis]`

### Why it matters to you

- **Job lens:** Two concrete moves this weekend: (a) **12 Anthropic apps** per [`03` §2](./03-practical-skills-and-tools.md#2-anthropic-req-list) — before the roadshow-window req-freeze; (b) **3 well-funded startup apps** from Vinit's list — Braintrust, Metronome, and one of the audit-log wedge companies from Q3-founding.
- **Startup lens:** The 90-day hiring plan reads as a **procurement plan** too. Anthropic is buying: eval infra (needs vertical-specific), Solutions tooling (needs Claude-Code-adjacent SKU), audit-log infra (needs enterprise-grade retention-hold). Those are the wedges where an Anthropic-adjacent startup can land a design-partner logo faster than any other lab.
- **Insight:** The S-1 is a **hiring-plan disclosure document masquerading as a financial one.** Read it that way. Every segment revenue line implies a hiring plan; every operating-expense line implies which functions are absorbing the incoming capital. **Practice: after IPO, pull the 10-K and re-do this exercise every fiscal quarter for the next 3 years — that habit is how you spot inflection points in the labor market ~90 days early.**

→ Cross-link: [`03` §2 12 Anthropic reqs](./03-practical-skills-and-tools.md#2-anthropic-req-list) · [2026-09-10/05 §1 hiring map](../2026-09-10/05-career-and-startup.md#1-hiring-map).

---

## 2. Friday skill re-price — verticalized evals up, generic evals commoditised {#2-reprice-friday}

**What happened:** Braintrust ([`02` §1](./02-new-emerging.md#1-braintrust-series-b)) + Meta-Freeplay ([`02` §2](./02-new-emerging.md#2-meta-freeplay)) + Google Vertex Evaluation SKU + Anthropic's rumored internal "Verdict" + OpenAI's Evals API — **every big lab has an eval offering as of Friday.** The **generic 5-case eval suite** template from [2026-09-10/04 §3](../2026-09-10/04-research-progress.md#3-eval-suite-template) is still valuable as a *personal* artefact but no longer differentiating as a *product*. Two skill re-prices:

**Up:**
- **Verticalized eval design** — legal-doc extraction, health-summary accuracy, code-review recall/precision, financial-workflow correctness. These are all *not-generic* eval suites where the cases require domain expertise.
- **Live receipts of your own traffic** — Braintrust can show your logs; Braintrust can NOT show real revenue impact from your prod stack. That receipt is your moat.
- **Drift-metric analysis** ([`04` §1](./04-research-progress.md#1-continual-eval)) — the continual-eval / rolling-window / CUSUM primitive is not yet a Braintrust feature; owning that intellectual layer is a 60–90 day advantage.
- **Cascade + verifier routing** ([`04` §3](./04-research-progress.md#3-routing-survey) + [`04` §4](./04-research-progress.md#4-small-papers)) — the routing survey's SOTA moves.

**Down:**
- **Generic prompt-eval SDKs.** Braintrust's SDK is going to be excellent inside 90 days; there's no wedge left for a hobby generic-eval library. Don't build one.
- **"Latest model" model-fluency** — still deprecated, same as Thursday.

### Sources
- Recap of Braintrust round → [`02` §1](./02-new-emerging.md#1-braintrust-series-b)
- Recap of Meta-Freeplay acquisition → [`02` §2](./02-new-emerging.md#2-meta-freeplay)
- arXiv routing survey → [`04` §3](./04-research-progress.md#3-routing-survey)
- Continual eval paper → [`04` §1](./04-research-progress.md#1-continual-eval)

### Why it matters to you

- **Job lens:** Replace 3 of your 5 eval cases with **vertical-specific** cases from a public workflow you actually use — legal-doc-extraction pattern from a canvassed template, or code-review case from your own OSS PR history, or a summarisation case from your Zettelkasten notes. This is a 90-minute Sunday-morning task with 10× the interview-conversation value of the generic version.
- **Startup lens:** If you're pursuing the tooling wedge, **abandon the "another generic router / another generic eval SDK" framing this weekend and re-orient toward vertical specialization or drift-metric-owning.** The 90-day category-defense window is already partially spent.
- **Insight:** The general pattern — **when a category consolidates, the horizontal winner takes the biggest slice and the *vertical* specialists take the rest of the market.** Same shape as Datadog vs. Sentry vs. Rollbar in monitoring, or Snowflake vs. Databricks vs. ClickHouse in analytics. In 2026 eval infra, Braintrust is the horizontal; the vertical seats are open.

→ Cross-link: [2026-09-10/05 §2 skill re-price Thursday](../2026-09-10/05-career-and-startup.md#2-reprice) · [`03` §1 cost-dashboard build](./03-practical-skills-and-tools.md#1-cost-dashboard).

---

## 3. End-of-week checkpoint against Thursday's 4-artefact / 5-app / 2-paper plan {#3-checkpoint}

**What happened:** Thursday's [`05` §4](../2026-09-10/05-career-and-startup.md) set the week's targets. Friday is the honest measurement point.

### The scoreboard

| Target (Thursday's plan) | Ideal by Friday EOD | Actual (check yourself) | Recovery move if behind |
|---|---|---|---|
| **Update LinkedIn headline → "AI Engineer"** | Done Tue | ☐ | 5 min tonight. No excuse. |
| **Skills line: model routing + eval design + prompt caching + MCP + subagents + hooks + Claude Code** | Done Tue | ☐ | Same 5 min. |
| **Ship router + 5-case eval-suite repo (public)** | Tue tonight | ☐ | Skip Friday's dashboard and do the router tonight instead. The router is the anchor artefact; the dashboard is the extension. |
| **Cost dashboard extension** ([`03` §1](./03-practical-skills-and-tools.md#1-cost-dashboard)) | This weekend (Friday-Sun) | ☐ | 3 hours Sat morning; publish Sun. |
| **Founder-wedge memo** (Wedge A or B) | Weekend | ☐ | Post it Sunday even if it's 500 words. Cadence > perfection. |
| **3 Anthropic apps** | Fri EOD | ☐ | See [`03` §2](./03-practical-skills-and-tools.md#2-anthropic-req-list) — 12 mapped roles, apply to top 3 tonight. |
| **2 well-funded startup apps** | Fri EOD | ☐ | Braintrust + Metronome or Verdant tonight. |
| **Two arXiv papers read** (2511.04898 + 2512.13564) | Read + notes by Fri EOD | ☐ | Read the abstracts + methods sections tonight; full read weekend. Add 2601.07822 to the queue. |
| **Verticalize 3 eval cases** (NEW Friday) | Weekend | ☐ | 90 min Sunday morning. Pick your domain, pick 3 cases, ship. |

### If everything is checked

You just built more distinctive output than 90% of the 2026 AI-hire applicant pool in **one week.** Compound another 3 weeks and you're at 16 artefacts + 20 applications + 8 papers by Oct 8 — a portfolio that reads as *"this person has a point of view on the 2026 model landscape and ships weekly"*, which is exactly the frame Anthropic Applied AI, OpenAI FDE, Scale Field Solutions, and every $30M+ Series A AI startup wants.

### If nothing is checked

Do exactly one thing: **the router repo tonight (Thursday's `03` §3).** That single artefact keeps the compounding intact. Everything else recovers next week.

### Sources
- [ACTIONS.md](../ACTIONS.md) — running personal task tracker
- [APPLICATIONS.md](../APPLICATIONS.md) — application tracker (update tonight)
- [STARTUPS.md](../STARTUPS.md) — wedge log (update after the weekend memo)

### Why it matters to you

- **Job lens:** The compounding-artefact strategy is now measurable — cadence is the primary variable, count is secondary. Miss one week and you drop from the top-decile pace; miss two weeks and the compounding restarts. **Protect Fridays for shipping and Sundays for writing.** That two-day protection is worth more than any single tactical move.
- **Startup lens:** The founder-wedge memo (Wedge A or B from Thursday's [`05` §3](../2026-09-10/05-career-and-startup.md#3-startup-wedges)) needs to be updated with today's news — Braintrust took the horizontal seat on Wedge A; **your Wedge A version must now be vertical or drift-metric-specific.** If your memo doesn't reflect that Friday's update, rewrite the 3 relevant paragraphs Sunday morning.
- **Insight:** The **weekly-cadence artefact model is more durable than any single application strategy.** Applications get rejected; artefacts compound. If you have a 3-month window and can ship 12 artefacts, one of them will convert an application. If you send 12 applications with zero artefacts, none of them will convert. **The path is: artefacts first, applications second.**

→ Cross-link: [`03` §1 cost dashboard](./03-practical-skills-and-tools.md#1-cost-dashboard) · [`03` §2 the 12 reqs](./03-practical-skills-and-tools.md#2-anthropic-req-list) · [ACTIONS.md](../ACTIONS.md).

---

## 4. Weekend rhythm — the two things to do, in order

**Saturday (~3 hours):**
1. Cost-dashboard build ([`03` §1](./03-practical-skills-and-tools.md#1-cost-dashboard)) — SQLite table, aggregation script, static dashboard, GitHub Pages deploy. Public repo. Screenshot Sun.
2. Read arXiv 2601.07822 abstract + methods ([`04` §1](./04-research-progress.md#1-continual-eval)) — 30 min.

**Sunday (~3 hours):**
1. Verticalize 3 eval cases (see [`05` §2](#2-reprice-friday)) — 90 min. Push to the router repo.
2. Founder-wedge memo — updated for the Friday news — 60 min. Post publicly.
3. LinkedIn post: **the whitespace-cache-invalidation fix from [`03` §3](./03-practical-skills-and-tools.md#3-caching-regression)** with a dashboard screenshot. 30 min.
4. Application admin — update [APPLICATIONS.md](../APPLICATIONS.md) with what went out this week.

### Why it matters to you

- **Insight:** The two-day weekend rhythm doubles as a **stress test for the compounding model** — if you consistently miss the Saturday build or the Sunday post, the compounding won't hold. **Track it in [ACTIONS.md](../ACTIONS.md) every Sunday evening for the next 4 weeks; if any single item slips 2 weeks in a row, cut it or automate it.**
