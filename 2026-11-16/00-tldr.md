# TL;DR — 2026-11-16 (Monday)

Sixty-second skim. **This is the single biggest AI market-structure week of 2026: Anthropic IPO prices Wed Nov 18 and begins trading Thu Nov 19 on Nasdaq under ANT (range $70–$78, book 6× oversubscribed, $1.33–$1.41T fully-diluted valuation, $26B concurrent PIPE on top of a $64.4B IPO = ~$90B raise), and NVIDIA prints fiscal Q3 FY27 Tuesday Nov 17 after close — the first full quarter of Vera Rubin shipments.** Together, the two prints re-anchor every AI comp conversation through Q1 2027 and give you a **public lab comp print by Friday morning**. Underneath: **OpenAI quietly shipped ChatGPT Wallet GA (Nov 13) + GPT-6 Luna in-country inference GA in India/Japan/Australia (Nov 10)**; Google DeepMind's **"Gemini 4 Carbon"** is circulating but not on Google's own newsroom (`[rumor]` pending primary); **Apple opened Siri AI to every developer (Nov 3)** with an App Store ship window locked to spring 2027; **Ramp Nov 2026 AI Index shows Anthropic at 60.1% of US business token spend**, median US business AI spend **$15.70/employee/month** (up **2.48× YTD**); **Cognition raised Devin's multi-repo scan cap to 1,000** (enterprise mono/poly-repo in reach); and the **MSFT 60K buyout window closes Dec 1** with likely uptake 3–10× the spokesperson's 3–5% guidance. Research: **memory-for-agents is back at #1 on HF daily trending**, counterweighted by the **AMA-Bench null result** showing long-context + retrieval beating most bolted-on memory architectures. Practical: **Claude Code 2.1.319 adds MCP tasks in terminal + "deny instead of prompt" permission**; **Simon Willison's `llm` 0.37** shipped with new OpenAI-compatible-endpoint config; **MCP 2026-07-28 stateless is now default on Claude.ai**.

---

1. **ANT IPO prices Wed Nov 18, first trade Thu Nov 19.** 825M shares at **$70–$78**, Nasdaq ticker **ANT**, book **6× oversubscribed** by Nov 12 (Reuters/Bloomberg). Fully-diluted valuation **$1.33T → $1.41T**; IPO proceeds up to **$64.4B** + **$26B concurrent PIPE** = **~$90B raise**. **Pre-IPO revenue (9 mo to Sept 30): $33.24B.** Lockup 180 days → employee liquidity ~May 2027 = biggest "ex-Anthropic researcher seed" supply shock of 2027. → [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo-pricing) `#anthropic #ipo #comp`

