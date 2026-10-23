# Career & Startup — 2026-10-03

The 2026 job market has split in half, and the split is now operational: **AI/ML lane open with 500K+ unfilled roles and a 63% talent shortage; generalist SWE entry-level down 25% from 2023 peak, new-grad top-tech hiring down 50%+.** Your path forward is on the AI side of the split. This section lays out (a) exactly what the labor split looks like today, (b) the three skills that got repriced upward this week, and (c) the apply-this-week list weighted around the Anthropic S-1 window.

Tags: `#careers #hiring #new-grad #ml-engineer #ai-engineer #fde #startup #routing #mods`

---

## 1. The labor split — AI lane open, generalist lane closed {#1-labor-split}

**What happened:** Multiple sources this week confirm the US CS labor market is bifurcated:

- **AI/ML engineers: 63% talent shortage, 500,000+ open roles globally.**
- **Entry-level software engineering positions: down 25% from 2023 peak.**
- **New grad hiring at top tech companies: down 50%+.**
- **Intern intakes: ~half of what they were pre-pandemic.**
- **Entry-level MLE base pay: $90K–$135K.** LLM specialists: **$220K–$280K base** (per [2026-09-10](../2026-09-10/)).
- **CS graduate unemployment rate: ~6.1% in 2026.**
- **Most in-demand technical skills:** Python (75% of postings), AWS (49%), PyTorch (47%), TensorFlow (39%).

**The qualitative shift:** companies "shifting from PhD requirements to practical experience and portfolio-based hiring." **"Cold applying with tutorial projects no longer works."** This is a vocabulary change by hiring managers that happened within the past 90 days.

