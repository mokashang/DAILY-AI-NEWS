# Big Lab Moves — 2026-10-29

The 6 days since the Oct 23 edition produced the single most consequential document of the 2026 AI cycle for a job-seeking CS grad: **Anthropic's public S-1**. Everything else this week — GPT-6.1 Terra at $1/$5, the GSA 40% expansion, the Mithril acquisition, the six Legal Artifacts, the 20-partner AI for Science expansion, the SentinelOne embed — is either the counter-move to the S-1 (OpenAI) or the pre-roadshow legibility sweep (Anthropic's own vertical-coverage story for the S-1 reader).

Tags: `#labs #anthropic #openai #ipo #s1 #gsa #verticals #legal #science #pharma #cyber`

---

## 1. Anthropic S-1 filed public (Oct 26) — Nasdaq "ANT", $16.3B H1 revenue, 11,900 enterprise accounts $100K+, NRR ~900% {#1-anthropic-s1}

**What happened (2026-10-26):** Anthropic filed a Form S-1 registration statement with the SEC for a proposed initial public offering of Class A common stock. Nasdaq Global Select Market ticker: **ANT**. The confidential draft was submitted to the SEC on June 1, 2026; the public filing landed Oct 26. The registration statement is on file but **not yet effective** (no securities can be sold until it is).

**Key financials disclosed:**

