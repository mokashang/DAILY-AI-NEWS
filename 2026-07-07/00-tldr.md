# TL;DR — 2026-07-07 (Tuesday)

Sixty-second skim. **The state gets a seat at the cap table, Anthropic gets out of jail with a new default model, Meta becomes a neocloud, and China closes the gap — all inside seven days, and today is the day it converges.** OpenAI is floating a **5% equity stake to the US government** (~$42.6B at its $852B valuation) via an Alaska-Permanent-Fund-style sovereign vehicle, and the proposal explicitly asks **Anthropic / Google / Meta** to hand over similar stakes — the White House **voluntary standards framework** for GPT-5.6's broad release is expected around today. Anthropic **restored Fable 5 + Mythos 5 on July 1** after 3 weeks in export-control jail and shipped **Claude Sonnet 5** ("most agentic Sonnet yet") at introductory **$2/$10 per-M through Aug 31**. Meta launched **Meta Compute** — turning excess AI capacity into a neocloud — and the market repriced the entire neocloud category (CoreWeave –14%, Nebius –17%). And **CNBC's July 7 headline: Chinese GLM 5.2 is within 1 point of Opus 4.8 on agentic bench at ~1/5 the cost**, with the fastest week-1 adoption of any 2026 model on Vercel (27× tokens, 80× customers). For you: the **agentic-Sonnet-at-half-price window closes Aug 31** — that is the resume-building window, and the multi-vendor cost story is now a real interview differentiator.

---

1. **OpenAI floats 5% US-government equity stake (FT).** Sovereign-fund vehicle patterned on the Alaska Permanent Fund; ~**$42.6B** at OpenAI's **$852B** valuation. Altman engaging Trump, Lutnick, Bessent directly; would likely need an **act of Congress**. Same proposal asks **Anthropic, Google, Meta** to cede similar stakes. The **White House voluntary standards framework** for GPT-5.6 broad release is expected **around today**. → [`01` §1](./01-big-lab-moves.md#1-openai-govt-stake) `#openai #policy #public-markets #framework`

