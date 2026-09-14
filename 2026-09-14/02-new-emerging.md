# New & Emerging — 2026-09-14

The barbell held but the fat end got fatter. **Cognition's $2B+ at $48B** is the largest coding-agent round of 2026 and reprices the entire agent-native-tooling layer upward. Underneath: **Positron's $875M** revives the inference-silicon-against-NVIDIA thesis, **Forus's $150M at $3B** confirms that vertical AI with a transaction loop is where "measurable business results" money is flowing, and **MCP** graduated from dev tooling into pro-creative (**DaVinci Resolve 21.1**) and release-notes (**ReleasePad**) — the action layer has gone vertical.

Tags: `#funding #agents #cognition #coding-agents #hardware #inference #vertical-ai #healthcare #mcp #creative-tools`

---

## 1. Cognition $2B+ Series E at $48B — Devin's ARR jumped $492M → ~$900M in four months {#1-cognition-48b}

**What happened:** On Sept 8, Cognition AI (maker of the autonomous coding agent **Devin**) closed a **Series E north of $2B at a $48B post-money.** Co-led by new investors **Andreessen Horowitz + Accel**, with **Founders Fund, General Catalyst, and Avenir** following on. **NVIDIA joined as both investor and customer.** Run-rate revenue jumped from **$492M** (at the May round) to **~$900M** — an **~83% jump in four months.** Devin is now embedded inside **NVIDIA, GE Aerospace, Citi, Mercedes-Benz, and Modal.**

