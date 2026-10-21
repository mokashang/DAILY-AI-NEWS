# TL;DR — 2026-10-03 (Saturday)

Sixty-second skim. **Three stories converged this week and they rewrite the second-half-of-2026 playbook.** (1) **Anthropic's S-1 leaked (Sept 29)** — the thesis this repo has tracked since May is now a prospectus: **$4.59B 2025 revenue, $11.5B in a single Q2 2026 quarter, $42B GAAP net loss (mostly a $34B non-cash convertibles revaluation), $518B of future compute obligations, $20.28B cash, dual-class founder control, two customers = ~24% of revenue, potential $2T valuation on listing (eyed November)**. (2) **OpenAI DevDay 2026 (Sept 29–Oct 1) shipped 20+ announcements** — the headline is **Dots** (always-on agents with a dedicated cloud PC), **GPT-6.1 Sol** at **⅕ the price of Astra** with Astra-approaching performance, **Ultrafast** speed tier (up to **8× faster Codex at 300 tok/s**), **ChatGPT Space** (shared human+agent workspace), **$500/mo Pro plan**, Agents API gets **computer use + multi-agent + tool search**. (3) **Claude Code `mods` shipped (Oct 1)** — TypeScript hooks that rewrite prompts, block tools, redact secrets, replace UI — **but not sandboxed; they can read your API key.** The practical reprice: **agent extensibility and persistent-agent cost control are now the two interview questions that matter.** For you: fork the TypeScript mod examples tonight.

---

