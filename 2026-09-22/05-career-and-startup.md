# Career & Startup — 2026-09-22

The Tuesday summary for a CS grad targeting SDE / MLE / AI-Engineer or founder tracks: **the pacing consensus opened a brand-new hiring lane (AI-assurance / pre-deployment eval), the Astra-vs-Fable enterprise-share flip rebalances the frontier-lab funnel, and durable-execution / RSI-observability / interpretable-memory are the three founder wedges you can actually prototype this month.** Ship the router-in-Temporal artifact ([`03` §1](./03-practical-skills-and-tools.md#1-durable-execution)) tonight; it's the single-highest-signal move in your funnel.

Tags: `#careers #salary #startups #fde #ai-engineer #mle #hiring #anthropic #openai #pacing #assurance #durable-execution`

---

## 1. The hiring map — where the reqs actually are, week of Sept 22 {#1-hiring-map}

**What happened:** Axial Search's 2026 dataset (**43,500 postings analyzed**) confirms the H1 trend hardened through September:

- **AI Engineer:** LinkedIn's #1 Job on the Rise, ~**1,550 US postings / week**, **median base $176K**, with senior TC clearing **$300K+** once equity is counted.
- **ML Engineer:** ~**490 US postings / week**, sustained through 2026; **70% mid or senior IC**, only 2% director+.
- **FDE (Forward-Deployed Engineer):** **+1,000% YoY through early 2026**, still the fastest-growing single title. Comp bands cluster **$300K–$550K TC** at large labs; **OpenAI + Anthropic mid-and-senior FDEs $385K–$785K**, **frontier-lab principal $1M+ TC.**
- **Vinit Shahdeo's tracker:** still **160+ funded AI startups actively hiring engineers.**

**Skills that hire — the 2026 stack:** Python (still 71% of AI-eng postings), **evaluation authoring**, **cost-aware routing**, **MCP fluency**, **durable-execution wrapping** (new this week — Temporal + LangGraph + Claude Agent SDK), **capability-preview eval** (new this week from the pacing essay), **agent-memory design**.

**Sources:**
- [Axial Search — AI Engineering Jobs: 43,500 Postings Analyzed](https://axialsearch.com/insights/ai-engineering-jobs) `[analysis]`
- [Axial Search — State of the ML Engineering Job Market in 2026](https://axialsearch.com/insights/ml-engineering-jobs) `[analysis]`
- [Perspective AI — 2026 FDE Hiring Trends: What 1,000 Job Posts Reveal](https://getperspective.ai/blog/2026-fde-hiring-trends-what-1000-job-posts-reveal) `[analysis]`
- [Plank — FDE Job Market: 982 Forward-Deployed Engineer Roles](https://joinplank.com/fde-job-market) `[analysis]`
- [Robert Half — AI/ML Engineer Salary (Updated for 2026)](https://www.roberthalf.com/us/en/job-details/aiml-engineer) `[analysis]`
- [Uvik — AI Engineer Salary 2026: Level & Country](https://uvik.net/blog/ai-engineer-salary/) `[analysis]`
- [Vinit Shahdeo — AI Startups Hiring in 2026: 160+ Funded Companies for Engineers](https://vinitshahdeo.substack.com/p/ai-startups-hiring-engineers-2026) `[aggregator]`
- [ilinmaks — The AI job market in 2026: who gets hired, what they earn, and which roles are fading](https://www.ilinmaks.com/blog/en/ai-jobs-market-2026) `[analysis]`

### Why it matters to you

- **Job lens:** Your target list this quarter, refined for the Sept 22 signals: **5 frontier labs + 20 funded AI startups + 5 traditional-SDE safeties + 3 new AI-assurance lane (see §2 below).** New emphasis: **weight Anthropic Solutions / FDE / Applied AI outreach 60/40 over OpenAI's equivalents** — the pre-IPO discipline is real ([`01` §4](./01-big-lab-moves.md#4-astra-flip)), which means fewer roles but higher signal-per-hire. If your artifact stack has the router+durable-execution repo + a hardened MCP server, you're in the top decile of the Anthropic funnel.
- **Startup lens:** The salary anchors also **set your fundraise floor** — if you're founding, budget for the $180–200K base band for a senior AI hire, or you have a durable talent problem. The compounding move: **use the founder-wedge memos ([§3 below](#3-startup-wedges)) as your recruitment magnet**, not just your VC pitch.
- **Insight:** The **September signal shift** is that **specialty carries a premium again.** In H1, generalist "AI Engineer" hires cleared $200K medians. In H2, the roles paying $300K+ are more specialized: **agent-reliability**, **pre-deployment eval**, **memory-agent design**, **model-migration**. Reframe your LinkedIn under one of those subtitles this week — the recruiter outreach delta is meaningful.

→ Cross-link: [`03` §1 the router+durable-execution artifact](./03-practical-skills-and-tools.md#1-durable-execution) · [§2 the pre-deployment eval lane](#2-reprice).

---

## 2. Skill re-price — pre-deployment eval + durable execution up; "current-model fluency" down again {#2-reprice}

**What happened:** Two skills gained value this week thanks to the pacing consensus + Temporal round, one continued its slide.

### 2a. Up: pre-deployment eval / AI assurance (new lane)

The **Global Call for AI Red Lines** ([`01` §1](./01-big-lab-moves.md#1-red-lines)) + Amodei's essay ([`01` §2](./01-big-lab-moves.md#2-amodei-pacing)) will produce a **fundable, hiring category of "capability-preview eval / pre-deployment red team"** inside the next 90 days. The lane is thin today; get in before it's crowded. Roles to search: **Anthropic Frontier Red Team, OpenAI Preparedness, Google DeepMind Safety and Responsibility, US AISI (if federal AI EO revives), UK AISI, EU AI Office, PwC/EY/Deloitte AI Risk, JPMorgan/Goldman AI Risk Office.** Search terms for your LinkedIn: **"pre-deployment eval," "capability preview," "frontier model risk assessment," "AI assurance," "release-gate eval."**

### 2b. Up: durable-execution + parallel-agent orchestration

Temporal's $550M round ([`02` §1](./02-new-emerging.md#1-temporal)) + Anthropic's Claude Projects redesign ([`03` §2](./03-practical-skills-and-tools.md#2-parallel-projects)) validated **reliable agent infra** as core. Recruiters at Temporal itself, Sierra, Cognition, and every top-100 enterprise now filter for: **"Temporal / LangGraph / Claude Agent SDK durable workflows"**, **"parallel-agent orchestration"**, **"per-branch cloud sessions."** If your router artifact ([`03` §1](./03-practical-skills-and-tools.md#1-durable-execution)) is Temporal-wrapped by Friday, add these terms to your headline the same day.

### 2c. Down again: "current model fluency"

Not a new call — but reinforced. Nobody can be current on four labs shipping in 7 days. **The router + eval-suite + Temporal-wrapper pattern replaces it.**

### The compounding move for you (September-October artifact plan)

| Week | Artifact | Why it lands |
|---|---|---|
| This week (Sept 22–28) | Router **wrapped in Temporal** + 5-case eval | Answers "reliable multi-provider LLM infra" |
| Next week (Sept 29–Oct 5) | **Parallel Claude Projects reproducer repo** — coordinator + 3 workers, tests hooked | Answers "you shipped the Sept 17 pattern the week it landed" |
| Week 3 (Oct 6–12) | **MCP server (hardened, HTTP-unified, SSO/audit)** — one workflow you already do | Answers "MCP-native, enterprise-shape" |
| Week 4 (Oct 13–19) | **Pre-deployment eval harness** — a 15-case suite across capability, bio, cyber, manipulation refusal | Answers "AI-assurance ready" |
| Week 5 (Oct 20–26) | **RSI-observability micro-project** — 3-generation self-improving script + audit log | Answers "you've thought about the 2027 problem" |

**Five artifacts by Oct 26.** That is *further ahead of the applicant pool than the Sept 10 plan projected.* — because you're also carrying the July MCP baseline + the router baseline already.

### Sources
- Amodei essay + UN Red Lines coverage → [`01` §1](./01-big-lab-moves.md#1-red-lines) · [`01` §2](./01-big-lab-moves.md#2-amodei-pacing)
- Temporal round → [`02` §1](./02-new-emerging.md#1-temporal)
- Parallel Claude Projects → [`03` §2](./03-practical-skills-and-tools.md#2-parallel-projects)

### Why it matters to you

- **Job lens:** The pre-deployment-eval lane is **early enough that a well-argued one-pager + a 10-case demo eval** is a differentiator. Ship one alongside the router artifact — total time <2 evenings, applies to 3 lanes at once (labs + Big-4 AI Risk + banks).
- **Startup lens:** The router-wedge → **eval-suite-wedge → durable-execution-wedge** progression is the same fundable-thesis progression a Seed VC would draw on a whiteboard. Ship the sequence in public and your **inbound VC ratio changes** measurably around week 3.
- **Insight:** The signal-per-artifact ratio in Q4 2026 is highest for **infra that composes** (router → +Temporal → +eval-harness → +MCP → +RSI-observability). Every additional artifact makes the *previous* ones more valuable, because it demonstrates system-thinking.

---

## 3. Startup path check-in — three wedges to prototype this month {#3-startup-wedges}

The three wedges that (a) are net-new to Sept 2026, (b) match a CS-grad skillset, (c) can be prototyped in 1–2 weekends each.

### Wedge A — Durable-execution middleware for the Claude Agent SDK / LangGraph / OpenAI Agents SDK

- **What to build:** an open-source library that adds Temporal-style durability to the three agent SDKs without forcing a Temporal cluster (start with SQLite-backed workflows, upgrade to Temporal Cloud optionally).
- **Why now:** Temporal's round validated the category; the SDKs haven't shipped durable primitives yet.
- **First-check target:** $500K–$1M pre-seed on a working demo + 2 open-source integrations.

### Wedge B — Recursive-self-improvement observability

- **What to build:** a dashboard + audit log that tracks, per experiment, which pieces of research work were designed / run / interpreted by an agent vs a human; alignment invariants that must hold across generations; drift detection.
- **Why now:** Anthropic's 26% disclosure ([`01` §3](./01-big-lab-moves.md#3-claude-builds-claude)) is the first public metric. Every lab with a preparedness / frontier-red-team will need this, and no incumbent exists.
- **First-check target:** $1–2M pre-seed with an OSS reference + one lab design partner (frontier or fast-follower).

### Wedge C — Interpretable memory-controller middleware

- **What to build:** the [three-signal-controller pattern](./04-research-progress.md#2-memory-controllers) as a plug-in for LangGraph / Claude Agent SDK / OpenAI Agents SDK, with a hosted control plane that visualizes recall decisions.
- **Why now:** Memory has become the second-highest-priority evaluation axis after tool-use, and interpretability is quietly re-entering as a procurement requirement.
- **First-check target:** $500K–$2M pre-seed on a working demo + 2 SDK integrations.

### Do this weekend (4 hours)

Pick one of A / B / C. Write a **one-page memo** with:

- The 3 real payloads (agent × workload × pain-point) that break today.
- The minimal primitive (5 endpoints or fewer) that unblocks them.
- The 500-line reference impl you'll ship next weekend.

Post it publicly. This memo is your seed-round warm-intro currency and your senior-hire recruitment magnet.

### Why it matters to you

- **Startup lens:** The three-wedge shortlist covers the **fundable universe** for a CS-grad-shaped founder in Sept 2026. Everything else on the barbell (frontier models, embodied AI) is capital-constrained beyond your reach; everything below the barbell won't fund without paying customers first.
- **Job lens:** Even if you don't start a company, publishing the memo is the **highest-signal artifact of 2026 for a founder-track hire** (first engineer at a $10–20M Series A startup). These roles want *thesis-quality thinking*, not just code.
- **Insight:** The founder-vs-job decision doesn't have to be made yet ([ME.md](../ME.md)). The two-artifact combination — the router-in-Temporal repo + a founder-wedge memo — is a **preserves-optionality** move: it strengthens your job search *and* is a real founder artifact if the year plays that way.

→ Cross-link: [`01` §1 UN Red Lines / AI-assurance lane](./01-big-lab-moves.md#1-red-lines) · [`02` §1 Temporal round](./02-new-emerging.md#1-temporal) · [`04` §1 RSI papers](./04-research-progress.md#1-rsi-papers) · [`04` §2 memory controllers](./04-research-progress.md#2-memory-controllers).

---

## 4. This Tuesday's concrete moves

- **Tonight (60–90 min):** Ship the router-in-Temporal artifact ([`03` §1](./03-practical-skills-and-tools.md#1-durable-execution)). Public repo. Push to GitHub. Add to LinkedIn "Projects."
- **Also today (20 min):** Update LinkedIn headline / skills line:
  - **Add:** "durable execution", "pre-deployment eval", "parallel-agent orchestration", "recursive-self-improvement monitoring", "interpretable memory."
  - **Keep:** "AI Engineer", "MCP", "Claude Code", "eval design", "model routing", "prompt caching".
- **Applications (this week):**
  - **3 Anthropic:** Applied AI Engineer / Solutions Engineer / Frontier Red Team — attach the router-in-Temporal repo and reference the 26% disclosure specifically as "why I want to work on the R&D-supervision side."
  - **2 OpenAI:** FDE / Preparedness — attach the router-in-Temporal repo and an Astra-vs-Fable eval-run README.
  - **1 Temporal:** SE / Solutions — attach the router-in-Temporal repo as your work sample.
  - **1 US or UK AISI:** any listed technical role — the pacing-consensus + UN-red-lines context is your cover-letter opener.
- **Reading (30 min this week):**
  - Amodei "We Must Pace the Frontier" — the primary source.
  - **One** of the four RSI papers ([`04` §1](./04-research-progress.md#1-rsi-papers)) — pick the one closest to a concrete implementation you'd fork (probably 2609.19526 fast-tree-search).
  - The three-signal memory-controller abstract ([`04` §2](./04-research-progress.md#2-memory-controllers)).
- **Weekend (4 h):** One founder-wedge memo from [§3 above](#3-startup-wedges). Post publicly.

**End-of-week checkpoint:** router-in-Temporal repo shipped, 6 applications out, 2 papers read, 1 wedge memo posted. If you hit this, **you're materially ahead of where the Sept 10 plan projected you'd be by this date.**

### Sources
- All cross-links above.
