# TL;DR — 2026-06-19 (Friday)

Sixty-second skim. **The government turned off a frontier model — and then turned it back on, six days later.** The single biggest story since this archive last published (May 22 → today; ~4-week gap, restart edition): on **June 12** Anthropic received a Commerce Department export-control directive and **disabled Fable 5 and Mythos 5 worldwide for foreign nationals — including its own foreign-national employees.** On **June 18**, after staff-level negotiations with the White House, **Fable 5 came back online.** First time in history the US government forced a publicly-deployed frontier model offline. The threading-needle stories underneath: **Trump's AI executive order is SIGNED (June 2)** — the postponed order from [2026-05-22](../2026-05-22/01-big-lab-moves.md#1-eo-postponed) landed, voluntary 30-day pre-release review (not 90 — labs won that fight); **OpenAI publicly disclosed its S-1 on June 8** (was confidential May 22); **Anthropic Seoul (June 17), Bengaluru announced** — frontier labs going regional; **Claude Code crosses ~$1B ARR**; and **Claude Code shipped a real subagent stack** (`/cd`, sub-agents-of-sub-agents up to 5 levels, `--safe-mode`, `fallbackModel`, Artifacts). For you: the export-control regime **just stratified frontier-lab hiring by passport**; the EO **opened the pre-deployment-eval lane for real**; and the FDE/Solutions market has now publicly absorbed Tomoro's 150 engineers via OpenAI DeployCo.

---

