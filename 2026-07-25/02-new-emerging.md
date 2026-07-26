# New & Emerging — 2026-07-25

If [`01`](./01-big-lab-moves.md) was the frontier consolidating, this file is where the *capital* went instead. Three funding rounds worth watching this week: **Etched at $10.3B** (transformer-specialty ASICs — a real challenger to Nvidia inference margins), **Cathedral at $1.4B** (DOGE alumni + a16z + Sequoia = defense-cyber AI as a category), and **Humanoid at $1.35B** (Europe's first humanoid unicorn). Plus **MCP's 2026-07-28 stateless spec** finalizes Monday — the biggest platform-migration deadline of the summer for anyone shipping MCP servers. And Anthropic's **Economic Index connector + $200M Economic Futures Research Fund** made "we take labor displacement seriously" the lab's official public positioning.

Tags: `#funding #ai-chips #defense #robotics #mcp #stateless #anthropic #economic-index #adoption #ramp`

---

## 1. Etched raises $300M Series C at $10.3B — Sequoia's highest-valuation Series C on record {#1-etched}

**What happened:** On **2026-07-23**, transformer-specialty ASIC startup **Etched** (founded 2022, three Harvard dropouts — CEO Gavin Uberti) closed **$300M Series C at $10.3B post-money**.

- **Sequoia led**; a16z, SK hynix, Jane Street, Diffusion Capital joined.
- **Valuation ~2× in 7 months** (was $5B on a $500M raise in Dec 2025).
- **$1B in inference-chip orders** on the books; first Sohu silicon manufactured last month; first full systems in customer testing.
- Bet: **transformer-only ASICs (Sohu)** at inference vs. Nvidia's general-purpose GPUs.
- Reportedly the **highest-valuation Series C Sequoia has ever led**.

**Sources:**
- [MarketScale — Etched closes $300M Series C at $10.3B, orders hit $1B](https://www.marketscale.com/industries/software-and-technology/etched-closes-300m-series-c-at-103b-valuation-doubling-in-seven-months-as-inference-chip-orders-hit-1b) `[primary]`
- [TechCrunch — AI chip startup Etched defies skeptics, hits $10.3B](https://techcrunch.com/2026/07/23/ai-chip-startup-etched-defies-skeptics-hits-10-3b-valuation-from-big-name-investors/) `[secondary]`
- [MLQ.ai — Etched Raises $300M Series C at $10.3B](https://mlq.ai/news/etched-raises-300m-series-c-at-103b-valuation-to-scale-gpu-free-inference-chips/) `[analysis]`

### Why it matters to you

- **Job lens:** Inference-specific silicon is a **real venture category now**, not a science project. Comp for **kernel / compiler / model-hardware co-design engineers** at Etched, Tenstorrent, Groq, Cerebras is climbing fast. If you have any low-level ML systems background — CUDA, Triton, MLIR, PyTorch internals — the queue at these companies is roughly 100× thinner than at Anthropic/OpenAI, and the equity story is arguably better because these are pre-IPO.
- **Startup lens:** If Sohu ships at claimed throughput, **Anthropic-stack inference economics change** — a startup targeting Claude-latency/cost workloads should be *actively modeling* non-Nvidia deployment paths for 2027. Also: the **inference-optimization layer** on top of custom silicon (batching, speculative decoding, KV-cache mgmt) is a fundable adjacent wedge, and it composes with your MCP-server skills.
- **Insight:** OpenAI's [$750B capex](./01-big-lab-moves.md#2-openai-750b) and Etched's $10.3B are two sides of the same seam. The frontier labs are betting that **the answer is more scale** (own the utility); Etched is betting that **the answer is more specialization** (change the hardware assumption). Both bets can win — but they imply very different operating environments in 2028. Watch which one Anthropic quietly aligns with in its Q4 capacity announcements.

---

## 2. Cathedral (DOGE alumni) — $160M at $1.4B for military-cyber AI {#2-cathedral}

**What happened:** On **2026-07-22**, **Cathedral** — a stealth startup founded by four ex-**Department of Government Efficiency** staffers (Gavin Kliger, Luke Farritor, Marko Elez, Jack Stein) — raised **$160M at $1.4B post-money**, **co-led by a16z and Sequoia** (both took board seats).

- Building AI tools for **offensive and defensive cyber**, targeted at DoD contracts, framed as China counter-threat.
- **Kliger was previously chief data officer at the Pentagon** — involved in the DoD's legal fight with Anthropic over military use of Claude.
- Fits inside the a16z "American Dynamism" thesis that is now consensus (Anduril, Palantir, Shield AI, Scale gov'l units all in the same lane).

**Sources:**
- [ExecutiveBiz — Military Cyber Startup Cathedral Raises $160M](https://www.executivebiz.com/articles/cathedral-doge-cyber-startup-160m-funding-1-4b-valuation) `[primary]`
- [citybiz — a16z, Sequoia Lead $160M for DOGE Staff Venture](https://www.citybiz.co/article/878111/andreessen-horowitz-sequoia-capital-lead-160m-round-for-former-doge-staffs-venture/) `[secondary]`
- [TNW — Cathedral: DOGE alumni military cyber startup at $1.4B](https://thenextweb.com/news/cathedral-doge-alumni-military-cyber-startup-1-4-billion) `[analysis]`

### Why it matters to you

- **Job lens:** Defense / government AI is being underwritten at **unicorn valuations pre-revenue** and paying comparable to frontier labs, with a **much thinner applicant queue** — most CS grads self-select out. If you're OK with clearance work, the ROI is favorable. Concrete near-term targets: Anduril, Palantir, Shield AI, Scale AI (gov'l), and — for the willing-and-adjacent — Cathedral itself once they open reqs.
- **Startup lens:** The **Kliger-vs-Anthropic history** is worth reading between the lines. It implies a growing class of **"no-guardrails-for-USG"** competitors positioned explicitly against the labs' usage policies. If you're building on the Claude API and your customer base includes gov'l, understand what the alternative frontier stack looks like — you may end up either partnering with or competing against Cathedral-shaped incumbents.
- **Insight:** When a **stealth pre-product startup** with an obvious talent story clears $1.4B at seed-like maturity, VCs are pricing in **policy tailwind + a China threat narrative** that is not going to reverse in this administration. Every wedge downstream (secure evals, model-red-teaming, on-prem inference for classified data, defense-fit MCP servers) inherits that tailwind for at least 24 months.

---

## 3. Humanoid raises $152M Series A at $1.35B — Europe's first humanoid unicorn {#3-humanoid}

**What happened:** On **2026-07-21**, UK-based **Humanoid (SKL Robotics Ltd.)** closed **$152M Series A at $1.35B post-money** — the largest-ever Series A for a humanoid-first robotics company in Europe.

- **Prime Movers Lab led**; **Schaeffler, Bosch, Fubon Financial Holding VC, Aglaé Ventures** participated.
- Funds go to **mass manufacturing of wheel-based robots** plus next-gen bipedal work.
- Sits inside a **~$56B robotics funding wave in 2026** (roughly 2× 2025). Reference point: China's AI2 Robotics raised **~$735M at ~$3B** this year.

**Sources:**
- [SiliconANGLE — Humanoid raises $152M at $1.35B](https://siliconangle.com/2026/07/21/humanoid-raises-152m-1-35b-valuation-bring-human-like-robots-factories/) `[primary]`
- [Forbes — Humanoid Raises $152M: Europe's Newest Robot Unicorn](https://www.forbes.com/sites/johnkoetsier/2026/07/21/humanoid-raises-152-million-at-135-billion-valuation-europes-newest-robot-unicorn/) `[secondary]`
- [PYMNTS — Humanoid Raises $152M](https://www.pymnts.com/news/investment-tracker/2026/humanoid-raises-152-million-to-expand-robotics-company/) `[secondary]`

### Why it matters to you

- **Job lens:** **Embodied-agent stacks** (VLA models, sim-to-real, planning, low-level control) are a rapidly-professionalizing job market. Your Anthropic-stack skills transfer more than you might expect — most humanoid companies run **LLM/VLM planners on top of custom control stacks**, and the "high-level planner ↔ low-level controller" seam is a lot like the "planner ↔ worker" seam in Claude Code agent teams. See the Anthropic [Project Pilot / Drone-Bench result](./04-research-progress.md#4-project-pilot) for the exact skill vocabulary.
- **Startup lens:** Bosch and Schaeffler writing checks means **factory-deployment is being underwritten**, not just demos. Wedges to consider: **teleop-to-autonomy data pipelines**, **eval harnesses for embodied agents**, **fleet-management + observability for humanoid deployments**. All three compose with the MCP-server + agent-orchestration skills you already have.
- **Insight:** The **language of "unicorns" understates the concentration** — 2026 robotics funding is going to <20 companies globally, most of them at ≥$1B pre-Series-B. If humanoid works even partially, the market structure will look like frontier LLMs: 3–5 winners, everyone else in adjacency. Pick your bet accordingly if you're founding — or aim for the picks-and-shovels layer.

---

## 4. MCP 2026-07-28 stateless spec finalizes Monday — the summer's biggest migration deadline {#4-mcp-stateless}

**What happened:** The **Model Context Protocol 2026-07-28 release candidate** is live and the spec finalizes **this Monday**. It is the **biggest MCP change since authorization** landed.

- **Stateless protocol core:** the `initialize` handshake and `Mcp-Session-Id` header are **removed** — any request can hit any server instance. MCP servers now deploy **behind a plain round-robin load balancer**, no sticky sessions.
- **Hardened OAuth 2.1** — single Google / GitHub sign-in to connect a server, no JSON config.
- **Three new primitives:** **MCP Apps** (server-rendered UIs inside clients), **Tasks** (long-running work), **Server Cards** (capability discovery at a `.well-known` URL).
- New required headers on requests: `MCP-Protocol-Version`, `Mcp-Method`, `Mcp-Name` (the last two make per-tool routing/rate limits/kill-switches trivial at the edge).
- Client metadata now travels in `_meta` on every request.
- **Back-compat break:** servers on the new revision may not work with old clients; migrate deliberately.
- **Ecosystem context:** MCP has crossed **10,000+ published servers**.
- GitHub already shipped support ahead of the Monday finalization.

**Sources:**
- [MCP Blog — 2026-07-28 Release Candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) `[primary]`
- [The Register — Model Context Protocol prepares to break with its stateful past](https://www.theregister.com/devops/2026/07/23/model-context-protocol-prepares-to-break-with-its-stateful-past/5276722) `[secondary]`
- [GitHub Changelog — GitHub MCP Server supports the next MCP spec (2026-07-23)](https://github.blog/changelog/2026-07-23-github-mcp-server-supports-the-next-mcp-specification/) `[primary]`
- [Digital Applied — MCP Goes Stateless: Migration Guide](https://www.digitalapplied.com/blog/mcp-2026-07-28-spec-stateless-migration-guide) `[secondary]`
- [WorkOS — Everything your team needs to know about MCP in 2026](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) `[analysis]`

### Why it matters to you

- **Job lens:** Stateless + OAuth 2.1 turns MCP servers into **normal web services**. "MCP server engineer" is about to look like "REST API engineer, c. 2015" — an entire job category unlocked. This is directly on your Anthropic-stack career path; you should have **at least one MCP server migrated to the new spec** in your portfolio by mid-August. See [`03` §2](./03-practical-skills-and-tools.md#2-mcp-migration) for the concrete migration steps.
- **Startup lens:** **Server Cards + MCP Apps** open a new distribution channel: you can ship a Claude-integrated product **without shipping a client** — users discover your server capability from `.well-known` and connect via OAuth. Any vertical SaaS with proprietary workflow data should evaluate shipping an MCP surface as a distribution wedge before the incumbents (Zapier, Make, n8n) commoditize it.
- **Insight:** The **back-compat breakage** creates a real **60-day consulting/migration window** — a legitimate freelance revenue lane while you're job-hunting. Add a "migrated N production MCP servers to the 07-28 spec" line to your resume by September and you've turned a spec break into a portfolio artifact.

→ Cross-link: [`03` §2 the exact migration steps](./03-practical-skills-and-tools.md#2-mcp-migration) · [`05` §4 how to convert the migration window into cash / calls](./05-career-and-startup.md#4-migration-window).

---

## 5. Anthropic Economic Index connector + $200M Economic Futures Research Fund {#5-anthropic-economic-index}

**What happened:** On **2026-07-22**, Anthropic released the **Anthropic Economic Index** as a Claude **connector** — any claude.ai user can enable it and query aggregated Claude-usage data about occupations, tasks, and industry trends.

- Same-day: **$200M commitment to the Economic Futures Research Fund** to underwrite external research on AI's labor-market impact.
- Day before (**2026-07-21**): another **$20M donation to Public First Action** (policy advocacy).
- Ambient adoption signal: **Ramp data shows Anthropic at 34.4% of business AI spend vs. OpenAI at 32.3%** — the first month Anthropic leads in enterprise share.

**Sources:**
- [Anthropic — The Anthropic Economic Index connector](https://www.anthropic.com/news/anthropic-economic-index-connector) `[primary]`
- [Anthropic — Economic Futures Research Fund agenda](https://www.anthropic.com/news/economic-futures-research-fund-agenda) `[primary]`
- [MindStudio — Anthropic vs OpenAI Business Adoption 2026: Ramp Data](https://www.mindstudio.ai/blog/anthropic-vs-openai-business-adoption-2026-ramp-data-2) `[analysis]`
- [AI Weekly — Anthropic Details $200M Research Agenda on AI's Labor Impact](https://aiweekly.co/alerts/anthropic-details-200m-research-agenda-on-ais-labor-impact) `[secondary]`

### Why it matters to you

- **Job lens:** Anthropic is publicly positioning as the **"we take labor displacement seriously"** lab. In every Anthropic-anything interview loop (Solutions / FDE / Applied AI / Fellows), being able to reference the Economic Index specifically — and cite one concrete finding from it — is now table-stakes signal. Spend 20 minutes with the connector this weekend and pull a stat you'd actually cite. It's the cheapest "did they read past the headlines" filter you can pass.
- **Startup lens:** **Enterprise share crossing to Anthropic** (Ramp 34.4% vs. 32.3%) means Anthropic-stack expertise is now the **majority-share enterprise skill**, not the minority. Product decisions default to "does this work on Claude" first; a startup that builds Claude-first and adds OpenAI compatibility later is following the market, not swimming against it.
- **Insight:** The $200M research fund + $20M policy check are Anthropic **building the policy environment it wants to inherit** — the same "voluntary framework" energy that produced the (postponed) [Trump EO in May](../2026-05-22/01-big-lab-moves.md#1-eo-postponed). If you're interested in AI policy as a *career* lane, the number of paid roles at Anthropic + funded external researchers is materially growing this quarter.

→ Cross-link: [`05` §1 the Fellows deadline that pairs with this](./05-career-and-startup.md#1-fellows-deadline).
