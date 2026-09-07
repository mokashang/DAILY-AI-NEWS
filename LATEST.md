# LATEST — pointer to the most recent edition

> **2026-09-07** — see [`2026-09-07/00-tldr.md`](./2026-09-07/00-tldr.md)

This file is auto-updated every edition so a one-click read of the latest TL;DR is always at the repo root.

---

## Today's headline

**Monday (US Labor Day) — the frontier shipped four flagships in 72 hours, Nvidia bought the open-weights layer for $12.9B, and Claude finished a machine-checked proof of Fermat's Last Theorem in Lean — all inside one week off the labor holiday.** **Anthropic Fable 5.1 + Mythos 5.1 (Sept 1)** — cache reads cut 4× ($1 → $0.25/M); effective cost –25% typical / –45% agentic [`01 §1`](./2026-09-07/01-big-lab-moves.md#1-fable-mythos-5-1). **Meta Muse Spark 1.3 (Sept 2)** — –20% tool calls, –25% tokens, paid API opens day-0 [`01 §2`](./2026-09-07/01-big-lab-moves.md#2-muse-spark). **Google Gemini 3.8 Flash + Flash Cyber (Sept 2)** — $0.75/$3.75 through Dec 31, doubles Jan 1; Lyria 3.5 into Gemini app + API Sept 4 [`01 §3`](./2026-09-07/01-big-lab-moves.md#3-gemini-3-8-flash). **OpenAI GPT-6 Astra (Sept 3)** — first model to hit Critical cybersecurity tier; 100% ExploitBench, discovered 2 zero-days during eval [`01 §4`](./2026-09-07/01-big-lab-moves.md#4-gpt-6-astra). **Nvidia → Hugging Face $12.93B (definitive Sept 2)** — open-weights layer consolidates to a chipmaker [`02 §1`](./2026-09-07/02-new-emerging.md#1-nvidia-hf). **Claude formalized Fermat's Last Theorem in Lean via Prove2Me (Sept 4)** — 11 days, ~6B output tokens, 13M-line proof, largest Lean proof ever [`04 §1`](./2026-09-07/04-research-progress.md#1-fermat-lean). **Anthropic Fellows Cohort 3 (Aug 2027 start) applications reopen this month** [`05 §1`](./2026-09-07/05-career-and-startup.md#1-fellows-reopens).

**For you:** the base-token price war is now a *cache-price* war (Anthropic 4× cut), the cyber-SKU split (Mythos + Daybreak + Flash Cyber) is the first regulated AI category in practice, and the highest-EV solo application of the quarter (Fellows Cohort 3) is opening this month.

Full edition → [`2026-09-07/`](./2026-09-07/)

---

## One-thing-to-do (Labor Day Mon Sep 7 → Fri Sep 11)

→ **Today (60 min): Fellows watchlist + 1-pager draft.** Bookmark [alignment.anthropic.com](https://alignment.anthropic.com/2025/anthropic-fellows-program-2026/), set a weekly Monday check, pre-write the 1-page research direction now. [`05 §1`](./2026-09-07/05-career-and-startup.md#1-fellows-reopens).

→ **Today (30 min): Cache reprice audit.** Migrate one running workload to Fable 5.1 with prompt caching turned on; capture before/after per-1K-request cost; screenshot the delta as your portfolio artifact. [`03 §1`](./2026-09-07/03-practical-skills-and-tools.md#1-cache-reprice).

→ **This week (Wed–Fri, 4–6 hrs total): ship the Labor Day artifact.** A single-repo agent team — Fable 5.1 planner → Muse Spark 1.3 or Gemini 3.8 Flash worker → Haiku 4.5 verifier + a Fermat-inspired external verifier stage; per-step cost log; publish repo + 90-sec Loom. [`03 §4`](./2026-09-07/03-practical-skills-and-tools.md#4-multi-agent-lean-lessons).

→ **This week: apply to one Anthropic Applied AI Engineer (FDE) role.** ~60% wash on the customer-conversation round — practice with a friend before submitting. [`05 §2`](./2026-09-07/05-career-and-startup.md#2-fde-market).

→ **Watch for the Daybreak-adjacent security FDE lane** (GPT-6 Astra tripped Critical — 20–40 new postings expected inside 60 days). If you have any security background, this is the highest-conviction application to write this month. [`05 §3`](./2026-09-07/05-career-and-startup.md#3-cyber-fde-lane).