**Sources:**
- [Pragmatic Engineer — State of the software engineering job market in 2026, part 2](https://newsletter.pragmaticengineer.com/p/the-job-market-in-2026-part-2) `[analysis]`
- [Medium — AI Engineering Hiring Trends 2026](https://medium.com/@thedataexec/ai-engineering-hiring-trends-2026-1c1d894492aa) `[analysis]`
- [Hakia — The AI Talent Market: Skills in Demand & Salary Trends 2026](https://hakia.com/tech-insights/ai-talent-market/) `[analysis]`
- [Final Round AI — Software Engineering Job Market 2026: Data, Trends and Outlook](https://www.finalroundai.com/blog/software-engineering-job-market-2026) `[aggregator]`
- [Open Data Science — The 12 Most In-Demand AI Job Roles in 2026](https://opendatascience.com/12-in-demand-ai-job-roles-2026-how-to-get-hired/) `[analysis]`
- [IEEE Spectrum — How to Stay Ahead of AI as an Early-Career Engineer](https://spectrum.ieee.org/ai-effect-entry-level-jobs) `[secondary]`
- [Glassdoor — 14,801 AI engineer Jobs in United States, October 2026](https://www.glassdoor.com/Job/us-ai-engineer-jobs-SRCH_IL.0,2_IN1_KO3,14.htm) `[primary]`
- [Simplify.jobs — New Grad Data Science & AI/ML Jobs (2026-2027)](https://simplify.jobs/l/New-Grad-Data-Science-AI-ML) `[primary]`
- [Indeed — New Grad AI Engineer Jobs](https://www.indeed.com/q-new-grad-ai-engineer-jobs.html) `[primary]`

### Why it matters to you

- **Job lens:** Three concrete reads:
  1. **Don't apply as a "software engineer, new grad."** Apply as "AI/ML engineer, new grad" or "AI Engineer, new grad" or "FDE / Integration Engineer, new grad." The job titles have diverged, and most ATS systems route by title keyword, not resume content. Rewrite your resume headline this weekend.
  2. **Portfolio artifacts > GPA.** Companies have explicitly moved to this bar. Three artifacts beat a 4.0 with no artifacts. The three to have shipped by end of October: (a) **the router repo** ([2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact)), (b) **one Claude Code mod** ([`03` §1](./03-practical-skills-and-tools.md#1-claude-code-mods)), (c) **a persistent-agent design memo** ([`03` §3](./03-practical-skills-and-tools.md#3-persistent-agents)).
  3. **The $90–135K MLE floor is a de-risked base case.** The $220–280K LLM-specialist band is accessible after 1–2 years in the first role, provided you specialize. **The specialization you pick next matters more than the first paycheck.** Pick cost-aware routing + persistent-agent design + MCP for the next 12 months.
- **Startup lens:** The **labor split IS the market opportunity.** The 500K open AI/ML roles minus the ~50K actually-trained ML engineers = **a 10:1 shortage**. That's the TAM for:
  - **AI-career-pivoter training** for mid-career SWEs (SentryOne / Hyperskill / Scrimba-type offering, repositioned as "SWE → AI engineer in 90 days"). Mercor-adjacent, but training-first instead of marketplace-first.
  - **Hiring tooling that reads portfolios** (not resumes) for AI companies. The Mercor model, but opinionated about MCP + mods + router artifacts specifically.
  - **"AI apprenticeships" as a product** — pair a new grad with a startup for 6 months at a fixed low rate; the training is on the job. Classic Lambda School shape, but tightly scoped to AI roles.
- **Insight:** The **"cold applying with tutorial projects no longer works"** line is the most important sentence in this week's hiring data. **The compensation goes to the people whose work can be verified without the hiring manager running the code.** A gif + a leaderboard + a 1-page memo verifies without clicking "run." A README that says "clone and run `python main.py`" doesn't. **Optimize every artifact for "the hiring manager never clones."**

→ Cross-link: [`03` §1 the mod artifact](./03-practical-skills-and-tools.md#1-claude-code-mods) · [`03` §3 the persistent-agent memo](./03-practical-skills-and-tools.md#3-persistent-agents).

---

## 2. The three skills that got repriced upward this week {#2-reprice}

**What happened:** The news-cycle events of this week (DevDay + Claude Code mods + S-1 leak) specifically repriced three skills:

### (a) TypeScript mod authoring for Claude Code

- **Before:** didn't exist as a category; nobody listed it.
- **After:** 48 hours old, extremely sparse supply, and Anthropic will internally promote mod authors in the ecosystem (precedent: how Claude Legal plugin authors were promoted May). First 100 mod authors have **a direct line into Anthropic + its 10 biggest customers.**
- **Signal strength:** 10/10. Build one by Monday.

### (b) Persistent-agent architecture design

- **Before:** fuzzy "agent" talk; interviewers asked vague questions.
- **After:** Dots is a product with pricing. "Design a persistent agent that does X" is now a concrete design-interview category with a shared vocabulary. See [`03` §3](./03-practical-skills-and-tools.md#3-persistent-agents) for the template.
- **Signal strength:** 9/10. Have the memo by Monday.

### (c) Multi-provider cost-aware routing

- **Before:** nice-to-have; a side script.
- **After:** two major price cuts in 30 days (Fable 5.1 cache + GPT-6.1 Sol) mean routing is a measurable cost delta. **Hiring managers can read a routing leaderboard faster than they can read any other type of AI artifact.**
- **Signal strength:** 9/10. Add GPT-6.1 Sol as a row this weekend.

### What got repriced DOWN

- **"I built a chatbot with GPT-4o" as a portfolio project** — now actively a negative signal. Suggests you shipped the artifact in 2024 and haven't updated it. Delete it or rewrite as "shipped in 2024, migrated to [current stack] in 2026, kept backward-compat because X."
- **Being able to recite benchmark scores from Twitter** — redundant to a Perplexity query. Replace with "I ran my own 5-case eval and here are MY numbers."
- **"Fine-tuned a 7B model on my laptop"** — the laptop-fine-tune skill has been commoditized by cheap API fine-tune endpoints at every provider. Reframe as "**chose to NOT fine-tune and here's why**" — that's the senior-engineer story.

→ Cross-link: [`03` §1–3 the three artifacts](./03-practical-skills-and-tools.md).

---

## 3. Apply this week — the Anthropic-S-1 window + DevDay backfill {#3-apply-list}

**The window:** three weeks (Oct 3 → Oct 24) before the Anthropic S-1 becomes mainstream news and the applicant flood arrives. Apply NOW.

### Highest-priority apply targets (weight: 60%)

| Target | Why now |
|---|---|
| **Anthropic — Solutions / FDE / Integration / Applied AI** | S-1 pre-flood window; refresh grants being re-indexed; team expansion signaled by $7.33B compute line |
| **Anthropic — Public Sector / Federal** | FedRAMP High GA = team is funded and under-applied-to |
| **Anthropic — Finance / Legal / Healthcare vertical teams** | Next 3 verticals to GA; thin applicant pool |
| **Anthropic — Developer Relations / Mods ecosystem** | New primitive (mods) means new DevRel reqs; ship a mod before applying |

### Secondary apply targets (weight: 25%)

| Target | Why now |
|---|---|
| **OpenAI — FDE / Deployment Co / Dots team** | DevDay staffing wave; backfill for talent lost to Anthropic |
| **OpenAI — Codex Cloud + Ultrafast team** | New product line → new eng + GTM openings |
| **OpenAI — Agents API eng** | Computer-use + multi-agent surface = net-new team |

### Tertiary apply targets (weight: 15%)

| Target | Why now |
|---|---|
| **Shield AI / Peregrine / Anduril-adjacent** | Series G at $12.7B → late-stage hire with equity upside |
| **Mercor / Hiring-AI platforms** | Labor-split tailwind for talent-matching products |
| **Nscale / Wayve / Axelera (UK)** | Under-crowded geo; competitive comp |
| **PwC / Deloitte / Accenture / EY — AI Engineer, Client Delivery** | Still the strongest "safety-net while startup brews" offer |
| **Earendil / Yedric / aweb (seed-stage)** | Founding-engineer slots at the newest MCP harnesses |

### Application mechanics

- **One application per day, weekdays only.** Not 5 on Monday. The 1/day rhythm beats batch applications for interview conversion.
- **Each application: resume + a link to one of your three artifacts (router / mod / persistent-agent memo).** The link is the hook; the resume is the proof.
- **Reference someone named in the news.** For Anthropic: Ami Vora, Boris Cherny, Angela Jiang (the Code w/ Claude London keynote panel). For OpenAI: the DevDay 2026 presenters. Pick ONE sentence that references a specific decision they made and your take on it. 20× response rate improvement.

---

## 4. Weekend plan (Oct 3–5) {#4-weekend-plan}

### Saturday (today)

- Ship ONE Claude Code mod (60 min — pick the cost-router mod or secrets-redaction mod from [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-mods)).
- Add GPT-6.1 Sol row to router repo + rerun eval (15 min).
- Record 60-sec Loom / gif of the mod + the router leaderboard.

### Sunday

- 30-min persistent-agent memo ([`03` §3](./03-practical-skills-and-tools.md#3-persistent-agents)) — one page, concrete goal.
- Weekly review: write WEEK-2026-09-28.md rollup (new convention from May 2026 that's been inconsistent — restart this week).
- Rewrite resume headline: "**AI Engineer / Integration Engineer — Claude Code mods, multi-provider cost-aware routing, persistent-agent design**." Not "Software Engineer." The title keywords matter.

### Monday

- LinkedIn post with the mod gif + 3 sentences about why it exists. Tag @AnthropicAI if your account is unknown; otherwise don't.
- Send first application of the week (Anthropic Solutions / FDE). Attach the three artifacts; reference a specific Code w/ Claude London keynote decision.
- Set the daily 1/weekday application rhythm for the rest of the month.

### End-of-month target (Oct 31)

- 20 applications sent (1/weekday).
- 3 shipped artifacts (mod, router update, memo) + 1 LinkedIn post each.
- 2–3 phone screens on the books.
- 1 draft of a startup wedge memo (pick one from [`02` §1–2](./02-new-emerging.md)).

---

## 5. Startup wedge of the week {#5-wedge}

**The wedge:** **"Mod directory for your stack"** — an open-source index of Claude Code mods (plus eventually OpenAI Dots skills, Microsoft Copilot plugins), with install counts, review ratings, security audit badges, and an authored-by registry. First-mover + MIT-licensed + 90-day sprint = defensibility via community + the ratings data moat.

### Why this works

- **Timing:** mods are 48 hours old. The directory space is empty.
- **Precedent:** `npm`, `pip`, VS Code Marketplace, Chrome Web Store, Shopify App Store — every extension ecosystem has one dominant directory and the moat is engagement + reviews + trust.
- **Security angle:** mods are not sandboxed. The directory that **publishes security audits** (e.g., "this mod does NOT read env vars") becomes trusted by enterprises in a way the Anthropic default directory cannot easily match. **This is the differentiator vs. the official directory.**
- **Revenue path:** at scale, charge enterprise customers for "allowlist of audited mods" (a $500/seat/yr line item) and charge mod authors for premium placement (a $100/mo line item). B2B SaaS on a community base.

### Risk + mitigation

- **Risk:** Anthropic ships an official security-audit layer and the differentiator disappears.
- **Mitigation:** be cross-vendor from day 1 (Claude Code + OpenAI Dots + Copilot). The multi-vendor angle is the real moat; the audit is just the hook.

### What to do before next weekend

- 1-page memo describing the wedge, the market (who pays, when, how much), and the 90-day build plan.
- Mock-up the directory landing page (one HTML artifact; 2 hours of work).
- 3 cold emails to Claude Code mod authors asking "what would you want from a directory?"

**Add to [STARTUPS.md](../STARTUPS.md) at next weekly rollup.**
