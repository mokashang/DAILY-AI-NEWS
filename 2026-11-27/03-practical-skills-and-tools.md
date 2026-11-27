# Practical Skills & Tools — 2026-11-27

Three Claude Code shipping events, one reported Rust rewrite, one new category of multi-model routing work — and a long weekend to actually try one of them. The practice-level answer this fortnight: **ship one portfolio artifact that routes across all three labs**, because that is the single skill the multi-cloud / public-lab era just made the most hireable.

Tags: `#claude-code #mcp #tooling #rust #multi-model #skills`

---

## 1. Claude Code cadence — v2.1.317 → v2.1.327 in 15 days {#1-claude-code-cadence}

**What shipped (Nov 2 → Nov 17, 2026):**

### v2.1.317 (Nov 2) — cost reporting + blocking hooks
- **Cost reports for gateway admins.** If you're running the Claude gateway for a team, you can see per-user, per-session, per-model spend without exporting to BigQuery/Datadog first. The anchor metric for showing "we justified the AI line item" in a budget review.
- **Agent SDK hooks that can block on failure.** A hook returning an error now stops the agent turn instead of logging and continuing. The missing primitive for enforcing guardrails / HITL gates.
- Long list of fixes.

### v2.1.326 (Nov 16) — Code Mode + agent teams coexist
- **Code Mode on simultaneously with agent teams enabled.** Previously an either/or. Now you can run a `/plan`-style team of subagents while staying in Code Mode's deterministic tool surface.
- **`/status` row explaining why features are off.** Diagnostic surface — no more "why isn't my MCP server showing up?" grep-hunting.
- **Remote Control replies stream to phones or browsers as they're written.** Latency win for mobile users; also enables "watch my agent think" demos from a meeting room.

### v2.1.327 (Nov 17) — Bash + Windows speedups
- **First Bash command in a session is faster.** Shell start-up files run before approval, so the approval dialog doesn't block zsh/bash init.
- **Windows start-up and PowerShell tool got faster.** Specific Windows-native path optimizations.

