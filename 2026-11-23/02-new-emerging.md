# New & Emerging — 2026-11-23

Funding slowed to one high-signal story this week (**Sierra reportedly in talks at ~$30B**), but the market-structure story is louder: **three $8–$3 frontier models** now sit at the same price band with Fable 5.2 #1, GPT-6.2 Astra #2, Gemini 4 Neon #3 on the public intelligence index — and **Ramp's token-share data (Anthropic 49.3%, +10.5% MoM)** confirms the enterprise money is already following those model rankings. The emerging thread: an **"arms dealer"** category underneath the frontier labs is settling — Sierra for customer service, Rox for sales, fal for inference infra, Harvey/Decagon/Nooks each holding one vertical logo — and the public-markets scoreboard is pricing them against Anthropic/OpenAI/Google at legible multiples for the first time.

Tags: `#funding #market-structure #agents #vertical-ai #arms-dealers`

---

## 1. Sierra reportedly in talks for ~$1.5B at ~$30B valuation (The Information, Nov 18) {#1-sierra}

**What happened (2026-11-18):**
- **The Information reported** that Sierra (Bret Taylor's AI customer-service agents company) is in talks to raise **~$1.5B at ~$30B valuation**.
- That is **~2× the May 2026 mark** of $15–$15.8B (when Sierra raised $950M, covered in 2026-05-19).
- **Status: talks, not a closed round.** Treat the valuation as a target, not a fact; wait for the primary disclosure before wiring it into pitch math.
- No lead investor named in available coverage.

**Sources:**
- [Value Add VC — Sierra in talks at $30B valuation](https://valueaddvc.com/pulse/sierra-30b-valuation-talks-1-5b-round-2026) `[analysis]` (citing The Information)

### Why it matters to you

- **Job lens:** A 2× revaluation inside 6 months pulls Sierra's internal hiring bar up — expect **TC band jumps of 10–20% for new hires** and tighter interview loops. If Sierra is one of your five target FDE applications, fire it this week before the comp band formalizes — early hires post-mark typically get the better equity. Interview signal: Sierra specifically filters for **vertical-depth founders / customer-engineer types** (healthcare, financial services, retail support) over generic ML résumés.
- **Startup lens:** $30B at (conservatively) ~$120–$150M ARR implies a ~200× revenue multiple — **~20–30% above typical AI-agents comp**. If it closes, every "AI customer service / sales / support agent" pitch repries against $30B as the North Star. The flip side: a ~$30B Sierra occupies the category hard enough that the next general CX-agent raise *at any size* will have to answer "why not Sierra." Vertical-only wedges from here (healthcare-specific, utilities-specific, government-specific).
- **Insight:** The signal is **"The Information scoop + no counter-leak"** = Bret Taylor is comfortable with the valuation framing. Bret Taylor has IPO'd two companies (Salesforce as CTO, OpenAI board chair) and knows how to sequence a public-markets exit. A ~$30B mark 6 months before a plausible IPO window is **pre-IPO positioning**, not a mid-cycle up-round.

→ Cross-link: [`05` §5 — Sierra as FDE target this week](./05-career-and-startup.md#5-sierra-fde)

---

## 2. Thin / unverified rounds this window {#2-thin-rounds}

Three names appeared on Nov funding roundups but **could not be verified against primary sources** in this research window. Logging them as watch-items, not as facts.

- **ASI — reported $325M Series C**
- **Sentra — reported $150M Series C** (Capital One Ventures lead)
- **Pliant — reported $80M Series C**

**Source:** [AI Funding Me — November 2026 roundup](https://aifunding.me/roundups/november-2026) `[aggregator]`

**Treatment:** Don't publish specific numbers until a primary (company blog / Crunchbase / Form D) confirms. All three may be legit but the aggregator in question also showed some stale totals. **The verified M&A story of the week is Sierra's revaluation; everything else is unconfirmed.**

### Why it matters to you

- **Insight:** This is **post-IPO week quiet** in AI funding — a recognizable pattern. A huge IPO absorbs late-stage attention (press, LP conversations, legal bandwidth) for about two weeks. **Expect a backlog of $100M+ rounds to land Dec 5 → Dec 20** as advisors clear their Anthropic engagements. If you track funding for signal, the **first week of December is the one to focus on**.

---

## 3. Three-model week — the price-per-intelligence-point just collapsed {#3-three-model-week}

**The structural fact:**

| Model | Launched | $/M in | $/M out | Intelligence Index | Rank | Context |
|---|---|---|---|---|---|---|
| Claude Fable 5.2 | Nov 10 | **$8** | **$40** | top | **#1** | 1M |
| OpenAI GPT-6.2 Astra | Nov 17 | **$8** | **$40** | +5.2 vs GPT-6 | **#2** | ~1M |
| Google Gemini 4 Neon | Nov 18 | **$3** | **$15** | **61 @ max effort** | **#3** | 1M |
| OpenAI GPT-6.2 Sol | Nov 17 | $2 | $10 | mid | (tier below) | 272K+ |

**Three observations:**

1. **The $8/$40 price band is now the "frontier" bucket**. Fable 5.2 and GPT-6.2 Astra priced to the exact dollar. Expect a quarterly dance around this number until the next compute generation.
2. **Gemini 4 Neon is $3/$15 at #3 on intelligence** — a ~62% price drop vs the $8/$40 tier for ~90% of the intelligence (back-of-envelope). That's the **best-value frontier model as of today**.
3. **Price-per-intelligence-point has fallen ~30% in 10 weeks** (vs the start of Q4 2026 baseline). The curve is steepening, not flattening.

**What is still vendor-specific:**
- **Coding (Terminal-Bench 4.1, FrontierCode 2.0):** Claude only. Opus 5.5 remains on top.
- **Agents' Last Exam:** OpenAI claims lead on cost-adjusted score with GPT-6.2 Astra.
- **Vending-Bench 2 + SEC-bench Pro:** Google Gemini 4 Neon leads (agentic business workflows, finance-filing analysis).

**Sources:** All referenced in [`01`](./01-big-lab-moves.md).

### Why it matters to you

- **Job lens:** This table **is** the answer to the FDE whiteboard question "how do you pick a model?" Save it, memorize the rank order and price band, and in an interview draw the two-axis chart (cost-weighted × task-class-weighted). Then name an eval that tests the pick. Two sentences into a model question and you'll be visibly in the top 10% of applicants.
- **Startup lens:** If your app does **generalist text generation** at >1M tokens/month, route to **Neon** first, escalate to Fable 5.2 only on failure — you'll save ~60% of your model bill. If your app does **code-in-a-shell** (agent-mode coding, SWE-Bench workflows), stay on **Opus 5.5 / Fable 5.2**. If your app does **tool-heavy agents** with many short completions, test **GPT-6.2 Astra** — OpenAI's agent harness is improving fastest.
- **Insight:** The **Opus-5.5 coding monopoly** is now the single highest-value Claude-specific moat. **If you have exactly one portfolio artifact to ship**, make it a working MCP server + Claude Code 2.1.326 Code-Mode hook that demonstrates Claude-specific coding wins. That is the portfolio piece that cross-sells into *every* Anthropic/OpenAI/Sierra/Decagon FDE pipeline you have open.

→ Cross-link: [`03` §2 — ship your routing policy tonight](./03-practical-skills-and-tools.md#2-routing-policy) · [`01` §2 — GPT-6.2 pricing](./01-big-lab-moves.md#2-gpt-62) · [`01` §3 — Neon's workflow benchmarks](./01-big-lab-moves.md#3-gemini-4-neon)

---

## 4. Ramp token-share regime change — Anthropic 49.3%, +10.5% MoM {#4-ramp-token}

**What happened (2026-11-11):**
- Ramp published its **November AI Index: "New Fronts in the AI Trade"** covering October data.
- **Total AI token spend +10.5% MoM** — breaking the ~flat multi-month pattern that defined Aug–Sept.
- **Anthropic token share: 49.3%** (week ending Nov 1) — a 5+ pp lead over the next vendor.
- Vendor share by *dollars*: **Anthropic 44.8% / OpenAI 40.6%** (close-run on dollars, Anthropic clearly ahead on tokens).
- **Adoption:** 56.8% of U.S. businesses on Ramp using AI (+1 pp MoM, +13.3 pp YoY).
- **Spend:** Median $16.32/employee/month (+$0.93); top-1% **$10,199.20/employee/month** (up from $7,500 cited in prior edition — verify against Ramp's own page).
- **Department cut (secondary coverage, verify):** **Engineering = ~72% of classified AI spend**.

**Sources:**
- [Ramp AI Index — New Fronts in the AI Trade (Nov 2026)](https://ramp.com/data/ai-index-nov-2026) `[primary]`
- [Crypto Briefing — Ramp AI Index top 1% spending](https://cryptobriefing.com/ramp-ai-index-top-1-percent-spending/) `[secondary]`

### Why it matters to you

- **Job lens:** The engineering = 72% number (if it holds) explains why the **FDE hiring surge is concentrated at infra/engineering-first customers**. If you can speak Anthropic + show a GPU-aware project, you're hiring-signal-positive at any top-1% spender — and there are ~1,500 of them. On outbound: target companies whose public comms or job boards reference "AI platform team" or "AI engineering" (not "AI ops" or "AI operations" — different budget).
- **Startup lens:** **+10.5% MoM is a regime change from ~flat** — the "token prices are falling faster than usage grows" pattern that threatened thin-wrapper startups through Q3 has broken. Enterprise usage is scaling into the price cuts. For a wrapper startup, this is the first month in 2026 where margin compression from price cuts is at least offset by volume growth. **Still verify your own cohort data before celebrating** — the median $16.32 number says it's the top 1% driving the aggregate.
- **Insight:** **49.3% Anthropic token share, pre-IPO, is the most valuable single data point for your Claude bet.** That number validates the specialty-lane decision in your `ME.md` (Anthropic agentic stack as primary portfolio investment) and gives you a quotable statistic for every interview this quarter. Memorize: "Anthropic hit 49.3% of enterprise AI token share, per Ramp's November index, the same week it went public."

→ Cross-link: [`05` §3 — Ramp index (careers)](./05-career-and-startup.md#3-ramp-index) · [`ME.md`](../ME.md)

---

## 5. The arms-dealer layer is settling — what's left to build around it {#5-arms-dealers}

**The sorted-out category as of today:**
- **Customer-service agents:** Sierra (~$30B talks), Decagon ($1.5B earlier 2026), Cognigy, Parloa → **category closed to generalists**
- **Sales agents:** Rox ($1.3B, Nov 11 prior edition) → **category closed**
- **Inference infrastructure:** fal ($16B, Nov 3 prior edition), Baseten, Together, Modal, Replicate → **two tiers emerging** (brand + commodity)
- **Legal:** Harvey → **still single-vendor premium**
- **Sales dev / outbound:** Nooks → **cap-light wedge**
- **Vertical-of-the-week open:** manufacturing (Anthropic plugin shipped Nov 9), construction, utilities, government, lab automation

**What is still open for a 2026–27 startup:**
1. **Routing / observability / cost-governance infra for the three-model world.** $8 × 2 + $3 = many permutations; spend is now big enough that a $20–$50M ARR company fits in the margin.
2. **Eval-as-service for agents** — Terminal-Bench 2.1 audit shows the category needs hardening.
3. **Vertical agents in regulated industries** — FDA/HIPAA, SOX, banking — where the generalist incumbents won't go because compliance work is uneconomic without distribution.
4. **Agent memory + cross-session continuity.** SlackBench (arXiv 2611.05512) and the research-agent delivery paper (arXiv 2611.14364) both show a persistent reliability gap that is market-sized.

### Why it matters to you

- **Job lens:** For your two-track job search, the arms-dealer sorting says: **customer-service/sales FDE jobs are high-volume this quarter; inference-infra SRE/MLE jobs are high-leverage this quarter; vertical-AI roles are a 2027 bet**. Apply wide on CX-agent FDEs *now*; file one well-researched inference-infra application *and one* vertical-AI application alongside.
- **Startup lens:** If you want to found or co-found, the four open lanes above are the **best risk-adjusted bets as of 2026-11-23**. Of those four, **(1) routing/observability** has the fastest time-to-ARR (enterprise AI budgets are big enough right now) but the hardest moat; **(3) vertical regulated** is the slowest to first revenue but the easiest to defend. For a first startup, pick (1); for a decade-long bet, pick (3).
- **Insight:** The arms-dealer sort is fast enough that **a "generic AI agent for X" pitch is now DOA across tier-1 VCs** unless X is a regulated vertical or you have an unfair data/distribution advantage. The 2027 equivalent of the 2026 "AI customer service" wave will be **"agent for compliance / governance"**, not another horizontal category.

→ Cross-link: [`05` §5 — Sierra as job target](./05-career-and-startup.md#5-sierra-fde) · [`STARTUPS.md`](../STARTUPS.md)
