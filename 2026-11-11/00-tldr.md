# TL;DR — 2026-11-11 (Wednesday)

Sixty-second skim. **The 28 days since Oct 14 reshape your plan again — but this time at the capital-markets level.** On **Oct 26 Anthropic filed a public S-1 under ticker ANT (Nasdaq)**; the amended S-1/A (Nov 2) discloses **$33.24B revenue for the nine months ended Sept 30, 2026** ($16.3B H1); the **roadshow opened the week of Nov 9**, with **pricing targeted the week of Nov 16** at a reported **$1.5T–$2T valuation raising $100B+**, listing **pre-Thanksgiving** (Nov 12 is the financials-stale cliff). On **Nov 9 Anthropic shipped Claude Fable 5.2 (GA) + Mythos 5.2 (vetted-tier)** at **$8/$40 per 1M tokens (-20% vs 5.1), $0.20/1M cached, optional "Fast Mode" at 2× price, 30% faster than 5.1** — the pre-IPO show-of-strength model. On **Nov 12 (tomorrow) OpenAI terminates Cursor's direct API access** following SpaceX's acquisition of Anysphere — the first clean frontier-vendor pull of 2026. On **Sept 30 Google unveiled Gemini 4 Argon in restricted rollout to Fairwind cyber-defenders only** (77.9% DeepSWE v1.1, 70.9% Wiz pen-test, 68% CWE-bench v1; Gemini 3.5 Pro cancelled). **Microsoft Ignite is Nov 17–20** with Copilot Autopilot + Code + Home shipping GA. **NVIDIA Q3 FY27 prints Nov 17/18** (consensus ~$108–109B). Underneath: **Haiku 5.5 effort levels + Fable 5.2 Fast Mode + cached pricing = routing is now a 4-dimensional tunable**, and the Nov 12 Cursor cutoff **re-prices "vendor-neutral by architecture" from nice-to-have to résumé-table-stakes.**

---

1. **Anthropic public S-1 (Oct 26, ticker ANT, Nasdaq) + roadshow week of Nov 9 + pricing week of Nov 16.** $33.24B revenue 9 months through Sept 30 ($16.3B H1); reported **$1.5T–$2T valuation, $100B+ proceeds**; listing targeted pre-Thanksgiving; Nov 12 cliff on June 30 financials going stale. **First frontier lab to transition to a public company.** → [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo) `#anthropic #ipo #ant #nasdaq #careers`

