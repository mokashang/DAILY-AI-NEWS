# TL;DR — 2026-05-20 (Wednesday)

Sixty-second skim. **The morning after.** Yesterday's pre-staging pays off: we now have the *actual* Google I/O keynote (not leaks), and the story is bigger than predicted. Google shipped **Gemini 3.5 Flash at ~⅓ Claude's price** ("within 2 points" on benchmarks), an entire **agent platform (Antigravity 2.0 + Managed Agents in the Gemini API)**, and — the under-weighted headline — **WebMCP, an open web standard built on Anthropic's MCP lineage, shipping in Chrome 149.** Code w/ Claude London ran *no new model* and ratified an already-shipped roadmap. **Meta's 8,000-person cut is executing in real time today.** And Google's same-week threat report found **real PayPal-payload prompt injections in the wild**, recommending the *exact* dual-model defense that last week's TrajAD verifier research pointed at. The frontier just moved from "smartest model" to "cheapest-good-enough + best agent rails + safe under autonomy."

---

1. **Google I/O scorecard: ~7/9 predictions hit — and the agent platform is the story.** **Gemini 3.5 Flash** went GA same-day at **$1.50/1M in · $9/1M out** (1M-token context, text+image+audio+video in), positioned "within 2 points of Anthropic's flagship at ~⅓ the price," already GA in GitHub Copilot. **Gemini 3.5 Pro** ships June. Sundar led **enterprise-first** (Antigravity, Managed Agents, ADK 2.0) — per yesterday's frame, Google is *committing to the enterprise-agent war*, not conceding it. → [`01` §1](./01-big-lab-moves.md#1-io-scorecard) `#gemini35flash #io2026 #scorecard #price-war`

2. **WebMCP — the day's real headline.** Google proposed **WebMCP**, an open web standard letting sites expose callable tools so browser agents *call* functions instead of scraping HTML. Experimental **origin trial in Chrome 149.** The name concedes that **Anthropic's MCP has become the industry default** — the largest browser vendor is extending it into a web standard. This is a standards-level win for the protocol you're already learning. → [`02` §1](./02-new-emerging.md#1-webmcp) `#webmcp #mcp #standards #agentic-web`

