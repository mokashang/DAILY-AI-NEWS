# LATEST — pointer to the most recent edition

> **2026-07-03** — see [`2026-07-03/00-tldr.md`](./2026-07-03/00-tldr.md)

This file is auto-updated every edition so a one-click read of the latest TL;DR is always at the repo root.

---

## Today's headline

**Friday — Anthropic answers the token-billing revolt with three shipped products in 48 hours; the compute floor adds a second neocloud; Cloudflare puts a paywall between agents and the web.** Anthropic ships the **[Claude apps gateway for Bedrock + Google Cloud](./2026-07-03/01-big-lab-moves.md#1-gateway)** — self-hosted control plane, SSO, spend caps, failover, published open protocol — plus **[Claude Science](./2026-07-03/01-big-lab-moves.md#2-claude-science)** (AI workbench for researchers; **$30K credit-grant deadline July 15**) plus **[Artifacts-in-Claude-Code](./2026-07-03/01-big-lab-moves.md#3-limits-artifacts)** + doubled rate limits plus a **[new public constitution](./2026-07-03/01-big-lab-moves.md#4-constitution)**. Meanwhile **[SoftBank stands up SB Neo](./2026-07-03/02-new-emerging.md#1-sb-neo)** (10 GW by 2030), **[Together AI closes $800M at $8.3B](./2026-07-03/02-new-emerging.md#2-together)**, and **[Cloudflare splits AI traffic into Search / Agent / Training](./2026-07-03/02-new-emerging.md#3-cloudflare)** with **Sept 15 defaults blocking Agent + Training on ad-monetized pages**. **For you: the gateway is the FDE demo of Q3, the neocloud lane is the second-strongest hire lane after FDE, and the $30K Claude Science grant is a real startup on-ramp with 12 days to the deadline.**

Full edition → [`2026-07-03/`](./2026-07-03/)

---

## One-thing-to-do (Weekend 07-04 → 07-06)

→ **Deploy the Claude apps gateway on a personal AWS or GCP account + one live-Artifact long-running agent, push to a public `personal-fde-lab` repo.** [`2026-07-03/03 §1`](./2026-07-03/03-practical-skills-and-tools.md#1-gateway-deploy). Sat morning: gateway build (Fargate + RDS or Cloud Run + Cloud SQL), wire SSO, cap spend at $10/day, run outage drill (revoke Bedrock IAM → observe Vertex failover). Sat afternoon: [Artifacts-in-Claude-Code recipe](./2026-07-03/03-practical-skills-and-tools.md#2-artifacts-recipe) — one long refactor with live status page. Sun: [rewrite routing config](./2026-07-03/03-practical-skills-and-tools.md#3-routing) — add Together AI, Meta Compute, Cloudflare `Agent` identifier. **One weekend = the strongest single artifact you can put in front of an FDE recruiter in Q3.**

→ **Apply Anthropic FDE Applied AI Monday** with the gateway repo attached + a 1-page "Karp / Uber / Lindy → gateway → what I'd do about it" writeup. [`2026-07-03/05 §1`](./2026-07-03/05-career-and-startup.md#1-fde-surge).

→ **Draft the Claude Science credit-grant proposal by Thu July 9.** Deadline **Wed July 15** ($30K credits × up to 50 projects). Frame around a stepwise-verifiable science-agent workflow; cite [AutoResearchBench](./2026-07-03/04-research-progress.md#3-autoresearch) + [SciAgentArena](./2026-06-28/04-research-progress.md). [`2026-07-03/05 §3`](./2026-07-03/05-career-and-startup.md#3-grant-deadline).

→ **Read [`01` §1 Claude apps gateway](./2026-07-03/01-big-lab-moves.md#1-gateway) + [`02` §3 Cloudflare Search/Agent/Training](./2026-07-03/02-new-emerging.md#3-cloudflare).** 10 minutes; the two threads most likely to reprice the AI-application layer in Q3 — the first *unblocks* enterprise Claude Code rollouts, the second *changes the economics* of every browser-use agent.