2. **NVIDIA FY27Q3 earnings Tue Nov 17 after close.** Guide ~**$108B ±2%** (+105.9% YoY); first full Rubin-shipment quarter (~20% of data-center rev mix). AWS **+2M GPUs through FY29**. Watch **Rubin CPX SKU revenue mix** and **HBM pricing commentary** — these are the 2027 inference-pricing-floor numbers. **$500B cumulative Blackwell + Rubin revenue visibility** carries over. → [`01` §2](./01-big-lab-moves.md#2-nvidia-q3-fy27) `#nvidia #earnings #chips`

3. **OpenAI mid-November cluster: ChatGPT Wallet GA (Nov 13) + GPT-6 Luna in-country inference GA India/Japan/Australia (Nov 10).** The **data-residency SKU** that enterprise procurement wanted. Naming trail still messy (locale-first English release notes, "GPT-5.6 vs GPT-6 Cyber" ambiguity). "Businesses in ChatGPT" beta (Nov 10) = SMB workspace layer; expect platform-engineering + commerce-FDE reqs to open. → [`01` §3](./01-big-lab-moves.md#3-openai-mid-nov-cluster) `#openai #wallet #sku`

4. **Gemini 4 Carbon circulating `[rumor]` — DeepMind's strongest frontier model, reported $2/M input / $10/M output.** Not on Google's own newsroom yet; Kavukcuoglu's Sept "ship well before EOY" statement makes mid-Nov plausible. If real, **router/multi-model-arbitrage startups get a new price axis**; cost-aware routing becomes default for any code/sci agent. Gemini 3.5 Pro reportedly cancelled. → [`01` §4](./01-big-lab-moves.md#4-gemini-4-carbon) `#google #gemini #routing`

5. **Apple Siri AI Developer Preview — every dev gets access (iOS 27.3), App Store ship blocked until spring 2027.** Foundation models co-developed with Google; **NVIDIA GPUs** for complex queries. ~$1B/year Apple→Google. New AI head: **Amar Subramanya**. **Fixed-start-gun App Store AI gold rush spring 2027** = the most predictable "I shipped a Siri-AI feature day one" interview story available. → [`01` §5](./01-big-lab-moves.md#5-apple-siri-ai-dev-preview) `#apple #siri #mobile`

6. **Anthropic $26B concurrent PIPE — hyperscaler coupling made permanent.** AWS + Google explicitly carried into the public era. **Every "bring-your-own-cloud" 2027 enterprise negotiation references this precedent.** Antitrust-adjacent regulation of AI-cloud partnerships now the most likely 2027 policy flashpoint. → [`02` §1](./02-new-emerging.md#1-anthropic-pipe) `#anthropic #cloud #antitrust`

7. **Ramp AI Index Nov 2026: Anthropic 60.1% of token spend; median US business AI spend $15.70/emp/mo (up 2.48× YTD); 55.9% adoption.** New **department-level breakdown** released. Grok (SpaceXAI) flat at 2.2%. **Build Anthropic-first, route-for-fallback — "vendor-neutral" is a sales-deck claim your telemetry contradicts.** → [`02` §2](./02-new-emerging.md#2-ramp-nov-2026) `#ramp #spend #anthropic`

8. **Devin multi-repo cap raised to 1,000 (Nov 2) + SSO + budgets (Oct 30) + "log out everywhere" (Nov 6).** Windsurf is now **Devin Desktop**; Cascade EOL'd July 1 → **Devin Local (Rust rewrite)**. Coding-agent platform wars settled into **Claude Code + MCP (practitioner)** vs **Devin (enterprise procurement)**. Cursor + Copilot squeezed. **Pick a camp, use the product daily, don't be neutral.** → [`02` §3](./02-new-emerging.md#3-devin-multi-repo) `#devin #claude-code #coding-agents`

9. **Execution-bottleneck thesis crystallizes: models commoditize, sandbox + agent-desktop is the moat.** Vercel Agent Desktop on GitHub trending; tier-1 sandboxes to know: **E2B, Daytona, Modal Sandboxes, Cloudflare Browser Rendering, Vercel Sandbox, AWS Bedrock Sessions.** One-weekend portfolio artifact: **browser-using agent inside a sandbox, orchestrated by Claude Code, plumbed to one MCP server.** → [`02` §4](./02-new-emerging.md#4-execution-bottleneck) `#sandbox #execution #portfolio`

10. **Practical upgrades this week: (a) Claude Code 2.1.319** adds MCP tasks in terminal + "deny instead of prompt" permission + Apps Gateway controls — mandatory for `/loop`-style auto-mode in CI; (b) **Simon Willison `llm` 0.37** (Nov 2) covers 2 months of fixes, adds `gpt-6.1-sol`/`-terra` + easier OpenAI-compatible-endpoint config (critical for Together/Fireworks pipes); (c) **MCP 2026-07-28 stateless** is now Claude.ai default — any MCP server built before July 2026 needs rewrite/shim; **shipping one MCP server is the #1 portfolio artifact for FDE applications this week**. → [`03`](./03-practical-skills-and-tools.md) `#claude-code #llm #mcp`

11. **Research threads: memory-for-agents (arXiv 2512.13564) back at HF #1; AMA-Bench null result (long-context + retrieval beats bolted-on memory); process-reward shaping for multi-agent systems; AgentDebugX open-source observability.** The citable interview framing: *"In 2027, the stack splits into frontier models (commoditizing) + execution surfaces (sandbox) + control plane (memory, routing, hooks, eval). Jobs and startups compound in the control plane."* → [`04`](./04-research-progress.md) `#arxiv #memory #eval #agents`

12. **MSFT buyout window closes Dec 1 — spokesperson 3–5% uptake vs. April precedent 30% (2,600 of 8,750).** Likely **5,000–18,000 ex-MSFT engineers hit the market Jan 1, 2027**. **Apply ahead of the wave: now through Dec 20** at Glean, Writer, Cresta, Observe.AI, Cohere, Weaviate, Pinecone, LangChain, Modal, Anthropic FDE. Q1 2027 founder bump expected from Azure/AI Platform 5–10 YOE cohort. → [`05` §1](./05-career-and-startup.md#1-microsoft-buyout-countdown) `#msft #buyout #timing`

13. **FDE comp bands crystallize: Palantir new-grad $135–$145K base, Domino $123–$152K, experienced median $173,816, Anthropic FDE $280–$320K base, frontier lab TC $300–$550K.** Glean's $160–$270K is **TC not base** (correcting 2026-11-14's framing). FDE new-grad **beats SWE new-grad median (~$110–$125K)** with shorter interview loops. **~40% of 2025–26 vertical-AI YC founders were FDEs.** Can't get FDE title → aim at "Solutions Engineer — AI" / "Applied AI Engineer" — same job, less competition. → [`05` §2](./05-career-and-startup.md#2-fde-comp-bands) `#fde #comp #newgrad`

14. **The re-price of the week: ANT public float + NVDA Rubin print + MSFT buyout deadline all land in the same 15-day window.** Skills re-pricing *up*: **MCP-server authoring on 2026-07-28 spec, sandbox/execution-layer plumbing, eval design, control-plane primitives (hooks, routing, deny-not-prompt), process-reward shaping.** Re-pricing *down*: raw prompt engineering, "we're vendor-neutral" positioning, "latest model fluency" as a differentiator, horizontal agent-memory pitches without a vertical. → [`05` §3](./05-career-and-startup.md#3-ant-week-thesis) + [`05` §5](./05-career-and-startup.md#5-buyer-psychology) `#reprice #skills #moats`

---

## One thing to DO this Monday night

→ **Rewrite your résumé top section with an FDE lane (60 min) + fire 5 applications before Thu Nov 19.** The FDE top section is three lines: **(1) customer-facing work, (2) prototype velocity (problem → demo), (3) one vertical you understand**. Stack line: *Claude Code 2.1.319, MCP 2026-07-28 servers, Python/TypeScript, {one sandbox: E2B / Vercel Sandbox / Daytona / Modal}*. Then **5 applications in one sitting**: **Glean (Founding FDE), Distyl, Decagon, Sierra, Harvey**. Save **Palantir + OpenAI + Anthropic for the week of Dec 1** — their 8–12-week pipelines will be ANT-week-distracted. Full template + ANT-week comp answer in [`05` §2](./05-career-and-startup.md#2-fde-comp-bands) and [`05` §3](./05-career-and-startup.md#3-ant-week-thesis).

## Watchlist deltas

- ✅ **Anthropic ANT roadshow + Nov 16 pricing window** (from 2026-11-14): **RESOLVED (near)** — pricing **Wed Nov 18**, first trade **Thu Nov 19**, range **$70–$78**, **6× oversubscribed**. New sub-thread: Day 1 price action, above-range pricing scenario, ~May 2027 lockup expiry math.
- 🆕 **NVIDIA FY27Q3 earnings Tue Nov 17** — first full Rubin-shipment quarter; listen for CPX SKU revenue mix + HBM pricing floor.
- 🆕 **Anthropic $26B concurrent PIPE** — hyperscaler coupling made permanent; 2027 "bring-your-own-cloud" negotiations reference this.
- 🆕 **ChatGPT Wallet GA (Nov 13)** — Wallet collapses the affiliate-discovery layer; pivot wedges for discovery-wrapper startups are vertical catalogs or merchant-side infra.
- 🆕 **GPT-6 Luna in-country inference India/Japan/Australia** — data-residency SKU landed; regulated-vertical AI ARPU accelerates.
- 🆕 **Gemini 4 Carbon `[rumor]`** — if real, $2/$10 per M undercuts Fable 5.2 by 4×; router/multi-model-arbitrage startups get a new price axis.
- 🆕 **Apple Siri AI Developer Preview + spring 2027 App Store ship** — predictable fixed-start-gun AI gold rush on iOS.
- 🆕 **Ramp Nov 2026 Index: Anthropic 60.1% of token spend; dept-level dataset new** — token spend still lags volume = prices falling faster than usage.
- 🆕 **Devin 1,000-repo scanning + enterprise procurement** — coding-agent-platform wars settle into two camps.
- 🆕 **Execution-bottleneck thesis** — sandbox + agent-desktop is the new moat layer.
- 🆕 **Claude Code 2.1.319 "deny instead of prompt" + MCP tasks in terminal** — `/loop`-safe auto-mode is production-ready.
- 🆕 **MCP 2026-07-28 stateless is now Claude.ai default** — pre-July-2026 MCP servers need rewrite/shim.
- 🆕 **Memory-for-agents cluster back at HF #1 + AMA-Bench null result** — horizontal agent-memory pitches without a vertical are now contested.
- ➡️ **MSFT 60K buyout (from 2026-11-14):** Dec 1 deadline now 15 days away; April precedent suggests 30% uptake vs. 3–5% guidance = Jan 1 supply bulge 5,000–18,000 engineers.
- ➡️ **FDE lane (from 2026-10-14):** new-grad comp band confirmed at $135–$150K base (Palantir / Domino); experienced median $173,816.
- ⬇️ **"Vendor-neutral" positioning** — Ramp data contradicts it; Anthropic at 60.1% is a concentration risk your sales deck should admit.
- ⬇️ **Horizontal agent-memory wedge** — AMA-Bench null + crowded field (Mem0, Letta, Zep, Papr); vertical-only or debug-tooling-only from here.
- ⬇️ **Static benchmarks for agent evals** — training-contamination problem is real; use controllable-rollout benchmarks (LongMINT, AgentLongBench).

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo-pricing) (ANT IPO pricing) |
| 20 min | [`01` §1–2](./01-big-lab-moves.md) + [`05` §1–3](./05-career-and-startup.md) — ANT pricing + NVDA earnings + MSFT buyout + FDE comp + ANT-week thesis |
| Today | [`05` §6](./05-career-and-startup.md#6-monday-action) — 5 FDE apps before Thursday night |
| This weekend | [`03` §3](./03-practical-skills-and-tools.md#3-mcp-2026-07-28) — ship one MCP server on 2026-07-28 spec (the #1 portfolio artifact for FDE applications this week) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
