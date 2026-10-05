# 02 — New / Emerging — 2026-07-04

New models, tools, protocols, funding rounds, paradigm shifts. What's newly-real in the last 24–72 hours.

---

## 1. MCP goes stateless — 2026-07-28 Release Candidate is out (T-24 days) {#1-mcp-stateless}

**What happened.** The **Model Context Protocol 2026-07-28 spec RC** is published. This is the biggest MCP revision since launch. Headline shift: **the protocol is now stateless at the transport layer** — six SEPs work together to get there, with two extensions layered on top (**Tasks**, **Apps**).

**The six SEPs (breaking changes summary).**
1. **Sessions removed (SEP-2567)** — `Mcp-Session-Id` header + protocol-level session are gone from Streamable HTTP. Any request can land on any server instance. Sticky routing + shared session stores are no longer required at the *protocol* layer.
2. **Required routing headers** — `Mcp-Method` + `Mcp-Name` on every request. Load balancers, gateways, and rate-limiters route on the operation without inspecting the JSON-RPC body.
3. **Caching semantics on list/read** — responses now carry `ttlMs` and `cacheScope`. Clients know exactly how long `tools/list` is fresh + whether it's shareable across users.
4. **Error code normalization (SEP-2164)** — the MCP-custom `-32002` becomes the JSON-RPC standard `-32602 Invalid Params`.
5. **Deprecations** — `Roots`, `Sampling`, `Logging` marked deprecated (existing usage keeps working; move off it).
6. **OAuth 2.1 / OIDC hardening (six SEPs)** — iss-parameter validation per RFC 9207 and other alignment fixes.

**The two extensions.**
- **Tasks extension** — a `tools/call` can return a **task handle**; the client drives it with `tasks/get`, `tasks/update`, `tasks/cancel`. This is the stateless-safe replacement for long-running work that previously leaned on session identity.
- **Apps extension (SEP-1865)** — servers can render **HTML UIs in sandboxed iframes**. Tools declare UI templates; all actions route through JSON-RPC audit/consent paths. First time MCP servers can ship embedded UIs without leaving the protocol's security model.

**Timeline.** RC published now; **spec locks July 28, 2026**. Ten-week window for SDK maintainers and client implementers to validate against real workloads. Beta SDKs are already out.

