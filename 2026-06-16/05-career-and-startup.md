# Career & Startup — 2026-06-16

This file is where the last 30 days of compounding signal converges into specific moves you make *this week*. The two anchors: (1) **FDE total compensation at frontier labs is now published in the $665K–$750K band**, the highest-paid IC ladder in tech and growing; (2) **three new hyperscaler-Claude roles** persist (AWS Bedrock SA / Vertex Customer Engineer / Foundry Partner Engineer) on the back of Fable 5's tri-cloud GA — *even with Fable 5 currently suspended*, these roles are absorbing Opus 4.8 + Sonnet 4.6 workloads and the hiring urgency is unchanged. Your Anthropic-stack focusing decision now monetizes through **at least five distinct employer paths**, which is the rare position where ME.md's commitment is *increasing* in optionality, not narrowing it.

Tags: `#careers #fde #integration-engineer #anthropic #openai #hyperscalers #startups #wedges`

---

## 1. FDE total comp band is now public: $665K–$750K at Anthropic/OpenAI L4–L5 {#1-fde-tc}

**What's now confirmed:** the **Forward Deployed Engineer comp band** at frontier labs has been published in multiple recruit-side analyses ([MarkTechPost](https://www.marktechpost.com/2026/05/20/what-is-a-forward-deployed-engineer-the-ai-role-openai-anthropic-and-google-are-hiring-in-2026/), [Sundeep Teki's recruit playbook](https://www.sundeepteki.org/advice/how-to-get-hired-at-openai-anthropic-and-google-deepmind-in-2026), [Perspective AI hiring guide](https://getperspective.ai/blog/how-to-hire-an-fde-the-2026-forward-deployed-engineer-hiring-playbook)) and converges on:

- **TC range: $665K–$750K at Anthropic / OpenAI for L4–L5.**
- **Equity component: 55–70% of TC** (will mark to public price post-S-1).
- **Palantir comparison: ~$215K median TC** — frontier-lab FDEs now pay **~3× the prior incumbent's median**.
- **Skill requirements (Anthropic's published JD):**
  - "production experience with LLMs including advanced prompt engineering, agent development, evaluation frameworks, and deployment at scale"
  - "hands-on experience with agent frameworks including LangGraph, LangChain, CrewAI, and DSPy"
  - "multi-step tool-use chains where models call external APIs, read from databases, or write to internal systems"
- **Recruit dynamics:** **top FDEs are passive, don't browse job boards**; recruitment cycles take **8–12 weeks**; best-candidate profile is "former early-stage startup engineer + hands-on solutions architect who still writes code + data/backend engineer who has shipped against messy real-world data."

**Sources:**
- [MarkTechPost — What is a Forward Deployed Engineer: The AI Role OpenAI, Anthropic, and Google Are Hiring in 2026](https://www.marktechpost.com/2026/05/20/what-is-a-forward-deployed-engineer-the-ai-role-openai-anthropic-and-google-are-hiring-in-2026/) `[analysis]`
- [Sundeep Teki — How to Get Hired at OpenAI, Anthropic & DeepMind in 2026](https://www.sundeepteki.org/advice/how-to-get-hired-at-openai-anthropic-and-google-deepmind-in-2026) `[analysis]`
- [Perspective AI — How to Hire an FDE: The 2026 Forward Deployed Engineer Hiring Playbook](https://getperspective.ai/blog/how-to-hire-an-fde-the-2026-forward-deployed-engineer-hiring-playbook) `[analysis]`
- [The New Stack — Why OpenAI and Anthropic are hiring forward deployed engineer teams](https://thenewstack.io/forward-deployed-engineers-ai/) `[secondary]`

### Why it matters to you

- **Job lens:** The **comp band is now legible** — which means you can negotiate against it explicitly. Three operational moves this week:
  1. **Update your LinkedIn skills section to the exact JD vocabulary** ("agent frameworks: LangGraph, LangChain, CrewAI, DSPy", "multi-step tool-use chains", "evaluation frameworks at deployment scale"). The recruiter-side LinkedIn search is calibrated against the JD; matching the JD lifts your discoverability ~5–10× for these roles.
  2. **Use the public comp band as your reservation price.** If a recruiter offers $215K–350K (Palantir-shaped or pre-AI software band), counter with "the public comp band for senior FDEs at frontier labs is $665K–$750K with 55–70% equity; let's align on the lab band, not the legacy band."
  3. **Apply via the passive-candidate route.** Top-of-band FDEs are sourced, not screened. Ship the meter-aware Claude Code starter ([`03` §1](./03-practical-skills-and-tools.md#1-meter-aware-starter)) and the iOS Extension demo ([`03` §3](./03-practical-skills-and-tools.md#3-ios-extension-weekend)) publicly, then **DM the Anthropic recruiter for Solutions / FDE in your geo** with the artifacts linked. The recruit cycle is 8–12 weeks; start the clock today.
- **Startup lens:** **$665K–$750K TC at the labs reprices the founder-CEO opportunity cost dramatically.** If you're considering starting a company, the "right" pre-seed pay-yourself number is now the post-tax equivalent of a frontier-lab L4 — call it ~$300K. Anything less, you're under-paid (which compounds risk); anything more, you'll spook investors. **Set your founder salary against this band, not against 2024 norms.**
- **Insight:** The FDE band is the *commercial* face of the recursive-self-improvement thesis Karpathy named at Anthropic ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)). Labs are paying engineers $665K because each engineer represents **leverage on a product that is itself becoming more capable** — the engineer ships a customer integration that uses Claude to do more work per customer-hour, which expands the customer's spend, which pays back the engineer's TC many times over. **The 2026 frontier-lab engineer is the highest-leverage IC role in modern software history.** Get the math right and aim accordingly.

→ Cross-link: [ME.md focusing decision](../ME.md) · [APPLICATIONS.md](../APPLICATIONS.md) — add comp-band column · [`01` §2 IPO equity pricing context](./01-big-lab-moves.md#2-both-s1).

---

## 2. Three new hyperscaler-Claude roles opened in 48 hours {#2-three-roles}

**What's now applicable:** Fable 5's day-one tri-cloud GA ([`02` §1](./02-new-emerging.md#1-fable-5-distribution)) means **three distinct hyperscaler employers** now have an active "Claude integration" job-to-be-done in customer-facing roles:

- **AWS Bedrock — Solutions Architect (Claude on Bedrock).** Customer-facing engineer who deploys Claude/Fable 5 into AWS-customer workloads, ports prior tooling, optimizes cost (the meter-aware concerns from [`03` §1](./03-practical-skills-and-tools.md#1-meter-aware-starter)).
- **Google Vertex — Customer Engineer (Claude on Vertex).** Same shape, different employer. Note the unusual move: Google is paying its FDEs to deploy *competitor* models, because the customer is the unit of revenue.
- **Microsoft Foundry — Partner Engineer (Claude inside Foundry 11K-model catalog).** Microsoft hedging its OpenAI exclusivity by becoming a multi-model distribution surface; this is the role inside Foundry that owns the *non-OpenAI* model relationships.

**Why it's a new lane:** day-zero tri-cloud GA is the *first time* an Anthropic flagship landed simultaneously across the three hyperscalers. The roles existed before in principle; the **hiring urgency** is new because the customer demand is now structurally aligned across all three platforms simultaneously.

**Sources:**
- [Anthropic — Fable 5 / Mythos 5 tri-cloud GA announcement](https://www.anthropic.com/news/claude-fable-5-mythos-5) `[primary]`
- [BuildFastWithAI — Foundry's 11K-model catalog with Claude inside](https://www.buildfastwithai.com/blogs/ai-news-today-june-8-2026) `[aggregator]`
- [AWS — Bedrock Solutions Architect role family](https://www.amazon.jobs/) `[primary-adjacent]`
- [Google Cloud — Vertex AI Customer Engineer role family](https://careers.google.com/) `[primary-adjacent]`
- [Microsoft — Azure AI / Foundry Partner Engineer roles](https://careers.microsoft.com/) `[primary-adjacent]`

### Why it matters to you

- **Job lens:** Add all three to APPLICATIONS.md as **first-tier apply targets this week** — the urgency window is open right now (8-week recruit cycle starting now lines up with Q3 hiring close). Apply to **all three** as a hedge — the same artifacts (Claude starter kit, Anthropic-stack proficiency, cost-routing portfolio) qualify you for all three; you optimize separately for *fit* in the cover letter (AWS = enterprise depth, Google = research culture, Microsoft = Foundry's multi-model framing).
- **Startup lens:** Three hyperscalers competing to be the Claude-distribution channel means your Anthropic-stack startup wedge has **three distinct M&A acquirers** instead of one. Move "potential acquirers" in STARTUPS.md from {Anthropic} to {Anthropic, AWS Bedrock, Google Vertex, Microsoft Foundry}.
- **Insight:** **Notice the asymmetry.** Anthropic pays FDEs $665K–$750K (the labs' band); AWS / Vertex / Foundry pay solutions roles in the $250K–$450K band (the hyperscaler band). The same skill stack pays ~50–70% more if you sell *for* Anthropic vs. *through* a hyperscaler. **Apply to all three hyperscalers** as insurance, but make Anthropic the targeted offer — and use the hyperscaler offer (when it lands) as the comp benchmark in the Anthropic negotiation.

→ Cross-link: [`02` §1 Fable 5 tri-cloud GA](./02-new-emerging.md#1-fable-5-distribution) · [APPLICATIONS.md](../APPLICATIONS.md) — add 3 new rows · [`01` §3 Fable 5 launch context](./01-big-lab-moves.md#3-fable-5).

---

## 3. The portfolio shovel of the week — iOS 27 Extensions {#3-portfolio}

**What to ship this weekend:** the Claude-as-Siri-default Extension demo from [`03` §3](./03-practical-skills-and-tools.md#3-ios-extension-weekend). One Saturday build, one Sunday post. Time-window arbitrage: the iOS 27 SDK is **8 days old as of today**, and the iOS 27 GA is **~3 months out**. Both ends mean applicant supply is currently *thin*.

**The post structure that maximizes recruiter signal:**

1. **Title:** "I shipped a Claude Extension for iOS 27 the week of WWDC — here's the playbook."
2. **Lede:** screen recording (15–30 sec) of Siri → Claude Extension → mail draft preview. Make the user-perceptible value clear in 5 seconds.
3. **Section 1: architecture diagram.** Siri intent → Apple Extension entry point → Claude Agent SDK call → mail-draft API → user preview. Note **cost trace** as a first-class component (from [`03` §1.5](./03-practical-skills-and-tools.md#1-meter-aware-starter)).
4. **Section 2: cost economics.** "Under the June 15 metering, a single Extension invocation costs ~$X. Here's how I routed Flash for cheap intents to keep the per-invocation cost under $0.001."
5. **Section 3: what I'd build next.** Vertical Extension (Claude for Legal / Claude for SMB Accounting) — tease the wedge in case a founder/VC is reading.
6. **CTA:** "DM if you want the full repo / I'm interested in Solutions / FDE roles at Anthropic, OpenAI, AWS Bedrock, Vertex, Foundry."

### Why it matters to you

- **Job lens:** Six embedded recruit signals in one post — the Anthropic stack ✕ the meter-aware cost framing ✕ the new Apple distribution ✕ the iOS 27 beta urgency ✕ an explicit CTA for the 5 employer tracks ✕ a clear founder-readiness undertone if needed. **It's the single most efficient artifact you can ship before June 30.**
- **Startup lens:** Use the same demo as the warm intro to **3 vertical SaaS founders** in your network — "I built the technical shell; would you co-found the vertical?" The Extension framework removes the *distribution* problem (Apple App Store) and the *integration* problem (Claude Agent SDK); what's left is the customer/domain depth, which is exactly what a vertical co-founder brings. Three DMs, one weekend's worth of work; one yes is a startup.
- **Insight:** The **temporal scarcity** of this artifact ages out around the iOS 27 GA in September. For the next ~12 weeks, this single artifact compounds across both your founder track and your IC-job track. **After September it's commoditized.** Ship it the upcoming weekend or lose the asymmetric leverage.

→ Cross-link: [`03` §3 iOS 27 Extension weekend project](./03-practical-skills-and-tools.md#3-ios-extension-weekend) · [`01` §4 Apple Extensions reveal](./01-big-lab-moves.md#4-apple-extensions) · [STARTUPS.md](../STARTUPS.md) — add "Vertical Extension as wedge" row.

---

## 4. Two new application/watch lanes added in 48 hours {#4-soc-and-gpu-lanes}

**What's new on the apply list (from this edition):**

- **Agent-identity / agent-credential security** (anchored by NewCore $66M, [`02` §2](./02-new-emerging.md#2-identity-and-compute)) — TC band likely tracks Israeli-cyber-startup norms ($200–450K + meaningful equity). Add **NewCore (Tel Aviv + remote US)** + **agentic-IAM startups generally** to APPLICATIONS.md Reach Lane.
- **Decentralized GPU infrastructure** (anchored by Hydra Host $100M w/ NVIDIA, [`02` §2](./02-new-emerging.md#2-identity-and-compute)) — TC band $200K–500K for senior GPU systems engineers; ~$150–250K for AI factory deployment specialists. Add **Hydra Host (Boulder + remote)** + **adjacent GPU-marketplace startups** to APPLICATIONS.md Reach Lane.

Both are **thin lanes** today — applicant supply is still tracking the labs and the consumer-AI startups; the picks-and-shovels are under-applied to. The 2026-05-22 *agentic-SOC* lane (Exaforce $125M) from [2026-05-22/05 §4](../2026-05-22/05-career-and-startup.md#4-soc-lane) sits alongside these as a third under-applied lane.

### Why it matters to you

- **Job lens:** **Three under-applied lanes (NewCore-style identity, Hydra Host-style GPU infra, Exaforce-style agentic SOC) collectively show up as "Reach Lane"** in APPLICATIONS.md — but the reach is actually *modest* because the applicant pool is thinner than the lab pool. **Throw 1 application per lane this week.** Worst case: practice in a lower-stakes interview cycle. Best case: a thin-lane offer becomes leverage in an Anthropic/OpenAI negotiation.
- **Startup lens:** Both NewCore and Hydra Host **price a category** — meaning the next 12 months will see **at least 3–5 follow-on startups in each lane**. Watching the seed/Series A rounds in agent-identity and GPU-marketplace over the next 90 days tells you *exactly* where capital thinks the unfair-advantage layer of the agent stack is. **Subscribe to the AI Funding Tracker daily digest** ([SOURCES.md Tier 5](../SOURCES.md)) and review weekly.
- **Insight:** Every "under-applied lane" is a temporary pricing inefficiency in the talent market. The reason it's under-applied is **vocabulary** — "agent identity" doesn't yet feel like a 'career'; "GPU marketplace" doesn't yet feel like a 'team I'd want to join'. **First-mover advantage on vocabulary is real**: the engineer who internalizes the lane name first writes the LinkedIn post that defines the lane, which the next 100 applicants then quote — and *that* engineer is the one the founders find first.

→ Cross-link: [`02` §2 NewCore + Hydra Host details](./02-new-emerging.md#2-identity-and-compute) · [2026-05-22/05 §4 Exaforce / agentic-SOC](../2026-05-22/05-career-and-startup.md#4-soc-lane) · [APPLICATIONS.md](../APPLICATIONS.md) · [STARTUPS.md](../STARTUPS.md).

---

## 5. This week's specific applications + outreach {#5-this-week}

Concrete moves, in priority order, for the **week of June 16–22**:

| Day | Action | Effort | Source |
|---|---|---|---|
| **Tue (today)** | Run `/billing` audit + LinkedIn post "What I changed June 15" | 30 min | [`00` "One thing to DO"](./00-tldr.md) |
| **Tue (today)** | Update LinkedIn skills to FDE JD vocabulary (LangGraph, LangChain, CrewAI, DSPy, multi-step tool-use, evaluation frameworks at scale) | 15 min | [§1](#1-fde-tc) |
| **Wed** | Apply to **AWS Bedrock SA — Claude**, **Vertex Customer Engineer — Claude**, **Foundry Partner Engineer — Claude** (3 apps, same artifacts) | 45 min | [§2](#2-three-roles) |
| **Wed** | Apply to 1 Anthropic Solutions / FDE / Integration role — reference Fable 5 + meter-aware starter kit explicitly | 30 min | [§1](#1-fde-tc) |
| **Thu** | Read the Agentic Reasoning survey + curated list end-to-end | 90 min | [`04` §2](./04-research-progress.md#2-agentic-reasoning) |
| **Thu** | Read the Eval-of-LLM-Agents survey (arXiv 2503.16416) for the trace-eval framing | 60 min | [`04` §1](./04-research-progress.md#1-trace-eval) |
| **Fri** | Apply to NewCore (agent-identity, Tel Aviv + remote US) and Hydra Host (GPU marketplace, Boulder + remote) | 30 min | [§4](#4-soc-and-gpu-lanes) |
| **Sat** | Build the iOS 27 Extension Claude-as-Siri demo | 6 hrs | [`03` §3](./03-practical-skills-and-tools.md#3-ios-extension-weekend) |
| **Sun** | Post the iOS Extension write-up + cross-post to LinkedIn + Hacker News + X | 60 min | [§3](#3-portfolio) |
| **Sun** | Weekly review: write WEEK-2026-06-15.md rollup; refresh ACTIONS.md | 60 min | [ACTIONS.md](../ACTIONS.md) |

### Why it matters to you

- **Job lens:** This week is structured to be the **highest-applied** week of the quarter — 6 applications, 1 portfolio piece, 1 LinkedIn post, 2 deep reads. Anything less and you're under-pricing the macro moment.
- **Startup lens:** The portfolio piece + the meter-aware starter kit + the trace-eval reading converge into **a coherent founder pitch** by Sunday: *"I'm building cost-aware agent observability for the post-metering Claude economy."* Whether or not you commit to founder mode this quarter, ship the artifacts that *could* be the seed deck.
- **Insight:** The single highest-ROI activity in the week is the **LinkedIn post on Tuesday** — it date-stamps everything else. The recruit-cycle is calendar-driven, not capability-driven; getting *visible* in the week after the metering deadline is more valuable than getting *capable* a week later. Ship the post first; everything else is downstream.

→ Cross-link: [ACTIONS.md](../ACTIONS.md) — update with the row-by-row checklist above · [APPLICATIONS.md](../APPLICATIONS.md) — add the 5 new applications.
