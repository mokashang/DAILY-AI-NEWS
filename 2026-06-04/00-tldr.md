# TL;DR — 2026-06-04 (Thursday)

Sixty-second skim. **Anthropic filed. Claude Opus 4.8 shipped. The multi-model thesis got priced.** Inside ~10 days the [2026-05-22](../2026-05-22/) "S-1 as early as today" line became reality: **Anthropic confidentially submitted a draft S-1 to the SEC on June 1 at a ~$965B private valuation and $47B revenue run-rate** — *ahead* of OpenAI in both valuation and filing order. The same week, **Claude Opus 4.8 GA'd** with **dynamic workflows** (parallel subagents in-session) + **effort controls** + **fast-mode 3× cheaper** + **~4× less code-bug deception**. The **multi-model production thesis** got its anchor round: **OpenRouter $113M Series B at $1.3B post**, token volume **5T → 25T weekly in six months**, with **NVIDIA + Snowflake + Databricks** as strategic backers. **WWDC T-4 (Mon Jun 8):** Siri 2.0 + Apple Intelligence Extensions + a confirmed Apple-Google **Gemini chatbot partnership** — the multi-AI default-picker becomes consumer reality. For you: **the public-market turn is no longer hypothetical**, the **dynamic-workflow primitive is what you ship this weekend**, and **multi-model routing is now a category, not a hack**.

---

## Since 2026-05-22 (the 13-day gap)

