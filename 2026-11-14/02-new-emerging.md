# New & Emerging — 2026-11-14

Split-screen month. At the top of the stack, **foundation-model economics kept breaking records** — Anthropic and OpenAI both marked near $1.25T, fal's $1.65B inference round at $16B. At the application layer, **sales/agent tooling (Rox, Nooks) is consolidating around compound workflows** rather than chatbots. Meta's **Muse Spark Open** finally shipped weights but trails **three Chinese open models** (Kimi K3, GLM 5.3, Qwen 3.8) at coding — the open-weight frontier is now explicitly non-US. For a grad student picking a wedge: **infra is a capital game, agents are a go-to-market game, and the open layer is where you can still build without a billion dollars.**

Tags: `#funding #startups #models #agents #open-source #inference #sales-ai #ipo`

---

## 1. fal raises $1.65B across Series E + F — inference platform at $16B {#1-fal}

**What happened (2026-11-03):** Generative-media inference startup **fal** disclosed a combined **$1.65B across two rounds**, doubling its valuation to **$16B**.
- **Series F:** $1.3B led by **Bessemer Venture Partners** at **$16B**.
- **Series E:** $350M led by **Sequoia** at **$8B**, closed April 2026, disclosed now.
- Other participants: **NVIDIA, Sound Ventures, HOF Capital, T. Rowe Price**.
- Positioning: SF-based inference platform running image/video/audio models for developers; **rate-limited paying customers** over the summer due to demand.

