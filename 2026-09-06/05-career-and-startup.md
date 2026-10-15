# Career & Startup — 2026-09-06

Where **your** goals — CS grad student, targeting startup + FDE/MLE/AI-Integration roles — collide with the week's news. **The FDE surface is now measured at 982 live postings across 462 companies (Sept 4)** — with **OpenAI opening Healthcare + Legal FDE tracks** for the first time. **Startup capital has bifurcated cleanly** — vertical + regulated + revenue-adjacent wins, horizontal wrappers struggle. **DevDay Sept 29 is a dated hiring inflection.** Cadence > intensity — one artifact this weekend (the 3-model comparison in [`03` §4](./03-practical-skills-and-tools.md#4-this-weekends-artifact)) beats five applications you didn't tailor.

Tags: `#careers #fde #openai #anthropic #applied-ai #startups #vertical-ai #healthtech #legal-ai #devday`

---

## 1. FDE market — 982 live postings, 462 companies, OpenAI opens Healthcare + Legal tracks {#1-fde-market}

**What the numbers say (as of Sept 4, 2026):**

- **982 live FDE postings across 462 companies** (FDEPulse aggregator; Plank counts similar).
- **FDE hiring is up ~1,000% YoY through early 2026**, ~800% Jan–Sep 2025, still trending in 2H 2026.
- **OpenAI** aggressively hiring across two job boards; **~23 FDE-titled roles**, including **new Healthcare and Legal FDE tracks** — the first public vertical-FDE structuring inside a lab.
- **OpenAI Deployment Company** hiring FDEs in **5 regions**.
- **Top FDE hirers (rolling):** Palantir · OpenAI · Databricks · Mistral · Cohere · Cresta · Scale AI.
- **Compensation:** OpenAI-official Sept 2026 base ranges — **$162–280K** (FDE), **$153–325K** (Fwd-Deployed SWE), **$170–400K** (OpenAI Deployment Company US FDE). Community-reported TCs: **mid $300–450K · senior $450–550K · staff/principal $600K+**.
- **Career framing:** "FDE hiring is the primary way frontier labs and applied-AI startups convert model capability into enterprise revenue" — the deployment surface is the industry bottleneck, not model quality.

