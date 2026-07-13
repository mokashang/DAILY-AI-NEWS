# Big Lab Moves — 2026-07-03

Anthropic's day. **Three shipped products in 48 hours** — the **Claude apps gateway** for Amazon Bedrock and Google Cloud (SSO + spend caps + failover), **Claude Science** (an AI workbench for scientists), and a **rate-limit + Artifacts-in-Claude-Code bump** — plus a **new public "constitution"** clarifying Claude's values. Read together, this is the enterprise counter-punch to yesterday's [Karp/Uber/Lindy token-billing revolt](../2026-07-02/01-big-lab-moves.md#5-token-attack): give the CFO controls, give the researcher a workbench, give the CISO an SSO gateway. Meta Compute is Day 3 and still moving; GPT-5.6 has no fresh material.

Tags: `#labs #anthropic #meta #openai #enterprise #policy #science`

---

## 1. Anthropic ships the Claude apps gateway for Amazon Bedrock + Google Cloud — SSO, spend caps, failover in one control plane {#1-gateway}

**What happened:** Anthropic published the **Claude apps gateway** — a **self-hosted control plane** for Claude Code (and other Claude apps) on **Amazon Bedrock, Google Cloud, and the Claude API**. It runs as a **single stateless container on Linux** backed by **PostgreSQL**, holds the upstream cloud credential, authenticates developers against your **corporate identity provider (SSO)**, distributes managed settings, and reports **per-user usage** to a collector you operate. Key primitives shipped in the first version:

