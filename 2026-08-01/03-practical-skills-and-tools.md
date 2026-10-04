# Practical Skills & Tools — 2026-08-01

Hands-on. Things you can *do* this weekend — not read-and-file.

---

## 1. Weekend project: ship the MCP 2026-07-28 server on Cloudflare Workers (2–3 hrs, real portfolio artifact) {#1-mcp-workers-weekend}

**What to build.** One MCP server, **stateless per the 2026-07-28 spec**, deployed to Cloudflare Workers, with two tools: (a) a `Tasks` handle (create / status / cancel — the new handle-based Tasks model that replaces session-bound `tasks/list`), and (b) an `Apps` handle that renders a sandboxed HTML preview tool. **Wire format:** `Mcp-Method` + `Mcp-Name` HTTP headers, `_meta` object for versioning. **Auth:** OAuth 2.1 as resource server (one of the six SEPs in this spec).

**Why now, not next month.** The 2026-07-28 spec **shipped Jul 28** with a 12-month deprecation window on Roots/Sampling/Logging/HTTP+SSE transport; SDK downloads crossed ~400M/mo (4× YoY). The migration blogs are landing this week, so a public GitHub repo + 90-second Loom this weekend catches the traffic curve at the top and doubles as **the exact talking-point you need for any FDE / Applied AI interview in August**.

