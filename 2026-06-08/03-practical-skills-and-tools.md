# Practical Skills & Tools — 2026-06-08

This week's practical edge: **Claude Opus 4.8 shipped (May 28) and changes the orchestrator economics.** SWE-bench Verified **88.6%**, SWE-bench Pro **69.2%**, Terminal-Bench 2.1 **74.6%**, **4× less likely** to silently leave bad code, **Fast mode 2.5× faster and 3× cheaper** — all at the *same headline price* as Opus 4.7 ($5/$25 regular, $10/$50 Fast). The 30-minute project tonight: **upgrade your `CLAUDE.md` orchestrator config to 4.8, swap Sonnet 4.6 as worker, add a per-step cost log, and re-run yesterday's task to capture a before/after.** That artifact is the single most-useful interview-asset for any frontier-lab Solutions / FDE conversation in June (and it's the direct mitigation for the **June-15 Agent SDK metering cliff, T-minus 7 days**). Companion: **the 2026 MCP hygiene checklist** to lock down before WWDC's Extensions API ships you a *second* "should I trust this tool?" surface.

Tags: `#claude-code #opus-4-8 #mcp #orchestration #cost-routing #practical #metering`

---

## 1. The Opus-4.8 orchestrator + Sonnet-4.6 worker baseline (re-run tonight) {#1-opus-48-baseline}

**What changed:** Claude Opus 4.8 (released May 28) is a **drop-in upgrade** for the orchestrator role in the multi-agent pattern that's become the 2026 default ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)). The numbers that matter for *your* config:

| Metric | Opus 4.7 | Opus 4.8 | Delta |
|---|---|---|---|
| SWE-bench Verified | 87.6% | **88.6%** | +1.0pp |
| SWE-bench Pro | 64.3% | **69.2%** | +4.9pp (the real jump) |
| Terminal-Bench 2.1 | 66.1% | **74.6%** | +8.5pp |
| Silent-bad-code rate | baseline | **~25% of baseline** | 4× safer |
| Fast-mode latency | baseline | **2.5× faster** | — |
| Fast-mode $/Mtok in/out | $15 / $75 | **$10 / $50** | ~33% cheaper |
| Regular $/Mtok in/out | $5 / $25 | **$5 / $25** | unchanged |

It's also the **only model that passes every case on the "Super-Agent" benchmark end-to-end**, and the first to break 10% overall on the "all-pass" Legal Agent Benchmark — both of which are stand-ins for "can it actually finish a multi-step real-tool task?"

**Sources:**
- [Anthropic — Introducing Claude Opus 4.8](https://www.anthropic.com/news/claude-opus-4-8) `[primary]`
- [Anthropic Docs — What's new in Claude Opus 4.8](https://platform.claude.com/docs/en/about-claude/models/whats-new-claude-4-8) `[primary]`
- [VentureBeat — Anthropic's Claude Opus 4.8 with 3X cheaper fast mode and near-Mythos level alignment](https://venturebeat.com/technology/anthropics-claude-opus-4-8-is-here-with-3x-cheaper-fast-mode-and-near-mythos-level-alignment) `[secondary]`
- [TechCrunch — Anthropic releases Opus 4.8 with new 'dynamic workflow' tool](https://techcrunch.com/2026/05/28/anthropic-releases-opus-4-8-with-new-dynamic-workflow-tool/) `[secondary]`
- [The Decoder — Anthropic ships Claude Opus 4.8 as a "modest but tangible improvement"](https://the-decoder.com/anthropic-ships-claude-opus-4-8-as-a-modest-but-tangible-improvement-that-tops-gpt-5-5-in-most-benchmarks/) `[secondary]`
- [Computing for Geeks — Claude Opus 4.8: Features, Benchmarks, Claude Code](https://computingforgeeks.com/claude-opus-4-8-released-features-benchmarks/) `[analysis]`

### Tonight's 30-minute upgrade (the artifact)

```bash
# 1. Pin the model in your global config — explicit beats implicit
echo "model: claude-opus-4-8" >> ~/.claude/settings.json   # or via /config

# 2. In any project's CLAUDE.md, lock the orchestrator/worker split:
cat >> CLAUDE.md <<'EOF'
## Orchestration policy (Opus 4.8 orchestrator + Sonnet 4.6 workers)
- Use `claude-opus-4-8` for: planning, code review, multi-file refactor decisions, eval design
- Use `claude-sonnet-4-6` for: parallel sub-agent execution, line-level edits, mechanical work
- Use Opus *Fast mode* for: interactive prompts where I'm waiting on the response live
- Cap any single task at $1.50 in API spend without an explicit override prompt
- Log every model call to .agent-cost.log with: timestamp, model, input_tokens, output_tokens, $cost
EOF

# 3. Add a hook to log cost on every model call (settings.json):
#    "hooks": { "PostToolUse": [{ "matcher": "*", "command": "scripts/log_cost.sh" }] }

# 4. Run a known-baseline task (e.g. a small refactor you've done before with 4.7), 
#    then diff .agent-cost.log against your last 4.7 run.
```

**What to capture for the artifact:** a 3-line README diff showing **(a) total $ spent on the baseline task before vs after, (b) wall-clock seconds before vs after, (c) any change in test-pass rate.** That's the interview talking-point — **"I measured the 4.7→4.8 migration on a real task; here's the cost delta and reliability delta."** Three lines of evidence beats six paragraphs of "I follow Claude best practices."

### Why this matters (Job · Startup · Insight)

- **Job lens:** The interview tell is **"do you measure your own model spend per task?"** With **June-15 Agent SDK metering 7 days away**, this stops being a hygiene question and becomes a competence filter for any Anthropic Solutions / FDE / AI Engineer role. **Per-task cost log = ticket of admission.** Bring the artifact to interviews and to your LinkedIn — "I cut my agent-task spend 40% by routing Opus-orchestrator to Sonnet-workers, here's the diff" is a much better story than any CLAUDE.md screenshot.
- **Startup lens:** Cost-routing across model tiers is **a tiny, ownable wedge** that lets you ship MVPs at 30–40% lower marginal cost than competitors who default to Opus-only. It's not a moat, but it's a **6-month margin advantage** while everyone else is figuring it out — meaningful in seed-stage unit economics.
- **Insight:** The 4× silent-bad-code reduction is the **most under-rated number** in the 4.8 release. The 80%-of-merged-code disclosure ([`01` §3](./01-big-lab-moves.md#3-anthropic-self-build)) and the 4× safer-code number are the *same story from two angles*: Anthropic isn't shipping a better model so much as **shipping a model whose default behavior is to verify itself before merging.** That's the actual frontier move — and your `CLAUDE.md` should reflect it (always plan → annotate → "address all notes, don't implement yet" → implement, in that order).

→ Cross-link: [2026-05-22/03 §1 — the original orchestrator/worker pattern](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [`05` §1](./05-career-and-startup.md#1-fde-comp) — comp band that pays for this skill.

---

## 2. The 2026 MCP hygiene checklist (lock this down before Apple's Extensions ships) {#2-mcp-hygiene}

**What this is:** A 6-item checklist of MCP server configuration practices that have hardened over the last 60 days, distilled from the practitioner consensus across Claude docs, MCP Directory, TinyFish's "30 Verified" review, and Builder.io's tip-list. Lock these in *before* WWDC's Apple Intelligence Extensions ships you a *second* surface to evaluate ([`01` §1](./01-big-lab-moves.md#1-wwdc)) — same trust-and-budget questions apply.

1. **One narrow credential per MCP server.** A read-only GitHub PAT scoped to one repo for `github-mcp`. A read-only Postgres user for the database server. If a server gets compromised, blast radius is one repo, not your account.
2. **Environment-variable secrets only.** Never inline tokens in `mcp.json` or `settings.json`. Use `export GITHUB_MCP_TOKEN=...` in a `.envrc` (gitignored) or a real secrets manager. Tokens in config files leak via screen-share, screenshots, and copy/paste.
3. **Cap your active servers at 3–5.** Each MCP server's tool list inflates Claude's tool-selection prompt; >5 active servers measurably degrades selection quality. Run only what today's task needs; toggle the rest.
4. **Comment every server in your config with *why*.** Treat `mcp.json` like a dotfile — every entry gets a 1-line `// because:` note. Forces you to delete servers you no longer use (typical: I added `notion-mcp` for one report, never removed it).
5. **Audit on every change.** Whenever you `claude mcp add` or pull a new dotfile, run `claude mcp list` + `claude mcp diff` and read every line. *New tools are a new attack surface.*
6. **Default to local stdio servers, not remote HTTP, for anything touching private data.** Remote MCP servers are convenient but introduce a network egress + a third-party trust boundary. Local stdio servers (most official MCP servers) run in-process — no network, no shared credentials.

The single best MCP-tools-of-the-week list, with usage notes, is TinyFish's "30 Verified" review (linked below) — useful as a *what to evaluate*, not a *what to install*.

**Sources:**
- [Anthropic — Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Clarista — Claude Code MCP Servers & Plugins: The Complete 2026 Guide](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) `[secondary]`
- [TinyFish — Best MCP Servers for Claude Code 2026: 30 Verified](https://www.tinyfish.ai/blog/best-mcp-servers-for-claude-code) `[secondary]`
- [Truefoundry — MCP Authentication in Claude Code 2026 Guide](https://www.truefoundry.com/blog/mcp-authentication-in-claude-code) `[analysis]`
- [Builder.io — 50 Claude Code Tips and Best Practices For Daily Use](https://www.builder.io/blog/claude-code-tips-best-practices) `[analysis]`
- [MCP Directory — Claude Code Best Practices: From Vibe Coding to Agentic Engineering](https://mcp.directory/blog/claude-code-best-practices) `[analysis]`

### Why this matters (Job · Startup · Insight)

- **Job lens:** "I can configure a hardened MCP stack" is the **smallest concrete skill that maps directly into the Solutions Engineer / FDE JD bullet list** at Anthropic, OpenAI, Palantir, Databricks, and the 39 AI companies hiring FDEs (see [`05` §1](./05-career-and-startup.md#1-fde-comp)). Bring your `mcp.json` (sanitized) to interviews — it's a 30-second proof-of-skill that's stronger than any cert.
- **Startup lens:** Most YC-stage AI companies *do not* do (1) and (5) correctly — narrow credentials + audit-on-every-change. A **"hardened-by-default MCP wrapper"** product (or even an open-source linter for `mcp.json`) is a $0-to-PMF wedge you could ship by next weekend. Pitchable as the **"DevSecOps for agent tools."**
- **Insight:** MCP servers are the **2026 equivalent of npm dependencies in 2016**. The supply-chain attack surface is identical; the security tooling is 7 years behind. Whoever ships the `npm audit` of the MCP ecosystem will get the same kind of category-defining traction Snyk got. **Even if you're not building it — being one of the first people who can talk credibly about MCP supply-chain hygiene in an interview is worth real money.**

→ Cross-link: [`01` §1 — Apple Extensions API as the next "trust this tool?" surface](./01-big-lab-moves.md#1-wwdc) · [2026-05-17/03 — the Karpathy `CLAUDE.md` thread](../2026-05-17/03-practical-skills-and-tools.md).

---

## 3. The one-line cost-router pattern (T-7 to June-15 metering) {#3-cost-router}

**What this is:** A pattern, not a tool. With June-15 Agent SDK metering 7 days away, you don't need to write a router framework — you need to add **one explicit model-tier decision** at the top of every script you run programmatically:

```python
# In every Claude Code project, top of every long-running script:
MODEL = (
    "claude-opus-4-8"        if task_type in ("plan", "review", "design") else
    "claude-sonnet-4-6"      if task_type in ("execute", "edit", "test") else
    "claude-haiku-4-5"       if task_type in ("classify", "extract", "lint") else
    "claude-sonnet-4-6"      # safe default
)
```

That's it. Three tiers, named at the top of the script, never re-decided mid-loop. The point is **not** to be clever — it's to make the cost decision *legible* to future-you (and to interviewers reading your code). For the 90% of agent tasks where the workload pattern is "one plan + many executes + many classifies," this single change typically lands the **40% cost reduction** the orchestrator/worker pattern promises ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) — without writing any new framework.

**Sources:**
- [Anthropic — Best practices for Claude Code (model-routing section)](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Anthropic Docs — What's new in Claude Opus 4.8 (Fast mode pricing)](https://platform.claude.com/docs/en/about-claude/models/whats-new-claude-4-8) `[primary]`

### Why this matters (Job · Startup · Insight)

- **Job lens:** "I tier my model calls by task type" is one sentence in an interview that signals **you understand the unit economics of AI applications.** That's exactly what the FDE/Solutions track gets paid for ([`05` §1](./05-career-and-startup.md#1-fde-comp)). Practice the sentence.
- **Startup lens:** If your MVP runs on Opus-only, your **gross margin is 3–5× worse than it needs to be**, and a *sophisticated* customer will price-pressure you on it. Tiered routing is the *cheapest* defensible unit-economics narrative you can put in a deck.
- **Insight:** The June-15 metering change is going to **publicly humiliate** the developers who didn't add this — they'll get their first credit-exhaustion notice and post about it. **Don't be in that batch.** Set the toggle (per the [2026-05-18 watchlist row](../WATCHLIST.md) reminder) *and* add the tiered router this week.

→ Cross-link: [§1 — the orchestrator config that uses this pattern](#1-opus-48-baseline) · [2026-05-22/03 §1 — orchestrator/worker cost math](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost).