2. **Claude Fable 5.2 (GA) + Mythos 5.2 (vetted-tier) shipped Nov 9.** $8 in / $40 out per 1M, $0.20/1M cached, Fast Mode 2× (optional per-call), 30% faster than 5.1; cybersecurity + biology safeguards; same underlying weights for Fable (public) and Mythos (vetted CVP tiers). The IPO show-of-strength model — and **the Fast Mode knob makes model-choice a 4-dimensional tunable (model × effort × fast-mode × cache state).** → [`01` §2](./01-big-lab-moves.md#2-fable-5-2) `#anthropic #fable-5-2 #mythos-5-2 #pricing #routing`

3. **OpenAI terminates Cursor direct API access TOMORROW (Nov 12)** following SpaceX's close of its $60B Anysphere acquisition (Aug 14). OpenAI cites distillation / contract-breach concerns tied to Musk-company history. Anthropic responded by raising Claude usage limits for Cursor users. **First real-world frontier-vendor pull of 2026 — "vendor-neutral by architecture" is now a procurement requirement, not a nice-to-have.** → [`01` §3](./01-big-lab-moves.md#3-openai-cursor-cut) `#openai #cursor #spacex #distribution #vendor-risk`

4. **Google Gemini 4 Argon — limited rollout to Fairwind cyber-defenders only (Sept 30).** Public release timing undisclosed. Argon: 77.9% DeepSWE v1.1, 70.9% Wiz pen-test, 68% CWE-bench v1 (self-reported; Bloomberg contests). **Gemini 3.5 Pro cancelled before launch.** Access-tier-gating mirrors Mythos playbook — **vetted-tier release is now the industry default for frontier capability tier.** → [`01` §4](./01-big-lab-moves.md#4-gemini-4-argon) `#google #gemini-4 #argon #fairwind #cyber-defender`

5. **Microsoft Copilot Autopilot + Code + Home GA (Nov Frontier → worldwide); Ignite Nov 17–20 San Francisco.** Autopilot = always-on cloud personal agent for proactive long-running enterprise tasks; Code = app-building; Home = Chat + Cowork unified. **Direct answer to ChatGPT-as-OS and Claude Code's desktop/CLI distribution.** Pricing to drop at Ignite = the number that re-prices the agent-runtime market. → [`01` §5](./01-big-lab-moves.md#5-microsoft-copilot) `#microsoft #copilot #autopilot #ignite #agents`

6. **Funding barbell — the Nov 2–6 week printed ~$9.8B across 25 rounds.** Headliners: **fal $1.3B Series F at $16B** (Bessemer; Nvidia / Sound / T. Rowe — generative-media inference, $800M+ ARR; valuation doubled from $8B in April) · **Applied Compute $350M at $3.25B** (Elad Gil; Nvidia / Shopify / HubSpot — ex-OpenAI founders, $100M ARR in 18 months) · **Nooks $500M from General Catalyst Customer Value Fund** (performance-linked capital, not equity — Revenue Agent Platform) · **Ocient $100M** (policy-controlled agent data access) · **Automation Anywhere → Boost.ai $1.2B** (conversational-agent consolidation) · **Salesforce → Loops** (agentic analytics into Tableau). → [`02` §1](./02-new-emerging.md#1-funding-barbell) `#funding #series-f #fal #applied-compute #nooks #m&a`

7. **Anthropic Skills / Plugins / Connectors merged into one Plugins page; Enterprise admin cutover Nov 30.** Free/Pro/Max/Team/Ultra rolling out since Oct 29. **If your target org is Enterprise, confirm Skills is toggled ON by Nov 30 or Claude Desktop plugins stop working.** Open-standard: each skill is a folder with `SKILL.md` + optional scripts/resources. → [`03` §1](./03-practical-skills-and-tools.md#1-skills-plugins) `#anthropic #skills #plugins #admin #enterprise`

8. **Claude Code v2.1.317 (Nov 2) — Agent SDK blocking hooks + per-gateway cost reports.** Pre-tool hooks that exit non-zero now **halt the agent** (previously only warned); gateway admins get per-team/per-user spend tables. v2.1.318 followed Nov 3; Opus 4.8 fast mode deprecated Nov 30. → [`03` §2](./03-practical-skills-and-tools.md#2-claude-code-2-1-317) `#claude-code #hooks #gateway #cost-controls`

9. **Research: routing as a measured discipline.** **PISA / PISA-E (arXiv 2611.10193)** = **36% / 25% lower cost** vs strongest single-model / ensemble baselines at matched quality. **Route Anything (arXiv 2611.05275) = 8.82× quality-per-dollar** with <0.5-pt quality loss, gains largest on code tasks. **Agent Architecture Cost-Success (arXiv 2611.12953)** = single agent is the efficient default; multi-agent costs **1.5–4.8× more tokens**, **2.5–5.9× more latency** without proportional success gain. → [`04` §1](./04-research-progress.md#1-routing-arxiv-wave) `#arxiv #routing #cost-aware #single-agent`

10. **Research: memory went from pitch to measured attack surface in 2 weeks.** **Delivered-Not-Used (arXiv 2611.01718)** = across 8,000 SWE-bench Verified episodes, memory-equipped agents stay **within 0.4pp of no-memory baseline** at resolve rate — most delivered memory is irrelevant at the point it's retrieved. **MemoryDojo (arXiv 2611.09721)** = every memory system tested is susceptible to poisoning. → [`04` §2](./04-research-progress.md#2-memory-reality-check) `#arxiv #memory #evals #poisoning #security`

11. **MCP crossed 10K public servers + 97M monthly SDK downloads (Stacklok / Nordic APIs, Oct).** **41% of enterprise software orgs have MCP in limited-or-broad production.** Simon Willison (Oct 22) reaffirmed MCP's core value = **controlled access to sensitive resources**, not "wrap an API." The surviving MCP niche = gated data + per-tool audit logs + stateful sessions. → [`03` §5](./03-practical-skills-and-tools.md#5-mcp-at-10k) · [`05` §1](./05-career-and-startup.md#1-reprice) `#mcp #open-source #enterprise #adoption`

12. **The re-price of the month — four knobs, not one.** Model-fluency keeps sliding (Fable 5.2 + Fast Mode makes "which Claude" a 4D tunable). **Priced UP:** trajectory-level eval authoring (Arize / Langfuse / DeepEval all shipped it in Oct), **model-router design** across the 4D grid, **MCP server authoring with security + governance built in**, **cyber-defender adjacency** (Gemini 4 Argon / Mythos 5.2 both gate on verified defender status), **pre-IPO disclosure engineering** (new lane at Anthropic). **Priced DOWN:** single-vendor coding-agent fluency (the Nov 12 Cursor cutoff is Exhibit A), raw prompting, and the AI/ML pay premium itself — **1.29× non-AI, down from 1.34×** per FutureProofing's Levels.fyi analysis. → [`05` §1](./05-career-and-startup.md#1-reprice) `#careers #routing #fde #mcp #compensation`

---

## One thing to DO this Wednesday

→ **Submit 2 apps + ship one portfolio patch, 55 minutes, before 11:59 PM PT:**

1. **:00–:15** — **OpenAI Forward Deployed SE, Public Sector, DC** ($255K–$405K base) — lead with: "I know how to migrate stacks between frontier vendors cleanly — the Nov 12 Cursor cutoff is my talking point." [posting](https://openai.com/careers/forward-deployed-software-engineer-gov-washington-dc/)
2. **:15–:30** — **Anthropic Solutions Architect, Applied AI (Beneficial Deployments)** (SF, $240K–$270K) — lead with: "I'm shipping a post-Cursor router this weekend that routes to Fable 5.2 default, Mythos 5.2 for gated-cyber paths, Gemini 4 Argon when the customer is Fairwind-verified."
3. **:30–:45** — **Patch public MCP server README** with a 5-line "Vendor-neutral by design — swap backends via config" callout. Interview-ready evidence for apps 1 and 2.
4. **:45–:55** — **3 cold emails**: one Academy partner-firm AI engineer (McKinsey QuantumBlack / Bain Vector / Deloitte AI Institute), one Anthropic Solutions Architect (LinkedIn), one fal engineer (just raised $1.3B, hiring spike incoming).

Details in [`05` §2](./05-career-and-startup.md#2-apply-plan).

## Watchlist deltas

- 🆕 **Anthropic IPO public (ANT, Nasdaq):** new thread, highest signal. Pricing range, first-day pop, lock-up schedule, Pentagon-break disclosure language, T&S / Research-Governance hiring spike post-listing.
- 🆕 **Fable 5.2 / Mythos 5.2 + Fast Mode as a routing primitive:** new thread. Watch whether OpenAI / Google match within 30 days; whether Fast Mode becomes a routing primitive separate from effort level.
- 🆕 **OpenAI × Cursor cutoff (Nov 12):** new thread. First real-world vendor pull; watch for "vendor-neutral by contract" procurement language in F500 RFPs.
- 🆕 **Gemini 4 Argon locked to Fairwind:** new thread. Access-tier-gating as the new norm; watch whether Fairwind opens beyond cyber by Q1 2027.
- 🆕 **Skills → Plugins Enterprise cutover Nov 30:** new thread. 19 days to confirm admin toggle; silent fail downstream.
- 🆕 **Microsoft Ignite Nov 17–20 + Autopilot pricing:** new thread. The $/seat that re-prices the agent-runtime market.
- 🆕 **NVIDIA Q3 FY27 Nov 17/18:** new thread. $108–109B consensus; capex-thesis pivot point (beat drags Anthropic IPO pricing up; miss drags it down).
- 🆕 **fal $1.3B / $16B as capacity-scarcity signal:** new thread. Replicate / Together / Modal / Fireworks responses in the next 60 days.
- ➡️ **Frontier Academy (Oct 2):** holding — no cohort stats yet; first credentials early 2027; still nomination-only.
- ➡️ **Pentagon break (Oct 5):** stalled publicly — no visible ruling; disclosure item in the S-1.
- 🟢 **Haiku 5.5 (Oct 7):** superseded upward — Fable 5.2 is the new frontier; Haiku 5.5 keeps the worker tier; effort levels confirmed as a research-grade routing primitive (PISA / Route Anything).
- 🟢 **OpenAI confidential → public IPO path:** **possibly slipping to 2027** per one source — OpenAI may delay to seek higher valuation after Anthropic prints.
- ⬇️ **"Latest model" fluency:** further deprecated. Fast Mode + effort + cache state = the question is no longer "which model" but "which 4D cell."
- ⬇️ **AI/ML pay premium:** 1.34× → 1.29× in-window (FutureProofing / Levels.fyi). Still a premium, closing.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo) (the IPO — the career-reset story of November) |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) + [`05` §1–2](./05-career-and-startup.md) — IPO + Fable 5.2 + Cursor cutoff + apply plan |
| Today | [`05` §2](./05-career-and-startup.md#2-apply-plan) — 2 FDE apps + patched MCP README + 3 cold emails before 11:59 PM PT |
| This weekend | [`03` §3](./03-practical-skills-and-tools.md#3-post-cursor-router) — ship the Post-Cursor Router repo + Show HN + Mon 9 AM PT tweet (rides the IPO news cycle) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
