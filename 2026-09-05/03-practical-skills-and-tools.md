# Practical Skills & Tools — 2026-09-05

Four models shipped or repriced in seventy-two hours: **GPT-6 Astra, Fable 5.1, Muse Spark 1.3, Grok 4.6.** The single most useful thing you can do this weekend is build a **per-effort cost + quality dashboard** across them and put it on GitHub. Concrete, cheap to run, exactly the artifact **Anthropic Applied AI + OpenAI FDE + Meta Applied AI** are hiring against right now ([`05` §1](./05-career-and-startup.md#1-anthropic-fde)). Beneath that: **cache-read pricing changed on Sept 1** — refactor one agent tonight and reclaim 25–45% of its bill. **MCP roadmap update Aug 22** changed session semantics — a portfolio-friendly migration window is open. And **Simon Willison's "Don't classify. Hallucinate!"** pattern (Aug 14) is the single best free-lunch prompt technique of the summer.

Tags: `#practical #playbook #four-way-router #cache-refactor #mcp #context7 #chrome-devtools #hallucinate-then-embed #claude-code #llm-cli`

---

## 1. The four-way agent router — Opus 5 · Fable 5.1 · GPT-6 Astra · Muse Spark 1.3 {#1-four-way-router}

**What/why:** With Astra ([`01` §2](./01-big-lab-moves.md#2-gpt-6-astra)), Fable 5.1 ([`01` §3](./01-big-lab-moves.md#3-anthropic-51-s1)), and Muse Spark 1.3 ([`01` §4](./01-big-lab-moves.md#4-meta-muse-spark)) all shipping inside 72 hours — with Opus 5 still on the shelf from July — the market has four viable flagships at wildly different price points and capability curves. **The routing decision is now compiler-level, not vendor-level.** A minimal starting policy:

| Task pattern | First choice | Why |
|---|---|---|
| Long-horizon coding + tool use | **Opus 5, `effort=high`** | Still best SWE-bench Verified balance-of-cost; 1M ctx |
| Reasoning-heavy planning / research | **GPT-6 Astra** | ARC-AGI-3 99.9%; but $10/$50 per MTok — call sparingly |
| Bulk classify / extract / summarize | **Muse Spark 1.3** | ~$0.10/M blended; 98.5% long-context retrieval |
| Cache-heavy agentic loops | **Fable 5.1** | Cache-read $0.25/M (0.025× base) — free reads at scale |
| Verifier / adversarial critic | **Haiku 4.5 or Muse Spark 1.3** | Cheap enough to run per-step |
| Verified-cyber / life-sciences | **Mythos 5.1** (if enrolled) | Same weights as Fable 5.1, verified-only |

**The action:** Wire a router that (a) tags each subtask with `pattern`, `budget`, `latency_class`, `criticality`; (b) selects the first-choice model by table lookup; (c) logs `tokens_in / tokens_out / cache_read / cost / wall_time` per call. Push the log to a SQLite file (Simon's `llm` 0.33 does this for free — [§5](#5-llm-cli-hallucinate)).

**Sources:**
- [Artificial Analysis — Benchmarking GPT-6 Astra](https://artificialanalysis.ai/articles/benchmarking-gpt-6-astra) `[analysis]`
- [VentureBeat — Anthropic Fable/Mythos 5.1 pricing](https://venturebeat.com/technology/anthropics-claude-fable-5-1-and-mythos-5-1-arrive-with-a-75-cost-reduction-for-fable-cache-reads) `[secondary]`
- [Meta AI Research — Muse Spark 1.3](https://research.meta.ai/blog/introducing-muse-spark-1-3) `[primary]`
- [BenchLM — SWE-bench Verified leaderboard](https://benchlm.ai/benchmarks/swe-bench-verified) `[analysis]`

### Weekend deliverable

- Public repo `four-way-agent-router` with (a) the routing table above as YAML, (b) five reproducible agent tasks (Django bug fix, Notion page extractor, SEC-10K summarizer, weekly-email triage, terminal-bench mini task), (c) per-task cost/quality logs across all four flagships, (d) a README with two paragraphs of insight.
- Screenshot the cost delta and put it in your job-app portfolio slot. This is the artifact **Anthropic Applied AI** is scored on in their take-home ([`05` §1](./05-career-and-startup.md#1-anthropic-fde)).

---

## 2. Refactor to the new cache-read pricing tonight (Sept 1 change) {#2-cache-refactor}

**What/why:** Sept 1 changes to Anthropic API cost mechanics:

- **Cache-read pricing is now model-dependent**: **0.1× base input on most models**; **0.025× on Fable 5.1 and Mythos 5.1**. Cache-read on Fable 5.1 = **$0.25/M** (was $1/M).
- Cache-read tokens **no longer count against Input-Tokens-Per-Minute limits** on 3.7 Sonnet (backported).
- **Batches API + prompt caching now compose** — cache hits on batches are best-effort but stack the 50% batch discount.
- TTL is 5-min default; **mis-tuning that alone can swing bills 30–60%**.

**The refactor pattern** for any long-lived agent:

```
┌───────────────────────────────────────┐
│  System prompt                        │  ← above cache breakpoint
│  Tool defs (all)                      │  ← above cache breakpoint
│  Repository outline / long context    │  ← above cache breakpoint
├───────────────────────────────────────┤  ← breakpoint (marked with cache_control)
│  Per-turn user message                │  ← below (cheap or free-of-cache-write)
│  Recent tool results                  │
└───────────────────────────────────────┘
```

Then:
- Non-latency-sensitive backfills → **Batches API** (50% discount + caching stacks).
- Cache TTL: bump from default 5m to **1h** for stable system prompts (small write premium, huge read savings if reused).
- Log `cache_creation_input_tokens` vs `cache_read_input_tokens` vs `input_tokens` — target **>70% cache-read ratio** for anything running >100 turns/day.

**Sources:**
- [Anthropic — Token-saving updates](https://claude.com/blog/token-saving-updates) `[primary]`
- [Anthropic docs — Batch processing](https://platform.claude.com/docs/en/build-with-claude/batch-processing) `[primary]`

### Weekend deliverable

- Pick one agent you already use daily. Refactor per the pattern. Log 24 hours of runs. Publish a "Before / After" table in `/four-way-agent-router/cache-refactor.md`. Real numbers → interview gold.

---

## 3. MCP roadmap update (Aug 22) — the post-2026-07-28 migration window {#3-mcp-roadmap}

**What/why:** The MCP team published a new roadmap on **2026-08-22** covering the releases past the 2026-07-28 stateless spec. Concrete changes to plan for:

- **Stateless request/response core** landed — servers no longer track session; each request must carry all state it needs.
- **Cacheable list results** — `tools/list`, `resources/list`, `prompts/list` are now etaggable.
- **Authorization hardening pass** — OAuth 2.1 required; **Dynamic Client Registration formally deprecated** in favor of Client Identity Metadata Documents (CIMD).
- **Tasks extension** — moved out of experimental core into `io.modelcontextprotocol/tasks` with poll-based `tasks/get` + new `tasks/update` (SEP-2663).
- **Extensions framework** — formal namespacing (`io.<org>/<name>`) for capability declarations.

**Migration checklist for your MCP servers:**

- [ ] Remove all `session_id` state; move to request-scoped auth
- [ ] Migrate to OAuth 2.1 with CIMD (kill DCR endpoints)
- [ ] Add `Mcp-Method` / `Mcp-Name` headers so a plain round-robin LB works
- [ ] If you use tasks, move to the extension namespace + implement `tasks/update`
- [ ] Add etag support to `tools/list` — big cache win on cold starts

**Sources:**
- [MCP Blog — New Roadmap](https://blog.modelcontextprotocol.io/posts/mcp-roadmap/) `[primary]`
- [MCP Blog — 2026-07-28 spec release](https://blog.modelcontextprotocol.io/posts/2026-07-28/) `[primary]`

### Weekend deliverable

- Migrate one of your MCP servers to the new spec. Open a PR to a public MCP registry (`awesome-mcp-servers` or the official directory). PR = credential + interview conversation.

---

## 4. THIS WEEKEND'S artifact — merged: four-way router × 07-28 MCP × cache refactor {#4-this-weekends-artifact}

**One repo answers three interview questions at once.** Ship it before Monday.

**Repo layout:**

```
four-way-agent-router/
├── README.md                    # thesis, screenshots, cost delta
├── routing_table.yaml           # per-pattern first-choice
├── tasks/
│   ├── django_bugfix.py
│   ├── notion_extractor.py
│   ├── sec_10k_summarizer.py
│   ├── email_triage.py
│   └── terminal_task.py
├── mcp_servers/
│   └── postgres_analyst/       # 07-28-spec, OAuth 2.1, no session_id
├── router.py                    # tag → model → cost log
├── cost_refactor/
│   ├── before.md                # log before cache refactor
│   └── after.md                 # log after
└── analysis.ipynb               # cost/quality plot per task per model
```

Interview questions this artifact pre-answers:
1. **"Walk me through a cost-aware agent design."** — routing table + logs.
2. **"How do you migrate an MCP server to the new spec?"** — the `postgres_analyst` diff.
3. **"How do you actually measure agent cost?"** — `analysis.ipynb`.

Time budget: **Saturday 4 hrs + Sunday 3 hrs.** Realistic if the tasks are pared to 20-line reproducibles.

---

## 5. `llm` 0.33 + "Don't classify. Hallucinate!" — Simon Willison's cheapest wins {#5-llm-cli-hallucinate}

**What/why:** Two updates from Simon in late August:

- **`llm` 0.33** (Aug 22) — Simon's Python CLI. Adds **visible reasoning traces, server-side provider tools, content-addressable SQLite logs, OpenAI Responses API support.** SQLite-per-call logging alone turns any one-off exploration into a reproducible eval harness.
- **"Don't classify. Hallucinate!"** (Aug 14) — the anti-pattern of forcing an LLM to pick from a fixed vocabulary is fragile. Instead: **let it emit free-form tags, then vector-embed the tags and snap them to your real corpus.** Better recall, less prompt-engineering, and the "canonical vocabulary" evolves with your corpus rather than fighting it.

**Sources:**
- [Simon Willison — Don't classify. Hallucinate!](https://simonwillison.net/2026/Aug/14/dont-classify-hallucinate/) `[primary]`
- [Simon Willison — LLM 0.33 release](https://simonwillison.net/2026/Aug/22/llm/) `[primary]`

### Weekend deliverable

- Take a classification task you already have (email triage, PR labeling, issue routing) and re-implement it hallucinate-then-embed style. Log everything via `llm` 0.33's SQLite. Compare accuracy vs the classify version — write it up in a 500-word README.

---

## 6. Claude Code (Sept 2026) — `/claude-api cost-optimize` + `/diff` panel {#6-claude-code-sept}

**What/why:** The September Claude Code changelog added:

- **`/claude-api cost-optimize`** — profiles your project's Claude API spend and walks you through caching / token hygiene / batch / effort / model-choice **one measured change at a time**. Directly addresses the [§2](#2-cache-refactor) refactor without hand-tuning.
- **`SendFeedback` tool** — Claude drafts a bug report you review via `/feedback`.
- **`/diff` panel** — fullscreen alongside the conversation showing uncommitted changes live as Claude edits. Removes the "did Claude actually change that?" tax on long refactors.
- **Auto mode** is default on Pro/Max/Team since Aug 14.

**Sources:**
- [Claude Code Changelog](https://code.claude.com/docs/en/changelog) `[primary]`
- [Origami — Claude Code August 2026 update](https://origami.sa/en/blog/claude-code-august-2026/) `[secondary]`

### Weekend deliverable

- Run `/claude-api cost-optimize` on the same agent from [§2](#2-cache-refactor) — treat it as ground truth on your before/after refactor. Open `/diff` on a >200-line change and confirm the flow.

---

## 7. MCP servers worth adding to your Claude Code config today {#7-mcp-servers}

**What/why:** August npm/GitHub metrics — three MCP servers are now unambiguously the baseline install:

- **Playwright MCP** — 23.7M downloads. Browser automation / testing.
- **Context7** — 61K stars / 3.9M downloads. **Fetches fresh library docs at inference time — kills stale-training-data bugs.**
- **Chrome DevTools MCP** — inspect console, network, Lighthouse, perf traces from an agent. Unblocks agentic perf-regression debugging.

New in August: **Kubernetes, Terraform, Auth0, Supabase** MCP servers.

**Sources:**
- [DEV — 10 MCP servers worth adding to your AI coding workflow in 2026](https://dev.to/erikch/10-mcp-servers-worth-adding-to-your-ai-coding-workflow-in-2026-1j1m) `[secondary]`
- [Agent Depot — Cursor / Windsurf / Claude Code mid-2026 recap](https://agentdepot.dev/blog/cursor-windsurf-claude-code-whats-new-mid-2026) `[analysis]`

### Weekend deliverable

- Add Context7 + Chrome DevTools MCP to your Claude Code config. Reproduce one real perf regression from an old side project: have Claude pull a Lighthouse trace, cross-check current framework docs via Context7, propose a patch. Screenshot the three-tool loop for your portfolio.

---

## 8. Ethan Mollick's Summer 2026 "which AI for what" guide (Aug 31) {#8-mollick-guide}

**What/why:** Mollick's plain-language decision table for **ChatGPT vs Claude, model + thinking-level per task, and the four-way of Work / Cowork / Codex / Claude Code.** Companion post "Agency and Agents" argues for org design around agents that plan and escalate without asking (his "Twilight Factory" layer).

**Sources:**
- [One Useful Thing — Agency and Agents](https://www.oneusefulthing.org/p/agency-and-agents) `[primary]`
- [One Useful Thing — Summer 2026 opinionated guide](https://substack.com/@oneusefulthing/p-166124170) `[primary]`

### Weekend deliverable

- Print Mollick's decision table. Route one recurring personal workflow (weekly reading digest, PR triage, class prep) through his recommended pairing for one week. Measure time saved.

---

## 9. Cross-links {#9-cross-links}

- Career: [`05` §1 Anthropic FDE hiring across 8 cities](./05-career-and-startup.md#1-anthropic-fde) — the artifact from [§4](#4-this-weekends-artifact) is the differentiator
- Research: [`04` §5 ProgRouter](./04-research-progress.md#5-prog-router) — the academic paper behind the [§1](#1-four-way-router) routing table
- Big Lab: [`01` §3 Anthropic S-1 Monday](./01-big-lab-moves.md#3-anthropic-51-s1) — the eval framework you'll want in hand when the S-1 lands
