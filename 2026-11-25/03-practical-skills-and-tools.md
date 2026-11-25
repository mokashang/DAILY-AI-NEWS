# Practical Skills & Tools — 2026-11-25

Three operational shifts worth your afternoon: **Claude Code's auto-mode-default (v2.1.319)** rewires how `.claude/settings.json` should be structured; **v2.1.327's short-notes subagent progress** is a meaningful per-run token-cost reduction you want in every long-running harness; and **MCP formalized its release cadence** on Nov 11, which means **the current 2026-07-28 stateless spec is stable enough to publish production servers against for the first time**.

Tags: `#claude-code #mcp #settings #cost #agents`

---

## 1. Claude Code November cluster: auto-mode-default, blocking hooks, short-notes subagents, fast-mode Opus 4.8 sunset Nov 30 {#1-claude-code-nov-cluster}

**v2.1.317 (Nov 2):**
- Cost reports for gateway admins.
- **Agent SDK hooks can now block on failure** — your `PreToolUse` / `PostToolUse` / `SubagentStop` hooks can finally `exit 2` and the orchestrator respects it.

**v2.1.319 (Nov 6) — the big one:**
- **Auto mode is now the default.** Actions the server can't check get **prompted or denied**, not judged by the built-in classifier.
- **MCP task support in the terminal** — you can now hand off a task to an MCP-defined tool natively.
- **Setting:** denies instead of prompting. Useful for CI-style unattended runs.

**v2.1.326:**
- **Code Mode now works with agent teams.**
- **Startup warnings catch malformed tool rules** (saves you from debugging silent mis-configs).

**v2.1.327 (Nov 17):**
- **Subagent progress summaries on Bedrock / Vertex / Foundry now use short notes instead of full conversation transcripts.** Per-subagent-handoff token cost drops materially.

**Fast mode:**
- Added on Vertex in global / US / EU regions, with fallback to standard speed.
- **Fast mode on Opus 4.8 sunsets Nov 30, 2026.** After that, requests return an error rather than falling back. **If you're on a 4.8-pinned pipeline, you have 5 days.**

