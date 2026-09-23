# Practical Skills & Tools — 2026-09-20

Three items. The first is a *reset* to your fundamentals — context engineering is now the practitioner-consensus discipline (Sourcegraph, Neo4j, mem0, Towards AI, DEV Community). The second is a **Claude Code changelog walk-through** you can act on in 15 minutes tonight. The third is a **weekend artifact** — the OpenAI DevDay 2026 (T-9) predictions doc that lets you publicly grade yourself on Sept 30 and turn the grade into an interview line.

Tags: `#context-engineering #agents #memory #claude-code #skills #plugins #mcp #evals #devday #artifact`

---

## 1. Context engineering — the 2026 practitioner fundamental {#1-context-engineering}

**What happened:** The 2026 middle-year consensus (Sourcegraph, Neo4j, mem0, DEV Community, Towards AI, iwoszapar) has converged on **"context engineering" as the fundamental** — replacing "prompt engineering" as the phrase practitioners lead with. **Prompt engineering asks *what words?*; context engineering asks *what configuration of the whole context is most likely to generate the desired behavior?***

The six techniques that matter:

1. **Hybrid sliding window** — keep the latest N turns raw, summarize older ones. The most practical starting point for any long-running agent.
2. **Structured memory** — separate short-term (working context), long-term (embeddings + KV store), and episodic (agent trajectory logs) instead of one blob.
3. **Tool-def hygiene** — put a single canonical tool spec at the top of the system prompt, then reference it, don't re-inject.
4. **RAG budget** — every retrieved chunk gets a per-request token budget; cheapest-relevant wins.
5. **Cache-anchored system prompts** — Fable 5.1 cache reads at $0.25/1M ([2026-09-10/03](../2026-09-10/03-practical-skills-and-tools.md)) make the "big static system prompt + tiny variable suffix" pattern nearly free.
6. **Ablation-tested compression** — never compress a context without an eval that measures the drop. **Never LLM-generate your context files** (Gloaguen 2026 result: LLM-generated context files degrade downstream agent performance vs. hand-authored).

**Corollary:** *If you have to explain to a colleague what "context engineering" means, use this line: "Prompt engineering is a sentence; context engineering is the whole pipeline that produces that sentence and everything around it."*

### Concrete tonight (30 minutes)

