# TL;DR — 2026-09-20 (Sunday)

Sixty-second skim. **The 10 days since [2026-09-10](../2026-09-10/) resolved the two biggest open threads of the year at once: Anthropic picked its IPO venue (Nasdaq, October, $800B–$2T range with Goldman + Morgan Stanley + JPMorgan on the book), and Anthropic published the first hard number on "Claude builds Claude" — Claude now *leads* 26% of Anthropic's R&D, with ~30,000 internal agents running at any moment and one in every ~47,000 actions blocked by an online monitor.** Under that: the first real vertical-Claude launch that ships with capital-markets partners on day one (**Claude for Financial Advisors**, Sept 14 — BlackRock, Charles Schwab, Addepar, Envestnet, Vanguard, Morningstar, S&P Global), a threat-intelligence report that names **China / Iran / Russia weapons-development attempts on Claude** (hypersonic vehicle drafts, kamikaze-drone swarms, targeting rosters), **Novo Nordisk × Claude Science** for drug discovery, **OpenAI's first Sponsored Agents inside ChatGPT** (Wayfair + Angi — the agent-ad primitive lands), **Meta quietly abandoned Project OT** (its own AI-driven layoff plan; the AI wasn't good enough), and **T-9 to OpenAI DevDay 2026 (Sept 29, Fort Mason SF)**. For you: **the "Claude builds Claude" number and the Anthropic S-1-in-October arc are the two most legible career-planning signals of 2026** — and Sunday is the day to pre-stage a DevDay watch-list + finish this week's portfolio push.

---

1. **Anthropic picks Nasdaq — October IPO, $800B–$2T range.** Bloomberg / QZ / Business Today / Yahoo Finance all confirm: **Anthropic chose Nasdaq for its planned IPO, October target**, Goldman + Morgan Stanley + JPMorgan bookrunners. Reported ranges vary from **$800B (Yahoo) through the current $965B post-money to as high as $2T (Business Today, Reuters cite)**. With **$30B+ revenue run-rate and 1,400% YoY growth**, an operating profit is projected this quarter. → [`01` §1](./01-big-lab-moves.md#1-anthropic-nasdaq) `#anthropic #ipo #nasdaq #public-markets`

2. **"Claude builds Claude" now has a number: 26% (Sept 17–18 disclosure).** Anthropic disclosed Claude *leads* — completes end-to-end from a high-level prompt, under human supervision — **26% of internal R&D as of August 2026, up from 0% in February.** **~30,000 agents** run concurrently; **~1B decisions in August**, **1-in-47,000 (0.002%) blocked** by an online monitor; **100% reviewed post-hoc offline.** Third-party evaluators being embedded in the company. → [`01` §2](./01-big-lab-moves.md#2-claude-builds-claude) `#anthropic #agents #safety #recursive-improvement`

3. **Claude for Financial Advisors — vertical #2, capital-markets edition (Sept 14).** After Legal (May) and Small Business (May), Anthropic ships **Claude for Financial Advisors**: pre-wired connectors to **Schwab, BlackRock, Addepar, Envestnet, iCapital, Orion, Wealthbox, Wealth.com, Vanguard, Zocks, FactSet, S&P Global, Morningstar**. **$70–120/user/month.** Human-in-loop kept for investment recommendations + client comms. → [`02` §1](./02-new-emerging.md#1-claude-financial-advisors) `#anthropic #vertical #finance #wealth`

4. **Anthropic threat report (early Sept) names China / Iran / Russia weapons attempts on Claude.** China-linked draft of a **Chinese-language technical proposal for an anti-torpedo weapon** with Claude playing critical reviewer; a Yemen-based cell drafted **rocket guidance software + a hypersonic glide vehicle concept**; a Russia-based team tried to build a **swarm of autonomous kamikaze drones**; Iranian actor built **a U.S. Navy personnel targeting roster** with commercial satellite-imagery query scripts. → [`01` §3](./01-big-lab-moves.md#3-threat-report) `#security #national-security #weapons #biosec`

5. **Novo Nordisk × Anthropic — Claude Science lands its first big-pharma logo (Sept 16).** Novo Nordisk will use Anthropic's frontier models + Claude Science in R&D. Novo has already built **NovoScribe** on Claude — clinical study reports in minutes not months. Anthropic's life-sciences head names **"neglected diseases traditional biopharma won't touch"** as the wedge. → [`01` §4](./01-big-lab-moves.md#4-novo-anthropic) `#pharma #drug-discovery #science #anthropic`

6. **OpenAI ships Sponsored Agents inside ChatGPT — Wayfair + Angi first (Sept 16).** The **agent-ad primitive** is live: paid-placement agents surface inside ChatGPT flows. This is the **cleanest contrast yet with Anthropic's ad-free pledge** — two frontier labs, two opposite business models, both going public in Q4. → [`01` §5](./01-big-lab-moves.md#5-openai-sponsored-agents) `#openai #ads #agents #chatgpt`

7. **Gemini Enterprise adds agent-spend caps + $0 base tier + PAYG (Sept mid-week).** Google shipped **pay-as-you-go pricing, up to 20% token discounts, monthly caps on per-agent spending, and a zero-dollar base subscription** for Gemini Enterprise — the first public-cloud agent platform to publish cost-control primitives as a *product feature*, not an afterthought. → [`02` §2](./02-new-emerging.md#2-gemini-enterprise) `#google #gemini #agents #cost-control`

8. **Practical: context engineering is the new prompt engineering.** The 2026 practitioner consensus (Sourcegraph, Neo4j, mem0, DEV Community, Towards AI): the skill is no longer *word choice inside a prompt* — it's **what you put in the context on every call.** Six techniques matter (hybrid sliding window, structured memory, tool-def hygiene, RAG budget, cache-anchored system prompts, ablation-tested compression). One line to steal tonight: **stop LLM-generating your context files** (Gloaguen 2026 — degraded performance vs. hand-authored). → [`03` §1](./03-practical-skills-and-tools.md#1-context-engineering) `#context-engineering #agents #memory #cost`

9. **Claude Code Sept 2026 changelog — three quiet wins.** (a) **`syncClaudeAiSkills` / `syncClaudeAiPlugins`** — your claude.ai skills + plugins now sync to terminal sessions; (b) **`/plugin install --marketplace <source>`** adds the marketplace at install time; (c) **subagent MCP-tool prompt-caching bug fixed** (resumed subagents no longer re-render MCP defs and break caching). Run `claude --upgrade` this evening. → [`03` §2](./03-practical-skills-and-tools.md#2-claude-code-changelog) `#claude-code #skills #plugins #mcp`

10. **arXiv: agent-memory + MCP-agent evaluation moved from "papers" to "benchmarks with error taxonomies."** **MCPAgentBench** (2512.24565 — 33 real MCP servers × 188 tools × 600 queries), **MCPEvol-Bench** (2607.14642 — dynamic MCP evolution), **StructMem** + **ContextBudget** + **Agent Zero Memory (2608.29606)** — memory is now a first-class architectural component with its own benchmark suite. → [`04` §1](./04-research-progress.md#1-mcp-benchmarks) · [`04` §2](./04-research-progress.md#2-memory-benchmarks) `#arxiv #mcp #memory #benchmarks`

---

## One thing to DO this Sunday

→ **Pre-stage your OpenAI DevDay (Sept 29) watch-list this afternoon (60 minutes).** DevDay is T-9 days. Draft a **one-pager with 5 predictions and their confidence levels** (my defaults: (i) a stable "GPT-6 Astra" API tier repricing, (ii) an Agents SDK 2.x with a Managed-Agents-shaped runtime, (iii) an official ads/monetization SDK for the Sponsored Agents primitive, (iv) a Codex-in-mobile expansion, (v) a voice or realtime API update). Publish it to your GitHub before Sept 29. **The grading-on-Sept-30 doc is a lightweight interview artifact — it proves "watches the frontier, writes it down, gets graded"** which is the exact skill FDE / AI-Engineer / Solutions hiring managers evaluate. Details in [`03` §3](./03-practical-skills-and-tools.md#3-devday-watchlist).

## Watchlist deltas

- 🟢 **Anthropic IPO — venue confirmed:** Nasdaq (Sept 13/14), Goldman + Morgan Stanley + JPMorgan. Watch for the S-1 filing date and revenue-line-item split (Claude Code vs. Verticals vs. Enterprise API).
- 🆕 **Claude builds Claude — 26% and rising:** new thread. Watch the monthly disclosure cadence and whether the "% led by Claude" number crosses 50% before year-end.
- 🆕 **Anthropic Threat Intelligence Report as a recurring publication:** new thread. Sept 2026 is the first named quarterly report — watch for the Dec 2026 issue and whether Google/OpenAI publish equivalents.
- 🆕 **Vertical-Claude cadence:** Legal (May) → Small Business (May) → Financial Advisors (Sept) — track the next verticals (Healthcare + Government + Education are the leading candidates given the Gates + Novo signals).
- 🆕 **OpenAI Sponsored Agents live:** new thread — track advertiser count, categories, and click-through disclosure.
- 🆕 **OpenAI DevDay T-9 (Sept 29):** new thread — track leaks and prediction accuracy.
- ➡️ **Anthropic S-1 (from [2026-05-22](../2026-05-22/)):** venue resolved, filing pending.
- ➡️ **1,100-employee pacing petition (from [2026-09-10](../2026-09-10/)):** July 28 letter, Anthropic + OpenAI corporate endorsement within 24h (Washington Post) — now context, not news.
- ⬇️ **Latest-model-fluency skill:** further deprecated. Context-engineering + eval-authoring + model-routing are the H2 stack.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-nasdaq) (Nasdaq IPO) + [`01` §2](./01-big-lab-moves.md#2-claude-builds-claude) (Claude builds Claude) |
| 20 min | [`03` §1–3](./03-practical-skills-and-tools.md) — context engineering + Claude Code changelog + DevDay watch-list |
| Today | [`03` §3](./03-practical-skills-and-tools.md#3-devday-watchlist) — publish your DevDay predictions doc |
| Tonight | [`04` §1](./04-research-progress.md#1-mcp-benchmarks) + [`04` §2](./04-research-progress.md#2-memory-benchmarks) — the MCP + memory benchmark set |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
