# TL;DR — 2026-10-02 (Friday)

Sixty-second skim. **The race just inverted twice in 72 hours.** On the capability side, **Google shipped Gemini 4 Argon** (Sept 30) and immediately took the **#1 slot on the Vals Index at 68.90%** — Google is credibly "back at the frontier" for the first time this year. On the business side, **Anthropic pushed its IPO from October to mid-November at a reported ~$2T valuation** (would be the largest IPO of all time) while **OpenAI ruled out an IPO for 2026** entirely — Altman cited AI safety concerns and switched to a **$30B bridge round at ~$1.4T**. Meanwhile **OpenAI DevDay dropped "Dots" (persistent ChatGPT agents) + GPT-6.1 Sol + computer use in the Agents API + Decisions API + plugin extensions + ChatGPT Space**, and **Amodei's "slow the pace" essay** got a public endorsement from Altman — the first time the two frontier CEOs have aligned on anything substantive. For you: **the pacing truce + the Google re-entry + the Dots primitive together re-price three skills — multi-model routing (up), persistent-agent architecture (up sharply), and "which lab is winning" fluency (down to zero).**

---

1. **Google Gemini 4 Argon — #1 on the Vals Index, Google back at the frontier (Sept 30).** 68.90% on Vals (41 tests), beating Claude Sonnet 5.5 (67.04%), Claude Opus 5.5 (66.97%), and Claude Fable 5.1 (65.83%). **Ties GPT-6 Astra at 53 on the Artificial Analysis Intelligence Index.** 1M-token context, 262K max output. **Promotional pricing $2/M input · $10/M output + 5% cache discount** (reverts to $4/$20 after promo). First Google flagship since February. → [`01` §1](./01-big-lab-moves.md#1-gemini-4-argon) `#google #gemini #frontier #benchmarks`

2. **Anthropic IPO slips to mid-November at ~$2T; OpenAI pulls out of 2026 entirely.** Anthropic now targeting roadshow the week of Nov 9 — would be the largest IPO of all time. **OpenAI's Altman: "ill-advised moment to go public"** citing AI safety; raising **$30B bridge at $1.4T** instead. Anthropic 2025 revenue **$4.6B (12×)**; order-of-market from the Sept 10 edition **inverts again** — Anthropic now goes alone. → [`01` §2](./01-big-lab-moves.md#2-ipo-split) `#anthropic #openai #ipo #public-markets`

3. **OpenAI DevDay — Dots, GPT-6.1 Sol, computer use, ChatGPT Space.** **Dots = persistent agents inside ChatGPT** with their own cloud computer, connected apps, and (coming) texting + teams-of-Dots. **GPT-6.1 Sol** at 1/5th Astra's token price; **8× faster in Codex, 6× in API**. **Agents API public beta** with hosted execution + memory + multi-agent; **Decisions API in limited preview** (Luna-powered classifier/router); **plugin extensions** = full apps in ChatGPT with directory; **ChatGPT Space + Pages** for teams and agents to share project context. → [`01` §3](./01-big-lab-moves.md#3-openai-devday) `#openai #devday #agents #gpt-6-1`