This archive paused at `2026-05-22`. The biggest deltas in the missed window, before today's news, in one paragraph: **Anthropic confidentially filed its S-1 (Jun 1)** at **$965B / $47B ARR** — overtaking OpenAI's reported $852B (a meaningful order-flip vs. May 22's read). **Anthropic closed a $65B Series H** ahead of filing. **Claude Opus 4.8** shipped with **dynamic workflows** + **effort controls** + **fast-mode 3× cheaper** (May 28). **OpenRouter** raised **$113M Series B at $1.3B** (May 26, CapitalG lead). **Gemini app crossed 900M MAU**; **AI Mode in Search crossed 1B MAU**; **Google cut Ultra $250→$200/mo** and added a **$100/mo Developer tier**; **Gemini 3.5 Flash** is GA, **3.5 Pro** lands this month. **DeepMind paid ~$80–90M for the Contextual AI team** (~20 researchers, license-and-hire). **Anthropic Project Glasswing** expanded Claude Mythos Preview to **~150 new orgs** and added **Claude Security** (codebase scans + patch suggestions). **WWDC 2026 (Mon Jun 8)** is now T-4 with an Apple-Google Gemini Siri partnership confirmed. The June-15 Agent SDK metering switchover is **T-11**.

---

1. **Anthropic confidentially files draft S-1 — $965B private valuation, $47B revenue run-rate.** Filed June 1 with the SEC. **Anthropic is now the larger of the two filings**; OpenAI's confidential S-1 dropped May 22 at a reported $852B–$1T target. Anthropic separately closed a **$65B Series H** ahead of the filing. The "frontier AI as public-market asset class" thread is no longer hypothetical. → [`01` §1](./01-big-lab-moves.md#1-anthropic-s1) `#anthropic #ipo #public-markets`

2. **Claude Opus 4.8 GA'd (May 28) — dynamic workflows + effort controls + 3× cheaper fast mode.** **SWE-Bench Pro 69.2 · OSWorld-Verified 83.4 · GDPval-AA 1890 · Humanity's Last Exam 57.9.** Alignment team reports **~4× less likely than 4.7 to silently let bugs in generated code through.** Claude Code adds **dynamic workflows** ("ultracode" setting) — plan a task, **spawn hundreds of parallel subagents in one session**, verify, report. → [`01` §2](./01-big-lab-moves.md#2-opus-4-8) `#anthropic #model-release #claude-code`

3. **WWDC 2026 (Mon Jun 8) T-4: Siri 2.0 + Apple Intelligence Extensions + Gemini partnership.** Expected: an **all-new dedicated Siri app**, **Extensions across iOS/iPadOS/macOS 27**, and a custom AI model **built with Google's Gemini team** powering Siri's chatbot path. Users can set **third-party AI as default** for Writing Tools / Image Playground. The May-7 multi-AI-Extensions thread now lands on the **consumer default surface**. → [`01` §3](./01-big-lab-moves.md#3-wwdc) `#apple #wwdc #siri #extensions`

4. **Emerging: OpenRouter $113M Series B at $1.3B — the multi-model production thesis gets priced.** **CapitalG lead**; NVentures, ServiceNow Ventures, a16z, Menlo + strategic from **NVIDIA, Snowflake, Databricks**. **Weekly token volume 5T → 25T in six months.** The bet: enterprises are moving from "one model picker" to **multi-model production routing** — same primitive Apple is about to ship on the consumer side. → [`02` §1](./02-new-emerging.md#1-openrouter) `#funding #openrouter #multi-model #routing`

5. **Practical: dynamic workflows + the "ultracode" toggle — your single most important Opus 4.8 change.** Opus 4.8 + `/effort xhigh` or **`ultracode`** lets Claude Code **plan → fan-out **parallel** subagents → verify → report**, in one session. Tonight: enable it once, run **one** codebase-wide bug hunt against a public repo, save the trace. That's a portfolio artifact by Friday. **Also: June 15 Agent SDK metering switchover is T-11** — audit and toggle now. → [`03` §1](./03-practical-skills-and-tools.md#1-dynamic-workflows) `#claude-code #dynamic-workflows #ultracode`

6. **Research: the MCP-benchmark wave is *here*.** Four arXiv landings worth knowing the names of: **MCP-AgentBench** (33 servers · 188 tools · 600 queries; six categories) · **MCPMark** (stress-test under realistic load) · **177,436 MCP tools study** (Nov 24 → Feb 26; **67% of tools are dev tools; 90% of downloads**) · **MCPTox / MCPSecBench** (tool-poisoning + protocol-security baselines). Eval bar moved from "mock tools" to **"poison-resistant against real servers."** → [`04` §1](./04-research-progress.md#1-mcp-benchmark-wave) `#arxiv #mcp #benchmarks #security`

7. **Career: Agentic-AI postings +280% YoY (~90K US listings); entry-level postings −35% since early 2023.** Two opposite forces in one chart: agentic-AI is *the* fastest-growing US lane, **but** raw entry-level supply is shrinking as AI absorbs "grunt work." The threading needle: **internship/work-experience pre-grad doubles your hire rate.** Your edge today = a *visible* agentic-AI artifact, not a degree-only signal. → [`05` §1](./05-career-and-startup.md#1-jobs-data) `#jobs #careers #agentic-ai`

8. **Skill read of the week:** the value migrated again. May 19–22 it was "I designed who-does-what at what cost." Today it's **"I designed a *dynamic*, *self-fanning-out* team that uses real tools and survives prompt-injection on real MCP servers."** Opus 4.8's dynamic workflows (industrialize) + the MCP-benchmark wave (verify) + OpenRouter's $113M (route) are three sides of the same hardening. → [`05` §2](./05-career-and-startup.md#2-skill-reprice) `#skills #careers`

---

## One thing to DO this Thursday

→ **Tonight (45 min):** enable **dynamic workflows** in Claude Code (`/effort ultracode` or via the effort menu, [`03` §1](./03-practical-skills-and-tools.md#1-dynamic-workflows)), run **one** codebase-wide audit on a public repo (suggestion: a small open-source project you actually use), **save the trace + a per-step cost log**. Tomorrow: write a **15-line README** that frames it as *"how I'd run a safety-relevant audit at predictable cost against a real-tool surface"* — pulls in [`04` §1 MCP-AgentBench](./04-research-progress.md#1-mcp-benchmark-wave) and [`01` §2 Opus 4.8](./01-big-lab-moves.md#2-opus-4-8). Same artifact, but now **dynamic + measured**. **Also: 60-min Anthropic / OpenAI / Sierra job-board sweep tonight** ([`05` §3](./05-career-and-startup.md#3-apply-window)) — post-filing hiring cycles tighten *fast* once an S-1 is in.

## Watchlist deltas

- 🟢 **Anthropic confidential S-1: FILED (Jun 1).** Status flips 🟡→🟢-filed. Valuation $965B / ARR $47B. Watch: public S-1 disclosure (~15d pre-roadshow), revenue mix by segment, lock-up.
- 🟢 **Anthropic Series H $65B closed** (pre-filing). Status flips ⚪→🟢. Confirms the $50B-class raise thread.
- 🆕 **Claude Opus 4.8 GA'd (May 28):** new thread — track adoption vs Opus 4.7 (especially the "4× less silent-bug" claim under real use), GDPval-AA / SWE-Bench Pro deltas vs GPT-5.5 + Gemini 3.5 Pro when it lands.
- 🆕 **OpenRouter $113M Series B at $1.3B (May 26):** new thread — multi-model routing as a category; **NVIDIA/Snowflake/Databricks strategic** = both supply + demand sides bought in.
- 🆕 **WWDC 2026 T-4 (Mon Jun 8):** new thread — Siri 2.0, Extensions, Apple-Google Gemini partnership, third-party default toggle.
- 🆕 **DeepMind ~$80–90M Contextual AI team license-and-hire (~20 researchers):** new talent thread, RAG-research consolidation under Google.
- 🆕 **Gemini 3.5 Flash GA + Gemini app 900M MAU + Ultra $250→$200/mo + $100/mo Developer tier:** new product-pricing thread.
- ➡️ **OpenAI confidential S-1 (May 22):** still live; **Anthropic filed second but at higher valuation** — order matters less than the spread.
- ➡️ **Anthropic Agent SDK metering (June 15):** T-minus **11 days** — the dynamic-workflows toggle in [`03`](./03-practical-skills-and-tools.md) magnifies spend; audit *before* metering flips.
- ➡️ **MCP eval wave (MCP-Atlas/Toolathlon → MCP-AgentBench/MCPMark + MCPTox/MCPSecBench):** continues from 2026-05-22; **security half is the new growth edge**.
- ➡️ **Trump AI executive order (postponed 5-22):** still postponed as of today; track for re-scheduling.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [Anthropic S-1 + Opus 4.8 in `01` §1–2](./01-big-lab-moves.md) |
| 20 min | [`01` §3 WWDC preview](./01-big-lab-moves.md#3-wwdc) + [`04` §1 MCP-benchmark wave](./04-research-progress.md#1-mcp-benchmark-wave) — the two deepest signals |
| Tonight | [`03` §1 enable dynamic workflows + run one audit](./03-practical-skills-and-tools.md#1-dynamic-workflows) |
| This week | [`05` §3 apply window](./05-career-and-startup.md#3-apply-window) — Anthropic Solutions / OpenAI FDE / Sierra CX inside 7 days of the S-1 |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