1. **Anthropic S-1 leaked — the first frontier-lab IPO prospectus is public (unofficially).** $4.59B 2025 rev → **~12× YoY**; **Q2 2026 alone ~$11.5B**; **$8.06B operating loss**, **$42B GAAP net loss (mostly non-cash $34B convertibles revaluation)**; **$518B future cloud/compute obligations** disclosed; **$20.28B cash**; **two customers = ~24% of revenue** (concentration risk); **dual-class founder control for 7 co-founders**; **November listing eyed, up to ~$2T valuation.** → [`01` §1](./01-big-lab-moves.md#1-anthropic-s1) `#anthropic #ipo #s-1 #public-markets`

2. **OpenAI DevDay 2026 — Dots + GPT-6.1 Sol + Ultrafast + ChatGPT Space + $500/mo Pro.** **Dots** = always-on agent with its own cloud PC that works through Slack/Teams on evolving projects. **GPT-6.1 Sol** approaches Astra on evals at **⅕ the input/output price.** **Ultrafast** hits **300 tok/s in Codex (8× faster), 6× faster in API.** **ChatGPT Space** = shared workspace where humans + agents share context. **Agents API** adds computer use, multi-agent, tool search, context compaction. → [`01` §2](./01-big-lab-moves.md#2-openai-devday) `#openai #devday #agents #gpt-6-1 #ultrafast #dots`

3. **Claude Code `mods` — the extension surface changed.** TypeScript function hooks (Claude Code **v2.1.287+**) that rewrite prompts, block/retry tool calls, approve/deny permissions, redact secrets, edit UI; ship inside plugins, install with `/plugin`. Official examples: **Token Weather** (live ctx-window forecast), **Blast Radius** (dry-run dangerous commands), **Replay Theater** (step through edits). **Security:** mods are **NOT sandboxed** — a mod can read your `ANTHROPIC_API_KEY` and anything in env. Install only from sources you trust. → [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-mods) `#claude-code #mods #plugins #extensibility #security`

4. **Claude for Government — FedRAMP High GA.** Coding + agentic work for federal + state agencies with spend controls, audit logs, desktop file support; Claude Code CLI and Claude for Microsoft 365 in early access. Opens a government-adjacent FDE lane most new grads aren't pricing yet. → [`01` §3](./01-big-lab-moves.md#3-claude-government) `#anthropic #government #fedramp`

5. **Microsoft counter-programs: Autopilot (upgraded Scout) + Copilot Code.** Autopilot = **digital coworker with configurable permissions**; Copilot Code = natural-language apps + dashboards. Classic Microsoft play: launch six months after the frontier shows the pattern, bundle into every seat, win on distribution. → [`01` §4](./01-big-lab-moves.md#4-microsoft-autopilot) `#microsoft #copilot #autopilot`

6. **Amazon Ads Agent + agentic commerce as an unlock category.** Amazon Ads + DVA (ex-DSP) unified into a context-maintaining **Ads Agent**; AI-assisted campaign setup now default. First mainstream **agent-mediated commerce** platform at scale — the "Natural $30M" thesis from [2026-09-10/02](../2026-09-10/02-new-emerging.md#2-natural-agent-payments) just got a $1.5T buyer. → [`02` §1](./02-new-emerging.md#1-amazon-ads-agent) `#amazon #agentic-commerce #ads`

7. **Earendil Pi 1.0 + a wave of MCP-native agent harnesses.** MIT-licensed hardened harness with **Codemode + native MCP + non-LLM backends** (image/vision models side-by-side with LLMs), **virtual-model extensions, deferred tool loading, Anthropic cache warming, mid-conversation system messages.** Plus **Yedric** (one-script-tag agent for existing SaaS) and **aweb** (open comms layer with stable agent identities). Pattern: **MCP went from "a protocol" to "an ecosystem" in six weeks.** → [`02` §2](./02-new-emerging.md#2-mcp-harness-wave) `#mcp #agents #harness #earendil`

8. **arXiv: three agent-safety primitives landed this week — PACE, TRACE, DeFA.** **PACE** = provenance-aware capability enforcement for tool-using LLM agents (prevents tool/memory poisoning). **TRACE** = trajectory return attribution + contrastive erasure for multi-turn safety. **DeFA** = dependency-guided failure attribution across agent execution. Plus "**Verify Claims, Not Scores**" argues aggregate benchmarks can't localize which component lost value → **component-level eval is the next frontier.** → [`04` §1](./04-research-progress.md#1-agent-safety-trio) `#arxiv #agents #safety #evals #provenance`

9. **AI engineer job market: 500K+ open AI/ML roles globally, 63% talent shortage — but entry-level generalist SWE down 25% YoY, new-grad top-tech hires down 50%+.** MLE new-grad base $90–135K; LLM-specialist base $220–280K (from 2026-09-10). The split is now operational: **AI/ML lane open, generalist SWE lane closed.** Companies shift from PhD-required to portfolio-and-practical. → [`05` §1](./05-career-and-startup.md#1-labor-split) `#careers #hiring #new-grad #ml-engineer`

10. **The reprice of the week:** **Mods-authoring (TypeScript, Claude Code) + Dots-equivalent persistent agent design + GPT-6.1-Sol-vs-Astra cost-routing** are the three interview-ready skills that didn't exist 8 days ago. **The router artifact from [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) just needs GPT-6.1 Sol added as a row** — one evening of work. → [`05` §2](./05-career-and-startup.md#2-reprice) `#skills #careers #routing #mods`

---

## One thing to DO this Saturday

→ **Fork `claude-code/mods-examples`, write ONE mod of your own (even a 20-line one), publish it as a plugin, and record a 60-second demo gif.** Candidate wedges: (a) a **cost-router mod** that automatically swaps model-ID to GPT-6.1 Sol / Fable 5.1 by task type (ties the router artifact to Claude Code directly); (b) a **secrets-redaction mod** that scrubs `AWS_*` / `OPENAI_API_KEY` / cookies from tool output (addresses the "not sandboxed" security concern head-on); (c) an **S-1-signal mod** that posts a chart of your project's weekly Claude spend (your own personal billing audit artifact from [ME.md](../ME.md), finally shipped). Any one of these is a Monday-morning LinkedIn post. Full build steps: [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-mods).

## Watchlist deltas

- 🟢 **Anthropic IPO** — **S-1 LEAKED Sept 29.** Reset the thread with the real numbers; now a public-market event. Watch for official filing + the SEC's "quiet period" clock starting.
- 🆕 **Dots as a new product category** — "persistent cloud-PC agent with ongoing responsibilities" is now a distinct SKU with pricing; expect Anthropic + Google parity within 60 days.
- 🆕 **GPT-6.1 Sol at ⅕ of Astra pricing** — the second major 2026 inference-price cut (after Fable 5.1 cache reads). Rerun your cost dashboard this weekend.
- 🆕 **Claude Code mods ecosystem** — new primitive. Watch the first 10 breakout mods on the directory; whichever gets the most installs is the Hacker News thread of November.
- 🆕 **Agent-safety research consolidation** — PACE/TRACE/DeFA + "Verify Claims Not Scores" together argue the eval frontier moves from end-to-end scores to **component-level provenance + attribution.**
- ➡️ **Model fatigue (from 2026-09-10):** confirmed and amplified. Enterprise contracts starting to add cadence clauses (per Dealroom + CNBC follow-ups).
- ⬇️ **"Build a chatbot with the frontier model"** as an interview artifact — **further** deprecated. Replace with (router + mod + persistent-agent design) triple.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-s1) (Anthropic S-1) + [`01` §2](./01-big-lab-moves.md#2-openai-devday) (DevDay) |
| 20 min | [`03` §1–3](./03-practical-skills-and-tools.md) — mods playbook + GPT-6.1 Sol routing update + persistent-agent design |
| Today | [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-mods) — fork mod examples, ship one, record a gif |
| Tonight | [`04` §1](./04-research-progress.md#1-agent-safety-trio) — PACE / TRACE / DeFA so you can quote them in the FDE loop next week |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
