# Career & Startup — 2026-09-14

The bimodal job market intensified. **AI-spend-per-employee fell 10% at top firms in August** — the first "cracks in the thesis" data point of the year — even as **enterprise adoption crept up** (Anthropic **43.8%** vs OpenAI **39.8%**). **Sept 1–10 tech layoffs jumped +199% vs August (6,300+ cuts).** But the FDE hiring surge is **+1,000% YoY**, and the **2027 intern cycle** opened with AI/ML intern postings outpacing generalist SWE **for the first time.** The message: **the bar just went up, and the routes around the bar are narrow and specific.** Meanwhile, the [pacing accord (§01 §1)](./01-big-lab-moves.md#1-pace-the-frontier) creates a new career lane — evaluator-adjacent roles at METR, Apollo, and AISI equivalents.

Tags: `#careers #hiring #layoffs #fde #applied-ai #interns #salaries #verticals #evaluator`

---

## 1. Ramp AI Index Sept 2026 — the first "cracks in the thesis" data point {#1-ramp-cracks}

**What happened:** Ramp's monthly AI Index (Sept 9) reported that **median AI expenditure among the top-1% of AI spenders fell from ~$7,976/employee (July) to ~$7,205/employee (August)** — a **~9.7% drop** — while overall enterprise adoption barely inched up (56.0%, +0.4pt m/m).

Vendor split:
- **Anthropic**: 43.8% (+0.34pt m/m) — passed OpenAI in April, still leading.
- **OpenAI**: 39.8% (+0.09pt m/m).
- **Google**: rising in enterprise Workspace bundles but still fragmented in dedicated AI spend.

**Effective average token price: $0.68/1M** in August, vs **$1.15/1M in March** — a **~41% drop in 6 months.** That's the [Fable 5.1 cache-read discount from Sept 1](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics) plus GPT-6 Astra's aggressive input pricing plus general model-competition compression.

Ara Kharazian's substack framed this as "cracks in the AI thesis, part 2" — the first monthly data point that suggests **top spenders are pulling back, not doubling down.**

**Sources:**
- [Ramp AI Index — September 2026](https://ramp.com/data/ai-index-sept-2026) `[primary]`
- [Ara Kharazian — Cracks in the AI Thesis, Part 2](https://econlab.substack.com/p/ai-index-sept-2026) `[analysis]`
- [TechCrunch — AI spend per employee slumped at top firms in August](https://techcrunch.com/2026/09/09/ai-spend-per-employee-slumped-at-top-firms-in-august-summer-doldrums-or-a-warning-sign/) `[secondary]`

### Why it matters to you

- **Job lens:** The "we'll hire anyone who says AI" phase is over. Every enterprise buyer that pulled back per-employee spend also **raised the internal bar for what an "AI hire" needs to deliver.** Translation for your applications: **generic "worked with LLMs" bullets are now null-value.** Ship at least one artifact that quantifies the *value* of your AI work — cost reduction, throughput increase, eval pass-rate lift. The [`03` §1 plugin-eval report](./03-practical-skills-and-tools.md#1-plugin-eval) is the fastest way to generate that number.
- **Startup lens:** Token-price compression means **application-layer margins are compressing.** If your startup wedge assumes you can pass $3/1M input to enterprise buyers with a 5× markup, that math just got worse. Wedges that survive: (a) **transaction-loop revenue** (Forus-style, [`02` §3](./02-new-emerging.md#3-forus)); (b) **per-outcome pricing** (from May's playbook); (c) **eval / observability / compliance** — sold *to* the labs, priced against their savings, not their spend.
- **Insight:** Read this alongside adoption still rising. **Adoption up + spend/employee down + token price down = healthy market maturing, not collapsing.** The doom-take is wrong; the "money is finding better allocation" take is closer. But the transition period (Q4 2026 through Q1 2027) will look like a hiring slowdown from the candidate side.

---

## 2. Sept 1–10 layoff surge — 6,300+ tech cuts, +199% vs August {#2-layoff-surge}

**What happened:** The first 10 days of September saw **>6,300 tech layoffs**, a **+199% jump vs August**, concentrated in **internet companies (77%).** Layoffs.fyi's cumulative 2026 total passed **128,536 across 299 companies by Sept 10** — already exceeding all of 2025.

Named cuts:
- **Uber**: 10% globally.
- **Nike**: ~1,400, mostly tech / engineering.
- **TikTok, Apple, AT&T, Zoox** all posted meaningful cuts.
- **Salesforce**: 133 more filed via WARN (see §3).

Simultaneously: **~275K AI-related U.S. roles remain open**, and employers announced hiring plans for **119,825 workers through August** (19,751 in tech). The market is **bimodal**, not shrinking.

**Sources:**
- [Crunchbase — Tech Layoffs Tracker](https://news.crunchbase.com/startups/tech-layoffs/) `[secondary]`
- [FinChannel — Tech Layoffs 2026: TikTok, Apple, AT&T, Zoox](https://finchannel.com/tech-layoffs-2026-tiktok-apple-att-and-zoox-put-u-s-jobs-back-in-focus/134444/american-business-trends/2026/09/) `[aggregator]`

### Why it matters to you

- **Job lens:** **Route around the eliminated categories.** Traditional QA, content mod, customer-support engineering, middle-management-for-middle-management, and generalist-SDE-at-a-mature-consumer-product are all sinking. Route *toward*: ML/eval/infra, agent-building, applied-AI in regulated verticals, evaluator-org roles ([§4](#4-evaluator-jobs)).
- **Startup lens:** Layoff surges seed founder waves 6–12 months out. Track the departure lists — **Uber layoff cohorts historically produce founder-tier engineers** who go build vertical B2B SaaS. If any of those pivot to AI-native versions of Uber's internal tools, expect 2–3 launches in Q1 2027 worth watching.
- **Insight:** The Anthropic/OpenAI Ramp share numbers aren't dropping. **What's shrinking is *headcount that used to sit in front of an AI tool, doing tasks the tool now does.*** This confirms the [May thesis on "AI Integration Engineer as fastest-growing"](../2026-05-16/) — the destruction and creation happen simultaneously, but not in the same job families.

---

## 3. Forward Deployed Engineer hiring +1,000% YoY — Anthropic's Applied AI JV structure {#3-fde-hiring}

**What happened:** Perspective AI's 1,000-post FDE dataset (Sept 2026 update) shows FDE and FDE-adjacent postings up **>1,000% YoY.** Salary structure:
- **OpenAI FDE**: **$350K–$550K TC**; equity can double cash at Staff.
- **Palantir FDE**: **~$238K average**, **Staff $630K+.**
- **Anthropic Applied AI Engineer**: not disclosed, but the [$1.5B Blackstone/Goldman/Apollo/H&F JV (May 7)](../2026-05-07/) is *specifically structured* to embed engineers inside portfolio companies. Anthropic FDE headcount is likely on a Q4 hiring ramp.

**Fastest-growing employers**: **Sierra ("agent engineers"), Decagon, Harvey, Cresta, Hebbia, Writer, Glean.**

**Sources:**
- [Perspective AI — 2026 FDE Hiring Trends (1,000 job posts)](https://getperspective.ai/blog/2026-fde-hiring-trends-what-1000-job-posts-reveal) `[analysis]`
- [Paraform — OpenAI Forward Deployed Engineer role breakdown](https://www.paraform.com/blog/openai-forward-deployed-engineer) `[secondary]`
- [MarkTechPost — What is an FDE? The AI role OpenAI/Anthropic/Google are hiring in 2026](https://www.marktechpost.com/2026/05/20/what-is-a-forward-deployed-engineer-the-ai-role-openai-anthropic-and-google-are-hiring-in-2026/) `[analysis]`

### Why it matters to you

- **Job lens:** This is your **highest-ROI application track.** For a CS grad targeting [Anthropic + OpenAI + Sierra + Decagon per your ME.md](../ME.md), the FDE surface is (a) hiring hard, (b) paying $350K+ TC, (c) hires on *evidence of shipping* rather than LeetCode aggregate. What to ship (aligned with your active portfolio):
  1. **One MCP server** for a real product (per §02 §4 pattern).
  2. **One plugin-eval report** with 5 golden cases + before/after diff (per §03 §1).
  3. **One cost-router + eval-suite** for a routing decision (per 2026-09-10/03 §3).
  Three artifacts, one Sunday each. Ship them, put them at the top of GitHub + LinkedIn, apply to 5 FDE roles per week starting next weekend.
- **Startup lens:** The FDE market is now hot enough that **"FDE-as-a-service"** is a startup wedge. Anthropic's JV model (Applied AI engineers embedded via a Blackstone-scale vehicle) is the enterprise version; the equivalent for smaller AI startups selling into mid-market is untapped. Founder wedge: **fractional-FDE for early-stage AI startups that need embedded engineering but can't hire $400K TC full-time.**
- **Insight:** FDE roles are **compressing to *builder* profiles.** Anthropic's Applied AI Engineer and Sierra's Agent Engineer titles are the tell — they don't want "consultant who writes prompts on behalf of clients", they want "engineer who builds working agents for clients." That's a good thing for you: the LinkedIn keyword arbitrage from "Forward Deployed Engineer" is closing, but the underlying craft (build agents, evaluate them, deploy them, iterate) is exactly what you're already positioning around.

---

## 4. Evaluator-org roles as the new career lane (post-pacing accord) {#4-evaluator-jobs}

**What happened:** Amodei's Sept 12 essay + Altman's endorsement (see [`01` §1](./01-big-lab-moves.md#1-pace-the-frontier)) commit the labs to **permanent employee-level system access for third-party evaluators**, with **METR (Model Evaluation & Threat Research)** named as the initial beneficiary. **Apollo Research** and the **UK AISI / US CAISI equivalents** are the obvious next-tier recipients of similar arrangements.

This is the first time a top-tier lab has publicly committed to *paying* for external evaluation infrastructure — and it means **evaluator organizations transition from a niche safety-community track to a first-class career destination.**

**Sources:**
- [Dario Amodei — We Must Pace the Frontier](https://darioamodei.com/post/we-must-pace-the-frontier) `[primary]`
- [METR — Careers](https://metr.org/careers) `[primary]` — (verify current openings)
- [Apollo Research — Careers](https://www.apolloresearch.ai/careers) `[primary]`

### Why it matters to you

- **Job lens:** Evaluator-org hiring runs 6-months-delayed from lab announcements, so **applications opened this week** are the ones that will fill Q1 2027 seats. Roles to target:
  1. **Model red-teamer** — hands-on jailbreaking, capability elicitation, dangerous-capability probing.
  2. **Evaluation infrastructure engineer** — automating benchmark runs at scale, integrating with lab-provided APIs and internals.
  3. **Interpretability engineer** — mechanistic analysis, attribution studies, feature-level probes.
  4. **Policy-technical translator** — writing lab-facing recommendations from technical findings (rare CS-grad skill; premium).
- **Startup lens:** The **evaluator-as-a-service** wedge just got underwritten by the labs. If you can build a company that offers "we run the ARC-AGI + AgentActionBench + your-custom-suite before your next release, and give you a public-defensible report", the labs are now *contractually incentivized* to buy. Adjacent: **evaluator-focused compute** (bulk-inference contracts at the labs' new terms), **evaluator-tooling** (the plugin-eval report format, but productized).
- **Insight:** If you're on the fence between "startup" and "job" — evaluator orgs are the rare place where a job pays like a mid-startup, ships work that reads publicly, and puts you 3 degrees from the actual frontier research. For a CS grad who wants **maximum optionality** over the next 24 months, evaluator-org > FAANG > safety-adjacent regulator > academia.

---

## 5. Class of 2027 intern cycle opens — AI/ML postings outpace SWE for the first time {#5-verticals}

**What happened:** US SWE intern postings ran at **~1,268/day in September vs ~790/day in August** — a **+60.5% m/m** jump as the fall wave hit on schedule. Notable data points:
- **Google Student Researcher (BS/MS, Fall 2026)** — open through Nov 27, 2026.
- **Google + Meta now explicitly permit AI coding assistants during interview rounds.** This is a paradigm change — LeetCode-only prep is no longer sufficient; the interview loop is *evaluating your ability to use AI tools well.*
- **AI/ML intern openings outpace generalist SWE for the first time in this cycle.** Handshake's Class of 2026 baseline: **70% of CS majors pessimistic, 14% optimistic**; **42% use GenAI daily**; **45% highlight AI skills on resumes.**

**Sources:**
- [Extern — Tech Internships Summer 2027 Timeline](https://www.extern.com/post/tech-internships-summer-2027-guide) `[aggregator]`
- [Handshake — Class of 2026 CS spotlight](https://joinhandshake.com/blog/network-trends/class-of-2026-spotlight-computer-science/) `[secondary]`
- [ApplyBolt — 2027 New Grad Application Timeline](https://www.applybolt.app/guide/2027-new-grad-jobs) `[aggregator]`

### Why it matters to you

- **Job lens:** Two immediate to-dos:
  1. If you have any 2027-cycle SDE/MLE intern applications still open, **finish them this week** — the Nov 27 Google deadline is the anchor.
  2. **Practice interviews with your AI tools ON.** If Google + Meta let you use them, your interview loop is now *"efficient use of AI + fundamentals"* rather than *"fundamentals in isolation."* This is a real skill, not the same as raw LeetCode grinding — practice narrating your thought process while an AI drafts a solution.
- **Startup lens:** The **AI-coding-assistant-for-interviews** wedge just got officially blessed by Google + Meta. Startups building "practice interviews with AI, like the real ones" (e.g., Interviewing.io + AI mode, various YC entries) have their TAM permanently expanded.
- **Insight:** *"AI/ML intern openings outpace SWE for the first time"* is a signal buried inside the intern data, but it's the single most durable career-cycle statistic of 2026. **The generalist SWE ladder is now a specialist AI/ML ladder wearing generalist clothing.** If you've been optimizing your resume for "SDE" — recalibrate to have MLE / AI-Engineer as the lead line, SDE as the fallback.

---

## Weekly action list (Sunday → next Sunday)

1. **Tonight**: Write 5 plugin-eval golden cases, run before/after, commit report to GitHub. ([`03` §1](./03-practical-skills-and-tools.md#1-plugin-eval))
2. **Mon–Wed**: Apply to **5 roles** — 2× Anthropic Applied AI + 1× Sierra Agent Engineer + 1× METR/Apollo evaluator + 1× funded startup FDE from the [Vinit Shahdeo tracker](https://github.com/vinitshahdeo). Cite your plugin-eval report in each cover letter.
3. **Thu**: Recruiter/alumni outreach — **5 DMs**, one paragraph each, referencing the pacing accord as the industry-context signal.
4. **This weekend**: Ship the **MCP-server + evals repo** (per [`02` §4](./02-new-emerging.md#4-mcp-verticalizes) pattern + [`03` §1](./03-practical-skills-and-tools.md#1-plugin-eval) discipline). One vertical, three tools, five evals, README. That's the *third* portfolio artifact in [ME.md's active list](../ME.md#active-portfolio-artifacts).
