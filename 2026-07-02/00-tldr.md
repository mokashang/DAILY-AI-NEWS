# TL;DR — 2026-07-02 (Thursday)

Sixty-second skim. **Fable 5 is back, the fourth hyperscaler is being born, and enterprise buyers just started auditing the token bill.** The Commerce Department lifted export controls on **Claude Fable 5** yesterday; Anthropic redeployed today with a **retrained cybersecurity classifier** (>99% block on the original bypass) and a silent **Opus 4.8 fallback** for false-positives — the export-control-driven suspension is over, but the shape of "gated redeployment" is now the template. **Meta announced Meta Compute** — a cloud unit under Santosh Janardhan + Daniel Gross + Dina Powell McCormick to sell excess AI capacity (both Bedrock-style hosted models and raw compute vs. CoreWeave), stock **+10%**, 2026 capex raised to **$125–145B**. And on the demand side: Uber blew its annual AI budget in four months, **Lindy migrated 100% of traffic from Claude → DeepSeek**, and Palantir's Karp called the token-billing model **"completely wrong."** For you: **model-routing/caching/cheap-fallbacks moved from optional to baseline resume skill**, and the FDE/Integration-Engineer lane just got a fresh $30B run-rate reason to be hiring.

---

## Gap note

This archive paused after [2026-05-22](../2026-05-22/). Today resumes daily cadence. No attempt is made to backfill the intervening ~6 weeks — items still relevant surface as "since we last checked" callouts inline. Threads that changed materially: **OpenAI's S-1 path (still confidential, no roadshow yet), Anthropic's revenue ramp (now ~$30B run-rate, was projected ~$10.9B Q2), the Karpathy→Anthropic team (shipped nothing public yet), Fable 5 (suspended June 12 → restored today).**

---

