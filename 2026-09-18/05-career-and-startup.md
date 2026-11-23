# Career & Startup — 2026-09-18

The two career threads that moved this week: (1) **Anthropic's transparency drop is a job-description generator** — the three metrics + the State of Agents report translate into interview vocabulary and role JDs that will be public within 30 days; (2) **the AI Engineer salary band widened again** ($155K–$252K base, $200K–$310K+ TC), with Bay Area senior ICs now clearing **$252K base** on average, and Anthropic + OpenAI both actively hiring FDE / Applied AI Engineer with **no fixed deadline** (rolling). For a CS grad, the concrete moves are three: **apply this weekend**, **ship one artifact from `03`**, and **submit for Claude Corps cohort 3** (newgrad-safe, applications reopen this September).

Tags: `#careers #salary #fde #applied-ai-engineer #new-grad #startup #anthropic #openai`

---

## 1. The AI-Engineer market update — bar rising, band widening, three roles with rolling deadlines {#1-market}

**The market data (Sept 2026):**

- **Median AI Engineer base:** ~$176K (up from $172K in July per Axial Search's July analysis).
- **Bay Area senior IC base:** ~$252K (a 14% jump from 2024 levels).
- **Mid-level base band:** $155K–$200K; senior TC $200K–$310K, top-of-band $300K+.
- **AI/ML Engineer at mainstream tech employers (Robert Half 2026 Salary Guide):** $134K start · $170,750 mid · $193,250 high.
- **Postings volume:** Axial Search now analyzing **43,500 AI-engineer postings**; the function is the fastest-growing across all AI-adjacent roles.

**Three roles with rolling deadlines this week:**

1. **Anthropic — Forward Deployed Engineer (Applied AI).** Hybrid solutions eng / ML eng / embedded PM for enterprise Claude deployments. Interview loop: recruiter → tech phone → take-home or live coding → customer-conversation simulation → onsite system design. **68 R&E roles listed at last count; no published deadline.** Interview volume is highest H2. `[primary]` → [Anthropic Applied AI Engineer / General Catalyst mirror](https://jobs.generalcatalyst.com/companies/anthropic/jobs/69674588-forward-deployed-engineer-applied-ai)
2. **OpenAI — FDE.** Rolls into DevDay week (Sept 29); recruiter volume peaks Sept 15–Oct 15. Prep tip: use OpenAI's own new incident-disclosure framework language in your "AI oversight" answer.
3. **Anthropic — Claude Corps cohort 3.** 12-month program placing you inside a US nonprofit building practical Claude tools (legal aid, public health, housing, education, food security, conservation). **Applications reopen this September; cohort starts Aug 2027.** The **highest-signal newgrad-safe Anthropic application** in the calendar year. `[primary]`

**Sources:**
- [Axial Search — Inside the AI Engineering Job Market: 43,500 Postings Analyzed](https://axialsearch.com/insights/ai-engineering-jobs) `[analysis]`
- [Kore1 — AI Engineer Salary 2026: $145K–$310K (Real Offer Data)](https://www.kore1.com/ai-engineer-salary-guide/) `[analysis]`
- [Pin — AI Compensation Benchmarks 2026: The AI Hiring Bubble](https://www.pin.com/blog/ai-compensation-salary-guide/) `[analysis]`
- [Robert Half — AI/ML Engineer Salary Updated for 2026](https://www.roberthalf.com/us/en/job-details/aiml-engineer) `[secondary]`
- [Glassdoor — AI Engineer Average Salary Trends 2026](https://www.glassdoor.com/Salaries/ai-engineer-salary-SRCH_KO0,11.htm) `[secondary]`
- [Perspective AI — Anthropic Applied AI Engineer Interview Process 2026](https://getperspective.ai/blog/anthropic-applied-ai-engineer-interview-process-frontier-lab-2026) `[analysis]`
- [Exponent (Aced) — Anthropic FDE Interview Guide 2026](https://www.tryexponent.com/guides/anthropic-forward-deployed-engineer-interview) `[analysis]`

### Why it matters to you

- **Job lens (direct action):** File **3 applications this weekend** — Anthropic FDE / Applied AI Engineer (top of the loop), OpenAI FDE (DevDay window), and Claude Corps cohort 3. Attach the three-metric dashboard screenshot and the stateless-MCP diff link to each. That's a resume tier that beats 90% of newgrad submissions in this cycle.
- **Startup lens:** The **$252K Bay Area senior base** is a two-way signal — (a) if you want to hire a senior IC into your startup, budget $260K + equity + insurance to compete; (b) if you're deciding between a $250K W-2 role and founding, the option value of the founding path needs to clear ~$1.2M / 3 yrs to be equivalent. That's a real math exercise to do this weekend.
- **Insight:** The **"3.2× demand-vs-supply gap"** from [2026-09-17/00 §10](../2026-09-17/00-tldr.md) hasn't closed. But the **entry-level gap has widened** — most postings ask for real production AI/ML experience. The single asymmetric move a CS grad can make in the next 90 days: **land one paid AI-adjacent contract** (a Claude / GPT integration for a small business at $5–15K) — that's "production experience" on your resume for every H2 application.

→ Cross-link: [`03` §1 three-metric dashboard as portfolio](./03-practical-skills-and-tools.md#1-three-metrics-template) · [`03` §3 stateless-MCP port as portfolio](./03-practical-skills-and-tools.md#3-stateless-mcp-checklist).

---

## 2. The weekend artifact — pick one, ship it by Sunday night {#2-weekend-artifact}

Three options. Ship **one** — not all three. This is the Cadence > Intensity rule from [ME.md](../ME.md).

**Option A — The three-metric dashboard (~4 h).** Instrument your top project with Anthropic's three metrics ([`03` §1](./03-practical-skills-and-tools.md#1-three-metrics-template)). Ship a dashboard page + a 300-word README section. Post the screenshot to LinkedIn with "Anthropic released three AI-oversight metrics this week — here's what mine look like." Deliverable = 1 screenshot + 1 GitHub commit + 1 LinkedIn post.

**Option B — The stateless-MCP port + blog post (~4 h).** Port one MCP server to the July 2026 spec ([`03` §3](./03-practical-skills-and-tools.md#3-stateless-mcp-checklist)). Deliverable = 1 PR diff + 1 blog post (500 words) + 1 LinkedIn post about the port.

**Option C — The eval-suite artifact (~4 h).** Given [`04` §1](./04-research-progress.md#1-swe-converged) says SWE-bench top-30 is unorderable, write **your own 5-case coding eval** for your favorite repo — a novel bug, a refactor, a cross-file trace, a doc regeneration, a test-generation task — run 3 coding agents on it, report results. Deliverable = 1 repo + 1 blog post + 1 LinkedIn post. This is the highest-return option for someone applying to Anthropic/OpenAI/GitHub/Cursor roles.

### Why it matters to you

- **Job lens:** Each option produces exactly one interview-conversation topic + one recruiter-searchable keyword cluster. That's the shape of a portfolio artifact that gets you into loops.
- **Startup lens:** Options B and C both open real founder wedges (see [`02` §3 MCP-hosting](./02-new-emerging.md#3-mcp-grows-up) and [`04` §1 bespoke-eval-as-a-service](./04-research-progress.md#1-swe-converged)). Do one, and you have proof of technical execution in a category you might commercialize later.
- **Insight:** The compounding effect of a weekend artifact matters more than the artifact quality. One per week for six months = 26 signal-generating LinkedIn posts + 26 GitHub commits with technical content. Recruiters at frontier labs and top-tier VCs pattern-match on **consistent cadence**, not one heroic project.

→ Cross-link: [`03` §1](./03-practical-skills-and-tools.md#1-three-metrics-template) · [`03` §3](./03-practical-skills-and-tools.md#3-stateless-mcp-checklist) · [`04` §1](./04-research-progress.md#1-swe-converged).

---

## 3. The founder wedge board — what's opened, what's crowded, what's closed {#3-wedge-board}

**Opened this week:**

- **Agent Oversight as a Service** — the three-metric SaaS ([`01` §1](./01-big-lab-moves.md#1-anthropic-metrics)). Buyers: regulated-industry AI users. $5–15M ARR wedge inside 18 months.
- **Compliance-shaped agent memory** — GDPR-style retention/deletion policies for agent memory ([`04` §2](./04-research-progress.md#2-shared-memory)). Buyers: EU + healthcare + finance. Underweighted because "memory" reads as an infra topic; the wedge is compliance + memory together.
- **EU-hosted MCP registry / marketplace** — the Mistral-adjacent sovereign AI thesis ([`02` §2](./02-new-emerging.md#2-mistral-sovereign)). Requires EU data-residency guarantee. Two founders in Paris or Munich are enough to start.

**Hardening (crowded but still open):**

- **Model-router-as-a-service / cost observability** — see [2026-09-10/01 §1](../2026-09-10/01-big-lab-moves.md#1-model-fatigue). Now has ~5 known startups; still winnable in a specific vertical.
- **Bespoke coding-agent evals** — [`04` §1](./04-research-progress.md#1-swe-converged). Two known players; category leader unnamed.
- **AI Integration Engineer as a service** — the FDE-market wedge from [2026-05-08](../2026-05-08/). Multi-body agencies are entering; boutique + vertical specialization still open.

**Closed / late:**

- **Model-fluency content** (courses, newsletters teaching "how to use Claude / GPT") — commoditized, [2026-09-10/00 §10](../2026-09-10/00-tldr.md).
- **Generic MCP server directories** — the value is now hosting + registry + eval, not a list of links.
- **Prompt-engineering-as-a-service** — the frontier labs' first-party docs (see [`03` §2](./03-practical-skills-and-tools.md#2-context-hygiene)) are eating the tail.

### Why it matters to you

- **Startup lens:** If you're going to pick a wedge in the next 90 days, pick from the **Opened** column. **Hardening** column is fine only if you have a specific customer already asking. **Closed** column: do not spend a weekend on any of these; the return isn't there.
- **Job lens:** Any of the **Opened** wedges is also the shape of a great side-project pitch in interviews — "I've been thinking about the three-metric dashboard as a product; here's the prototype." Interviewers at Anthropic Solutions / OpenAI FDE / applied-AI teams love this framing because it's the kind of conversation their sales engineers have with buyers.
- **Insight:** **The wedge lifecycle is compressing.** In 2024 a founder wedge stayed open ~9 months before category leaders emerged. In 2026 it's 3–4 months. That means the **weekend-artifact cadence** ([`05` §2](#2-weekend-artifact)) is not optional; it's the only reasonable pace at which a solo grad can maintain option-space while deciding between founding vs. joining.

→ Cross-link: [STARTUPS.md](../STARTUPS.md) · [ACTIONS.md](../ACTIONS.md) · [APPLICATIONS.md](../APPLICATIONS.md).

---

## Friday action (60–90 min, do it tonight)

1. **Open [APPLICATIONS.md](../APPLICATIONS.md).** Add three rows: Anthropic FDE / Applied AI, OpenAI FDE, Claude Corps cohort 3. Timestamp Friday-night. `[10 min]`
2. **Draft the three cover-letter openers** using the three metrics as vocabulary: "This week Anthropic published three metrics — coverage, intercept rate, safety-compute share. On my own project I run…" `[20 min]`
3. **Pick a weekend artifact from `§2`.** Write the deliverable spec + a saturday morning start-time on your calendar. `[10 min]`
4. **Update [ACTIONS.md](../ACTIONS.md)** with the Sunday-night ship deadline. `[5 min]`
5. **Send 1 cold DM** — a Mistral engineer (or an Anthropic Claude Corps alumnus if reachable). Reference this week's metric release + one specific question. `[15 min]`

Total: **60 minutes, no interruption.** By 11 PM Friday you have 3 filed applications, one weekend commitment on the calendar, one warm intro seeded. That is the shape of a week where the market moves in your favor.
