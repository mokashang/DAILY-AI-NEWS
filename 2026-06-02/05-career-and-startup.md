# Career & Startup — 2026-06-02

The post-S-1 hiring window opens today, and it doesn't stay open long. **Anthropic just filed** ([`01` §1](./01-big-lab-moves.md#1-anthropic-s1)); the next ~30 days are the window where JDs are still loose, before the roadshow-quality-control pass tightens them. The macro numbers haven't softened — **AI Engineer remains the #1 fastest-growing US job title at +143% YoY**, with a **56% AI-skill wage premium** (up from 25% one year ago). The skill *gradient* keeps climbing: from "I can prompt" → "I can route, verify, and cost" → "I can run systems that build systems" ([`04` §2](./04-research-progress.md#2-autoresearchclaw)). And the assurance lane from last week needs **rebrand-and-redirect** after today's lighter-touch EO ([`01` §2](./01-big-lab-moves.md#2-trump-eo-signed)).

Tags: `#careers #jobs #fde #anthropic #ipo #skills #startup #playbook #applications`

---

## 1. The post-S-1 30-day hiring window — apply to Anthropic this week {#1-s1-hiring-window}

**The mechanism:** When a private company files a confidential S-1, three things happen to hiring:
1. **JDs and rubrics tighten** within ~30 days — the company starts normalizing every role for the eventual public-disclosure pass (consistent leveling, consistent titles, consistent headcount narrative).
2. **Hiring volume often *spikes* in the run-up to the roadshow** — quarterly headcount growth is a number public-market investors care about; private companies pre-stage hires they'd be embarrassed *not* to have closed by the time the public S-1 prices.
3. **Approval thresholds drop temporarily** as managers race to close reqs before the freeze that often precedes the roadshow itself.

**Net effect:** the **~3-week window starting today (2026-06-02)** is one of the better windows of 2026 to land an Anthropic role on the Solutions / FDE / Integration track.

**This week's apply list (highest-leverage, from [ME.md](../ME.md#job-search-targeting-as-of-latest-edition) targets):**

