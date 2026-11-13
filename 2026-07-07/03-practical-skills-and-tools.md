# 03 — Practical Skills & Tools — 2026-07-07

## 1. The three cost levers that survive June-15 metering (do these tonight) {#1-cost-levers}

If you've been running Claude Code / Anthropic Agent SDK past the June-15 metering change, your bill has moved from **subsidized** to **API-list**. There are exactly three levers that compound; run all three:

### Lever A — Prompt caching (60–90% input-token cut)

- **Cached input tokens ≈ 10% of the normal input price** on Claude.
- Turn it on for **any prompt with a stable prefix** (system prompt, tool definitions, doc corpus, few-shot). Claude Code handles this automatically for its main loop, but **you have to structure your own prompts to hit the cache** — put the volatile bits at the *end*.
- **Subagents don't inherit the parent cache.** Each subagent warms its own cache from scratch. Two implications:
  1. Prefer **long-running subagents with stable system prompts** over one-shot spawns.
  2. **Batch** related work into one subagent invocation rather than N.
- Per-model caches: Opus and Haiku (and Sonnet 5) are **separate**. Route light tasks to a lighter model *before* thinking about caching.

### Lever B — Tool Search Tool (–85% token usage, big MCP-eval jump)

Anthropic's **Tool Search Tool** is the "you don't have to load 40 tool schemas into every prompt" fix.
- **~85% reduction in tool-token usage** while retaining access to your full tool library.
- **Opus 4** MCP eval: **49% → 74%.**
- **Opus 4.5** MCP eval: **79.5% → 88.1%.**
- **How:** register your MCP servers as usual, then let Claude search for the tool by task description instead of prefetching the whole tool catalog. In practice this means turning on Tool Search in your `.mcp.json` and stripping any manual "here are all the tools" preludes from your CLAUDE.md.

### Lever C — Minimal Claude Code setup (the "one of each" rule)

The 2026 consensus setup — echoed by okhlopkov, alexop, and marktechpost 25-features writeups — is:

- **1 short `CLAUDE.md`** (project rules + goals + gotchas; no history).
- **1 scoped `.mcp.json`** (only the servers you actually use — usually GitHub + browser + one DB + one deploy).
- **1 safety hook** (session-start or pre-tool; blocks a category of destructive command).
- **1 reusable skill** (one `.claude/skills/name/SKILL.md` for the workflow you repeat 3+ times/week).
- **Subagents only when a task would otherwise pollute the main context** — research, review, or a bounded refactor. Not for "make my prompt look smart."

If you can't explain **why every server, hook, skill, and subagent exists** in one sentence, delete it. Everything past minimal costs tokens and cognitive load.

### Combined effect (from the field reports)

Stacking these three on a real production loop takes a workload from **~$2,490/month to ~$100/month** (unoptimized 100 msgs/day at 166K input on Opus 4.6) per the aimagicx tutorial, and the towardsdatascience "Agentic AI: How to Save on Tokens" walkthrough puts typical production savings at **70–80%**.

**Why it matters — three lenses.**
- **Job:** the interviewer's next favorite question is **"how much do your agents cost per successful task?"** Have a real number.
- **Startup:** this is the single biggest gross-margin lever available to you before Aug 31 (Sonnet 5 intro pricing).
- **Insight:** the differentiated 2026 skill isn't "I prompt well." It's **"I designed the cache/route/schema layout that made this workload survive the API list price."**

