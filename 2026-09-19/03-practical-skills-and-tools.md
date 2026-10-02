# Practical Skills & Tools — 2026-09-19

Three actions this weekend. **All three shorter than 3 hours; all three produce a public artifact.** Theme: **your Sept-10 router artifact just got a fourth column (DeepSeek V4.1-Flash), Anthropic just industrialized the Skills refactor with Smart Reports, and Claude Code shipped a set of small-but-material updates that change how you organize a repo tonight.**

Tags: `#claude #claude-code #skills #hooks #router #deepseek #evals #cost #mcp`

---

## 1. Anthropic Smart Reports for Enterprise (beta) — the tool that industrializes the Skills refactor {#1-smart-reports}

**What happened:** Anthropic launched **Smart Reports** in beta for Enterprise (Sept). Automatically analyzes team Claude usage and surfaces:

- Which work is getting done, at what cost, at what latency.
- Where sessions run into friction (multiple retries, tool failures, escalations).
- **"Which repeated patterns are worth packaging as shared Skills."**

The bolded line is the important one. The [2026-09-10 §2 Claude Code decision tree](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree) told you *what* the four primitives are and *how* to sort your rules; Smart Reports tells you *which* rules in your current codebase / prompt library are actually worth converting. It's the missing productivity tool for the primitive refactor.

### How to use it if you have Enterprise access (30 min tonight)

1. Enable Smart Reports in Claude Enterprise settings.
2. Run it against your team's last 7 days of Claude usage.
3. Take the top 3 "repeated pattern" recommendations. For each: (a) is it enforcement → Hook; (b) is it contextual knowledge → Skill; (c) is it delegation → Subagent; (d) is it always-on → CLAUDE.md. Refactor the top 3, ship.
4. Screenshot the "before/after" cost + friction delta — this is a **portfolio artifact** for interviews.

### What to do if you don't have Enterprise access

Build the **poor-person's version** locally: (a) log every Claude Code session's tool-calls + latencies + retries to a local SQLite; (b) run a weekly Claude Code script that reads the log and asks "which patterns repeat 3+ times, which fail 2+ times, and what Skill would consolidate them?"; (c) publish the script as a GitHub gist. This is a **10-line prompt in a 30-line wrapper** — perfect Saturday project.

### Sources