**Sources.**
- **[primary]** [MCP Blog — The 2026-07-28 MCP Specification Release Candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/)
- **[primary]** [MCP Blog — Beta SDKs for the 2026-07-28 MCP Spec RC](https://blog.modelcontextprotocol.io/posts/sdk-betas-2026-07-28/)
- **[primary]** [MCP Roadmap](https://modelcontextprotocol.io/development/roadmap)
- **[analysis]** [ChatForest — Six Breaking Changes and What Every Production Server Must Do Before July 28](https://chatforest.com/builders-log/mcp-spec-2026-07-28-release-candidate-stateless-breaking-changes-builder-guide/)
- **[analysis]** [Stacktree — MCP 2026-07-28 spec: what changed, what breaks](https://stacktr.ee/blog/mcp-2026-spec-changes)
- **[analysis]** [WorkOS — The biggest MCP spec update ships July 28: agent authentication](https://workos.com/blog/mcp-2026-spec-agent-authentication)
- **[analysis]** [byteiota — MCP Goes Stateless: What the July 28 Spec Breaks](https://byteiota.com/mcp-goes-stateless-july-2026-breaking-changes/)
- **[analysis]** [MCP.Directory — 2026-07-28 Release Candidate Explained](https://mcp.directory/blog/mcp-2026-07-28-release-candidate)

**Why it matters to you.**
- **Job.** MCP-migration engineering is a **credential-cheap, evidence-heavy** skill. The industry has ~24 days to ship stateless-safe servers before the RC locks. Every FDE / integration-engineer / platform team is behind on this. A weekend migration writeup (see [`03` §1](./03-practical-skills-and-tools.md#1-mcp-migration)) is a top-of-funnel-crushing artifact for Applied AI hiring.
- **Startup.** The **Tasks + Apps extensions** create two new startup surfaces. **Tasks** = long-running-agent SaaS (progress tracking, cost accounting, retry semantics) built on the standard instead of proprietary. **Apps** = "shopify for agent tools" — a marketplace of MCP-App servers with pre-built UI. Both are early enough that a solo dev can put a working demo in front of a lead investor in one month.
- **Insight.** Protocol churn = market-mapping. Whoever was already at [Karpathy's `CLAUDE.md` + hooks + subagents](../2026-05-17/03-practical-skills-and-tools.md) has a **26-week head start** on the population that's about to touch MCP for the first time next month. Compounding advantage.

`#mcp #protocol #agents #tasks #apps`

---

## 2. Meituan open-sources LongCat-2.0 — 1.6T MoE, MIT, trained on Chinese chips {#2-longcat}

**What happened.** Meituan open-sourced **LongCat-2.0**, a **1.6-trillion-parameter Mixture-of-Experts** model built for **agentic coding**:
- **License:** MIT (fully commercial-use permissive).
- **Training data:** 30+ trillion tokens.
- **Hardware:** trained **entirely on domestic Chinese silicon** — no Nvidia GPUs claimed anywhere in the pipeline.
- **Performance:** near-frontier on agentic coding benchmarks; **has been leading OpenRouter usage among open-weights models**.
- **Positioning:** an alternative to DeepSeek V4 for the same open-weights routing slot.

**The signal in the timing.** This lands the same 72-hour window as Anthropic's China loophole crackdown ([`01` §1](./01-big-lab-moves.md#1-china-loopholes)). Chinese labs are increasingly *not* dependent on frontier-lab API access to remain productive. The Anthropic AUP wall becomes leverage against **only US-based downstream customers** — Chinese users have a legitimate MIT-licensed alternative today.

**Sources.**
- **[primary]** [Meituan LongCat-AI (Hugging Face)](https://huggingface.co/meituan-longcat) — weights + config
- **[secondary]** [VentureBeat — Meituan open sources LongCat-2.0, 1.6T near-frontier agentic coding model, leads OpenRouter](https://venturebeat.com/technology/meituan-open-sources-longcat-2-0-the-1-6t-near-frontier-agentic-coding-model-thats-been-leading-openrouter-trained-entirely-on-chinese-chips)
- **[secondary]** [SiliconANGLE — China's Meituan open-sources LongCat-2.0, trained on domestic chips (Jun 30)](https://siliconangle.com/2026/06/30/chinas-meituan-open-sources-massive-longcat-2-0-ai-model-saying-trained-domestic-chips/)
- **[analysis]** [Cryptopolitan — Meituan open-sources 1.6T LongCat-2.0 trained on Chinese chips](https://www.cryptopolitan.com/meituan-longcat-2-0-ai-model-chinese-chips/)
- **[analysis]** [Geopolitechs — LongCat-2.0: China's Most Unexpected AI Model](https://www.geopolitechs.org/p/longcat-20-chinas-most-unexpected)
- **[aggregator]** [ThunderCompute — Best Open Source LLMs (July 2026)](https://www.thundercompute.com/blog/best-open-source-llms)

**Why it matters to you.**
- **Job.** If you're applying to companies with **China-adjacent go-to-market** (Cursor, Cognition, Together AI, Fireworks) or **compliance-oriented** teams (Anthropic policy / Databricks governance / any bank), being fluent in "what an MIT-licensed 1.6T MoE trained without Nvidia means for our product surface" is a real interview question this month. Prepare a 60-second version.
- **Startup.** **The open-weights routing slot is now a moat problem for closed-model startups.** If you're building on Sonnet 5 or GPT-5.5 as your only backend, you're pricing yourself out of workloads where LongCat-2.0 is 80% as good at 5% of the cost. The routing-config discipline from [2026-07-03/03 §3](../2026-07-03/03-practical-skills-and-tools.md#3-routing) with a 5th slot (`open-weights: LongCat-2.0` via Together AI or Baseten) is the update.
- **Insight.** The **"trained on domestic chips"** claim is the political story, but the **agentic-coding target is the technical story.** LongCat isn't chasing MMLU — it's chasing what Sonnet 5 + Claude Code own. That's a direct commercial threat, not a research one.

`#open-source #china #agents #coding #routing #longcat`

---

## 3. Grok 4.5 in private beta at SpaceX & Tesla — 1.5T V9 base + Cursor coding data {#3-grok-45}

**What happened.** Elon Musk announced on **June 28** (freshly relevant this weekend) that **Grok 4.5 has entered private beta at SpaceX and Tesla** — the first deployment ahead of any wider release.
- **Base:** xAI's **V9 foundation model** (1.5T params); training finished May 26.
- **Supplemental data:** **Cursor coding-environment sessions** — first time xAI has publicly acknowledged a code-focused post-training corpus.
- **Musk's benchmark claim:** near or above Claude Opus. **No system card. No independent benchmarks.**
- **Cadence claim:** Musk says xAI will release "**models completely trained from scratch through SpaceX every month**" for the rest of the year — read this as marketing, but note the *shape* is more frequent releases than the Anthropic/OpenAI cadence.

**Sources.**
- **[secondary]** [TechTimes — Grok 4.5 Enters Private Beta at SpaceX and Tesla: No Public Access, No Independent Benchmark (Jun 29)](https://www.techtimes.com/articles/319314/20260629/grok-45-enters-private-beta-spacex-tesla-no-public-access-no-independent-benchmark.htm)
- **[analysis]** [explainX — Grok 4.5 Private Beta at SpaceX/Tesla + Cursor V9](https://www.explainx.ai/blog/grok-4-5-private-beta-spacex-tesla-cursor-v9-2026)
- **[analysis]** [DigitalApplied — Grok 4.5: SpaceX's 1.5T V9 Model Trained on Cursor](https://www.digitalapplied.com/blog/grok-4-5-cursor-data-flywheel-spacex-private-beta-2026)
- **[secondary]** [Hans India — Grok 4.5 enters private testing at SpaceX, Tesla](https://www.thehansindia.com/amp/tech/grok-45-enters-private-testing-at-spacex-tesla-elon-musk-1091457)
- **[secondary]** [Free Press Journal — Grok 4.5 Enters Private Beta at SpaceX & Tesla](https://www.freepressjournal.in/tech/grok-45-enters-private-beta-at-spacex-tesla-as-xai-signals-faster-ai-rollout-cycle-with-15t-model)
- **[aggregator]** [Times of AI — xAI Launches Grok 4.5 Private Beta](https://www.timesofai.com/news/xai-launches-grok-4-5-private-beta/)

**Why it matters to you.**
- **Job.** If you're targeting xAI or Musk-orbit companies, the deployment loop **inside SpaceX/Tesla is the FDE hiring signal** — they need integration engineers who can operate under the rocket + auto safety constraints, not just chatbot QA. Different lane, different comp band.
- **Startup.** Cursor's role as **the coding-data flywheel supplier** is a startup lesson. If you're building any developer-tooling product, the data flowing through your users is now an explicit training corpus for a frontier lab. Model that in your pricing / terms.
- **Insight.** Without a system card or independent benchmarks, "close to Opus" is a **marketing claim**, not data. But the *cadence* claim — monthly models — is worth taking seriously as a competitive move against Anthropic + OpenAI's ~quarterly rhythm. Whether xAI can actually sustain it is the real signal.

`#xai #grok #private-beta #cursor #coding`

---

## 4. Funding pulse — the H1 2026 close, and what's flowing next {#4-funding-pulse}

**What happened.** Two headline numbers to anchor Q3 planning:
- **Global VC funding H1 2026: ~$510B** (Crunchbase) — surpasses all of 2025 ($440B). Second consecutive record quarter after Q1 hit **$300B** ([carried thread from 2026-05-19](../2026-05-19/02-new-emerging.md)).
- **OpenAI + Anthropic alone: $217B / 43%** of that H1 total. The broader AI stack (frontier labs + infra + apps + tooling) is **~65–70% of H1 VC**.

**Fresh late-June / early-July rounds worth flagging:**
- **TwelveLabs** — **$100M Series B** led by NEA (Jul 1). Video-understanding models.
- **RunPod** — **$100M Series A** (Jun 25). Rental-GPU marketplace.
- **General Intuition** — **$320M Series A** led by Khosla (Jun 25). AI-agent operating platform.

**Sources.**
- **[analysis]** [Crunchbase News — Global Startup Investment Hit Record $510B In H1 2026](https://news.crunchbase.com/venture/global-startup-exits-ipo-ma-soar-ai-q2-h1-2026/)
- **[analysis]** [Crunchbase News — Q1 2026 Shatters Venture Funding Records As AI Boom Pushes Startup Investment To $300B](https://news.crunchbase.com/venture/record-breaking-funding-ai-global-q1-2026/)
- **[analysis]** [Qubit Capital — AI Startup Funding Trends 2026](https://qubit.capital/blog/ai-startup-fundraising-trends)
- **[aggregator]** [AIFundingTracker — Latest Funding News](https://aifundingtracker.com/ai-startup-funding-news-today/)
- **[aggregator]** [Fundup AI — Recently Funded Startups Jul 2026](https://fundup.ai/recently-funded-startups)

**Why it matters to you.**
- **Job.** Median AI-startup Series A now $50M+; Series B ~$143M. That means **Series-A/B startups now have runway to hire aggressively** — traditional "we can afford one senior in Q3" thinking is outdated for AI. Widen your target list to include earlier-stage companies you'd previously discount.
- **Startup.** The macro tells you what money is willing to fund — and the specific rounds ([TwelveLabs](https://twelvelabs.io/), [General Intuition](https://www.generalintuition.com/), [RunPod](https://runpod.io/)) tell you which *shapes* are winning. Two patterns: (1) **agentic-OS layer** (General Intuition, [Sierra 950M/$15B on 05-19](../2026-05-19/02-new-emerging.md)), (2) **compute-tier arbitrage** (RunPod, [Together 800M/$8.3B on 07-03](../2026-07-03/02-new-emerging.md#2-together)). Your wedge should live inside one.
- **Insight.** When two companies (OpenAI + Anthropic) absorb 43% of H1 global VC, the rest of the market is **starved of frontier-lab-tier compute and talent** — which is exactly why LongCat-2.0 (§2 above) and Meta Compute (07-01) exist. The commoditization of the *floor* is the pattern of the next 12 months.

`#funding #vc #q3 #twelvelabs #generalintuition #runpod #ai-index`

---

## Cross-refs

- [2026-07-03/02 §1 SB Neo (SoftBank 10 GW)](../2026-07-03/02-new-emerging.md#1-sb-neo)
- [2026-07-03/02 §2 Together AI $800M / $8.3B](../2026-07-03/02-new-emerging.md#2-together)
- [2026-07-03/02 §3 Cloudflare Search/Agent/Training Sept 15 defaults](../2026-07-03/02-new-emerging.md#3-cloudflare)
- [2026-07-02/01 §2 Meta Compute stand-up](../2026-07-02/01-big-lab-moves.md#2-meta-compute)
- [2026-05-19/02 Q1 2026 venture data, $300B / 80% AI](../2026-05-19/02-new-emerging.md)
