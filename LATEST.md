# LATEST — pointer to the most recent edition

> **2026-09-26** — see [`2026-09-26/00-tldr.md`](./2026-09-26/00-tldr.md)

This file is auto-updated every edition so a one-click read of the latest TL;DR is always at the repo root.

---

## Today's headline

**Saturday — Dreamforce week + Copilot refresh + Meta Connect + Qwen-Audio 3.1 = the F500 UI is now optional and voice is 95% cheaper — all in five days.** **Salesforce Dreamforce '26** shipped **AIforce + Headless 360** (a 60+ tool MCP server exposing every Salesforce cloud) with **Claudeforce** as the deepened Anthropic integration and **Koa**, a CRM-vertical reasoning model built with NVIDIA on Nemotron; Marc Benioff's framing: *"AI replaces the UI."* **Microsoft Copilot redesign (Sept 25)** rolled out a three-layer platform — Home + Code + a persistent **Autopilot** agent with tenant identity + memory + workspace — plus **Agent 365** governance (identity, monitoring, policy, spend). **Meta Connect (Sept 24)** unveiled **Muse Charm** (pendant), **Muse Realtime Avatar**, and **100+ AI-glasses styles by year-end**. **Alibaba Qwen-Audio 3.1 (Sept 23–24)** cut ASR up to **95%**, TTS ~70%, Realtime ~85% — setting the global floor on enterprise voice API pricing overnight. Meanwhile **Google DeepMind's Kavukcuoglu** confirmed **Gemini 4 is in post-training** with a "much earlier than year-end" target, and the **Anthropic public S-1** window narrowed to end of September (first-trade October). Full edition → [`2026-09-26/`](./2026-09-26/).

**For you:** the **"AI Integration Engineer for F500 SaaS agent surfaces"** lane opened as a discrete sub-market this week — 500–1,000 unadvertised roles now, **10,000–15,000 by December**. Skills that repriced upward this week: **MCP-server author-experience, agent governance (identity + audit + allowlist + cost cap), vertical eval design, cost-aware routing across three tiers × four labs**. The **weekend project** is a router-to-MCP shim ([`03 §1`](./2026-09-26/03-practical-skills-and-tools.md#1-router-shim)) that consumes a real MCP server, wires per-tool cost logging + 5-case eval, and adds 6 governance primitives ([`03 §2`](./2026-09-26/03-practical-skills-and-tools.md#2-agent-governance)) — ship publicly this weekend with a price/quality frontier plot.

Full edition → [`2026-09-26/`](./2026-09-26/)

---

## One-thing-to-do (Sat Sept 26 → Sun Sept 27)

→ **Saturday (4–6 h): ship the router-to-MCP shim.** Take last weekend's router; wire it as an MCP client; mount `filesystem` / `github` / `postgres` MCP; add the 5-case eval (extraction / coding / long-context Q&A / multi-hop agentic tool use / bulk labeling via OpenRouter Batch); log per-tool cost + latency; publish public MIT with a price/quality frontier plot. Add the 6 agent-governance primitives (per-agent identity, per-tool allowlist, per-request cost cap, immutable audit trail, rate/burst limiting, human-in-the-loop escalation). Post to LinkedIn by 8 PM PT. [`03 §1`](./2026-09-26/03-practical-skills-and-tools.md#1-router-shim) · [`03 §2`](./2026-09-26/03-practical-skills-and-tools.md#2-agent-governance).

→ **Sunday (2–3 h): DolphinBench summary + 5 applications + 3 cold DMs.** Read **DolphinBench (arXiv 2609.24971)** — the Pareto-frontier-of-agent-memory paper (accuracy × cost × latency); write a 500-word summary and post as `NOTES-dolphinbench.md`. Submit 5 applications (3× Anthropic Applied AI / Solutions / FDE — pick Life Sciences post-ART or Legal per your background + 2× funded startup: Cognition post-$2B, Sierra, Instinct, Twelve Labs). Draft 3 cold DMs for Monday 8 AM PT: Anthropic Solutions engineer on Claudeforce + Salesforce Headless 360 integration lead + Microsoft Copilot Autopilot PM. Update **LinkedIn headline**: `AI Integration Engineer · Anthropic-stack · MCP + agent governance`. [`04 §1`](./2026-09-26/04-research-progress.md#1-dolphinbench) · [`05 §4`](./2026-09-26/05-career-and-startup.md#4-saturday-action).

→ **Voice-cost worksheet (60 min):** for one active STARTUPS.md wedge, re-run unit economics against Qwen-Audio 3.1's new pricing (ASR ~$0.03/hr, TTS ~$0.30/hr). If payback period improves >3×, the wedge just moved from "not fundable" to "seed-shape." [`03 §3`](./2026-09-26/03-practical-skills-and-tools.md#3-voice-worksheet).

→ **Watch Sept 27–Oct 3** for the **Anthropic public S-1 filing** (read it the day it lands — segment-revenue lines + risk factors are the highest-signal doc of Q4), **HubSpot/Zendesk/Adobe/Workday parity to Claudeforce** (each triggers its own integration-engineer hiring wave), **Microsoft Autopilot private-preview customer names**, **Deepgram / ElevenLabs US price responses** to Qwen-Audio 3.1, and **Google Gemini 4** dropping "much earlier" per Kavukcuoglu.