**Sources:**
- [Claude Code changelog](https://code.claude.com/docs/en/changelog) `[primary]`
- [claudekit — Claude Code 2.1.327](https://claudekit.io/en/updates/claude-code-2-1-327/) `[aggregator]`
- [claudekit — Claude Code 2.1.326](https://claudekit.io/en/updates/claude-code-2-1-326/) `[aggregator]`
- [havoptic — Claude Code November 2026 Releases](https://www.havoptic.com/releases/claude-code/2026/11) `[aggregator]`
- [Claude World — November 2026 what's new](https://claude-world.com/zh-tw/articles/claude-code-november-2026-whats-new/) `[aggregator]`

### Try this weekend
- **Enable the gateway cost report once you have 3 teammates using Claude Code** — it's the cheapest "I am a cost-aware MLE" résumé line you can earn.
- **Write one blocking Agent SDK hook** (e.g., block a `write_file` that would overwrite a tracked file). Ship it as a `.claude/hooks/` sample repo.
- **Run Code Mode + agent teams on the same project** to feel which of the two drives velocity for *your* codebase. Report the finding on Hacker News or your personal blog.

---

## 2. MCP servers — the FDE application artifact that still clears the bar {#2-mcp-servers}

**What's new (ongoing, no fortnight-specific release):**
- MCP **2026-07-28 stateless spec** + **FastMCP** (noted in 2026-11-14 edition) still define the shortest path from "idea" to "running production-grade MCP server."
- New pattern this fortnight: **MCP servers as shared-team primitives** — three Anthropic FDE job reqs posted in November list "ship a prod MCP server end-to-end" as explicit resume criteria.
- MCP servers also serve as **the single best test of Claude Code 2.1.317's blocking-hooks pattern**: build an MCP server that wraps a destructive action (SQL DROP, git force-push, file rm) and gate it on a blocking hook.

### Try this weekend
- **Pick one real workflow you do weekly** — gmail triage, calendar prep, invoice reconciliation, interview prep — and wrap it in an MCP server with 3 tools. Publish to GitHub with a README, a 90-second demo gif, and a 5-case eval table. **This is the single highest-ROI portfolio artifact you can ship in a weekend.**
- Pair it with a short blog post: "Why I built this, what it taught me about MCP's trust boundary." Links from 3 of those posts landed 2026 FDE hires per LinkedIn self-reports.

---

## 3. "Tests-as-spec" — the vibe-coding pattern that ships {#3-tests-as-spec}

**What's new:**
- The 2026-11-14 edition introduced the pattern. In the 13 days since, it has *actually* been published in a couple of practitioner blogs as **"human writes a failing test, agent iterates, CI gates on red."** Pattern:
  1. Human writes `test_X.py` describing the desired behavior (what, not how).
  2. Agent writes the implementation.
  3. CI blocks merge if either the test or the implementation changes without the other.
  4. Human reviews the *test*, not the code.
- Combines well with Claude Code 2.1.317's **blocking Agent SDK hooks** — the hook enforces the "don't change the test without a human" rule.

### Try this weekend
- Take one function you've been meaning to clean up. **Write the test you wish existed. Delete the function. Let the agent write it back.** See whether the test survives unchanged. If yes, you have the pattern working.

---

## 4. Anthropic reportedly rewrote the Messages API in Rust with Claude agents — treat as unconfirmed but study the pattern {#4-rust-rewrite}

**What happened (per aggregator, not Anthropic directly):**
- **aiweekly.co's Nov 27 roll-up reports Anthropic rewrote its Messages API from Python to Rust with Claude agents**, citing **~70% lower CPU and >80% lower memory** vs. the Python stack.
- The underlying post was **not** officially announced by Anthropic (I could not find it on their blog or Anthropic's engineering writeups as of today). **Treat the number as directional until an engineering blog post appears.**

**Sources:**
- [aiweekly.co — AI News Today, Nov 27 (aggregator roll-up)](https://aiweekly.co/ai-news-today) `[aggregator]`

### Why the pattern matters anyway (even if the numbers are off)

- **The "AI writes its own infra" story is real.** Whether or not the 70/80% number holds, 2026 is the first year where large companies routinely use coding agents on *hot-path production code*. The craft question is: **what's the harness that makes the agent productive on a Rust hot path?**
- **The practice:** fence the agent inside `cargo check` + `miri` + proptest / `fuzzcheck` + a performance regression test. Those four tools are what turn "the agent wrote Rust" into "the agent wrote Rust that passes clippy, UB-checks, property tests, and perf tests." Ship *that* harness as a GitHub template.

### Try this weekend
- **Take one Python function with a hot loop** (CSV parse, JSON flatten, image resize). **Ask Claude Code to Rust-port it with a `PyO3` wrapper.** Keep the Python interface identical; run `pytest` before and after; report CPU + memory delta. Publish as a blog post titled "What I learned porting [X] to Rust with Claude Code."
- If the agent gets stuck: that is also a publishable finding. **Documenting agent failure modes is a hireable skill at every lab's Applied team.**

---

## 5. The multi-model router — the weekend artifact of the week {#5-multi-model-router}

**Why now:**
- **OpenAI → Google Cloud Model Garden** (Oct 21, private preview — see [`01` §2](./01-big-lab-moves.md#2-openai-gcp)).
- **Anthropic ANT trading live** + Fable 5.2 API stable + Mythos 5.2 for deep reasoning.
- **Gemini 4 reachable** via DeepMind Antigravity + Google API.
- All three labs, all three clouds — simultaneously accessible for the first time this week.

### Blueprint — ship it this weekend
```
mmr/                              # multi-model router
├── Readme.md
├── router.py                     # choose model by task class + budget
├── providers/
│   ├── anthropic_claude.py       # Claude Fable 5.2 + Mythos 5.2
│   ├── openai_gpt.py             # GPT-6 Astra / Sol / Luna via direct OR GCP MG
│   └── google_gemini.py          # Gemini 4 early-release via Vertex
├── eval/
│   ├── tasks.yaml                # 5 task classes: code, math, extraction, sum, chat
│   └── bench.py                  # run each task across each provider
├── cli/
│   └── route                     # `route --task code "fix this test"`
└── docs/
    └── comparison-table.md       # the deliverable
```

**Scope discipline:**
- 5 task classes, not 20.
- 1 real benchmark per class (e.g., HumanEval-100, MATH-20, DROP-10, XSum-10, MT-Bench subset).
- Publish the comparison table + which provider won on cost × accuracy.

**Why this artifact beats the MCP server for *this particular* job search:**
- The MCP server proves **you can ship a Claude-native primitive**.
- The multi-model router proves **you can be lab-agnostic**, which is exactly what an FDE / Solutions Engineer / AI Integration Engineer does on Day 1 at any lab.
- With the ANT IPO + OpenAI-on-GCP + Gemini-4 all landing in Nov 2026, this artifact is also *topical* — recruiters will read the README because it's current.

### Reading
- [Simon Willison's llm](https://llm.datasette.io/) — reference implementation; `llm` 0.37 adds reasoning traces + server-side tools, worth reading before you write your own router.
- [OpenAI — OpenAI models on Google Cloud (announcement)](https://openai.com/index/openai-models-google-cloud/) `[primary]`
- [Google Cloud — Model Garden](https://cloud.google.com/model-garden) `[primary]`
- [Anthropic — Claude for Developers](https://www.anthropic.com/claude/developers) `[primary]`

---

## 6. Codex on Google Cloud — practical implications for GCP developers {#6-codex-on-gcp}

**What's practical today:**
- Codex **CLI and Desktop** can now target Gemini-platform inference via Google Cloud (private preview).
- For a developer already on GCP: the net-new primitive is **one toolchain, two models** — Codex-style agent UX against Gemini backends.
- Pricing / GA timing not disclosed.

### Try this weekend
- **If you have GCP credits:** request private-preview access to OpenAI in Model Garden. Even if denied this round, you're on the waitlist for the next tier.
- **If you don't:** ship the multi-model router (§5) with a provider stub that will slot in when GA happens. "Future-ready" code is a recruiter-impressing property.

---

## 7. The Black Friday builder's checklist

This long weekend — Thanksgiving (Thu Nov 26) + Black Friday (Fri Nov 27) + Weekend — is the single longest uninterrupted block before year-end. **Pick ONE and ship it before Sunday night:**

- [ ] **Multi-model router** (§5) — highest leverage for this quarter's job market
- [ ] **MCP server** (§2) — highest leverage for Anthropic FDE applications specifically
- [ ] **Rust-port a hot-loop function** (§4) — highest leverage for infra / performance roles
- [ ] **Blocking Agent SDK hook sample** (§1) — highest leverage for "safety eng" / RL-eng roles
- [ ] **"Tests-as-spec" working example on a real repo** (§3) — highest leverage for showing craft

The failure mode is starting all five and shipping none. **One shipped artifact with a README and a demo beats five half-finished branches.**

---

## Running toolchain status

| Tool | Version | Notable change this fortnight | Source |
|---|---|---|---|
| Claude Code | **2.1.327** (Nov 17) | Blocking hooks, Code Mode + teams, Bash + Windows speedups | [Changelog](https://code.claude.com/docs/en/changelog) |
| `llm` (Simon Willison) | 0.37 | Reasoning traces + server-side tools (noted in 11-14) | [simonwillison.net](https://simonwillison.net/) |
| MCP | 2026-07-28 stateless | stable | [MCP spec](https://modelcontextprotocol.io/) |
| FastMCP | current | stable | [FastMCP](https://github.com/jlowin/fastmcp) |
| LangChain | 1.4.9 | HITL interrupt middleware (noted in 11-14) | [LangChain](https://python.langchain.com/) |
| Codex (OpenAI) | — | CLI + Desktop now target Gemini backend via GCP private preview | [OpenAI](https://openai.com/index/openai-models-google-cloud/) |
| Antigravity (Google) | — | Gemini 4 internal testing platform; dev access pending | [DeepMind](https://deepmind.google/) |
