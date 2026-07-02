# LATEST — pointer to the most recent edition

> **2026-07-02** — see [`2026-07-02/00-tldr.md`](./2026-07-02/00-tldr.md)

This file is auto-updated every edition so a one-click read of the latest TL;DR is always at the repo root.

---

## Today's headline

**Thursday — Meta Compute stood up, the token bill is under audit, and Grok's voice layer just went no-code.** **Meta announces Meta Compute** (yesterday) — a Bedrock-style hosted-models service + a CoreWeave/Nebius-competing raw-compute business under Janardhan/Gross/Powell McCormick; 2026 capex raised to **$125–145B**; **META +10%** = fourth hyperscaler is being born. On the demand side, enterprise buyers stopped tolerating token pricing: **Uber blew its annual AI budget in four months**, **Lindy migrated 100% of traffic from Claude → DeepSeek**, and **Palantir's Karp (July 1) called the token model "completely wrong."** And **xAI ships the Grok Voice AI Agent Builder today** — no-code, <2 min setup, 25+ languages. Yesterday's [Fable-5 redeployment](./2026-07-01/01-big-lab-moves.md#2-fable-return) is Day 2; watch the false-positive-rate data. **For you: model-routing/caching/cheap-fallback moved from optional to baseline resume skill.**

Full edition → [`2026-07-02/`](./2026-07-02/)

---

## One-thing-to-do (Thursday)

→ **Ship the "cost-aware Claude Code config" gist tonight** — [`2026-07-02/03 §1`](./2026-07-02/03-practical-skills-and-tools.md#1-prompt-cache) + [`§3`](./2026-07-02/03-practical-skills-and-tools.md#3-hooks). 60 minutes: (a) `cache_control` with `ttl: "1h"` on system prompt + tool defs; (b) `PreToolUse` hook filtering pytest/go test/npm test output; (c) trimmed <200-line CLAUDE.md + one `.claude/skills/*/SKILL.md`. Log per-session cost before/after. One artifact answers three interview questions — the direct counter to the Karp/Lindy narrative.

→ **Apply to Anthropic FDE Applied AI this week.** [`2026-07-02/05 §2`](./2026-07-02/05-career-and-startup.md#2-anthropic-fde) — attach the cost-aware config gist + a 1-page "Karp / Uber / Lindy → what I'd do about it" write-up. The FDE lane is where CS-grad polymath skills beat a pure-ML-PhD pedigree.

→ **Draft the Anthropic AI-for-Science credit-grant application by Saturday.** [`2026-07-02/01 §6`](./2026-07-02/01-big-lab-moves.md#6-anthropic-science) — deadline **July 15**. Frame around a stepwise-verifiable science-agent workflow (cite [SciAgentArena](./2026-06-28/04-research-progress.md)). ~13 days to ship.

→ **Read [`01` §2 Meta Compute](./2026-07-02/01-big-lab-moves.md#2-meta-compute) + [`01` §5 the token-billing revolt](./2026-07-02/01-big-lab-moves.md#5-token-attack).** 10 minutes; the two threads most likely to reprice the AI-application layer this quarter.