**Sources.**
- [primary] [Claude Code Docs — Prompt Caching](https://code.claude.com/docs/en/prompt-caching)
- [primary] [Anthropic — "Introducing advanced tool use on the Claude Developer Platform"](https://www.anthropic.com/engineering/advanced-tool-use) (Tool Search Tool)
- [primary] [Anthropic — "Code execution with MCP"](https://www.anthropic.com/engineering/code-execution-with-mcp)
- [primary] [Anthropic — "Best practices for Claude Code"](https://www.anthropic.com/engineering/claude-code-best-practices)
- [analysis] [okhlopkov — "Claude Code Setup 2026: MCP, Hooks, Skills"](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/)
- [analysis] [alexop.dev — "Claude Code Explained (2026): MCP, Skills, Subagents"](https://alexop.dev/posts/understanding-claude-code-full-stack/)
- [analysis] [MarkTechPost — "Claude Code Guide 2026: 25 Features with Examples + Demo"](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/)
- [analysis] [Towards AI — "Claude Code: The 2026 Zero to Hero Guide"](https://pub.towardsai.net/claude-code-the-2026-zero-to-hero-guide-3be2eee55f66)
- [analysis] [Tosea.ai — "How to Use Claude Code: Complete 2026 Guide"](https://tosea.ai/blog/claude-code-complete-guide-2026)
- [analysis] [Suprmind — "Claude Features 2026: Projects, Artifacts, Memory, Computer Use, Skills, MCP"](https://suprmind.ai/hub/claude/features/)
- [analysis] [AI Magicx — "Prompt Caching for Claude: Cut Your API Bill 60% in Production"](https://www.aimagicx.com/blog/prompt-caching-claude-api-cost-optimization-2026)
- [analysis] [MindStudio — "Prompt Caching to Cut Claude Code Token Costs"](https://www.mindstudio.ai/blog/prompt-caching-cut-token-costs-claude-dynamic-workflows) · [Token management guide](https://www.mindstudio.ai/blog/claude-code-dynamic-workflows-token-management-cost)
- [analysis] [Respan.ai — "Claude Prompt Caching: 90% Cost Reduction Guide"](https://www.respan.ai/articles/claude-prompt-caching)
- [analysis] [Claude Code Camp — "How Prompt Caching Actually Works in Claude Code"](https://www.claudecodecamp.com/p/how-prompt-caching-actually-works-in-claude-code)
- [analysis] [mager.co — "Claude: How prompt caching actually works"](https://www.mager.co/blog/2026-04-29-claude-prompt-caching/)
- [analysis] [Build This Now — "Claude Code Prompt Caching: The Token Discount Most People Never Turn On"](https://www.buildthisnow.com/blog/guide/development/claude-code-prompt-caching)
- [analysis] [Towards Data Science — "Agentic AI: How to Save on Tokens"](https://towardsdatascience.com/agentic-ai-how-to-save-on-tokens/)

---

## 2. This week's portable interview artifact: "3-vendor eval + cost log"

The two big vendor stories today — **Sonnet 5 at intro pricing** and **GLM 5.2 at ~1/5 the cost** — combine into a single portfolio artifact that answers three interview questions at once.

**Ship this by Sunday:**

1. Pick one small task with a **clean success signal** (e.g., "extract these 5 fields from a PDF and return valid JSON"). Aim for something with a **binary evaluator**.
2. Wire it against **three vendors** — **Sonnet 5**, **GPT-5.5 / 5.6-if-available**, **GLM 5.2 via OpenRouter**.
3. Run **50 real cases** through each. Log per-call: **cost (cached + uncached), latency, success%.**
4. Publish a README with a **three-column comparison** and a one-sentence recommendation per use case.
5. Open-source the harness on GitHub with `#mcp #eval #cost` tags.

This one artifact demonstrates: **multi-vendor competency**, **real-tool eval discipline**, **cost-aware engineering** — the three things that show up on every 2026 AI Engineer / FDE / Integration JD.

**Sources.**
- [primary] [Claude Sonnet 5 launch](https://www.anthropic.com/news/claude-sonnet-5) (Aug 31 intro pricing)
- [primary] [OpenRouter model rankings](https://openrouter.ai/) (verify GLM 5.2 position for your write-up)
- See [`02` §1](./02-new-emerging.md#1-glm-52) for the GLM 5.2 context.
