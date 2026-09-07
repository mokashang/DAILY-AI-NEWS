# Practical Skills & Tools — 2026-06-06

Two things to actually do this weekend, one thing to pre-stage for Monday. **The Claude outage on June 5** (claude.ai + API + Code + Cowork, restored 18:27 UTC) is the *operational* reminder that the 3-provider router you've had on the ME.md punch list since 2026-05-10 is no longer academic. **Fast mode now defaults to Opus 4.8 at $10/$50 per MTok at ~2.5× speed** — that flips the "Opus is too expensive to default to" mental model. And **WWDC is in 48 hours** — pre-stage the same 15-minute-block live-monitoring discipline you used for Google I/O.

Tags: `#claude-code #outage #failover #multi-vendor #routing #opus-4-8 #pricing #fast-mode #wwdc #monitoring #practical`

---

## 1. The Claude outage of June 5 → ship the 3-provider router this weekend {#1-failover-router}

**What happened:** On **June 5, 2026**, **claude.ai, the Claude API, Claude Code, and Claude Cowork all went down**. Anthropic attributed the outage to **infrastructure issues, not a security breach**. **Full restoration was confirmed at 18:27 UTC.** No data-loss report; the working assumption is a single-provider availability event, not a model-quality regression.

**Sources:**
- [Cybersecurity News — Anthropic's Claude Services Down — claude.ai, Claude Code, and Cowork Affected [Updated]](https://cybersecuritynews.com/anthropics-claude-services-down/) `[secondary]`
- (Confirm against Anthropic's official status page going forward — `status.anthropic.com`.)

### Why it matters to you

This is the **second qualifying event** for your "multi-vendor router is production discipline, not a hobby project" thesis (the first was [2026-05-09 Colossus tenancy concentration risk](../2026-05-09/01-big-lab-moves.md)). The action is now overdue, not premature.

**Do this — weekend artifact (target: tonight + Saturday morning):**

1. **Stand up a thin failover wrapper** around your current Claude-only code path:
   - Primary: **Claude (Opus 4.8 for orchestration, Sonnet 4.6 for workers)** — the default
   - Failover-A: **Gemini 3.5 Flash** ($1.50/$9 per MTok — [2026-05-19/01](../2026-05-19/01-big-lab-moves.md) confirmed pricing) — instant if Claude returns 5xx or times out >N seconds
   - Failover-B: **GPT-5.5 Instant** — if both above fail
2. **Log per-request:** `{provider, model, latency_ms, input_tok, output_tok, cost_usd, success}`. Even 24 hours of this log is interview gold.
3. **Make the README answer three interview questions in one artifact:**
   - "How do you handle provider outages?" → failover policy + log
   - "How do you control cost?" → per-request cost row + monthly rollup
   - "How do you decide which model to use?" → the routing rule + observed mix
4. **One day of real traffic** beats a perfect spec. Wire it into the lowest-stakes existing project you have and let it run.

This artifact **rolls up three of your active threads at once**: the dual-model sanitiser ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)), the cost router ([2026-05-20/03 §4](../2026-05-20/03-practical-skills-and-tools.md#4-cost-routing)), and the 3-provider router from ME.md. **Don't build three things — build one thing that answers three questions.**

→ Cross-link: [ME.md active portfolio artifacts](../ME.md#active-portfolio-artifacts) · [2026-05-20/03 §4 cost-routing](../2026-05-20/03-practical-skills-and-tools.md#4-cost-routing) · [ACTIONS.md](../ACTIONS.md) (move 3-provider-router up to "this weekend").

---

## 2. Fast mode now defaults to **Opus 4.8** at $10/$50 per MTok, ~2.5× speed — re-do your model selector tonight {#2-fast-mode-opus}

**What happened:** Anthropic's **Fast mode** (a low-latency variant for chat surfaces) **now defaults to Opus 4.8** at **$10 / $50 per MTok in/out** at **~2.5× the speed** of standard Opus. This is the first time Opus has had a default "fast lane" priced this aggressively.

**Sources:**
- [Releasebot — Anthropic Release Notes June 2026 (Fast mode default to Opus 4.8)](https://releasebot.io/updates/anthropic) `[aggregator]`
- [Releasebot — Claude Updates by Anthropic June 2026](https://releasebot.io/updates/anthropic/claude) `[aggregator]`
- (Cross-check against Anthropic's pricing page + the release-notes commit log when verifying for a portfolio artifact.)

### Why it matters to you

The whole **routing heuristic** you've been carrying — "Opus only for the orchestration step because it's expensive" — needs to be **re-examined.** With Fast Opus 4.8 at $10/$50 + 2.5× speed:

- The **Opus-orchestrator + Sonnet-worker split** ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) is still cheaper per chain, but the **per-decision latency cost of using Opus drops sharply** — chains that previously had to go Sonnet for latency may now stay Opus end-to-end for quality.
- For **interactive surfaces** (your Anthropic Solutions/FDE interview demos), Fast Opus 4.8 is the **new default to pitch** — it changes the demo "feel" in a way an interviewer can hear.
- **Re-benchmark your existing chains tonight** (15-min job): record `(model, latency_ms, tokens_in, tokens_out, $)` for one representative chain on Sonnet 4.6, Opus 4.7, Fast Opus 4.8. The delta is the talking point.

**Do this tonight (15 min):**
1. Pull last week's prod chain
2. Replay it on each model
3. Tabulate latency × cost × quality (eyeball)
4. Commit the table to the [`README`](../README.md)-adjacent of your router project
5. Use it as the **opener** to your next FDE/Solutions outreach email

→ Cross-link: [2026-05-22/03 §1 agent-team cost lever](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [`05` §1 Anthropic application leverage](./05-career-and-startup.md#1-anthropic-hiring).

---

## 3. WWDC live-monitoring discipline — pre-stage tonight {#3-wwdc-discipline}

**What happens Monday:** **WWDC 2026 keynote, June 8, 10 AM PT** ([`01` §3](./01-big-lab-moves.md#3-wwdc-extensions)). Reuse the I/O discipline ([2026-05-19/03 §1](../2026-05-19/03-practical-skills-and-tools.md#1-io-live-discipline)) — it worked.

**Sources:** see [`01` §3](./01-big-lab-moves.md#3-wwdc-extensions).

**Pre-stage tonight (10 minutes):**

```
WWDC-2026/
├── notes.md           # 15-min time-stamped blocks during keynote
├── claims.md          # bullet list of each named feature + my prediction
└── post.md            # 1-page Tuesday-morning takeaway draft skeleton
```

**Hypothesis list to write down *before* Monday** (so you can grade yourself, the way you did at I/O):

1. **Extensions SDK ships with Claude, ChatGPT, Gemini named on stage** (confidence: high)
2. **A "default AI" picker in Setup** (confidence: medium-high)
3. **Siri 2.0 standalone app** with dedicated chat UI (confidence: high)
4. **An Extensions billing model** — either Apple-rails (revenue share) or BYO-key (no rails) (confidence: medium; this is the *strategic* tell)
5. **An on-device-vs-cloud routing API exposed to developers** (confidence: medium)
6. **Image Playground gets a third-party image model option** (confidence: medium)
7. **A new Apple-silicon ML-runtime announcement** (confidence: medium)
8. **No mention of agents-acting-on-other-apps** (confidence: medium — Apple is more likely to gate this behind App Intents)

**Monday discipline:**
- **15-min blocks** during keynote → notes.md
- **Tuesday 9 AM PT** → publish 1-page graded comparison post + update LinkedIn skills with the *real* on-stage terms (don't repeat the "Vertex AI Agent Platform" mistake — [2026-05-20/01 §1](../2026-05-20/01-big-lab-moves.md#1-io-scorecard)).
- **Tuesday by EOD** → apply to **one Anthropic role referencing the iOS 27 Extension integration angle specifically** — before the post-WWDC application wave.

→ Cross-link: [2026-05-19/03 §1 I/O live-monitoring discipline](../2026-05-19/03-practical-skills-and-tools.md#1-io-live-discipline) (the template that worked) · [`05` §4 Extensions = AI Integration Engineer lane](./05-career-and-startup.md#4-extensions-lane).
