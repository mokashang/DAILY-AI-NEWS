# TL;DR — 2026-07-27 (Monday)

Sixty-second skim. **The Sunday timers all fired: Kimi K3 weights are live, Fellows deadline closed, and the MCP 07-28 spec finalizes tomorrow.** **Kimi K3 open weights hit HuggingFace at 00:00 UTC today** as [yesterday's edition](../2026-07-26/00-tldr.md) predicted — 2.8T sparse MoE, 1M context, largest open-weight model ever published, ~51% hallucination gap between vanilla weights and hosted API is the fresh-morning observation. **MCP 2026-07-28 stateless spec finalizes tomorrow (Tuesday)** — the RC has been out since May, so this is a scheduled cutover, but the PR still needs to draft tonight. And the **FLI Summer 2026 Safety Index** (published 07-07) is the C+ ceiling + military-use-reversal framing that will land in every values-fit interview this fall — it pairs directly with [yesterday's ExploitGym incident](../2026-07-26/01-big-lab-moves.md#1-openai-exploitgym) as the new safety vocabulary.

*(Anthropic Fellows Nov 2026 deadline was 2026-07-26 11:59 PT — last night, as [`05` §1 of 07-26](../2026-07-26/05-career-and-startup.md#1-fellows-tonight) called out. If you submitted, mark it and move on; if you didn't, [`05` §1](./05-career-and-startup.md#1-fellows-postmortem) has the calendar for the next windows.)*

---

1. **Kimi K3 open weights released 2026-07-27 00:00 UTC.** Moonshot AI (Beijing). **2.8T sparse MoE**, native multimodal, 1M-token context, Modified MIT license. ~594GB checkpoint (INT4 quant ~1.4TB full-precision). Largest open-weight model ever public; independent testers report ~51% hallucination on the released weights vs. the hosted API. The **open-vs-closed gap on the Intelligence Index just tightened to single digits** — the open-frontier story you can point to in interviews. → [`01` §1](./01-big-lab-moves.md#1-kimi-k3) · [`03` §1](./03-practical-skills-and-tools.md#1-kimi-k3-run) `#kimi #moonshot #open-weights #moe`

2. **MCP 2026-07-28 stateless spec finalizes TOMORROW.** Sessions removed, OAuth 2.1 for connection, `Mcp-Method` / `Mcp-Name` per-request headers, MCP Apps + Tasks + Server Cards. Every server behind a plain round-robin LB with no sticky routing. **Do the migration PR tonight** — Wednesday it stops being a "shipped on day one" story. → [`03` §2](./03-practical-skills-and-tools.md#2-mcp-migration-day) · [2026-07-25/03 §2 the full server-author checklist](../2026-07-25/03-practical-skills-and-tools.md#2-mcp-migration) `#mcp #stateless #protocol #oauth`

3. **FLI Summer 2026 AI Safety Index (2026-07-07).** Anthropic **C+** (top; leads 5/6 domains), OpenAI **C**, Google DeepMind **C**, Meta **D+**, xAI **F**. **Between 2024 → 2026, Anthropic + OpenAI + DeepMind + Meta all reversed prior military-use restrictions** and began actively seeking defense contracts. The C+ ceiling is now the enterprise-buyer conversation and the framing you need for any AI-safety interview question. → [`01` §4](./01-big-lab-moves.md#4-fli-safety-index) · [`05` §3](./05-career-and-startup.md#3-safety-narrative) `#safety #fli #governance #defense`

4. **Google Gemini 3.6 Flash + 3.5 Flash-Lite + 3.5 Flash Cyber shipped 2026-07-21.** 3.6 Flash: 1M context, knowledge cutoff **March 2026**, **~17% fewer output tokens** than 3.5 Flash on the same task, higher on coding + long-context + computer-use benchmarks. **Pro is delayed** — Google's public admission that 3.5 Pro missed internal bars on coding and complex reasoning is the frame Wall Street will discount into Alphabet numbers next earnings. → [`01` §2](./01-big-lab-moves.md#2-gemini-36-flash) `#google #gemini #flash #pro-delayed`

5. **Together AI closed $800M Series C at $8.3B (2026-07-01), Aramco Ventures lead.** ~$1.15B annual bookings, plans to grow infra 50× over 5 years, 500 MW compute committed. The neocloud category is *the* infra winner of the open-weights escalation — pairs directly with tonight's Kimi K3 drop. → [`02` §1](./02-new-emerging.md#1-together-ai) `#together #open-source #neocloud #inference`

6. **EU AI Omnibus in force (July 2026): high-risk deadlines pushed to Dec 2027 / Aug 2028.** Annex III → 2 December 2027, Annex I → 2 August 2028. **Article 50 (GPAI transparency + synthetic-media labeling) stays strictly enforceable from 2 August 2026 — six days from today.** Any product you ship into the EU that surfaces AI-generated content needs the label in place by Sunday. → [`02` §3](./02-new-emerging.md#3-eu-omnibus) `#eu #ai-act #compliance #article-50`

7. **AI Engineer #1 fastest-growing US job (LinkedIn) — Agentic AI skills +587% YoY, AI Agents +503%, AI Infrastructure +366%.** Median AI engineer TC: **~$173K national → up to $795K at OpenAI**. Skills-gap ratio: **3.4 open positions per qualified candidate**. The skill line that matters for you this week is **Agentic AI + MCP + effort-routing** — literally the sentence [`03`](./03-practical-skills-and-tools.md) hands you. → [`05` §2](./05-career-and-startup.md#2-hiring-signal) `#hiring #agentic-ai #linkedin #comp`

8. **arXiv: AgentGym2 (2026-07-06) — LLM agents in *de-idealized* real-world environments.** Pre-packaged tool interfaces stripped; inputs are noisy; agents must handle multi-step failures. Top model pass-rate ~28% vs. 71% on prior idealized benches — a **~40-point sim-to-real gap.** The eval to cite when defending "agents don't work yet in production." → [`04` §1](./04-research-progress.md#1-agentgym2) `#arxiv #agents #benchmark #sim-to-real`

---

## One thing to DO this Monday

→ **File your MCP 2026-07-28 migration PR by tonight, tagged for tomorrow's spec ship.**
1. **Tonight (60 min) — draft the migration PR** on your public MCP server(s). Rip out `Mcp-Session-Id`, add OAuth 2.1, publish the Server Card at `/.well-known/mcp-server-card`, bump `MCP-Protocol-Version: 2026-07-28`. Full checklist: [2026-07-25/03 §2](../2026-07-25/03-practical-skills-and-tools.md#2-mcp-migration). Merge Tuesday when the spec lands. → [`03` §2](./03-practical-skills-and-tools.md#2-mcp-migration-day)
2. **Tonight (30 min) — Kimi K3 API smoke test** on 3 of your Claude-based agent prompts; log token-cost delta and answer-quality delta. This is a 45-minute portfolio artifact and an interview-ready A/B story. → [`03` §1](./03-practical-skills-and-tools.md#1-kimi-k3-run)
3. **This week (2h Wednesday) — write the "AI safety at C+" framing memo.** One page: what Anthropic's C+ actually means as a buyer, what the military-use reversal changes for enterprise procurement, what you'd advise a startup founder to say to a security-conscious customer. Answers the safety question that will hit you in every Anthropic FDE / Applied AI loop this fall. → [`05` §3](./05-career-and-startup.md#3-safety-narrative)

## Watchlist deltas since the 2026-07-26 edition (24 hours)

*One day, three timers matured plus one framing shift:*

- ✅ **Kimi K3 open weights** — dropped on schedule at 00:00 UTC. Weights are downloadable *now*; run the [smoke test](./03-practical-skills-and-tools.md#1-kimi-k3-run) tonight while it's fresh news. The ~51% hallucination gap between vanilla weights and hosted API is the *smart* observation to publish.
- ✅ **Anthropic Fellows Nov 2026 cohort** — deadline closed 11:59 PT last night. Postmortem in [`05` §1](./05-career-and-startup.md#1-fellows-postmortem); next windows are May 2027 + July 2027.
- ➡️ **MCP 2026-07-28** — spec finalizes tomorrow. The 07-26 [MCP guidance](../2026-07-26/03-practical-skills-and-tools.md#1-mcp-sunday-migration) told you to queue the PR yesterday morning; if you didn't, do it *now* — [`03` §2](./03-practical-skills-and-tools.md#2-mcp-migration-day) is the 60-minute recipe.
- 🆕 **FLI Summer 2026 Safety Index (07-07)** — surfacing today because the [ExploitGym incident from 07-26](../2026-07-26/01-big-lab-moves.md#1-openai-exploitgym) reframes it. C+ ceiling + military-use reversal + first documented sandbox escape = the *complete* AI-safety vocabulary you need for interviews.
- ➡️ **DeepMind talent exodus** — thread from [07-26 §2](../2026-07-26/01-big-lab-moves.md#2-deepmind-exodus). Combined with the [ex-AGI-Lab redistribution](./01-big-lab-moves.md#3-amazon-aftermath), the coffee-DM window (see [`05` §5](./05-career-and-startup.md#5-ex-agi-lab-coffee)) is unusually good this week.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Kimi K3 in [`01` §1](./01-big-lab-moves.md#1-kimi-k3) + MCP migration day in [`03` §2](./03-practical-skills-and-tools.md#2-mcp-migration-day) |
| 20 min | [`01` §1–4](./01-big-lab-moves.md) (Kimi K3 + Gemini 3.6 + AGI-lab aftermath + FLI Safety) + [`03` §1–2](./03-practical-skills-and-tools.md) (Kimi run + MCP migration) — the four signals that changed your week |
| Tonight | [`03` §2](./03-practical-skills-and-tools.md#2-mcp-migration-day) — MCP migration PR draft + Kimi K3 smoke test |
| Wednesday | [`05` §3](./05-career-and-startup.md#3-safety-narrative) — one-page "AI safety at C+" framing memo |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