2. **Claude Sonnet 5 launched + Fable 5 / Mythos 5 restored globally (July 1).** Sonnet 5 = "most agentic Sonnet yet" (autonomous browsers, terminals, multi-step tools), close to Opus 4.8 at much lower cost. **Introductory pricing: $2/M input, $10/M output through Aug 31.** Fable 5/Mythos 5 back after a **3-week export-controls pause** (triggered by an Amazon-researcher jailbreak → vuln-code demo); new cybersecurity classifiers added as "strongest safeguards." → [`01` §2](./01-big-lab-moves.md#2-sonnet-5-fable-back) `#anthropic #sonnet-5 #fable-5 #safety`

3. **Meta launches "Meta Compute" — Meta as neocloud.** Announced July 1; Meta will rent out **excess AI compute** to outside customers; unit led by Santosh Janardhan + Daniel Gross (MSL) + Dina Powell McCormick. Meta **+8.8%** to $612.91; **CoreWeave –14%, Nebius –17%, IREN tumbled**. Meta 2026 AI capex guide **$115–135B**; total commitments **$182.9B**. The neocloud category thesis just got a hyperscaler-attached competitor. → [`01` §3](./01-big-lab-moves.md#3-meta-compute) `#meta #compute #neocloud #capex`

4. **Chinese GLM 5.2 closes the frontier gap — fastest week-1 adoption of any 2026 model.** Zhipu / Z.ai released **GLM 5.2** in June; **within 1 point of Opus 4.8 on an agentic benchmark at ~1/5 the cost**, **1M-token context**, now **top of OpenRouter** for coding/agentic and **#5 on Artificial Analysis intelligence**. Vercel: **27× daily tokens, 80× customer count** in first week. Zhipu also released **ZCode** (its Claude-Code-style harness). US enterprises still gated by data-security concerns; **cost-sensitive + emerging-market** share is where China is winning. → [`02` §1](./02-new-emerging.md#1-glm-52) `#china #open-weights #glm #cost`

5. **Emerging: agentic-vertical Series B wave — Tenex.AI $250M (agentic SOC) + Avoca $125M (AI CX agents).** Tenex Series B led by **Crosspoint Capital** (+ a16z, Shield, DTCP, Deepwork, FL Opportunity Fund); joins the AI-SOC unicorn tier. Avoca Series B led by **General Catalyst + Meritech** (with Kleiner, YC). **Taktile** added a **$110M Series C** (Goldman GE) for agentic decisioning at banks/insurers. Series B is now the **modal round** in agentic AI = the category has moved past experimentation. → [`02` §2](./02-new-emerging.md#2-agentic-vertical-b-wave) `#funding #agents #cybersecurity #cx #fintech`

6. **Research: real-tool eval is the new frontier of measurement.** **MCP-Bench** (real MCP servers, complex tasks) + **LiveMCP-101** (stress-test / diagnose MCP-enabled agents) + **Odysseys** (long-horizon web-agent benchmark) + **Workspace-Bench 1.0** (large-scale file-dependency workspace tasks) + **OfficeQA Pro** (enterprise end-to-end grounded reasoning) + **WebWorld** (large-scale world model for web-agent training). The eval bar has moved from mocked tools to **the actual stack**. → [`04` §1](./04-research-progress.md#1-real-tool-eval) `#benchmarks #mcp #agents #arxiv`

7. **Practical: prompt caching + Tool Search Tool + minimal-setup Claude Code — the three levers that survive June 15 metering.** Prompt caching: **cached input tokens ≈ 10% of normal price** → **60–90% input-cost cut** on production loops. **Tool Search Tool: –85% token usage** and Opus 4.5 MCP-eval jumps **79.5% → 88.1%**. Minimal setup: **one CLAUDE.md, one scoped .mcp.json, one safety hook, one reusable skill, subagents only when they'd otherwise pollute the main context.** → [`03` §1](./03-practical-skills-and-tools.md#1-cost-levers) `#claude-code #caching #tool-search #mcp #cost`

8. **Skill read of the week:** the interview-differentiating story is now **"which model, on which task, verified against real tools, at a cached-token cost"** — Sonnet 5's intro window, GLM 5.2's cost gravity, and MCP-Bench/LiveMCP-101 all point at **multi-vendor cost-aware verification** as the 2026 hire-signal. Ship one artifact that shows it end-to-end before Aug 31. → [`05` §2](./05-career-and-startup.md#2-skill-reprice) `#skills #careers #multi-vendor`

---

## One thing to DO this Tuesday

→ **Rebuild the dual-model sanitiser artifact on Sonnet 5** ([carried from 2026-05-22](../2026-05-22/00-tldr.md#one-thing-to-do-this-friday)) using the intro **$2/$10** window. Add a **cached-prompt harness** ([`03` §1](./03-practical-skills-and-tools.md#1-cost-levers)) and a **10-case MCP-Bench-style eval** against a real MCP server ([`04` §1](./04-research-progress.md#1-real-tool-eval)). One README now demonstrates: agentic-Sonnet, verified real-tool eval, and cached per-step cost. **Also:** apply to **one Tenex.AI + one Avoca** FDE/AI-Eng role ([`05` §3](./05-career-and-startup.md#3-apply-this-week)).

## Watchlist deltas

- 🆕 **US-government AI equity vehicle (5%):** new thread — track Anthropic/Google/Meta responses, the White House standards framework text, and whether the vehicle survives Congress.
- 🆕 **Sonnet 5 intro pricing window ($2/$10 through Aug 31):** new thread — this is the **portfolio-building window**; log which of your artifacts use Sonnet 5 as the workhorse.
- 🆕 **Meta Compute / neocloud repricing:** new thread — watch whether CoreWeave/Nebius/IREN rebound or Meta locks in anchor tenants; this reshapes the AI-infra hiring lane.
- 🆕 **GLM 5.2 adoption curve:** new thread — Vercel telemetry, OpenRouter rank, ZCode uptake. Cost-share is the leading indicator.
- 🆕 **Agentic-SOC + Agentic-CX Series B wave:** new thread — Tenex + Avoca set the comps; watch for the next $100M+ round in either lane.
- ➡️ **Real-tool eval (MCP-Bench / LiveMCP-101 / Odysseys):** continues from 2026-05-22 (MCP-Atlas / Tool Decathlon). Verification-against-real-tools is now the standard.
- ➡️ **OpenAI S-1 / IPO timing:** last update 2026-05-22 (targeting Sept 2026); watch whether the govt-equity proposal delays or accelerates the roadshow.
- ➡️ **Anthropic Agent SDK metering (was June 15):** now past — measure and share your actual bill delta as a portfolio artifact.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + OpenAI/US-govt equity + Sonnet 5 in [`01` §1–2](./01-big-lab-moves.md) |
| 20 min | [`02` §1](./02-new-emerging.md#1-glm-52) (GLM 5.2 cost gravity) + [`04` §1](./04-research-progress.md#1-real-tool-eval) (real-tool eval) — the two deepest signals |
| Today | [`05` §3](./05-career-and-startup.md#3-apply-this-week) — 1× Tenex + 1× Avoca application |
| Tonight | [`03` §1](./03-practical-skills-and-tools.md#1-cost-levers) — turn on prompt caching + Tool Search on your Sonnet 5 workhorse |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
