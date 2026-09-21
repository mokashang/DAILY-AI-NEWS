# Big Lab Moves — 2026-06-10

Four lab-level events stacked into a 48-hour window. **(1)** Today is **Code w/ Claude Tokyo** — Anthropic's first APAC developer event, livestreamed globally, expected to extend the SF-May-6 ship list (Managed Agents public beta, Dreaming, Outcomes) for an APAC enterprise audience anchored on the NEC partnership. **(2)** Yesterday Anthropic shipped **Claude Fable 5 / Mythos 5** — the first models in a new **Mythos-class** tier above Opus 4.8, structurally *the same model with a safeguard switch* (Fable public, Mythos restricted to Glasswing). **(3)** The **IPO race already inverted** — Anthropic filed first at $965B, OpenAI followed on Jun 8 at $852B; Altman walked back near-term timing. **(4)** Tomorrow (T-1), **SpaceX prices the largest IPO in market history** ($135 / share, $1.75T, NASDAQ "SPCX") — the public-market comp for everything else this quarter. The frame: *Anthropic's developer relationship goes APAC, frontier capability splits into two tiers, and the entire AI public-market window opens with SpaceX as the price discovery instrument.*

Tags: `#labs #anthropic #openai #spacex #tokyo #ipo #public-markets #mythos-class #devrel`

---

## 1. Code w/ Claude Tokyo — TODAY, global livestream {#1-tokyo}

**What's happening:** Anthropic's **Code w/ Claude Tokyo** runs **today, 2026-06-10**, with a **global livestream**. It's the first APAC instance of the developer event series ([SF May 6](https://relvehq.com/events/code-with-claude-tokyo), [London May 19](../2026-05-19/01-big-lab-moves.md)) and Anthropic's most concentrated push into the Japanese enterprise market.

**What to expect (extrapolating from SF + London):**

