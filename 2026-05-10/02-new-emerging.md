# New & Emerging — 2026-05-10

New models, startups, tools, funding rounds, paradigm shifts.

---

## 1. Sierra Hits $15B Valuation on $950M Series E — The Customer-Agent Category Has a Clear Winner

**What happened:** Bret Taylor and Clay Bavor's **Sierra closed a $950M Series E on May 4** at a **$15B+ post-money valuation**, up from $10B in the fall. The round was led by **Tiger Global and Google's GV**, with Benchmark, Sequoia, and Greenoaks participating. Sierra's pitch: enterprise-grade conversational AI agents for customer experience, replacing call centers and Tier-1/Tier-2 support teams.

The metrics that justified the round:
- **$150M ARR** (up from $100M in November 2025) — 50% growth in ~3 months
- **Nearly half the Fortune 50** as customers (Prudential, Cigna, Blue Cross Blue Shield, Rocket Mortgage)
- Outcome-based pricing (charged per resolved customer interaction, not per seat)
- ~600 employees, mostly forward-deployed engineers and customer success

This makes Sierra the clearest "category winner" in the **AI customer agent** space, an entire SaaS category they're building on top of (or replacing) Zendesk, Intercom, Genesys, Salesforce Service Cloud.

**Sources:**
- [TechCrunch — Sierra raises $950M as enterprise AI race gets serious](https://techcrunch.com/2026/05/04/sierra-raises-950m-as-the-race-to-own-enterprise-ai-gets-serious/)
- [CNBC — Bret Taylor's Sierra raises nearly $1B](https://www.cnbc.com/2026/05/04/bret-taylor-sierra-fundraise-openai.html)
- [SiliconANGLE — Sierra valued at $15B in $950M round](https://siliconangle.com/2026/05/04/ai-agent-startup-sierra-valued-15b-new-950m-funding-round/)
- [The AI Insider — Sierra to become global standard for AI customer agents](https://theaiinsider.tech/2026/05/05/sierra-secures-950m-at-15b-valuation-to-become-global-standard-for-ai-customer-agents/)
- [Tech Startups — Sierra at $15.8B as demand for AI agents surges](https://techstartups.com/2026/05/04/bret-taylors-ai-startup-sierra-raises-950m-at-15-8b-valuation-as-demand-for-ai-agents-surges/)

**Why it matters to you:**
- **Job lens:** Sierra has ~600 people and is hiring **forward-deployed engineers** at a furious pace. FDE is the highest-leverage AI eng role in 2026: you embed with the customer, design the agent, ship it, measure it, iterate. Pay is FAANG+ levels and you ship to production every week. If you have any customer-facing experience plus eng skills, Sierra/Anthropic/OpenAI's FDE roles are the best-priced jobs in the market. (See: [Sierra Careers](https://sierra.ai/careers))
- **Startup lens:** Sierra owns **Fortune 50 customer agents**. There are 100+ Fortune-1000 companies, 5,000+ mid-market companies, and ~30,000 SMBs that need the same product but can't afford Sierra's enterprise contracts. The wedge is *self-service Sierra-for-the-mid-market* — turnkey customer agent for a $50K/year subscription. Distribution: AppExchange, HubSpot Marketplace, vertical industry communities.
- **Insight:** Sierra is the case study for **"outcome pricing > seat pricing"**. Customers pay per resolved ticket, which scales with usage and aligns Sierra's incentives with customer success. Every AI startup founded today should default to outcome pricing, not seat pricing — it's the right thing for the customer *and* it produces dramatically faster ARR growth (because customers don't ration usage).

---

## 2. Moonshot AI Reaches $20B Valuation on $2B Round — Kimi K2.6 Is Now the #2 LLM on OpenRouter

**What happened:** Beijing-based **Moonshot AI closed a ~$2B funding round on May 7 at a $20B valuation**, led by **Meituan's Long-Z Investments**, with Tsinghua Capital, China Mobile, and CPE Yuanfeng participating. The valuation has gone **$4.3B → $10B → $20B in six months**. ARR crossed $200M in April.

The product behind the run-up: **Kimi K2.6** (released April 20 under a Modified MIT license):
- **1-trillion-parameter MoE**, 32B active parameters per inference
- **262K-token context window**
- **Agent Swarm system** — scales to 300 domain-specialized sub-agents at inference
- Currently the **#2 most-used LLM on OpenRouter** (behind Claude Opus 4.7, ahead of GPT-5.5)
- Open-weights — anyone can self-host

**Sources:**
- [TechCrunch — China's Moonshot raises $2B at $20B as open-source AI demand skyrockets](https://techcrunch.com/2026/05/07/chinas-moonshot-ai-raises-2b-at-20b-valuation-as-demand-for-open-source-ai-skyrockets/)
- [Bloomberg — Kimi maker Moonshot valued at $20B in Meituan-led round](https://www.bloomberg.com/news/articles/2026-05-07/kimi-chatbot-maker-moonshot-ai-valued-at-20-billion-in-meituan-led-round)
- [SiliconANGLE — Open-source AI developer Moonshot raises $2B](https://siliconangle.com/2026/05/07/open-source-ai-developer-moonshot-ai-raises-2b-20b-valuation/)
- [CTOL Digital — Kimi $2B funding paradox](https://www.ctol.digital/news/kimi-moonshot-ai-2b-funding-20b-valuation-paradox/)
- [TechNode — Kimi at $20B+ valuation](https://technode.com/2026/05/07/kimi-reportedly-nears-2-billion-funding-round-at-over-20-billion-valuation/)

**Why it matters to you:**
- **Job lens:** **Open-weight expertise is now a hireable specialty.** Companies that need to self-host (governments, regulated industries, latency-sensitive consumer apps) need engineers who can fine-tune and serve Kimi K2.6, DeepSeek V4, Llama 4, Qwen 3.6 Max. The skill stack: vLLM/SGLang/TensorRT-LLM, LoRA/QLoRA, distributed training across H100/B100/Ascend. There's a 6–12 month window where this skill is undersupplied and overpaid.
- **Startup lens:** **The cost of intelligence is collapsing on the open-weight side.** DeepSeek V4 Pro is 75% off through May 31. Kimi K2.6 is open-weight. Moonshot's per-API revenue is growing fast precisely because cost is so low. **Build your product assuming inference cost trends to $0.** What matters: distribution, workflow, data, brand. Don't build a moat that says "we're cheaper" — that's a race you'll lose to whichever Chinese or open lab releases next month.
- **Insight:** China's open-weight thesis is now *paying off in dollars*. Moonshot's $200M ARR and $20B valuation prove that a permissive license + serious capability + low API price wins users globally. The next 18 months will see at least 2 more Chinese AI labs cross $10B valuation. Strategic implication for the US: **OpenAI and Anthropic now have to defend on capability AND price** — that's hard to do simultaneously.

---

## 3. Scout AI Raises $100M Series A — Defense AI Is Now a Capital-Markets Category

**What happened:** **Scout AI**, a startup building autonomous operating systems for uncrewed military fleets (drones, ground robotics, maritime), closed a **$100M Series A** in early May 2026. The round was led by tier-1 defense-tech VCs (Founders Fund, Lux Capital, and General Catalyst typically lead this category), with strategic LPs from defense primes participating.

Defense AI is now a recognized investment theme alongside agent infrastructure and vertical AI. Other recent moves in the same vein:
- **Anduril** continuing as the public market comp (private $14B valuation as of 2025)
- **Shield AI** raised $200M+ in late 2025 for its Hivemind autonomy stack
- **Anthropic Pentagon services deal** (covered in May 6 edition) — formal classified-cleared track now open

**Sources:**
- [Mean.ceo Blog — AI Startup Funding News May 2026](https://blog.mean.ceo/ai-startup-funding-news-may-2026/)
- [ImFounder — 7 explosive AI updates May 2026](https://imfounder.com/science-tech/ai/ai-updates-may-2026/)
- [CNN Business — Pentagon AI Anthropic deal context](https://www.cnn.com/2026/05/01/tech/pentagon-ai-anthropic)

**Why it matters to you:**
- **Job lens:** Defense-tech AI engineers now make **20–40% above FAANG** at top tier startups, and the work is far more interesting if you can stomach the mission. **Required:** US citizenship + ability to clear at least Secret (preferably TS/SCI). **Big advantage:** robotics, embedded, simulation (Isaac Sim, Unreal), or low-latency inference experience. If you don't have a clearance yet, **start the process now** — it adds 6–18 months but doubles your TAM.
- **Startup lens:** Defense AI is the rare 2026 vertical where the moat compounds rapidly: every contract gives you proprietary mission data, classified network access, and procurement relationships that competitors can't replicate. The downside is brutal sales cycles and binary outcomes. If you're a CS grad without military experience, **co-founder yourself with a former 18-Series, MARSOC, AF cyber, or DoD acquisitions person**. Without the operator, you can't sell. With the operator, you can compound on every program.
- **Insight:** "Defense" is no longer one category — it's bifurcating into **autonomy** (Anduril, Shield, Scout, Saronic), **AI cyber** (Palantir, Two Six, Hex Security), **decision-support** (BigBear, Vannevar), and **AI for back-office** (Govini, Decisive Point). Each has different buyer dynamics. Pick one before you build.

---

## 4. The 2026 Model Leaderboard — Where Things Actually Stand

Pulling the live data from Artificial Analysis, LMSys Arena, OpenRouter usage, and SWE-Bench Pro:

| Rank | Model | Approx. Intelligence Score | Key Strength | License |
|---|---|---|---|---|
| 1 | **Claude Opus 4.7** | 73 | Long-form reasoning, financial-services agents, code | Closed |
| 2 | **GPT-5.5** | 71 | General reasoning, voice (5.5 + Realtime-2), Codex | Closed |
| 3 | **Gemini 3.1 Pro** | 70 | Multimodal, long-context, Workspace integration | Closed |
| 4 | **Claude Mythos (preview)** | ~74 (cyber-restricted) | Cybersecurity capability — restricted at launch | Closed (gated) |
| 5 | **Meta Muse Spark** | 52 | Open-weight reasoning, multimodal | Open (Llama license) |
| 6 | **DeepSeek V4 Pro** | ~58 | Code, math, reasoning at $0.145/M input | Open (MIT) |
| 7 | **Kimi K2.6** | ~57 | 1T MoE, agent swarm, 262K context | Open (Modified MIT) |
| 8 | **Qwen 3.6 Max** | ~55 | Multilingual, China cloud workloads | Open (Apache) |
| 9 | **Grok 4.3** | ~62 | Math, science, 1M context | Closed |

**Sources:**
- [Artificial Analysis — Muse Spark + Intelligence Index](https://artificialanalysis.ai/articles/muse-spark-everything-you-need-to-know)
- [LLM Stats — AI News May 2026](https://llm-stats.com/ai-news)
- [Spectrum AI Lab — Claude Opus 4.7 vs GPT-5.5 vs Gemini 3.1 Pro vs DeepSeek V4](https://spectrumailab.com/blog/claude-opus-4-7-vs-gpt-5-5-vs-gemini-3-1-pro-vs-deepseek-v4-comparison-2026)
- [BuildFastWithAI — Best AI Models May 2026 Leaderboard](https://www.buildfastwithai.com/blogs/best-ai-models-may-2026-leaderboard)

**Why it matters to you:**
- **Practical lens:** For **production work** in 2026, default to Claude Opus 4.7 (best reasoning + agent reliability) for back-office work, GPT-5.5 for consumer-facing chat, Gemini 3.1 Pro for anything with images/video, and DeepSeek V4 Flash for high-volume / low-margin tasks. For self-hosting, Kimi K2.6 if you have the GPUs (~8× H100), Muse Spark if you need vision.
- **Job lens:** **"I can pick the right model for the workload"** is now an interview question and a hireable skill. Be ready to argue: "for this task I'd use [model] because of [latency/cost/capability/license tradeoff]." Don't say "I just use ChatGPT" — that signals you've never built anything serious.
- **Insight:** **There is no #1 model anymore.** The frontier has fragmented into 6–8 models that are all "good enough" for most tasks, with each leading on a specific dimension. The product question has shifted from *"which model is smartest?"* to *"what's the cheapest model that meets my evaluation bar on my workload?"* — which is a much more grown-up question.

---

## 5. Tool & Product Releases This Week (Worth Noticing)

| Tool | What's new | Why it matters |
|---|---|---|
| **Simon Willison's `llm` 0.32a0** | Major Python LLM library + CLI alpha; new schema for tool definitions | If you build LLM tools at the CLI/scripting layer, this is the cleanest abstraction. Read [the changelog](https://simonwillison.net/2026/May/) |
| **`datasette-llm` 0.1a7** | Datasette plugin lets you configure default options per model (e.g., temperature 0.5 for enrichment) | Production teams shipping AI features to internal users — fastest way to give analysts a queryable LLM endpoint |
| **`n8n-MCP`** | New MCP server for the n8n workflow automation tool | Lets you build n8n workflows from inside Claude Desktop or Cursor by chatting. Huge for non-engineer ops folks |
| **Hugging Face `ml-intern`** | Open-source ML research agent that runs experiments end-to-end | If you're a researcher, this is a credible Codex-for-ML-research alternative; lets you reproduce arXiv papers automatically |
| **PageCrawl MCP** | Lets Claude/Cursor monitor websites for changes | Lets you build a "competitive intel" agent in 30 minutes for any vertical |

**Sources:**
- [Simon Willison's Weblog — May 2026 entries](https://simonwillison.net/2026/May/)
- [AIToolly — n8n-MCP for Claude/Cursor](https://aitoolly.com/ai-news/article/2026-05-06-n8n-mcp-a-new-model-context-protocol-tool-for-building-n8n-workflows-via-claude-desktop-and-cursor)
- [PageCrawl MCP Server Guide](https://pagecrawl.io/blog/mcp-server-monitor-websites-ai-agents-claude-cursor)
- [AgentConn — HuggingFace ml-intern open-source ML research agent](https://agentconn.com/blog/huggingface-ml-intern-open-source-ml-research-agent-2026/)

**Why it matters to you:**
- **Practical lens:** Pick **one** of these tools and ship a project this weekend. The compounding effect of *shipping with new tools weekly* is the single highest-leverage habit for both job-hunt and startup readiness. A portfolio of 12 small projects you actually shipped beats a CS GPA of 4.0 in 2026 hiring.
- **Insight:** The **MCP ecosystem is maturing fast**. There's now an MCP server for almost any tool you'd want to integrate (n8n, Playwright, GitHub, Slack, Linear, Postgres, browsers, websites). The unfair advantage in 2026 is **knowing the MCP catalogue better than your interviewer / customer**. Spend 30 minutes/week skimming new MCP releases.