| Role family | Why this week | Target count |
|---|---|---|
| **Anthropic — Solutions Engineer / Customer Engineer / FDE** | Post-S-1 window opens *today*; the FDE/Solutions function is the one Anthropic disclosed to grow fastest on [2026-05-21/01 §2](../2026-05-21/01-big-lab-moves.md#2-anthropic-colossus) | **2** |
| **Anthropic — Applied / Integration Engineer (customer-facing)** | Same window; rubrics still loose | **1** |
| **OpenAI — FDE / Solutions** | OpenAI's S-1 slipping means hiring discipline *tightens* in the next 6 weeks; apply *before* the freeze | **1** |
| **Frontier-adjacent (Sierra, Decagon, Cognigy)** | Customer-eng adjacencies — comp gap with Anthropic FDE roles narrows here | **1** |
| **AI-application companies (Plaid, Intuit, HubSpot, Canva)** | Integration roles; longer cycle but more positions open | **1** |

**Application artifact to attach (per [ACTIONS.md](../ACTIONS.md)):** the **re-costed routing-table table** from [`03` §1](./03-practical-skills-and-tools.md#1-reroute-opus48), dated today. *"On the day Opus 4.8 dropped, I re-costed our agent team, cut browser-agent cost ~30%, and ran it against one real MCP server."* That's the proof of frontier-velocity that distinguishes you from candidates who list "Claude Code" in their skills.

**Sources:**
- [Anthropic — Confidential S-1 announcement](https://www.anthropic.com/news/confidential-draft-s1-sec) `[primary]`
- [HeroHunt — Fastest Growing AI Roles in 2026: Data and Rankings](https://www.herohunt.ai/blog/fastest-growing-ai-roles-in-2026-data-and-rankings/) `[analysis]`
- [SpectraForce — AI in Hiring 2026: Five Roles Driving Demand and the Supply Problem](https://spectraforce.com/blog/technology-ai-in-hiring/ai-hiring-trends-2026/) `[analysis]`
- [365 Data Science — AI Engineer Job Outlook 2026](https://365datascience.com/career-advice/career-guides/ai-engineer-job-outlook-2025/) `[analysis]`
- [TechTimes — Entry-Level Tech Jobs 2026: 148,092 Cuts Expose Which Skills Still Get You Hired](https://www.techtimes.com/articles/317535/20260601/entry-level-tech-jobs-2026-148092-cuts-expose-which-skills-still-get-you-hired.htm) `[secondary]`
- [Lorien — Which Emerging AI Jobs Will Be in Demand in 2026?](https://www.lorienglobal.com/insights/emerging-ai-jobs-in-demand) `[analysis]`
- [2026-05-15/05 §1 — AI Engineer #1 fastest-growing, +143% YoY (baseline)](../2026-05-15/05-career-and-startup.md#1-ai-engineer-fastest) `[archive]`

### Why it matters to you

- **Job lens:** This is the window. Don't read this entry and bookmark; **submit the Anthropic Solutions / FDE application tonight**. The application doesn't have to be perfect — it has to be *in*, dated within the window, before the rubric tightens. You can always send a follow-up note when you ship the next portfolio artifact.
- **Startup lens:** The macro numbers (143% YoY, 56% wage premium) say one thing clearly: **the *talent layer* of the AI ecosystem is fully priced**. If your startup wedge depends on hiring cheap senior AI engineers, the math doesn't work — design for **leverage on a small team** (Opus 4.8 + agent teams + tight routing), not for hiring scale.
- **Insight:** **MLOps Engineers, Forward-Deployed Engineers, AI Governance specialists** consistently show up in the top-5 most-in-demand list. Two of those three (**MLE** and **FDE**) are in your [ME.md target list](../ME.md#primary-goals). The third (**AI Governance**) is the **rebrand** of the AI-assurance lane from [`01` §2](./01-big-lab-moves.md#2-trump-eo-signed) — keep an option on it (see §3 below).

---

## 2. The skill gradient: prompt → route/verify/cost → systems-that-build-systems {#2-skill-gradient}

**The gradient, named:**

| Layer | What it looks like | What you say in an interview | Status in 2026 |
|---|---|---|---|
| **L1 — Prompt** | "I can write a prompt that gets good output." | "I use Claude effectively." | **Commoditized.** Floor. Not differentiating. |
| **L2 — Route + Verify + Cost** | "I architected a multi-model team; tracked tokens by seat; ran it against a real MCP server with a verifier." | "I designed who-does-what, on which model, verified against real tools, at a predictable cost." | **Where the market is paying right now.** Where Anthropic Solutions / FDE roles select. |
| **L3 — Systems that build systems** | "I designed an agentic pipeline whose output is the *next* version of itself — eval harness, sandboxed experiments, multi-agent peer review." | "I run an auto-research/auto-engineering loop with verifiable artifacts." | **The frontier this year.** Karpathy's hire ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)) + AutoResearchClaw ([`04` §2](./04-research-progress.md#2-autoresearchclaw)) are two sides of this. |

**Where to invest this quarter (your portfolio plan):**
1. **Solidify L2 (the safety project, re-costed today)** — this gets you the interview.
2. **Sketch one L3 artifact** — pick one workflow (research summarization? a code-modernization loop? a personal "scout-the-job-market" agent?) and design it as an iterating loop with **evaluation built in**. Doesn't have to be 23 stages; 5 well-instrumented stages is enough for a portfolio piece.

**Sources:**
- [2026-05-22/01 §3 — Karpathy at Anthropic (the L3 production version)](../2026-05-22/01-big-lab-moves.md#3-karpathy) `[archive]`
- [`04` §2 — AutoResearchClaw (the L3 open-source version)](./04-research-progress.md#2-autoresearchclaw) `[archive]`
- [2026-05-15/05 — AI Engineer #1 fastest-growing US job title](../2026-05-15/05-career-and-startup.md) `[archive]`

### Why it matters to you

- **Job lens:** Almost every candidate now claims L1. A surprising number claim L2 but can't actually produce the token/cost/verifier table when asked. **Almost nobody can credibly claim L3.** Your differentiator is being the *only candidate in the pile* with an L3 sketch — even an incomplete one.
- **Startup lens:** L3 is **where venture capital is currently funding** (Anthropic-stack picks-and-shovels). L2 is **where customers are currently paying** (per-task agent products). Build your startup product on L2 economics and your fundraising story on L3 ambition.
- **Insight:** **The gradient compresses time.** A year ago, L2 was the frontier. Today L2 is the floor. Plan for L3 to be the floor in ~12 months — and start now, not when the market says so.

---

## 3. EO-driven rebrand: from "pre-deployment evaluation" to "frontier-model cyber assurance" {#3-eo-reframe}

**The change:** Today's signed EO ([`01` §2](./01-big-lab-moves.md#2-trump-eo-signed)) **kept the cybersecurity-clearinghouse half** but **softened or dropped the mandatory pre-release review** that was the heart of last week's hiring-lane story. That changes your vocabulary, not your skill investment.

**Updated phrasing for cover letters, LinkedIn, and conversations:**

| Don't say (last week's vocab) | Say (this week's vocab) |
|---|---|
| "Pre-deployment evaluation" | **"Frontier-model cyber assurance"** |
| "AI assurance under federal review" | **"Vulnerability disclosure for pre-release LLMs"** |
| "90-day model-release governance" | **"Clearinghouse-style red-teaming of unreleased frontier models"** |
| "Compliance with mandatory federal AI review" | **"Voluntary participation in the federal AI-cyber clearinghouse"** |

**Where the jobs actually live in this new framing:**
- **Inside the labs** (Anthropic, OpenAI, Google DeepMind, xAI) — red team + adversarial robustness roles
- **Inside enterprises with high cyber-risk exposure** (banks, defense, critical infrastructure) — GRC + AI-security analyst roles
- **Inside the agentic-SOC startups** — Exaforce ([2026-05-22/02 §2](../2026-05-22/02-new-emerging.md#2-exaforce)) and the next round of $100M+ AI-SOC raises that will follow

**Sources:**
- [`01` §2 — The signed EO (today)](./01-big-lab-moves.md#2-trump-eo-signed) `[archive]`
- [The White House — Promoting Advanced AI Innovation and Security](https://www.whitehouse.gov/presidential-actions/2026/06/promoting-advanced-artificial-intelligence-innovation-and-security/) `[primary]`
- [2026-05-22/05 §2 — The (delayed) assurance lane / skill re-price](../2026-05-22/05-career-and-startup.md) `[archive]`

### Why it matters to you

- **Job lens:** Update **LinkedIn headline + GitHub README** keywords *this week*, before the rest of the job market figures out the EO went lighter than expected. First-mover on the *correct* terminology = first to surface in recruiter keyword searches for the new framing.
- **Startup lens:** **A voluntary, light-touch federal framework is bullish for AI-security tooling startups** because it creates buy-side demand without dictating product specs. Exaforce-style agentic SOC is exactly this thesis (and was funded with that thesis pre-EO).
- **Insight:** **Track the *language* of a policy as carefully as the policy itself.** Today's EO uses *"innovation"* before *"security"* in the title — that ordering is the doctrine. Every later regulatory action will be read against this title. Calibrate accordingly.

→ Cross-link: [`01` §2 today's EO](./01-big-lab-moves.md#2-trump-eo-signed) · [2026-05-22/05 §2 the prior version of this lane](../2026-05-22/05-career-and-startup.md) · [`ACTIONS.md`](../ACTIONS.md) · [`APPLICATIONS.md`](../APPLICATIONS.md).