- **Routing + failover** — one gateway routes to Claude API, Bedrock, or Vertex; automatic failover between providers on outages or classifier flags (integrates with the [Fable 5 → Opus 4.8 fallback](../2026-07-01/01-big-lab-moves.md#2-fable-return) pattern).
- **Spend caps** — daily / weekly / monthly limits, applied per **organization, group, or user**.
- **Data privacy** — no inference traffic or usage data leaves your VPC unless you explicitly point at Anthropic's hosted API.
- **Open protocol** — Anthropic published the gateway protocol so third parties (Databricks, Snowflake, LiteLLM, portkey) can ship compatible implementations.

Before this: running Claude Code on Bedrock/Vertex required **per-developer cloud credentials**, manual `settings.json` distribution, and separate BI tooling for cost attribution — the exact friction that made big-co rollouts stall.

**Sources:**
- [Anthropic — Introducing the Claude apps gateway](https://claude.com/blog/introducing-the-claude-apps-gateway) `[primary]`
- [Claude Code docs — apps gateway](https://code.claude.com/docs/en/claude-apps-gateway) `[primary]`
- [Google Cloud Blog — Claude apps gateway for Google Cloud](https://cloud.google.com/blog/topics/developers-practitioners/announcing-claude-apps-gateway-for-google-cloud) `[primary]`
- [DevOps.com — SSO + spend caps for Bedrock/Google Cloud](https://devops.com/anthropic-adds-enterprise-gateway-to-simplify-claude-code-access-on-aws-and-google-cloud/) `[secondary]`
- [Clauding — protocol walk-through](https://clauding.de/en/posts/claude-apps-gateway-bedrock-google-cloud) `[analysis]`

### Why it matters to you

- **Job lens:** This is the single most **FDE-shaped feature** Anthropic has shipped in 2026. Every Fortune-1000 buyer that stalled on "we can't ship Claude Code without SSO + per-seat cost caps" just got their objection removed — and someone at each of those buyers has to **deploy the gateway container, wire the IdP, define the spend policy, and prove per-user attribution to Finance**. That someone is an FDE / Solutions Engineer / AI Integration Engineer. **Deploy the gateway on a personal AWS/GCP account this weekend** (see [`03` §1](./03-practical-skills-and-tools.md#1-gateway-deploy)) and you have a legitimate FDE-interview demo.
- **Startup lens:** The **open gateway protocol** creates a new opening for "the Datadog / Vanta / Vercel of AI-cost governance" — third-party control planes on top of Anthropic's protocol with UX/analytics that ship faster than a first-party dashboard. Two levels up from a wrapper: you sell **spend-attribution + policy-as-code**, not tokens. This is a legitimate S27/W27 YC wedge; see [STARTUPS.md](../STARTUPS.md).
- **Insight:** The **direct counter to yesterday's token-billing revolt** ([2026-07-02/01 §5](../2026-07-02/01-big-lab-moves.md#5-token-attack)). Karp's argument — "the token model is completely wrong" — implicitly assumes the CFO has no controls. This ships the controls. Watch whether Anthropic (a) deprecates the "unlimited-plan overage anxiety" pitch and (b) uses the gateway to introduce **outcome-priced product lines** in Q3 (batch-of-workflows SKUs vs. token buckets).

→ Cross-link: [`03` §1 the deploy walk-through](./03-practical-skills-and-tools.md#1-gateway-deploy) · [`05` §1 the FDE surge this creates](./05-career-and-startup.md#1-fde-surge) · [2026-07-02/01 §5 token-billing revolt](../2026-07-02/01-big-lab-moves.md#5-token-attack).

---

## 2. Claude Science ships — AI workbench for researchers + $30K credit-grant deadline now T-12 days {#2-claude-science}

**What happened:** Anthropic released **Claude Science** — a **beta desktop app on macOS + Linux** for Pro / Max / Team / Enterprise plans, aimed at researchers. It bundles the tooling scientists actually use (Jupyter, papers, code, chem/bio libraries) into a single workbench that produces **auditable, reproducible artifacts**:

- **Native rendering** of 3D protein structures, genome browser tracks, chemical structures, plots.
- **Every figure ships with** the exact code + environment that produced it, a plain-language description, and the full message history — so a reviewer or a future-you can validate + reproduce months later.
- **Team plan for academic labs** with discounted seats.
- Anthropic will fund **up to 50 AI-for-Science projects** with **up to $30K in Claude credits each**; **applications close July 15, 2026** — biology/biomedical priority.

The launch anchors the John-Jumper-team narrative from [2026-07-02/01 §6](../2026-07-02/01-big-lab-moves.md#6-anthropic-science): Anthropic is standing up a formal vertical in science.

**Sources:**
- [Anthropic — Claude Science, an AI workbench](https://www.anthropic.com/news/claude-science-ai-workbench) `[primary]`
- [TNW — Claude Science launch coverage](https://thenextweb.com/news/anthropic-claude-science-ai-workbench-scientists) `[secondary]`
- [The New Stack — hands-on look](https://thenewstack.io/anthropic-claude-science-workbench/) `[analysis]`
- [pharmaphorum — pharma-researcher angle](https://pharmaphorum.com/news/anthropic-launches-claude-science-pharma-researchers) `[secondary]`

### Why it matters to you

- **Job lens:** The **AI-for-Science vertical** is Anthropic's newest hiring lane and (per Jumper's team ramp) will have **less-crowded** FDE / research-engineer reqs than Claude Code / Solutions through Q4. **Any wet-lab, bio, chem, physics, or numerical-methods background from your CS coursework is a wedge** — pair it with a small Claude Science project this weekend (build one reproducible figure end-to-end).
- **Startup lens:** The **$30K credit grant + July 15 deadline is a real on-ramp**. Practical shape: pick one narrow, stepwise-verifiable science workflow (protein-mutation triage, retrosynthesis QC, single-cell RNA-seq gating) and propose an agent that produces the auditable artifact Claude Science already renders. Pair with the [SciAgentArena](../2026-06-28/04-research-progress.md) stepwise-validator framing. **T-12 days; block Saturday afternoon.**
- **Insight:** "Auditable artifacts" is the meta-theme of Anthropic's week — Claude Science produces reproducible figures; the [gateway](#1-gateway) produces reproducible cost attribution; the [new constitution](#4-constitution) produces auditable behavior specs. The **reproducibility/auditability wedge** is Anthropic's differentiation vs. OpenAI's [GPT-5.6 preview](../2026-07-02/01-big-lab-moves.md#3-gpt56) speed narrative. Interview lens: talk about *artifacts your agent produced*, not *prompts you wrote*.

→ Cross-link: [`04` §1 the survey of agent benchmarks](./04-research-progress.md#1-agent-eval-survey) · [`05` §1 FDE surge](./05-career-and-startup.md#1-fde-surge) · [2026-06-28/04 SciAgentArena stepwise-validator pattern](../2026-06-28/04-research-progress.md).

---

## 3. Claude Platform rate limits up + Artifacts inside Claude Code on Pro/Max {#3-limits-artifacts}

**What happened:** Two smaller ships, but they compound with §1 into a "we heard you" week for enterprise:

- **Claude Platform rate limits raised** across Chat / Cowork / Claude Code / API. Simplified tiers no longer keyed to API spend; **5× higher limits for the latest Sonnet + Haiku on the top tier**. On the API, **Tier 1 saw a 1500% increase in max input tokens/min and 900% for output** on Opus.
- **Artifacts inside Claude Code on Pro + Max** — Claude Code can now build, publish, and **update private interactive pages** (PR walkthroughs, dashboards, mini-dashboards) *while it continues coding*. Effectively, "your coding agent can spin up a private status page for the run."
- Carried: **Claude Code weekly limits raised 50% through July 13** (Anthropic's anti-Codex bump).

**Sources:**
- [Anthropic — Claude Code Artifacts + rate limits](https://releasebot.io/updates/anthropic) `[aggregator]` (release-notes tracker)
- [Appwrite blog — Claude Code 5-hour limits doubled](https://appwrite.io/blog/post/anthropic-doubles-claude-code-rate-limits) `[secondary]`
- [Northflank — 2026 rate-limit + pricing map](https://northflank.com/blog/claude-rate-limits-claude-code-pricing-cost) `[analysis]`

### Why it matters to you

- **Job lens:** Interactive Artifacts inside Claude Code is a **real interview demo** — build a long-running agent that publishes a **live status Artifact** as it works (test runs green, files touched, cost meter). One weekend project = a portfolio piece that also demonstrates the [dual-model orchestration cost pattern](../2026-05-22/03-practical-skills-and-tools.md) from earlier editions.
- **Startup lens:** "Coding-agent → status Artifact" is a **primitive**, not a product. But it repositions all the *observability-for-agents* wedges in [`02`](./02-new-emerging.md) around a fact: the labs are shipping the "what is the agent doing right now" surface themselves. Third-party dashboards need to sell **fleet-of-agents / cross-project / cost-attribution** views the first-party surface won't ship first.
- **Insight:** Rate-limit upgrades near a big competitor release ([GPT-5.6 preview](../2026-07-02/01-big-lab-moves.md#3-gpt56)) are a **standing pattern** — Anthropic doubled limits before Google I/O in May, again before Codex in June, again this week. Read it as a leading indicator that Anthropic's inference capacity is not the bottleneck it was in Q1.

→ Cross-link: [`03` §2 Artifacts-in-Claude-Code recipe](./03-practical-skills-and-tools.md#2-artifacts-recipe).

---

## 4. Anthropic publishes a new "constitution" for Claude — auditable values doc, framing for the UN Geneva dialogue July 6 {#4-constitution}

**What happened:** Anthropic published a **new public document called the "constitution"** — a detailed description of the values, tradeoffs, and behavior Claude is trained toward. It replaces the older, terser policy language. Timing: **three days before the UN Global Dialogue on AI Governance opens in Geneva (July 6)**, where member states will discuss international approaches to frontier models.

**Sources:**
- [Anthropic — Claude's new constitution](https://www.anthropic.com/news/claude-new-constitution) `[primary]`
- [UN News — Global Dialogue on AI Governance opens July 6](https://news.un.org/en/story/2026/07/1167848) `[primary]`

### Why it matters to you

- **Job lens:** The **AI-policy / safety-engineering** lane is expanding fast — every frontier lab is now hiring "safety engineer / trust & safety analyst" roles tied to policy documents that they can point regulators at. Read the constitution once; you'll be quotable in interviews and in EO/UN-facing writeups.
- **Startup lens:** A published constitution + [gateway spend controls](#1-gateway) + [Claude Science auditable artifacts](#2-claude-science) form Anthropic's **enterprise-legibility trio**. If your startup sells to regulated verticals (financial services, health, gov), align your pitch language to these three artifacts — buyers will recognize it.
- **Insight:** Watch whether other labs publish comparable docs before July 6. If OpenAI does not, expect **member-state pressure at Geneva** to converge on Anthropic's shape as the reference. That is a soft-power move worth naming in your notes.

→ Cross-link: [2026-05-22/01 §1 the postponed EO](../2026-05-22/01-big-lab-moves.md#1-eo-postponed).

---

## 5. Meta Compute — Day 3 dispatch {#5-meta-compute-day3}

**What happened:** Yesterday's [2026-07-02/01 §2](../2026-07-02/01-big-lab-moves.md#2-meta-compute) covered the announcement. Day 3 updates:

- **META remains up** on the report; sell-side coverage is moving to "Meta Compute vs CoreWeave/Nebius/Together AI on GPU-hour price" — i.e., commodity framing already.
- Forbes' John Werner has a piece framing this as an **industry-structural move**: excess-capacity monetization is no longer an accident but a formal hyperscaler category.
- No formal SLA or pricing sheet from Meta yet; the reveal-to-first-customer window is where sell-side analysts expect to see actual sticker prices.

**Sources:**
- [Forbes — Meta makes cloud play](https://www.forbes.com/sites/johnwerner/2026/07/02/meta-makes-cloud-play-to-sell-excess-ai/) `[analysis]`
- [Tom's Hardware — Meta Compute vs AWS](https://www.tomshardware.com/tech-industry/meta-reportedly-plans-to-rent-out-its-ai-compute) `[secondary]`

### Why it matters to you

- **Job/Startup/Insight:** All carried from [2026-07-02/01 §2](../2026-07-02/01-big-lab-moves.md#2-meta-compute) — but pair with [SB Neo](./02-new-emerging.md#1-sb-neo) and [Together AI's raise](./02-new-emerging.md#2-together) below: within a **single week the neocloud / excess-capacity market added two formal entrants and one $800M raise.** That is a **structural repricing of the compute layer** and the loudest MLE/infra hiring signal of Q3.

→ Cross-link: [`02` §1 SB Neo](./02-new-emerging.md#1-sb-neo) · [`02` §2 Together AI $800M](./02-new-emerging.md#2-together).

---

## 6. GPT-5.6 preview — no fresh material {#6-gpt56}

Full context: [2026-07-01/01 §4 GPT-5.6 Sol / Terra / Luna](../2026-07-01/01-big-lab-moves.md#4-gpt-56) and [OpenAI preview post](https://openai.com/index/previewing-gpt-5-6-sol/). **No new deployment, pricing, or partner disclosures today.** Watch (a) whether Terra ($2.50/$15) actually undercuts Sonnet 5's promo pricing (see [2026-07-01/01 §1](../2026-07-01/01-big-lab-moves.md#1-sonnet-5)) once GA, (b) the ~20-partner preview list, and (c) **whether Cerebras 750 tokens/sec ships this month** as promised at preview.

→ Cross-link: [`03` §3 routing table update](./03-practical-skills-and-tools.md#3-routing).
