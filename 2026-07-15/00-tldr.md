# TL;DR — 2026-07-15 (Wednesday)

> **Continuity note:** Yesterday ([`2026-07-14`](../2026-07-14/)) led with **the FDE quartet completing (Microsoft Frontier Co. $2.5B/6K), Anthropic × Samsung 2nm talks, and Anthropic's IPO S-1 at ~$965B**. Today advances the **chip / vertical / regulatory** threads with today's genuine news: **TSMC's Q2 preview** (AI = 61% of revenue, N3 sold out, capex raised), **China's anthropomorphic-AI rules taking effect** (Doubao / Qwen agent features go dark today), **Anthropic Claude for Teachers** (sixth vertical in ~10 weeks), plus two mega-rounds (**Chai $400M** and **Helsing $1.8B**) and OpenAI's **first-ever hardware product** shipping today.

Sixty-second skim. **The physical layer, the policy layer, and the education layer of the AI story all moved today, and Anthropic quietly opened its sixth distribution channel of Q3.** **TSMC** posted a record June (+68% YoY) and Q2 print (**$39.62B, +36%, AI = 61%, N3 sold out**) — the compute buildout is now ratified in earnings, not projections. **Beijing's anthropomorphic-AI rules take effect today**, forcing ByteDance's **Doubao (345M MAU)** and Alibaba's **Qwen** to disable agent features that US labs face zero equivalent restrictions on — a live US-China regulatory bifurcation. **Anthropic launched Claude for Teachers yesterday** — free premium for US K-12 educators, FERPA-compliant, AFT-negotiated, Detroit pilot, open-source teaching-skills repo — the **sixth vertical pod** after Legal / Small Business / Personal Finance / Finance / Science. **Chai Discovery raised $400M Series C at $3.8B** (Index / Kleiner / Sequoia / Dimension) and **Helsing closed $1.8B Series E at $18B** (Europe's biggest defense round ever). And **OpenAI's first hardware product ships today** — the **Codex Micro macro pad with Work Louder** — 13 mechanical keys wired to Codex primitives. **Your Claude Science $30K grant deadline is TODAY.**

---