4. **Amodei + Altman agree: slow the pace.** Amodei's weekend essay (Sept 12 cycle, now surfacing in Oct 2 coverage): AI labs should "collectively slow development" because a coordinated swarm of agents could "take over the internet in 6–12 months." **Altman endorsed hours later** ("I agree with Dario that we need to pace the frontier") and said OpenAI would adopt one of Amodei's safeguards. First real alignment between the two CEOs. Proposed: embedded external safety testers + common standards among democratic nations + international agreements. → [`01` §4](./01-big-lab-moves.md#4-pacing-truce) `#safety #pacing #policy #governance`

5. **MCP donated to the Agentic AI Foundation.** Co-founded by **Anthropic, Block, OpenAI**; backed by **Google, Microsoft, AWS, Cloudflare, Bloomberg**. MCP is now a cross-lab commons rather than an Anthropic-stewarded protocol — the single biggest change to its governance since launch, and a hard proof that MCP is the industry default (consistent with WebMCP in Chrome back in May). → [`02` §1](./02-new-emerging.md#1-mcp-foundation) `#mcp #open-standards #agents`

6. **Funding barbell holds — Rhoda AI $450M Series A, 8090 Solutions $135M, Sail Research $80M.** **Rhoda AI** = FutureVision robotic-intelligence platform (video-predictive control); **8090 Solutions** = enterprise multi-agent dev platform (Chamath Palihapitiya CEO), Salesforce-led; **Sail Research $80M at $450M** = inference infra for hour/day-long agent runs. Theme: **long-horizon agent runtime is the funded wedge.** → [`02` §2](./02-new-emerging.md#2-funding) `#funding #agents #robotics #inference`

7. **Practical: the Argon-vs-Fable-vs-Sol routing update.** With Argon at $2/$10 promo + top of Vals, your router's weights change this week. **New rule-of-thumb**: Argon for coding + long-context + enterprise agents; Fable 5.1 for cached-heavy conversational agents (still cheapest on cache reads post-Sept-1 discount); Sol-6.1 for computer-use + Codex-style async workloads (1/5 Astra token price). The router artifact from the Sept 10 edition **re-fits in <30 min** with the new numbers; publish v2 by Monday. → [`03` §1](./03-practical-skills-and-tools.md#1-router-v2) `#routing #pricing #evals`

8. **Practical: Claude Code "deferred tool loading" shipped — load 50+ MCP tools without context tax.** Claude Code now loads tool *names* at startup and fetches schemas on demand via ToolSearch. **Order-of-magnitude context savings** when running many servers; also: **MCP streamable HTTP + OAuth 2.1 with PKCE** for remote servers (no more local stdio-only). Pair with the 4-primitive rule (CLAUDE.md / Skills / Hooks / Subagents) from Sept 10. → [`03` §2](./03-practical-skills-and-tools.md#2-claude-code-mcp-mature) `#claude-code #mcp #skills`

9. **Research: the agent-memory benchmark wave.** **DolphinBench (arXiv 2609.24971, Sept 21)** — 3 knowledge-work personas × ~500K user-message tokens each, maps the **Pareto frontier of agent memory**. **MemoryArena, EverMemBench, HaluMem, AMA-Bench, RealMem, StreamMemBench** all land in Sept–Oct. "Near-saturated LoCoMo models drop to **40–60%** on interdependent multi-session tasks." Memory is now the eval-authoring frontier — exactly where the career skill premium is. → [`04` §1](./04-research-progress.md#1-memory-wave) `#arxiv #agents #memory #evals`

10. **Career re-price:** **AI/ML engineer talent shortage now 63% with 500K+ open roles globally;** US median AI-engineer TC **$242K**, frontier labs materially higher (Anthropic **$300–490K**, OpenAI median **~$795K**, Meta **$430K**, Google **$290K**). SWE generalist roles **-25% from 2023 peak**. **Dots + persistent-agent architecture** = the fresh niche the market hasn't priced yet — carve it into your portfolio this weekend. → [`05` §1](./05-career-and-startup.md#1-salary-map) `#careers #salary #hiring`

---

## One thing to DO this Friday

→ **Ship router v2 tonight + add a "memory lane" to it tomorrow.** v2 adds Gemini 4 Argon to the routing table and re-runs your 5-case eval. Then add a 6th case: multi-session interdependent memory (steal a 2-persona subset from DolphinBench). The combined artifact = **"router + memory eval"** is the single scarcest thing in the AI-engineer hiring market right now — because it's the one artifact that answers both "which model" and "how do you prove it kept the thread" in interview. Details in [`03` §1](./03-practical-skills-and-tools.md#1-router-v2) and [`04` §1](./04-research-progress.md#1-memory-wave).

## Watchlist deltas

- 🆕 **Google back at the frontier:** new thread. Argon #1 on Vals + ties Astra on AAII = Google is a credible top-3 again. Watch for Antigravity 2.1 / Vertex Agent Platform updates in the next 30 days.
- 🆕 **Pacing truce (Altman + Amodei):** new thread. First substantive public alignment between the two CEOs. Watch for actual policy artifacts (embedded testers? joint standards?) in Q4.
- 🆕 **MCP Foundation governance:** new thread. If the foundation adds a competing lab (Mistral? xAI?) to the board, MCP's neutrality thesis strengthens; if Anthropic retains spec-votes majority, it's branding only.
- 🆕 **Dots as persistent-agent primitive:** new thread. Compare roadmap to Anthropic Managed Agents + Google Antigravity Managed Agents — all three now have a competing "cloud-resident agent" story.
- ➡️ **Anthropic IPO (from 2026-09-10):** slipped Oct→mid-Nov; valuation doubled to ~$2T; **OpenAI order flipped — OpenAI now explicitly NOT in 2026.**
- ➡️ **Model-fatigue (from 2026-09-10):** eased slightly — only one frontier release in the last 72 hours — but Dots + Argon raise the *primitive* count instead.
- ⬇️ **"Which lab is winning" as a career skill:** deprecated hard this week. Argon took #1 one month after Fable 5.1 took it from Opus. Nobody is winning for more than 30 days.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-gemini-4-argon) (Argon) + [`01` §2](./01-big-lab-moves.md#2-ipo-split) (IPO split) |
| 20 min | [`03` §1–2](./03-practical-skills-and-tools.md) (router v2 + Claude Code MCP maturity) |
| Today | [`03` §1](./03-practical-skills-and-tools.md#1-router-v2) — ship router v2 before you log off |
| Weekend | [`04` §1](./04-research-progress.md#1-memory-wave) — read DolphinBench, add the memory lane to your eval suite |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
