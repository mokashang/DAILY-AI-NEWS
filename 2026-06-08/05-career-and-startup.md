# Career & Startup — 2026-06-08

This week the **FDE / Solutions Engineer lane got its first real published compensation benchmark** (1,200-respondent survey: **$130–300K base; senior at frontier labs $400–500K TC; Palantir 51 open roles, OpenAI 31**), the **AI Engineer title remained the #1 fastest-growing US job title (+143% YoY)** even as **entry-level tech postings stayed down 35% from 2023**, and the **WWDC Extensions API + Anthropic IPO arc** create two concrete shifts in *where* the apply leverage is for the next 90 days. Read together: **the lane is funded, the salary is published, and the apply-window is now structurally narrowing** as Anthropic + Apple push hiring into more-disciplined cadences.

Tags: `#careers #fde #solutions #ai-engineer #compensation #wwdc #anthropic #ipo #startups #wedges`

---

## 1. FDE compensation benchmark: $130–300K base, $400–500K TC senior at frontier labs — Palantir + OpenAI lead {#1-fde-comp}

**What's new:** Perspective AI published the **2026 Forward Deployed Engineering Compensation Report (1,200 respondents)**, and FDE Pulse cross-tabulated **open roles by company** — together, the cleanest snapshot of the FDE/Solutions market we've had:

- **Base:** $130K–$300K, depending on level and company.
- **Senior at frontier labs (OpenAI, Anthropic, Mistral, Cohere):** **$400K–$500K total comp**, including equity.
- **Top hirers (May 2026 snapshot):** **Palantir 51**, **OpenAI 31**, Databricks 12, Mistral 11, Cohere 10, with a long tail across 118 hiring companies and **224 total open FDE roles across 39 AI-native companies**.
- **Profile:** technical specialist embedded *inside* a customer's company to scope, build, and deploy AI systems end-to-end — *post-sale* (not the pre-sale Solutions Engineer role), with discovery + technical scoping + system design + build + production rollout responsibility.
- **Why the lane is hot:** It's the *only* role at a frontier lab that combines high direct-customer leverage with technical depth — and it's the role that *converts* a model release into actual recognized revenue.