3. **Antigravity 2.0 + Managed Agents = Google copies (and names) the Anthropic playbook.** "One API call → an agent that reasons, uses tools, executes code in an isolated Linux sandbox" — near-verbatim Anthropic Managed Agents. Two of three labs now ship one-call sandboxed managed agents; **the agent-runtime primitive is now table stakes.** Plus Chrome DevTools-for-agents supporting **20+ non-Google coding agents.** → [`01` §2](./01-big-lab-moves.md#2-antigravity) `#antigravity #managed-agents #convergence`

4. **Code w/ Claude London: no new model, roadmap ratified.** Four of five "announcements" had already shipped — the event *ratified* a quietly-shipped roadmap (Dreaming, Outcomes, multi-agent orchestration, Claude Finance, Add-ins). Re-confirmed: **Colossus 1** (220K+ GPUs, 300+ MW), **Claude Code 5-hr limits doubled** + peak throttle lifted, demand **~80× YTD**. Honest read: **Google closed real ground on the agent layer in 24 hours.** → [`01` §3](./01-big-lab-moves.md#3-cwc-london) `#anthropic #code-w-claude #colossus`

5. **Meta's 8,000-person cut is executing TODAY.** ~8K notified Wed (≈10%), +6K canceled reqs = ~14K impact; Singapore first (4 AM), then UK/US. New detail: **~7,000 redirected** into new AI teams (**Applied AI Engineering · Agent Transformation Accelerator XFN · Central Analytics**) — so the Thursday wave splits *three* ways, not two. AI infra spend cited at **$145B**. More cuts planned H2. Your outreach window opens **Thu 8 AM PT.** → [`01` §4](./01-big-lab-moves.md#4-meta-executing) · [`05` §1](./05-career-and-startup.md#1-meta-outreach) `#meta-layoff #outreach`

6. **Prompt injection is now empirical, not theoretical.** Google's threat report: **+32% relative growth in malicious IPI (Nov 2025→Feb 2026)**, with **real PayPal-transaction payloads hidden invisibly in HTML** targeting payment-capable agents. Recommended fix: a cheap **dual-model "sanitiser"** in front of the privileged agent — the *same* primitive as TrajAD's verifier and JADE's per-claim checker. **One primitive, three research lanes.** → [`04` §1–2](./04-research-progress.md#1-ipi-wild) `#prompt-injection #agent-safety #convergence`

7. **AI Ultra ($100/mo) + Gemini Spark.** Google shipped a **24/7 proactive consumer agent (Spark)** in a new $100/mo tier — matching Anthropic Max-5x's price point. Proactive autonomous agents are the consumer frontier all three labs converge on; their shared unsolved problem is **trust under autonomy** (see #6). → [`02` §2](./02-new-emerging.md#2-ai-ultra) `#gemini-spark #ai-ultra #proactive-agents`

8. **The skill re-price.** Frontier shifting to "cheapest-good-enough + best rails + safe" means: **cost-aware routing** and **agent-safety/IPI defense** became *scarce & valuable*; raw "I can prompt a model" got *commoditized*; **MCP/WebMCP** got *stronger*. → [`05` §2](./05-career-and-startup.md#2-price-war) `#cost-aware #skills #careers`

---

## One thing to DO this Wednesday

→ **Publish the filled-in I/O comparison table** ([`03` §1](./03-practical-skills-and-tools.md#1-comparison-table)) — a *graded, sourced* Gemini-3.5-Flash vs Claude vs GPT table with the real numbers, plus your one-line take ("the frontier is now cheapest-good-enough + best rails, not smartest"). Then **update LinkedIn skills to the real on-stage terms** (`Antigravity 2.0 · Managed Agents (Gemini API) · WebMCP · Gemini 3.5 Flash · Claude Agent SDK · MCP · cost-aware agents`) — yesterday's pre-keynote bet was "Vertex AI Agent Platform," which Google did *not* use; correcting it publicly and grading your own prediction is a credibility signal. **~45 minutes, top-of-feed visibility for 48 hours.**

## Watchlist deltas

- ✅ **Google I/O 2026 prediction thread → RESOLVED.** ~7/9 hits; Gemini 3.5 (Flash) ✅, Spark ✅, XR ✅, Aluminium OS ✅; Gemma 4 soft; "Omni" folded into 3.5 multimodal. Close thread.
- 🆕 **WebMCP origin trial (Chrome 149):** new thread — first-mover demo repo opportunity; catalyzes the agent-identity/auth wedge with a concrete ship date
- 🆕 **Gemini 3.5 Flash price war ($1.50/1M):** new thread — compresses "cheap inference" startups; elevates cost-aware routing as a skill; watch Claude/OpenAI price response
- 🆕 **Indirect prompt injection in the wild (Google report, +32%):** new thread — agent-safety moves from values-talk to measurable production requirement; track next quarter's number
- 🆕 **Antigravity 2.0 / Gemini Managed Agents:** new thread — Google's agent runtime; add Google Cloud Agent-Solutions roles to apply list
- 🆕 **Meta 7,000 redirected into AI teams (Applied AI Eng / Agent Transformation Accelerator):** new thread — re-skilling, not just cutting; pool (c) outreach
- ⬆️ **Meta May 20 layoff:** EXECUTING today; ~8K + 6K reqs = ~14K; $145B infra; H2 cuts planned. Outreach window opens Thu 8 AM PT
- ⬆️ **Code w/ Claude London:** ran no new model; ratified shipped roadmap; doubled Claude Code limits + lifted peak throttle
- ➡️ **Anthropic Agent SDK metering (June 15):** T-minus 26 days — doubled *interactive* limits ≠ change to programmatic metering; manual toggle still required
- ➡️ **Anthropic $30B raise at $900B+:** still "imminent"; Code w/ Claude London window passed without a term-sheet print

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the I/O scorecard table in [`01` §1](./01-big-lab-moves.md#1-io-scorecard) |
| 20 min | [`03`](./03-practical-skills-and-tools.md) — publish the comparison table + start the dual-model sanitiser |
| Tonight | [`05` §1–2](./05-career-and-startup.md#1-meta-outreach) — prep Thursday Meta outreach (split pools b/c); rewrite LinkedIn skills row |
| This week | Ship 3 artifacts: graded comparison table · cost-router + savings chart · dual-model sanitiser |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