**Sources:**
- [Claude Code official changelog (code.claude.com)](https://code.claude.com/docs/en/changelog) `[primary]`
- [ClaudeKit — v2.1.319 (Nov 6) auto-mode default](https://claudekit.io/en/updates/claude-code-2-1-319/) `[aggregator]`
- [ClaudeKit — v2.1.327 (Nov 17) subagent short-note progress](https://claudekit.io/en/updates/claude-code-2-1-327/) `[aggregator]`
- [Havoptic — v2.1.326 Code Mode + agent teams](https://www.havoptic.com/r/claude-code-2.1.326) `[aggregator]`

### Why it matters to you

- **Job lens:** **Interviewers will start asking for an auto-mode-default `.claude/settings.json`**. Have a one-liner answer: *"I default to auto-safe, allowlist concrete Bash patterns per-project, and block on failed tests via SubagentStop."* Show the file in your GitHub.
- **Startup lens:** If your product embeds Claude Code or the Agent SDK, **port the short-notes subagent summary pattern** — it's a direct infrastructure cost reduction for multi-step agents without any accuracy tradeoff.
- **Insight:** **The direction of the harness is converging: safety-by-default → cost-aware-by-default.** Next quarter's expected shifts are **structured-output-by-default** (JSON Schema validation inline) and **eval-gated deploys-by-default** (auto-run the project's eval harness on `pr merge`). Stay ahead of both.

### 10-minute ritual to run today

```bash
# verify your installed version
claude --version

# upgrade if needed
claude update

# audit your project settings
cat .claude/settings.json

# look for: permissionMode (should be "auto" or "auto-safe"),
# allow / deny lists for Bash, SubagentStop hooks
```

If `permissionMode` is unset or `yolo`, switch to `auto` and add explicit Bash allowlists per-project. See the `/update-config` skill if it's in your session.

→ Cross-link: [`01` §4 — Anthropic silent-shipping via release notes](./01-big-lab-moves.md#4-anthropic-silence)

---

## 2. MCP's "More Predictable Release Cycle" post (Nov 11) — what it means for you {#2-mcp-release-cycle}

**What the MCP steering group published on Nov 11, 2026:**
- A **hard freeze one month before each release**. Only **critical security fixes** and **release-blocking correctness / interoperability defects** can merge during the freeze.
- Signal: **the project is treating MCP as production infrastructure now**, not an experimental protocol.

**Current status:**
- Latest spec remains **2026-07-28 (stateless core)**. No new spec has shipped since.
- Next spec release date is announced-but-undated. Expect **~30 days from official preview** per the new cadence.

**Sources:**
- [MCP Blog — New release cadence post index](https://blog.modelcontextprotocol.io/posts/index.xml) `[primary]`
- [MCP Changelog — 2026-07-28 release notes](https://modelcontextprotocol.io/specification/2026-07-28/changelog) `[primary]`
- [Claude.com — Bringing MCP 2026-07-28 to Claude](https://claude.com/blog/bringing-mcp-2026-07-28-to-claude) `[primary]`

### Why it matters to you

- **Job lens:** **An MCP server you built against 2026-07-28 stateless won't need breaking-change rewrites for the rest of 2026 and likely well into 2027.** Safe to publish, safe to put in your résumé, safe to demo in interviews.
- **Startup lens:** Any product's **MCP surface** is now **the industry-standard way to expose tool capabilities to agents**. If you're building an agent product, **ship MCP server access as a first-class feature** alongside your API — hiring managers and VCs both check for it.
- **Insight:** **The absence of breaking changes since July is the signal**. Standards that stabilize get adopted; standards that churn get abandoned. MCP has crossed the "safe to invest in" threshold.

→ Cross-link: [`03` §3 — weekend MCP artifact](#3-mcp-weekend-artifact)

---

## 3. Weekend artifact: public MCP server with 5-case eval, README, demo clip, auto-mode-default settings {#3-mcp-weekend-artifact}

**The single highest-leverage weekend you can run this week.** Shipped on a four-day Thanksgiving weekend, this artifact becomes the #1 thing recruiters open when they check your GitHub.

### Build spec

1. **Pick one tool surface worth automating.** Must be: (a) publicly accessible, (b) non-trivial input shape, (c) represents a repetitive workflow you've actually done. Good picks:
   - **GitHub repo stats** for a user (commits/PRs/stars, filterable by date).
   - **arXiv search + abstract fetch** scoped to a category and keyword set.
   - **MBTA/BART/MTA transit arrivals** for a saved station set.
   - **Notion / Linear / Jira / Google Calendar** read-only summary for the past 7 days.
2. **Author with FastMCP + the 2026-07-28 spec.** 3–5 tools maximum. Resist feature creep.
3. **Write a 5-case eval.** One line per case: input → expected behavior. **No model-grading. Just assertions in Python.**
4. **README.md.** Must include: (a) `pipx install .` + Claude-Desktop install instructions, (b) screenshot + 30s demo clip, (c) **the eval results** with pass/fail.
5. **`.claude/settings.json`** in the repo root with `permissionMode: auto-safe` and the Bash allowlists you'd actually run.
6. **Push to `github.com/<your-handle>/<server-name>-mcp`.** Add topic tag `mcp-server`.
7. **Post the link**: Simon Willison's LLM-related tag, `r/LocalLLaMA`, HN Show HN, LinkedIn with a one-paragraph explainer.

### Why it clears every FDE/Solutions screen

- Signals: **you ship end-to-end**, you write evals, you care about security defaults, you follow primary-source protocol releases.
- Reproducible: your reader can install and run in <5 minutes.
- Specific: a published link beats any résumé line.

### Target completion time

**Fri PM start → Sun PM ship.** If you blow past Sunday night, your scope was too big. Cut tools from 5 → 3 and ship.

→ Cross-link: [`05` §1 — portfolio artifact priorities for FDE/Solutions apps](./05-career-and-startup.md#1-fde-new-grad-window)

---

## 4. Source-tiering as a hireable instinct {#4-source-tiering}

**Why this section exists this week:** today's edition cites a rumored GPT-6.2 launch from a single blog ([`01` §5](./01-big-lab-moves.md#5-openai-rumor)). The right response is **tag it `[rumor]` and move on**, not write around it.

### The four-tier mental model

| Tier | What it is | Example | When you cite it |
|---|---|---|---|
| `[primary]` | First-party announcement | openai.com/news, anthropic.com/news, arxiv.org PDF | Default. Always try this first. |
| `[secondary]` | Reputable journalism with named sources | Bloomberg, Reuters, WSJ, The Information, TechCrunch (when the reporter has sources) | When primary is gated (quiet period) or when you need context. |
| `[analysis]` | Named-analyst writeup | SemiAnalysis, Stratechery, Sacra, Interconnects | When you want framing, not facts. |
| `[aggregator]` | Curated digest | TLDR AI, The Rundown, Ramp AI Index, release trackers | Use for speed, verify before quoting. |
| `[rumor]` | Single-source, unconfirmed | One blog, one X thread, one leaked screenshot | **Note-only. Never cite in an interview or cover letter.** |

### The two-minute rule for anything you want to share

1. **Does the source have a name + a working link?** No → `[rumor]`.
2. **Can you reach a primary source in ≤ 2 clicks?** No → `[rumor]` or `[aggregator]`.
3. **If the claim is wrong, can you tell in 30 seconds by reading one paragraph of the primary?** No → **don't share**.

### Why this reads as hireable

**Every FDE, Solutions, and MLE job is partially about filtering noise.** When you walk into an interview quoting a single-source rumor as fact, you are giving the signal that you can't tell signal from noise in a real customer meeting. When you walk in saying *"there's an unverified report that X — I'm tracking it against openai.com/news for confirmation"*, you give the opposite signal.

### Build this into your workflow

- Tag every entry in your `WATCHLIST.md` with one of the five tiers.
- When something moves from `[rumor]` to `[primary]`, log the delta.
- Every quarter, read back your tier-shift log. **This is literally the skill FDE interviews test.**

→ Cross-link: [`04` §5 — primary-source reading as a career habit](./04-research-progress.md#5-primary-source-habit)

---

## Lens roll-up for Practical Skills & Tools

- **Job:** Auto-mode-default `.claude/settings.json` + a published MCP server with evals + the source-tiering habit = **three compounding signals every FDE/Solutions screen tests for**. Build all three this week.
- **Startup:** Short-notes subagent pattern is a drop-in cost cut for any Agent-SDK-embedded product. Ship an MCP surface for your tool today — it's now the standard.
- **Insight:** **The direction of the stack: safety-by-default + cost-aware-by-default + standards-stable.** The 2027 playbook will add structured-output-by-default and eval-gated deploys. Stay one quarter ahead.