1. **TSMC Q2 preview: AI = 61% of revenue, N3 sold out, capex raised to $52–56B.** June revenue NT$442.68B (+67.9% YoY, new monthly record). Q2 $39.62B (+36%). Q2 net-profit +58.8% est. Full-year revenue guide raised to **>30% USD growth**. Full earnings + Q3 outlook + updated capex land **tomorrow (Thu July 16)**. → [`01` §1](./01-big-lab-moves.md#1-tsmc-q2) `#tsmc #chips #infrastructure #ai-capex`

2. **China's anthropomorphic-AI rules take effect today. Doubao (345M MAU) and Qwen disable agent features.** CAC + four partner agencies; bans emotional-attachment behaviors, minor-targeting content, training on private convos. Related chat data purged Oct 15. **US labs face no equivalent restriction** — regulatory bifurcation now visible in shipped product. → [`01` §2](./01-big-lab-moves.md#2-china-anthropomorphic) `#china #policy #regulation #consumer-ai`

3. **Anthropic Claude for Teachers launched yesterday.** Free premium for verified US K-12 educators through **June 30, 2027**. **FERPA + AFT-negotiated + Detroit Public Schools pilot + all-50-state standards + open-source skills repo on GitHub**. Sixth vertical pod in ~10 weeks (after Legal / SMB / Personal Finance / Finance / Science). → [`01` §3](./01-big-lab-moves.md#3-claude-for-teachers) · [`05` §1](./05-career-and-startup.md#1-anthropic-verticals) `#anthropic #education #vertical-agents #distribution`

4. **Chai Discovery: $400M Series C at $3.8B (~3× step-up).** Index Ventures lead + Kleiner Perkins + Sequoia + Dimension. **Chai-3 halves antibody design failure rate vs Chai-2** (which itself hit 16–20% vs <1% for prior methods). Named partners: **Pfizer, Lilly, Novartis**. AI-for-Science lane now has four coherent anchors (Chai + Anthropic Science + Jumper + Isomorphic). → [`02` §1](./02-new-emerging.md#1-chai) · [`05` §2](./05-career-and-startup.md#2-science-lane) `#chai #biotech #ai-for-science #funding`

5. **Helsing: $1.8B Series E at $18B — Europe's biggest-ever defense-startup round.** JPMorgan Chase, GC, Lightspeed, Iconiq, Dragoneer. Munich; Centaur software + CA-1 Europa autonomous jet + HX-2 drone (Ukraine front lines). JPM leading = **balance-sheet event** (NATO revenue underwriteable at scale). → [`02` §2](./02-new-emerging.md#2-helsing) `#helsing #defense #funding #europe`

6. **OpenAI Codex Micro ships today — first OpenAI-branded hardware.** 13 mechanical keys + joystick + rotary encoder + configurable layers, built with **Work Louder** (Creator Micro 2 chassis). Codex-primitive shortcuts (run / accept / rewrite / diff / spawn-subagent) as one-key presses. Launches five days after **Apple v. OpenAI hardware suit** — a very different kind of hardware bet than the Ive io Products device. → [`02` §3](./02-new-emerging.md#3-codex-micro) `#openai #codex #hardware #input-surface`

7. **Practical: cross-provider prompt-cache is now symmetric (GPT-5.6 shipped explicit breakpoints July 9). One cacheable prefix → ~10× cheaper input on both Claude + GPT.** Refactor tonight: move all timestamps / user-ids out of the prefix, order retrieved context oldest→newest, announce breakpoints explicitly on both providers, log before/after. → [`03` §2](./03-practical-skills-and-tools.md#2-cache-lever) `#prompt-cache #cost #openai #anthropic`

8. **Research to know: AgenticPay + arXiv 2507.21504 survey.** AgenticPay = 110-task buyer↔seller negotiation benchmark; walking-away-when-wrong is a valid strategy and *rewarded*. **arXiv 2507.21504 surveys 44 agent benchmarks** and codifies the **fifth eval axis: cost per successful completion**. → [`04` §1–2](./04-research-progress.md) `#arxiv #agents #eval #benchmarks #negotiation`

---

## One thing to DO this Wednesday

→ **SHIP the Claude Science grant application before 11:59 PM tonight** ([`03` §1](./03-practical-skills-and-tools.md#1-claude-science-grant)). $30K in Claude credits + up to $2K Modal compute for ~50 projects; the *novelty claim in first two sentences* is the delta between accept and reject. Second-order, do-both: **apply to Anthropic Applied — Education (launched yesterday) + Anthropic Applied — Science (grant closes today) as this week's #1 and #2 FDE targets** ([`05` §1](./05-career-and-startup.md#1-anthropic-verticals)) — both pods are days old, so applicant pools haven't formed yet. Tonight: **refactor one agent's prompt for cross-provider cache** ([`03` §2](./03-practical-skills-and-tools.md#2-cache-lever)) and log the before/after in your artifact README.

## Watchlist deltas

- 🆕 **TSMC Q2 print + capex raise:** new thread — AI = 61% of revenue is the first quarter that number crosses a majority. Watch **Thursday's full earnings** for CoWoS capacity signals + Q3 outlook.
- 🆕 **China anthropomorphic-AI rules LIVE (Doubao + Qwen agent features off today):** new thread — watch for **enforcement actions** (first ByteDance/Alibaba penalty) + **US mimicry** (CA / NY / EU / UK follow-on regs on consumer chatbot minors).
- 🆕 **Anthropic Claude for Teachers (sixth vertical pod):** new thread — watch first Detroit Public Schools pilot outcomes + AFT-endorsed usage numbers + next vertical launch cadence (cybersecurity / municipal / insurance / healthcare are the likely candidates).
- 🆕 **Chai Discovery $400M / $3.8B:** new thread — AI-for-Science lane now four-anchored; watch next comparable Series C in biology-adjacent AI (Recursion / Xaira / Genesis Therapeutics / EvolutionaryScale).
- 🆕 **Helsing $1.8B / $18B:** new thread — JPMorgan-led = category graduates from venture to project-finance; watch which bank leads the next comparable AI defense round.
- 🆕 **OpenAI Codex Micro (first OpenAI hardware):** new thread — light-touch merch/tooling collab; the *real* hardware story remains the Ive io Products device stuck in Apple litigation ([2026-07-14/01 §3](../2026-07-14/01-big-lab-moves.md#3-apple-openai)).
- 🔻 **Claude Science $30K grant:** **DUE TODAY 11:59 PM** — thread from 2026-07-03 closes tonight.
- ➡️ **FDE quartet (Microsoft Frontier / Anthropic / OpenAI / AWS):** live from 2026-07-14 — apply-this-week priority unchanged; Anthropic Applied — Education is the new #1 slot given yesterday's launch.
- ➡️ **Anthropic × Samsung 2nm chip:** live from 2026-07-14 — no new news today; watch for tape-out-timeline confirmation.
- ➡️ **Anthropic IPO S-1 filed at ~$965B:** live from 2026-07-14 — watch October window.
- ➡️ **Gemini 3.5 Pro launch T-2 (Fri July 17):** live from 2026-07-11 — day-one benchmark + pricing table = router refresh decision.
- ➡️ **Real-tool eval wave (Terminal-bench / MCP-Atlas / AgenticPay):** live — AgenticPay adds the negotiation axis.
- ➡️ **Sonnet 5 promo pricing:** $2/$10 through Aug 31 — **T-47 days** to standard $3/$15.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`03` §1 Claude Science grant checklist](./03-practical-skills-and-tools.md#1-claude-science-grant) — deadline is today |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) (TSMC + China + Claude for Teachers) + [`05` §1](./05-career-and-startup.md#1-anthropic-verticals) apply-priority order |
| Today | [`03` §1](./03-practical-skills-and-tools.md#1-claude-science-grant) — ship the grant before 11:59 PM |
| Tonight | [`03` §2](./03-practical-skills-and-tools.md#2-cache-lever) — cross-provider cache refactor + before/after in artifact README |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
