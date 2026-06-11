# TL;DR — 2026-06-11 (Thursday)

Sixty-second skim. **Three weeks compressed into one news cycle. The Mythos-class model is now public, the IPO is filed, and the policy that would have quietly degraded Claude for AI researchers got reversed *today*.** **Anthropic shipped Claude Fable 5 (the public version of Mythos) and Mythos 5 on Tue June 9** — SOTA on essentially every public benchmark; SWE-Bench Pro **80.3%** (vs Opus 4.8 69.2%, GPT-5.5 58.6%); priced **$10/M in · $50/M out**. **Anthropic's confidential S-1 went to the SEC on June 1 at a ~$965B valuation** (revenue run-rate ~$47B, up from ~$10B a year ago) — completing the May-22 thread. **Today: two big moves.** (1) **Anthropic walks back the silent frontier-LLM-research safeguard** ("we made the wrong tradeoff and we're sorry") after Simon Willison, Nathan Lambert, and Dean Ball flagged that Fable 5 was covertly degrading replies on pretraining / distributed-training / accelerator-design questions; (2) **Claude Corps** — a **$150M / 1,000-fellow / $85K-salary / 12-month** nonprofit fellowship for early-career people **with under 2 years of full-time experience** — applications close **July 17**, first cohort 100, placements October. Backdrop: **WWDC just wrapped (Mon June 8)** and Apple Intelligence is now **built on a custom $1B/yr Gemini partnership with Google** — a meaningful flip of the iOS-Extensions narrative away from Anthropic. **For you: Claude Corps is on your eligibility line; the safeguards reversal is a hiring/portfolio tell about *visible* safety design; the Apple-Gemini deal re-prices which provider lane to invest in for consumer-AI integration work.**

---

