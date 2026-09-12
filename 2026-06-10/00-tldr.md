# TL;DR — 2026-06-10 (Wednesday)

Sixty-second skim. **Today is Code w/ Claude Tokyo, tomorrow is SpaceX IPO pricing, and the "Mythos-class" tier is now 24 hours old.** Anthropic's APAC developer event runs **today with a global livestream** ([Tokyo — Code w/ Claude](https://claude.com/code-with-claude/tokyo)); the SF event back in May 6 already minted **Managed Agents (public beta)**, **Dreaming (session-memory developer preview, Harvey reporting ~6× task-completion lift)**, **Outcomes**, and a **SpaceX-compute-funded 2× rate-limit bump for Pro/Max/Team + 1500% / 900% input/output token increase for Tier-1 API customers**. **Tomorrow (Thu Jun 11) SpaceX prices its IPO at $135/share for a ~$1.75T valuation — the largest IPO in market history** — and trades Friday on NASDAQ as **SPCX**. Under both: yesterday's **Claude Fable 5** ship (Mythos-class tier, $10/$50 per MTok, **80.3% SWE-bench Pro vs GPT-5.5 58.6%**), and the **AWS MCP Server GA** ([2026-06-09](../2026-06-09/00-tldr.md)) that turned MCP into AWS-native infrastructure. The frame for today: *the developer relationship goes APAC, the compute-bill counterparty goes public, and the agent stack you'd build on becomes table-stakes.*

---

