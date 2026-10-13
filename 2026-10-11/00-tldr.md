# TL;DR — 2026-10-11 (Sunday)

Sixty-second skim. **The week the "small model" line got re-drawn and the policy frame hardened.** On **Oct 7, Anthropic shipped Claude Haiku 5.5 at $0.10 in / $0.50 out per 1M tokens** (short prompts) — **~75% cheaper than Haiku 4.5** — with a 1M-token context window and the **first "effort levels" slider on a Haiku**. The same day, **OpenAI started rolling GPT-6 (Sol on paid, Luna on Free/Go) with "Intelligent UI"** across ChatGPT — answers can now include inline interactive charts, forms, buttons and task-tools, not just text. Nine days earlier, **the White House "Joint Commitment on Frontier Responsibilities"** was signed (Sept 29): voluntary, no penalties, external audit + board committee at each lab. Under the noise: **Q3 2026 AI absorbed ~$102B = 64% of global VC** (Crunchbase roundup; Instinct $1B / $10B, Armadin $255.5M / $2.5B, EliseAI $350M / $4B, Supabase $150M + Turso M&A). **For you: cheap-but-smart Haiku 5.5 just re-opened the "orchestrator + swarm" cost math — and Intelligent UI makes the "AI-as-interface-generator" wedge concrete overnight.**

---

