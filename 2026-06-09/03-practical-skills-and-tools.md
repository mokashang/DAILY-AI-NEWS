# Practical Skills & Tools — 2026-06-09

Hands-on workflows. Act on this tonight.

---

## 1. Install the AWS MCP Server + lock your Claude Code MCP set to 4–6 <a id="1-aws-mcp-setup"></a>

**What you're doing.** Wiring Claude Code (or Cursor / Codex) to the **just-released AWS MCP Server (GA today — [`02` §1](./02-new-emerging.md#1-aws-mcp-ga))** so a single Claude conversation can read CloudWatch metrics, query S3, inspect Lambda config, etc., with **IAM-scoped agent permissions** that are *separate* from your own IAM user.

**Why now.** Three converging signals:

1. **AWS MCP Server is GA today** ([primary] [AWS blog](https://aws.amazon.com/blogs/aws/the-aws-mcp-server-is-now-generally-available/)).
2. The Anthropic best-practices doc updated this quarter explicitly recommends **picking 4–6 MCP servers, not all available options** — Cursor's 40-tool ceiling fills faster than people expect ([primary] [Claude Code best practices](https://code.claude.com/docs/en/best-practices) · [analysis] [community summary](https://mcp.directory/blog/claude-code-best-practices)).
3. **Agent SDK metering goes live Sunday Jun 15 (T-6)** ([2026-05-16](../2026-05-16/01-big-lab-moves.md)) — programmatic Claude calls now bill at API list rates. **Cost-aware MCP setup is no longer optional.** Pair with the [Opus-4.8 orchestrator + Sonnet-4.6 worker baseline from 2026-06-08/03 §1](../2026-06-08/03-practical-skills-and-tools.md#1-opus-48-baseline).

**The 15-minute install (verify against the AWS doc — paths and flags may differ from this sketch).**

```bash
# 1. Install the AWS MCP Server plugin for Claude Code
claude mcp add aws --transport http --url https://mcp.aws.amazon.com/<your-region>

# 2. Create a dedicated IAM role for the agent (read-only by default)
aws iam create-role --role-name claude-agent-readonly \
  --assume-role-policy-document file://trust-policy.json
aws iam attach-role-policy --role-name claude-agent-readonly \
  --policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess

# 3. Verify Claude Code only got read scopes
claude mcp call aws describe-permissions

# 4. Send the first request and verify CloudWatch logged it as 'mcp-server-call'
claude "summarize the last 24h of CloudWatch errors in production"
```

**Your 4–6 MCP set** (tune to your stack — this assumes the CS-grad + AI-engineer profile from [`ME.md`](../ME.md)):

| Slot | Server | Why |
|---|---|---|
| 1 | **AWS MCP** (just installed) | Multi-cloud-ops + portfolio evidence |
| 2 | **GitHub MCP** | PRs, issues, CI — agentic engineering bread-and-butter |
| 3 | **Playwright MCP** | Autonomous UI verification (see §2) |
| 4 | **Postgres / Supabase MCP** | Any data-touching project will need this |
| 5 (optional) | **Slack MCP** | If you're doing customer-discovery DMs at volume |
| 6 (optional) | **Notion / Linear MCP** | Project management — only if you actually use one |

**Avoid:** every random MCP server from `awesome-mcp-servers`. The 40-tool Cursor ceiling is real; Claude Code's effective tool-use degrades as tool count rises ([primary] [Anthropic best practices](https://code.claude.com/docs/en/best-practices)).

**Portfolio artifact.** When done, write a **300-word LinkedIn post**: *"Wired Claude Code to AWS the day MCP Server went GA — IAM-scoped agent permissions + CloudWatch tracing. Why it matters: enterprise agent ops needs human-vs-agent permission separation, which is now a native AWS primitive."* Pairs with the Partner-Network FDE application ([`05` §1](./05-career-and-startup.md#1-partner-network)) and ratifies the **Tuesday-morning post** that yesterday's `00-tldr` already queued ([2026-06-08/00](../2026-06-08/00-tldr.md)).

### Why it matters to you

- **Job:** Interview-ready sentence in 15 minutes. See above.
- **Startup:** Validates demand for **MCP-server-as-managed-service for non-AWS estates** ([`02` §1](./02-new-emerging.md#1-aws-mcp-ga) wedge).
- **Insight:** Token-cost-per-tool now matters more than tool-availability — fewer, better-scoped tools beat more, less-scoped ones. The opposite intuition of 2024.

→ Cross-link: [2026-06-08/03 §1 — Opus 4.8 orchestrator + Sonnet worker cost baseline](../2026-06-08/03-practical-skills-and-tools.md#1-opus-48-baseline) · [2026-05-22/03 §1 — agent-team cost lever](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [2026-05-18/03 — Agent SDK manual toggle](../2026-05-18/03-practical-skills-and-tools.md).

`#aws #mcp #claude-code #install`

---

## 2. Apple Intelligence Extensions — pre-stage your dev environment today <a id="2-extensions-prestage"></a>

**What you're doing.** Apple shipped the **Apple Intelligence Extensions framework** at WWDC yesterday ([`01` §1](./01-big-lab-moves.md#1-wwdc-graded)) — but the developer SDK access date is **not yet on stage**. Pre-stage tonight so when the SDK opens (likely within 10 days), you can ship the first 100-LOC Extensions demo before the saturation curve.

**The 10-minute pre-stage.**

```bash
# 1. Update Xcode to the WWDC beta
xcodes install --latest

# 2. Bookmark the App Intents + Apple Intelligence Extensions docs
# (the URLs land 24-48 hours after the keynote — check developer.apple.com)
open https://developer.apple.com/wwdc26/

# 3. Sketch your "first Extension" — keep it small, sharp, one verb
#   Example: "PriceCheck" intent — Siri asks Claude/Gemini/ChatGPT
#   for current product price + posts to Reminders
```

**Suggested first Extensions to build** (pick ONE — ship it in a weekend when the SDK opens):

| Vertical | Verb | Why it's good for portfolio |
|---|---|---|
| **Focus** | "summarize my unread Slack into 3 priorities" | Hits the FDE-shaped "real productivity" story |
| **Calendar** | "find the next 30-min slot the four of us all have free" | Hits multi-step reasoning + multi-source data |
| **Notes** | "extract the action items from this meeting note" | Demonstrates intent + entity extraction |
| **Accessibility** | "describe what's on screen in 2 sentences" | High social signal; Apple promotes these |

**Track these threads after WWDC:**

- **Anthropic Extensions confirmation** — likely [Anthropic news](https://www.anthropic.com/news) post within 48 hours.
- **OpenAI Extensions confirmation** — likely [OpenAI news](https://openai.com/news/) post within 48 hours.
- **Revenue-share %** — likely buried in the iOS 27 dev guide ~10 days out; this is the gate on Extensions-native startup viability.

### Why it matters to you

- **Job:** Pre-staging beats reacting. When the SDK opens, you ship a demo + LinkedIn post in 48 hours, not 2 weeks. That's the difference between "early on Apple Intelligence Extensions" and "another Extensions developer."
- **Startup:** The 6-month window opens with SDK release. Don't commit to a vertical until you know the revenue-share %.
- **Insight:** The Extensions intent grammar is **MCP-shaped** — see [`01` §1](./01-big-lab-moves.md#1-wwdc-graded) and [`02` §1](./02-new-emerging.md#1-aws-mcp-ga). Skill transfer from your AWS MCP install is partial-to-substantial.

`#apple #extensions #pre-stage #portfolio`

---

## 3. Daily routine — what to do this week to not drop threads <a id="3-routine"></a>

Minimal sustainable cadence so the May 23 → June 9 gap doesn't happen again.

| Cadence | What | Where |
|---|---|---|
| **Daily (5 min)** | Skim [llm-stats.com/llm-updates](https://llm-stats.com/llm-updates), [Anthropic news](https://www.anthropic.com/news), [OpenAI news](https://openai.com/news/), [Google DeepMind blog](https://deepmind.google/discover/blog/), [The Rundown](https://www.therundown.ai/) | Browser bookmarks bar; AM coffee |
| **Daily (10 min)** | Glance at [arXiv cs.AI new](https://arxiv.org/list/cs.AI/new) + [HF Papers Trending](https://huggingface.co/papers/trending) | Save anything interesting for weekend deep-read |
| **Tue + Sun (20 min)** | Update [WATCHLIST.md](../WATCHLIST.md) + [ACTIONS.md](../ACTIONS.md) | Repo root |
| **Weekly (60 min)** | Ship one artifact (per [ME.md "one artifact every weekend" rule](../ME.md)) | Weekend |
| **Monthly (15 min)** | Re-read [SOURCES.md](../SOURCES.md); add/remove sources as quality shifts | First Sunday |

**Three sources to add to [`SOURCES.md`](../SOURCES.md) today** (filed under Tier 3 — Specialized AI News Platforms):

- **[llm-stats.com/llm-updates](https://llm-stats.com/llm-updates)** — daily model-release tracker
- **[artificialanalysis.ai](https://artificialanalysis.ai/)** — Intelligence Index (now cited in mainstream coverage; canonical model-ranking source for 2026)
- **[lmcouncil.ai/benchmarks](https://lmcouncil.ai/benchmarks)** — independent benchmark aggregation; cross-reference for Artificial Analysis claims

`#routine #sources #habit`

---

## Cross-links

- AWS MCP install ([§1](#1-aws-mcp-setup)) pairs with the Partner-Network FDE application ([`05` §1](./05-career-and-startup.md#1-partner-network)).
- Apple Extensions pre-stage ([§2](#2-extensions-prestage)) pairs with the Tuesday-morning WWDC scorecard post queued from yesterday ([2026-06-08/03 §3](../2026-06-08/03-practical-skills-and-tools.md#3-wwdc-discipline)).
- Daily routine ([§3](#3-routine)) pairs with [ME.md "Personal rules"](../ME.md).
