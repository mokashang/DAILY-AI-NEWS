# TL;DR — 2026-07-02 (Thursday)

Sixty-second skim. **The fourth hyperscaler is being born, the token bill is under audit, and Grok's voice layer just went no-code.** **Meta announced Meta Compute** yesterday — a cloud unit under Santosh Janardhan + Daniel Gross + Dina Powell McCormick to sell excess AI capacity (both Bedrock-style hosted models and raw compute vs. CoreWeave), stock **+10%**, 2026 capex raised to **$125–145B**. On the demand side: Uber blew its annual AI budget in four months, **Lindy migrated 100% of traffic from Claude → DeepSeek**, and **Palantir's Karp (July 1) called the token-billing model "completely wrong."** And **xAI ships the Grok Voice AI Agent Builder today** (no-code, <2 min setup, 25+ languages) — the voice-agent creation layer is now commoditized across labs. Yesterday's Fable-5 redeployment ([2026-07-01/01 §2](../2026-07-01/01-big-lab-moves.md#2-fable-return)) is Day 2 today; watch the false-positive-rate data. For you: **model-routing/caching/cheap-fallbacks moved from optional to baseline resume skill**, and the FDE/Integration-Engineer lane just got a fresh reason to be hiring.

---

1. **Meta Compute — the fourth hyperscaler is being stood up.** Meta plans to monetize excess capacity via **Meta Compute** (Bedrock-style hosted-model service + raw compute rental competing CoreWeave/Nebius), under Janardhan/Gross/Powell McCormick. **Capex raised to $125–145B**, 1 GW Midwest DC + 2,250-acre Louisiana "Hyperion" campus. META +10% on the report. → [`01` §2](./01-big-lab-moves.md#2-meta-compute) `#meta #cloud #capex`

2. **The token-billing model is under enterprise attack — Karp goes on record July 1.** CNBC: Uber added **$1,500/mo AI tiers** after burning its **annual AI budget in four months**. **Lindy moved 100% traffic Claude → DeepSeek**. Palantir's **Alex Karp (July 1)** publicly called the token model **"completely wrong."** Model-routing / caching / cheap-model-fallback is now baseline resume skill. → [`01` §5](./01-big-lab-moves.md#5-token-attack) `#pricing #routing #cost`

3. **xAI ships Grok Voice AI Agent Builder (no-code, launches today).** Browser-based, **<2-min agent assembly**, **25+ languages**, sub-second latency; new users get a free phone number, BYO-SIP for enterprise. Runs on Grok's voice model. Plus: Musk (June 28) claimed **Grok 4.5** (1.5T V9, reportedly Cursor-data-trained) is in **private beta at SpaceX and Tesla**. The voice-creation layer is now commoditized across labs. → [`01` §4](./01-big-lab-moves.md#4-xai) `#xai #voice #no-code`

4. **Fable-5 redeploy — Day 2 dispatch.** Yesterday's [2026-07-01/01 §2](../2026-07-01/01-big-lab-moves.md#2-fable-return) covered the return of Fable 5 (+ Mythos 5) after the June-12 export controls lifted; today watch the **false-positive rate** on legitimate coding-agent workflows and **which cloud regions Bedrock/Vertex rolled back first.** No new material yet from Anthropic; the story to track is *usage-side*, not press-release-side. → [`01` §1](./01-big-lab-moves.md#1-fable5) `#anthropic #safety`

5. **Meituan open-sources LongCat-2.0 — 1.6T MoE trained on 50K Chinese ASICs, no NVIDIA.** MIT license, 1M-token context, **59.5% SWE-Bench Pro (beats GPT-4.5) and 70.8% Terminal-Bench**. Ran as "Owl Alpha" on OpenRouter for ~2 months before reveal. Weights on Hugging Face. → [`02` §1](./02-new-emerging.md#1-longcat) `#open-source #coding-agents #china`

6. **Anthropic AI-for-Science event aftermath — $30K credit grants, apply by July 15.** Jumper's first Anthropic public appearance was Monday night in SF; the tangible output for you is the **credit-grant program for up to 50 projects** with a **July 15 deadline**. Frame around a stepwise-verifiable science-agent workflow (cite [SciAgentArena — 2026-06-28/04](../2026-06-28/04-research-progress.md)) — 13 days to draft. → [`01` §6](./01-big-lab-moves.md#6-anthropic-science) `#anthropic #science #credits`

7. **Practical you can do tonight: fix your prompt-cache for the 5-min TTL.** Anthropic cut the default cache TTL from 60 min → 5 min this year. Cache-write costs (1.25×) keep firing but reads (~10%) rarely land. Fix: pass `cache_control: {"type": "ephemeral", "ttl": "1h"}` on your **largest stable block** (system prompt + tool defs), or stack Batch API (50% off) + Haiku routing + caching → **~$0.05/1M cached tokens.** → [`03` §1](./03-practical-skills-and-tools.md#1-prompt-cache) `#cost #api #caching`

8. **The skill re-price this week:** the value isn't "I built an agent" — it's **"I can prove the per-query unit economics."** Karp's token attack, Lindy's DeepSeek pivot, Baseten's raise, and the 2.5%-of-postings-target-0–2-yrs bottleneck are four faces of the same shift: **cost-aware, routing-aware, eval-aware agent engineering is what gets you into the AI-adjacent 2.5%.** → [`05` §5](./05-career-and-startup.md#5-newgrad) `#skills #careers`

---

## One thing to DO this Thursday

→ **Ship the "cost-aware Claude Code config" gist.** In one artifact: (a) the 1h cache_control override with a keep-alive ping, (b) a `PreToolUse` hook that filters `pytest`/`go test`/`npm test` output to failing lines, (c) a trimmed <200-line `CLAUDE.md` + one `.claude/skills/*/SKILL.md`. Push to your GitHub, log a per-session cost before/after. This one artifact answers three interview questions (cost, hooks, skills) and directly counters the Karp/Lindy narrative — see [`03` §1](./03-practical-skills-and-tools.md#1-prompt-cache) + [`03` §3](./03-practical-skills-and-tools.md#3-hooks).

## Watchlist deltas

- 🆕 **Meta Compute (fourth hyperscaler)** — track pricing versus Bedrock/CoreWeave/Nebius, whether Muse Spark ships GA there first, and how it re-prices the routing table for Claude-on-Bedrock alternatives.
- 🆕 **Enterprise token-billing revolt (Uber / Lindy / Karp)** — Karp's July 1 statement anchors this as an on-record enterprise thread. Watch for Anthropic/OpenAI *outcome* pricing or bulk-inference credits in Q3.
- 🆕 **xAI Grok Voice AI Agent Builder + Grok 4.5 private beta** — voice-agent creation layer is now commoditized; differentiation moves to retention on a vertical workflow.
- ➡️ **Fable 5 / Mythos 5 return** — Day 2. Carried from [2026-07-01/01 §2](../2026-07-01/01-big-lab-moves.md#2-fable-return). Watch false-positive rate + cloud-region rollback order.
- ➡️ **Anthropic AI-for-Science / VirBench / $30K credit grants** — event on June 30 evening; **credit-grant deadline July 15** is the actionable item.
- ➡️ **Anthropic S-1 / October Nasdaq listing** — carried from [2026-07-01/01 §3](../2026-07-01/01-big-lab-moves.md#3-anthropic-s1); public S-1 still 15d pre-roadshow.
- ➡️ **Sonnet 5 promo pricing ($2/$10 through Aug 31)** — carried from [2026-07-01/01 §1](../2026-07-01/01-big-lab-moves.md#1-sonnet-5); T-60 days to standard $3/$15.
- ➡️ **GPT-5.6 Sol / Terra / Luna preview** — carried from [2026-07-01/01 §4](../2026-07-01/01-big-lab-moves.md#4-gpt-56); GA "in the coming weeks."
- ➡️ **Meituan LongCat-2.0** — open-source frontier on non-NVIDIA silicon; second week — watch adoption on OpenRouter and whether US teams add it to routing sheets.

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
