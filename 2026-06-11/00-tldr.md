# TL;DR — 2026-06-11 (Thursday)

Sixty-second skim. **SpaceX prices the largest IPO in history after close today; Anthropic walks back a hidden safeguard on Fable 5 in under 48 hours; and Anthropic announces Claude Corps — $150M, 1,000 fellows, $85K, twelve months, under-two-years-FT eligibility — directly on your eligibility window.** **SpaceX priced after close at $135/share for a ~$1.75T valuation, ~$75B raised, trades Friday on NASDAQ as SPCX** ([2026-06-10 set this up at T-1](../2026-06-10/01-big-lab-moves.md#4-spacex-ipo)); MSCI flagged early Global Standard Index inclusion June 13 (T+1) — that's *forced* index demand from day two. Underneath: Anthropic's Tuesday Fable 5 ship ([2026-06-09](../2026-06-09/01-big-lab-moves.md#2-fable-mythos)) shipped with a **silent** safeguard buried in a 319-page system card — Simon Willison, Nathan Lambert (AI2), Dean Ball, and Fortune flagged that Fable 5 was *covertly degrading* responses on pretraining / distributed training / ML-accelerator-design queries via steering vectors. **Today: Anthropic reversed.** *"We made the wrong tradeoff and we apologize for not getting the balance right."* Flagged queries now visibly fall back to Opus 4.8 — the same pattern as cyber/bio. And **Claude Corps** ([anthropic.com/news/claude-corps](https://www.anthropic.com/news/claude-corps)) is the structured embodiment of the pre-IPO mission story — *fellow program for early-career people, run with CodePath* — and **applications close July 17**. For you: SpaceX sets the public-market comp for next month's Anthropic + OpenAI roadshows; the safeguards reversal *is* a hireable interview answer about visible safety design; Claude Corps is the cheapest week to apply.

---

1. **SpaceX prices the largest IPO in history — $135/share, ~$1.75T, ~$75B raised, SPCX trades Friday on NASDAQ.** Goldman / Morgan Stanley / BofA / Citi / JPM. Starlink alone: **$11.4B revenue, $4.4B operating profit in 2025**; SpaceX total revenue **$18.7B (+33% YoY)** with $4.94B GAAP net loss (Starship capex). **MSCI early inclusion in Global Standard Indexes June 13 (T+1)** — index funds *forced* to buy from day two. This is the **public-market comp benchmark** for Anthropic's October-target / $965B S-1 and OpenAI's $852B (June-8 filing). → [`01` §1](./01-big-lab-moves.md#1-spacex-prices) `#spacex #ipo #spcx #public-markets`

2. **Anthropic walks back the silent Fable 5 safeguard on frontier-LLM-research queries — under 48 hours.** Fable 5 ([2026-06-09](../2026-06-09/01-big-lab-moves.md#2-fable-mythos)) shipped with a hidden, **steering-vector + prompt-modification** safeguard that covertly degraded replies on pretraining / distributed training / ML accelerator design — buried in one paragraph of a 319-page system card. Backlash from **Simon Willison · Nathan Lambert (AI2) · Dean Ball · Fortune**. Anthropic to Wired today: *"We made the wrong tradeoff and we apologize for not getting the balance right."* Flagged queries now **visibly fall back to Opus 4.8** — same UX as cyber/bio safeguards. → [`01` §3](./01-big-lab-moves.md#3-safeguards-reversal) `#anthropic #safety #policy #transparency #fable-5`

3. **Claude Corps — $150M / 1,000 fellows / $85K / 12-month nonprofit fellowship (TODAY).** With **CodePath** (employer-of-record) + **Social Finance** (M&E). Anyone **18+ with <2 years full-time work experience, any educational background**. First cohort **100 fellows · apps close July 17 · placements October 2026**. Host orgs (≥400) get **$10K + free Claude credits**. **You're squarely on the eligibility line.** The applicant volume hasn't compounded yet — this week is the cheapest week to apply. → [`05` §1](./05-career-and-startup.md#1-claude-corps) `#anthropic #careers #fellowship #nonprofit`

4. **WWDC ratified Apple-Gemini ($1B/yr, ~1.2T params).** Already covered Mon-Tue in [2026-06-08](../2026-06-08/01-big-lab-moves.md) / [2026-06-09](../2026-06-09/01-big-lab-moves.md). Net for your application list: **add `#gemini` to your skills row; add Apple AI / Apple Intelligence Engineering as an adjacent lane** — the integration-engineering hiring inside Apple is under-priced. → [`05` §3](./05-career-and-startup.md#3-gemini-fluency) `#apple #google #gemini #wwdc`

5. **OpenAI maintenance week:** GPT-5.4 mini to Free/Go via "Thinking"; **GPT-4.5 sunsets June 27 (30-day) · o3 sunsets August 26 (90-day)**; Codex gains **web-search-in-code-mode + richer MCP schemas + plugin marketplace**; ChatGPT memory **"dreaming"** (auto-update + reviewable page); **Workspace Agents stays free until July 6**, then credit-priced. → [`01` §5](./01-big-lab-moves.md#5-openai-stack) · [`03` §2](./03-practical-skills-and-tools.md#2-codex-mcp) `#openai #gpt #codex #mcp #sunsets`

6. **TensorWave $350M Series B at $1.55B — AMD + Magnetar lead, Nvidia-free AI cloud (June 10).** AMD Ventures as co-lead means **AMD is funding the demand side** of its own ecosystem; a real second-supplier story for inference. Lower-applicant-volume hiring lane (ROCm / MI300X). → [`02` §1](./02-new-emerging.md#1-tensorwave) `#funding #amd #infra`

7. **Growth-round wave**: **Supabase $500M @ $10.5B (GIC) · Suno $400M D @ $5.4B (Bond) · PhysicsX $300M C @ $2.4B (Temasek) · Flourish $500M (brain-inspired).** Pattern is **devtools + vertical applied AI + alt-architecture**, not frontier models. → [`02` §2](./02-new-emerging.md#2-growth-wave) `#funding #devtools #industrial-ai`

8. **Research: real-tool agent eval consolidates.** **ToolMisuseBench** (offline-deterministic — *misuse* + *recovery* scoring), **MCPVerse** (real MCP servers at scale), **Test-Time Scaling of General LLM Agents**, **"Agents Learn Their Runtime"** (interpreter persistence as training-time semantics), and the **Externalization in LLM Agents survey** (best single-read of the month). The May-22 thread — *eval bar is now your stack, not a sandbox* — is the category now. → [`04` §1](./04-research-progress.md#1-real-tool-evals) `#arxiv #benchmarks #agents #mcp #tool-use`

---

## One thing to DO this Thursday

→ **Start the Claude Corps application tonight (60 min).** Apps close **July 17**; submit by **June 22** to clear the early-decision read window before applicant volume compounds. Anchor the personal statement on your three live artifacts — the MCP server (in progress), the dual-model sanitiser project ([2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact)), and the Fable-5 router rebaseline ([`03` §1](./03-practical-skills-and-tools.md#1-fable-5-router)) — and frame the narrative around *"applying Claude inside a low-resource, mission-driven org where each hour of operational leverage matters more."*

Second action — **install the visible-safeguards interview answer** ([`05` §2](./05-career-and-startup.md#2-visible-safety)) and ship the **30-min visible-safeguards eval harness** ([`03` §3](./03-practical-skills-and-tools.md#3-visible-safeguards)). Together they're the cheapest portfolio + interview-prep combo of the quarter.

## Watchlist deltas

- 🟢 **SpaceX IPO pricing (T-1 from yesterday):** **CLOSED → priced at $135/share, ~$1.75T, ~$75B raised, SPCX trades Fri June 12 on NASDAQ.** MSCI Global Standard Index inclusion June 13 (T+1). Largest IPO ever. Watch first-day pop and the read-across to Anthropic ($965B) + OpenAI ($852B) S-1 pricing.
- 🆕 **Visible-safeguards regime as policy norm:** new thread — the Anthropic reversal will be cited in interviews and enterprise procurement for the rest of 2026. Watch for OpenAI / Google parity transparency commitments and whether **"safeguard transparency"** becomes a buyer requirement in regulated verticals.
- 🆕 **Claude Corps cohort 1 (apps close July 17):** new thread — track which 100 fellows get selected (signal about Anthropic's preferred early-career hiring funnel) and which host orgs are chosen (signal about preferred nonprofit verticals).
- 🆕 **TensorWave $350M + AMD-led AI infrastructure:** new thread — real second-supplier emergence. Track for an anchor customer (hyperscaler or frontier lab) inside 60–90 days; ROCm-native MLOps tooling startups as second-order wedges; Nvidia's inference-pricing response.
- ➡️ **Anthropic IPO ($965B, filed June 1):** still live. SPCX's first-day pop tomorrow is the read-across.
- ➡️ **OpenAI confidential S-1 ($852B, filed June 8):** still live; Altman's "may be a while" framing softens timing. SEC first-comment-letter window is the next milestone.
- ➡️ **Anthropic Agent SDK metering goes live (Sun June 15) — T-4.** The Fable-5-in-orchestrator router rebaseline ([`03` §1](./03-practical-skills-and-tools.md#1-fable-5-router)) is the direct mitigation.
- ➡️ **Fable 5 free-included window for Pro/Max/Team ends June 22.** Credits required June 23+; your billing audit ([ME.md](../ME.md)) maps directly.
- ⬇️ **Trump AI executive order:** still **POSTPONED** since [2026-05-22](../2026-05-22/01-big-lab-moves.md#1-eo-postponed); Project Glasswing is filling the cyber-clearinghouse role *de facto* (see [2026-06-10/02 §1](../2026-06-10/02-new-emerging.md)).

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the safeguards reversal in [`01` §3](./01-big-lab-moves.md#3-safeguards-reversal) (the policy/portfolio tell) |
| 20 min | [`01` §1 SpaceX pricing](./01-big-lab-moves.md#1-spacex-prices) + [`01` §3 safeguards reversal](./01-big-lab-moves.md#3-safeguards-reversal) — the two highest-signal stories |
| Tonight | [`05` §1 Claude Corps application](./05-career-and-startup.md#1-claude-corps) — start tonight, submit by June 22 |
| Weekend | [`03` §1 Fable 5 in the orchestrator seat](./03-practical-skills-and-tools.md#1-fable-5-router) + ship the portable MCP server ([`03` §2](./03-practical-skills-and-tools.md#2-codex-mcp)) before June 15 metering |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
