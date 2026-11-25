# Practical Skills & Tools — 2026-10-08

Three operational shifts the frontier made actionable this week: (1) the agent *runtime* is now the thing you pick, not scaffold; (2) GPT-6 Sol's price cut rewrites the Claude-cache-read math; (3) the weekend artifact that re-prices your resume is now a two-runtime comparison with a public cost dashboard — not another "I built an agent" repo.

Tags: `#claude-code #openai-agents #dots #managed-agents #routing #pricing #evals #runtime`

---

## 1. The agent-runtime decision tree — pick a runtime, don't build one {#1-runtime-decision-tree}

**What changed:** Three frontier labs now ship consumable agent runtimes:

- **OpenAI Dots** — always-on; per-dot cloud computer + browser; 4,000+ app integrations via OpenAI plugins; one dot free on ChatGPT Pro / Business Premium; GPT-6 Astra backend; **enterprise/edu/healthcare = off by default**.
- **Anthropic Managed Agents / "Dreaming"** — sandboxed Linux-env agent runtime with hooks + skills + subagents + MCP tool-calling + CLAUDE.md; shipped progressively since May.
- **Google Antigravity 2.0 + Managed Agents (Gemini API) + ADK 2.0** — "one API call → sandboxed agent that reasons, uses tools, executes code"; Chrome DevTools-for-agents supports 20+ non-Google agents (per Google I/O 2026).

**Pick-by-job table** (the one you want on the whiteboard in the interview):

| Decision | OpenAI Dots | Anthropic Managed Agents | Google Antigravity |
|---|---|---|---|
| **Need always-on background work** | ✅ native | ⚠️ via subagent + cron | ⚠️ via scheduled job |
| **Deterministic enforcement (block-on-violation)** | ⚠️ plugin policy | ✅ **Hooks** (exit code 2) | ⚠️ IAM-only |
| **Hot-reloadable domain knowledge** | ⚠️ plugin store | ✅ **Skills** (per repo / per project) | ⚠️ docs upload |
| **Isolated context for a side task** | ✅ secondary dot | ✅ **Subagents** | ✅ sub-agent via ADK |
| **Project-level always-on guidance** | ⚠️ system prompt only | ✅ **CLAUDE.md** | ⚠️ instructions file |
| **Lowest per-request cost (coding, non-cached)** | **GPT-6 Sol $2/$10 per 1M** | Fable 5.1 $3/$15 (non-cache) | Flash 3.8 $0.75/$3.75 (intro, doubles Jan 1) |
| **Lowest per-request cost (coding, 70%+ cache hit)** | n/a | **Fable 5.1 cache $0.25/1M** | n/a |
| **Enterprise admin controls** | ✅ (DevDay) | ✅ (team / org level) | ✅ (Workspace) |
| **Government-restricted variant** | — | **Mythos 5.1** | **Gemini 3.8 Flash Cyber** (Fairwind) |