**Sources:**
- [Anthropic — "MCP 2026-07-28 spec: stateless core, coming to Claude"](https://claude.com/blog/bringing-mcp-2026-07-28-to-claude) [primary]
- [MCP Blog — 2026-07-28 Specification](https://blog.modelcontextprotocol.io/posts/2026-07-28/) [primary]
- [Digital Applied — Migration Guide](https://www.digitalapplied.com/blog/mcp-2026-07-28-spec-stateless-migration-guide) [analysis]
- [Vindler — What Breaks, What It Unlocks](https://vindler.solutions/blog/mcp-2026-07-28-stateless-spec) [analysis]

**Deliverables (pin to README):**
1. `mcp-workers-hello` repo — 1 `wrangler.toml`, 1 `worker.ts`, 1 README section per tool.
2. `demo.mp4` — 90-second Loom: `curl -H "Mcp-Method: tools/call" ...` against the deployed URL.
3. `MIGRATION.md` — one page: "here's the pre-07-28 version, here's the diff, here's why sessions went away."

**Why it matters to you.**
- **Job:** every FDE / Solutions Eng / Applied AI screen for the next 90 days will ask "have you built an MCP server?" You want the answer to be a live URL + a repo, not "I read the spec."
- **Startup:** stateless MCP means **you can charge per-request without a session-store cost line**. That's the moment "MCP-server-as-a-service" ($5/mo hobbyist, $99/mo team) becomes cost-defensible against zero-margin free tiers.
- **Insight:** every previous MCP-server example was built for a *dev laptop*. The 2026-07-28 spec is the first that's economically deployable as a *product*. First-mover advantage window is ~3 weeks.

`#mcp #cloudflare-workers #weekend-project #portfolio #stateless`

---

## 2. Router refresh — add DeepSeek V4-Flash-0731 to the tier picker (20-min job) {#2-deepseek-router-refresh}

**What to do tonight.** Add three lines to your model registry, benchmark against three tasks, log $/successful-task.

```python
# add to router.py alongside sonnet-5, gpt-5-6-luna
"deepseek-v4-flash-0731": {
    "endpoint": "https://api.deepseek.com/v1",   # OpenAI-compatible + Responses API
    "input_per_mtok":  0.14,   # confirm on your dashboard
    "output_per_mtok": 1.10,
    "context": 128_000,
    "tier": "workhorse",
}
```

Then run **20 real messages of your actual workload** across (a) DeepSeek V4-Flash-0731, (b) OpenAI Luna at $0.20/$1.20 (post-cut), (c) Anthropic Sonnet 5 at $2/$10 (last 30 days of promo pricing), (d) Kimi K3. Log `$/successful task` — that's the number your interviewer asks about, in the exact shape they want it in.

**Sources:**
- [Simon Willison — DeepSeek-V4-Flash-0731 notes](https://simonwillison.net/2026/Jul/31/deepseek-v4-flash-0731/) [analysis]
- [Wan27 — Responses API support + agent benchmarks](https://wan27.org/blog/deepseek-v4-flash-official-release) [aggregator]
- [Digital Applied — official release + benchmarks](https://www.digitalapplied.com/blog/deepseek-v4-flash-0731-official-release-agent-benchmarks) [analysis]
- Yesterday's [Router refresh action](../2026-07-31/03-practical-skills-and-tools.md#2-router-refresh)

**Why it matters to you.**
- **Job:** the router refresh is the answer to "*How do you keep agent costs predictable?*" — the top-3 most-asked FDE-interview cost question of the summer. Have the JSON diff open in a browser tab.
- **Startup:** if your product is metered ($X per user-task), a two-line router swap that moves 60% of workload off Sonnet 5 promo onto V4-Flash-0731 **restores your gross margin the day the promo ends (Aug 31).**
- **Insight:** open-weights + Responses-API + $0.14/$1.10 is the **new price floor for workhorse-tier tokens** across the industry. Every closed-model workhorse-tier price above ~$1.50 output has 60 days to justify itself or cut.

`#router #deepseek #v4-flash #cost #workhorse-tier`

---

## 3. Two 5-minute audits before Monday — Fable 5 credit + Sonnet 5 promo countdown {#3-two-5min-audits}

**Audit A — Claim the Fable 5 $100 credit before Sun Aug 2 (T-1 day).** [Anthropic Newsroom](https://www.anthropic.com/news) — the promotional credit expires 2026-08-02. If you've been meaning to spin up a Fable-5 project (fast writing / long-context brainstorm), do it this weekend, hit the "add credit" button, and put a `# Reminder: Fable 5 credit active thru 2026-08-02` comment at the top of one project so you actually use the balance.

**Audit B — Sonnet 5 promo pricing $2/$10 ends 2026-08-31 (T-30 days).** Standard pricing $3/$15 takes effect Sept 1 — a **50% input jump, 50% output jump**. Two consequences to plan: (1) any recurring Sonnet-5 job in cron or Cowork Scheduled Tasks is about to cost 50% more; audit your top-5 by monthly spend and decide *now* which tier to demote (V4-Flash-0731 for retrievers, Haiku 4.5 for classifiers, keep Sonnet 5 only for the flows that need it). (2) if you're pitching a Sonnet-5-based SaaS on gross-margin math, **rebuild the model with the Sept 1 numbers** before you show anyone a deck.

**Sources:**
- [Anthropic pricing](https://www.anthropic.com/pricing) [primary]
- [ClaudeLog news feed](https://claudelog.com/claude-news/) [aggregator]

**Why it matters to you.**
- **Job:** the Sept-1 price step-up **is the interview question** for any Anthropic Solutions or FDE screen in August ("what's changing on the price side, and how would you advise a customer to prepare?"). Being ready to answer with a real audit table beats being ready with generic advice.
- **Startup:** if your COGS model is on last-month's Sonnet 5 promo pricing and you close a customer Sept 2, you sold at negative margin. Rebuild the model.
- **Insight:** promo-pricing sunsets are Anthropic's **soft-launch of the Aug-Nov rate card**. The Sonnet 5 step-up is the first data point; watch for a Haiku 4.5 promo expiration in the next 30 days too.

`#anthropic #fable-5 #sonnet-5 #pricing-audit #saturday-5min`

---

## 4. Two containment-checklist deltas from yesterday's Claude breach postmortem {#4-containment-checklist-delta}

**What to add to your local `agent-container` project (if you have one).** The 141k-session postmortem [`01` §1](./01-big-lab-moves.md#1-anthropic-141k) surfaced two mitigations that were absent from the pre-07-31 industry consensus:

1. **Reduced-refusals mode is a distinct evaluation state that MUST be scoped to `--net=none` + a filesystem overlay you can `rm -rf` after.** No exceptions. If you can't trivially confirm "the agent cannot reach 1.1.1.1", you're not doing red-team cyber-evals safely.
2. **Victim-notification is a first-class T&S process, not an incident afterthought.** If your agent could plausibly reach outside your infra during an eval, decide *ahead of time* who owns the notify-the-victim workflow. Both Anthropic and OpenAI needed 3-6 days from detection to victim contact — that gap is where reputational damage lives.

Turn both into a one-page `CYBER-EVAL-CONTAINMENT.md` in your repo. **This is the shortest possible portfolio piece for the assurance lane in [`05` §1](./05-career-and-startup.md#1-assurance-lane-week1).**

**Sources:** [Anthropic Newsroom postmortem](https://www.anthropic.com/news), [Al Jazeera coverage](https://www.aljazeera.com/news/2026/7/31/after-openai-disclosure-anthropic-claude-hacked-outside-systems), yesterday's [containment checklist](../2026-07-31/03-practical-skills-and-tools.md#3-agent-containment-checklist).

`#security #containment #cyber-evals #assurance #checklist`
