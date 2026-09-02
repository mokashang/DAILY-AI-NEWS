# New & Emerging — 2026-06-04

The category that came of age this week is **multi-model routing** — as a *paid* enterprise wedge, not a hack. **OpenRouter $113M Series B at $1.3B post-money**, **CapitalG-led**, with **NVIDIA + Snowflake + Databricks as strategic backers** and **weekly token volume 5× in six months (5T → 25T)**, is the anchor round of the thesis. Underneath: **Gemini's platform numbers passed thresholds that change the consumer landscape** — Gemini app **900M MAU**, AI Mode in Search **>1B MAU**, **Ultra cut $250→$200/mo + a new $100/mo Developer tier**. The frame: *the consumer surface (Apple Extensions, [`01` §3](./01-big-lab-moves.md#3-wwdc)) and the production surface (OpenRouter) are getting wired for routing across labs at the same time.*

Tags: `#funding #openrouter #multi-model #routing #gemini #pricing #deepmind #talent`

---

## 1. OpenRouter $113M Series B at $1.3B post — multi-model routing gets priced {#1-openrouter}

**What happened:** **OpenRouter** — the multi-model API marketplace — closed a **$113M Series B at ~$1.3B post-money**, announced **May 26, 2026**. The round details:

- **Lead:** **CapitalG** (Alphabet's growth fund).
- **Participating:** **NVentures, ServiceNow Ventures, Andreessen Horowitz, Menlo Ventures.**
- **Strategic backers:** **NVIDIA, Snowflake, Databricks** — i.e., both compute supply and enterprise demand explicitly on the cap table.
- **Valuation arc:** $547M post-money one year ago (~$40M Series A in June 2025) → **$1.3B today** — **~2.4× in 12 months**.
- **Usage signal that paid for the round:** **weekly token volume rose from ~5 trillion to ~25 trillion in just six months** (a 5× / 6-month curve).

**Sources:**
- [Business Wire (OpenRouter press release) — OpenRouter Raises $113 Million CapitalG-led Series B as Weekly Volume Explodes to 25T Tokens](https://www.businesswire.com/news/home/20260526953416/en/OpenRouter-Raises-$113-Million-CapitalG-led-Series-B-as-Weekly-Volume-Explodes-to-25T-Tokens) `[primary]`
- [TechCrunch — OpenRouter more than doubles valuation to $1.3B in a year](https://techcrunch.com/2026/05/26/openrouter-more-than-doubles-valuation-to-1-3b-in-a-year/) `[secondary]`
- [SquaredTech — OpenRouter Funding: $113M Series B Revealed For AI Routing](https://www.squaredtech.co/openrouter-raises-113m-to-power-the-multi-model-ai-era) `[secondary]`
- [Inc — OpenRouter Helps Companies Pick the Best AI for the Job—and Could Be Worth $1.3 Billion](https://www.inc.com/ben-sherry/openrouter-helps-companies-pick-the-best-ai-for-the-job-and-could-be-worth-1-3-billion/91325983) `[secondary]`
- [Crunchbase News — The Week's 10 Biggest Funding Rounds: Anthropic Dominates In An Otherwise Slower Week](https://news.crunchbase.com/ai/biggest-funding-rounds-ai-anthropic-65b-dominates/) `[aggregator]`
- [Qubit Capital — US Series B+ Weekly Funding Roundup (May 25–Jun 1, 2026)](https://qubit.capital/blog/us-series-b-plus-weekly-funding-roundup-week-1-june-2026) `[analysis]`

### Why it matters to you

- **Job lens:** **Multi-model routing is now a hiring category, not a side project.** OpenRouter is the unicorn; the next 12 months will produce mid-stage routing/policy/observability competitors with concrete openings for **AI Integration Engineers, Solutions Engineers, MLEs who can quantify cost/quality trade-offs across models.** Two tactical moves: (1) **write a 30-line README** showing a small script that routes a task across Claude / Gemini / GPT and reports per-task cost + quality (your portfolio piece for any Solutions / FDE role); (2) **add "model routing / multi-provider inference" to LinkedIn keywords** — recruiters will search it next.
- **Startup lens:** The **strategic cap table** is the most-readable VC signal of 2026 so far. **NVIDIA bought because routing increases their TAM (more inference, regardless of model). Snowflake + Databricks bought because routing is the inevitable feature their enterprise customers will demand inside the data platform.** For your [`STARTUPS.md`](../STARTUPS.md), the adjacent wedges are now legible: **(1) policy/governance layer on top of routing** (which model is allowed for which data class), **(2) per-tenant cost analytics on top of routing**, **(3) routing-aware eval harness** (which model wins on which slice of *your* traffic). All three have buyers; none has a $1B+ winner yet.
- **Insight:** **The Apple-Extensions move ([`01` §3](./01-big-lab-moves.md#3-wwdc)) and OpenRouter's round are the same thesis on two surfaces.** Consumer (Apple) and enterprise (OpenRouter) both decided in the same fortnight that **the user — not the lab — owns the model choice.** That's a structural shift; if it holds, lab moats need to live somewhere other than "you only use my API." Karpathy's move to Anthropic (recursive self-improvement, [2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)) is one answer to that pressure; **specialized verticals** are another.

→ Cross-link: [`01` §3 Apple Extensions = consumer routing](./01-big-lab-moves.md#3-wwdc) · [`05` §2 skill re-price](./05-career-and-startup.md#2-skill-reprice) · [`STARTUPS.md` routing-adjacent wedges](../STARTUPS.md).

---

## 2. Gemini's platform numbers crossed thresholds: 900M MAU, $250→$200 Ultra, new $100 Developer tier {#2-gemini-platform}

**What happened:** A cluster of Gemini updates from the **post-I/O 2026 window** (May 19 keynote, follow-on updates through end of May):

- **Gemini app crossed 900M MAU** (announced at Google I/O on May 19; more than 2× the ~400M reported a year earlier).
- **AI Mode in Search separately crossed >1B MAU.**
- **Gemini 3.5 Flash** is generally available, framed as "most intelligent model for sustained frontier performance on agentic + coding tasks"; **outperforms Gemini 3.1 Pro** on key benchmarks; **Gemini 3.5 Pro lands in June**.
- **Gemini Omni** (any input → any output, starting with video).
- **Gemini Spark** (agentic assistant initially exclusive to AI Ultra subscribers; carried from [2026-05-19](../2026-05-19/01-big-lab-moves.md)).
- **Pricing change:** **Ultra cut from $250 → $200/mo**; **new $100/mo Developer tier** introduced for engineers and professional users. This is the first material consumer-AI price *cut* of 2026 — and the new Developer tier is positioned exactly where the Claude Code "Max 5x = $100" tier sits.
- **DeepMind talent acquisition:** **~$80–90M licensing deal that brought >20 Contextual AI researchers under DeepMind** — RAG-research consolidation, license-and-hire structure.

**Sources:**
- [Google Cloud Blog — Innovations from Google I/O 26 on Google Cloud](https://cloud.google.com/blog/products/ai-machine-learning/innovations-from-google-io-26-on-google-cloud) `[primary]`
- [Alphabet Investor — Investor presentation, June 2026](https://blog.google/alphabet/investor-presentation-june-2026/) `[primary]`
- [Gemini API — Release notes / changelog](https://ai.google.dev/gemini-api/docs/changelog) `[primary]`
- [StartupHub — Sundar Pichai at Google I/O 2026: Gemini Hits 900M Users](https://www.startuphub.ai/ai-news/ai-figures/2026/figure-sundar-pichai-google-io-2026-keynote-recap-2026-06-01) `[analysis]`
- [HeyGoTrade — Google I/O 2026: Cheaper Gemini, DeepMind Talent Push](https://www.heygotrade.com/en/news/google-io-2026-gemini-deepmind-contextual-ai/) `[secondary]`
- [Tom's Guide — Biggest Google I/O 2026 announcements (Gemini Spark, Intelligent Eyewear glasses and more)](https://www.tomsguide.com/news/live/google-io-2026-live-news-updates) `[secondary]`

### Why it matters to you

- **Job lens:** **The $100/mo Developer tier is a direct shot at Claude Max 5x's price point** — Google is now competing for the *developer* who would otherwise spend on Claude Code. For a job-search angle: **a portfolio artifact that runs the *same* dynamic-workflow audit on Claude Opus 4.8 *and* Gemini 3.5 Pro and reports cost + quality is, by itself, an FDE-level deliverable.** The interview narrative writes itself.
- **Startup lens:** **900M Gemini app + 1B AI Mode = the largest consumer-AI distribution surface in the world**, and Google is now subsidizing developer + ultra usage at lower prices. If you're building consumer-facing, **Gemini API + Google's distribution** is the cheapest path to first 100K users. The trade-off: **ad-incentive contamination** (Google's ad business is the only one big enough to discipline these decisions). The cleanest founder bet against this is a **paid, ad-free, vertical-trust product on Anthropic's stack** — the [`ME.md`](../ME.md) focusing decision survives this update.
- **Insight:** **DeepMind's $80–90M license-and-hire for Contextual AI researchers is a quieter signal worth tracking.** The structure (license IP + bring the team over) is how labs consolidate research-front leads without antitrust friction. Watch for Anthropic / OpenAI doing similar deals — they're the *real* talent-market price discovery, more honest than published comp data.

→ Cross-link: [2026-05-19 Google I/O day](../2026-05-19/01-big-lab-moves.md) · [`01` §3 Apple-Google Gemini partnership](./01-big-lab-moves.md#3-wwdc) · [`05` §2 skill re-price](./05-career-and-startup.md#2-skill-reprice).

---

## 3. The rest of the week's funding — Corgi $106M + the small-but-loud rounds {#3-other-rounds}

**What happened (week of May 25 – June 1, 2026):** OpenRouter ($113M, §1) led the table; the rest of the week's Series-B-and-up rounds:

- **Corgi Insurance — $106M Series B** (US — AI-enabled insurance distribution). Pairs with the [Chapter Medicare-AI $100M Series E from May](../2026-05-12/02-new-emerging.md) as the *insurance-AI-distribution* thread hardening.
- **Orkes — $60M Series B** (AI-enabled software workflow orchestration platform).
- **Series A round-trip data:** Series A rounds for AI startups now **average $51.9M**; rounds **above $100M** are common but concentrated. Median Series B valuations for AI companies are **~$143M** — meaningfully higher than non-AI peers.
- **Anthropic Series H $65B** (ahead of the S-1, [`01` §1](./01-big-lab-moves.md#1-anthropic-s1)) skewed the week's total but is broken out separately.

**Sources:**
- [Intellizence — Top 5 Startup Funding Deals of the Week: Anthropic, Cognition, Stord, OpenRouter, Corgi Insurance](https://intellizence.com/insights/startup-funding/top-5-funding-deals-anthropic-cognition-stord-openrouter-corgi-insurance-lead-the-market/) `[aggregator]`
- [Qubit Capital — US Series B+ Weekly Funding Roundup (May 25–Jun 1, 2026)](https://qubit.capital/blog/us-series-b-plus-weekly-funding-roundup-week-1-june-2026) `[analysis]`
- [Eqvista — AI Startup Fundraising Trends 2026 (Seed → Series B)](https://eqvista.com/ai-startup-fundraising-trends/) `[analysis]`
- [Fundup AI — Recently Funded Startups, June 2026](https://fundup.ai/recently-funded-startups) `[aggregator]`
- [AI Funding Tracker — Latest deals & rounds, 2026](https://aifundingtracker.com/ai-startup-funding-news-today/) `[aggregator]`

### Why it matters to you

- **Job lens:** **Corgi and Chapter together = insurance-distribution-AI is now a hiring lane.** Quiet, vertical, well-funded; less competitive than the frontier-lab funnel. Worth a **15-minute search** for SDE / MLE / Solutions roles at both companies — and at Orkes for workflow-orchestration platform work.
- **Startup lens:** Two facts from the data: (1) **Series A average $51.9M and B median $143M** = the bar is *higher capital and more traction* than the 2024 narrative; (2) **AI companies trade at ~2× non-AI peers in valuation** at Series B. Translation for you: if you go founder, the next 12 months will demand **paying customers + retention by Series A**, not just a model demo. Use this to calibrate the "ship something real" weekend cadence in [`ME.md`](../ME.md).
- **Insight:** The composition of the week's rounds — **Anthropic $65B, OpenRouter $113M, Corgi $106M, Orkes $60M** — is the cleanest picture of the 2026 AI funding stack: one **lab**, one **multi-model platform**, two **vertical applications**. Track that ratio (1 lab : 1 infra : 2 vertical) — it's the kind of pattern that pre-figures the next cycle's defensible moats.

→ Cross-link: [2026-05-12/02 Chapter Medicare-AI](../2026-05-12/02-new-emerging.md) · [`STARTUPS.md` vertical-AI thesis](../STARTUPS.md).
