# New & Emerging — 2026-05-08

New models, startups, tools, and paradigm shifts that just landed on the radar.

---

## 1. DeepSeek V4 — Frontier Performance at 1/10 the Compute Cost (and It Runs on Huawei Ascend)

**What it is:** DeepSeek released **V4 Pro and V4 Flash** on April 24, refined through May 4. Both released under MIT license on Hugging Face.

| Variant | Total Params | Active Params/Token | Context | Notes |
|---|---|---|---|---|
| **V4-Pro** | 1.6T | 49B | 1M tokens | Multimodal, frontier performance |
| **V4-Flash** | 284B | 13B | 1M tokens | Mid-size GPU rigs can serve it |

**The breakthrough — Hybrid Compressed Attention:**
- Combines **Compressed Sparse Attention (CSA)** + **Heavily Compressed Attention (HCA)**
- At 1M tokens, V4-Pro requires only **27% of single-token inference FLOPs** and **10% of KV cache** compared to DeepSeek V3.2
- V4-Flash trained on **32 trillion tokens**

**The geopolitical wrinkle:** Both models are **runnable on Huawei Ascend chips** — meaning Chinese teams can train and serve frontier-grade models without NVIDIA hardware. This is a structural shift in the export-controls game.

**Sources:**
- [Hugging Face — DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)
- [Hugging Face — DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash)
- [Latent Space — DeepSeek V4 Pro and Flash, runnable on Huawei Ascend](https://www.latent.space/p/ainews-deepseek-v4-pro-16t-a49b-and)
- [DataCamp — DeepSeek V4 features and comparisons](https://www.datacamp.com/blog/deepseek-v4)
- [TechCrunch — DeepSeek closes the gap with frontier models](https://techcrunch.com/2026/04/24/deepseek-previews-new-ai-model-that-closes-the-gap-with-frontier-models/)
- [BuildFastWithAI — V4-Pro review](https://www.buildfastwithai.com/blogs/deepseek-v4-pro-review-2026)

**Why it matters to you:**
- **Immediately actionable:** If you're building anything that doesn't *require* the absolute frontier, **DeepSeek V4-Flash on Hugging Face Inference / DeepInfra / Together is dramatically cheaper than GPT-5.5 or Claude Opus 4.7** for comparable quality on most agentic tasks. Migrate non-critical inference workloads and pocket 5–10× cost savings.
- **Startup lens:** Open-weight frontier models change the economics of *any* AI startup. Your unit economics no longer depend on a closed-API gatekeeper. Use this to your advantage — businesses with regulatory or data-residency requirements can self-host V4-Flash on a few H100s and have a defensible product.
- **Insight:** China's open-weight strategy is now a **deliberate counter-positioning** to the closed Western frontier. GLM-5.1, MiniMax M2.7, Kimi K2.6, and DeepSeek V4 all landed at the same capability ceiling within weeks of each other. The next-generation open ecosystem is more likely to be Chinese-trained than Meta-trained — this changes the geopolitics of AI deployment in every non-aligned country.

---

## 2. Pit (Stockholm) — $16M from a16z to Build "AI Product Teams as a Service"

**What happened:** Pit launched out of stealth on May 7 with a **$16 million round led by Andreessen Horowitz**, with participation from Lakestar and individual executives from OpenAI, Anthropic, Google, Deel, and Revolut, plus Sweden's Stena and Lundin families.

**The pitch:** Pit Studio observes how teams work — spreadsheets, emails, SaaS tools, internal workflows — and **automatically builds custom AI-native software** to automate them. Founders are ex-Voi, Klarna, and iZettle. Early customers (Voi, Tre, Stena Recycling, Kry) report deployment timelines of **days to weeks instead of months**.

**Sources:**
- [Bloomberg — a16z funding round for Pit](https://www.bloomberg.com/news/articles/2026-05-07/andreessen-horowitz-in-funding-round-for-swedish-ai-startup-pit)
- [GlobeNewswire — Pit launches with $16M led by a16z](https://www.globenewswire.com/news-release/2026/05/07/3289856/0/en/pit-launches-with-16-million-led-by-andreessen-horowitz-to-bring-ai-native-software-to-enterprise-operations.html)
- [EU-Startups — Pit exits stealth with €13.6M](https://www.eu-startups.com/2026/05/stockholms-pit-exits-stealth-with-e13-6-million-a16z-led-funding-to-offer-ai-product-teams-as-a-service/)
- [Startup Fortune — US capital is still Europe's AI price-setter](https://startupfortune.com/andreessen-horowitz-leads-16-million-into-stockholms-pit-proving-us-capital-is-still-europes-ai-price-setter/)
- [TheNextWeb — Pit launches to build custom AI-native software](https://thenextweb.com/news/pit-16m-launch-andreessen-horowitz-ai-enterprise-operations)

**Why it matters to you:**
- **Startup lens (read this twice):** "AI product team as a service" is the **most important wedge formula of 2026**. Instead of selling a SaaS tool, you sell a service that *generates the SaaS tool* the customer needs. The customer pays once and gets a custom system; you keep the agent harness as IP. This is the closest thing to printing money for a 3-person founding team in this market.
- **Job lens:** If you can build agents that build software, you are the most hireable person in 2026. Skills involved: code-generating agents, MCP servers, evaluation harnesses, deployment automation, customer-discovery instinct. This is *exactly* the skill stack to develop now.
- **Insight:** Note who invested — operators from OpenAI, Anthropic, Google, Deel, Revolut. When operators write personal checks, the thesis is real. When *European* startups raise from a16z at the seed stage, US capital is signaling that AI-native services are the next unicorn factory.

---

## 3. Parallel Web Systems — $230M Total at $2B to Be the "Web Search for AI Agents"

**What happened:** Parallel Web Systems (founded by **Parag Agrawal**, former Twitter CEO) closed a **$100M Series B at $2B valuation** led by Sequoia Capital, with Kleiner Perkins, Index, Khosla, First Round, Spark, Terrain, and Abstract increasing participation. Total raised: **$230M**. The valuation **doubled in 5 months** from their Series A.

**The product:** APIs that give AI agents structured, grounded access to the open web — not text scraping, but a proprietary indexed web optimized for agent consumption. Their bet: agents need their own search infrastructure (different latency, structure, freshness, ranking signals than humans need).

**Sources:**
- [Parallel Web Systems](https://parallel.ai/)
- [TechCrunch — Parallel hits $2B valuation 5 months after last raise](https://techcrunch.com/2026/04/29/parallel-web-systems-hits-2b-valuation-five-months-after-its-last-big-raise/)
- [SiliconANGLE — Parag Agrawal builds parallel web for AI agents](https://siliconangle.com/2026/04/28/parag-agrawals-startup-raises-100m-build-parallel-web-ai-agents/)
- [PR Newswire — Parallel raises at $2B valuation](https://www.prnewswire.com/news-releases/parallel-raises-at-2-billion-valuation-to-scale-web-infrastructure-for-agents-302756350.html)
- [TechFundingNews — Sequoia leads $100M raise](https://techfundingnews.com/parag-agrawal-parallel-100m-series-b-sequoia-ai-agents/)

**Why it matters to you:**
- **Startup lens:** Agents need infrastructure that isn't optimized for human consumption — search, browsers, payments, identity. Each one is potentially a $1B+ company. Parallel = "Google for agents." What's the equivalent for **payments for agents**? **Identity for agents**? **Cron for agents**? **Auth for agents**? Pick a primitive and go.
- **Job lens:** "Agent infrastructure engineer" is a brand-new role. Building the backend (not the agent itself) is increasingly where the high-leverage work is. If your portfolio includes a project that exposes a clean API for agents to consume — bonus points.
- **Insight:** Parallel doubling valuation in 5 months on the *same* infrastructure thesis tells you VC is convinced that **the volume of agent-driven traffic will exceed human traffic on the web within 24 months**. Plan accordingly — your products may be consumed by agents more than humans before 2028.

---

## 4. Chinese Open-Weight Wave: GLM-5.1, MiniMax M2.7, Kimi K2.6, DeepSeek V4

**What happened:** Four Chinese labs (Z.ai, MiniMax, Moonshot, DeepSeek) shipped open-weight models within weeks of each other — all landing at roughly the same capability ceiling on agentic engineering tasks, all at meaningfully lower inference cost than Western frontier models.

| Model | Lab | Notable Property |
|---|---|---|
| **GLM-5.1** | Z.ai (Zhipu) | Strong agent + tool-use performance |
| **MiniMax M2.7** | MiniMax | Multimodal, long context |
| **Kimi K2.6** | Moonshot | Strong long-context reasoning |
| **DeepSeek V4** | DeepSeek | MIT license, runnable on Huawei Ascend |

**Sources:**
- [llm-stats.com — AI news and updates](https://llm-stats.com/ai-news)
- [Hugging Face — Trending models](https://huggingface.co/models?sort=trending)
- [The Decoder — Coverage of Chinese model releases](https://the-decoder.com/)

**Why it matters to you:**
- **Insight:** A year ago, "open weights" meant Llama. Today, the open-weight frontier is dominated by Chinese labs. If you're building anything where data sovereignty matters (EU, India, regulated industries), you can self-host a frontier-grade model with no Western dependency for the first time. This **resets the entire build-vs-buy calculus** for AI startups.

---

## 5. Davis (France) — €4.6M for AI-Generated Architecture (Gaudi-1)

**What happened:** French AI real-estate startup **Davis** raised **€4.6M** and unveiled **Gaudi-1**, a model for automated architectural generation. Gaudi-1 generates floor plans, elevations, and 3D models conditioned on site constraints, regulations, and brief.

**Sources:**
- [EU-Startups — Davis raises €4.6M](https://www.eu-startups.com/2026/05/french-ai-real-estate-startup-davis-raises-e4-6-million-and-unveils-gaudi-1-for-automated-architectural-generation/)

**Why it matters to you:**
- **Startup lens:** Vertical AI in **regulated, slow-moving industries** (architecture, construction, law, healthcare, accounting) is the durable opportunity. The big labs will not ship "generative architectural designer" — but a startup with one architect-cofounder and two engineers can. This is the YC pattern playing out — deep domain expertise + general-purpose foundation models = defensible business.

---

## 6. Watch List — These Are Coming Soon

- **Google I/O 2026** — Android Show May 12, keynotes May 19–20. Expect **Remy** personal agent public unveiling. ([Google I/O 2026](https://io.google/2026/))
- **Meta Hatch** personal agent — internal testing end of June, likely tied to Muse Spark launch
- **Apple's AI strategy** at WWDC 2026 (June) — last major lab without a clear personal-agent story
- **OpenAI Personal Agent** — OpenClaw-team-led product expected H2 2026
