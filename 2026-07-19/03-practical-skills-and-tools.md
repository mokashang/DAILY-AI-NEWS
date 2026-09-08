# Practical Skills & Tools — 2026-07-19 (Sunday review)

> **Continuity note:** [2026-07-18/03](../2026-07-18/03-practical-skills-and-tools.md) laid the 90-min Fable-5 eval-capture playbook + Kimi K3 hosted setup + provider-availability probe + schema-verify layers + cache-hit audit; [2026-07-17/03](../2026-07-17/03-practical-skills-and-tools.md) covered the MCP `2026-07-28` RC + Claude Code 2.1.212 fork/subtask + ultracode multi-agent; [2026-07-14/03](../2026-07-14/03-practical-skills-and-tools.md) covered the Sonnet 5 upgrade + cross-provider prompt cache breakpoints. This file is the **Sunday execution version** — three sections, one 2-hour block, deadline-anchored.

Tags: `#fable-5 #evals #sonnet-5 #routing #mcp #stateless #tasks #execution`

---

## 1. Fable-5 eval capture — 30 min BEFORE 11:59 PM PT tonight {#1-fable-5-evals}

**What to do (deadline: tonight):** Execute the eval capture from [2026-07-18/03 §1](../2026-07-18/03-practical-skills-and-tools.md#1-fable-5-evals). Three tasks · one MCP server · Fable 5 as the frontier baseline · **save raw API response JSON, not just parsed completion**.

**Save-the-JSON angle (new tonight):** If you only save the final answer, a 2-months-from-now retry against a *paid* Fable 5 model can only compare summaries. Save the entire response envelope — token counts, stop reason, tool_use ids, cache_creation vs cache_read tokens, the full trajectory — and your retry is a *proper* baseline compare, not a vibe check. This is the difference between an artifact that survives to Q4 interviews and one that ages out of usefulness.

**Concrete write path** (use whatever framework, but the structure matters):

```
evals/fable-5-baseline-2026-07-19/
├── README.md                    # the task set + methodology + what you'd change next time
├── task-1-structured-extraction/
│   ├── prompt.md
│   ├── response.json            # RAW API response, not parsed
│   └── analysis.md              # pass/fail + cost + fabrications
├── task-2-mcp-tool-use/
│   └── (same pattern)
└── task-3-agentic-coding/
    └── (same pattern)
```

**Sources:**
- [2026-07-18/03 §1](../2026-07-18/03-practical-skills-and-tools.md#1-fable-5-evals) — 90-min playbook `[archive]`
- [Anthropic pricing page](https://www.anthropic.com/pricing) — verify the sunset before you start `[primary]`

### Why it matters to you

- **Job lens:** A dated `evals/fable-5-baseline-2026-07-19/` folder in a public repo is one of the highest-leverage 30-min moves you'll make this quarter — because the *timestamp* is unforgeable: you either captured evals against the free tier before it closed, or you didn't. In interviews, "here's the raw-response JSON I saved before the sunset" reads as senior in a way "I've used Claude" does not.
- **Startup lens:** If you're running a product against Fable 5 in production, tonight is the point where your Q3 unit economics get recalculated. Run the *actual* traffic through the eval capture — real prompts, real trajectory lengths — so you have the data to make a routing decision Monday morning (Fable 5 paid vs. Sonnet 5 vs. Kimi K3 hosted vs. GPT-5.6 Terra).
- **Insight:** The subsidy-phase-ending pattern from [`02` §2](./02-new-emerging.md#2-fable-5-category-event) means *every quarter* now has a similar dated cliff for some model. Make dated-eval-capture a *habit*, not a one-off.

---

## 2. Stateless-MCP execution — 60 min migration + 10 min writeup {#2-mcp-stateless-execution}

**What to do:** Pick one MCP server you own, migrate it to the **`2026-07-28` release-candidate SDK** (Py / TS / Go / C# betas out). Follow the migration read at [2026-07-17/03](../2026-07-17/03-practical-skills-and-tools.md), and use tonight to hit **three specific execution points** that separate a "migrated" server from a *portfolio* migration:

1. **Kill the sticky-session infrastructure.** Route through a plain round-robin load balancer. If you're on Cloudflare Workers, drop the Durable Object session store; if you're on Fly.io, remove the app-level session middleware.
2. **Add at least one Task-extension handler.** Pick a tool that already takes >2 seconds and rewrite it to return a task handle with `tasks/get` / `tasks/update` / `tasks/cancel`. This is the piece that reads as "I actually understand the new spec" vs "I ran the migration script."
3. **Add one MRTR (`InputRequiredResult`) confirmation** to a destructive tool. `delete_note`, `send_message`, `run_bash` — anything that would benefit from a mid-call user confirmation. This is the primitive that removes ad-hoc "prompt for approval" hacks.

**Then the 10-min writeup:**

```markdown
# Migrating <server> to MCP 2026-07-28 (T-9 days before spec ships)

## Before / after
- Sticky sessions: **removed**
- Session store: **removed** (was: <thing>)
- Deploy shape: <was> → <now>
- Cold-start latency: XXms → YYms
- Cost per 1M tool calls: $X → $Y

## What breaks in migration
- <bullet>
- <bullet>

## Tasks-extension example
<code snippet showing tasks/get + tasks/update + tasks/cancel wired end-to-end>

## MRTR mid-call confirmation
<code snippet showing InputRequiredResult on a destructive tool>
```

Post as a public gist. **Add the gist URL to your GitHub profile README + your resume** *tonight*, before Jul 28. The unforgeable-timestamp trick again.

**Sources:**
- [2026-07-17/03](../2026-07-17/03-practical-skills-and-tools.md) `[archive]`
- [MCP RC post](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) `[primary]`
- [MCP Beta SDKs](https://blog.modelcontextprotocol.io/posts/sdk-betas-2026-07-28/) `[primary]`
- [Developers Digest — Breaking changes migration guide](https://www.developersdigest.tech/blog/mcp-2026-07-28-breaking-changes) `[analysis]`

### Why it matters to you

- **Job lens:** Being *dated-before-spec-day* is a real signal — it says you're reading the ecosystem's rolling upgrade cycle proactively, not reactively. Every recruiter who scans your GitHub in August will see the *pre-Jul-28* commit timestamp and read it correctly.
- **Startup lens:** The stateless-plus-Tasks combination lets a 2-person team ship an MCP-server SaaS behind a plain load balancer without the ops complexity of session state. That was not true 30 days ago; it is true starting Jul 28. If you're building infra, this changes what your minimum viable ops looks like.
- **Insight:** In a year, MCP-stateless will read the same way "HTTP is stateless" reads today — the alternative will feel weird. Being early to the mental model is worth more than being early to the specific SDK version.

---

## 3. Set up the 3-model routing rule (Sonnet 5 default + Kimi K3 hosted + Fable 5 paid escalation) {#3-3-model-routing}

**What to do (20 min):** Update your project's `CLAUDE.md` or router config so that:

- **Default worker:** Sonnet 5 ($2/$10 intro through Aug 31 — capture the intro window; see [2026-07-14/03](../2026-07-14/03-practical-skills-and-tools.md)).
- **Cheap default (agentic coding, single-attempt fine):** **Kimi K3 hosted** via OpenRouter at ~$0.30 cache-hit / $3 cache-miss / $15 output — [Frontend Code Arena #1 as of Jul 18](../2026-07-18/01-big-lab-moves.md#1-kimi-k3). Add it as *route #2*.
- **Escalation for hard reasoning:** Fable 5 (paid starting tonight), Opus 4.8, or GPT-5.6 Sol Max — whichever is cheapest for the specific eval-verified sweet spot.
- **Verification layer on every route:** schema-verify the output before accepting it (Layer A pass + Layer B semantic pass). If Layer A fails, retry; if Layer B fails, escalate.

**Concrete `CLAUDE.md` snippet:**

```markdown
## Model routing (2026-07-19 → 2026-08-31 window)

- **Default (agentic coding, brownfield, tool-use):** Sonnet 5 (intro $2/$10)
- **Cheap default (single-attempt code, high volume):** Kimi K3 hosted (~$0.30/$15)
- **Escalation:** Fable 5 paid (only after Layer B fail)
- **Verification:** schema-verify every completion; escalate on Layer A retry-fail

## Cost log

Log per-step: `{route, tokens_in, tokens_out, cache_read, cache_creation, cost, layer_a_pass, layer_b_pass}`.
Roll up monthly for the 4th-of-month billing audit.
```

**Sources:**
- [2026-07-18/01 §1](../2026-07-18/01-big-lab-moves.md#1-kimi-k3) — Kimi K3 arena results + hosted pricing `[archive]`
- [2026-07-14/03](../2026-07-14/03-practical-skills-and-tools.md) — Sonnet 5 upgrade `[archive]`
- [2026-07-18/03](../2026-07-18/03-practical-skills-and-tools.md) — provider-availability probe + schema-verify layers `[archive]`

### Why it matters to you

- **Job lens:** The `CLAUDE.md` routing block is the single most concrete evidence of "cost-aware model routing" the [ME.md focusing decision](../ME.md#current-focusing-decision) points at. When an interviewer asks *"how do you think about model choice?"*, opening a real `CLAUDE.md` file and walking through the block is what "senior" looks like.
- **Startup lens:** If you're building anything with model calls in production, the 3-model routing rule is the closest thing 2026 has to a *default architecture*. Copy this pattern for your own product's routing tier.
- **Insight:** The reason to log `layer_a_pass` and `layer_b_pass` alongside cost is that the *right* routing decision is not "cheapest model" — it is "cheapest model that keeps verification pass-rate above threshold." That's the metric that stays with you through every future model release.

→ Cross-link: [`02` §1 open-weights + MCP convergence](./02-new-emerging.md#1-open-weights-and-mcp-stack) · [`04` §1 Agentic Context Engineering](./04-research-progress.md#1-ace).
