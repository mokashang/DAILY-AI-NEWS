# Practical Skills & Tools — 2026-10-15

**Two concrete tasks today.** First: re-test your `.claude/hooks` against the Oct 8 hook-interpretation fix (`v2.1.294`) — if you were counting on blocking rules to prevent writes to `secrets/`, you may have been silently permissive. Second: scope the migration of your public MCP server to the `2026-07-28` stateless spec — because every pre-July MCP implementation is now technical debt, and your portfolio artifact is one of them.

Tags: `#claude-code #hooks #mcp #tooling #portfolio`

---

## 1. Claude Code v2.1.294 (Oct 8) — the hook-interpretation fix matters more than it reads {#1-cc-2-1-294}

**What shipped (2026-10-08):** Per havoptic.com's third-party changelog, Claude Code `v2.1.294` fixed how **instruction-based hooks** are interpreted so blocking rules work as intended. (The havoptic release page is an aggregator, so treat the version numbering as `[aggregator]` until the official changelog confirms.)

**What this means in practice:**

Before the fix, a non-trivial subset of instruction-matched blocking rules — the ones that specified string-match conditions on tool-call *contents*, not just tool-call *names* — were being evaluated in a way that could silently permit the call. The specific failure mode: a `PreToolUse` hook that said "block any `Write` where `file_path` contains `secrets/`" could still allow a write that passed through variable interpolation, because the matcher ran against the pre-interpolation instruction, not the post-interpolation call.

**Why it matters to you:**

- **If your `.claude/hooks` config has blocking rules on file paths, API endpoints, or shell commands, re-run your own red-team against them this morning.** Simplest test: write a Claude Code prompt that *should* be blocked, confirm it is blocked, then upgrade to `v2.1.294` and run the same prompt. If the behavior changes between versions, you had a silent gap.
- **For portfolio artifacts:** the public MCP server you're shipping should have its own hook tests in CI — not just unit tests on tool behavior, but adversarial tests on hook enforcement. **This is a differentiator in interviews:** "I shipped an MCP server with hook-coverage tests after reading the 2.1.294 fix" is a two-sentence story that signals security hygiene most new-grad applicants don't have.
- **The combined Oct 7 + Oct 8 stack:** v2.1.293 made Haiku 5.5 (1M context) the default; v2.1.294 fixed hooks. **The stack is now self-consistent** — meaning this is the right week to lock in your `.claude/settings.json` and `.claude/hooks/*.sh` baselines. Any changes you make now will survive the next 30 days of version bumps without churn.

