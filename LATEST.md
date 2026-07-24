# LATEST — pointer to the most recent edition

> **2026-07-24** — see [`2026-07-24/00-tldr.md`](./2026-07-24/00-tldr.md)

This file is auto-updated every edition so a one-click read of the latest TL;DR is always at the repo root.

---

## Today's headline

**Friday — the China-distillation fight goes federal, the "sell agents not models" pivot goes 3-for-3, and Claude Opus 5 didn't ship.** In one 48-hour window: (a) **OSTP Director Michael Kratsios publicly accused Moonshot of covertly distilling Anthropic's Fable (public since July 1) to build Kimi K3** — plus using GB300 chips accessed via Thailand — **Treasury weighing sanctions** [`01 §1`](./2026-07-24/01-big-lab-moves.md#1-moonshot-fable); (b) **OpenAI shipped "Presence" (Wed Jul 22)** — governed voice+chat agent platform delivered with FDEs — making all three US frontier labs sell the *same* product shape (Presence · Anthropic Managed Agents · Google ADK 2.0) [`01 §2`](./2026-07-24/01-big-lab-moves.md#2-openai-presence); (c) the widely-predicted **Claude Opus 5 launch (July 23)** did not happen — Anthropic silent, product velocity elsewhere very high [`01 §3`](./2026-07-24/01-big-lab-moves.md#3-opus5-noshow); (d) **DeepSeek endpoints retire 15:59 UTC TODAY** with asymmetric migration — `deepseek-reasoner` → **`v4-flash`**, NOT `v4-pro` [`03 §1`](./2026-07-24/03-practical-skills-and-tools.md#1-deepseek-deprecation).

**For you:** the FDE lane got its clearest post-launch req-open window of the summer, the distillation story hands you a distinct second hiring lane (model-IP protection / cross-model data-flow auditing), and there's a 30-minute production hygiene task due before end of business.

Full edition → [`2026-07-24/`](./2026-07-24/)

---

## One-thing-to-do (Friday July 24)

→ **Ship the "Presence vs Managed Agents vs ADK" one-pager on your public channel today** ([`2026-07-24/05 §1`](./2026-07-24/05-career-and-startup.md#1-fde-catalyst)) — structure it around the five components every managed-agent platform now has (SOP schema, permission model, escalation, simulation harness, continuous-improvement loop). This single artifact opens more FDE-hiring conversations over the next 30 days than any other Friday deliverable.

→ **⏰ HARD DEADLINE 15:59 UTC:** audit any DeepSeek client. If `deepseek-reasoner` appears anywhere, migrate to `v4-flash` (not `v4-pro`) — silent capability downgrade if you route wrong ([`2026-07-24/03 §1`](./2026-07-24/03-practical-skills-and-tools.md#1-deepseek-deprecation)).

→ **Read [`2026-07-24/05 §2`](./2026-07-24/05-career-and-startup.md#2-distillation-hiring-signal)** — the Kimi K3 distillation accusation opens a distinct second hiring lane (Ring 1: labs' T&S teams · Ring 2: enterprise CIO/CISO orgs · Ring 3: Big-4 AI compliance). Add the new keywords to LinkedIn + resume this weekend.