**Sources (methodology & reference):**
- [OpenAI DevDay 2026 recap (Dots, Agents API, Decisions API)](https://openai.com/index/devday-2026-recap/) `[primary]`
- [Towards AI — Claude Code Skills vs Subagents vs Hooks vs Workflows: Which to Use in 2026](https://pub.towardsai.net/claude-code-skills-vs-subagents-vs-hooks-vs-workflows-which-to-use-in-2026-120db6ae5b3c) `[analysis]`
- [MCP Directory — Skills vs Subagents vs Plugins vs Hooks (2026)](https://mcp.directory/blog/claude-code-skills-vs-subagents-vs-plugins-vs-hooks-2026) `[analysis]`
- [AI Architects — Best Claude Code Skills](https://theaiarchitects.com/blog/best-claude-code-skills) `[analysis]`
- [Developer in the Loop — The Ultimate Guide to Configuring Claude Code (2026 Update)](https://developerintheloop.substack.com/p/the-ultimate-guide-to-configuring) `[analysis]`
- [Chudi.dev — Claude Code Skills vs Subagents](https://chudi.dev/blog/claude-code-skills-vs-subagents) `[analysis]`
- [Constellation Research — OpenAI SDKs for app integrations, agentic AI building blocks](https://www.constellationr.com/insights/news/openai-sets-sdks-app-integrations-agentic-ai-building-blocks) `[analysis]`

### Why it matters to you

- **Job lens:** When an interviewer asks "which runtime would you use for X?", give the one-sentence version of the table above + name the policy / cost tradeoff. That answer is already better than 80% of candidates in Q4 2026.
- **Startup lens:** The gap in the table is **"deterministic enforcement + per-dot cost control + hot-reloadable skills + government variant"** — i.e., no single runtime wins all four. A **runtime-agnostic policy + cost + skills layer** is a legitimate seed-stage startup today.
- **Insight:** The 2026-era rule-of-thumb: **enforcement → Hooks; contextual knowledge → Skills; delegation boundary → Subagents; always-on project guidance → CLAUDE.md.** For OpenAI: Plugins = Skills-equivalent; Agents API computer-use = Subagent-equivalent; Decisions API = Hooks-equivalent. For Google: ADK sub-agents = Subagent; Workspace instructions = CLAUDE.md. The *concepts* are now cross-vendor; the *implementations* diverge.

→ Cross-link: [2026-09-10/03 §2 Claude Code decision tree](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree) · [`03` §3 weekend artifact](#3-weekend-artifact).

---

## 2. Rebuild your pricing model — GPT-6 Sol just changed the Claude-cache-read math {#2-pricing-rebuild}

**What changed:** The pricing table for the three major coding/agentic models shifted twice in 10 days:

| Model | Non-cached in / out ($/1M) | Cached in ($/1M) | Notes |
|---|---|---|---|
| Claude Fable 5.1 | $3 / $15 | **$0.25** (Sept 1 cut) | 75% cache discount; refresh every 60 min |
| GPT-6 Sol | **$2 / $10** (Sept 22 cut) | — (no prompt-cache tier publicly priced equivalent) | Half of GPT-5.6 Sol |
| Gemini 3.8 Flash | **$0.75 / $3.75** (Sept 2) | — (prompt-cache priced separately) | Intro — doubles to $1.50/$7.50 on **Jan 1, 2027** |

**The rebuild rule-of-thumb** (keep in a repo at `~/dev/router/pricing-notes.md`):

- **Cache hit rate ≥ 70%** → Fable 5.1 wins almost every coding workload.
- **Cache hit rate < 40%, cost-first** → GPT-6 Sol wins unless Gemini 3.8 Flash can handle the task.
- **High-volume classification / extraction** → Gemini 3.8 Flash intro pricing wins through Dec 31; migrate off (back to Haiku-5 if shipped, or Luna) before Jan 1 price double.
- **Government / restricted workload** → Mythos 5.1 or Gemini 3.8 Flash Cyber only; no cost comparison, access decides.
- **Agentic long-horizon with high tool-call counts** → favor Fable 5.1 if your prompts are reusable (cache); favor GPT-6 Sol via Dots if you need the runtime + plugins.

**Sources (pricing primary):**
- [ProPakistani — OpenAI launches GPT-6 Sol and Luna with 50% lower API costs](https://propakistani.pk/2026/09/24/openai-launches-gpt-6-sol-and-luna-with-50-lower-api-costs/) `[secondary]`
- [ComputingForGeeks — GPT-6 Sol/Luna released: features, benchmarks](https://computingforgeeks.com/gpt-6-sol-luna-released-features-benchmarks/) `[secondary]`
- [VentureBeat — Claude Fable 5.1 and Mythos 5.1 arrive with 75% cost reduction for Fable cache reads](https://venturebeat.com/technology/anthropics-claude-fable-5-1-and-mythos-5-1-arrive-with-a-75-cost-reduction-for-fable-cache-reads) `[secondary]`
- [benchlm — Gemini 3.8 Flash pricing and benchmarks](https://benchlm.ai/md/models/gemini-3-8-flash.md) `[aggregator]`
- [LetsDataScience — Google adds Gemini 3.8 Flash to AI Mode](https://letsdatascience.com/news/google-adds-gemini-38-flash-to-ai-mode-51fb6349) `[secondary]`

### Why it matters to you

- **Job lens:** Memorize the numeric table above. Interviewers in Q4 are explicitly testing cost reasoning — "what would you pay for 10M tokens of coding help this month?" has a specific right answer per workload.
- **Startup lens:** The **Jan 1 Gemini 3.8 Flash price double** is a marketing moment. If you ship a cost-aware routing tool, your campaign should fire **Dec 15–Jan 15**, with a free "see my new bill" one-page audit landing in CTO inboxes on Jan 2.
- **Insight:** The thing worth watching next: **does Anthropic push the cache discount further, or ship a Haiku-5 to re-anchor the cheap tier?** My read: Haiku-5 before year-end — otherwise Fable 5.1 cache-read is the *only* answer for cost-aware shops, which is a dangerous single-product dependency for them. Prepare both routes in your router.

→ Cross-link: [2026-09-10/03 §1 Fable 5.1 economics](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics) · [2026-05-20/03 Gemini 3.5 Flash price war](../2026-05-20/03-practical-skills-and-tools.md).

---

## 3. The weekend artifact — port one workflow to Dots or Managed Agents, publish evals + costs {#3-weekend-artifact}

**The problem this solves:** Every CS grad has "I built an agent" on their resume by now. The thing that re-prices you upward in Q4 is **proof you can pick a runtime, evaluate it, and own the cost model.**

### The spec (3–5 hour project)

**Pick one real workflow** you (or your team) run manually today. Example candidates:

- "**Weekly code-review triage**" — read 20 PRs, flag the 3 that need human attention.
- "**Research paper screener**" — pull last week's arXiv cs.AI, score the 10 most relevant to a thesis.
- "**Job-posting monitor**" — watch 15 careers pages for new postings matching a role template.

### Build

1. **Implement in two runtimes:**
   - Version A: **OpenAI Dots** (public preview) with a plugin or two.
   - Version B: **Anthropic Managed Agents** (Dreaming) with a Skill + a Hook.
2. **5-case eval suite** — identical inputs across both runtimes; golden outputs; score with a cheap LLM-judge (Gemini 3.8 Flash is fine). Public GitHub repo with `evals/*.jsonl`.
3. **Cost dashboard** — simple HTML page or Streamlit that reads your per-request logs and shows: cost per task, latency, tokens, tool-call count. Deploy to Vercel / HF Spaces / GitHub Pages.
4. **Write-up** — one `README.md` of **≤800 words** explaining: the workflow, both implementations, the eval table, the pick, and *why*.

### Publish

- Public GitHub repo. README with embedded eval table + cost dashboard link.
- Short LinkedIn post ("I ported an agentic workflow onto Dots and Managed Agents — here's which won and why") with the dashboard screenshot.
- Pin the repo on your GitHub profile.

### The 60-line router scaffold (seed code)

```python
# ~/dev/router/route.py
# minimal routing shim — expand with eval + cost logging
from __future__ import annotations
import os, time, json
from dataclasses import dataclass

@dataclass
class RouteDecision:
    runtime: str      # "dots" | "managed_agents" | "antigravity"
    model: str
    reason: str

def route(task: dict) -> RouteDecision:
    kind = task.get("kind")
    cache_hit_rate = task.get("expected_cache_hit", 0.0)
    is_restricted = task.get("restricted", False)
    always_on = task.get("always_on", False)

    if is_restricted:
        return RouteDecision("managed_agents", "mythos-5.1",
                             "restricted-access workload")
    if always_on:
        return RouteDecision("dots", "gpt-6-astra",
                             "needs background always-on cloud computer")
    if kind == "coding" and cache_hit_rate >= 0.7:
        return RouteDecision("managed_agents", "fable-5.1",
                             f"cache-friendly ({cache_hit_rate:.0%}) coding")
    if kind == "coding":
        return RouteDecision("dots", "gpt-6-sol",
                             "cold-cache coding; sol at $2/$10 wins")
    if kind in {"classification", "extraction"} and cheap_window():
        return RouteDecision("antigravity", "gemini-3.8-flash",
                             "high-volume + Flash intro pricing (through Dec 31)")
    return RouteDecision("managed_agents", "fable-5.1", "default")

def cheap_window() -> bool:
    # Dec 31 is the Gemini 3.8 Flash intro price boundary; see 03 §2
    return time.gmtime().tm_year == 2026 and time.gmtime().tm_mon <= 12
```

### Why it matters to you

- **Job lens:** This artifact answers *three* interview questions at once: (a) "have you shipped an agent?", (b) "do you understand cost?", (c) "can you evaluate?". No other 5-hour project does all three. Expect it to clear 2–3 rounds that a vanilla agent repo would not.
- **Startup lens:** If this evolves into a maintained *public* leaderboard (your eval suite + fresh model prices updated weekly), you have the seed of a **cost-aware-router SaaS**. Several Q3 funded startups (Natural; Parallel; Runware) share this DNA.
- **Insight:** The deeper point: in a world where models change weekly, **the artifact that stays current is more valuable than the model benchmark that was true two weeks ago.** This is why the eval suite matters more than the agent code — it is the thing that keeps earning dividends.

→ Cross-link: [2026-09-10/03 §3 router artifact](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) · [`04` §1 agent-memory research](./04-research-progress.md#1-agent-memory-icml).

---

## 4. The 5-minute daily reading loop {#4-reading-loop}

**Problem:** 20+ announcements per DevDay × 3 labs × weekly cadence = unreadable.

**Fix:** The 5-minute morning check-list, in order:

1. **1 min —** `https://openai.com/news/`, `https://www.anthropic.com/news`, `https://deepmind.google/discover/blog/`. Scan headlines only.
2. **1 min —** `https://huggingface.co/papers/trending`. Open the top 3 abstracts in tabs; read titles + first-paragraph.
3. **1 min —** `https://news.ycombinator.com/` → Ctrl-F "AI" or "Claude" or "GPT". Open any threads with >100 comments.
4. **1 min —** check **Simon Willison** (`https://simonwillison.net/`) and **Latent Space** for any new post.
5. **1 min —** add any noteworthy items to today's TLDR draft or `WATCHLIST.md`.

### Why it matters to you

- **Job lens:** Candidates who can speak to *this week's* news in interviews stand out immediately. The 5-minute loop is sustainable; a 60-minute daily newsletter habit is not.
- **Startup lens:** Being the person *in your network* who flags the Oct 1 Armadin raise two days before it hits aggregators is social-capital compounding. The 5-min loop produces that outcome at near-zero cost.
- **Insight:** Simon Willison's own advice — "**use models for several hours on a variety of tasks to develop an intuition about what they can and can't do**" — is still the single highest-leverage reading-adjacent habit. Pair your 5-min scan with 1 hour of hands-on model use per day; the two together produce the "AI-fluent engineer" signal.

**Sources:**
- [Simon Willison's weblog](https://simonwillison.net/) `[primary]`
- [Lessons from Simon Willison (summary)](https://www.antoinebuteau.com/lessons-from-simon-willison/) `[analysis]`
- [RealPython — Simon Willison on LLMs for Python Development](https://realpython.com/podcasts/rpp/236/) `[secondary]`

→ Cross-link: [`SOURCES.md`](../SOURCES.md) · [`ME.md` — personal rules](../ME.md#personal-rules).
