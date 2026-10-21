# Practical Skills & Tools — 2026-10-03

Three high-ROI items for the weekend. **The theme: the extension surface for Claude Code just got bigger (mods), the cost math for OpenAI just got cheaper (GPT-6.1 Sol at ⅕ of Astra), and "persistent agent" is now a design problem you need an answer to for every FDE interview this month.** All three compound on the router artifact from [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact).

Tags: `#claude-code #mods #plugins #routing #gpt-6-1 #persistent-agents #cost #evals`

---

## 1. Claude Code mods — fork, ship, demo-gif tonight (60 minutes) {#1-claude-code-mods}

**What happened:** On **October 1, 2026**, Anthropic shipped **mods** for **Claude Code v2.1.287+**: TypeScript function hooks that run on the agent's internal events and change what it does. **A mod can:**

- Rewrite a prompt before it reaches the model.
- Block, retry, or redirect a tool call.
- Approve or deny a permission request.
- Redact secrets from tool output.
- Edit or replace interface elements (CLI banners, desktop panes, status lines).

**Distribution:** Mods ship **inside plugins**, install with **`/plugin`**, work in **both CLI and desktop app**.

**Official examples (study these first):**
- **Token Weather** — live context-window forecast displayed above the prompt box.
- **Blast Radius** — dry-runs dangerous commands (e.g. `rm -rf`) and previews the blast area before execution.
- **Replay Theater** — steps through a round of edits one change at a time.

