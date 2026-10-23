# TL;DR — 2026-10-04 (Saturday)

Sixty-second skim. **The week the "frontier" started hiring, cancelling, and acquiring instead of just shipping.** OpenAI pulled **GPT-6.1 Astra over alignment failures** at DevDay and shipped **GPT-6.1 Sol at 1/5 the price**, plus an **Agents API in public beta with computer use**, a **Decisions API in limited preview**, and a persistent-agent product called **Dots** — 20+ announcements in one keynote. **Anthropic committed $100M to the Claude Frontier Academy — train 10,000 FDEs by end of 2027** with Accenture · Deloitte · McKinsey · Morgan Stanley · Novo Nordisk as the first cohorts (the biggest hiring signal for your lane this entire quarter). **Claude Code shipped MODS Oct 1** — TypeScript plugins that intercept prompts, tool calls, permissions, and UI; **the agent itself is now the surface you customize.** Underneath, a **$2B+ funding week** hardens the agent-infrastructure stack: **Temporal $550M/$12.55B** (durable execution — OpenAI + JPM are customers), **Supabase $150M + acquires Turso** ("every agent its own database"), **Armadin $255.5M/$2.5B** (agent-swarm security), **Baselayer $35M** ("Know Your Agent" identity), **EliseAI $350M/$4B**, **FieldAI $700M/$10B** (universal robot brain), **Arcee $150M**. For you: **the agent-primitive thesis from May just added three concrete reference points — identity, database, durable execution — and your Frontier Academy wedge opened.**

---