1. **Fable 5 / Mythos 5 SUSPENDED June 12, RESTORED June 18.** Commerce Department export-control directive → Anthropic disabled both models for *all foreign nationals globally* (incl. foreign-national Anthropic employees). Restored after senior-staff-level talks with White House. The ostensible trigger was a **jailbreak claim** (later reported as multi-agent extraction of weapons-synthesis pathways); the precedent is what matters — **a frontier model can now be turned off by phone call.** → [`01` §1](./01-big-lab-moves.md#1-fable-export-control) `#anthropic #export-control #policy #national-security`

2. **Trump AI EO SIGNED June 2 — the postponed order landed.** "Promoting Advanced AI Innovation and Security." Voluntary 30-day pre-release access for "covered frontier models" (NSA/CISA/NIST set a *classified* threshold); explicitly rejects mandatory licensing. Framework due **August 1**. The pre-deployment-eval career lane just went from "predicted" to **real**. → [`01` §2](./01-big-lab-moves.md#2-trump-eo-signed) `#policy #regulation #ai-assurance`

3. **OpenAI publicly disclosed S-1 on June 8** (was confidential May 22). Goldman + Morgan Stanley + JPMorgan; Sept-2026 listing window, **valuation expected >$1T**; **$25B annualized revenue but ~$1.22 lost per $1 earned**, full-year 2026 loss forecast ~$14B. Anthropic's own S-1 reportedly filed *a week earlier*. → [`01` §3](./01-big-lab-moves.md#3-openai-s1-public) `#openai #ipo #public-markets`

4. **Anthropic Seoul (June 17) + Bengaluru, India** office announced — **regional expansion = regional Integration / Solutions roles opening.** Plus TCS + DXC partnerships for regulated-industry Claude rollout. → [`02` §1](./02-new-emerging.md#1-anthropic-global) `#anthropic #global #integration-eng`

5. **Claude Code at ~$1B ARR; ~300K firms now on Anthropic tools.** That's the single loudest product-traction signal of Q2; it's also why this week's Claude-Code updates (below) actually matter. → [`02` §2](./02-new-emerging.md#2-claude-code-arr) `#anthropic #claude-code #arr`

6. **Claude Code June drop — real subagent stack landed.** `/cd` mid-session directory change without cache-rebuild; **sub-agents can spawn sub-agents (5-level cap)**; `--safe-mode` for troubleshooting; `fallbackModel` (up to 3); **Artifacts in Claude Code** (live shareable web pages); **Workload Identity Federation (GA June 17)** = keyless auth across SDK/Claude Code; **doubled rate limits**. → [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-june-drop) `#claude-code #subagents #playbook`

7. **Research: "When AI Builds Itself" (Anthropic, June 4)** — formally argues AI systems are approaching recursive self-improvement and proposes a coordinated pause. Pairs with the Karpathy → Anthropic hire ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)) and a **deep-research-eval benchmark wave** (DeepResearch Bench · AutoResearchBench · DREAM · FinDeepResearch). → [`04` §1](./04-research-progress.md#1-self-improvement-paper) `#research #arxiv #safety #recursive-self-improvement`

8. **Skill read of the month:** the export-control regime just made **"who can touch which weights"** a hiring filter at every frontier lab. **Read your own passport into the job-search strategy** ([`05` §1](./05-career-and-startup.md#1-passport-strategy)) and **anchor your portfolio on the EO's pre-deployment-eval vocabulary** ([`05` §2](./05-career-and-startup.md#2-eo-lane-real)) — both lanes just got real, not predicted.

---

## One thing to DO this Friday

→ **Sit down for 30 minutes with the EO text** ([`01` §2 sources](./01-big-lab-moves.md#2-trump-eo-signed)) and write a **one-page personal "pre-deployment-eval position paper"** — what *you* would test, what evidence would qualify a model as "safe to release to trusted partners," and what the report deliverable should look like. Save as `apps/pre-deployment-eval-position-paper.md` in your portfolio repo. This is the **single highest-leverage hour you'll spend in June** — three downstream uses: (a) cover-letter substance for Anthropic Solutions / OpenAI FDE / bank-AI-assurance roles, (b) the README framing for the dual-model sanitiser carried from [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact), (c) the spine of a vertical startup pitch in the assurance lane.

## Watchlist deltas

- 🟢 **Trump AI executive order:** **SIGNED June 2** (was postponed on 2026-05-22). Voluntary 30-day window survived; framework deadline Aug 1. Status 🟡-stalled → 🟢-live. The pre-deployment-eval lane is now hiring-ready, not predicted.
- 🆕 **Export-control regime for frontier models (June 12):** new top-priority thread — track how Anthropic implements foreign-national access controls, whether OpenAI/Google receive the same directive, and what the **classified covered-model threshold** turns out to look like.
- 🆕 **Anthropic Seoul + Bengaluru offices:** new thread — regional hiring queues (APAC + South Asia) are thin and just opened.
- 🆕 **Claude Code subagent-of-subagent (5-level cap):** new thread — the orchestration playbook from [2026-05-21/03](../2026-05-21/03-practical-skills-and-tools.md) just got recursive. Cost-tracking matters more, not less.
- 🆕 **Deep-research eval benchmark wave (DeepResearch Bench · AutoResearchBench · DREAM · FinDeepResearch):** new thread — the real-tool benchmark line from [2026-05-22/04](../2026-05-22/04-research-progress.md) extended to *research-agents* specifically. FinDeepResearch is the one to read first if you're in financial-services applications.
- ➡️ **OpenAI S-1 / Sept-IPO trajectory:** still live; the public disclosure on June 8 means the financials become legible in 2–3 months.
- ➡️ **Anthropic Agent SDK metering (June 15):** *passed* — the cost-routing skill in [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) is now load-bearing on every bill.
- ➡️ **Karpathy at Anthropic / "use Claude to train Claude":** ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)) thematically reinforced by the "When AI Builds Itself" paper.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the export-control story in [`01` §1](./01-big-lab-moves.md#1-fable-export-control) |
| 20 min | [`01` §1](./01-big-lab-moves.md#1-fable-export-control) (export controls) + [`01` §2](./01-big-lab-moves.md#2-trump-eo-signed) (EO signed) + [`05` §1](./05-career-and-startup.md#1-passport-strategy) (passport strategy) — the three deepest signals |
| Today | [`05` §3](./05-career-and-startup.md#3-action-pre-deployment-paper) — 30-min pre-deployment-eval position paper |
| This weekend | [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-june-drop) — install the June Claude Code drop + redo the subagent team with `fallbackModel` configured |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.

> **Restart note.** This edition resumes the daily after a 4-week pause (last edition: [2026-05-22](../2026-05-22/)). Stories framed to *close out* any thread that resolved during the pause (EO signed; OpenAI S-1 public; Agent SDK metering activated) so the archive's threading stays intact. Daily cadence resumes from here.