- [Anthropic — Claude Platform release notes overview](https://platform.claude.com/docs/en/release-notes/overview) `[primary]`
- [Releasebot — Anthropic Release Notes September 2026](https://releasebot.io/updates/anthropic) `[aggregator]`
- [Suprmind — Claude Features 2026: Projects, Artifacts, Memory, Computer Use, Skills, MCP](https://suprmind.ai/hub/claude/features/) `[analysis]`

---

## 2. Add DeepSeek V4.1-Flash to your model router — the 15-minute upgrade {#2-deepseek-router}

**What happened:** DeepSeek V4.1-Flash ([`02` §1](./02-new-emerging.md#1-deepseek-v41-flash)) makes your Sept-10 model router a **four-provider artifact** instead of three. The upgrade takes 15 minutes and turns the same GitHub repo into a more interview-defensible artifact than 90% of your peers will have by Monday.

### The upgrade (concrete steps)

1. **Pull the DeepSeek python SDK:** `pip install openai` (DeepSeek exposes an OpenAI-compatible endpoint at `https://api.deepseek.com`).
2. **Add a fourth row to your router config table:**
   ```
   "cheap_open" → { "provider": "deepseek", "model": "deepseek-flash", "endpoint": "https://api.deepseek.com/v1", "cost_in_per_1M": 0.14, "cost_out_per_1M": 0.28 }
   ```
   (Cost numbers are approximate — verify against the DeepSeek pricing page the day you ship; they change often.)
3. **Route by task type:** existing routes (`coding` → Fable 5.1, `long_context_qa` → Fable 5.1 cached, `agentic` → Fable 5.1), and add `cheap_bulk_summary` → `cheap_open` (DeepSeek). If your task is high-volume summarization, translation, classification, or first-pass extraction, the open-weight route often wins on cost by 4–8×.
4. **Add a 6th eval case** to the 5-case suite ([2026-09-10 §3](../2026-09-10/04-research-progress.md#3-eval-suite-template)): **"multilingual long-summary at scale"** — this is DeepSeek's strongest suit and lets the leaderboard tell the honest story.
5. **Publish the leaderboard delta.** Update the README with a "Sept 19 additions" note that says: "*V4.1-Flash added; new cheapest option on cases 1, 5, 6 — quality parity with GPT-6 Astra on case 6.*"

### Why this matters (as a candidate)

The **interview quote** for the next 8 weeks is: "*model-fluency is worthless when four labs ship per week — I built the layer that stays honest by measurement.*" Adding an open-weight route to your router is the concrete artifact that lets you defend the quote. Combined with the smart-reports refactor above, the two published repos are the *complete evidence pack* for FDE / AI Engineer / Solutions interviews at Anthropic, OpenAI, Sierra, Decagon, PwC AI Engineering, and every well-funded startup on the [160+ list](https://vinitshahdeo.substack.com/p/ai-startups-hiring-engineers-2026).

### Sources

- [SiliconANGLE — DeepSeek releases V4.1-Flash](https://siliconangle.com/2026/09/10/deepseek-releases-v4-1-flash-says-it-outperforms-flagship-v4-pro/) `[secondary]`
- [DeepSeek API Docs — Change log](https://api-docs.deepseek.com/updates/) `[primary]`
- [Emergent.sh — DeepSeek V4.1 Flash Launches with Multimodal Capabilities](https://emergent.sh/news/deepseek-v4-1-flash-launches-multimodal) `[analysis]`

---

## 3. Claude Code September updates — what actually changes tonight's project {#3-claude-code-updates}

**What happened:** Anthropic shipped a set of Claude Code updates in Sept 2026. The material ones for a working project **tonight** (not the flashy-but-niche ones):

| Update | What it changes for you | Priority |
|---|---|---|
| **Managed MCP servers** | Anthropic hosts common MCP servers (GitHub, Linear, Notion, filesystem) — you stop maintaining half your MCP inventory | **HIGH** |
| **Unattended headless permission controls** | You can now run `claude -p` in CI without permission prompts blocking; scope permissions per-run | **HIGH** |
| **`claude plugin eval` command** | Runs a plugin's eval suite; outputs scored, reproducible JSON + HTML report | **MEDIUM** |
| **`/output-style` command** | Switch output styles at runtime; useful if you're rendering into different downstream pipelines | LOW |
| **GitLab MR recognition** | Same PR flow as GitHub, now works on GitLab | LOW unless you use GitLab |
| **JSON plugin validation + faster startup + workflow views** | Ambient QoL, no code change from you | LOW |
| **Bash tool file-edit diff** | Bash-tool actions that touch files now show a diff — better auditability | MEDIUM (safety) |

### The 60-minute tonight action

1. **Migrate your top-2 MCP servers to managed.** If you're running `github-mcp` or `filesystem-mcp` locally, switch to managed. Frees a memory tab and a maintenance surface. ~15 min.
2. **Set up headless permissions on your CI project.** Use unattended-mode + explicit scoped permissions in `.claude/settings.json` (`allow: ["Bash(pytest)", "Read(*)", "Edit(src/**)"]`). Enables `claude -p` to run overnight against your test suite without blocking. ~20 min.
3. **Write a plugin eval suite for your one custom plugin.** Even 3 cases counts. Run `claude plugin eval`, save the JSON report. Publish the report as a GitHub Action badge on your README. ~25 min.

Deliverable at the end: a public repo that has managed MCP integration + a scored plugin eval report — *another portfolio artifact* to hand to a recruiter.

### Sources

- [Claude Code changelog (primary)](https://code.claude.com/docs/en/changelog) `[primary]`
- [Releasebot — Claude Code Updates September 2026](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Gradually.ai — Claude Code Changelog (September 2026)](https://www.gradually.ai/en/changelogs/claude-code/) `[aggregator]`
- [Blog.mean.ceo — Claude Code News, September 2026 (Startup Edition)](https://blog.mean.ceo/claude-code-news-september-2026/) `[aggregator]`
- [Updatify — Claude Code release notes](https://updatify.io/releases/claude-code) `[aggregator]`
- [Havoptic — Track Claude Code updates](https://www.havoptic.com/tools/claude-code) `[aggregator]`

---

## 4. Prompt-cache math is even more attractive after Fable 5.1 + DeepSeek V4.1-Flash {#4-cache-math}

**What happened:** No new news this week, but a reminder: the [Fable 5.1 cache-read cut ($1.00 → $0.25/1M)](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics) is now **compounded** by the availability of a MIT-licensed DeepSeek V4.1-Flash for the cache-miss path or for the "cheap-parallel" verification step.

**Re-quote of the ballpark cost stack (updated for this week):**

| Setup | ~ Cost / 1M input tokens (typical agent) | Change vs. baseline |
|---|---|---|
| No caching, Fable 5 | $3.00 | 0% |
| Caching, Fable 5 | $1.20 avg | –60% |
| Caching, Fable 5.1 | $0.65 avg | –78% |
| Caching, Fable 5.1 + DeepSeek route on 40% of miss traffic | ~$0.42 avg | **–86%** |

**Do this weekend:** if you already caching, wire DeepSeek in as the cache-miss fallback for the 3 cheapest task types (bulk summary, extraction, classification). ~40 minutes of routing code + eval. Update your public cost graph.

### Sources

- [Anthropic — Fable 5.1 announcement](https://www.anthropic.com/news/claude-fable-5-mythos-5) `[primary]`
- [DeepSeek API Docs — pricing / model listing](https://api-docs.deepseek.com/updates/) `[primary]`

---

## 5. This week's meta-lesson: publishing beats mastering {#5-meta-lesson}

**What happened:** three practical items above and none of them ask you to *learn* a new thing — they ask you to *ship* an addition to something you already built. That's the pattern of Q4 2026:

- The frontier changes weekly.
- Nobody masters it.
- The portable skill is **iterating on your public artifact fast enough to reflect what changed.**

That's the differentiator in every FDE / AI Engineer / Solutions interview through end-of-year. Publish 3× before Nov 1. Don't wait until an artifact is "done."