1. **GPT-6.1 Astra cancelled; Sol ships at 1/5 the price.** OpenAI pulled **Astra over alignment failures** that surfaced in internal testing of its autonomous-agent capabilities, and shipped **GPT-6.1 Sol** instead — near-Astra intelligence at **1/5 the standard token prices**, error rate **11.4% → 7.7%**, more vocal about limitations, more reliable on safety constraints. Shipped alongside: **Agents API in public beta with computer use, hosted execution, memory, multi-agent support**; **Decisions API** (limited preview); **Dots** persistent agents with their own cloud computer; **8× faster token generation in Codex, 6× in the API**. → [`01` §1](./01-big-lab-moves.md#1-devday) `#openai #gpt-6 #alignment #agents-api`

2. **Anthropic $100M → Claude Frontier Academy → 10,000 FDEs by end-2027.** A funded, residency-structured ("simulated enterprise deployment → graded assessment → medical-residency-style casework → credential") pipeline for Field/Deployed Engineers, with cohorts drawn from **Accenture · Deloitte · McKinsey · Morgan Stanley · Novo Nordisk** and the broader Claude Partner Network. This is **the single clearest hiring signal of 2026 for the AI Integration Engineer / FDE lane** — Anthropic just put $100M behind making the credential exist. → [`01` §2](./01-big-lab-moves.md#2-frontier-academy) `#anthropic #fde #hiring #academy`

3. **Claude Code gets MODS — TypeScript plugins that rewrite the agent (Oct 1).** Small TS/JS modules that **intercept prompts before the model, block/retry tool calls, approve/deny permission requests, redact secrets, replace UI**. Ship inside plugins; share via the Claude directory; run with full local access (no sandbox). The 2026 Claude Code primitive map adds a 5th slot: **Hooks · Skills · Subagents · CLAUDE.md · Mods.** If you've been shipping agents in prompts, this is the Saturday project that moves you up a tier. → [`03` §1](./03-practical-skills-and-tools.md#1-mods) `#claude-code #mods #plugins #agent-primitives`

4. **Temporal $550M Series E @ $12.55B — durable execution is the infra moat for agents.** Co-led by **Lightspeed** (returning: a16z, Sequoia, Index, GIC, Sapphire); **ARR >$250M, growing 200% YoY, 4,300 paying customers including OpenAI + JPMorgan Chase.** Thesis: **agents break in production and need a workflow engine that survives failure.** The Series D in Feb was at $5B — valuation **2.5× in ~8 months.** → [`02` §1](./02-new-emerging.md#1-temporal) `#funding #agents #infrastructure`

5. **Supabase $150M + acquires Turso — "every agent gets its own database."** CapitalG (Alphabet's growth fund) led the round; Turso founder **Glauber Costa joins as Head of Agentic Services**; **70% of new Supabase databases now spin up from an AI tool** (up from 60% in June). First major **agent-native database primitive** acquisition. → [`02` §2](./02-new-emerging.md#2-supabase-turso) `#funding #agents #database`

6. **Baselayer $35M Series A — "Know Your Agent" (KYA) identity for banks + merchants.** M13 led; **2,000+ US FIs already on the base platform, >$1B fraud losses prevented**. The **Agentic Identity Suite** (first interoperable trust layer + agentic fraud consortium) with FIS / Prove / Socure as credential issuers. Confirms the **agent-primitive thesis** (payments → Natural in May, identity → Baselayer this week, database → Turso this week). → [`02` §3](./02-new-emerging.md#3-baselayer) `#funding #identity #agents #compliance`

7. **Armadin $255.5M Series B @ $2.5B — agent swarms for cyber.** Founded by **Kevin Mandia** (ex-Mandiant); **a16z + Accel co-led**. Confirms the **agentic-SOC** category started by Exaforce in May; **two $100M+ rounds in the category in 5 months**. → [`02` §4](./02-new-emerging.md#4-armadin) `#funding #security #agents`

8. **Research: "Heavy-Tailed Memory Traces in Long-Horizon Language Agents" (arXiv 2610.00010).** Agent memory concentrates on a small core; rare states live in a long tail where **prediction errors accumulate**. Authors propose **Core–Tail World Model (CTWM)** — a single-exponent rank-based memory controller — achieving **24.48% token reduction on LongMemEval with accuracy parity.** Accepted to the NeurIPS 2026 Interpreting-Agent-Behavior workshop. **Pair with the Mem0 2026 agent-memory survey** = your interview arsenal for Q4 FDE/MLE loops. → [`04` §1](./04-research-progress.md#1-heavy-tailed-memory) `#arxiv #memory #agents`

9. **Meta Muse Spark co-authored 6 math papers in one month — 5 answered open problems. All via the regular meta.ai chat UI.** Probability, differential equations, group theory (a 384-element group disproving a 2024 conjecture), optimization, arithmetic physics, non-associative algebra. **No custom research scaffolding — Thinking Mode on Muse Spark 1.1/1.2.** Companion to May's OpenAI/Erdős result, except now at **sustained collaboration scale, not single-shot.** → [`04` §2](./04-research-progress.md#2-muse-spark-math) `#research #math #meta`

10. **Career: AI engineer is officially LinkedIn's #1 fastest-growing US role for Q4 2026 — 14,801 US openings (Glassdoor) / 15,000+ on LinkedIn; median base $146K, senior $225–310K; top payers Meta · Apple · LinkedIn.** The **Frontier Academy credential is the mid-term career lever** — if you're in a Partner Network firm (Big-4, MBB, Morgan Stanley), you have a direct application path with a $100M-backed deliverable. → [`05` §1](./05-career-and-startup.md#1-hiring-map) `#careers #salary #academy`

---

## One thing to DO this Saturday

→ **Ship your first Claude Code mod + apply to one Frontier Academy sponsor.** The mod: a 30-line TypeScript plugin that intercepts `pre_tool_call` for Bash and redacts anything matching a secrets regex before it reaches the model. Push to GitHub, write a 400-word post ("why I built this"), link it on LinkedIn. **Then** apply to one Accenture / Deloitte / McKinsey AI-Engineer-track role, naming the mod in the cover letter — you can't apply to the Academy directly yet, so the apply surface is **the Partner Network firms it recruits from.** Details in [`03` §1](./03-practical-skills-and-tools.md#1-mods) + [`05` §2](./05-career-and-startup.md#2-frontier-academy-wedge).

## Watchlist deltas

- 🆕 **GPT-6.1 Astra cancelled over alignment:** new thread. First time a frontier lab has pulled a flagship over alignment failures *post-hoc* (vs. restricted-access gating like Mythos). Watch for Anthropic / Google parallel disclosures.
- 🆕 **Claude Frontier Academy / 10,000 FDEs:** new thread. Track first-cohort start dates (expected Q1 2027), credential name, external-vs-internal availability.
- 🆕 **Claude Code mods:** new thread. Watch for the first "killer mod" (security-audit mod, cost-router mod, test-harness mod) hitting 1K+ installs — that's the career artifact.
- 🆕 **Agent-primitive stack filling in:** payments (Natural, May) + identity (Baselayer, Oct 2) + database (Supabase+Turso, Oct 2) + durable execution (Temporal, Oct 1) = **four of the five core primitives funded in 2026.** Missing: agent-to-agent **comms/messaging** (Photon's $4.5M seed is early-stage) and **reputation/audit**.
- 🆕 **Shopify Canvas + DoorDash SMS agent:** consumer surfaces for agent commerce now live.
- ➡️ **OpenAI IPO (from 2026-05-22 / 2026-09-10):** reported valuation now **~$1.4T** per DevDay-week funding chatter; Anthropic likely still prices first.
- ➡️ **Model-routing/eval-authoring skills (from 2026-09-10):** reinforced — GPT-6.1 Sol at 1/5 Astra price adds a 6th routing lane.
- ⬇️ **"Which flagship is best this week" fluency:** still deprecated. The Astra cancellation underscores it — the model you picked Monday was pulled Thursday.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §2](./01-big-lab-moves.md#2-frontier-academy) (Frontier Academy — the career signal) |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) + [`03` §1](./03-practical-skills-and-tools.md#1-mods) (DevDay recap + the Claude Code mods decision tree) |
| Today | [`03` §1](./03-practical-skills-and-tools.md#1-mods) — ship the secrets-redaction mod |
| Tonight | [`05` §2](./05-career-and-startup.md#2-frontier-academy-wedge) — the Frontier Academy application path |
| Weekend | [`04` §1](./04-research-progress.md#1-heavy-tailed-memory) + [`04` §2](./04-research-progress.md#2-muse-spark-math) — the memory paper and the Muse Spark math set |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