1. **Claude Haiku 5.5 ships — 75% cheaper, 1M ctx, first Haiku with effort control.** $0.10 / $0.50 per 1M (≤100K-tok prompts); $0.50 / $2.50 above 100K. **Sonnet 5.5 cache reads also cut in half** the same release. Available Day 1 on API, Bedrock, Vertex, Microsoft Foundry. **One migration gotcha:** some sampling params (incl. assistant prefill) now return errors — update your SDK calls tonight. → [`01` §1](./01-big-lab-moves.md#1-haiku-55) `#anthropic #haiku #pricing #claude-code`

2. **GPT-6 + Intelligent UI rolls out to all ChatGPT tiers (Oct 7-8).** GPT-6 Sol on paid, GPT-6 Luna on Free/Go; Work and Codex unchanged for now. **Intelligent UI = answers composed of interactive components** (charts, calculators, maps, comparison tables, forms, buttons). OpenAI's claim: "~44% faster web-search answers vs GPT-5.6 Instant" (one source says 32% — verify on your workload). → [`01` §2](./01-big-lab-moves.md#2-gpt-6-intelligent-ui) `#openai #gpt-6 #ui #multimodal`

3. **The White House "Joint Commitment on Frontier Responsibilities" (Sept 29).** Trump + Amodei, Pichai, Zuckerberg, Brockman (OpenAI), Huang, Musk. Voluntary, "morally binding," no penalties. Each company commits to internal controls, an independent external auditor, and a board-level review committee. **AI Czar name coming "in the next few days."** → [`01` §3](./01-big-lab-moves.md#3-wh-accord) `#policy #governance #audits`

4. **Instinct $1B Series C @ $10B** (Sequoia · Benchmark · Coatue). The Sept $250M Series B at $2.5B just got re-marked 4× in ~6 weeks — same thesis (viral consumer agent + personal memory) now fully priced. → [`02` §1](./02-new-emerging.md#1-instinct-10b) `#funding #startups #consumer-ai`

5. **Armadin $255.5M Series B @ $2.5B+ (Oct 1, a16z + Accel).** AI-native **offensive security** — agents that find and exploit, continuously. **Pair-trade with the WH accord's audit requirement:** every lab now needs a red-team vendor they can expense. → [`02` §2](./02-new-emerging.md#2-armadin) `#funding #security #agents`

6. **EliseAI $350M Series F @ $4B (Oct 1, a16z + Bessemer); Supabase $150M + Turso acquisition (Oct 2); Flow Engineering $50M (Oct 3); OneByZero $20M (Oct 5).** Vertical SaaS + developer-infra are both bid. → [`02` §3](./02-new-emerging.md#3-rest-of-week) `#funding #vertical #devtools`

7. **Practical: the Haiku 5.5 "orchestrator + swarm" math is live again.** With Sonnet 5.5 driving + Haiku 5.5 at 1/10th the cost doing parallel tool-calls, workloads that were ~$0.08/task on Sonnet-only drop to ~$0.025 before caching — and the Sonnet cache-read cut halves that further. **Rebuild your cost-router this week, with Haiku-5.5 effort="low" as the new default tier below Sonnet-5.5.** → [`03` §1](./03-practical-skills-and-tools.md#1-haiku-swarm) `#claude-code #routing #cost`

8. **Practical: Intelligent UI = a 72-hour startup wedge.** If OpenAI can ship inline forms and calculators, so can your app via **MCP + generative UI**. The one-page product spec: "an assistant that returns calculators, not paragraphs, for X vertical." The 2026 Claude Code 4-primitive stack (Hooks · Skills · Subagents · CLAUDE.md) still holds — add a **"UI component tool"** to any Skill and you have the same primitive. → [`03` §2](./03-practical-skills-and-tools.md#2-ui-wedge) `#startups #ui #mcp #skills`

9. **Research: agents' evals go adversarial.** Analytics Vidhya's "Top 5 Agentic AI Papers of 2026" (updated Aug 22) locks in: **Agents' Last Exam** (long professional workflows), **ClawBench** (live-site web agents), **Code as Agent Harness**, **AutoResearchClaw**, and **AREX** (verification-driven deep research). Volume: ~9,000 agent papers to date, ~1,000/month pace; **safety + alignment the fastest-growing arXiv sub-track.** → [`04` §1](./04-research-progress.md#1-top-5-agentic) `#arxiv #agents #evals #safety`

10. **Career: MLE market holds ~490 postings/wk H1 2026 (Axial, 13,776 US postings).** AI-engineering broader: ~1,550 postings/wk, median base **$176K**. **Supply crunch: ~1.6M open AI roles vs ~518K qualified candidates, ~5-mo avg time-to-fill.** → [`05` §1](./05-career-and-startup.md#1-hiring) `#careers #mle #ai-engineer #hiring`

11. **The re-price of the week:** cheap-small-model skills ↑ (Haiku 5.5 makes "swarm the problem" a default pattern), **generative-UI skills ↑** (Intelligent UI legitimized the surface), **"just use Opus for everything" patterns ↓**. The scarce engineer builds routing + UI-tool-returning agents, not single-model wrappers. → [`05` §2](./05-career-and-startup.md#2-reprice) `#skills #careers`

---

## One thing to DO this Sunday

→ **Ship a 50-line "Haiku-swarm orchestrator" and record a 90-sec demo.** Sonnet-5.5 planner routes to N Haiku-5.5 workers (effort="low"), returns a merged answer with inline cost + wall-clock. Publish repo + demo. **This is the artifact that answers "did you touch the Oct 7 pricing drop?"** Details in [`03` §1](./03-practical-skills-and-tools.md#1-haiku-swarm).

## Watchlist deltas

- 🆕 **Haiku 5.5 "effort levels":** new thread. First time a cheap Anthropic model has the Opus/Sonnet effort slider — watch for pricing-tier re-shuffling across the ecosystem.
- 🆕 **Intelligent UI as a new interaction primitive:** new thread. Track which labs ship their counter (Google Gemini agent + sub-agents in preview; Anthropic's "Artifacts" overlap is the obvious comparator).
- 🆕 **White House Joint Commitment:** new thread. Watch the AI Czar announcement, the named external auditors, and whether California / NY add penalty clauses on top.
- 🆕 **Q3 2026 = $102B / 64% of global VC into AI** (Crunchbase roundup) — AI vs non-AI venture is now a ~2:1 split in dollars.
- ➡️ **Anthropic IPO (from 2026-09-10):** no new filing this week; Haiku 5.5 pricing cut reads as pre-S-1 ARR expansion.
- ➡️ **Apple v OpenAI (from 2026-09-10):** Oct 1 hearing happened, no sanctions reported in our sources — monitor Davila's docket next.
- ⬇️ **"Latest model fluency":** still deprecated (per 2026-09-10) — reinforced by GPT-6 + Haiku 5.5 landing the same week.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-haiku-55) (Haiku 5.5) + [`01` §2](./01-big-lab-moves.md#2-gpt-6-intelligent-ui) (GPT-6 + UI) |
| 20 min | [`03` §1–2](./03-practical-skills-and-tools.md) — the Haiku-swarm math + the generative-UI wedge |
| Today | [`03` §1](./03-practical-skills-and-tools.md#1-haiku-swarm) — build and publish the orchestrator |
| Tonight | [`04` §1](./04-research-progress.md#1-top-5-agentic) — the agentic-eval papers for interview talk-tracks |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
