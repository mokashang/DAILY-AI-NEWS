# Practical Skills & Tools — 2026-07-16

Three moves you can make **tonight** — all of them turn today's news into an artifact you can point to in interviews next month. The **big one** is the **Cowork scheduled-task cookbook**: Anthropic just gave every Max subscriber an "async second engineer" and it's underused.

Tags: `#claude-code #cowork #scheduled-tasks #prompt-engineering #cost-aware #workflows #mcp #skills`

---

## 1. Wire your first Cowork scheduled task tonight (the "async second engineer" workflow) {#1-cowork-mobile}

**What changed (this week):** Claude Cowork went **cross-device and background-executing** — start on desktop, get updates on phone, review + approve anywhere. **Scheduled tasks run when your laptop is closed.** Cowork usage limits **doubled through August 5**. See [`01` §4](./01-big-lab-moves.md#4-cowork) for the launch details.

**The under-priced skill this creates:** *designing scheduled agent briefs.* Not prompting a live chat — writing a **compact, verifiable, self-recoverable brief** that runs at 6 AM without you there. The whole discipline is different: you can't clarify midstream, so **the brief has to be complete, the success criterion has to be checkable, and the fallback has to be an unsent draft, not an unattended action.**

**Concrete blueprint — the "async second engineer" workflow:**

```
name: morning_ai_brief
schedule: weekdays 6:00 AM local
brief:
  role: Research analyst tracking AI news for a CS grad student
  inputs:
    - my ~/reading-list Notion page (via MCP Notion connector)
    - arxiv daily list (fetch via WebFetch): cs.AI, cs.LG, cs.CL
    - my Gmail label "AI-newsletters" (last 24h)
  task: |
    1. Skim inputs; keep only items relevant to CS-grad-with-startup-goals
       (agents, MCP, evals, funding, hiring signals).
    2. For each keeper, write a 2-line summary and tag with the ME.md-style
       Job/Startup/Insight lenses.
    3. Rank by "would-I-regret-missing-this" score 1-5.
  output: |
    Markdown file in ~/daily-briefings/YYYY-MM-DD.md
    Draft email to me with the top 3, subject "AI brief YYYY-MM-DD"
    Do NOT send. Leave in drafts folder.
  success check: |
    Top 3 items each have >=1 source URL and >=1 lens applied.
    File has >=5 keepers total.
  on_failure: leave a draft to me with what worked, what didn't, links you found
```

**Three templates worth building this weekend:**

1. **`morning_ai_brief.md`** — the workflow above. You get a curated arXiv+newsletter+Notion digest at 6 AM every weekday, ready in your inbox.
2. **`weekly_repo_review.md`** — Fridays 5 PM: Cowork clones your public repo, runs a self-review against a rubric ("clarity, tests, docs, README completeness"), and leaves a PR with markdown comments. **This is the artifact that answers agent-eval and code-review interview questions simultaneously.**
3. **`job_board_delta.md`** — Mondays 7 AM: Cowork walks a fixed list of career pages (Anthropic, OpenAI, Sierra, Palantir, Google, Databricks, YC AI Jobs) via WebFetch, diffs against last week's saved JSON, and drops a "new roles you care about" note into your inbox with drafted 3-sentence intro paragraphs.

**Publish the artifact:** create a public repo **`scheduled-tasks-cookbook`** with these three YAML/markdown briefs + a README that explains the design pattern (complete brief · checkable success criterion · unsent-draft fallback). *One artifact, three interview stories:* agent design, reliability under async, real production workflow.

**Sources:**
- [Anthropic — Claude Cowork on web and mobile](https://claude.com/blog/cowork-web-mobile) `[primary]`
- [Enterprise DNA — Claude Cowork Goes Mobile: AI Agents Work While You Sleep](https://enterprisedna.co/resources/news/anthropic-claude-cowork-mobile-web-background-agents-july-2026/) `[analysis]`
- [Digital Applied — Claude Cowork Goes Web and Mobile: A Team Rollout Guide](https://www.digitalapplied.com/blog/claude-cowork-web-mobile-expansion-guide-2026) `[analysis]`

### Why it matters to you

- **Job lens:** This is a **directly-shippable interview artifact**. When an interviewer asks "tell me about a time you built something with an agent," Cowork scheduled tasks give you **actually-running production examples** with observable success rates over 30 days — not a "here's a Colab I ran once."
- **Startup lens:** Wedges hiding here — **"vertical Cowork skill packs"** (a lawyer-focused, a PM-focused, an SDR-focused set of pre-built scheduled-task templates) sold as $19/mo skill libraries. Also: an **observability layer** ("your scheduled Cowork tasks failed 3× this week — here's why").
- **Insight:** The mental model shift is **from "AI as an accelerator I use" to "AI as a teammate I brief."** Every teammate has a running relationship — you know their reliability curve, their common failure modes, and when to check on them. Start building that model now on Cowork — it will be table-stakes fluency in H2 2026.

→ Cross-link: [`01` §4 Cowork mobile launch](./01-big-lab-moves.md#4-cowork) · [2026-05-22/03 §1 the Opus-orchestrator / Sonnet-worker cost split](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) — pair with scheduled tasks (orchestrator schedules; workers execute).

---

## 2. Prompt engineering, mid-2026 edition — the four rules that actually still matter {#2-prompt-eng-2026}

**What changed:** Anthropic and Simon Willison both published updated 2026 prompt-engineering guides this quarter. The **most important update** is that a lot of 2024–2025 "prompt engineering" no longer buys much: **XML tags, heavy role-play scaffolding, and long chain-of-thought preambles are less necessary** with Fable 5 / GPT-5.6 / Gemini 3.5. What *does* still matter:

**Rule 1 — Start simple, add complexity only when a failure demands it.** Test each addition. If the output is the same, delete the addition. The 2026 base models are strong enough that you often *don't need* the scaffolding.

**Rule 2 — Grant the model permission to say "I don't know."** Add one line: *"If you're not confident about a fact, say so explicitly rather than guessing."* Reduces hallucinations more than any structural change.

**Rule 3 — Put the most important instruction at the very top.** Not buried at line 47. Not after a wall of context. Top of prompt.

**Rule 4 — Give the model something to check itself against.** Expected output shape, a passing test, a screenshot, a rubric. Self-verification is the reliability primitive.

**Bonus (Claude-specific): the six primitives that drive extensibility in Claude Code are `CLAUDE.md`, skills, subagents, slash commands, hooks, and MCP.** If you can't name what each does in one sentence, spend an hour tonight on the docs.

**Sources:**
- [Anthropic — Prompt engineering best practices for 2026](https://claude.com/blog/best-practices-for-prompt-engineering) `[primary]`
- [Anthropic Platform Docs — Prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) `[primary]`
- [Anthropic Platform Docs — Prompt engineering overview](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/overview) `[primary]`
- [Simutecra — Stop Wasting Claude AI: Prompt Guide for Engineers](https://simutecra.com/blogs/prompt-engineering-claude-ai-engineers-guide) `[analysis]`
- [Skakarh — Claude Code Prompts: 25 Proven Templates for AI-Assisted Development (2026)](https://www.skakarh.com/blog/claude-code-prompts) `[analysis]`
- [MarkTechPost — Claude Code Guide 2026: 25 Features with Examples](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[analysis]`
- [Sabita (Medium) — 50 Claude Code Best Practices Every AI Engineer Should Know](https://medium.com/@sabita2025/50-claude-code-best-practices-every-ai-engineer-should-know-6ee3f2fdf669) `[analysis]`

### Why it matters to you

- **Job lens:** In interviews, the *good* signal isn't that you know 20 prompt tricks — it's that you can **explain why you dropped the XML tags** and can point to a **passing test that catches regressions in prompt behavior.** Verify-driven prompting > technique-hoarding.
- **Startup lens:** This is why "prompt engineer" is no longer a job title in 2026. The skill migrated up the stack to **eval design, agent design, and cost-aware routing.** If you're building a product, don't hire a prompt engineer — hire someone who owns evals + skills + observability end-to-end.
- **Insight:** When the models get better, the *techniques* get worse. The **durable skill** isn't any specific trick — it's the **empirical discipline** of "test the addition, keep it only if it helps." Same principle as coding, same principle as science.

→ Cross-link: [2026-05-17/03 Karpathy CLAUDE.md 109K stars](../2026-05-17/03-practical-skills-and-tools.md) — the durable playbook — remains valid; today's updates are subtractive, not additive.

---

## 3. The three cost levers to pull *before* your next AI bill lands {#3-cost-levers}

**Context:** Post-June-15 metering means agent workloads bill at API list rate (see [2026-05-16/01 §1](../2026-05-16/01-big-lab-moves.md#1-agent-metering)). Cowork mobile doubles surface area for accidental spend. Anthropic's Samsung chip is 18–30 months out. **You need cost levers you can pull *now*, not later.**

**Lever 1 — Prompt caching (60–90% input-cost savings on repeat context).**
The single-highest-ROI move in 2026. Any prompt where the *system* + *tools* + *example set* + *retrieved context* is stable across calls (i.e., ~every agentic loop) qualifies. Turn it on. Verify hit rate in your usage logs.

**Lever 2 — Model routing (Opus-orchestrator + Sonnet/Haiku-worker ≈ 40% cheaper).**
The pattern from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost). Orchestrator on the flagship (Opus 4.8 / Fable 5), workers on the tier below (Sonnet 4.6 / Haiku 4.5). Plus the **plan → annotate → "address all notes, don't implement yet"** reliability primitive.

**Lever 3 — Cost tracing on scheduled tasks (before the invoice, not after).**
Cowork scheduled tasks are your **highest-variance spend** because they run without you watching. Wire a `budget_gate` skill: it aborts the task if cumulative token spend crosses a threshold and drafts you an email explaining why. This is trivial to build and the artifact itself becomes a talking point (**"here's how I put a governor on my own agent."**)

**Sources:**
- [Anthropic — Prompt caching](https://platform.claude.com/docs/en/build-with-claude/prompt-caching) `[primary]`
- [2026-05-17/03 Prompt caching playbook (this repo)](../2026-05-17/03-practical-skills-and-tools.md) — original writeup, still current
- [2026-05-22/03 Opus-orchestrator / Sonnet-worker split (this repo)](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) — pairs with §1 here
- [2026-07-09/03 four-price routing table (baseline to refresh with Gemini 3.5 Pro tomorrow)](../2026-07-09/03-practical-skills-and-tools.md) — the artifact to update Friday
- [Artificial Analysis — Pricing benchmarks](https://artificialanalysis.ai/) `[analysis]`

### Why it matters to you

- **Job lens:** "Can you optimize the token bill" is now a **live interview question at Anthropic Solutions, OpenAI FDE, and every AI-first startup**. Come with numbers: "on my personal agent stack I reduced $X/mo to $Y by combining caching (Z%) + routing (W%) + a budget gate." That's the story.
- **Startup lens:** Cost is now the **primary product differentiator** at parity capability. If your MVP costs 3× a competitor's for the same output, you're dead in enterprise procurement — regardless of demo polish. Instrument cost from day one.
- **Insight:** Cost-optimization used to be an afterthought in AI ("compute is cheap enough, ship features"). It is now the discipline that most separates senior from mid-level AI engineers. Practicing it on your *own* usage is the cheapest lab you'll ever run.

→ Cross-link: [`01` §4 Anthropic Compute + Samsung chip = 2028 tailwind](./01-big-lab-moves.md#4-anthropic-carry) · [2026-05-22/03](../2026-05-22/03-practical-skills-and-tools.md).

---

## 4. DeepSeek deprecation — T-8, migrate today (silent-downgrade risk if you don't) {#4-deepseek-deprecation}

**What happens Fri Jul 24 15:59 UTC:** DeepSeek deprecates `deepseek-reasoner` and `deepseek-chat` as of **T-8 days from today**. Migration mapping is **not symmetric** and picking the wrong target model gets you a **silent capability downgrade at the same billing**:

- `deepseek-reasoner` → **`deepseek-v4-flash`** ✅ (correct target)
- `deepseek-reasoner` → `deepseek-v4-pro` ❌ (**wrong** — costs more, reasons *less* on reasoner-shaped tasks; per [2026-07-13/00](../2026-07-13/00-tldr.md))
- `deepseek-chat` → `deepseek-v4-flash` ✅

**The 5-minute audit tonight:**

1. `grep -rn "deepseek-reasoner\|deepseek-chat" .` across every repo, notebook, scheduled job, MCP server, and prod config you own.
2. For each hit, replace with `deepseek-v4-flash` (not `-pro`). Commit the diff with the deadline in the message so future-you can grep it.
3. Run one canonical prompt against `v4-flash` and diff the output vs today's `reasoner` output. If quality is unacceptable on your workload, **route to Sonnet 5 or GPT-5.6 Terra** rather than `v4-pro` — the latter is not a drop-in replacement.
4. If you have anything running on the *unmigrated* endpoints past Jul 24 15:59 UTC, it will 404 and any scheduled job will silently fail.

**Sources:**
- [DeepSeek — Model deprecation announcement (July 2026)](https://api.deepseek.com/docs/deprecation) `[primary]`
- [2026-07-13/00 Monday action flagging the correct target model (this repo)](../2026-07-13/00-tldr.md)

### Why it matters to you

- **Job lens:** Doing a clean deprecation-migration and *documenting it* is the exact skill enterprise-AI hiring managers care about. "Silent capability downgrade" is a phrase interviewers respect — because it names the *specific* failure mode that separates careful practitioners from vibe-coders.
- **Startup lens:** If you're building on DeepSeek for cost reasons, this deprecation is your reminder that **open-weight-adjacent APIs have a policy risk that closed-frontier-lab APIs don't**. Budget for a migration once a quarter and treat every scheduled job as needing a version-pin check.
- **Insight:** The `reasoner` → `v4-flash` mapping is *counterintuitive on purpose* — the vendor renamed the tiering. Whenever a vendor renames tiers, **read the actual model-card benchmarks against your workload before assuming the "obvious" mapping is right**. This is generalizable: it will happen again with the next OpenAI or Anthropic model-family reshuffle.

→ Cross-link: [2026-07-13/00 T-11 flag on this exact migration](../2026-07-13/00-tldr.md).