**Sources:**
- [Perspective AI — 2026 FDE Hiring Trends (1,000 job posts analyzed)](https://getperspective.ai/blog/2026-fde-hiring-trends-what-1000-job-posts-reveal) `[analysis]`
- [Plank — FDE Job Market (982 roles)](https://joinplank.com/fde-job-market) `[aggregator]`
- [FDE Pulse — FDE Jobs & Salaries](https://fdepulse.com/) `[aggregator]`
- [KORE1 — How to Hire AI Forward Deployed Engineers in 2026](https://www.kore1.com/hire-ai-forward-deployed-engineers-2026/) `[analysis]`
- [Jobs by Culture — FDE: Fastest-Growing AI Role in 2026](https://jobsbyculture.com/blog/forward-deployed-engineer-boom-2026) `[analysis]`
- [Yochana — Forward Deployed Engineer 2026 Hiring Guide](https://www.yochana.com/forward-deployed-engineer-2026-hiring-guide/) `[analysis]`
- [tryexponent — OpenAI FDE Interview Prep](https://www.tryexponent.com/jobs/fde/openai) `[aggregator]`
- [Pragmatic Engineer — State of the software engineering job market in 2026](https://newsletter.pragmaticengineer.com/p/state-of-the-job-market-2026) `[analysis]`
- [futureproofing.dev — AI Engineer Demand 2026](https://www.futureproofing.dev/resources/ai-talent-gap/ai-engineer-demand-2026) `[analysis]`

### Why it matters to you

- **Job lens (direct):** Two things to do **this week**:
  1. **Apply to at least one of the new OpenAI Healthcare or Legal FDE tracks** — the first-week applicant pool is materially thinner than a mature req, and vertical-tagged FDE roles are the first hires that map to specific customer named accounts. **Even a marginal domain fit** (any grad-school work touching biomedical, clinical, or legal data) is a leverage point.
  2. **Refresh the base OpenAI Deployment Company application** — 5 regions × active hiring means new reqs land weekly.
- **Job lens (interview craft):** From [2026-07-25 §2](../2026-07-25/05-career-and-startup.md#2-fde-market): **~60% of coding-passing candidates wash out on the customer-conversation round.** Record a **2-minute customer-conversation clip** of yourself walking through the 3-model comparison ([`03` §1](./03-practical-skills-and-tools.md#1-astra-vs-opus5)) as if the customer is a mid-market CTO — timing it, delivering it, and cutting the umms. This is a single highest-EV practice rep you can do this weekend.
- **Startup lens:** The **FDE surface is also a wedge signal**. If a lab is hiring FDEs by vertical (Healthcare, Legal), the *deployment gap* in those verticals is real and lucrative — a startup that packages "the boring parts of a Healthcare FDE engagement" (data connectors, HIPAA-compatible telemetry, eval harnesses on public healthcare datasets) is riding a live tailwind.
- **Insight:** **Verticalization is the story.** OpenAI opening Healthcare + Legal FDE tracks is a structural sign the pure "generalist FDE" role peaked and started to specialize — the industry entered its **domain-vertical scale-out phase** for deployment. The next FDE tracks to open are likely **Financial Services** and **Public Sector**; if you're tracking either domain, watch for a **6–12 week window** to apply into a thin pool.

→ Cross-link: [`02` §1 vertical-first funding thesis matches vertical-first hiring](./02-new-emerging.md#1-funding-week) · [`03` §1 the artifact FDE interviews grill you on](./03-practical-skills-and-tools.md#1-astra-vs-opus5).

---

## 2. Startup lens — the mean.ceo filter, the vertical wedge, and what your ME.md commitments imply {#2-startup-lens}

**What the market is saying:**

- Funding is available; **vague AI is un-fundable** ([`02` §1](./02-new-emerging.md#1-funding-week)).
- **Regulated + vertical + revenue-adjacent** wins (biotech, health, cyber, financial ops, legal).
- **Series A round now demands eval + regulated buyer + per-seat pricing**.

**Filter to add to `STARTUPS.md`:**

For each wedge you're evaluating, score 0–2 on each dimension:

| Dimension | 0 | 1 | 2 |
|---|---|---|---|
| Close to revenue | Ad-supported / long payback | Trial-to-paid | Contract-driven / regulated buyer already pays for adjacency |
| Regulated buyer | Consumer, no regulation | Some (fintech-adjacent) | Directly regulated (HIPAA, SOC2, GLBA, GDPR-critical) |
| Physical operations | Pure SaaS | Some workflow tie-in | Ties to a physical / operational process |
| Real-world risk | Low | Medium | High (medical, safety, financial harm) |

**Score ≥5** = plausibly fundable in 2H 2026. **Score ≤3** = tighten the wedge or pick a new one. This isn't a religion — it's the aggregators' current pattern, and pattern-matching to it beats fighting it.

**How this matches your ME.md commitments:**

- Your **Anthropic-stack focus + MCP-server + cost-aware agent** portfolio is well-matched to **vertical-AI** wedges (each vertical needs 3–5 MCP servers + a routing layer). Concretely: **Healthcare Claude workflows** (with EFS-style telemetry) or **Legal Claude workflows** (case-summary, contract-parse, MCP into Ironclad/iManage) both pass the filter cleanly.
- If you want a **less-crowded lane**, look at **AI Integration Engineer for Public Sector / Financial Services** — passes the filter, has fewer YC alumni founders in it, and both sectors are late to the FDE hiring wave that Healthcare/Legal are already in.

**Sources:**
- [Blog.mean.ceo — AI Startup Funding News (Sept 2026)](https://blog.mean.ceo/ai-startup-funding-news-september-2026-2/) `[aggregator]`
- [Qubit Capital — AI startup fundraising trends](https://qubit.capital/blog/ai-startup-fundraising-trends) `[analysis]`
- [Wellows — AI Startups by valuation & growth](https://wellows.com/blog/ai-startups/) `[aggregator]`

### Why it matters to you

- **Startup lens:** Score your three current wedges on the filter tonight. If none scores ≥5, pick two new ones inspired by the OpenAI Healthcare + Legal FDE tracks (§1) — those tracks *are* Anthropic/OpenAI validating the market direction.
- **Job lens (indirect):** Every one of these wedges is *also* a hiring surface. If you can't get to Series A on a wedge, you can often get hired at a Series A/B company already in it — same domain expertise, less capital risk. Update [`APPLICATIONS.md`](../APPLICATIONS.md) with 2–3 vertical-AI companies each week.

---

## 3. DevDay Sept 29 hiring wave — pre-stage {#3-devday-hiring}

**What to do (60 min, before Sept 29):**

1. **Refresh your OpenAI application(s)** across FDE / Deployment Company / Solutions — you want to be in the pool when the DevDay-driven reqs land within 72 hours.
2. **Refresh your Anthropic Applied AI / Solutions / FDE application(s)** — Anthropic historically **counter-hires** off OpenAI DevDay signals within 5–10 days.
3. **Pre-draft your DevDay reaction post** — headline + 3 bullets + comparison-table skeleton. Publishing within 2 hours of the keynote is the peak-attention window.
4. **Calendar the keynote + 90 min after** — treat it as a work block.

**Sources:**
- [OpenAI — Announcing OpenAI DevDay 2026](https://openai.com/index/devday-2026/) `[primary]`
- [OpenAI Jobs — Careers page](https://openai.com/careers/) `[primary]`

### Why it matters to you

- **Job lens:** The dated hiring window is real and short — usually 1–3 weeks of expanded requisitions before the pool re-crowds. Being early in the pool is a **20–30% callback advantage** based on the pattern from prior DevDays.
- **Insight:** If Google or Anthropic counter-programs DevDay (both have historically), the **48-hour comparison-post window** is the largest single-day audience opportunity for a technical writer. Prepare the skeleton.

---

## 4. Fellows track & research residency — still the highest-EV single application (reminder) {#4-fellows}

From [2026-07-25 §1](../2026-07-25/05-career-and-startup.md#1-fellows-deadline): the Anthropic Fellows program remains the single highest-EV research-adjacent application for a CS grad student. **Verify the next cohort deadline on [alignment.anthropic.com](https://alignment.anthropic.com/)** — if a cohort is open, submit before end of Sept.

Adjacent reach applications for the ME.md track:

- **OpenAI Residency 2026** — check openai.com/residency.
- **Google DeepMind Early Career** — check the DeepMind careers portal for the 2026-start cohort.
- **Anthropic Fellows (next open cohort)** — [alignment.anthropic.com](https://alignment.anthropic.com/).

Even a submitted-and-rejected application produces a **research-direction essay** that becomes a portfolio artifact and a data point for future applications. Cadence > outcome.

### Why it matters to you

- **Job lens:** The essay itself is a hiring-eval-worthy document that can be reused across every alignment-adjacent application in Q4.
- **Insight:** These programs increasingly recruit for **eval + safeguard-policy + red-team engineering** in addition to research — matching your skill-reprice from [`03` §5](./03-practical-skills-and-tools.md#5-skill-reprice).

---

## 5. Sunday action checklist {#5-checklist}

Small, concrete, do-this-today:

- [ ] Ship the 3-model comparison ([`03` §4](./03-practical-skills-and-tools.md#4-this-weekends-artifact)) as a public gist.
- [ ] Refresh Claude Code to the Sept build ([`03` §2](./03-practical-skills-and-tools.md#2-claude-code-updates)) — try `managedMcpServers` on one server.
- [ ] Run the Sonnet-5 cost re-audit ([`03` §3](./03-practical-skills-and-tools.md#3-sonnet-repricing)) — pull August's bill, project September.
- [ ] Apply to one **OpenAI Healthcare or Legal FDE** posting ([`§1`](#1-fde-market)).
- [ ] Score your 3 startup wedges against the mean.ceo filter ([`§2`](#2-startup-lens)); update `STARTUPS.md`.
- [ ] Calendar DevDay Sept 29 keynote + 90 min ([`§3`](#3-devday-hiring)).
- [ ] Check the Anthropic Fellows cohort status ([`§4`](#4-fellows)); if open, block time to submit before end of Sept.

Cadence > intensity. If you only do the first three, you've done a good weekend.

---

*Back to top: [`00-tldr.md`](./00-tldr.md).*
