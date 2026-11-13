# Practical Skills & Tools — 2026-06-15 (Monday)

`#claude-code #agent-sdk #billing #cost-routing`

Two clock-time actions. One verification step at the top of the day; one date-aware adjustment to the Fable 5 dependency audit you shipped last night.

---

## 1. METERING IS LIVE — verify the toggle landed and adopt the 3-line cost rule {#1-metering-live}

**Step 0 — Verify (5 min, do at 8:00 AM PT or as soon as you read this).**

```bash
# Quick check: did the credit pool activate for your account?
claude api cost --since=24h --format=json | jq '.agent_sdk_credit'
# Expected: { "available": 20.00 } for Pro, 100.00 / 200.00 for Max-5x / Max-20x.
# If you see `credit_pool_not_claimed: true`, go back to:
#   Account Settings → Billing → Agent SDK Credits → "Claim my monthly credit"
```

If your morning's `claude -p` calls failed with `credit_pool_not_claimed` errors, you have ~30 minutes of work to: (a) toggle the credit, (b) enable overflow billing, (c) re-run the failed calls. Don't postpone.

**Step 1 — Adopt the 3-line cost rule (10 min, applies to every project starting today).**

The new metering changes the per-token economics for programmatic Claude. The Opus / Sonnet ratio justifies a simple, durable rule:

1. **Opus 4.8 for orchestration / planning turns only.** The expensive model writes the plan; the cheap model executes it.
2. **Sonnet 4.6 for worker turns + tool I/O.** All the "go fetch, summarize, call this MCP, return JSON" turns.
3. **Anything you can run locally or on Gemini 3.5 Flash, do.** Especially: classifier turns, redaction passes, log-summary turns, pre-prompt validators.

Encode the rule in a 4-line `policy.md` at your `CLAUDE.md` top:

```md
## Cost policy (post-2026-06-15)
- Default model: claude-sonnet-4-6
- Use claude-opus-4-8 only for orchestration / multi-step planning turns
- Use Gemini 3.5 Flash or local Llama 4 for classifiers + validators
- Track `cost_log.jsonl` daily; tag turns with metadata.user_id
```

**Step 2 — Daily cost log + weekly review (15 min on Sundays).**

Cron job `~/scripts/anthropic_cost.sh`:

```bash
#!/bin/bash
# Daily cost snapshot, tagged with the date.
DATE=$(date +%Y-%m-%d)
claude api cost --since=24h --format=json \
  | jq -c --arg date "$DATE" '. + {date: $date}' \
  >> ~/anthropic_cost_log.jsonl
```

Add to crontab: `0 23 * * * ~/scripts/anthropic_cost.sh`. Sundays, eyeball `tail -n 7 ~/anthropic_cost_log.jsonl`; look for the day your credit-pool burn outpaces the daily budget.

**Sources.**
- `[secondary]` [The New Stack — Anthropic splits billing again: Agent SDK gets separate credit pools](https://thenewstack.io/anthropic-agent-sdk-credits/)
- `[analysis]` [Coders Era — Anthropic's June 15 Billing Change](https://codersera.com/blog/anthropic-june-2026-billing-change-claude-code/)
- `[analysis]` [Context Studios — June 15 Billing Split: Your Break-Even Decision](https://www.contextstudios.ai/blog/anthropics-june-15-billing-split-your-break-even-decision)
- `[aggregator]` [Canonical reference gist — Anthropic Agent SDK $200 credit](https://gist.github.com/MagnaCapax/d9177e35b355853f03c730dfcaa693ef)

**Why it matters to you.**

- **Job ·** "Show me your cost log + your routing policy" is a real interview prompt now. Tonight's commit gives you a clean answer.
- **Startup ·** The cost log is the most-honest unit-economics document a founder can have. Print it. Bring it to investor meetings.
- **Insight ·** Cost-aware routing was a research topic 90 days ago; today it's table-stakes ops. **Skill commoditization in real time** — the gap between "researcher" and "operator" is now days, not quarters.

`#metering #claude-code #cost #routing`

---

## 2. The June 22 cliff: even if Fable 5 returns, the bundled pricing window ends in 7 days {#2-jun22-cliff}

**What's happening.** When Anthropic launched Fable 5 on June 9, the announcement included a key fine-print line: **"Free access on subscription plans runs through June 22, 2026."** On **June 23**, Fable 5 *was* scheduled to move out of bundled Pro / Max / Team / Enterprise plans and into the new credit pool, billed at $10 / $50 per 1M tokens. **The shutdown does not reset this clock.** Whatever date Fable 5 comes back, **bundled-tier free access expires on June 22 regardless.** `[secondary]`

**The two-cost-shock-in-8-days picture.**

| Date | What changes for the Anthropic-stack builder |
|---|---|
| **Jun 15 (today)** | Programmatic Claude (Agent SDK + Code GA + third-party agents) moves to credit-pool metering at API list rates. |
| **Jun 22** | Even if Fable 5 returns by then, bundled subscription access to it ends. From Jun 23, Fable 5 = $10/$50 per 1M tokens. |
| **(if Fable 5 stays offline through Jun 22)** | The cliff happens silently — you may never see Fable 5 inside your subscription at all. |

**What to do.**

1. **Update the Fable 5 dependency audit from yesterday.** When you do re-pin to Fable 5 (post-restoration), include a **per-prompt cost-cap check** since the bundled subsidy is gone. Refuse to fall through to Fable 5 unless `cost_estimate < threshold`.
2. **Re-do your Anthropic-stack monthly spend forecast.** Two cost shocks in 8 days; the new baseline matters for your portfolio-cost budget.
3. **Re-write your `models.py` `FALLBACK_CHAIN`** (from [yesterday's `03` §2](../2026-06-14/03-practical-skills-and-tools.md#2-anthropic-stack-hedge)) to **default to Sonnet 4.6**, with Opus 4.8 only as the orchestrator-turn override. Fable 5 sits at the *bottom* of the chain (expensive + currently unavailable) — not the top.

**Sources.**
- `[secondary]` [Developers Digest — Fable 5 Leaves Your Claude Plan on June 22](https://www.developersdigest.tech/blog/claude-fable-5-june-22-deadline)
- `[analysis]` [Shadow — Is Claude Fable 5 Worth It? Pricing and Breakeven Analysis](https://www.shadow.inc/resources/claude-fable-5-pricing-breakeven-analysis)
- `[analysis]` [UsageBox — Anthropic's June 15 Double Hit: Agent SDK Credit Split + Claude 4 Retirement](https://usagebox.com/articles/anthropic-june-15-agent-sdk-credit-split-claude-4-retirement)

**Why it matters to you.**

- **Job ·** "How did you handle the June 15 + June 22 cost shocks?" is one specific interview question; have a paragraph answer ready by next Tuesday.
- **Startup ·** Whatever monthly Anthropic-stack bill you projected before June 15: scale it up roughly 25–60 % for the next two months. Re-confirm investor reserves.
- **Insight ·** Anthropic is **conditioning the market to per-agent + per-model pricing**. Within 6 months expect: per-agent billing, per-team SKUs, and a separate "production-Fable" tier at higher price.

`#anthropic #pricing #fable5 #cost-shock`

---

## Cross-page

- See [`01` §1](./01-big-lab-moves.md#1-fable-day4) for the prediction-market pricing of Fable 5 restoration.
- See [`05` §1](./05-career-and-startup.md#1-week-execution) for the Mon→Fri application execution plan.
- See yesterday's [`03` §2](../2026-06-14/03-practical-skills-and-tools.md#2-anthropic-stack-hedge) for the router shim this page updates.