**Sources:**
- [tech.eu — fal doubles valuation to $16B after $1.3B Series F](https://tech.eu/2026/11/04/fal-doubles-valuation-to-16b-after-13b-series-f/) `[secondary]`
- [SiliconANGLE — Generative media inference startup fal raises $1.3B](https://siliconangle.com/2026/11/03/generative-media-inference-startup-fal-raises-1-3b-at-a-16b-valuation/) `[secondary]`
- [Securities.io — fal announces $1.65B combined Series E+F](https://securities.io/fal-announces-1-65-billion-in-combined-series-e-and-f-funding) `[aggregator]`

### Why it matters to you

- **Job lens:** Inference-platform hiring is the clearest MLE/SRE signal right now — fal is paying for **GPU-aware systems engineers, schedulers, model-optimization specialists**, not prompt engineers. Expect similar rounds at **Replicate, Modal, Baseten** to open comparable reqs.
- **Startup lens:** The "arms dealer" wedge is still a $16B category even without training frontier models. There's room for **vertical inference (voice, 3D, music)** — but you need a serious systems team on day one; this is not a prompt-engineering startup.
- **Insight:** **Inference, not training, is where media AI monetizes.** When demand outruns supply (fal literally rate-limited paying customers), capital flows to fund GPUs. Watch who sells GPUs next: this round funded capacity more than R&D.

---

## 2. Rox raises $100M Series B at $1.3B — AI sales agents, 160× ARR multiple {#2-rox}

**What happened (2026-11-11):** Enterprise sales-agent startup **Rox** closed a **$100M Series B at $1.3B**, co-led by **General Catalyst and March Capital**.
- Returning: **Sequoia, Factory**. New: **Databricks Ventures, Prosperity7 Ventures**.
- Product: **AI agents for lead gen, meeting booking, deal management** — direct Salesforce competitor framing.
- Prior: $50M seed + Series A (Nov 2024), with General Catalyst investing pre-product, pre-revenue.
- Use of funds: AI research, custom models, enterprise expansion in **healthcare, industrial, FS, energy, tech**.
- Reported ARR ~$8M → **~160× multiple** on the Series B.

**Sources:**
- [Unite.AI — Rox raises $100M Series B at $1.3B](https://www.unite.ai/rox-raises-100m-series-b-at-1-3b-valuation-to-advance-ai-research/) `[secondary]`
- [ValueAddVC — Rox hits $1.3B valuation](https://valueaddvc.com/pulse/rox-100m-series-b-1-3b-valuation-salesforce-2026) `[analysis]`
- [Dealroom — AI sales startup Rox hits $1.2B / $8M ARR](https://dealroom.co/news/126775-ai-sales-startup-rox-hits-1-2b-valuation-and-8m-arr-with-new-round/) `[aggregator]`

### Why it matters to you

- **Job lens:** $1.3B at ~$8M ARR means Rox is **hiring ahead of revenue** — ML engineers, FDEs, applied-AI PMs. FDE roles at agent companies are now the 2015-equivalent of "ML engineer" title — **ill-defined, high leverage, premium pay**.
- **Startup lens:** Rox validates "AI for every CRM seat" but **raises the ante** — if you attack sales, you need either (a) a sharper vertical wedge than horizontal sales agents or (b) a different go-to-market (SMB/PLG vs. Rox's enterprise motion).
- **Insight:** **Compound agent products (agent + data + workflow) are being valued at ~160× ARR** when enterprise logos are present. The multiple is for the moat (data + integrations), not the model.

---

## 3. Meta ships Muse Spark Open — 816B MoE, trails three Chinese models at coding {#3-muse-spark-open}

**What happened (2026-10-15):** Meta released weights for **Muse Spark Open** — its most capable open-weight model to date.
- Architecture: **816B total / 42B active mixture-of-experts**, **1M-token context**, natively multimodal.
- Availability: Hugging Face + **Amazon SageMaker AI, Google Cloud Model Garden, Microsoft Foundry**.
- License: **"Muse Model License"** (not OSI-approved); requires **"Built with Muse Spark Open"** attribution; bars military + critical-infrastructure uses.
- **Benchmarks:** **76.4 on Terminal-Bench 2.1** — trails **Kimi K3 (85.0), GLM 5.3, and Qwen 3.8** on coding.
- Shares base model with closed Muse Spark 1.3.

**Sources:**
- [Meta Research — Muse Spark Open](https://research.meta.ai/blog/muse-spark-open) `[primary]`
- [Implicator — Muse Spark Open trails Chinese rivals at coding](https://www.implicator.ai/meta-releases-muse-spark-open-an-816b-model-that-trails-chinese-rivals-at-coding/) `[analysis]`
- [The New Stack — Meta Muse Spark Open](https://thenewstack.io/meta-muse-spark-open/) `[secondary]`

### Why it matters to you

- **Job lens:** Open-weight models at this scale redefine the "applied ML" job. If you can **fine-tune, distill, or quantize a 42B-active MoE**, you can clear **$300K+ TC** at any enterprise with regulated data. Build a public eval or distillation repo — it's a portfolio in itself.
- **Startup lens:** The **US open-weight frontier is no longer obviously best** — Kimi K3, GLM 5.3, Qwen 3.8 beat it at coding. A startup can plausibly serve non-US customers with a Chinese open model on their own GPUs, **no API dependency**. That's a **new geopolitical wedge**.
- **Insight:** **"Open weight" is quietly becoming "shared base, split post-training."** Meta's open and closed Muse Spark share a base — the post-training is the moat. Expect this pattern from every lab that claims openness.

---

## 4. Thinking Machines Lab in talks at $40B — down from $50B {#4-thinking-machines}

**What happened (late Oct 2026, The Information):** Mira Murati's **Thinking Machines Lab** is in advanced talks to raise **$1B+ at ~$40B pre-money** — **below an earlier $50B target**.
- Prior: **$2B seed at $12B post** (July 2025) — largest AI seed on record.
- Product footprint so far: **one API, limited product output** since founding.
- NVIDIA eyeing the round.
- **DefiLlama pre-IPO tracker estimated $10.9B secondary valuation** as of Oct 29 — secondary-market skepticism loud.
- No closed round as of today.

**Sources:**
- [AI Weekly — Thinking Machines Lab $40B talks](https://aiweekly.co/alerts/mira-muratis-thinking-machines-lab-in-talks-to-raise-1b-at-40b-pre-money-below) `[rumor]`
- [Crypto Briefing — Thinking Machines Lab $40B valuation](https://cryptobriefing.com/thinking-machines-lab-40b-valuation/) `[secondary]`
- [DefiLlama — Thinking Machines pre-IPO](https://defillama.com/pre-ipo/thinking-machines) `[aggregator]`

### Why it matters to you

- **Job lens:** The "all-star OpenAI alum team + one API" pattern is being **revalued downward**. If you're interviewing at founder-only labs with no public product, use this as a negotiation anchor — **even Murati can't hold $50B without shipping**.
- **Startup lens:** The 25%+ haircut on a hyped frontier lab is the **first crack in the "founder narrative = unlimited valuation" meme**. If you're a researcher-founder, you now need either shipped product or shipped revenue to clear $10B+; the free ride is ending.
- **Insight:** **Secondary markets (DefiLlama, Hiive, Forge) are pricing frontier labs ~75% below primary rounds.** Watch the spread — it predicted Stability AI's unraveling and may predict the next.

---

## 5. Nooks takes $500M non-dilutive from General Catalyst's CVF — revenue-share capital goes mainstream {#5-nooks}

**What happened (2026-11-04):** AI sales startup **Nooks** secured a **$500M growth commitment** from General Catalyst's **Customer Value Fund (CVF)** — structured as **revenue-share, not equity**.
- **Non-dilutive:** funds sales + marketing against predictable unit economics.
- Launched **Revenue Agent Platform + Node** ("first AI personal assistant for sales," deal management focus).
- Reported: **135% NRR**, ARR expected to **triple by year-end**.
- Prior equity: $22M Series A (Apr 2024), $43M Series B led by **Kleiner Perkins** (Oct 2024).

**Sources:**
- [Webull — Nooks Secures $500M, Launches Node](https://www.webull.com/news/15865863830529024) `[secondary]`
- [Finimize — Nooks $500M war chest without giving up equity](https://finimize.com/content/nooks-got-a-500-million-war-chest-without-giving-up-equity) `[analysis]`
- [CityBiz — Nooks Secures $500 Million](https://www.citybiz.co/?p=929354) `[aggregator]`

### Why it matters to you

- **Job lens:** Non-dilutive capital changes hiring math — Nooks can scale GTM **without stock-dilution pressure**, which usually means **bigger cash salaries but smaller equity grants**. If you optimize for cash, agent companies with CVF-style backing are now the **most mercenary offers** in the market.
- **Startup lens:** This is **structural**. CVF/revenue-based financing is becoming VC's answer to "growth is expensive, dilution is painful." If your startup hits predictable unit economics, you can raise 10× ARR **without giving up board seats**. Model it into your pitch deck.
- **Insight:** **"Growth capital" at AI startups is starting to look like Shopify Capital or Clearco** — tied to revenue, not equity. The VC model is bifurcating: equity for 0→1, revenue-share for 1→100.

---

## 6. DeepSeek ships new coding agent — cadence 2× faster than US labs {#6-deepseek-agent}

**What happened (2026-11-01):** **DeepSeek launched an enhanced coding agent**, positioned as a Claude Code alternative.
- Available via API + web interface.
- Early benchmarks reportedly competitive (independent validation still thin).
- Ships alongside **DeepSeek V4.1-Flash-1017**, **#1 trending on Hugging Face** (1,988 likes, week of Oct 13–20).
- Pricing significantly undercuts frontier US coding agents (common DeepSeek pattern).

**Sources:**
- [Emergent — DeepSeek coding agent launches](https://emergent.sh/news/deepseek-coding-agent-launches-challenge) `[secondary]`
- [Firecrawl — DeepSeek V4.1-Flash tops HF trending](https://www.firecrawl.dev/prompts/trending-ai-models) `[aggregator]`
- [Zhihu Frontier Weekly — DeepSeek V4 → Kimi K2.6](https://zhihufrontier.substack.com/p/zhihu-frontier-weeklyfrom-deepseek) `[analysis]`

### Why it matters to you

- **Job lens:** US coding-agent companies (Cursor, Cognition, Replit, Codeium) are now under **real cost pressure**. Expect hiring to shift toward **differentiation** — enterprise sales, codebase-specific RL, repo-level context — rather than pure model/UX work.
- **Startup lens:** If you're building dev tools, **assume a free/open Chinese model equals your closed-API tool within 6 months**. Defensible wedges: workflow lock-in, enterprise integration, or a specialized vertical (SAP, mainframe, embedded).
- **Insight:** **DeepSeek's cadence (V4 April → V4.1 ongoing → coding agent now) is 2× faster than US labs.** For builders, "wait for the Chinese open release" is now a valid product-planning assumption — it's shortening US frontier moats from **quarters to months**.

---

## 7. Anthropic and OpenAI both marked near $1.25T — the IPO window is open {#7-trillion-club}

**What happened (2026-11-06, Bloomberg):** Both Anthropic and OpenAI were marked **near $1.25T** in recent secondary/primary activity.
- Anthropic: filed S-1/A on **2026-11-02**; Polymarket priced an Anthropic listing by Nov 30 at **~76%** (as of Nov 6).
- OpenAI: $1.25T mark reported by Bloomberg Nov 6.
- Prior checkpoints: Anthropic **$965B** in May 2026 after $65B Series H; OpenAI **$852B** following its $122B round earlier in 2026.
- **IPO watch:** Anthropic, OpenAI, and SpaceX all expected to list in the near term.

**Sources:**
- [FourWeekMBA — OpenAI, Anthropic both near $1.25T](https://fourweekmba.com/ai-openai-anthropic-both-near-1-25t-only-one-files-revenue/) `[analysis]`
- [NeuronFeed — Anthropic files for IPO at $965B after Series H](https://neuronfeed.com/news/anthropic-files-for-ipo-at-965-billion-valuation-after-series-h) `[secondary]`
- [Open the Magazine — Anthropic nears $1T, overtakes OpenAI](https://openthemagazine.com/business/anthropic-nears-1-trillion-valuation-overtakes-openai-ahead-of-ipo) `[secondary]`

### Why it matters to you

- **Job lens:** An Anthropic IPO within 30 days means **refresh grants, retention packages, and a liquidity event that will mint hundreds of millionaires** — and a wave of post-IPO departures founding new companies. Watch for **"ex-Anthropic researcher" seed rounds in Q1 2027**, likely the hottest early-stage market of the cycle.
- **Startup lens:** If you want to raise from the Anthropic/OpenAI diaspora, **start conversations now**. Post-vest cliff + IPO = angel checks. Your wedge should be something these researchers themselves can't easily build in a lab — **vertical product, distribution, hardware**.
- **Insight:** The frontier-lab bubble now has a **public-markets ceiling to test**. Whether the $1.25T valuations hold at IPO is the **single most important datapoint for AI capital allocation in 2027**. If Anthropic prices below, **Series B multiples compress across the board within two quarters**.

→ Cross-link: [`01` §1 — Anthropic roadshow timing](./01-big-lab-moves.md#1-anthropic-ipo-roadshow)