- **Managed Agents public beta** — with Multi-agent Orchestration and Outcomes. Detail in [`03` §1](./03-practical-skills-and-tools.md#1-managed-agents).
- **Dreaming (developer preview)** — agents that **review and reorganize their own session history between runs**. **Harvey** (the legal-AI company) reported a **~6× task-completion-rate lift** after deploying it.
- **SpaceX-compute follow-throughs:** **2× rate limits for Pro/Max/Team/Enterprise**; **1,500% input-token / 900% output-token increase for Tier-1 API**; peak-hours throttling **eliminated** for Pro/Max.
- **APAC customer presenters** — expect NEC (Apr-2026 global partner, ~30k employees on Claude) and Japanese system-integrator partners.
- **New SDK / MCP / Dreaming features** — Anthropic has used both prior events to ship new surface area. Watch for an explicit reference to **AWS MCP Server GA** (live since yesterday — [2026-06-09/02 §1](../2026-06-09/02-new-emerging.md#1-aws-mcp-ga)).

**Sources:**
- [Anthropic — Tokyo: Code w/ Claude 2026 (event page)](https://claude.com/code-with-claude/tokyo) `[primary]`
- [Gadgetbond — Code with Claude 2026: SF, London, Tokyo dates confirmed](https://gadgetbond.com/code-with-claude-2026-anthropic-developer-conference/) `[secondary]`
- [Tygart Media — Code with Claude London (May 19) and Tokyo (June 10): What to Know and Watch For](https://tygartmedia.com/code-with-claude-london-tokyo-2026/) `[analysis]`
- [ChatForest — Code with Claude Tokyo: Builder's Preview for June 10](https://chatforest.com/builders-log/code-with-claude-tokyo-june-10-builder-preview-guide/) `[analysis]`
- [note (chusho_yosuke) — Why Anthropic Chose Tokyo: 3 Perspectives](https://note.com/chusho_yosuke/n/nd174b8025f6b?hl=en) `[analysis]`
- [Relve Events — Code with Claude Tokyo 2026](https://relvehq.com/events/code-with-claude-tokyo) `[aggregator]`
- [MIT Technology Review — Anthropic's Code with Claude showed off coding's future](https://www.technologyreview.com/2026/05/21/1137735/anthropics-code-with-claude-showed-off-codings-future-whether-you-like-it-or-not/) `[secondary]`

### Why it matters to you

- **Job lens:** Tokyo is the **single highest-density learning event** of your week. Anthropic's developer events double as **the hiring funnel** for FDE / Solutions / DevRel — recruiters watch who's actively engaging on the livestream + on X with informed takes. **Action:** watch the livestream live, post **one specific technical reaction** (cite a feature by name) to X / LinkedIn within 2 hours, and tag at least one Anthropic engineer who presented. The keyword-precision discipline from [2026-05-20/01 §1](../2026-05-20/01-big-lab-moves.md) applies.
- **Startup lens:** Japan is **structurally under-built** as an Anthropic-ecosystem market — NEC is the anchor, but the **system-integrator layer** (Fujitsu, NTT Data, Hitachi, accenture-Japan) is wide open. If you have any APAC connection, this is the **lowest-competition geo** for a Claude-Partner-Network–style consulting or vertical-AI startup. Anthropic's Partner Network ([2026-06-03 announcement](../2026-06-09/02-new-emerging.md#2-partner-network)) is the discovery surface.
- **Insight:** This is Anthropic's **first** APAC developer event and its **third** Code w/ Claude overall in 6 weeks. Cadence ≈ every 2 weeks now. That cadence rate is a *direct read on revenue urgency* — they're using developer events to onboard the build-side of the customer pipeline ahead of the S-1 financials becoming public. Read every Code w/ Claude announcement through that lens: *what does this enable a developer to spend money on this quarter?*

→ Cross-link: [`03` §1 Managed Agents build path](./03-practical-skills-and-tools.md#1-managed-agents) · [`05` §1 FDE hiring through the events surface](./05-career-and-startup.md#1-fde-hiring) · [2026-06-09/01 §1 WWDC graded scorecard](../2026-06-09/01-big-lab-moves.md#1-wwdc-graded).

---

## 2. Claude Fable 5 & Mythos 5 — the "Mythos-class" tier ships {#2-fable-mythos}

**What happened:** Anthropic released **Claude Fable 5** on **2026-06-09**, the first publicly available model in a new **Mythos-class** tier above Opus 4.8. The same underlying model with safeguards *lifted in specific areas* ships as **Claude Mythos 5**, gated behind the **Project Glasswing** program ([`02` §1](./02-new-emerging.md#1-glasswing)). The split is the headline architecture choice: *capability without misuse-resistance is a different product than capability with it.*

- **Naming convention:** "Fable" = public, fully-safeguarded; "Mythos" = restricted-access. Same weights.
- **Pricing (Fable 5):** **$10 / $50 per MTok** input/output — **2× Opus 4.8** and **2× GPT-5.5** input. **Batch:** $5 / $25 per MTok.
- **Benchmarks:** **SWE-bench Pro: 80.3%** vs **GPT-5.5: 58.6%** — a +21.7-point margin on Anthropic's hardest internal coding eval.
- **Availability:** API `claude-fable-5`, consumption-based Enterprise, Amazon Bedrock at launch.
- **Subscription window:** Included **at no extra cost** in Pro / Max / Team / seat-Enterprise **through 2026-06-22**. **From 2026-06-23**, programmatic usage requires credits — paired with the Agent SDK metering change on Sun Jun 15.
- **Mythos 5 access:** Restricted to **Project Glasswing** + **vetted cybersecurity researchers**. Anthropic states it will *not* release Mythos to the general API.

**Sources:**
- [Anthropic — Newsroom](https://www.anthropic.com/news) `[primary]`
- [Yahoo Finance — Claude Fable 5 and Mythos 5 Launch: What To Know](https://finance.yahoo.com/markets/crypto/articles/anthropic-claude-mythos-launches-today-142844796.html) `[secondary]`
- [Codersera — Claude Fable 5: Anthropic's New Mythos-Class Model (Benchmarks, Pricing)](https://codersera.com/blog/claude-fable-5-launch-guide-2026/) `[analysis]`
- [Finout — Claude Fable 5 and Mythos 5: Pricing, API Costs, and Benchmark Comparison vs Opus 4.8 and GPT-5.5](https://www.finout.io/blog/claude-fable-5-mythos-5-pricing-benchmarks) `[analysis]`
- [Vellum — Claude Fable 5 & Claude Mythos 5 Benchmarks Explained](https://www.vellum.ai/blog/claude-fable-5-and-mythos-5-benchmarks-explained) `[analysis]`
- [Unico Connect — Claude Fable 5 & Mythos 5: Benchmarks, Pricing, Verdict](https://unicoconnect.com/blogs/claude-fable-5-mythos-5) `[analysis]`
- [DigitalApplied — Claude Fable 5 & Mythos 5: The Frontier, Split in Two](https://www.digitalapplied.com/blog/claude-fable-5-mythos-5-release-benchmarks-2026) `[analysis]`
- [TokenMix — Claude Fable 5 Review 2026: Pricing, Benchmarks, vs Opus 4.8](https://tokenmix.ai/blog/claude-fable-5-review-pricing-benchmark) `[analysis]`
- [DevToolPicks — Anthropic Splits Claude Subscriptions: June 15 Changes](https://devtoolpicks.com/blog/anthropic-splits-claude-subscriptions-agent-sdk-credit-june-2026) `[analysis]`

### Why it matters to you

- **Job lens:** Strongest possible reinforcement of your `ME.md` Anthropic-stack focusing decision. The Mythos-class concept *only* makes sense if you understand both Anthropic's safety story and deployment patterns — exactly the **Solutions / FDE / Integration Engineer** skillset you're targeting. Interview line: **"the Mythos-class split is the right way to ship a frontier model with asymmetric capability/misuse-risk profiles."** Pattern-matches an FDE answer in one breath.
- **Startup lens:** The 2× pricing of Fable 5 vs Opus 4.8 is **not a bug, it's the routing primitive**. Smart agent teams will keep Opus 4.6/4.8 in worker roles and put **Fable 5 only at the orchestrator step** (or on the *last 10% hardest* tier). Startup wedge: **a model-router + cost ledger** that lets a developer say "do this hard step on Fable 5, the rest on Sonnet 4.6" and *prove* cost-per-resolved-task — pairs with the Agent SDK metering change (T-5).
- **Insight:** The Mythos/Fable split is the most important *governance design pattern* of 2026 so far. It cleanly answers a problem the Trump EO ([2026-05-22/01 §1](../2026-05-22/01-big-lab-moves.md#1-eo-postponed)) couldn't: *how do you give security defenders the strongest model without handing it to anyone with $10/MTok?* Same weights, two distribution rails. Expect every frontier lab to copy this within 6 months.

→ Cross-link: [`02` §1 Project Glasswing (Mythos's deployment surface)](./02-new-emerging.md#1-glasswing) · [`03` §1 Managed Agents (where Fable 5 lives in your stack)](./03-practical-skills-and-tools.md#1-managed-agents).

---

## 3. IPO race — Anthropic filed first ($965B), OpenAI followed ($852B); Altman softens timing {#3-ipo-race}

**What happened:** The 2026-05-22 thread tracked OpenAI's confidential S-1 "as early as today." The fact pattern **inverted**: **Anthropic filed first** at **~$965B** (the week of June 1); **OpenAI followed on 2026-06-08** at **~$852B**, with **Goldman Sachs and Morgan Stanley**. Altman then **walked back the timeline**: *"We have not decided on timing yet; it may be a while because there are things we want to do that are likely easier as a private company."*

- **Anthropic:** **$965B confidential filing** — first; valuation exceeds OpenAI's private mark.
- **OpenAI:** **2026-06-08 confidential S-1** at **~$852B**, targeting (per prior reporting) September 2026 — *but* timeline now soft.
- **Polymarket:** **OpenAI IPO by 2026-06-30: 0.5%**. **By 2026-12-31: 69.5%**. Mass moved to year-end after Altman's comment.
- **Pipeline:** Bloomberg framing — AI IPO pipeline now ~**$3.6T** including SpaceX, Anthropic, OpenAI.

**Sources:**
- [Bloomberg — OpenAI Joins a Massive AI IPO Pipeline Now Worth $3.6 Trillion](https://www.bloomberg.com/news/articles/2026-06-08/openai-filed-confidentially-for-ipo-as-rivals-race-to-market) `[secondary]`
- [HeyGoTrade — OpenAI Files IPO a Week After Anthropic](https://www.heygotrade.com/en/news/openai-anthropic-ai-ipo-pipeline/) `[secondary]`
- [CBS News — Claude maker Anthropic files for IPO](https://www.cbsnews.com/news/anthropic-ipo-confidential-filing-claude-ai/) `[secondary]`
- [NBC News — OpenAI files for IPO as AI investment race intensifies](https://www.nbcnews.com/business/markets/openai-chatgpt-files-ipo-rcna349101) `[secondary]`
- [Crypto Briefing — OpenAI files confidential IPO, market eyes December 2026](https://cryptobriefing.com/openai-files-confidential-ipo-market-eyes-december-2026-for-public-debut/) `[secondary]`
- [AI Weekly — OpenAI Files Confidential IPO Targeting $850B Valuation](https://aiweekly.co/alerts/openai-files-confidential-ipo-targeting-850b-valuation) `[aggregator]`
- [Polymarket — OpenAI IPO by…?](https://polymarket.com/event/openai-ipo-by) `[primary]`

### Why it matters to you

- **Job lens:** Two things just got more legible. **(1)** Anthropic's valuation cleared OpenAI's — the highest-resolution evidence yet that the talent market's read on Anthropic (Karpathy [2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy), FDE buildout) is *priced*. Your `ME.md` Anthropic-first stake is now backed by cap-table consensus. **(2)** Altman's "may be a while" softens the equity-liquidity story at OpenAI specifically — if you're choosing between offers in Q4, **expected time-to-liquidity is now shorter at Anthropic.**
- **Startup lens:** The **filing-order inversion** is a meaningful re-rating. Anthropic-aligned theses (MCP servers, evals, customer-eng tooling, on-platform applications) are about to get easier to fund. Conversely, anything depending on *OpenAI's distribution moat* should be stress-tested against Altman's "no hurry" signal.
- **Insight:** The market's wisdom in two numbers: **0.5% (Jun 30) vs 69.5% (Dec 31)**. Aim to have all four `ME.md` portfolio artifacts shipped by **October 1**.

→ Cross-link: [`01` §4 SpaceX IPO as the price-discovery instrument](./01-big-lab-moves.md#4-spacex-ipo) · [2026-05-22/01 §2 original OpenAI S-1 thread](../2026-05-22/01-big-lab-moves.md#2-openai-s1) · [`05` §2 timing your artifact ship-by date](./05-career-and-startup.md#2-shipping-bar).

---

## 4. SpaceX IPO — pricing tomorrow at $135/share for $1.75T (largest in market history) {#4-spacex-ipo}

**What's happening:** **SpaceX prices its IPO tomorrow (Thu Jun 11, 2026)** at a **fixed $135 per share**, selling **555.6M shares** for a **~$75B raise** at an **implied $1.75–1.77T valuation** — *the largest IPO in market history.* Trades **Friday Jun 12** on **NASDAQ as "SPCX."**

- **Underwriters:** Goldman Sachs (lead) + Morgan Stanley + Bank of America + Citigroup + JPMorgan Chase.
- **Greenshoe:** option to sell an additional **83.33M shares** at the IPO price (+$11.2B).
- **Control:** Musk retains **>82% voting control** after the offering.
- **Why it matters here:** SpaceX is the **compute counterparty** for both Anthropic ($1.25B/mo through 2029) and Google ($920M/mo, Oct 2026–Jun 2029). Tomorrow it becomes a publicly traded equity, which means **its compute contracts become publicly observable revenue lines** and the public market will *price* the lab-compute relationship in real time.

**Sources:**
- [CNBC — SpaceX targets fixed $135 IPO price for roadshow](https://www.cnbc.com/2026/06/03/spacex-ipo-stock-price-roadshow-musk.html) `[secondary]`
- [CNBC — SpaceX (SPCX) IPO: Live updates](https://www.cnbc.com/2026/05/20/spacex-ipo-live-updates.html) `[secondary]`
- [TradingKey — SpaceX IPO Date Set for June 12 at a $1.75 Trillion Valuation](https://www.tradingkey.com/analysis/stocks/us-stocks/261904604-spacex-ipo-spcx-date-set-for-june-12-175-trillion-valuation-tradingkey) `[analysis]`
- [Zacks — SpaceX IPO 2026 Guide: Price Predictions, Dates](https://www.zacks.com/featured-articles/741/spacex-ipo) `[analysis]`
- [BitMEX Blog — SpaceX IPO Guide: S-1 Breakdown, Valuation & Trading Strategy](https://www.bitmex.com/blog/spacex-ipo-guide) `[analysis]`
- [WEEX — SpaceX IPO Prediction 2026: $135 Price, $1.75T Valuation](https://www.weex.com/wiki/article/spacex-ipo-prediction-2026-date-135-price-175-trillion-valuation-and-what-spcx-could-do-next-tx6dzuavdmj2s2ihl9aig8xo) `[analysis]`

### Why it matters to you

- **Job lens:** SpaceX going public makes **AI-infra-adjacent comp** legible. The pre-IPO Crusoe / GridCARE / Sphere AI lane in your `ME.md` *reach* set just gained a **public-market comp**: every AI-infra startup will now reference SPCX as the price anchor. If you have any AI-infrastructure leaning, this is the moment to apply — *the comp print just got printed.*
- **Startup lens:** Two effects. **(a)** The biggest IPO in history *clears* the public-market path for the AI-IPO pipeline behind it (Anthropic and OpenAI both filed; the demand signal from SPCX tells everyone whether the demand is there). **(b)** Once SPCX is public, **the compute counterparty's earnings calls become AI-lab leading indicators** — you'll know how much capacity is contracted, utilized, and reserved before the labs themselves report. Build any market-research tooling that joins **SPCX 10-Q / 10-K compute revenue lines** with **lab API usage data** — that's a real data product.
- **Insight:** This is the *macro print* of the year. It either confirms or unwinds the entire "AI as a public-market asset class" thesis Anthropic and OpenAI are betting on by filing. **Watch first-day close (Fri Jun 12) carefully** — a SPCX that opens at $135 and closes at $150+ green-lights September Anthropic/OpenAI windows; a flat or red close *delays everything* and changes your time-to-liquidity calc on every Q4 offer you might receive.

→ Cross-link: [`01` §3 Anthropic + OpenAI IPO comp](./01-big-lab-moves.md#3-ipo-race) · [2026-06-09/00 the 96-hour stack](../2026-06-09/00-tldr.md).