1. Open your longest-running agent project. Pick one call site.
2. Print the actual context sent to the model on a real request (via SDK debug flag, not what you *think* you're sending).
3. Split it into 5 buckets: **system prompt · tool defs · retrieved context · conversation history · user input.**
4. Estimate tokens per bucket. Note which bucket you *didn't* know was that big.
5. Pick one intervention from the list above and A/B it with a 3-case eval. Log the outcome.

### Sources
- [Sourcegraph — Context Engineering: A Practical Guide for AI Agents (2026)](https://sourcegraph.com/blog/context-engineering) `[analysis]`
- [Neo4j — What is context engineering in AI agents?](https://neo4j.com/blog/agentic-ai/what-is-context-engineering/) `[analysis]`
- [Atlan — Context Engineering Techniques for AI Agents: A 2026 Guide](https://atlan.com/know/ai-agent/context-engineering/context-engineering-techniques-ai-agents/) `[analysis]`
- [mem0 — Context Engineering AI: How To Build Smarter LLM Agents In 2026](https://mem0.ai/blog/context-engineering-ai-agents-guide) `[analysis]`
- [DEV Community — Context Engineering for Developers: A Practical Guide (2026)](https://dev.to/amitba/context-engineering-for-developers-a-practical-guide-2026-pi1) `[analysis]`
- [Towards AI — State of Context Engineering in 2026](https://pub.towardsai.net/state-of-context-engineering-in-2026-cf92d010eab1) `[analysis]`
- [Towards AI — The 6 Techniques That Actually Matter in 2026](https://towardsai.com/p/machine-learning/context-engineering-the-6-techniques-that-actually-matter-in-2026-a-comprehensive-guide) `[analysis]`
- [iwoszapar — Context Engineering Research: Papers & Benchmarks (2026)](https://www.iwoszapar.com/p/context-engineering-research-2026) `[analysis]`

---

## 2. Claude Code September 2026 changelog — three wins you can capture tonight {#2-claude-code-changelog}

**What happened:** Anthropic's Sept 2026 Claude Code releases include three under-marketed improvements. The full changelog runs longer, but these three cover ~80% of the practical delta if you last updated in July.

### 2a. `syncClaudeAiSkills` / `syncClaudeAiPlugins` — your account state now syncs to terminal
Skills and plugins enabled on your `claude.ai` account now sync to Claude Code terminal sessions signed in with the same account. Opt out per-machine with `syncClaudeAiSkills: false` or `syncClaudeAiPlugins: false` in `~/.claude/settings.json`.

**Why it matters:** the "which skills am I actually running?" question just got a single source of truth. If you maintain skills across your laptop + a dev VM + a CI runner, this is a 15-minute cleanup that removes an entire category of drift bugs.

### 2b. `/plugin install <plugin> --marketplace <source>` — one-shot marketplace-plus-plugin add
The new flag offers to add the marketplace source *before* installing the plugin. Previously you had to add the marketplace, then install; now it's one command that prompts you.

**Why it matters:** onboarding a new dev to a repo with a curated plugin stack drops from 3 shell commands to 1. Add it to your `README.md` "getting started" section tonight for any repo with plugins.

### 2c. Subagent MCP-tool prompt-caching bug — fixed
Subagents that resumed a session (via context: fork, teammate, or explicit resume) were re-rendering their MCP tool definitions on every request, silently breaking prompt caching. **Fixed in the September releases.**

**Why it matters:** if you run long subagent chains with MCP tool sets larger than a few KB, your input cost on those chains just dropped meaningfully with no code change. Rerun your cost dashboard — the delta should be visible in the last 10 days if you're on the latest Claude Code.

### Bonus mention — `--forward-subagent-text` fixes
Subagents spawned by a `context: fork` skill, and forked skills invoked by another subagent, were dropping their `stream-json` / SDK output. Fixed. If you were seeing empty subagent transcripts and had a `context: fork` skill in the chain, that's why.

### Sources
- [Claude Code Changelog (official)](https://code.claude.com/docs/en/changelog) `[primary]`
- [Gradually — Claude Code Changelog (September 2026)](https://www.gradually.ai/en/changelogs/claude-code/) `[analysis]`
- [Releasebot — Claude Code Updates by Anthropic (September 2026)](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Duotach — Claude Code Subagents and Skills: Complete Guide 2026](https://duotach.com/en/blog/subagentes-claude-code) `[analysis]`
- [Totalum — Claude Code Skills in 2026: The Complete Guide (vs Hooks, vs Subagents, vs MCP)](https://www.totalum.app/blog/claude-code-skills-totalum) `[analysis]`
- [Totalum — Claude Agent SDK in 2026: Complete Guide to Plans, Credits, and Shipping to Production](https://www.totalum.app/blog/claude-agent-sdk-totalum-2026) `[analysis]`
- [MarkTechPost — Claude Code Guide 2026: 25 Features with Examples + Demo](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[analysis]`

---

## 3. Weekend artifact — the OpenAI DevDay 2026 predictions doc (publish before Sept 29) {#3-devday-watchlist}

**What happened:** OpenAI DevDay 2026 is on **Tuesday Sept 29 at Fort Mason SF**. Applications closed July 10 at $650. The **opening keynote livestreams.** Preview: developers will "go deep in technical sessions, test what's new, swap notes, and bring their questions and ideas to the teams creating OpenAI's tools." DevDay Exchanges follow in Bengaluru, Tokyo, Seoul, Paris, Berlin, London, São Paulo, Mexico City.

The artifact: **a public one-page GitHub doc titled `openai-devday-2026-predictions.md`** — your 5 falsifiable predictions with confidence weights, timestamped *before* the keynote and *graded* on Sept 30. It reads well on your resume, adds to your GitHub graph, and gives you two natural checkpoints for LinkedIn posts (pre-keynote prediction post; post-keynote graded post).

### Suggested 5 predictions to consider (feel free to swap based on your reading)

| # | Prediction | Confidence | Reasoning |
|---|---|---|---|
| 1 | **A "GPT-6 Astra" API-tier repricing** — either a batch-tier or cached-input discount to match Fable 5.1's 75% cache-read cut | 70% | Anthropic's Fable 5.1 economics ([2026-09-10/03](../2026-09-10/03-practical-skills-and-tools.md)) directly attack OpenAI's price position; DevDay is the natural response window |
| 2 | **An Agents SDK 2.x with a Managed-Agents-shaped runtime** — parity with Anthropic Managed Agents + Google's Antigravity 2.0 ([2026-05-20/00](../2026-05-20/00-tldr.md)) | 80% | The runtime primitive is already table stakes; OpenAI's Sponsored Agents launch requires this substrate |
| 3 | **An official Ads / Sponsored Agents SDK for advertisers** — the developer-side of the [2026-09-16 Sponsored Agents launch](./01-big-lab-moves.md#5-openai-sponsored-agents) | 60% | The Wayfair + Angi test is manual today; DevDay is when developer-side tooling ships |
| 4 | **Codex mobile expansion + Codex-in-Windows-desktop** — cross-platform parity with the [May 14 iOS/Android release](../2026-05-17/00-tldr.md) | 55% | Windows was the notable absentee from Codex's May mobile expansion; DevDay is the natural completion beat |
| 5 | **A Voice or Realtime API v3** — successor to Realtime-2 with lower latency + a new voice family | 50% | xAI's speech stack (May) + Google's WebMCP posture create pressure; OpenAI hasn't shipped a Realtime update in ~4 months |

### Grading rubric

Each prediction gets a binary hit/miss score. **Confidence-weighted Brier score** for the whole slate:
- Perfect calibration = Brier 0.0
- Coin-flip calibration = Brier 0.25
- Anything under 0.15 is a solid interview line ("I calibrated at Brier 0.13 on OpenAI DevDay 2026 — here's the writeup.")

### The interview-artifact play

The 5-prediction doc + the graded follow-up is a **legibly-tiny public commitment** that proves three specific things hiring managers screen for:
1. **You watch the frontier** (which is table stakes).
2. **You commit to falsifiable claims** (which most people don't — they hedge in prose).
3. **You keep score honestly on Sept 30** (Brier-score literacy is scarce and reads as intellectual honesty).

Include a link in your LinkedIn "featured" section. Include it in your Anthropic / OpenAI / Sierra application cover letter as `github.com/<you>/openai-devday-2026-predictions`.

### Sources

- [OpenAI — Announcing OpenAI DevDay 2026](https://openai.com/index/devday-2026/) `[primary]`
- [OpenAI DevDay 2026 site](https://devday.openai.com/) `[primary]`
- [OpenAI Developer Community — DevDay 2026 applications open](https://community.openai.com/t/openai-devday-2026-applications-are-now-open/1384509) `[primary]`
- [AIToolsReview — OpenAI DevDay 2026: Date, Location and What Is Confirmed](https://aitoolsreview.co.uk/insights/openai-devday-2026) `[analysis]`
- [gadgetbond — OpenAI DevDay 2026 is set for September 29 in San Francisco](https://gadgetbond.com/openai-devday-2026-september-29-san-francisco/) `[secondary]`

---

## Bonus micro-tips {#bonus-microtips}

- **Turn on `syncClaudeAiSkills` tonight** (see §2a) — one setting change, 30-second win.
- **Add `.claude/settings.json` to `.gitignore` if you haven't already** — the sync means it's now personal-context-heavy.
- **Publish your prompt-caching cost delta since Fable 5.1** (see [2026-09-10/03 §1](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics)) — a 3-line chart on Twitter/LinkedIn ties two threads (the model release + your public spend audit) into one recruiter-legible signal.
- **Move a "must run" line out of `CLAUDE.md` and into a hook this weekend** (per the [decision tree in 2026-09-10/03 §2](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree)) — a single move is a good interview anecdote.
