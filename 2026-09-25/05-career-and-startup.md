# Career & Startup — 2026-09-25

The AI-Engineer hiring map is stable at the top and reshuffling in the middle. **Three lanes changed value this week:** marketplace-integration engineering (Amazon), AI-policy & compliance (Amodei essay → antitrust), and cost-router / eval authoring (Opus 5.5 + Sol/Luna + Batch).

Tags: `#careers #jobs #startups #agentic-ai #hiring #compensation #anthropic #amazon #meta`

---

## 1. The hiring map, September 2026 {#1-hiring-map}

**Aggregate:**
- **AI Engineer** = most-hired AI role (per Axial Search analysis of 43,500+ postings).
- **Machine Learning Engineer** = most-common AI title in Europe; **64% of all AI engineering postings** carry ML-Engineer or a close variant.
- **Agentic-AI skill** in job postings went from **0.06% → 0.23%** of US postings YoY — **+280%**, roughly **90,000 postings** referencing agents specifically.
- **~1,550 AI-eng postings/week** through H1 held; the September curve looks similar (per [2026-09-10/05 §1](../2026-09-10/05-career-and-startup.md#1-hiring-map)).

**Compensation (US, September 2026, base):**

| Level | Base range | TC context |
|---|---|---|
| Entry / new-grad MLE | **$90K–$135K** | Frontier lab / big-tech: +$40–80K equity refresh |
| Mid-level (3–5 yrs) | **$122K–$180K** | +$50–120K equity, +bonus |
| Senior (5–8 yrs) | **$180K–$280K** | +$150–300K equity |
| LLM specialist | **$220–280K base** (per [2026-09-10](../2026-09-10/05-career-and-startup.md)) | Frontier labs approach $500K+ TC |
| Middle-80% of roles | **$122K–$265K** | — |

**Experience skew:** 78% of AI/ML-eng postings target 5+ yrs; 66% are IC; 35% mid, 31% senior.

**Geography:** California = 32% of US postings; Tech (46%), Financial Services (14%), IT Services (11%) lead by industry.

**Sources:**
- [Axial Search — AI/ML Engineering Jobs in 2026 (10,000+ posts)](https://axialsearch.com/insights/ai-ml-engineering-jobs/) `[analysis]`
- [Axial Search — Inside the AI Engineering Job Market: 43,500 Postings Analyzed](https://axialsearch.com/insights/ai-engineering-jobs) `[analysis]`
- [Axial Search — State of the ML Engineering Job Market in 2026](https://axialsearch.com/insights/ml-engineering-jobs) `[analysis]`
- [ilinmaks — AI job market 2026: who gets hired, what they earn, which roles are fading](https://www.ilinmaks.com/blog/en/ai-jobs-market-2026) `[analysis]`
- [Open Data Science — 12 Most In-Demand AI Job Roles in 2026](https://opendatascience.com/12-in-demand-ai-job-roles-2026-how-to-get-hired/) `[secondary]`
- [Glassdoor — 24,883 machine learning engineer Jobs, Sept 2026](https://www.glassdoor.com/Job/us-machine-learning-engineer-jobs-SRCH_IL.0,2_IN1_KO3,28.htm) `[aggregator]`

### Why it matters to you

- **What actually changed this week:** "Agentic AI" as a listed skill is now a *filter* on 90K US postings. If your LinkedIn skills list doesn't include it, add it tonight — with a link to a real artifact (the router from [`03` §3](./03-practical-skills-and-tools.md#3-router-refresh)) as proof.
- **Target lanes for you specifically** (extending [ME.md](../ME.md)):
  1. **AI Integration Engineer** (unchanged; still #1 lane per your ME.md focusing decision) — Anthropic Solutions, OpenAI FDE, PwC / Deloitte / Accenture / EY AI Engineer, Plaid / Intuit / HubSpot / Canva.
  2. **AI Integration Engineer, Marketplaces** *(new this week)* — Amazon Bedrock Agents / Selling Partner, and whoever ships Shopify + Etsy + Walmart parity plugins next.
  3. **AI-Policy / Compliance Engineer** *(new this week)* — Anthropic Public Affairs, OpenAI Global Policy, DeepMind Responsibility, Meta Responsibility. Legal-adjacent, CS-required.
  4. **Cost/Router Engineer** *(rising)* — every AI-Ops function inside every frontier-adjacent company. Small teams, high leverage.

---

## 2. The marketplace-integration wedge {#2-marketplace-integrations}

**The setup:** [Amazon opened Seller Central to outside agents on Sept 23](./01-big-lab-moves.md#4-amazon-agents), with Claude in beta. Shopify, Etsy, eBay, Walmart Marketplace, Mercado Libre, JD.com, Rakuten are all near-certain to publish plugin APIs within 30–90 days — competitive pressure guarantees it.

**Founder-track application:**

| Wedge | Positioning | Distribution moat | 12-month rev target |
|---|---|---|---|
| **Multi-marketplace seller agent** | "One agent that runs your Amazon + Shopify + Etsy + Walmart" | First-mover with real inventory arb logic | $2–5M ARR from top 500 multi-platform sellers ($200–500/mo) |
| **Agent-safe marketplace SDK** | "Vercel for marketplace-agent integration" | Standard-setting | $5–10M ARR if you become the default routing layer |
| **Marketplace-agent observability** | "Datadog for agent-driven commerce" | Enterprise usage-based | $2–3M ARR from mid-market marketplaces |
| **Vertical seller-agent (single niche)** | "Amazon Handmade agent," "Etsy vintage-jewelry agent" | Community/vertical | $500K–$2M ARR, exit-fit for the horizontal winner |

**Job-track application:**

- Amazon Bedrock is hiring for the Selling Partner plugin team; search LinkedIn for **"Bedrock Agents" + "Selling Partner"**.
- **Shopify AI Platform** almost certainly stands up a parity team inside 30 days; pre-apply now to the general Shopify AI Eng track.
- **The interviewing story you can start telling this week:** "Amazon just published a first-party plugin API for external agents. In 90 days, three other marketplaces will follow. The scarce role is the engineer who has *already* built the multi-marketplace routing/reconciliation layer." — that reframing works on both founder-hire and BigCo-hire calls.

**Sources:**
- [`01` §4 Amazon opens Seller Central](./01-big-lab-moves.md#4-amazon-agents)
- [Dreaming.press — Founder's Wire, Sept 25](https://dreaming.press/posts/2026-09-25-founders-wire-amazon-agents-seller-central-anthropic-enzyme-safa.html) `[analysis]`

### Why it matters to you

- **Startup lens:** This is *the cleanest new-market signal of Q3 2026 for your ME.md profile* — big incumbent publishes a plugin API, first-mover startups get 90 days of head-start before the second marketplace opens. Weekend prototype target: **a Claude-Agent-SDK skeleton that reads a Shopify store's inventory and generates the Amazon listings for the top 20 SKUs**, publishable as OSS by Sunday night.
- **Job lens:** If you'd rather work at Amazon than build the startup, apply to the Bedrock Agents team this week. The best signaling artifact is the same OSS repo above.

---

## 3. The policy / compliance-engineer lane repriced upward {#3-policy-lane}

**What changed:** The [Amodei essay + antitrust suit](./01-big-lab-moves.md#1-pacing-antitrust) means every frontier lab now needs:
- Someone who can draft/lobby the "narrow safety waiver" bill (**Congressional Affairs Engineer** — CS + policy background).
- Someone who can run cross-lab safety conversations under litigation-hold discipline (**Trust & Safety Ops Engineer**).
- Someone who can build the *evidence-integrity* infra so those conversations are subpoena-defensible (**Compliance Platform Engineer**).

**Where to apply:**
- **Anthropic Public Affairs / Responsible Scaling** — actively hiring per their public jobs page.
- **OpenAI Global Policy / Governance** — likely posting engineering-adjacent PMs and technical policy analysts.
- **Google DeepMind Responsibility & Safety** — new-grad and mid-level slots.
- **Meta Responsible AI** (note: Meta *dissents* from pacing — role there is more product-side than coalition-side).
- **CAISI (Center for AI Standards and Innovation)** and **UK AISI** — government-adjacent, high-leverage, less competitive.

### Why it matters to you

- **Job lens:** These lanes were mid-tier in May; they're mid-to-top-tier now. Salary bands haven't fully reset yet — apply *this month* while comp is still catching up. If your ME.md targets Anthropic Solutions (yes), consider adding **Anthropic Responsible Scaling Solutions** to the list — same company, adjacent surface, currently under-applied-to.

---

## 4. Startup-side thesis crystallization {#4-thesis}

**The founder thesis for Sept 2026 (compressed):**

> **The agent primitive is being installed everywhere.** The scarce infrastructure is: (1) the routing layer that picks which agent/model for which task at which price; (2) the memory layer that decides when to remember; (3) the connector layer between agent and marketplace/enterprise app; (4) the safety/verification layer that proves the agent behaved. All four are unowned. Ship a real MVP in any of them and you're inside a 6-month window.

**Your fit (per [STARTUPS.md](../STARTUPS.md) and [ME.md](../ME.md)):**

- **Best-fit wedge:** the **routing + observability layer** (extends your router-artifact work; adjacent to the [2026-05-22/05 dual-model sanitizer](../2026-05-22/00-tldr.md); marketplace-integration is the specific vertical).
- **Weekend deliverable:** publish a public repo — "Multi-marketplace agent skeleton (Amazon + Shopify)" — with the router artifact underneath and the OpenRouter Batch API wired in for the enrichment step. That is one artifact carrying three of the four thesis pillars.
- **Cold outreach targets this week:** 5 messages, distributed as:
  - 2 × Anthropic (one Solutions, one Applied AI on the Bedrock/Amazon partnership).
  - 1 × Amazon Bedrock Agents.
  - 1 × Shopify AI Platform.
  - 1 × any pre-Series-A marketplace-agent startup on the Vinit Shahdeo funded-startup tracker.

---

## 5. Actions for this week (Fri Sept 25 → Fri Oct 2) {#5-actions}

- [ ] **Tonight** — Ship the router refresh PR (`03` §3). One PR, includes Opus 5.5 + Sol + Luna + Batch. Add screenshot + cost table to `README.md`.
- [ ] **Saturday** — Start the multi-marketplace agent skeleton (Amazon Selling Partner plugin + Shopify Admin API + Claude Agent SDK). Aim to publish Sunday night.
- [ ] **Sunday** — Read Jev-Mem paper ([`04` §1](./04-research-progress.md#1-jev-mem)); note 3 sentences you can quote in a Monday interview.
- [ ] **Monday** — Update LinkedIn: add "Agentic AI," "Claude Opus 5.5," "OpenRouter Batch API," "Amazon Bedrock Agents"; pin the router repo.
- [ ] **Tuesday** — 5 cold outreach messages per §4 above.
- [ ] **Wednesday** — When Anthropic public S-1 lands (expected end-of-Sept): extract the three columns from [`01` §5](./01-big-lab-moves.md#5-anthropic-s1) into a one-page memo, share on LinkedIn.
- [ ] **Thursday** — 2 applications (Anthropic Solutions + Amazon Bedrock Agents; or substitute a peer role).
- [ ] **Friday** — Rerun the cost audit ([`03` §1](./03-practical-skills-and-tools.md#1-opus-55-economics)); take the delta screenshot; end-of-week update to [ACTIONS.md](../ACTIONS.md).

**Cadence rule (from [ME.md](../ME.md)):** one artifact per weekend, no exceptions. This weekend's artifact = the multi-marketplace agent skeleton.
