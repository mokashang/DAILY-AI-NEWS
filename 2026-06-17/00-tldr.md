# TL;DR — 2026-06-17 (Wednesday)

Sixty-second skim. **Three compounding threads peak today: G7 Évian Day 3 — *the working lunch is today* (set-piece readout this evening). Day 6 of Fable 5 / Mythos 5 dark (Polymarket / Octagon still pricing ~85% restored by July 1, ~5% by June 20). Day 3 of Agent SDK metering — early credit-pool depletion data starts publishing.** Two big signals layered on top: **the June Ramp AI Index landed — Anthropic 41% vs OpenAI flat** (Anthropic is now the most-adopted AI model in US enterprise) and **Claude Managed Agents shipped self-hosted sandboxes + MCP tunnels in public beta** — the production-grade pattern that *makes the Fable 5 governance crisis solvable for enterprises*. For you: **today's G7 readout sets the next 6 weeks of US-AI policy tone; the Ramp number validates the [ME.md focusing decision](../ME.md) harder than it has been validated yet; the sandbox + tunnel primitive is the single highest-leverage portfolio artifact you can ship tonight.**

---

1. **G7 Évian Day 3 — working lunch TODAY.** Altman / Amodei / Hassabis at the head-of-state table; 19-strong wider AI delegation (Mistral, Cohere, Black Forest Labs, Sarvam, Synthesia, Sakana, Meta-Wang, Salesforce). Watch the **communiqué AI section + the post-lunch readout** for (a) export-control language (Fable 5 directly relevant), (b) sovereignty-of-compute language (NewCore/Hydra Host wave), (c) synthetic-DNA/bio-threats — the only *unified* ask. → [`01` §3 EO 14365 framing carries directly into the lunch posture](./01-big-lab-moves.md#3-eo-signed) `#g7 #policy #sovereign-ai #biosecurity`

2. **Fable 5 / Mythos 5 — Day 6 dark.** Anthropic still positions the [June 12 Commerce/BIS directive](./01-big-lab-moves.md#1-fable-suspension) as a "misunderstanding" (capability "widely available from other models including GPT-5.5"). **Prediction-market state**: ~85% restored by July 1, ~50% by June 30, ~5% by June 20. **June 22 cliff still lands regardless** — when Fable 5 returns it exits Pro/Max/Team/Enterprise bundles on June 23 and moves into the metered pool at **$10/$50 per MTok**. Two cost shocks in 5 days. Opus 4.8 / Sonnet 4.6 / Haiku 4.5 remain unaffected fallbacks. → [`01` §1](./01-big-lab-moves.md#1-fable-suspension) `#anthropic #export-controls #policy #fable5`

3. **Agent SDK metering — Day 3.** First public reports of (a) ~10–20% silent-failure rate from skipped credit-pool toggle (the [2026-06-15 step-1 checklist](../2026-06-15/03-practical-skills-and-tools.md) catch), (b) Zed/Cursor/Cline/Aider vendor patches rolling out, (c) **realized 12×–175× effective price increases** per workload class in the first 48-hour bills. The cost-router skill is now load-bearing for anyone shipping agent workloads. → [`03` §2](./03-practical-skills-and-tools.md#2-cost-router) · [`03` §3](./03-practical-skills-and-tools.md#3-claude-code-updates) `#metering #agent-sdk #cost #claude-code`

4. **Ramp June AI Index landed: Anthropic 41% · OpenAI flat (~32%).** Anthropic is **now the most-adopted AI model in US enterprise** — quadrupled in 12 months while OpenAI grew **0.3%**. With Fable 5 currently dark and Opus 4.8 absorbing the load, this is a *Opus-4.8-is-enough* signal as much as a *Claude-is-winning* signal. → [`05` §1](./05-career-and-startup.md#1-ramp-validates) `#anthropic #ramp #enterprise #adoption`

5. **Self-hosted sandboxes + MCP tunnels in public beta.** Claude Managed Agents now run with **orchestration on Anthropic + tool execution on your infrastructure** (own host or Cloudflare / Daytona / Modal / Vercel). MCP tunnels in research preview. **This is the production-grade enterprise primitive** — and the Fable 5 suspension is the live proof case. Set up tonight; the README becomes your FDE-interview ticket. → [`03` §1](./03-practical-skills-and-tools.md#1-self-hosted-sandboxes) `#mcp #managed-agents #self-hosted #governance`

6. **GPT-5.6 launch nears — Fable 5 head-to-head deferred.** Chief scientist: "a meaningful leap." Benchmarks to watch: **Terminal-Bench 2.0** (5.5 = 82.7%) · **FrontierMath T4** (5.5 = 35.4%) · **SWE-bench Verified** (Fable 5 set the 95.0% bar that's currently *technically held by a model nobody can run*). OpenAI ships ~every 7 weeks. → [`02` §3](./02-new-emerging.md#3-gpt-56) `#openai #gpt-56`

7. **MCP ecosystem hit production scale.** 9,652 registered servers · 28,959 server/version records · 15,926 GitHub repos · **41% of orgs in limited-or-broad production** (Stacklok). **Spec 2026-07-28 RC** ships stateless core + Apps (server-rendered UIs) + Tasks (long-running) + OAuth/OIDC. → [`02` §1](./02-new-emerging.md#1-mcp-ecosystem) · [`04` §3](./04-research-progress.md#3-mcp-data) `#mcp #standards #ecosystem`

8. **Research: the externalization taxonomy.** arXiv **2604.08224 — "Externalization in LLM Agents: A Unified Review of Memory, Skills, Protocols and Harness Engineering"** = the 4-layer vocabulary that lets you talk about agent systems unambiguously. Pair with **arXiv 2604.27859 (Rethinking Agentic RL)** + **Astra-Bench** (tool use + personal-user context). Read the taxonomy this week — it's the new interview scaffold. → [`04` §1](./04-research-progress.md#1-externalization-survey) `#arxiv #benchmarks #agents`

---

## One thing to DO this Wednesday

→ **Stand up the self-hosted-sandbox + private-MCP demo on your own infrastructure tonight** ([`03` §1](./03-practical-skills-and-tools.md#1-self-hosted-sandboxes)). Public beta is open. The README — name-checking Fable 5 governance, the EO 14365 clearinghouse, and Ramp-41% as demand signal — becomes **your single best FDE / AI-Integration-Engineer artifact for the rest of the summer**. One artifact answers three interview questions (managed-agents fluency · MCP server authorship · governance-aware design). Pair with the **G7 readout watch** at end-of-day: track the communiqué section on AI for any language that *names* export controls or sovereignty — those are tomorrow's career headlines.

## Watchlist deltas

- ➡️ **G7 Évian Day 3:** working-lunch readout today. Watch communiqué AI section for export-control / sovereignty / biosecurity language.
- ➡️ **Fable 5 / Mythos 5 export-control suspension:** Day 6. No change in restoration probability; still ~85% by July 1, ~5% by June 20. June 22 cliff still lands regardless.
- ➡️ **Agent SDK metering:** Day 3 — first public credit-pool depletion reports surfacing. The dual-model / Opus-orchestrator-Sonnet-worker pattern is the lever.
- 🆕 **Self-hosted sandboxes + MCP tunnels public beta:** new thread — H2 2026's must-ship enterprise primitive.
- 🆕 **Ramp June Anthropic 41%:** new thread — track whether the lead widens (currently testing Opus-4.8-only without Fable 5) or compresses if ChatGPT Ads Manager dents adoption.
- 🆕 **GPT-5.6 launch window:** imminent. Refresh the Gemini-vs-Claude-vs-GPT comparison page within 48h of GA.
- ➡️ **SEC quiet windows (Anthropic Day-16 / OpenAI Day-9):** product cadence at both labs likely decelerating through July.
- ➡️ **June 22 Fable 5 subscription cliff:** T-5 days.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This + [`01` §1 Fable 5 Day 6 framing](./01-big-lab-moves.md#1-fable-suspension) + the §3 EO context for today's G7 lunch |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) — the whole lab–state–market triangle reads as one story |
| Tonight | [`03` §1](./03-practical-skills-and-tools.md#1-self-hosted-sandboxes) — set up the self-hosted-sandbox demo |
| End of day | The G7 working-lunch readout — set a 6 PM CET / 9 AM PT reminder |
| This week | [`05` §2](./05-career-and-startup.md#2-eo-lane-live) — the pre-deployment-eval lane is live on EO 14365's 30-day clock |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
