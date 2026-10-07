# TL;DR — 2026-09-26 (Saturday)

Sixty-second skim. **Dreamforce week + Copilot refresh + Meta Connect + Qwen-Audio 3.1 = the F500 UI is now optional and voice is 95% cheaper — all in five days.** Salesforce shipped **AIforce + Headless 360** (a 60+ tool MCP server exposing every Salesforce cloud) with **Claudeforce** as the deepened Anthropic integration; Microsoft rolled out the **Copilot redesign** with a persistent **Autopilot agent** + tenant-native **Agent 365** governance fabric; Meta announced **Muse Charm** (pendant), **Muse Realtime Avatar**, and **100+ AI-glasses styles by year-end**; Alibaba cut **Qwen-Audio 3.1** voice pricing by up to **95%**; and **Google DeepMind** confirmed **Gemini 4 is in post-training** with a "much earlier than year-end" launch target. The **Anthropic public S-1** window narrowed to end of September. For you: the **"AI Integration Engineer for F500 SaaS agent surfaces"** lane opened as a discrete sub-market this week — **1,000-15,000 unadvertised roles by December** — and your Saturday project is to ship a **router-to-MCP shim + agent-governance primitives** so your resume classifies you into that lane on Monday morning.

---

1. **Salesforce Dreamforce '26: AIforce + Headless 360 = "AI Replaces the UI."** Marc Benioff unveils an agentic interface layer that drives Salesforce from Claude / Slack / Lightning; Headless 360 exposes every Salesforce cloud through an **MCP server with 60+ tools**. Dario Amodei on stage to unveil **Claudeforce**; NVIDIA co-built **Koa**, a CRM-vertical reasoning model on the Nemotron family. → [`01` §1](./01-big-lab-moves.md#1-dreamforce-aiforce) `#salesforce #anthropic #mcp #agents #enterprise`

