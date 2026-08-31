# Career & Startup — 2026-07-22

Two career reads and the wedge conversation for founders.

Tags: `#jobs #careers #startup #wedge #ai-safety #handshake #cycle`

---

## 1. The 2027 recruiting cycle just flipped — AI/ML intern postings > SWE intern postings, first time ever {#1-cycle-flip}

**What happened:** Handshake / CNBC / Extern data covering the **2027 US new-grad recruiting cycle** (which opens now, July 2026) shows:

- **AI/ML intern postings** now **exceed traditional SWE intern postings** — the **first cycle ever** in which that's true.
- Overall class-of-2026 hiring is **up 5.6% YoY**; **77.2% of recent grads** land a role within three months.
- The paradox: **CS grads still show ~6.1% unemployment** — the *median* is fine, but the *tail* looks nothing like it did in 2022.
- Specific lanes hiring hardest: **cybersecurity, cloud, AI/ML engineering.**

Layer that against the Q2 lobbying filings ([`01` §3](./01-big-lab-moves.md#3-anthropic-lobbying)) — priority issues *cybersecurity + copyright + defense procurement* — and today's OpenAI × HF incident ([`01` §1](./01-big-lab-moves.md#1-openai-hf-breach)), and the concentration is unmistakable: **AI safety / eval / red-team / cyber-adjacent AI engineer** is the outperformer within the outperformer.

**Sources:**
- [CNBC — By the Numbers: What the class of 2026 job market actually looks like — and where AI fits in](https://www.cnbc.com/select/class-of-2026-hiring-stats-and-ai-trends/) `[secondary]`
- [FinalRoundAI — Computer Science Job Market 2026](https://www.finalroundai.com/blog/computer-science-graduates-face-worst-job-market-in-decades) `[analysis]`
- [Extern — Tech Internships Summer 2027: Timeline & Links](https://www.extern.com/post/tech-internships-summer-2027-guide) `[secondary]`
- [GitHub — speedyapply/2026-AI-College-Jobs (daily updated new-grad AI/ML jobs)](https://github.com/speedyapply/2026-AI-College-Jobs) `[primary]`
- [GitHub — speedyapply/2026-AI-College-Jobs/NEW_GRAD_USA.md](https://github.com/speedyapply/2026-AI-College-Jobs/blob/main/NEW_GRAD_USA.md) `[primary]`
- [ZipRecruiter — Computer Science AI New Grad jobs (aggregator with salary bands)](https://www.ziprecruiter.com/Jobs/Computer-Science-Ai-New-Grad) `[aggregator]`

### Do this today (60 minutes total)

1. **Rewrite your LinkedIn headline** (10 min) — include specifically **"AI Safety Evals · Agent Security · Cost-Aware Orchestration"** if you can honestly say you've shipped an artifact in any two of those. (Tonight's AGENTREDGUARD-lite hook from [`03` §2](./03-practical-skills-and-tools.md#2-agentredguard-lite) covers the first two.)
2. **Refresh your search on the speedyapply repo** (10 min) — grep the NEW_GRAD_USA.md for `safety`, `red-team`, `evals`, `trust`, `alignment` — flag every match to apply to this week.
3. **Send 3 warm intros** (20 min) — target: one Anthropic Trust & Safety Engineer, one OpenAI Model Behavior researcher, one Palo Alto Prisma AIRS engineer. Reference the OpenAI × HF postmortem in the opening line: *"the containment gap you named in the postmortem is exactly what I've been building against — here's my repo."*
4. **Update `APPLICATIONS.md`** (20 min) — add the three postings; log the outreach.

### Why it matters to you (Job · Startup · Insight)

- **Job:** The market is naming the winning specialty out loud — **AI safety-eval engineer** is the *specific* lane where AI/ML intern demand > SWE intern demand + Q2 lobbying priorities + this-week news headlines all point to the same seat. Two months ago on 2026-05-16 we called it "AI Integration Engineer / FDE." Today the narrower version — **AI safety eval + agent security** — is the outperformer. Don't abandon the FDE identity; add "with an AI-safety-eval focus" to it. **You are still one artifact away from being credible in the specific version of this lane that recruiters are trying to fill.**
- **Startup:** Founders always hire ahead of the median. The cycle flip means that the founding engineer / first-5 hires at **the ~30 Series-A / B agent-security startups** (Pillar, Exaforce, Judgment Labs, and roughly 25 stealth-mode peers) will be **CS grads with published safety-eval artifacts** — not senior SWEs, because senior SWEs don't have this material and won't take the pay cut. **You are inside the natural demographic for this hire.** Talk to those companies before their next round closes.
- **Insight:** In a *bad* median job market, the *distribution* still has clear winners — you just have to name them out loud. The lane naming this week: **AI safety eval, red-team, agent security, cyber-refusal calibration.** Every one of those is unspeakably specific — which means recruiters can filter for it and stack-rank instantly. That's what you want. The *last* thing you want in a low-median market is a generic profile ("AI/ML Engineer") — you want a *narrow* profile that scores 90th percentile on a keyword filter.

→ Cross-link: [ACTIONS.md — the week's application queue](../ACTIONS.md) · [APPLICATIONS.md — outcome tracker](../APPLICATIONS.md) · [ME.md — refresh keywords line](../ME.md).

---

## 2. Founder wedge check-in — "policy-safe execution for agentic pipelines" now has a named anchor buyer {#2-wedge}

**Where the wedge sits after today:**

The [STARTUPS.md](../STARTUPS.md) wedge for "policy-safe execution / agentic-SOC middleware" had three open questions at last update (2026-05-22):

1. *Who is the named buyer?*
2. *What is the demoable primitive?*
3. *What is the market signal for pricing?*

Today answers all three:

| Question | Answer as of 2026-07-22 |
|---|---|
| **1. Named buyer** | Any org that is running (or auditing) an eval like OpenAI × HF ([`01` §1](./01-big-lab-moves.md#1-openai-hf-breach)) *plus* any enterprise deploying **Cursor / Codex CLI / Gemini CLI / Antigravity** who saw the Pillar disclosures ([`02` §1](./02-new-emerging.md#1-pillar-sandbox)) *plus* any org in the four Anthropic-listed lobbying priority verticals ([`01` §3](./01-big-lab-moves.md#3-anthropic-lobbying)). |
| **2. Demoable primitive** | The **AGENTREDGUARD-lite hook** from [`03` §2](./03-practical-skills-and-tools.md#2-agentredguard-lite): PreToolUse hook + argument-parser allow-list + JSON audit trail + 6-case eval matrix that mirrors AgentRedBench ([`04` §1](./04-research-progress.md#1-agentredbench)). |
| **3. Pricing signal** | **Per-seat security control**, not per-token AI. Reference comp: **SOC 2 tooling ($10–20/seat/mo), IDE security plugins ($8–12/seat/mo), Prisma AIRS enterprise tiers ($15+/seat/mo)**. Price at $8–12/seat/mo to land the mid-market, offer a governance-tier at $30 with a dedicated audit-export SLA. |

### Your-fit score refresh (see STARTUPS.md tiering)

- **Timing:** 9/10 (news + benchmark + taxonomy landed same week — one-time window)
- **You-fit:** 7/10 (you can ship the hook tonight; you need one security-domain co-founder or advisor to close the buyer-side credibility gap)
- **Anchor buyer legibility:** 8/10 (post today, named in OpenAI's own blog)
- **Competitive density:** 6/10 — Pillar, Exaforce, Judgment Labs are Series A / B in adjacent lanes but not the *dev-workflow-sidecar* wedge specifically
- **Composite:** **7.5/10** — highest wedge score in the STARTUPS.md log since 2026-05-22.

### Why it matters to you (Job · Startup · Insight)

- **Job:** Even if you don't found — this wedge is the *hiring shape* of five different companies interviewing new-grads in Q3 2026. Ship the demoable primitive, use it as a portfolio piece to *get hired into one of them*, then re-evaluate the founder path in Q4 with much better market signal. **This is the safest possible way to run the founder bet — you get paid to test the wedge from inside a peer company.**
- **Startup:** If you are going to found — **the anchor buyer and the demoable primitive should not sit idle for another week**. Two-day sprint: hook + repo + landing page + 5 cold sales emails to CISO / Head of AppSec at named enterprises with obvious Cursor / Codex / Antigravity footprints (Shopify, Stripe, Ramp, Coinbase, Databricks — pick any five you can name warm intros into). Standard founder-market-fit test: *do 5 CISOs take the meeting?* If yes, the wedge is real and the founder path is ROI-positive vs the job path. If 0/5, revisit and de-risk.
- **Insight:** The **3 open questions → all answered in one week** pattern is what you want as a founder-timing signal. It doesn't happen often. When it does, **the founders who won that wedge started building the same week**, not the same quarter. If you're serious, block Saturday and Sunday.

→ Cross-link: [STARTUPS.md wedge log](../STARTUPS.md) · [ACTIONS.md founder-track tasks](../ACTIONS.md) · [WATCHLIST.md agent-security thread](../WATCHLIST.md).

---

## 3. Weekly rhythm reminder

- **Weekend artifact this week:** the AGENTREDGUARD-lite hook + LinkedIn thread ([`03` §2](./03-practical-skills-and-tools.md#2-agentredguard-lite)).
- **Applications this week:** 3 warm intros + 2 speedyapply flags (§1 above).
- **Spend audit:** Aug 4 (per [`ME.md`](../ME.md) personal rules).
- **Next SOURCES.md review:** early August (adding **Pillar Security blog**, **Zhipu AI GLM release notes**, and the **Handshake Employer Insights** report to Tier 3).
