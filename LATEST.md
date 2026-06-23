# LATEST — pointer to the most recent edition

> **2026-06-23** — see [`2026-06-23/00-tldr.md`](./2026-06-23/00-tldr.md)

This file is auto-updated every edition so a one-click read of the latest TL;DR is always at the repo root.

---

## Today's headline

**Tuesday — the June 22 Anthropic cliff lands; OpenAI plants a Daybreak flag the same week.** **Anthropic Fable 5 leaves Pro / Max / Team / seat-Enterprise plan limits today** as scheduled since [2026-06-15](./2026-06-15/01-big-lab-moves.md) — bills at API list rates ($10/M in · $50/M out, **2× Opus 4.8**). **Sonnet 4.6 + Opus 4.8 + Haiku 4.5 unchanged** — the broader Agent SDK metering rollout remains *paused* per [2026-06-21 watchlist](./2026-06-21/00-tldr.md); today's change is Fable-5-specific. (Fable 5 + Mythos 5 access was already restored [June 18](./2026-06-21/01-big-lab-moves.md#2-fable-restored).) **OpenAI Daybreak expanded Mon June 22** — four pieces shipped together: **GPT-5.5-Cyber GA**, **Codex Security plugin update** that now *patches* not just scans (30M+ commits / 70K+ human-confirmed fixes since March), a **partner program**, and **"Patch the Planet"** OSS. Help Net framing: *"Daybreak wants to own the patch, not just the bug."* For you (Anthropic-stack, AI-Integration-Engineer-lane): **re-route Fable 5 from daily-driver → verifier-only**, and **apply to one AI-cyber role this week** — the lane was minted on Monday.

Full edition → [`2026-06-23/`](./2026-06-23/)

---

## One-thing-to-do (Tuesday)

→ **Re-route your model defaults before your next agent run.** In Claude Code / Cursor / your CLI: drop default **Fable 5 → Sonnet 4.6** (or Opus 4.8 with a credits budget); explicitly tag Fable 5 as **verifier-only**. The 30-minute fix + cost-logging recipe is in [`2026-06-23/03 §1`](./2026-06-23/03-practical-skills-and-tools.md#1-reroute). Pair it with the orchestrator/worker baseline from [2026-05-22/03 §1](./2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost).

→ **Apply to one AI-cybersecurity role this week** — the lane was minted by Monday's Daybreak launch + the EO cyber-clearinghouse half. Target list in [`2026-06-23/05 §2`](./2026-06-23/05-career-and-startup.md#2-cyber-lane): Daybreak FDE at OpenAI · Solutions/Mythos-eng at Anthropic · Exaforce · CrowdStrike/Wiz/Snyk (likely partners) · JPM/GS/BofA AI Assurance.

→ **Ship one Codex-Security-validated patch PR on an OSS repo** before the partner-program closes the free-tier window. Recipe in [`2026-06-23/03 §2`](./2026-06-23/03-practical-skills-and-tools.md#2-codex-security). This is a *single weekend artifact* that answers three interview questions (agent verification + real-tool eval + cost discipline) and pivots cleanly into the cyber-lane.

→ **Read** [`2026-06-23/04 §1 StateGen`](./2026-06-23/04-research-progress.md#1-stategen) — state-grounded multi-agent synthetic data; the "backend-is-truth" pattern that eliminates tool-call hallucinations *by construction*. The most directly useful paper for an Integration-Engineer interview this month.
