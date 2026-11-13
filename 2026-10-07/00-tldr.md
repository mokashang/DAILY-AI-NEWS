# TL;DR — 2026-10-07 (Wednesday)

Sixty-second skim. **The DevDay anniversary made the agent-SDK fight explicit, and the browser became the next OS fight.** One year after Anthropic shipped MCP, OpenAI responded on **Oct 6, 2025** with **AgentKit + Apps SDK (both MCP-based) + GPT-5 Pro + Sora 2 in the API**, and a **~6GW / up-to-10% AMD stake** that re-prices OpenAI's compute runway. Two weeks earlier, Anthropic shipped **Claude Sonnet 4.5 + the Claude Agent SDK + Claude Skills** (Sept 29) — the first "coding model that holds a 30-hour agentic session." Then on **Oct 21** OpenAI shipped **ChatGPT Atlas**, a Chromium browser with an agent-mode side panel. For you: **the two SDK stacks (Claude Agent SDK vs OpenAI AgentKit) are now the Q4 interview-differentiator**; the FDE / AI-Integration-Engineer lane just got firmer (Indeed: **+729% YoY FDE postings**); and **model-routing + eval-authoring are still the two scarce skills** carried over from Sept.

---

1. **OpenAI DevDay 2025 (Oct 6) — the biggest single-day re-weight of the stack this year.** Shipped: **GPT-5 Pro** (API-only reasoning tier), **gpt-realtime-mini** (cheaper voice), **Sora 2 in the API** (synchronized audio), **AgentKit** (visual Agent Builder + ChatKit + evals), **Apps SDK on MCP** (first partners: Booking, Canva, Coursera, Expedia, Figma, Spotify, Zillow), and a **~6GW AMD Instinct deal with up-to-10% equity warrant** (AMD +23.7% on the day). → [`01` §1](./01-big-lab-moves.md#1-openai-devday-2025) `#openai #agentkit #devday #amd`

2. **Claude Sonnet 4.5 (Sept 29) — same price ($3/$15), stronger agent.** **77.2% SWE-bench Verified**, **61.4% OSWorld** (computer-use), **30+ hour sustained agentic sessions**. Shipped alongside: **Claude Agent SDK** (code-first; the production evolution of Claude Code), **VS Code extension**, **Claude Code checkpoints**, and **Claude Skills** (reusable domain packs). → [`01` §2](./01-big-lab-moves.md#2-claude-sonnet-45) `#anthropic #sonnet-45 #agent-sdk #skills`

3. **Anthropic APAC build-out: Tokyo (Oct 29) + Seoul (Oct 23) + Google TPU expansion.** Tokyo signed a Memorandum of Cooperation with Japan AI Safety Institute; Seoul is Anthropic's third APAC office; Google Cloud TPU use expanded on the same day. **Claude for Life Sciences launched Oct 20.** Reads as five distribution channels opening in 30 days. → [`01` §3](./01-big-lab-moves.md#3-anthropic-apac) `#anthropic #apac #tpu #life-sciences`

4. **ChatGPT Atlas (Oct 21) — the browser is the next OS fight.** macOS-first Chromium browser with **agent mode** (Plus/Pro/Business) that executes tasks on-page. Challenges Chrome, Edge, Perplexity's **Comet**, The Browser Company's **Dia**. Windows/iOS/Android "soon." The agent-mode UX bakes a persistent-memory layer directly into browsing — read the Watchlist entry on **agent-identity**. → [`02` §1](./02-new-emerging.md#1-chatgpt-atlas) `#openai #browser #agents #atlas`

5. **Thinking Machines Lab — Tinker ships, $50B talks open.** Mira Murati's lab launched **Tinker** (managed fine-tuning API) in Oct 2025 after the **$2B at $12B** seed (a16z lead; Nvidia, AMD, Accel, Cisco, Jane Street). By Nov, reporting had the next round at **~$50B** — ~4× in a quarter, on **one shipped API**. The fine-tuning-API wedge is officially a tier-1 category. → [`02` §2](./02-new-emerging.md#2-thinking-machines-tinker) `#thinking-machines #tinker #fine-tuning #funding`

6. **Perplexity $18B valuation (+$100M).** Tripled in a year. Search-as-answer-engine thesis still the fastest-compounding consumer-AI wedge. → [`02` §3](./02-new-emerging.md#3-perplexity-18b) `#perplexity #search #consumer`

7. **Practical: Claude Agent SDK vs OpenAI AgentKit — one artifact that answers "which stack."** AgentKit = visual builder, managed infra, plug-and-play tools, speed-to-ship. Claude Agent SDK = code-first, your-infra, MCP-first, control + data-sovereignty. The honest 2026 answer: **ship AgentKit for prototypes, Claude Agent SDK for anything that goes to production with your data in it.** → [`03` §1](./03-practical-skills-and-tools.md#1-sdk-comparison) `#claude-code #agentkit #sdk`

8. **Practical: Claude Skills (shipped with 4.5) — the under-weighted feature of the quarter.** A **Skill** is a reusable scoped-knowledge pack Claude loads on demand (persona + workflow + tool list + examples). Shipped as official primitive — **invoke the `skill-creator` by asking "create a skill for X"**. Pairs with the Sept 10 decision tree (Hooks / Skills / Subagents / CLAUDE.md). → [`03` §2](./03-practical-skills-and-tools.md#2-claude-skills) `#claude #skills #claude-code`

9. **Research: agent-memory benchmarks go production-grade.** **mem-agent** (Dria, Oct 9) — a 4B agent trained with GSPO using markdown files + Python tools as its memory layer. **MemoryAgentBench** — four competencies (retrieval, test-time learning, long-range understanding, conflict resolution). **MemoryArena** — human-crafted interdependent sub-tasks across web nav, planning, searching, formal reasoning. "Memory in the age of agents" has moved from thesis to measurable. → [`04` §1](./04-research-progress.md#1-memory-benchmarks) `#arxiv #memory #agents #evals`

10. **Career: FDE postings +729% YoY (Apr '25→Apr '26, Indeed). AI/ML postings +163% YoY. MLE median mid-level $149–219K, LLM-fine-tune premium 25–40%.** Hiring hottest in finance / healthcare / defense / advanced manufacturing. For you: **the FDE / AI-Integration-Engineer / Solutions-Engineer lane is now mathematically the under-priced path** — more roles opening than there are candidates with real production-agent artifacts. → [`05` §1](./05-career-and-startup.md#1-fde-boom) `#fde #careers #salary`

---

## One thing to DO this Wednesday

→ **Ship one Claude Skill, publicly, tonight.** Pick one workflow you repeat weekly (resume tailoring, code-review rubric, cover letter draft, a specific research routine). Package it as a `.claude/skills/<name>/SKILL.md` with a trigger line in the frontmatter and 5 example invocations. Push to a public repo. **This is the single artifact that answers "did you ship against the Sept 29 primitives" in a Nov–Dec interview.** Details in [`03` §2](./03-practical-skills-and-tools.md#2-claude-skills).

## Watchlist deltas

- 🆕 **OpenAI AgentKit + Apps SDK (both MCP):** new thread. MCP is now a two-vendor standard; the Apps SDK makes ChatGPT the first serious agent-OS (apps in the chat). Watch which third-party apps hit DAU first.
- 🆕 **Claude Sonnet 4.5 + Agent SDK + Skills (Sept 29):** new thread. First production agent-stack with a 30-hour time horizon claim and a reusable Skills primitive. Watch for enterprise contracts specifying "Skills library."
- 🆕 **OpenAI–AMD ~6GW + up-to-10% equity warrant:** new thread. Replaces the pure-Nvidia narrative with a 2-GPU-vendor compute strategy. Watch the stock-price / supply linkage.
- 🆕 **ChatGPT Atlas (Oct 21):** new thread. Agent-mode + browser history-as-memory is the first consumer agent-stack with persistent context across sites. Watch for privacy / incident reports; watch Comet/Dia responses.
- 🆕 **Thinking Machines Tinker + $50B round talks:** new thread. The fine-tuning-API category now has a $50B-valued anchor on a single API.
- 🆕 **ChatGPT Apps SDK on MCP:** new thread. First time an app-platform is MCP-native from day one. Watch for "ChatGPT app store" revenue sharing terms.
- ➡️ **Model-routing + eval-authoring as scarce skills (from Sept 10):** reinforced. The two-SDK-stack world made it mandatory, not optional.
- ➡️ **FDE / AI-Integration-Engineer lane:** +729% YoY confirms the May/Sept thesis. Apply this week.
- ⬇️ **"Pick one lab" career strategy:** deprecated further. The production answer is now Agent SDK + AgentKit fluency, not one lab.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-openai-devday-2025) (DevDay) + [`01` §2](./01-big-lab-moves.md#2-claude-sonnet-45) (Sonnet 4.5) |
| 20 min | [`03` §1–2](./03-practical-skills-and-tools.md) — SDK comparison + ship-a-Skill |
| Tonight | Ship the Skill |
| Weekend | [`04` §1](./04-research-progress.md#1-memory-benchmarks) — the memory-benchmark papers, so you can talk about them |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
