# Practical Skills & Tools — 2026-07-24

Two-part day. **Part 1 is a hard deadline** — DeepSeek's old endpoints retire at **15:59 UTC today**, and the migration mapping is asymmetric (`deepseek-reasoner` → `v4-flash`, *not* `v4-pro`). Miss it and scheduled jobs 404. **Part 2 is three Claude Code defaults you probably haven't flipped** — all shipped in the July release cycle, all portfolio-relevant, all under 15 minutes to configure.

Tags: `#playbook #claude-code #subagents #mcp #deepseek #migration #cost`

---

## 1. ⏰ DeepSeek endpoint deprecation — 15:59 UTC TODAY (last chance) {#1-deepseek-deprecation}

**Carry from [2026-07-16/03 §4](../2026-07-16/03-practical-skills-and-tools.md#4-deepseek-deprecation) — T-0 today.**

**The move:** DeepSeek's old model endpoints go 404 at **15:59 UTC on Friday July 24** (T-0 today). Any scheduled job, cron, agent loop, or downstream service still hitting them will silently fail.

**The critical asymmetry — do NOT copy-paste your way through this:**

| Old endpoint | Correct migration target | Common wrong target |
|---|---|---|
| `deepseek-chat` | `deepseek-v4-flash` | `deepseek-v4-pro` (over-priced for chat load) |
| `deepseek-reasoner` | **`deepseek-v4-flash`** | **`deepseek-v4-pro`** ← silent capability downgrade at same billing |

**The failure mode** if you route `deepseek-reasoner` to `v4-pro`: you continue getting responses, but they're **slower + more expensive + not measurably better** on your reasoning workloads. `v4-flash` is the *correct* successor for both endpoints; `v4-pro` is a **different tier**, not an upgrade.

**5-minute audit tonight:**

```bash
# In every repo you own that touches DeepSeek:
grep -rn "deepseek-chat\|deepseek-reasoner" .

# For each hit:
# 1. Update to deepseek-v4-flash
# 2. Run the existing test suite (if any)
# 3. Commit + push
```

If you have **scheduled tasks** (Cowork, GitHub Actions cron, CI jobs) hitting DeepSeek, **audit the config file, not just the code** — many teams have hardcoded model strings in scheduler configs that grep misses.

**Sources:**
- [2026-07-16/03 §4 — DeepSeek deprecation migration guide (T-8)](../2026-07-16/03-practical-skills-and-tools.md#4-deepseek-deprecation) `[archive]`
- [2026-07-13/00 — earlier T-11 warning](../2026-07-13/00-tldr.md) `[archive]`
- [2026-07-23/00 §Watchlist — the T-1 warning](../2026-07-23/00-tldr.md) `[archive]`

### Why it matters to you

- **Job lens:** Missing this deadline is exactly the class of production hygiene that shows up in a Solutions / FDE interview post-mortem question — *"tell me about a time you had to handle a vendor migration under a hard deadline."* Doing the audit tonight and being able to say *"I caught the asymmetric mapping — `reasoner → v4-flash`, not `v4-pro`, and re-routed 4 downstream jobs"* is a real, credible war story. Not doing it and having a Monday-morning 404 spiral is the same story from the wrong side.
- **Insight:** The *asymmetric migration mapping* is a broader pattern to internalize. When a vendor deprecates a tier, the "natural" successor by name is often *not* the natural successor by capability — cost-conscious vendors like DeepSeek use deprecation as an opportunity to **push customers toward their lower-margin tier by default**. Read every deprecation notice with that lens.

---

## 2. Three Claude Code defaults to flip tonight (~15 min total) {#2-claude-code-defaults}

**What happened:** Claude Code shipped several under-appreciated changes in the **July 2026** release cycle. Three of them are defaults that most heavy users still haven't touched, all documented in the [Claude Code — What's new](https://code.claude.com/docs/en/whats-new) page and the [Releasebot Claude Code changelog](https://releasebot.io/updates/anthropic/claude-code).

### (a) Subagents run in the background by default — set a session cap first

Any subagent you spawn keeps running while you keep working — you get a notification when it completes. There's a **new per-session cap** to stop runaway delegation loops:

```bash
# in your shell profile (bash/zsh)
export CLAUDE_CODE_MAX_SUBAGENTS_PER_SESSION=50   # default is 200
```

**Why 50 not 200:** if a top-level agent runs a `while ... await agent(...)` loop and one of the agent calls silently returns null (from an API blip or a hook rejection), the loop can chew through the cap in ~10 minutes on a live network. 50 is small enough to make you notice the runaway before it bills you into a wall; you can raise it per-project if you actually need it.

**Restructure your prompts to fan out immediately.** Instead of:

```
"Read A, then read B, then read C, then summarize"
```

...write:

```
"Read A, B, and C in parallel (three subagents), then summarize when all three return"
```

This is now the default speed setting, not a "power move." Direct continuation of the `/fork` (background) vs `/subtask` (inline) split from [2026-07-17/03](../2026-07-17/03-practical-skills-and-tools.md).

### (b) MCP tool calls > 2 minutes auto-background

If an MCP tool call runs longer than **2 minutes**, Claude Code **moves it to the background automatically** so the session stays usable. Combined with **`/resume`**, which now lists past sessions (including deleted ones) and resumes any as a background session, this changes how you should structure long-running MCP calls: **don't build synchronous wait states into your prompts** — the runtime already handles them for you.

### (c) `claude mcp login` — one-command MCP auth

For any configured MCP server that uses OAuth (Slack, Linear, Notion, Google Drive, GitHub — most third-party MCP servers do), you can now authenticate from your shell instead of the interactive `/mcp` menu:

```bash
claude mcp login <server-name>     # authenticate
claude mcp logout <server-name>    # clear stored creds
```

**Why this matters for scripting:** the interactive `/mcp` menu can't be automated. `claude mcp login` can — which means you can now put MCP-auth into a project's setup script, a CI job, or a fresh-container bootstrap. It's the last blocker that made "clone repo → immediately have working MCP tools in Claude Code" impossible. This is also the unblocker for the **MCP 2026-07-28 stateless RC** migration ([2026-07-21/03 §1](../2026-07-21/03-practical-skills-and-tools.md#1-mcp-stateless)) — with `claude mcp login` scriptable, you can now include auth setup in your migration playbook rather than leaving it as a manual step.

**Bonus: Sonnet 5 is the default now**

**Claude Sonnet 5** became the **new default model for Pro, Team Standard, and Enterprise seats** as of **June 30, 2026** — top-tier coding + tool use at Sonnet pricing, a **native 1M-token context window**, and **adaptive thinking on by default**. If you're still writing project READMEs that specify "Claude 3.5 Sonnet" or "Claude Opus 4," update them tonight — recruiters skim for model names and outdated ones read as "this candidate hasn't touched Claude Code since spring." (Related audit: the tokenizer silent re-pricing story from [2026-07-20/03 §3](../2026-07-20/03-practical-skills-and-tools.md#3-tokenizer-cost) — the Opus 4.7 tokenizer inflation is still worth measuring against your last month's Claude bill this weekend.)

**Sources:**
- [Claude Code — What's new (primary)](https://code.claude.com/docs/en/whats-new) `[primary]`
- [Releasebot — Claude Code Updates by Anthropic — July 2026](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Gradually.ai — Claude Code Changelog (July 2026)](https://www.gradually.ai/en/changelogs/claude-code/) `[aggregator]`
- [MarkTechPost — Claude Code Guide 2026: 25 Features with Examples + Demo](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[analysis]`
- [Developers Digest — Claude Code Agent Teams, Subagents, and MCP: The 2026 Playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) `[analysis]`

### Why it matters to you

- **Job lens:** These three flips are the *shibboleth* — the small operational details that separate "I use Claude Code" from "I run Claude Code as a production tool." In a technical interview for an FDE / Solutions / AI Integration role, being able to answer *"what's your subagent cap and why?"* or *"how do you script MCP auth in a fresh env?"* signals depth in ~30 seconds. Set them tonight; drop them into a project README so you can point to them.
- **Startup lens:** The **`claude mcp login` addition is the unblocker for productized MCP servers**. If you were holding off on shipping an MCP server because "customers can't self-serve auth in Claude Code," that's no longer true — a customer can now `claude mcp login your-server` and be running against production creds in one command. **Ship the MCP server this weekend** — it stacks perfectly with the MCP 2026-07-28 stateless RC migration ([2026-07-21/03 §1](../2026-07-21/03-practical-skills-and-tools.md#1-mcp-stateless)) that lands in 4 days.
- **Insight:** Anthropic's *product* shipping cadence in July has been higher than the *model* shipping cadence — subagent defaults, MCP auth, long-running-call handling, memory beta, HIPAA self-serve, Sonnet 5 default, Record a Skill, Claude Security. **The company is building the deployment surface**, not just the model. Match your project priorities to what the vendor is investing in (deployment > raw prompting), and you'll be building on the parts of the platform they're most incentivized to make better.

→ Cross-link: [`01` §3 the Opus 5 no-show — same shipping-cadence signal, opposite side](./01-big-lab-moves.md#3-opus5-noshow) · [2026-07-22/03 §1 Claude Code caps](../2026-07-22/03-practical-skills-and-tools.md#1-claude-code-caps) · [2026-05-22/03 §1 Opus-orchestrator + Sonnet-worker cost lever (still current)](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost).

---

## Weekend micro-project (ship in a Saturday afternoon)

**Build a Claude Code hook that logs every subagent spawn to a local `.claude/subagent-log.jsonl`** — so you can *see* the fan-out and prove to a recruiter (or to yourself) that you're actually parallelizing. ~30 lines of hook JSON + a tiny logger. Push the repo, screenshot the log after a real project run, drop it into next week's LinkedIn writeup. This is a natural companion artifact to the [Presence-vs-Managed-Agents-vs-ADK one-pager](./05-career-and-startup.md#1-fde-catalyst) — one shows you *think* about deployment surfaces, the other shows you *operate* on them.