2. **Microsoft Copilot redesign — Home / Code / Autopilot + Agent 365.** Sept 25 rollout. **Autopilot** = persistent cloud-hosted agent with tenant identity, memory, workspace, capable of multi-step workflows; **Copilot Managed Runtime** hosts natural-language-built apps *inside your tenant*; **Agent 365** provides identity + monitoring + policy + spend controls **for agents specifically**. Autopilot to private preview end of Sept. → [`01` §2](./01-big-lab-moves.md#2-microsoft-copilot) `#microsoft #copilot #agents #governance`

3. **Anthropic public S-1 expected by end of September; first-trade October.** ARR run-rate ~$47B → tracking to $110B; Series H at $965B post-money; underwriters Goldman/JPM/Morgan Stanley. First frontier lab to IPO. Read the risk-factors + segment-revenue sections the day it lands. → [`01` §3](./01-big-lab-moves.md#3-anthropic-s1) `#anthropic #ipo #public-markets`

4. **Google — Gemini 4 in post-training + Gemini 3.8 Live Avatar in Enterprise.** DeepMind chief Kavukcuoglu (Sept 23-24): Gemini 4 hopes to launch "much earlier" than end-of-year. Meanwhile Gemini 3.8 Live + Live Avatar ship in Gemini Enterprise with 97-language lip-sync. Prediction markets: ~74% Gemini-4-before-November. → [`01` §4](./01-big-lab-moves.md#4-google) `#google #gemini #multimodal`

5. **Meta Connect: Muse Charm pendant + Muse Realtime Avatar + 100 AI-glasses styles by year-end.** First-to-market consumer AI device at scale; OpenAI's Jony-Ive hardware slipping further under the Apple lawsuit. Reality Labs + Muse pods are the current Meta hiring engine. → [`01` §5](./01-big-lab-moves.md#5-meta-connect) `#meta #muse #consumer #devices`

6. **Alibaba Qwen-Audio 3.1: ASR −95%, TTS −70%, Realtime −85%. Five-model stack incl. ASR-Next + TTS-Next.** Sets the global floor on enterprise voice API pricing overnight. Deepgram / ElevenLabs / OpenAI Whisper procurement contracts should be re-run before renewal. → [`02` §1](./02-new-emerging.md#1-qwen-audio) `#alibaba #qwen #voice #pricing`

7. **MCP-server cascade: Eventtia (Sept 25) + Salesforce Headless 360 + Amazon Seller Central Selling Partner + Microsoft Agent 365 in five days.** MCP is now the dominant agent-to-tool interop standard. **MCP-server author-experience** is the differentiating skill for the next 6 months. → [`02` §2](./02-new-emerging.md#2-mcp-cascade) `#mcp #agents #integration`

8. **The router-to-MCP shim = Saturday's weekend project.** Take Friday's model-router; wire it as an MCP client; mount `filesystem` / `github` / `postgres` MCP; add per-tool cost logging + 5-case eval; ship public with a price/quality plot. ~3 hours. This artifact is *the* Q4 2026 interview differentiator. Add 6 governance primitives from [`03` §2](./03-practical-skills-and-tools.md#2-agent-governance) — you're done by 5 PM. → [`03` §1](./03-practical-skills-and-tools.md#1-router-shim) `#weekend #mcp #router #agents`

9. **arXiv: DolphinBench — mapping the Pareto frontier of agent memory (accuracy × cost × latency).** Sept 21 submission. The methodology is directly portable to any enterprise memory eval — and cite-drop for a senior-level agent-eng interview. Read + write a 500-word summary this Sunday; that's the paper of the month. → [`04` §1](./04-research-progress.md#1-dolphinbench) `#arxiv #agents #memory #evaluation`

10. **Career: "AI Integration Engineer for F500 SaaS agent surfaces" is now a distinct lane.** 500–1,000 unadvertised roles across SaaS / Big-4 / lab-Solutions / SI shops now, 10,000–15,000 by December. Salary floor **$184-$249K MLE at AI startups**, senior AI-Engineer $206K+ base + 30% premium for MCP / governance / eval-design / vertical / cost-routing skills. → [`05` §1](./05-career-and-startup.md#1-hiring-map) · [`05` §2](./05-career-and-startup.md#2-integration-lane) `#careers #integration #fde #anthropic`

---

## One thing to DO this Saturday {#one-thing-to-do}

→ **Ship the router-to-MCP shim + 6 governance primitives by 8 PM PT, and post the price/quality plot to LinkedIn by Sunday.** This is the artifact that answers "why should we hire you when four labs shipped new tiers this month?" — because you didn't try to be current on models, you built the layer that *stays* current *and* respects the tenant-identity, cost-cap, and audit-trail primitives every Q4 2026 enterprise agent-in-prod already needs. Full details in [`03` §1](./03-practical-skills-and-tools.md#1-router-shim) + [`03` §2](./03-practical-skills-and-tools.md#2-agent-governance) + [`03` §4](./03-practical-skills-and-tools.md#4-weekend).

## Watchlist deltas

- 🆕 **Salesforce Claudeforce + Headless 360 (60+ MCP tools):** new thread. Watch for HubSpot / Zendesk / Adobe / Workday parity announcements inside 30 days (each triggers its own integration-engineer hiring wave). Also watch: does Salesforce open Koa's weights? If yes, vertical-open-model wedge explodes.
- 🆕 **Microsoft Agent 365 + Autopilot:** new thread. Governance-first agent platform. Watch: Autopilot private-preview customer names when they surface late Sept / early Oct — that's the F500 CIO who trusts Microsoft over Anthropic/OpenAI for production agent identity.
- 🆕 **Qwen-Audio 3.1 (−95% ASR):** new thread. Watch: does Deepgram / ElevenLabs match within 30 days, and does US-side procurement start accepting Alibaba endpoints? Both are Q1 2027 arbitrage signals.
- 🆕 **Meta Muse Charm pendant + 100 AI-glasses styles by year-end:** new thread. Consumer-agent device race is now Meta's to lose. Watch: Meta Q3 earnings for Muse-device unit numbers, and whether SDK opens in Q1 2027.
- 🆕 **DolphinBench (arXiv 2609.24971):** new thread. Agent-memory eval canon is forming (DolphinBench + MemCalib + Jev-Mem + EverMemBench). Reading all four = top-1% candidate on this topic.
- ➡️ **Anthropic public S-1 (from 2026-09-25):** promoted from "expected inside 2 weeks" to "expected by end of September." Read it the day it lands.
- ➡️ **Gemini 4 (from 2026-09-25):** now with a "much earlier than year-end" signal from Kavukcuoglu. Prep router-shim extension slot for it now.
- ➡️ **MCP as agent-tool standard (from 2026-09-25):** further hardened — Salesforce / Microsoft / Amazon / Eventtia all shipped this week. Now baseline, not differentiator.
- ⬇️ **"General-purpose AI copilot for X":** deprecated. Microsoft Autopilot subsumes most of it. Any startup here needs a distribution or vertical moat Microsoft can't reach.
- ⬇️ **"Live-avatar for consumer":** deprecated. Google + Meta close the general consumer surface. Live-avatar wedges only survive in regulated verticals now.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1 Dreamforce/AIforce](./01-big-lab-moves.md#1-dreamforce-aiforce) + [`01` §2 Microsoft Autopilot](./01-big-lab-moves.md#2-microsoft-copilot) |
| 20 min | [`03` §1–3](./03-practical-skills-and-tools.md) — router-to-MCP + governance + voice-cost worksheet |
| Today | [`03` §1 + §2](./03-practical-skills-and-tools.md#1-router-shim) — ship the router-to-MCP shim + governance primitives |
| Sunday | [`04` §1 DolphinBench](./04-research-progress.md#1-dolphinbench) — read, summarize, post as `NOTES-dolphinbench.md` |
| Weekend total | [`03` §4 weekend playbook](./03-practical-skills-and-tools.md#4-weekend) + [`05` §4 Saturday action](./05-career-and-startup.md#4-saturday-action) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