**Sources:**
- [havoptic.com — Claude Code October 2026 Releases](https://www.havoptic.com/releases/claude-code/2026/10) `[aggregator]`

### Concrete action today (10 minutes)

```bash
# 1. See which Claude Code version you're on
claude --version

# 2. Upgrade if below 2.1.294
# (Follow the installer's self-update flow; do not downgrade.)

# 3. Smoke-test any blocking hook you've written:
#    Pick the strictest hook in .claude/hooks/*.sh
#    Prompt Claude to attempt the exact action the hook forbids
#    Confirm it blocks

# 4. If you catch a regression, open an issue in your own portfolio repo
#    with the before/after transcript — that transcript becomes an interview artifact
```

## 2. MCP spec `2026-07-28` is fully stateless + under Linux Foundation — migrate your public MCP server this weekend {#2-mcp-stateless}

**What's true as of today:**

- **The `2026-07-28` spec is the current MCP revision.** It removed the protocol-level session handshake and made every request carry its own protocol version + client capabilities. The protocol is now **fully stateless**.
- **Governance:** the Model Context Protocol project is now under the **Linux Foundation**. Download count went from ~2M monthly at launch to ~97M by March 2026 (per secondary blog; treat as a trend indicator, not a precise figure).
- **Roadmap:** the maintainers' Aug 22, 2026 roadmap names 5 priorities — agentic messaging primitives, HTTP-native transport (including local servers), and three others. **Nothing in the roadmap has shipped yet** — so the current migration task is just the stateless move, not anything downstream.

**Why it matters to you:**

- **If your public MCP server (per the ME.md portfolio list) was built before July 28, 2026, it is now protocol-non-compliant.** Specifically:
  - You likely held a server-side session object across requests. The new spec doesn't want that.
  - You likely accepted an `initialize` call that negotiated capabilities once. The new spec wants each request to carry its own capability declaration.
  - Your tests probably assume session continuity. They need to be re-written to be request-isolated.
- **The portfolio-artifact value of a stateless MCP server went up this week.** Any MCP server you ship after the `2026-07-28` migration can be marketed as "written against the current spec," which is a credibility beat that recruiters at Anthropic Solutions / Partnerships specifically look for.
- **Side benefit:** stateless servers scale horizontally much more cleanly. Your migration will almost certainly cut your inference-side latency and let you deploy to Cloudflare Workers / Vercel Edge / Lambda without a session-affinity shim.

**Sources:**
- [DEV Community — MCP's 2026 Update Makes Remote Servers Easier to Scale](https://dev.to/zira125/mcps-2026-update-makes-remote-servers-easier-to-scale-oo0) `[secondary]`
- [Cloudflare blog — The next generation of MCP](https://blog.cloudflare.com/mcp-v2/) `[primary]`
- [Agentic AI Foundation — MCP 2026 Changes the Rules](https://aaif.io/blog/mcp-2026-changes-the-rules) `[analysis]`
- [Mervin — MCP's New Roadmap: What's Next for the Protocol](https://mer.vin/news/mcps-new-roadmap-whats-next-for-the-protocol/) `[aggregator]`

### Concrete action this weekend (~4 hours)

1. **Pull your public MCP server's current code.** Verify the spec version it targets (`protocolVersion` in the handshake code).
2. **Clone the latest TypeScript / Python SDK that targets `2026-07-28`.** The SDKs do most of the stateless migration for you if you re-generate server stubs from the current spec.
3. **Delete server-side session state.** Replace with request-scoped context passed in each call.
4. **Re-write your test suite to be request-isolated.** Each test should be a single JSON-RPC request / response pair.
5. **Deploy to a serverless target** (Cloudflare Workers or Vercel Edge) — the stateless migration makes this trivial.
6. **Write a 150-word README section** titled "Spec compliance: `2026-07-28`" with a 3-line summary of what the migration changed and a link to the diff. **This paragraph is the interview artifact.**

## 3. Pre-IPO interview-prep tooling: the Anthropic one-pager {#3-ipo-prep-tooling}

Not a new tool, but a new application of your existing tools:

**Build an "Anthropic IPO one-pager" using Claude Code + the `[1m]` context window.** Prompt skeleton:

```
I'm interviewing at Anthropic for [role]. Help me build a 4-section
one-pager on the IPO:

1. Bull case: 5 bullets from the leaked S-1 (revenue growth, adjusted
   operating profit, Frontier Academy, Haiku 5.5 pricing, enterprise
   distribution via consulting partners).
2. Bear case: 5 bullets (net loss, customer concentration, compute
   commitment, Pentagon break, post-IPO revenue sustainability per WSJ).
3. For each bear bullet: a one-sentence counter-reading.
4. My personal take in one sentence that would land in an interview.

Use these sources: [paste the Oct 14 and Oct 15 edition links from the
repo].  Cite each claim inline. Output as Markdown. Keep to 1 page
when rendered.
```

**Save in** `apps/anthropic-ipo-brief.md`. Update when the public S-1 lands. **Every lab-adjacent interview between now and Thanksgiving will test some version of this** — see [`05` §3](./05-career-and-startup.md#3-this-week-plan) for the explicit interview-prep plan.

---

[← back: new emerging](./02-new-emerging.md) · [next: research progress →](./04-research-progress.md)