This is:
- The **largest coding-agent round of 2026** (edges out the [May 2026 Sierra $950M at $15B](../2026-05-19/) by valuation and by category).
- Confirmation that **coding-agent-as-a-service** is the fastest-compounding revenue vertical in AI (~$408M ARR added in ~4 months).
- The single strongest data point that the [Devin narrative from 2024 was correct](https://cognition.ai/blog/introducing-devin), and that the [Sept 3 GPT-6 Astra launch](../2026-09-10/) did *not* meaningfully cannibalize the coding-agent-startup layer — a scenario many investors feared.

**Sources:**
- [Unite.AI — Cognition Raises Over $2B Series E at $48B Valuation to Scale Devin Agents](https://www.unite.ai/cognition-raises-over-2b-series-e-at-48b-valuation-to-scale-devin-agents/) `[secondary]`
- [Dealroom — Cognition raises $2B Series E at $48B valuation to scale Devin](https://dealroom.co/news/149496-cognition-raises-2b-series-e-at-48b-valuation-to-scale-devin/) `[analysis]`
- [FourWeekMBA — Cognition Devin Series E $48B, NVIDIA dual role](https://fourweekmba.com/ai-cognition-devin-series-e-48b-valuation-nvidia/) `[analysis]`

### Why it matters to you

- **Job lens:** Cognition just gave itself **runway to hire ~500 engineers over the next 18 months** at Series-E burn. **Devin-adjacent roles** (Applied AI, Solutions Engineering, Forward Deployed) become one of the highest-signal application targets on the market — Cognition is famously talent-selective but the funnel widens post-round. Adjacent bets: **Cursor, Codeium, Zed, Replit, Vercel v0** — every direct competitor now has to raise or ship to justify their existing valuation.
- **Startup lens:** Cognition at $48B / ~$900M ARR = **~53× ARR multiple.** That's the *price anchor* for the whole layer. Wedges to consider:
  1. **The coding-agent QA layer** — "we run 200 Devin PRs / day and 12% break your tests; we tell you which 12% before the merge." Sold to Cognition's enterprise customers.
  2. **Coding-agent observability** — cost, latency, tool-use logs, prompt drift. Nobody has the Datadog of Devin.
  3. **Coding-agent evals-as-a-service** — private Terminal-Bench-Science / SWE-Bench Verified over your codebase, refreshed weekly.
  4. **Vertical-specific coding agents** — Devin for infra migrations, Devin for legacy Java, Devin for compliance-critical fintech code. Cognition can't be everywhere.
- **Insight:** NVIDIA showing up as **investor + customer** is the M&A tell of the year. NVIDIA-invested + NVIDIA-customer = NVIDIA has both a strategic option *and* first-look economics on the acquisition. If NVIDIA does buy Cognition (say, ahead of a Cognition IPO in 2027–2028), the multiple will re-anchor the whole AI-tooling M&A market. Track it.

→ Cross-link: [2026-05-19/02 Sierra $950M @ $15B](../2026-05-19/) · [`05` §3 FDE hiring +1,000% YoY](./05-career-and-startup.md#3-fde-hiring).

---

## 2. Positron AI $875M at $5B for memory-first inference silicon {#2-positron}

**What happened:** Reno-based **Positron** announced on Sept 10 a **two-tranche raise totaling $875M at a $5B pre-money valuation**:

- **$375M Series C at $3.5B pre-money** — co-led by **NEA, Atreides, Valor Equity Partners, Andra Capital, and SemiAnalysis Capital.**
- **$500M Series C-1** — anchored by NEA and **Netscape co-founder Jim Clark** (his largest post-Netscape hardware bet).

Proceeds fund:
- The **"Asimov"** inference chip — **288 GB to 2.3 TB LPDDR5X per die**, TSMC N3P tape-out end-2026.
- The **"Titan"** rack-level system — aimed at **16-trillion-parameter models and 10-million-token contexts** at inference time.

**Sources:**
- [PR Newswire — Positron AI raises $875M at a $5B valuation](https://www.prnewswire.com/news-releases/positron-ai-raises-875-million-at-a-5-billion-valuation-to-bring-its-next-generation-inference-silicon-to-market-302874601.html) `[primary]`
- [SiliconANGLE — Chipmaker Positron nabs $875M to speed up inference with consumer-grade memory](https://siliconangle.com/2026/09/10/chipmaker-positron-nabs-875m-to-speed-up-inference-with-consumer-grade-memory/) `[secondary]`
- [Implicator.ai — Positron raises $875M at $5B before Asimov chip tape-out](https://www.implicator.ai/positron-raises-875-million-at-5-billion-before-its-asimov-chip-tapes-out/) `[analysis]`

### Why it matters to you

- **Job lens:** Positron just gave itself ~24 months of hiring runway. **ML-systems engineers + HPC-adjacent CS grads** get a genuinely differentiated career path (vs. becoming NVIDIA hire #40,000). Roles to watch: **inference compiler engineer, LPDDR memory subsystem, PCIe / CXL fabric, cluster-scheduling for inference at scale.** These are the roles that pay in RSU appreciation if Positron ships Asimov on time.
- **Startup lens:** Memory-bound inference is the **new geometry.** If Positron's 288 GB–2.3 TB per die spec ships, the "how big is your context window" ceiling stops being an NVIDIA-fleet-scaling problem and starts being a chip-selection problem. That opens two adjacent startup wedges:
  1. **Inference-cost brokerage** — a router that maps each prompt to the cheapest-per-1M-tokens chip family, given SLA + memory footprint. (Adjacent to [`03` §1 the router artifact](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) from Sept 10.)
  2. **10M-context-native applications** — full-codebase understanding, multi-year enterprise document memory, video-generation-at-full-length-in-context. Startups that were forced to hack RAG can now consider straightforward in-context inference again.
- **Insight:** The **inference-silicon second wind** is real. Groq, Cerebras, Etched, Positron, and the rumored **XDOF Series B at $1.2B** (8VC-led, surfaced Sept 4) all signal VC belief that NVIDIA's inference moat is thinner than its training moat. If **two** of these five ship on time and hit their perf claims, NVIDIA's inference-only revenue line gets its first real disclosure pressure in the [Vera Rubin cycle](./01-big-lab-moves.md#4-nvidia-ssi).

→ Cross-link: [`01` §4 NVIDIA + SSI](./01-big-lab-moves.md#4-nvidia-ssi) · [2026-09-10/03 router artifact](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact).

---

## 3. Forus $150M Series C at $3B — vertical healthcare AI tripled in 4 months {#3-forus}

**What happened:** Vertical healthcare-AI startup **Forus** announced on Sept 8 a **$150M Series C at a $3B post-money valuation** — a **~3× valuation jump in four months** from its Series B. Led by **Bain Capital Ventures**, with **Thrive, General Catalyst, Accel, Redpoint, BoxGroup, Pear VC, Vast Ventures, SV Angel** all participating. Product: **AI agents that connect doctors, pharmacies, payers, and biopharma** to accelerate patients through insurance coverage, financial assistance, and prescription dispensing.

**Sources:**
- [Bloomberg — AI Health Company Forus Raises $150M at $3B Valuation](https://www.bloomberg.com/news/articles/2026-09-08/ai-health-company-forus-raises-150-million-at-a-3-billion-value) `[secondary]`
- [Fierce Healthcare — Forus secures $150M Series C at $3B](https://www.fiercehealthcare.com/health-tech/forus-secures-150m-series-c-3b-valuation) `[secondary]`
- [MedCity News — Forus reaches $3B valuation](https://medcitynews.com/2026/09/forus-secures-150m-series-c-reaches-3b-valuation/) `[secondary]`

### Why it matters to you

- **Job lens:** Healthcare-AI startups **hire CS grads at a premium** because compliance-adjacent engineering is rare. Forus + Nabla + Abridge + Ambience + Innovaccer are now all in the "big enough to onboard new grads" tier. If you have any interest in health-tech, **regulatory-adjacent AI engineering** (HIPAA, prior authorization automation, evidence-of-benefit computation) is a genuinely underpriced lane — pays MLE numbers with less LeetCode ceremony.
- **Startup lens:** Forus is the clearest **"AI agent with a transaction loop"** proof point of the quarter. The pattern:
  1. **Transaction I/O** — the agent doesn't just draft, it *transacts* with insurers and pharmacies. Revenue is percentage-of-transaction, not seat-based.
  2. **Regulated-industry moat** — HIPAA + payer contracts + FDA-adjacent workflows are 12-month buys but 5-year lock-ins.
  3. **Vertical data flywheel** — every processed prescription refines the agent's negotiation policy against payers.
  
  Copy this pattern for founder wedges in **legal transactions (contracts + case filings), compliance transactions (SOX / SOC / ISO evidence generation), and B2B sales-op transactions (quote-to-cash).**
- **Insight:** The Forus round is the first that reads as **"AI-native replacement of a broker + admin + biller stack"** at premium multiple. Note the shape: no consumer-facing brand, no marketplace, no wide moat around any single model — the moat is **workflow integration + regulated-transaction volume.** For a CS grad who *doesn't* want to compete on model quality, workflow-integration + regulated-transaction is where the return curve compounds fastest.

→ Cross-link: [2026-05-13/01 Anthropic Claude for Legal](../2026-05-13/) · [`05` §5 vertical AI hiring](./05-career-and-startup.md#5-verticals).

---

## 4. MCP goes vertical: DaVinci Resolve 21.1 native MCP + ReleasePad MCP {#4-mcp-verticalizes}

**What happened:** Two MCP milestones bracketed the week:

**Sept 8 — DaVinci Resolve 21.1 with a native MCP server inside Resolve Studio.** Blackmagic Design shipped the update; Claude, ChatGPT, and Codex can now drive **multicam edits, markers, audio, transcripts, and renders** directly via the editor's scripting API. **First major professional creative tool to ship MCP natively.**

**Sept 14 — ReleasePad launched an OAuth-based MCP server** letting coding agents **draft, publish, and measure release notes from a chat.** Combined with **Docusign's MCP GA on Sept 30** (announced Sept 4), MCP is quickly becoming the **default action layer for vertical SaaS.**

**Sources:**
- [explainx.ai — DaVinci Resolve 21.1 MCP server for AI agents](https://explainx.ai/blog/davinci-resolve-21-1-mcp-server-ai-agents-2026) `[analysis]`
- [Tech Startups — ReleasePad Launches MCP Server for release notes](https://techstartups.com/2026/09/14/releasepad-launches-mcp-server-so-ai-agents-can-draft-publish-and-measure-product-changelogs/) `[secondary]`

### Why it matters to you

- **Job lens:** MCP-server engineering just got a wider TAM. Every vertical-SaaS company with an API is now an MCP-server-implementation project. The role is often called "**Platform Engineer**" or "**Ecosystem Engineer**" — and it maps almost exactly to the FDE profile ([`05` §3](./05-career-and-startup.md#3-fde-hiring)). If you build **one MCP server for a real product this weekend** and put it in your GitHub, you have a portfolio piece that reads as senior on every application ahead of the [Sept 30 Docusign GA](https://docusign.com/) inbox rush.
- **Startup lens:** The action-layer wedge just widened from *"build an agent for a vertical SaaS"* to *"build the MCP server + evals + observability for a vertical SaaS."* Notably: MCP servers built for the top 20 SaaS TAMs by revenue (Salesforce, HubSpot, Workday, ServiceNow, Snowflake, Databricks, etc.) are startup-scale opportunities. Blackmagic-style native adoption + Docusign-style official OAuth server are the two go-to-market patterns; you want to be the "shadow" MCP-server-of-record for vendors who haven't shipped their own yet.
- **Insight:** MCP-in-DaVinci is the story people will point back to. Creative tools were the last holdout for AI-as-copilot vs. AI-as-agent; if editors can drive a timeline directly, the same pattern will replicate to Figma, Ableton, Blender, Fusion 360 within 12 months. The **"agent has hands, not just words"** era just cleared its most conservative industry hurdle.

→ Cross-link: [2026-05-20/01 WebMCP + Chrome origin trial](../2026-05-20/) · [`03` §4 MCP HTTP+SSE fallback](./03-practical-skills-and-tools.md#4-mcp-fallback).
