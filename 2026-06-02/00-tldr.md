# TL;DR — 2026-06-02 (Tuesday)

Sixty-second skim. **Two of the three biggest watchlist threads resolved in a single 36-hour window — and they resolved in *opposite* directions.** **Anthropic beat OpenAI to the SEC** with a confidential S-1 yesterday (Mon, Jun 1) at a **$965B valuation**, targeting an **October listing** — flipping the order of who-goes-public-first that we tracked all of last week. And the **Trump AI executive order — postponed on 2026-05-22 — was *signed today* as "Promoting Advanced Artificial Intelligence Innovation and Security"**, but in a *much* lighter-touch form than the May 21 draft. Meanwhile **Claude Opus 4.8 quietly shipped last Thursday (May 28)** with **dynamic workflows** + a **3× cheaper fast mode** + **69.2% SWE-Bench Pro** — and it changes the model-routing table from [2026-05-22/03](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) before your next agent run. For you: the **public-market turn that was a thesis last week is now a filing**, and the **routing table you're committing to skills around just got rewritten**.

⚠️ **Archive gap note:** No editions were filed for **2026-05-23 → 2026-06-01** (11 days). Stories from that window are summarized inline below with sources; ask if you want a backfill pass.

---

1. **Anthropic confidentially files draft S-1 (Mon, Jun 1).** Beat OpenAI to the SEC. **$965B post-money** (after last week's $65B Series H led by Altimeter/Dragoneer/Greenoaks/Sequoia — *valuation more than doubled from $380B in Feb*). **~$47B annualized revenue run-rate.** Target listing **October 2026**. → [`01` §1](./01-big-lab-moves.md#1-anthropic-s1) `#anthropic #ipo #public-markets`

2. **Trump signs AI EO TODAY: "Promoting Advanced Artificial Intelligence Innovation and Security."** The version that survived is **innovation-first, regulation-light** — the heavy 90-day pre-release review from the May 21 draft was **dropped or softened**; cybersecurity-clearinghouse pieces remain. Doctrine stated out loud: *don't get in the way of US labs leading.* → [`01` §2](./01-big-lab-moves.md#2-trump-eo-signed) `#policy #regulation #eo`

3. **OpenAI S-1 imminent — "in the coming weeks."** Anthropic going first changes the framing: now it's "who prices second after the market gives a read on the first." Watch whether OpenAI's window pulls back from September (the May 22 plan) toward late-Q3/Q4. → [`01` §3](./01-big-lab-moves.md#3-openai-s1-status) `#openai #ipo`

4. **Claude Opus 4.8 shipped (Thu, May 28).** **SWE-Bench Pro 69.2%** (vs 64.3% on 4.7), **OSWorld-Verified 83.4%**, **Online-Mind2Web 84%** (strongest browser-agent model tested), **Humanity's Last Exam 57.9%**. **"Dynamic workflows"** in Claude Code (model scopes work as it goes — multi-hour refactors without fixed plans). **Fast mode at 2.5× speed, 3× cheaper than 4.7's fast mode** ($10/$50 per M). Same base pricing as 4.7 ($5/$25). → [`02` §1](./02-new-emerging.md#1-opus-48) `#anthropic #model-release #claude-code`

5. **Grok V9-Medium completed training (May 25), public release mid-June.** **1.5T params**, **3× larger than current production Grok**. Musk explicitly targeting *coding lead* — the same lane Anthropic just put a 5-point benchmark moat around. → [`02` §2](./02-new-emerging.md#2-grok-v9) `#xai #grok #model-release`

6. **Agentic multimodal is the research wave you can't skip — DeepEyesV2 + WebWatcher + AutoResearchClaw + Metis.** Pattern: **models actively invoke tools (code, search, browser) as part of their reasoning loop** — and the new benchmarks (RealX-Bench, BrowseComp-VL) score them against real-world integrated tasks, not synthetic ones. AutoResearchClaw is the "Claude does the research paper" version of the Karpathy/Anthropic recursive-self-improvement thread. → [`04` §1](./04-research-progress.md#1-agentic-multimodal) `#research #arxiv #agents #multimodal`

7. **Practical: re-cost the routing table tonight — Opus 4.8 *fast mode* is now cheap enough to put in a worker seat for some tasks.** The May 22 default (**Opus orchestrator + Sonnet workers ≈ 40% cheaper**) still holds for most jobs, but for **browser-agent / computer-use / long-horizon refactor** legs, **Opus 4.8 fast mode** beats Sonnet 4.6 on quality at workable cost. **T-13 days to June 15 Agent SDK metering** — this is the last week to re-cost without the meter punishing you. → [`03` §1](./03-practical-skills-and-tools.md#1-reroute-opus48) `#claude-code #cost #routing`

8. **Skill read of the week:** the same theme three different ways — **Anthropic's S-1 (price the work), Opus 4.8 dynamic workflows (compress the work), DeepEyesV2/AutoResearchClaw (automate the work).** The frontier's leverage is moving *up the stack*: from "I can prompt" → "I can route, verify, and cost" → "I can run a system that builds systems." That's the gradient your portfolio should be climbing. → [`05` §2](./05-career-and-startup.md#2-skill-gradient) `#skills #careers`

---

## One thing to DO this Tuesday

→ **Re-cost your dual-model "sanitiser" artifact ([carried from 2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact)) against the *new* routing table** — swap one Sonnet worker for Opus 4.8 fast mode on the browser/computer-use leg, log per-step cost, and **add a one-paragraph "what changed on June 2"** to the README (signals you track the frontier in real time, not in season). Then **apply to 1 Anthropic Solutions / FDE role today** — public-S-1 hiring cycles typically *tighten* requirements within ~30 days of filing; the window where the JD is still loose is right now ([`05` §1](./05-career-and-startup.md#1-s1-hiring-window)).

## Watchlist deltas

- ✅ **Anthropic IPO path:** *RESOLVED — filed.* Closed thread. Open new sub-thread: roadshow window, public S-1 disclosure (revenue mix, Claude-Code share, ad-revenue *non*-disclosure), and lockup math for any equity you'd receive at a public co.
- ✅ **Trump AI EO:** *RESOLVED — signed today, in lighter form.* Closed the "will it sign?" thread. Open new sub-thread: which provisions survived intact vs which were watered down (the cyber-clearinghouse half was always the most durable).
- 🔻 **OpenAI S-1:** was "filing as early as today" on May 22; **not filed by June 2** (10 working days late vs the May 22 plan). Status: 🟡 → 🟡-slipping. Watch for any Friday filing pattern.
- 🆕 **Claude Opus 4.8 / dynamic workflows:** new thread — watch what people *ship* with multi-hour autonomous refactor; this is where 4.8 either becomes the new floor or quietly retracts.
- 🆕 **Grok V9-Medium mid-June release:** new thread — if Musk's "3× bigger, coding-lead" framing turns into real benchmark numbers, it's the first credible non-Anthropic threat to the Claude-Code adoption wedge.
- 🆕 **Agentic multimodal benchmarks (RealX-Bench / BrowseComp-VL):** new thread — successor to MCP-Atlas / Toolathlon from 2026-05-22.
- ➡️ **Anthropic Agent SDK metering (Jun 15):** **T-13 days.** Re-costing is now a billable risk, not a hypothetical.
- ➡️ **Karpathy → Anthropic pre-training team:** still live from 2026-05-22; AutoResearchClaw is the open-source rhyme.
- ➡️ **Meta cuts in execution / restructuring under Wang's Superintelligence Labs:** still live; quiet on the wire this week — watch for resume volume on LinkedIn.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the EO signed + the Anthropic S-1 in [`01` §1–2](./01-big-lab-moves.md) |
| 20 min | [`02` §1](./02-new-emerging.md#1-opus-48) (Opus 4.8 — the model your routing table depends on) + [`04` §1](./04-research-progress.md#1-agentic-multimodal) (agentic-multimodal wave) |
| Today | [`05` §1](./05-career-and-startup.md#1-s1-hiring-window) — apply to 1 Anthropic Solutions/FDE role inside the post-S-1 30-day window |
| Tonight | [`03` §1](./03-practical-skills-and-tools.md#1-reroute-opus48) — re-cost the routing table; swap Opus 4.8 fast mode into the right seat |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