1. **TODAY — Code w/ Claude Tokyo** (global livestream open). Anthropic's first APAC developer event. Expected SDK feature announcements, APAC customer presenters, follow-throughs from the **SF May-6 ship list** (Managed Agents public beta · Dreaming developer preview · Outcomes · 2× rate-limit bump). Anchored on the **NEC partnership** (Apr 2026 — ~30k NEC employees on Claude) — Japan is the front-line for Anthropic's enterprise APAC bet. → [`01` §1](./01-big-lab-moves.md#1-tokyo) `#anthropic #tokyo #devrel #apac #managed-agents`

2. **TOMORROW (T-1) — SpaceX IPO prices at $135/share for $1.75T.** **555.6M shares**, ~**$75B raise**, **NASDAQ: SPCX**, trading **Fri Jun 12**. Goldman / Morgan Stanley / BofA / Citi / JPM. **Largest IPO in market history.** This is the **precedent print** for the Anthropic ($965B, filed first) and OpenAI ($852B, filed Jun 8) S-1s already in queue. → [`01` §4](./01-big-lab-moves.md#4-spacex-ipo) `#spacex #ipo #spcx #public-markets`

3. **Yesterday's still-fresh: Claude Fable 5 / Mythos 5 — "Mythos-class" tier ships.** **Fable 5** (public): $10/$50 per MTok; **80.3% SWE-bench Pro** vs GPT-5.5 58.6%; API + Bedrock today; included in Pro/Max/Team **through June 22**, credits required June 23+. **Mythos 5** (restricted): same model, safeguards lifted, **Project Glasswing only**. → [`01` §2](./01-big-lab-moves.md#2-fable-mythos) `#anthropic #release #claude #mythos-class`

4. **IPO race already inverted: Anthropic ($965B, filed first) → OpenAI ($852B, filed Jun 8).** Altman walked back near-term timing ("may be a while"); **Polymarket: 0.5% chance OpenAI IPO by Jun 30; 69.5% by Dec 31.** SpaceX pricing tomorrow effectively sets the public-market comp benchmark. → [`01` §3](./01-big-lab-moves.md#3-ipo-race) `#openai #anthropic #ipo`

5. **Project Glasswing — 150 orgs / 15+ countries; 10,000+ critical-severity vulns found.** Critical infrastructure focus (power, water, healthcare, comms). The industry has effectively built the EO clearinghouse without the EO. → [`02` §1](./02-new-emerging.md#1-glasswing) `#security #glasswing #mythos #critical-infrastructure`

6. **Practical 1-2-3: AWS MCP Server GA (yesterday) + Managed Agents (cron + private MCP + sandbox) + Tool Search 85% context cut.** Installation order: **install AWS MCP Server → wire Managed-Agents schedule → set Fable-5/Sonnet-4.6/Haiku-4.5 routing → log per-step cost.** Ship one demo this week before the **Jun 15 Agent SDK metering** turns the dial. → [`03` §1](./03-practical-skills-and-tools.md#1-managed-agents) `#claude-code #aws #mcp #managed-agents`

7. **AlphaEvolve impact report — production-ships across genomics + quantum + Google infra.** **30%** DNA-variant-error reduction (PacBio/DeepConsensus); **10× lower** error quantum circuits on Google's **Willow** processor. The "AI does R&D" thesis ([Karpathy → Anthropic, 2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)) is **already shipping** at Google. → [`04` §1](./04-research-progress.md#1-alphaevolve) `#deepmind #alphaevolve #science`

8. **Skill read of the week:** the **"96-hour stack"** Anthropic queued ([2026-06-09](../2026-06-09/00-tldr.md)) collapses into a **single weekend artifact for you**: scheduled Managed Agent on AWS MCP infra, routing across Fable 5 / Sonnet 4.6 / Haiku 4.5, with a 5-clean / 5-planted eval set and per-step cost. Ship Sunday. → [`05` §2](./05-career-and-startup.md#2-shipping-bar) `#skills #careers #integration-engineer`

---

## One thing to DO this Wednesday

→ **Watch the Code w/ Claude Tokyo livestream** ([claude.com/code-with-claude/tokyo](https://claude.com/code-with-claude/tokyo)) — *with your eval-set notebook open*. Anytime an Anthropic engineer says a thing like "Dreaming gave Harvey ~6× task completion lift," **stop the video and ask: *"what would the equivalent metric for my weekend artifact look like?"*** The Tokyo demos are the **template you copy** when you write your artifact README on Sunday. Pair with installing the **AWS MCP Server** ([2026-06-09/03 §1](../2026-06-09/03-practical-skills-and-tools.md)) before lunch.

## Watchlist deltas

- 🟢 **LIVE TODAY — Code w/ Claude Tokyo** (livestream): watch for (a) APAC customer logos, (b) Managed-Agents production case studies, (c) any new SDK / MCP / Dreaming feature drops.
- ⏰ **T-1 — SpaceX IPO pricing (Thu Jun 11) → SPCX trading Fri Jun 12 @ ~$1.75T.** The public-market comp for the entire AI IPO pipeline (~$3.6T per Bloomberg).
- ⏰ **T-5 — Anthropic Agent SDK metering goes live (Sun Jun 15).** The 2026-05-22 routing plan needs to be wired this week. Fable 5 changes the matrix (see [`03` §1](./03-practical-skills-and-tools.md#1-managed-agents)).
- 🆕 **Mythos-class tier (Fable 5 + Mythos 5):** new thread — watch the **Jun 22 free-included window** end + comp/usage-tier renegotiation.
- 🔻 **Trump AI executive order:** still **POSTPONED** since [2026-05-22](../2026-05-22/01-big-lab-moves.md#1-eo-postponed) — Glasswing now fills the policy vacuum *de facto*. Status: 🟡-stalled, downgraded.
- 🆕 **OpenAI confidential S-1 (filed Jun 8, ~$852B):** filing confirmed, timeline soft. Track SEC first comment letter + Anthropic S-1 becoming public first.
- ➡️ **Anthropic IPO ($965B) — filed first:** filing-order inversion vs what we projected on [2026-05-22](../2026-05-22). Relative gap ($965B vs $852B) is the new headline.
- ➡️ **Karpathy → Anthropic pre-training (Claude-trains-Claude team):** still live; **AlphaEvolve's production-shipping at Google** is the parallel signal.
- 🆕 **AWS MCP Server GA + Apple Extensions framework (WWDC):** [2026-06-09 §2](../2026-06-09/02-new-emerging.md) — MCP is now the agent-tool standard across consumer browser (WebMCP), enterprise cloud (AWS MCP Server), and OS picker (Apple Extensions). Three surfaces ratified inside 30 days.
- 🆕 **Compute long-dated contracts:** Google → SpaceX **$920M/mo** + Anthropic → SpaceX **$1.25B/mo**, both through **2029**. SpaceX IPO tomorrow makes this counterparty *publicly tradeable*.
- 🆕 **Project Glasswing expansion (150 orgs / 15+ countries):** new thread — watch for first government joining.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Tokyo agenda in [`01` §1](./01-big-lab-moves.md#1-tokyo) + Fable 5 in [`01` §2](./01-big-lab-moves.md#2-fable-mythos) |
| 20 min | [`03` §1](./03-practical-skills-and-tools.md#1-managed-agents) (Managed Agents build path) + [`04` §1](./04-research-progress.md#1-alphaevolve) (AlphaEvolve impact) |
| Today | Watch Tokyo livestream + install AWS MCP Server (45 min) |
| Tonight | Re-cut the sanitiser project as a scheduled Managed Agent + private MCP (see [`03` §1](./03-practical-skills-and-tools.md#1-managed-agents)) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