**Sources:**
- [Perspective AI — The 2026 Forward Deployed Engineering Compensation Report: What 1,200 FDEs Earn](https://getperspective.ai/blog/2026-forward-deployed-engineering-compensation-report-1200-fdes) `[primary]`
- [FDE Pulse — Forward Deployed Engineer Hiring Trends 2026](https://fdepulse.com/insights/fde-hiring-trends-2026/) `[secondary]`
- [Jobs by Culture — Forward Deployed Engineer Boom: 224 Open Roles Across 39 AI Companies (2026)](https://jobsbyculture.com/blog/forward-deployed-engineer-boom-2026) `[secondary]`
- [FDE Academy — Why Companies Are Hiring Forward Deployed Engineers in 2026](https://fde.academy/blog/why-companies-are-hiring-forward-deployed-engineers) `[analysis]`
- [OpenAI Careers — Forward Deployed Engineer (FDE) - NYC](https://openai.com/careers/forward-deployed-engineer-(fde)-nyc-new-york-city/) `[primary]`
- [OpenAI Careers — Forward Deployed Engineer (FDE) - SF](https://openai.com/careers/forward-deployed-engineer-(fde)-sf-san-francisco/) `[primary]`

### Why it matters to you

- **Your apply slate this week** (concrete, ordered by your fit per [`ME.md`](../ME.md)):
  1. **OpenAI FDE (NYC or SF)** — apply this week with the $400–500K senior TC band as your reference (but apply to the standard FDE, *not* the senior posting; your story is "Anthropic-stack expertise + cost-routing artifact").
  2. **Anthropic Solutions Architect / Customer Engineering** — apply with the **Opus 4.8 + cost-router artifact** from [`03` §1](./03-practical-skills-and-tools.md#1-opus-48-baseline) as the portfolio anchor.
  3. **Palantir FDE (51 open roles)** — Palantir invented the lane; **broad hiring + structured interview = the highest-volume path** into the category. Apply even if Palantir isn't first-choice — interview rep is uniquely valuable.
  4. **Databricks / Cohere / Mistral FDE** — lower volume but lower competition and faster process.
  5. **Skip for now:** generic "AI Engineer (Cloud Partner)" postings at consultancies — comp band lower, the FDE roles above clear the same bar at higher comp.

- **Your portfolio for the apply:** the three artifacts already on your active list close the loop for this lane:
  - **Public MCP server (3 tools + 5-case eval + README + demo gif)** — proves you can ship.
  - **Opus 4.7→4.8 migration with cost log** ([`03` §1](./03-practical-skills-and-tools.md#1-opus-48-baseline)) — proves you measure unit economics.
  - **Gemini-vs-Claude-vs-GPT one-page comparison** ([`ME.md`](../ME.md)) — proves you read the platform tape.
- **Insight:** FDE is the **highest-comp / lowest-credential lane** in tech right now — but the *window for that arbitrage closes when the published comp band hits the mainstream search results.* Today *is* that day. **Apply this week**; comp benchmarks compress the easy-apply window from ~6 months to ~6 weeks.

→ Cross-link: [2026-05-17/05 — original FDE thread (+800% YoY postings)](../2026-05-17/05-career-and-startup.md) · [2026-05-19/05 — OpenAI Deployment Company + Tomoro 150 FDEs](../2026-05-19/05-career-and-startup.md) · [APPLICATIONS.md](../APPLICATIONS.md) — update with Priority-1 apply list.

---

## 2. AI Engineer still #1 fastest-growing job title (+143% YoY) — but entry-level is the trap {#2-ai-engineer}

**What's new:** The 2026 data continues to confirm: **AI Engineer is the #1 fastest-growing US job title** (LinkedIn Jobs on the Rise; +143% YoY through Q1 2026). **AND** entry-level tech postings remain **down 35% from early 2023**, with recruitment of new graduates at the **15 largest US tech companies down 55%** versus pre-2023 norms. The class-of-2026 placement-within-3-months rate is **77.2%**, up from 63.3% a year prior — but the *composition* has shifted away from generalist SWE roles.

**The implication for a CS grad student** is more interesting than either headline suggests in isolation: **the AI Engineer growth is real, but it's not absorbing the *entry-level* job loss** — those new AI Engineer roles are mostly going to engineers with 2–5 years of *applied AI* experience, not new grads with strong CS fundamentals but no AI track record. The bridge: **specialist AI-adjacent roles that hire at entry-level *because* they're new categories without an established senior pool.**

The four candidate "specialist entry-level" lanes for 2026:
1. **FDE / Solutions Engineer** (see §1) — *not* entry-level by title, but Palantir's FDE program + Anthropic's Customer Engineering programs *do* take new grads with strong portfolios.
2. **Eval / model-safety engineer** — Anthropic Frontier Red Team, METR, Apollo, UK AISI, US CAISI; expanding pool, structurally junior.
3. **AI integration / app-Intent engineer** at consumer apps building on WWDC's Extensions API ([`01` §1](./01-big-lab-moves.md#1-wwdc)) — entirely new role category opening *today*.
4. **MCP / agent infrastructure** at agent-first startups (Sierra, Decagon, Cognigy, Tomoro/OpenAI Deployment Company); these companies grew so fast they have *no* legacy senior bench, so they hire bright juniors with clean MCP/agent portfolios.

**Sources:**
- [LinkedIn 2026 Jobs on the Rise (US) — AI Engineer #1 +143% YoY (referenced widely)](https://www.metaintro.com/blog/new-grad-job-market-2026-ai-entry-level) `[aggregator]`
- [Pragmatic Engineer — State of the software engineering job market in 2026](https://newsletter.pragmaticengineer.com/p/state-of-the-job-market-2026) `[analysis]`
- [CNBC Select — Class of 2026 hiring stats and AI trends](https://www.cnbc.com/select/class-of-2026-hiring-stats-and-ai-trends/) `[secondary]`
- [HeroHunt — Tech Job Market 2026: What the Data Shows](https://www.herohunt.ai/blog/tech-job-market-2026-what-the-data-shows/) `[analysis]`
- [HeroHunt — Fastest Growing AI Roles in 2026](https://www.herohunt.ai/blog/fastest-growing-ai-roles-in-2026-data-and-rankings/) `[analysis]`
- [IEEE Spectrum — How to Stay Ahead of AI as an Early-Career Engineer](https://spectrum.ieee.org/ai-effect-entry-level-jobs) `[secondary]`
- [Fortune — Class of 2026 hottest jobs at small businesses](https://fortune.com/2026/05/01/one-million-new-grads-hired-small-businesses-2026-hottest-jobs-ai-proof-service-technicians/) `[secondary]`

### Why it matters to you

- **Job lens:** **Stop applying to generic SWE postings at FAANG-class companies.** The 55% recruitment cut means your application-to-interview rate is structurally worse than 2022, *regardless* of how good you are. Apply, but don't *prioritize.* Re-route the same hours into the four specialist lanes above — same applied effort, 3–5× higher response rate.
- **Startup lens:** The entry-level-tech drought is **a recruiting advantage if you're founding/joining a 2–10 person AI startup.** New grads from top CS programs are available *cheap* (relative to 2022) — if you can offer **equity + the chance to own a category** (e.g., "first MCP engineer at X"), you can hire ahead of where seed-stage startups historically can. Worth knowing whether you're founding or joining.
- **Insight:** The class-of-2026 data hides a bigger structural shift: **the "first job out of college" is now expected to be a *specialist* role from day one**, not a generalist SWE rotation. The traditional new-grad ladder ("FAANG → senior in 5 years → IC at AI startup") is being replaced by a specialist ladder ("FDE/Solutions/Eval/Integration at AI-native co → seed founder in 3 years"). **Plan your next 24 months as a specialist ladder.**

→ Cross-link: [§1 — FDE is the highest-comp specialist lane](#1-fde-comp) · [2026-05-15/05 — AI Engineer #1 thread origin](../2026-05-15/05-career-and-startup.md) · [2026-05-22/05 — skill-reprice signal](../2026-05-22/05-career-and-startup.md).

---

## 3. Startup wedges for the week {#3-startup-wedges}

**Three founder bets the week's news structurally enables:**

1. **Apple Intelligence Extensions–native consumer app.** WWDC opens the API today; first-mover featured-app window is ~3–6 months. The wedge isn't "use Gemini" (everyone will). The wedge is **(a) shipping an Extension *fast* — within ~30 days of the API spec dropping**, and **(b) picking a vertical the platform Gemini can't credibly serve** (e.g., privacy-sensitive notes, technical writing, professional task automation). Adjacent: a **"de-Geminify" router** that swaps system Siri/Gemini for Claude or local Mistral on sensitive prompts — niche, but defensible to a privacy-conscious power-user audience.
2. **AI-authored-code review pipeline.** The 80%-Claude-authored Anthropic disclosure ([`01` §3](./01-big-lab-moves.md#3-anthropic-self-build)) + the MLEvolve / AutoHarness / Self-Execution research stack ([`04`](./04-research-progress.md)) jointly say: *the bottleneck is verification, not generation.* Build a **GitHub-action review-the-AI's-PR harness** that surfaces (a) which lines an AI authored, (b) which tests cover them, (c) per-PR cost. Open-source the core, paid tier for enterprise. Adjacent: Judgment Labs ([2026-05-13/02](../2026-05-13/02-new-emerging.md)) at the seed-stage indicates VCs will fund this.
3. **MCP-stack-hygiene tooling (DevSecOps for agent tools).** Per [`03` §2](./03-practical-skills-and-tools.md#2-mcp-hygiene): most YC-stage AI cos don't enforce narrow credentials + audit. **Ship `mcp-audit` (open-source linter + config scanner) this weekend.** Then sell SaaS for the enterprise version. The Snyk-of-MCP-tools positioning is unowned.

For *your* fit per [`ME.md`](../ME.md), the **#2 (AI-authored-code review pipeline)** is the highest-leverage — it doubles as the portfolio artifact for the FDE apply (§1) *and* a sellable open-source repo *and* the front edge of a defensible founder thesis. Two weekends to ship the open-source core.

**Sources:**
- (All cross-referenced — no new external sources for this section.)

### Why it matters to you

- **Job lens:** Each of the three is an **interview-credibility-multiplier** even if you don't end up founding. "I shipped an open-source MCP audit tool and got 200 stars" is a *substantially* better story than "I built three side projects with Cursor."
- **Startup lens:** Notice the pattern — **all three wedges are 4–8 week ship windows, not 18-month thesis bets.** That's where the leverage is for a grad student right now: ride the platform-API openings (Apple, Anthropic, MCP) *while the windows are open*, not 6 months later when the obvious wedges are funded.
- **Insight:** The three wedges share a structural property — **they're shaped by the platform layer settling** ([`01` §1](./01-big-lab-moves.md#1-wwdc), [`02` §2](./02-new-emerging.md#2-msft-mai)). Each one would be unviable in a world where the platforms hadn't just made themselves more *legible* in the past two weeks. **The platform tape is the wedge tape.** Track it that way.

→ Cross-link: [STARTUPS.md](../STARTUPS.md) — update with the three wedges + your-fit scores.