- **Revenue:** ~$16.3B in the six months ended June 30, 2026, vs ~$1.2B in the year-earlier half (~13.7× YoY). Q2 2026 revenue ~$11.56B; Q1 2026 revenue ~$4.73B. (Q1 alone exceeded all of 2025.)
- **Mix:** Consumption revenue ~$13.1B (80%); subscription revenue ~$3.2B (20%).
- **Run-Rate Revenue (Anthropic's reported metric, replaces ARR):** passed $65B at end-July 2026 (Bloomberg first-reported, CNBC confirmed). Methodology: trailing-28-day consumption × 13 + monthly subscription × 12. Oct 31 figure was left blank in the public filing.
- **Enterprise:** **~11,900 customers paying $100,000 or more per year** (up from ~950 a year earlier) — **~12.5× YoY growth in six-figure accounts**.
- **Retention:** **Net Revenue Retention ~900%** — i.e. the median paying cohort grew ~9× in a year (interpret with care: NRR this high is dominated by a few hyperscaling accounts, but the headline number itself is unprecedented in SaaS or consumption-pricing comps).
- **Loss:** ~$80.7B H1 loss, overwhelmingly a non-cash remeasurement of convertible instruments (not operating loss). Underlying operating profitability was projected positive earlier in Q2 per 2026-05-21 reporting; the S-1's own operating-loss number is the one to read against the compute bill ($1.25B/mo Colossus burn).

**Trading timing:** WSJ (via CNBC) reports Anthropic is aiming to start trading **the week of Nov 16**, pending SEC effectiveness. Prediction-market traders are pricing an Anthropic IPO as **near-certain inside 2026** post-filing.

**Sources:**
- [Anthropic — "Anthropic files S-1 with the SEC"](https://www.anthropic.com/news/s1-sec) `[primary]`
- [Yahoo Finance — Anthropic IPO live updates: S-1 filing discloses $16.3B in first-half revenue, plans to list as "ANT"](https://finance.yahoo.com/technology/live/anthropic-ipo-live-updates-frontier-ai-lab-discloses-revenue-and-risks-in-highly-anticipated-s-1-filing-141702607.html) `[secondary]`
- [CNBC — Anthropic IPO live updates: AI lab's S-1 filing (Oct 26)](https://www.cnbc.com/2026/10/26/anthropic-ipo-live-updates-ai-s-1-filing.html) `[secondary]`
- [CNBC — Prediction market traders say an Anthropic IPO is near-certain this year after company filed with SEC](https://www.cnbc.com/2026/10/26/prediction-markets-think-anthropic-ipo-near-certain-in-2026.html) `[secondary]`
- [Yahoo Finance — "Anthropic's Public S-1 Still Missing From EDGAR as October IPO Window Opens" (context — now resolved)](https://finance.yahoo.com/markets/stocks/articles/anthropic-public-1-still-missing-210349323.html) `[secondary]`
- [tastytrade — Anthropic IPO 2026: Date, Valuation & Timeline](https://tastytrade.com/learn/markets/industry/anthropic-ipo/) `[analysis]`
- [LeverageShares — Anthropic IPO Tracker: Date, Valuation and S-1 Status](https://leverageshares.com/us/anthropic-ipo-tracker/) `[analysis]`
- [Tech-Insider — Anthropic IPO Filing: $80.7B Loss, $16.3B Revenue](https://tech-insider.org/anthropic-ipo-s-1-filing-ant-nasdaq-16-3b-revenue-2026/) `[analysis]`
- [Mostly Metrics — Anthropic IPO: S1 Breakdown](https://www.mostlymetrics.com/p/anthropic-ipo-s1-breakdown) `[analysis]`
- [Yahoo Finance / Mostly Metrics — Anthropic S-1 "could cross $100B ARR by year-end" reaction note](https://finance.yahoo.com/markets/stocks/articles/anthropic-1-draws-reactions-investor-022736245.html) `[analysis]`

### Why it matters to you

- **Job lens — the S-1 is the single clearest "what does the FDE funnel look like" document ever produced by a frontier lab.** Three numbers to internalize:
  - **11,900 enterprise accounts >$100K** → every one of those accounts has a Claude integration surface. The Solutions / FDE / Applied AI org has to staff against that surface. Even if the average account needs only a fifth of an FDE's attention, that's ~2,400 full-FDE-equivalents of work — and public Anthropic Solutions headcount is nowhere near that. **The hiring ramp is a mathematical necessity, not a maybe.**
  - **~900% NRR** → every landed account expanded ~9× in a year. The "land" motion works. The "expand" motion is where the growth lives. **Expansion work is FDE / Account Technical Lead work**, not sales work. If you can tell the story of a 10× account expansion on a cover letter — even a tiny internal one — you're reading as the right profile.
  - **80% consumption / 20% subscription** → the dollar is token-metered. Every FDE conversation ends with cost. **Cost-aware agent design is now literally the business model.** The repo's active portfolio focus (MCP + cost-aware agent design) is on-note for a reason.

  **Apply plan today** → [`05` §2](./05-career-and-startup.md#2-apply-plan). Four roles, 45 minutes.

- **Startup lens — the 900% NRR is the single most actionable datapoint in the S-1 for a founder.** It validates the Claude-adjacent land-and-expand GTM for H2 2026 / H1 2027. **Three wedges, in order of defensibility:**
  - **(a) Vertical workflow libraries** (contract review, patent review, trial-planning assistant) — this is what Anthropic itself just productized with Legal Artifacts [§4](#4-science-day). You can't out-Anthropic Anthropic on legal; you *can* out-Anthropic Anthropic on three narrower verticals Anthropic won't touch for 18 months.
  - **(b) Cost-telemetry / token-budget products** — if the dollar is token-metered, every CTO wants a per-prompt attribution dashboard. The gap between what Anthropic ships (basic Usage dashboard) and what a $100K+ account needs (budget alerts, team-level attribution, LLM-cost unit economics by product) is a Series-A shaped hole.
  - **(c) Expansion-automation tooling** (the "sell to the next team" motion) — if the median account 9×s, there's a predictable pattern of how team 1 recruits teams 2 through 10 inside the same company. A founder who codifies that path with product (not consulting) gets 11,900 potential customers overnight.

- **Insight — the frontier-lab IPO is now a public-market comp set, not a 2027 story.** Anthropic (ANT) + the (confidential) OpenAI S-1 (May 22 context) + the SpaceX-OpenAI-Anthropic frontier-tech IPO wave means **by Q1 2027 you can trade AI-lab exposure on a Robinhood account**. For a job-seeker: comp bands at labs will trail the first-day pop closely — target offers inside the roadshow window, not after. For a founder: the IPO comps give you a defensible "we're building a public-market-grade AI-infra company" pitch slide. For a researcher: lab headcount growth will inflect post-IPO; the research-residency / safety-fellow lanes will see 2–3× candidate volume starting Q1 2027.

**Reading cross-refs:**
- [2026-05-22 — Anthropic IPO path (October 2026 target)](../2026-05-22/01-big-lab-moves.md) — the original "October target" filing
- [2026-05-22 — OpenAI confidential S-1](../2026-05-22/01-big-lab-moves.md) — the paired OpenAI thread
- [2026-10-14 — Pentagon-Anthropic break](../2026-10-14/01-big-lab-moves.md) — now a disclosure item in Anthropic's risk factors

---

## 2. GPT-6.1 Terra shipped (Oct 26) — $1 in / $5 out per 1M tokens, 50% cheaper, 3× faster agents, computer-use first {#2-gpt61-terra}

**What happened (2026-10-26):** OpenAI released **GPT-6.1 Terra**, positioned as the agent/computer-use tier below Sol and Astra. Pricing: **$1 / $5 per 1M input/output tokens** (standard rate), **$0.05/M for cached input**. Reported tier pricing: Flex $0.50 / $2.50, Standard $1 / $5, Fast $2 / $10 (secondary — not verified against OpenAI pricing page). **50% cheaper than GPT-5.6 Terra and GPT-6.1 Sol**, per OpenAI's claim via BleepingComputer. 1M-token context (apidog/aicybr aggregators; verify).

**Availability:**
- **ChatGPT Work:** Plus, Pro, Business, Enterprise, Edu
- **Codex:** standard
- **API:** `gpt-6.1-terra` model id
- **Not available in ChatGPT Chat** — developer / agent tier only

**OpenAI positioning:** Sol / Astra for the hardest coding + research; Terra for cost-aware agents and computer-use loops. The "3× faster agents" framing suggests Terra is optimized for the toolcall-heavy workloads where Haiku 5.5 and Argon currently dominate.

**Sources:**
- [OpenAI — Introducing GPT-6.1 Sol (companion page; Terra pricing referenced)](https://openai.com/index/introducing-gpt-6-1-sol/) `[primary]`
- [BleepingComputer — OpenAI launches GPT-6.1 Terra with 3x faster AI agents, 50% lower pricing](https://bleepingcomputer.com/news/artificial-intelligence/openai-launches-gpt-61-terra-with-3x-faster-ai-agents-50-percent-lower-pricing) `[secondary]`
- [9to5Mac — OpenAI upgrades ChatGPT and Codex with new GPT-6.1 Terra model](https://9to5mac.com/2026/10/26/openai-upgrades-chatgpt-and-codex-with-new-gpt-6-1-terra-model/) `[secondary]`
- [EdTech Innovation Hub — OpenAI releases GPT-6.1 Terra with 50% lower API pricing and improved computer use](https://edtechinnovationhub.com/news/openai-releases-gpt-61-terra-with-50-lower-api-pricing-and-improved-computer-use) `[secondary]`
- [YourStory — GPT-6.1 Terra launched with 50% lower API pricing for developers](https://yourstory.com/ai-story/gpt-6-1-terra-lower-api-pricing-developers) `[secondary]`
- [LetsDataScience — OpenAI releases GPT-6.1 Terra, cutting price 50% and benchmark error rates](https://letsdatascience.com/news/openai-releases-gpt-61-terra-cutting-price-50-and-benchmark-bc892dc4) `[aggregator]`
- [AI Weekly — OpenAI publishes GPT-6.1 Terra at $1/$5 for computer-use](https://aiweekly.co/fr/alerts/openai-publie-gpt-61-terra-1-5-pour-le-computer-use) `[aggregator]`
- [Apidog — GPT-6.1 Terra Pricing](https://apidog.com/blog/gpt-6-1-terra-pricing/) `[analysis]`
- [AICybr — GPT-6.1 Terra: API Pricing, 1M Context, Computer Use and Coding Benchmarks](https://aicybr.com/blog/openai-gpt-6-1-terra-api-pricing-computer-use-benchmarks) `[analysis]`
- [AI Weekly Substack — AI Weekly: GPT-6.1 Terra, Agent Skills and Anthropic's S-1](https://amdatalakehouse.substack.com/p/ai-weekly-gpt-61-terra-agent-skills) `[analysis]`

### Why it matters to you

- **Job lens:** Terra at $1/$5 drops OpenAI into the **agent-worker tier** that Haiku 5.5 ($0.10/$0.50) and Argon ($2/$10 intro) already occupy. Multi-model agent architectures that pick a per-step model now have **four distinct worker options** (Haiku 5.5, Argon, Terra, Opus 5.5-effort-low). That's an interview question in itself: *"how would you route a 100-step agent workflow across these four models with a $0.50 budget per end-to-end run?"* Have the napkin math ready. (Weekend router artifact in [`03` §1](./03-practical-skills-and-tools.md#1-router-v2).)
- **Startup lens:** Every founder with a Claude-first agent product reads Terra's $1/$5 as the price point for the OpenAI counter-SKU. If your product's unit economics only work at Haiku pricing, Terra just made the "we use OpenAI as a fallback" story safer; if your product's margins already assume Opus-tier calls, nothing changed. Rebuild the per-run cost sheet with Terra inserted; it changes the 50th-percentile call cost by 15–30% depending on your mix.
- **Insight:** The pattern across Haiku 5.5 / Argon / Terra is that **the agent-worker tier is now the most price-aggressive segment of the market**. Flagship pricing is sticky; sub-$5-out-per-M is the lane where labs are willing to lose margin to lock in agent-architecture defaults. If you're a solo dev picking a worker tier, the right default right now is "Haiku 5.5 for the first 80%, Terra for computer-use + the last 20%, Opus 5.5 for the planner."

**Reading cross-refs:**
- [2026-10-14 §3 — Haiku 5.5 shipped](../2026-10-14/01-big-lab-moves.md#3-haiku-55)
- [2026-10-21 — Argon $2/$10 intro + Opus 5.5 effort levels](../2026-10-21/01-big-lab-moves.md)
- [2026-09-10 — Four frontier models in one week](../2026-09-10/01-big-lab-moves.md)

---

## 3. GSA OneGov expansion (Oct 27) — 40% federal discount on Claude, FedRAMP coverage, replaces $1/user promo {#3-gsa}

**What happened (2026-10-27):** The U.S. General Services Administration (GSA) and Anthropic announced an expanded **OneGov agreement** that grants federal buyers a **40% discount on consumption-based pricing for all Claude models available to government buyers, including in FedRAMP-authorized environments** for sensitive unclassified workloads. **No minimum purchase commitment.** Agencies can order direct from Anthropic or through GSA's Multiple Award Schedule.

- **Replaces:** the earlier $1/user/year promotional offer (announced Aug 2026, extended once in September, expired Oct 31).
- **Scope:** federal civilian + "federal civilian-adjacent" agencies. **Does not state coverage for state/local governments** (one secondary blog claims that extension — unverified).
- **Context:** GSA says OneGov has produced **>$1.8B in savings** since inception. OpenAI's GSA deal switched from $1/user to a 50% discount earlier in 2026.
- **DoD caveat:** The 2026-10-14 Pentagon-Anthropic break is unresolved; whether DoD-adjacent civilian agencies (e.g. DoE, DoT, VA components with DoD data) can use the OneGov discount with Anthropic in practice is an open compliance question.

**Sources:**
- [GSA — "GSA, Anthropic Reach OneGov Agreement on Discounted, Consumption-Based Pricing for Claude" (Oct 27, 2026)](https://www.gsa.gov/about-gsa/newsroom/news-releases/gsa-anthropic-reach-onegov-agreement-on-discounted-consumptionbased-pricing-10272026) `[primary]`
- [RuntimeWire — Anthropic expands GSA deal with 40% off Claude usage](https://runtimewire.com/article/anthropic-gsa-40-percent-government-claude-discount) `[secondary]`
- [Unite.ai — GSA extends Anthropic's Claude OneGov offer for federal agencies](https://unite.ai/gsa-extends-anthropics-claude-onegov-offer-for-federal-agencies) `[secondary]`
- [Washington Technology / NextGov — Anthropic extends $1 per user OneGov deal by a month (context, now superseded)](https://www.washingtontechnology.com/contracts/2026/09/anthropic-extends-1-user-onegov-deal-month/416062/) `[secondary]`
- [Mobile World Live — OpenAI swaps $1 government pricing for 50% discount (comparison)](https://mobileworldlive.com/ai-cloud/openai-swaps-1-government-pricing-for-50-discount) `[secondary]`

### Why it matters to you

- **Job lens — a new public-sector FDE lane opens:** The 40% discount on consumption means **federal budget-cycle demand pulls forward**. Agencies will ingest more tokens than they planned, which means **more deployment work than Anthropic Public Sector can staff directly** — so the work goes to the agency-facing consultancies: **Booz Allen, Deloitte Federal, Accenture Federal, GDIT, SAIC, Leidos.** These are an under-tapped FDE lane (less crowded than Anthropic direct; they're hiring on 6-month cycles aligned to the discount's budget uptake). Add two of them to your targeting list this week — specifically "AI Engineer — Federal Civilian Delivery" / "Claude Integration Lead" / "Generative AI Solutions Architect — Public Sector" req boards.
- **Startup lens:** Three wedges open when a 40% federal discount lands:
  - **(a) FedRAMP-authorized Claude integration tooling** (connector packs for DoE, HHS, Treasury data warehouses). High-moat (compliance cost). Low-TAM but high-ACV.
  - **(b) FOIA-friendly agent-audit tooling** — every federal deployment needs an audit trail. If a vendor-neutral audit stack ships this quarter, every OneGov pickup is a potential customer.
  - **(c) Government-specific eval suites** (constitutional-compliance evals, OMB-circular-compliance evals). Likely becomes a Nov 2026 OMB directive after the OneGov expansion lands with volume.
- **Insight:** This is the civilian half of the Pentagon break (Oct 5). The pattern across OpenAI + Anthropic federal strategy is now visible: **the frontier labs are competing for civilian AI budget while DoD budget routes to OpenAI / Google / xAI.** The civilian-FDE lane is specifically Anthropic-coded going into 2027. If a Trust & Safety / Governance target is on your reach list, the Anthropic civilian-FDE positioning *is* the Trust & Safety signal — the Pentagon break and the civilian expansion are the same story told two ways.

**Reading cross-refs:**
- [2026-10-14 §2 — Pentagon-Anthropic break](../2026-10-14/01-big-lab-moves.md#2-pentagon-break)
- [2026-10-14 §3 — Cyber Mission + Critical Infrastructure Defense Program](../2026-10-14/01-big-lab-moves.md#3-cyber-mission)

---

## 4. Anthropic Oct 28 verticals sweep — Legal Artifacts (×6, 60+ integrations) + AI for Science (20 partners) + Mithril Medicine + SentinelOne Mythos 5.1 {#4-science-day}

**What happened (2026-10-27 and 2026-10-28):**

**Oct 27 — Pharma:**
- **Mithril Medicine acquisition** — a sub-10-person startup (founder Cody Tranbarger) developing antibody treatments for two rare forms of **muscular dystrophy**. Founder used Claude to take a lead candidate **from concept to proof-of-principle in mice in 18 months**. Non-peer-reviewed Mithril technical report (Oct 26) reports **~2× forelimb force and grip strength** in treated mice. Clinical-trial start claim: **as early as late 2028** if candidates hold. Terms not disclosed.
- **Six pharma partnerships**: Generate, Divergence, BigHat, Enveda, Pleiades, **Bristol Myers Squibb** (BMS collaboration on clinical-trial planning specifically called out).
- **Context:** separate from the $400M Coefficient Bio acquisition reported earlier in October.

**Oct 28 — Science Day:**
- **AI for Science program expansion to 20 partners**: National Science Foundation (NSF), Simons Foundation, plus 18 more scientific foundations, institutions, and research groups. Free Claude credits.

**Oct 28 — Legal:**
- **Six prebuilt Legal Artifacts**: contract review, citation checks, matter tracking, regulatory monitoring (+2). Shipped as reusable templates inside Claude.
- **60+ legal integrations in the catalog**: Bloomberg Law, Filevine, Ivo, Legora, Patlytics, and 55+ others.

**Oct 28 — Cyber:**
- **SentinelOne** embeds **Claude Mythos 5.1** into its Singularity SOC product. First major SOC vendor to integrate Mythos-tier model directly into alert-triage workflow. "Help our analysts work at the pace of today's threats" — SentinelOne executive quote.

**Sources:**
- [eWeek — Anthropic Launches Six New Claude AI Tools for Legal Work](https://www.eweek.com/news/anthropic-claude-legal-ai-tools/) `[secondary]`
- [AlphaSignal — Anthropic Ships Prebuilt Legal Workflows Directly Into Claude](https://alphasignal.ai/news/anthropic-ships-prebuilt-legal-workflows-directly-into-claude) `[aggregator]`
- [AIwire / HPC Wire — Anthropic: Early Progress on Accelerating Drug Development with Claude (Oct 28)](https://www.hpcwire.com/aiwire/2026/10/28/anthropic-early-progress-on-accelerating-drug-development-with-claude/) `[secondary]`
- [Qazinform — Anthropic reports early progress in using Claude to accelerate drug development](https://qazinform.com/news/anthropic-reports-early-progress-in-using-claude-to-accelerate-drug-development-5f0907) `[secondary]`
- [RuntimeWire — Anthropic acquires Mithril Medicine to run drug programs with Claude](https://runtimewire.com/article/anthropic-acquires-mithril-medicine-cody-tranbarger) `[secondary]`
- [FourWeekMBA — Anthropic Buys a Drug Startup, Runs Claude in 6 Partnerships](https://fourweekmba.com/ai-anthropic-buys-a-drug-startup-runs-claude-in-6-partnerships/) `[analysis]`
- [Digg — Anthropic begins in-house drug discovery alongside six research partnerships](https://digg.com/ai/old0kgvj) `[aggregator]`
- [Crypto Briefing — Anthropic partners with six companies to push Claude into drug discovery](https://cryptobriefing.com/anthropic-claude-drug-discovery-partnerships/) `[secondary]`
- [RohitAI — Anthropic Mithril drug development evidence limits](https://rohitai.com/blog/anthropic-mithril-drug-development-evidence-limits) `[analysis]`
- [FourWeekMBA — Anthropic Gives NSF, Simons and 16 More Free Claude Credits](https://fourweekmba.com/ai-anthropic-gives-nsf-simons-and-16-more-free-claude-credits/) `[analysis]`
- [Investing.com — SentinelOne adds Anthropic's Claude to security service](https://www.investing.com/news/company-news/sentinelone-adds-anthropics-claude-to-security-service-93CH-4983598) `[secondary]`
- [Fox News (live) — Amazon relaxes push for AI use as Anthropic reveals shocking stats (Oct 28 live blog)](https://www.foxnews.com/live-news/ai-news-anthropic-openai-october-28) `[aggregator]`

### Why it matters to you

- **Job lens — six Artifacts × ~10 integrations each = ~60 integration SKUs now shipped**, each of which is a staffing surface. The job titles that would own these:
  - **Vertical FDE** (legal / scientific / pharma / cyber) — a specialty-coded FDE lane that didn't formally exist 60 days ago.
  - **Connector / integration engineer** — the lane from the 2026-10-23 edition; now visible via the Bloomberg Law / Filevine / SentinelOne / NSF integration surfaces.
  - **Deployment research scientist** — Mithril Medicine isn't a drug company Anthropic bought *for* Mithril's pipeline; it's an *empirical case study* Anthropic will cite in every scientific-partner conversation. **This is a research-residency-adjacent role**: half scientist, half FDE. Watch Anthropic careers for a formal "Science Residency" posting in Q1 2027.
- **Startup lens — the "vertical workflow pack" is now a shippable product category.** You can clone this template outside Anthropic:
  - Pick a vertical the labs will not reach for 18 months (e.g., **architecture / AEC**, **tax**, **patent prosecution**, **municipal gov**, **academic peer review**, **non-profit grant writing**).
  - Ship 4–6 Artifact-like templates on top of Claude, integrated with the 3 tools the vertical already uses.
  - Package the integrations under one brand. The Legal Artifacts just gave you the UX template.
- **Insight — this entire Oct 28 package is a *roadshow pitch slide***. Each vertical move is one line in Anthropic's "we're not a chatbot, we're a horizontal infrastructure deploying across law/science/pharma/cyber" slide. When you read a vertical sweep like this, map each announcement back to the S-1's **"Customers" section** and the **"Business" narrative** — that's how you understand what the lab wants the market to believe about it. Then back-compute: what vertical would an FDE candidate who *wants* to join this growth story market themselves into? Life sciences and legal are now overfished going into Q1 2027. **Underfished right now: cyber (SentinelOne embed is signal) + public-sector (GSA expansion is signal).**

**Reading cross-refs:**
- [2026-10-23 §1 — Claude Duet + 6,000 connectors](../2026-10-23/01-big-lab-moves.md#1-claude-duet)
- [2026-10-14 §1 — Claude Frontier Academy](../2026-10-14/01-big-lab-moves.md#1-frontier-academy)
- [2026-10-14 §4 — Anthropic Cyber Mission](../2026-10-14/01-big-lab-moves.md#3-cyber-mission)

---

## 5. Watch: OpenAI public S-1 inside 30 days? {#5-watch}

**What to watch:** The 2026-05-22 edition tracked OpenAI's confidential S-1 submission to the SEC (~May 22). Standard SEC timing says a public filing can follow a confidential draft on the issuer's schedule, typically 15 days before the roadshow starts. **If OpenAI's public S-1 drops before Nov 20, the frontier-lab IPO wave becomes a two-stock, Q4 2026 story — not a 2027 story.**

**Signals to watch:**
- SEC EDGAR for `openai` filings
- CNBC / WSJ reporting of OpenAI pricing-range disclosure
- OpenAI's "Deployment Company" subsidiary (Oct 2026 context from the Tomoro acquisition) — any S-1 amendment that discloses Deployment Company revenue separately would be structurally important.
- xAI / Meta-AI counter-filings: whether a third frontier lab accelerates its own S-1 against the two-horse-race framing.

**Why it matters to you:** If both S-1s are public before year-end, the comp set changes how recruiter negotiations happen: comp bands anchor to public-market valuations rather than private secondary rounds. **Comp-band inflation during the roadshow window is a tactical hiring opportunity** — target offers inside the window, specifically.

**Sources:**
- [2026-05-22 edition — OpenAI confidential S-1 filing](../2026-05-22/01-big-lab-moves.md)
- [BuildMVPFast — Anthropic vs OpenAI S-1 Filing Comparison 2026](https://www.buildmvpfast.com/blog/anthropic-vs-openai-s1-ipo-filing-comparison-2026) `[analysis]`