1. **Fable 5 redeployed globally with a new safety classifier.** Anthropic restored Claude Fable 5 to Claude.ai / Platform / Code / Cowork after Commerce lifted the June-12 export controls that had followed an Amazon-demonstrated jailbreak. Ships a retrained classifier + **automatic reroute to Opus 4.8** with a user notice on blocked prompts. → [`01` §1](./01-big-lab-moves.md#1-fable5) `#anthropic #safety #export-controls`

2. **Meta Compute — the fourth hyperscaler is being stood up.** Meta plans to monetize excess capacity via **Meta Compute** (Bedrock-style hosted-model service + raw compute rental competing CoreWeave/Nebius), under Janardhan/Gross/Powell McCormick. **Capex raised to $125–145B**, 1 GW Midwest DC + 2,250-acre Louisiana "Hyperion" campus. META +10% on the report. → [`01` §2](./01-big-lab-moves.md#2-meta-compute) `#meta #cloud #capex`

3. **OpenAI previews GPT-5.6 (Sol / Terra / Luna) to ~20 partners under U.S. gov coordination.** Three-tier flagship/mid/fast pattern; API + Codex only during preview; **Cerebras serving Sol at up to 750 tok/s**; GA "in the coming weeks." First frontier launch executed under the voluntary pre-deployment-review posture — the [2026-05-21 EO](../2026-05-21/01-big-lab-moves.md#1-trump-eo) framework operating in practice even without the signed order. → [`01` §3](./01-big-lab-moves.md#3-gpt56) `#openai #frontier #policy`

4. **Meituan open-sources LongCat-2.0 — 1.6T MoE trained on 50K Chinese ASICs, no NVIDIA.** MIT license, 1M-token context, **59.5% SWE-Bench Pro (beats GPT-4.5) and 70.8% Terminal-Bench**. Ran as "Owl Alpha" on OpenRouter for ~2 months before reveal. Weights on Hugging Face. → [`02` §1](./02-new-emerging.md#1-longcat) `#open-source #coding-agents #china`

5. **The token-billing model is under enterprise attack.** CNBC: Uber added $1,500/mo AI tiers after burning its yearly AI budget in **four months**; **Lindy moved 100% traffic Claude → DeepSeek**; Palantir's Karp on July 1 called token pricing **"completely wrong."** Model-routing / caching / cheap-fallback is now baseline resume skill, not advanced. → [`01` §5](./01-big-lab-moves.md#5-token-attack) · [`03` §1](./03-practical-skills-and-tools.md#1-prompt-cache) `#pricing #routing #cost`

6. **Baseten $1.5B Series F at $13B — "tripling headcount this year."** 160% valuation jump in 5 months (was $5B), ~20× YoY revenue, 1B+ daily inference requests across 87 clusters / 18 clouds. Runs on the Anthropic stack among others. **FDE / platform-eng / GTM openings.** Direct target if you've shipped anything with vLLM/TGI/Modal. → [`05` §1](./05-career-and-startup.md#1-baseten) `#funding #hiring #inference`

7. **Practical you can do tonight: fix your prompt-cache for the 5-min TTL.** Anthropic cut the default cache TTL from 60 min → 5 min this year. Cache-write costs (1.25×) keep firing but reads (~10%) rarely land. Fix: pass `cache_control: {"type": "ephemeral", "ttl": "1h"}` on your **largest stable block** (system prompt + tool defs), or stack Batch API (50% off) + Haiku routing + caching → **~$0.05/1M cached tokens.** → [`03` §1](./03-practical-skills-and-tools.md#1-prompt-cache) `#cost #api #caching`

8. **The skill re-price this week:** the value isn't "I built an agent" — it's **"I can prove the per-query unit economics."** Karp's token attack, Lindy's DeepSeek pivot, Baseten's raise, and the 2.5%-of-postings-target-0–2-yrs bottleneck are four faces of the same shift: **cost-aware, routing-aware, eval-aware agent engineering is what gets you into the AI-adjacent 2.5%.** → [`05` §5](./05-career-and-startup.md#5-newgrad) `#skills #careers`

---

## One thing to DO this Thursday

→ **Ship the "cost-aware Claude Code config" gist.** In one artifact: (a) the 1h cache_control override with a keep-alive ping, (b) a `PreToolUse` hook that filters `pytest`/`go test`/`npm test` output to failing lines, (c) a trimmed <200-line `CLAUDE.md` + one `.claude/skills/*/SKILL.md`. Push to your GitHub, log a per-session cost before/after. This one artifact answers three interview questions (cost, hooks, skills) and directly counters the Karp/Lindy narrative — see [`03` §1](./03-practical-skills-and-tools.md#1-prompt-cache) + [`03` §3](./03-practical-skills-and-tools.md#3-hooks).

## Watchlist deltas

- 🆕 **Fable 5 back with new classifier + Opus 4.8 fallback** — track false-positive rate on legit coding tasks (agentic red-team workflows will be affected first) and whether the "gated redeployment" pattern gets copied by OpenAI/Google.
- 🆕 **Meta Compute** — fourth hyperscaler; track pricing versus Bedrock/CoreWeave and whether Muse Spark gets first-party GA there.
- 🆕 **GPT-5.6 Sol / Terra / Luna preview** — track the ~20-partner list, Cerebras Sol pricing, and whether Terra/Luna undercut Haiku/Flash.
- 🆕 **Meituan LongCat-2.0** — open-source frontier on non-NVIDIA silicon; expect wave of adopters where API-Claude was previously the default.
- 🆕 **Enterprise token-billing revolt (Uber / Lindy / Karp)** — track whether Anthropic/OpenAI ship *outcome* pricing or bulk-inference credits in Q3.
- 🆕 **Baseten $13B Series F + Anthropic $30B run-rate + 1,000 seven-figure accounts** — the mechanical reason FDE demand is exploding; apply this week.
- 🆕 **YC S26 batch: ~60% AI, agent-infra RFS** — the highest-signal early-stage job board on the internet.
- ➡️ **Karpathy → Anthropic pre-training team** — carried from [2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy); no public artifact yet.
- ➡️ **OpenAI S-1** — carried from [2026-05-22/01 §2](../2026-05-22/01-big-lab-moves.md#2-openai-s1); still confidential, no roadshow.
- ⬇️ **Trump AI EO** — remains postponed from [2026-05-22/01 §1](../2026-05-22/01-big-lab-moves.md#1-eo-postponed); the *voluntary* review is happening anyway via GPT-5.6.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Fable-5 redeploy + Meta Compute in [`01` §1–2](./01-big-lab-moves.md) |
| 20 min | [`01` §5](./01-big-lab-moves.md#5-token-attack) (token-billing revolt) + [`03` §1](./03-practical-skills-and-tools.md#1-prompt-cache) (cache TTL fix) — read together, act tonight |
| Today | [`05` §1–2](./05-career-and-startup.md) — Baseten + Anthropic FDE roles; apply this week |
| Weekend | [`03` §2](./03-practical-skills-and-tools.md#2-long-running) — initializer + coding-agent pattern on a portfolio project |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
