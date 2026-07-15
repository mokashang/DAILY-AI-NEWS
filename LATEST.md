# LATEST — pointer to the most recent edition

> **2026-07-15** — see [`2026-07-15/00-tldr.md`](./2026-07-15/00-tldr.md)

This file is auto-updated every edition so a one-click read of the latest TL;DR is always at the repo root.

---

## Today's headline

**Wednesday — the physical layer, the policy layer, and the education layer all move on the same day.** **[TSMC's Q2 preview](./2026-07-15/01-big-lab-moves.md#1-tsmc-q2)** posted a record June (+68% YoY) and **AI = 61% of $39.62B Q2 revenue**, N3 sold out through year-end, 2026 capex raised to $52–56B, full-year revenue guide raised to **>30%** — the compute buildout is now ratified in earnings, not projections. **[Beijing's anthropomorphic-AI rules take effect today](./2026-07-15/01-big-lab-moves.md#2-china-anthropomorphic)** — ByteDance's **Doubao (345M MAU)** and Alibaba's **Qwen** disable agent features that US labs face zero equivalent restrictions on. **[Anthropic launched Claude for Teachers yesterday](./2026-07-15/01-big-lab-moves.md#3-claude-for-teachers)** — free premium for US K-12 educators, FERPA + AFT + Detroit Public Schools pilot + open-source skills repo — the **sixth vertical pod** in ~10 weeks. **[Chai Discovery $400M Series C at $3.8B](./2026-07-15/02-new-emerging.md#1-chai)** (Index / Kleiner / Sequoia / Dimension) + **[Helsing $1.8B Series E at $18B](./2026-07-15/02-new-emerging.md#2-helsing)** (Europe's biggest defense round ever, JPMorgan Chase lead). **[OpenAI Codex Micro](./2026-07-15/02-new-emerging.md#3-codex-micro)** — OpenAI's first-ever hardware — ships today.

**For you:** the **Claude Science $30K grant deadline is TODAY**; the **Anthropic Applied — Education + Applied — Science** pods just opened and applicant pools haven't formed yet; **cross-provider prompt-cache** is now symmetric — one refactor, ~10× cheaper input on both Claude + GPT.

Full edition → [`2026-07-15/`](./2026-07-15/)

---

## One-thing-to-do (Wednesday July 15)

→ **SHIP the Claude Science grant application before 11:59 PM tonight** ([`2026-07-15/03 §1`](./2026-07-15/03-practical-skills-and-tools.md#1-claude-science-grant)). $30K in Claude credits + up to $2K Modal compute for ~50 projects. Open the application with your **novelty claim in the first two sentences** — the specific scientific artifact that becomes possible with $30K of Claude credits. Even a rejected application drops your name in the pipeline and produces a durable line on your resume.

→ **Apply to Anthropic Applied — Education + Applied — Science before Friday** ([`2026-07-15/05 §1`](./2026-07-15/05-career-and-startup.md#1-anthropic-verticals)). Both pods are days old — applicant pools haven't formed yet. A cover letter that opens with "yesterday's Claude for Teachers launch" or "today's Claude Science grant deadline" is signal density no template can match.

→ **Refactor one agent's prompt for cross-provider cache** ([`2026-07-15/03 §2`](./2026-07-15/03-practical-skills-and-tools.md#2-cache-lever)). Move timestamps / user-ids out of the prefix, order retrieved context oldest→newest, add explicit breakpoints on both Claude and GPT-5.6, log before/after in your artifact README.

→ **Bookmark TSMC Q2 full earnings tomorrow (Thu July 16)** — CoWoS capacity signals + Q3 outlook are the leading indicators for hyperscaler capex-linked hiring waves.