**Security warning (don't skip):** **Mods are NOT sandboxed.** A mod runs with the same privileges as Claude Code, which means it can read your `ANTHROPIC_API_KEY`, environment variables, SSH keys, anything. **Install only from sources you trust.** This is the "VS Code extensions can read everything" tradeoff in a new form.

### Fast path to a shippable mod (60 min)

1. **Clone the examples repo** — spend 10 minutes reading `Token Weather` and `Blast Radius` end-to-end. The API surface is small; the examples cover 80% of it.
2. **Pick ONE of these three mod ideas** and build it:
   - **(a) Cost-router mod** — intercept prompts, read a small `routing.json`, swap the model-ID based on task type (coding → GPT-6.1 Sol via a shim, long-context → Fable 5.1, cheap-summary → Haiku-equivalent). Ties your router artifact directly into Claude Code's event loop. Resume differentiator: "my router isn't a side script, it's a Claude Code primitive."
   - **(b) Secrets-redaction mod** — scan tool output for `AWS_*`, `OPENAI_API_KEY`, `GITHUB_TOKEN`, auth cookies, JWTs. Redact in-place before the model ever sees them. Addresses the "not-sandboxed" security concern head-on and shows CISO-aware thinking.
   - **(c) Weekly-spend mod** — on each API call, log tokens + estimated $ to a local SQLite; render a weekly chart in CLI as a status line. Doubles as the "personal Claude billing audit" artifact from [ME.md](../ME.md).
3. **Record a 60-second Loom or gif** showing it running on a real project.
4. **Publish** as a plugin in a GitHub repo; add README with install instructions.
5. **Post to LinkedIn Monday morning** with the gif + 3-sentence writeup.

### Why this is the right artifact right now

- **Novel + concrete:** zero other new grads have shipped a Claude Code mod yet (the feature is 48 hours old at time of writing).
- **Interview-cover:** answers "do you know what shipped this week?" + "can you ship a demo?" + "do you think about agent security?" in one artifact.
- **Composable:** this is a Claude Code primitive; it will still work in 2027. Unlike a demo-chatbot repo, it does not rot.

### Sources
- [Anthropic — Claude Code announcements / mods](https://claude.com/blog-category/announcements) `[primary]`
- [AI Weekly — Anthropic Launches Claude Code Mods, TypeScript Agent Hooks](https://aiweekly.co/alerts/anthropic-launches-claude-code-mods-typescript-agent-hooks) `[secondary]`
- [Mixed News — Claude Code 2.1.287 adds mods, Anthropic says they can read your API key](https://mixed-news.com/en/claude-code-2-1-287-mods-not-sandboxed-api-key/) `[secondary]`
- [Gigazine — Claude Code customize mod feature](https://gigazine.net/gsc_news/en/20261002-claude-code-customize-mod/) `[secondary]`
- [Curated AI Tools — Claude Code Adds TypeScript Mods](https://curatedaitools.substack.com/p/claude-code-adds-typescript-mods) `[analysis]`
- [DEV Community — AI Daily Digest October 3, 2026](https://dev.to/hiroki-ii-ai/ai-daily-digest-october-3-2026-claude-code-mods-muse-on-smart-glasses-dgx-spark-64gb-tesla-olp) `[aggregator]`
- [DigitalApplied — Claude Code Mods: What Function Hooks Can Change](https://www.digitalapplied.com/blog/claude-code-mods-function-hooks-explained) `[analysis]`
- [cellcog.ai — Claude Code Mods: What They Can Do and What They Can Reach](https://cellcog.ai/blog/claude-code-mods/) `[analysis]`
- [Releasebot — Claude Updates by Anthropic — October 2026](https://releasebot.io/updates/anthropic/claude) `[aggregator]`

---

## 2. GPT-6.1 Sol routing update — add it to the router today {#2-gpt61-sol-routing}

**What happened:** OpenAI shipped **GPT-6.1 Sol** at DevDay with **"approaches GPT-6 Astra" quality at ⅕ the input + output price.** Combined with Anthropic's Fable 5.1 cache-read cut ($1 → $0.25 / 1M), the price curve for frontier-near-frontier work has moved **~70% down since late August.**

### The 15-minute router update

If you have the router artifact from [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact):

1. **Add a row** to `providers.json`:
   ```json
   {"name": "gpt-6-1-sol", "input_$per_m": "<official>", "output_$per_m": "<official>", "task_bias": ["coding", "cheap-summary", "tool-use"]}
   ```
2. **Add a routing rule:** when task-type is `coding` OR `cheap-summary`, route to GPT-6.1 Sol first; fall back to Fable 5.1 on refusal or quality-score < threshold.
3. **Re-run the 5-case eval suite** across all providers; update the leaderboard README.
4. **Commit + push.** Weekly re-run cadence from now on (DevDay cycle proves monthly isn't fast enough).

### What to put in the leaderboard README

Three columns the recruiter cares about:

| Task | Winner by cost | Winner by quality | Winner by latency |
|---|---|---|---|
| Cheap summary | likely GPT-6.1 Sol / Gemini 3.8 Flash | varies | likely Ultrafast tier |
| Long-context Q&A | likely Fable 5.1 (cache) | likely Astra | varies |
| Coding | likely GPT-6.1 Sol | varies by language | Ultrafast if available |
| Tool-use | varies | varies | varies |
| Refusal/safety | varies | varies | varies |

**Fill in with YOUR numbers, not Twitter numbers.** A measured leaderboard from your own eval suite is the artifact; a repeated-from-blog table is not.

### Why this is the single highest-leverage hour this week

- **Cost delta is real:** GPT-6.1 Sol being ⅕ of Astra means **a well-routed workload cuts your bill 30–60% with no code rewrite** — just a config swap. This is a line-item win you can show on a chart.
- **Interview trump card:** "What's the current state of model routing in H2 2026?" is now a question that half of hiring loops will ask. Your repo answers it.
- **Weekly cadence habit:** this exercise, done every Saturday for 8 weeks, becomes a 2-month timeline chart of the price-cuts of 2026 — a credible research artifact on its own.

### Sources
- [OpenAI — DevDay 2026 Recap](https://openai.com/index/devday-2026-recap/) `[primary]`
- [InfoQ — OpenAI DevDay 2026 Recap for Developers](https://www.infoq.com/news/2026/10/openai-devday-2026/) `[secondary]`
- [Memeburn — DevDay 2026 Recap: One Big Idea and a Quiet Price Reset](https://memeburn.com/openai-devday-2026-recap/) `[analysis]`

---

## 3. Persistent-agent design — the Dots-shaped question every FDE loop will now ask {#3-persistent-agents}

**What happened:** OpenAI's **Dots** turned "persistent cloud-PC agent with ongoing responsibilities" into a product category. Every FDE / Solutions Engineer / AI Engineer interview from now through Q1 will have a design question of the form **"design an agent that works on $goal across days/weeks."** Have an answer.

### The 5-question design template

Use these as the backbone when answering. **Memorize the order.**

1. **State management.** Where does the agent keep its working memory between invocations — a vector DB, a scratchpad file, structured JSON in a DB, or an episodic log? What's the recovery story if that store is lost or stale?
2. **Cost ceiling.** What's the per-day $ cap? How is it enforced — provider-side quota, custom middleware, or a kill-switch tool call? How do you alert BEFORE hitting it, not after?
3. **Human-in-the-loop boundaries.** Which actions require explicit approval (payments, external messages, destructive-command, writes to shared systems)? How does the approval UI work when the human isn't logged in?
4. **Progress & observability.** What dashboards / logs / summaries does a user see each day? How much is auto-summarized vs. verbatim? What's the "I don't trust this, show me the raw tape" affordance?
5. **Failure modes & recovery.** What happens when a tool call fails, when the model refuses mid-plan, when the user changes the goal halfway through? What's the "safe-mode" state the agent falls back to?

### 30-minute whiteboard exercise this weekend

Pick a concrete goal — e.g., **"an agent that keeps my inbox at zero over 14 days without ever sending an email I'd regret"** — and answer all 5 questions on paper. Then:

- Write a 1-page memo (not more).
- Post a redacted version to LinkedIn or your blog Monday.
- Reference it on every FDE interview this month. The memo IS the answer.

### Why this beats "I built a chatbot with GPT-4o"

- **Dots-shaped problems are the 2026 Q4 interview category.** First to show a memo wins the slot.
- **The 5-question template is reusable** — one memo, many interviews.
- **It makes you sound like someone who has run a system in production**, even if you haven't yet.

### Sources
- [OpenAI — DevDay 2026 Recap (Dots)](https://openai.com/index/devday-2026-recap/) `[primary]`
- [emergent.sh — Every Announcement, From Dots to GPT-6.1 Sol](https://emergent.sh/news/openai-devday-2026) `[aggregator]`
- [Firecrawl — Top 15 Agentic AI Trends to Watch in 2026](https://www.firecrawl.dev/blog/agentic-ai-trends) `[analysis]`

→ Cross-link: [`04` §1 agent-safety research applies here](./04-research-progress.md#1-agent-safety-trio).

---

## 4. One-line habits worth keeping this week {#4-habits}

- **`claude code --version` → confirm ≥ 2.1.287** on every project before you spend tonight writing a mod. A silent version mismatch wastes the hour.
- **Weekly router re-run** — add a Saturday-noon cron that reruns your eval suite + commits the updated leaderboard. The cadence beats any single eval score.
- **S-1 numbers memorized** — $4.59B 2025 rev · $11.5B Q2 2026 · $8B operating loss (not $42B) · $518B compute obligations · $20.28B cash. These are the interview-ready numbers for any Anthropic conversation this month.
- **One mod a week** — the directory is new; the fastest way to build a reputation in the Claude ecosystem for the next 90 days is to be a repeat mod author with 4–5 shipped mods by year-end.

### Sources
- [SmartScope — Claude Code Advanced Best Practices 2026](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[analysis]`
- [AgentsRoom — 50 Claude Code Tips & Tricks: Ship 10x Faster in 2026](https://agentsroom.dev/claude-code-tips) `[analysis]`
- [benchlm.ai — DevDay 2026: Dots, GPT-6.1 Sol, Ultrafast, and Codex Cloud](https://benchlm.ai/blog/posts/openai-devday-2026) `[analysis]`
