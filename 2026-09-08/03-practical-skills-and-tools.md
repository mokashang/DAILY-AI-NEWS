# Practical Skills & Tools — 2026-09-08

Things you can *do* this week. Ordered by ROI on your time.

---

## 1. Flip your default coding agent to Claude Fable 5.1 with prompt caching ON (30 min tonight) {#1-fable-51-cache}

**The change.** Fable 5.1 (released Sep 1, [`01` §1](./01-big-lab-moves.md#1-fable-mythos-51)) kept sticker pricing flat ($10/$50 per MTok) but **cut cache-read pricing 75%: $1 → $0.25 per MTok**. Typical repo workloads run ~25% cheaper; **agentic loops that re-read a working set every step run ~45% cheaper**.

**What to actually do tonight (30 min).**
1. Update your Claude Code / API client to point at `claude-fable-5-1`.
2. Turn on **prompt caching** for your system prompt + repo context (put your `CLAUDE.md` and long instructions at the top; wrap the block in the cache control header your SDK uses).
3. Run your **normal weekday coding-agent session** — one or two real tickets. Nothing artificial.
4. Read the response usage from the API: cache-read tokens vs cache-creation tokens vs fresh input tokens. **Note the ratio.** Anything above ~50% cache hits and you're now paying $0.25 per MTok on that portion — that's the ~45% workload savings materializing.
5. Screenshot the last week's Anthropic Console usage dashboard **before** you switch, then again next week. That delta is your interview artifact.

**Guardrails.**
- Cache hits require **byte-identical prompt prefixes.** If you insert a live date, a random seed, or a timestamp near the top, cache invalidates every call. Move those to the *end* of the prompt.
- Cache expiry defaults to **5 minutes** — extend to 1h with `cache_control: {type: "ephemeral", ttl: "1h"}` when your loop runs longer than that.
- Fable 5.1 GA has the standard safeguards; if you're building for cyber/life-sci and need Mythos 5.1, apply to Anthropic's restricted-access program separately.

**Sources.**
- [Fable 5.1 & Mythos 5.1 — cache-read 75% off (VentureBeat)](https://venturebeat.com/technology/anthropics-claude-fable-5-1-and-mythos-5-1-arrive-with-a-75-cost-reduction-for-fable-cache-reads) `[secondary]`
- [Fable 5.1 & Mythos 5.1 benchmarks (Vellum)](https://www.vellum.ai/blog/claude-fable-5-1-mythos-5-1-benchmarks-explained) `[analysis]`
- [Claude Fable 5.1 release notes (MacRumors, 2026-09-01)](https://www.macrumors.com/2026/09/01/anthropic-claude-fable-5-1/) `[secondary]`
- [Claude Mythos 5.1 platform docs](https://platform.claude.com/docs/en/models/mythos-5-1/overview) `[primary]`

**Why it matters to you.**
- **Job:** every applied-AI / FDE interview loop asks you to walk through a real cost-optimization. Show up with your own before/after numbers, not marketing copy.
- **Startup:** cache-heavy unit economics changed materially in one release. Anything you had that was borderline is worth re-running tonight.
- **Insight:** the derivative on **frontier-workhorse token pricing** is now flat-to-down. Plan roadmaps that assume this continues; the risk of *higher* token costs 12 months out is small.

**Tags:** `#claude-fable-51 #prompt-caching #api-cost #coding-agent`

---

## 2. Ship a stateless-MCP migration PR before Thursday (~4 hours Tue–Wed) {#2-mcp-migration-update}

**The change.** MCP **2026-07-28** (stateless) is now in **active production migration**. Google Developers Blog and Cloudflare shipped first-party migration guides; the deprecation window for **Roots, Sampling, Logging, Dynamic Client Registration, and legacy HTTP+SSE** is 12 months minimum. Two new primitives to internalize now:
- **MCP Apps (SEP-1865):** servers ship interactive HTML rendered by hosts in a sandboxed iframe. Tools declare UI templates ahead of time; hosts prefetch and security-review.
- **Tasks extension:** stateless-native long-running work. `tools/call` returns a task handle; client drives `tasks/get / update / cancel`.

Everything else is still there — session state is what left. Every request now carries protocol version, client info, and capabilities inline via `_meta`.

**What to actually do (~4 hours across Tue and Wed).**
1. **Pick one existing MCP server you already have** (or fork a small one — e.g. a Notion or GitHub connector from the community list). Do *not* start a green-field server for this exercise; the migration is the artifact.
2. Read the [2026-07-28 spec](https://blog.modelcontextprotocol.io/posts/2026-07-28/) end-to-end (~45 min).
3. Strip session state: no `initialize`/`initialized` handshake, no `Mcp-Session-Id`. Every handler is a pure function of the request.
4. Move the connection-time metadata into `_meta` on every request. Verify with the reference client.
5. Add **one** tool with an MCP Apps UI template (a form, a picker — anything that renders in a sandboxed iframe). This is the visual differentiator on the PR diff.
6. Add **one** long-running tool wired through the Tasks extension. Return a task handle within 100ms; poll with `tasks/get`.
7. Write a `README.md` section: "**Migration diff and one thing I learned.**" Post the repo on GitHub, tweet-thread it, link on LinkedIn.

**Why this is the portfolio piece of the week.** The migration window is **mid-migration, not post-migration** — most public servers still ship the old spec. A PR that lands the migration cleanly on a real server (yours or open-source), with the two new primitives exercised, is a résumé line that any Applied-AI or FDE hiring manager will read as concrete signal of currency + shipping speed.

**Sources.**
- [The 2026-07-28 Specification (MCP blog)](https://blog.modelcontextprotocol.io/posts/2026-07-28/) `[primary]`
- [Scaling AI agent infrastructure with MCP stateless updates (Google Developers Blog)](https://developers.googleblog.com/scaling-ai-agent-infrastructure-with-the-mcp-stateless-updates/) `[primary]`
- [The next generation of MCP (Cloudflare Blog)](https://blog.cloudflare.com/mcp-v2/) `[primary]`
- [MCP 2026-07-28: from local tool to distributed protocol — migration guide (AAIF)](https://aaif.io/blog/mcp-2026-07-28-whats-changing-and-how-to-migrate) `[analysis]`
- [MCP protocol update: more secure, production-ready (ITdaily)](https://itdaily.com/news/software/mcp-2026-update-specs/) `[secondary]`
- [Update on the next MCP protocol release (modelcontextprotocol.info)](https://modelcontextprotocol.info/blog/mcp-next-version-update/) `[aggregator]`
- [Claude Code MCP Setup — 2026 practical guide (DEV Community)](https://dev.to/stravukarl/claude-code-mcp-setup-a-practical-2026-guide-424f) `[analysis]`

**Why it matters to you.**
- **Job:** the delta between a candidate who "has read the spec" and one who "shipped the migration" is the entire signal for junior/mid FDE loops right now. This is a two-day investment for a résumé line that reads like eight weeks.
- **Startup:** if your product exposes an MCP server, you have a 12-month deprecation clock. Do it while the migration is portfolio-signalable, not while it's overdue triage.
- **Insight:** stateless was requested for two years and finally shipped. The next request-cycle-driven MCP change to watch is likely **stronger auth primitives** (OAuth 2.1 hardening keeps recurring in the spec revisions).

**Tags:** `#mcp #stateless #mcp-apps #tasks #migration #portfolio`

---

## 3. Claude Code September updates worth turning on today (~15 min) {#3-claude-code-updates}

**The change.** Claude Code shipped meaningful CLI updates in early September (per [Releasebot Claude Code changelog](https://releasebot.io/updates/anthropic/claude-code) and Anthropic release notes).
- **`managedMcpServers` managed setting** — org-level provisioning of HTTP/SSE MCP servers to every user.
- **`--permission-prompts none`** for unattended headless hosts.
- **`/claude-api cost-optimize`** — profiles existing Claude API spend and walks you through caching / token hygiene / batch / effort / model-choice levers.
- Fixed: concurrent sessions no longer revert each other's changes.
- Improvements across sessions, terminals, background tasks, remote control, and VS Code.

**What to do (~15 min).**
1. Update Claude Code to the latest.
2. Run `/claude-api cost-optimize` on your active project. Read the recommendations top-to-bottom.
3. If you run Claude Code on a headless CI host or a scheduled task: add `--permission-prompts none` and re-test the guardrails you have in place — this changes the default from "prompt on unknown" to "deny on unknown," which is the safer path but will break scripts that assumed a human was there.
4. If you're on a team, ask your admin whether **managedMcpServers** should be provisioned in the org — that's the answer to the "everyone in the team is manually adding the same six MCP servers" pain.

**Sources.**
- [Claude Code changelog (September 2026)](https://code.claude.com/docs/en/changelog) `[primary]`
- [Claude Code updates by Anthropic — September 2026 (Releasebot)](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Claude Code Changelog September 2026 (Gradually.ai)](https://www.gradually.ai/en/changelogs/claude-code/) `[aggregator]`
- [Claude Code News — September 2026 (blog.mean.ceo)](https://blog.mean.ceo/claude-code-news-september-2026/) `[aggregator]`
- [Claude Code best practices: CLAUDE.md and checks (Iwoszapar)](https://www.iwoszapar.com/p/claude-code-best-practices) `[analysis]`

**Why it matters to you.**
- **Job:** `--permission-prompts none` + a well-scoped agent is the exact recipe interviewers ask you to describe when they're testing "would you deploy this to a real customer environment." Learn the trade-offs by using them.
- **Startup:** managedMcpServers is what makes a Claude Code deployment scale from "one dev's laptop" to "engineering org standard." Any B2B agent-tooling wedge should have a story here.
- **Insight:** Anthropic's product cadence on Claude Code is now indistinguishable in speed from a standalone startup's — that's what "Claude Code as a platform" looks like operationally.

**Tags:** `#claude-code #mcp #cost-optimize #headless #org-tools`

---

## 4. The "reason with Fable, execute with Flash 3.8" pattern (weekend project) {#4-two-tier-agent-pattern}

**The setup.** Two frontier releases the same week ([`01` §1 Fable 5.1](./01-big-lab-moves.md#1-fable-mythos-51) and [`01` §3 Gemini 3.8 Flash](./01-big-lab-moves.md#3-gemini-38-flash)) both pushed *coding-agent* benchmarks up: Fable 5.1 leads AAII; Gemini 3.8 Flash lands 73.7% on DeepSWE v1.1 at $0.75/$3.75. The **cost gap** between them (~13× on output tokens) plus the **capability gap** (small enough that Flash is credible on well-scoped subtasks) makes the two-tier orchestration the cost-optimal default.

**The pattern.**
```
Planner    →  Claude Fable 5.1 (effort=high, prompt-cached repo context)
  produces: task graph, per-task acceptance criteria, per-task success test
Worker     →  Gemini 3.8 Flash (agentic mode, per-task iteration budget)
  produces: patch + test result for each subtask
Verifier   →  Claude Fable 5.1 (effort=medium, cached repo context)
  produces: accept/reject + retry note
```

Ship it as a small repo this weekend (a single `orchestrator.py` + a fixture repo you run it against). Emit **per-step cost log to stdout**. Post before/after tokens vs a Fable-only baseline.

**Why it's worth the weekend.** Every Applied AI / FDE interview between now and December will ask a variant of *"how would you drive cost down on this agent pipeline?"* This is the artifact that turns the answer from "I would consider…" into "here's the repo, here's the log, here's the delta."

**Tags:** `#orchestration #cost-optimization #agents #fable-flash #weekend-artifact`

---

## Quick tips (5 min each)

- **Rerun your baseline before Jan 1 2027.** Gemini 3.8 Flash sticker rises **$0.75 → $1.50 input / $3.75 → $7.50 output** at year-end ([Artificial Analysis](https://artificialanalysis.ai/articles/gemini-3-8-flash)). If your product's unit economics depend on Flash pricing, your Q4 planning number should be the Jan 1 rate.
- **Read the GPT-6 Astra system card before your next lab interview.** Alignment / safety / preparedness roles now expect a working vocabulary for CoT monitorability, sandbagging, and behavioral-vs-mechanistic auditing. Cite the card. → [OpenAI safety overview](https://openai.com/index/safety-overview-gpt-6-astra/).
- **`grep -r "#mcp" .`** across this repo whenever you want to catch up on how the MCP thread has moved week by week. That's what the `#tag` system exists for.

See [`01-big-lab-moves.md`](./01-big-lab-moves.md) for the model-release context, [`02-new-emerging.md`](./02-new-emerging.md) for the Mistral / YC S26 emerging picture, and [`04-research-progress.md`](./04-research-progress.md) for the CoT-monitorability + Fermat-in-Lean research angles that back the tips above.