1. **Claude Fable 5 + Claude Mythos 5 SHIPPED (Tue June 9).** Anthropic's first **public Mythos-class** model. **SWE-Bench Pro 80.3% · FrontierCode 29.3% · Mythos-5 cyber 78.0%** (~2× Opus-4.8's 40%) · pricing **$10/M in · $50/M out** (Mythos preview was $20/M / $100/M — Fable cuts list price in half); guarded queries silently routed to Opus 4.8 in <5% of sessions — **the routing later became the controversy in §3**. → [`01` §1](./01-big-lab-moves.md#1-fable-5) `#anthropic #fable-5 #mythos #benchmarks`

2. **Anthropic files confidential S-1 with SEC (June 1) — ~$965B target.** Closed **$65B Series H** "days earlier"; **revenue run-rate ~$47B** (vs ~$10B a year ago); underwriters **Morgan Stanley + Goldman Sachs + JPMorgan**; bankers expect **>$60B raised at IPO**. Completes the [2026-05-22 thread](../2026-05-22/01-big-lab-moves.md#2-openai-s1) — IPO wave confirmed. → [`01` §2](./01-big-lab-moves.md#2-anthropic-s1) `#anthropic #ipo #public-markets`

3. **Anthropic REVERSES silent safeguards on frontier-LLM-research queries (today).** Fable 5 was covertly degrading replies on **pretraining pipelines, distributed training, ML accelerator design** via *steering vectors and prompt modification* — no user notification; documented in one paragraph of the **319-page system card**. Backlash from **Simon Willison, AI2's Nathan Lambert, Dean Ball, Fortune**. Anthropic to Wired: *"We made the wrong tradeoff and we apologize for not getting the balance right."* Flagged requests now **visibly fall back to Opus 4.8**. → [`01` §3](./01-big-lab-moves.md#3-safeguards-reversal) `#anthropic #safety #policy #transparency`

4. **Claude Corps — $150M / 1,000 fellows / $85K (today).** With CodePath (employer-of-record) and Social Finance (M&E). Anyone **18+ with under 2 years FT experience**, **any educational background**. First cohort **100 fellows · apps close July 17 · placements October 2026**. Host orgs get **$10K grant + free Claude credits**. **This is directly on your eligibility line** — it's the highest-signal Claude credential outside a frontier-lab offer and you can apply this month. → [`05` §1](./05-career-and-startup.md#1-claude-corps) `#anthropic #careers #fellowship #nonprofit`

5. **WWDC 2026 (Mon June 8) — Apple Intelligence rebuilt on Google Gemini.** Multi-year **~$1B/yr custom Gemini build (~1.2T params)** powers Siri's cloud tier via **Private Cloud Compute**; on-device runs Apple's own foundation models. Siri AI rebuilt with system-wide context; Shortcuts gets **natural-language AI workflow builder**; **iOS 27 Agent Extensions for enterprise** previewed. Apple's [iOS 27 "Extensions" SDK](../2026-05-07/01-big-lab-moves.md#1-apple-extensions) thread from May 7 inverts: **Gemini is the default cloud brain**, Anthropic / OpenAI access likely opens later via Extensions but the foundation is Google's. → [`01` §4](./01-big-lab-moves.md#4-wwdc-apple-gemini) `#apple #google #gemini #wwdc #consumer-ai`

6. **OpenAI: GPT-5.4 mini ships to Free/Go, o3 + 4.5 sunset dates set, Codex gains web-search-in-code-mode + richer MCP schemas.** Sunsets: **GPT-4.5 → June 27 (30-day)** · **o3 → August 26 (90-day)**. **Workspace Agents stays free until July 6**, then credit-priced. ChatGPT memory gets **"dreaming" auto-updates + reviewable memory page**. Codex adds **plugin marketplace listings**. → [`01` §5](./01-big-lab-moves.md#5-openai-stack) · [`03` §2](./03-practical-skills-and-tools.md#2-codex-mcp) `#openai #gpt #codex #mcp #sunsets`

7. **Funding wave: TensorWave $350M Series B (AMD + Magnetar) at $1.55B — Nvidia-free AI cloud · Supabase $500M at $10.5B (GIC) · Suno $400M D at $5.4B · Flourish $500M (brain-inspired) · PhysicsX $300M Series C (Temasek).** TensorWave is the structural story: **AMD just funded the wedge** against Nvidia's monopoly — a real second supplier path for inference workloads. → [`02` §1](./02-new-emerging.md#1-tensorwave) `#funding #amd #infra #supabase #suno #physicsx`

8. **Research: real-tool agent eval is the consolidating category.** **ToolMisuseBench** (offline-deterministic — *misuse* + *recovery*, not just success), **MCPVerse** (real-world MCP servers at scale), **Test-Time Scaling of General LLM Agents**, **"Agents Learn Their Runtime"** (interpreter persistence as training-time semantics). Same lesson as MCP-Atlas / Toolathlon from [2026-05-22](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks): **the eval bar is now your stack, not a sandbox.** → [`04` §1](./04-research-progress.md#1-real-tool-evals) `#arxiv #benchmarks #agents #mcp #tool-use`

---

## One thing to DO this Thursday

→ **Start the Claude Corps application** ([`05` §1](./05-career-and-startup.md#1-claude-corps)). Apps close **July 17** — earlier than your usual cadence. **Why now, not later:** you fit the eligibility window (under 2 yrs FT), the brand is already strong, and **before applicant volume compounds** is the cheapest week to apply. 90 minutes tonight: pull two artifacts from your portfolio (MCP server demo + the dual-model sanitiser project from [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact)), write a single paragraph linking Claude → nonprofit operational leverage, save the application draft. Submit before June 22 to clear the early-decision read window.

Second action — **update your Fable 5 / pricing reality-check**: re-run your three-provider router with **Fable 5 ($10/$50) in the orchestrator seat**, log per-step cost ([`03` §1](./03-practical-skills-and-tools.md#1-fable-5-router)).

## Watchlist deltas

- 🟢 **Anthropic IPO path (Oct 2026 target):** **CLOSED → S-1 filed June 1 at ~$965B**, Morgan Stanley + Goldman + JPMorgan as underwriters, $65B Series H closed alongside. The thread from [2026-05-22](../2026-05-22/01-big-lab-moves.md#2-openai-s1) resolves.
- 🟢 **Mythos public release:** **RESOLVED → Fable 5 is the public Mythos**; Mythos 5 trusted-access only. Pricing halved vs Mythos preview. Cyber benchmark 78%.
- 🆕 **Visible-safeguards regime as policy norm:** new thread — Anthropic's reversal will be cited in interviews and policy debates; watch for OpenAI / Google parity commitments and whether **"safeguards transparency" becomes a buyer requirement** in enterprise procurement.
- 🆕 **Claude Corps cohort 1 (apps close July 17):** new thread — track who gets in (signal about Anthropic's hiring funnel for nonprofit-adjacent + early-career talent) and what host orgs are chosen.
- 🆕 **Apple ↔ Google Gemini ($1B/yr, ~1.2T params, multi-year):** new thread — completely re-prices the **consumer-AI integration lane**; watch whether iOS 27 Extensions opens cloud-tier access to Claude / GPT or just keeps them at the assistant-handoff layer.
- 🆕 **TensorWave $350M + AMD-led AI infrastructure:** new thread — real second-supplier emergence; track whether anchor customers (esp. anyone running Claude or open-weights inference) commit publicly and whether Nvidia responds on inference pricing.
- ➡️ **Anthropic Agent SDK metering (June 15):** T-4 days. Your Fable 5 router work below dovetails directly.
- ➡️ **WebMCP origin trial (Chrome 149):** still live from 2026-05-20; the OpenAI Codex MCP-schema upgrade is the second vendor leaning in.
- ⬇️ **Trump AI executive order (postponed 2026-05-22):** no movement reported this week; treat as dormant until the re-scheduled signing.
- ⬇️ **Anthropic $30–50B raise:** **superseded** — the $65B Series H closed at the same ~$965B mark cited for the IPO; thread folds into IPO row.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the safeguards reversal in [`01` §3](./01-big-lab-moves.md#3-safeguards-reversal) (the policy/portfolio tell) |
| 20 min | [`01` §3](./01-big-lab-moves.md#3-safeguards-reversal) + [`01` §4](./01-big-lab-moves.md#4-wwdc-apple-gemini) (the two highest-signal stories for *your* lane) |
| Tonight | [`05` §1](./05-career-and-startup.md#1-claude-corps) — start the Claude Corps application |
| Weekend | [`03` §1](./03-practical-skills-and-tools.md#1-fable-5-router) — Fable 5 in the orchestrator seat; log cost-vs-Opus delta |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
