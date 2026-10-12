# Practical Skills & Tools — 2026-09-24

Three-tier routing rubric to internalise this week + the four-primitive Claude Code discipline that every 2026 best-practice guide now converges on + the router-artifact extension your GitHub needs by Friday. **Frame: if you spent Q3 learning models, spend Q4 learning *routing across models* — that's where the marginal hour of practice pays back the most.**

Tags: `#claude-code #routing #skills #hooks #subagents #eval #agents`

---

## 1. Three-tier routing rubric — internalise this by Friday {#1-three-tier-routing}

**Why it matters now:** With Opus 5.5 + Sol + Luna (Sept 22), the four frontier labs each field a three-tier family covering the whole cost/capability spectrum. **Nobody can memorise 12 model/tier combinations** — but everyone can memorise a routing rubric and hand off the lookup to a config file. Here's the rubric that fits into working memory:

### The rubric (memorise this)

| Tier | Anthropic | OpenAI | Google | Meta | Use for |
|---|---|---|---|---|---|
| **Clerical** (~$0.10–1/1M) | (Haiku 4.5 continues; no fresh flagship) | **GPT-6 Luna** ($0.10/$0.50) | **Gemini 3.8 Flash** ($0.75/$3.75, doubles Jan 2027) | **Muse Spark 1.3** (~$0.10 blended) | Classification, tagging, extraction, summarisation, high-volume routing |
| **Workhorse** (~$2–4/1M in) | **Opus 5.5** ($4/$20) | **GPT-6 Sol** ($2/$10) | (Gemini 3.8 Pro tier) | (Muse Spark 1.5 Pro tier) | Coding agents, tool-heavy workflows, long-context Q&A, most FDE work |
| **Frontier** (~$10/1M in) | **Fable 5.1** ($10-ish public) + **Mythos 5.1** (restricted) | **GPT-6 Astra** ($10/$50) | (Gemini 4 upcoming) | (Muse Ultra rumoured) | Only when eval demonstrates the extra 5–10pt matters to revenue |

**The routing decision tree:**

```
Is the task classifying/tagging/extracting/summarising/routing?
├─ Yes → Clerical tier. Pick by (a) latency budget, (b) tool needs, (c) cost.
│        Default: GPT-6 Luna ($0.10/$0.50).
│        Latency-sensitive UI: Muse Spark 1.3 (fastest small model).
│        Multimodal in: Gemini 3.8 Flash.
└─ No → Is the task coding, tool-calling, multi-step agentic, or long context?
   ├─ Yes → Workhorse tier.
   │        Default: Opus 5.5 (best agentic reliability + 60% cache-read discount).
   │        Cost-critical / OpenAI-first infra: GPT-6 Sol at half the price.
   │        Only escalate to Frontier if your eval says so.
   └─ No → Is it novel / high-stakes / evaluation-sensitive?
      ├─ Yes → Frontier tier. Prove with eval, log per-request cost.
      └─ No → You misclassified — go back and re-route.
```

### The rubric's hidden discipline

- **Log per-request cost, model, tier, task-type, and eval-score to a single table.** Without this you can't defend a routing decision in a design review; with it, you can show a 40–60% cost delta at unchanged quality — which is what unblocks the promotion / offer.
- **Refresh the eval-suite quarterly.** As new models ship, the rubric shifts. Two rules of thumb: (a) if a workhorse-tier model matches frontier-tier on your eval, drop to workhorse; (b) if a clerical-tier model matches workhorse-tier on your eval, drop to clerical. Most cost savings come from the second rule.
- **Don't optimise for the wrong number.** Cost per token is the visible number; cost per *task-completion-of-quality-X* is the real one. A model that costs 2× but uses half the tokens (Opus 5.5's ~40% total workload savings) is a better deal.

**Sources:**
- [Digital Applied — September 2026 AI Model Releases Tracker](https://www.digitalapplied.com/blog/ai-model-releases-september-2026-tracker) `[analysis]`
- [Local AI Zone — September 2026 AI Model Updates](https://local-ai-zone.github.io/blog/September_2026_AI_Model_Updates.html) `[analysis]`
- [BenchLM — Gemini 3.8 Flash vs Muse Spark 1.3: Benchmarks & Cost](https://benchlm.ai/compare/gemini-3-8-flash-vs-muse-spark-1-3) `[analysis]`
- [LLM Gateway Changelog — Gemini 3.8 Flash, Muse Spark 1.3 & More Models](https://llmgateway.io/changelog/gemini-3-8-flash-muse-spark-new-models) `[aggregator]`

### Why it matters to you

- **Job lens:** **"How do you route across models?"** is now the single most common H2 2026 interview question at FDE / AI-Engineer / MLE screens. If you can walk through this decision tree from memory + show the router artifact ([`§3`](#3-router-extension)) + defend one specific routing decision with logged data, **you're in the top ~5% of applicants.** The rubric itself is the artifact.
- **Startup lens:** A routing rubric that stays current is worth productising — see [`02` §1 Sora migration playbook](./02-new-emerging.md#1-sora-api-shutdown) for the same pattern applied to video-gen. The startup wedge: **"routing-as-a-service with a public eval leaderboard tied to *your customer's* traffic patterns."**
- **Insight:** The rubric will need a **fourth tier by Q1 2027**: a **"local-inference / edge / open-weights"** tier as Muse Spark open-weights lands + Apple Foundation Models mature + Llama continues shipping. Start planning the eval-suite migration now — the local tier's eval is *different* (measure over 30-day drift, not one-shot performance).

→ Cross-link: [2026-09-10/03 §3 the router artifact](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) · [`§3` router extension](#3-router-extension).

---

## 2. Claude Code four-primitive discipline — the community consensus {#2-four-primitive-discipline}

**Why it matters now:** As of Sept 2026, every serious Claude Code best-practice guide (MarkTechPost, SmartScope, Totalum, Firecrawl, MCP.directory) converges on the same **four primitives + four decision rules**. If your Claude Code project embeds rules in inline prompts, you're doing 2025-era Claude Code and losing to team members who've internalised the discipline.

### The four primitives

1. **CLAUDE.md** — **always-on project guidance.** Short, opinionated, project-level. Version-controlled. Loaded into every session automatically. **Rule:** keep it under 200 lines; if it grows, move content into a Skill.
2. **Skills** — **long-lived domain expertise loaded when relevant.** Each Skill is a folder with a `SKILL.md` (frontmatter: name, description, trigger; body: instructions + example files). Loaded *conditionally* by Claude when the task matches the description. **Rule:** put "here's how we handle migrations / accessibility / auth" in a Skill, not CLAUDE.md.
3. **Subagents** — **forked Claude instances with their own context window.** Used to isolate work that would otherwise pollute the main context. **Rule:** prefer *less* parallelism — every subagent re-reads CLAUDE.md and preloaded Skills from scratch and pays that entry cost; parallel is worth it only when tasks are *truly* independent (5 blog posts on 5 topics: yes; 5 changes to the same file: no).
4. **Hooks** — **deterministic shell scripts that fire on lifecycle events.** Enforce rules at the system level (pre-commit lint, post-tool-use security check, pre-write file-safety gate). **Rule:** if a rule *must* be enforced (safety-critical, correctness-critical), use a Hook — prompts alone rely on the model interpreting the instruction, Hooks execute deterministic code.

### The four decision rules (memorise)

- **Enforce a rule?** → **Hook** or permissions.
- **Long-lived domain expertise?** → **Skill.**
- **Isolate work / delegation boundary?** → **Subagent.**
- **Always-on project guidance?** → **CLAUDE.md** (kept short).

### The failure modes to avoid

- **Skill-fatigue:** teams over-produce Skills; the model triggers them on false positives; performance degrades. **Fix:** audit Skills quarterly; delete anything not triggered in the last 30 days; refine descriptions.
- **CLAUDE.md bloat:** everything gets dumped into CLAUDE.md because it's "always on." **Fix:** move anything longer than 5 lines into a Skill.
- **Subagent-happy anti-pattern:** spawning subagents for every task because parallel *feels* faster. **Fix:** measure end-to-end wall-clock; parallel with cold-start costs is often slower than sequential warm-context.
- **Hook fatigue:** every rule becomes a hook; developer flow slows to a crawl. **Fix:** reserve Hooks for safety + correctness; use prompts / Skills for style + convention.

**Sources:**
- [MarkTechPost — Claude Code Guide 2026: 25 Features with Examples + Demo](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[secondary]`
- [SmartScope — Claude Code Advanced Best Practices: 11 Practical Techniques for Hooks, Subagents & Context Management (2026)](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[analysis]`
- [Totalum — Claude Code Skills in 2026: The Complete Guide (vs Hooks, vs Subagents, vs MCP)](https://www.totalum.app/blog/claude-code-skills-totalum) `[analysis]`
- [MCP.directory — Claude Code Best Practices: From Vibe Coding to Agentic Engineering (2026)](https://mcp.directory/blog/claude-code-best-practices) `[analysis]`
- [Firecrawl — 14 Best Claude Code Skills for Developers in 2026](https://www.firecrawl.dev/blog/best-claude-code-skills) `[analysis]`
- [AI Nexus Daily — Claude Code Hooks vs Skills vs Subagents: Three Ways to Extend the Agent, and When Each Backfires](https://ainexusdaily.vercel.app/article/2026-09-13-claude-code-hooks-vs-skills-vs-subagents-three-ways-to-extend-the-agent-and-when) `[analysis]`

### Why it matters to you

- **Job lens:** Every FDE / DX-Engineer / Solutions-Engineer role at Anthropic (and increasingly at OpenAI, given the Codex-Claude-Code convergence) will ask about this discipline. **Practise walking through a project you've built and pointing at which rules are Hooks, which are Skills, which are Subagents, which are CLAUDE.md.** That specific narration is what separates candidates who *use* Claude Code from candidates who *understand* it.
- **Startup lens:** The four-primitive discipline generalises beyond Claude — every agentic-coding tool (Cursor, Cline, Aider, OpenCode, Windsurf) needs equivalents. **Wedge:** a *portable* skills / hooks / subagents / project-guidance layer that works across agentic IDEs. Non-trivial engineering; large TAM.
- **Insight:** The four-primitive discipline is a **1:1 mirror of the classical DevOps discipline** (config as code, policy as code, environment as code, deployment as code). This is why it converged so fast — the industry has ~15 years of DevOps intuition to reuse. The next Claude Code discipline that will consolidate is **observability + eval-in-CI** — expect that to converge by Q1 2027.

→ Cross-link: [2026-09-10/03 §2 the 2026 Claude Code decision tree](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree) (earlier version of this rubric).

---

## 3. The router artifact extension — ship this by Friday {#3-router-extension}

**What to build:** Extend the router shim from [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) to route across the **three-tier × four-lab** matrix, with a **fourth eval case** for **novel-discovery-style workloads** (inspired by the ART method).

### The spec (aim for 60 lines of Python, 5 eval cases, published to GitHub with a README + demo GIF)

**Inputs:**
- `task_type ∈ {"clerical", "workhorse", "frontier"}`
- `lab_preference ∈ {"anthropic", "openai", "google", "meta", "auto"}`
- `max_cost_per_task ∈ float` (dollars)
- `latency_budget_ms ∈ int`

**Routing logic:**
- If `lab_preference == "auto"`: pick lab by (cheapest that satisfies eval-min-score for task).
- Else: pick the tier's model at that lab.
- Fall back one tier up if eval-min-score not met on a test case; log the fallback.

**The 5 eval cases:**
1. **Extraction** — pull structured JSON from an unstructured email.
2. **Coding** — implement a small function against a test suite.
3. **Long-agentic** — 5-step tool-use task (web search → parse → summarise → structured output → verify).
4. **Multimodal** (optional if you don't want to pay for image tokens): describe a chart's insight.
5. **NEW — Novel-discovery-style** — given a small database + a target pattern, iterate over candidates and rank by domain-specific score. Inspired by ART. This is the case that reveals whether the model has the *judgement + patience* to be worth its price on scientific / research workloads.

**What to log per request:**
- `model`, `tier`, `input_tokens`, `output_tokens`, `cache_hits`, `cost_usd`, `latency_ms`, `eval_score`, `fallbacks`

**What the README needs (in order of importance):**
1. **A price/quality frontier plot** — X = cost per task, Y = eval score, one point per model. Shows visually where the routing bets are.
2. **The routing decision tree** (copy from [`§1`](#1-three-tier-routing) above).
3. **A "what I learned" section** — 3–5 specific facts you couldn't have known without running the eval. This is what an interviewer will actually read.
4. **A "next steps" section** — enumerate the eval cases you'd add next (video-gen migration case? Local-inference tier? Fine-tuned specialist?). Signals judgement.

### Why ship it this week specifically

- The Sept 22 price cuts + the ART method's high visibility mean **this week is the peak signal moment**. A router artifact + eval published this week is worth 3× the same artifact published in October — because it appears at the moment recruiters + hiring managers are *actively re-searching* their networks for candidates who can talk about the new price tiers.
- **Cadence discipline:** even if the artifact is v0.1, ship it. You can iterate publicly. Silent projects don't get you interviews; imperfect public projects do.

**Sources:**
- Extends [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) — original spec.
- [Axial Search — The State of the ML Engineering Job Market in 2026](https://axialsearch.com/insights/ml-engineering-jobs) `[analysis]` — validates that "router / eval" is what's being hired.
- [Axial Search — Inside the AI Engineering Job Market: 43,500 Postings Analyzed](https://axialsearch.com/insights/ai-engineering-jobs) `[analysis]` — same.

### Why it matters to you

- **Job lens:** This is your **one Thursday-to-Sunday project** — the ROI curve is stacked heavily toward this weekend. If you do nothing else this week, do this.
- **Startup lens:** The eval-suite portion is your **beginning of a defensible "eval + routing" IP** — you own the eval cases, you own the results, you can turn it into content (a "state of frontier models" post), you can turn the content into inbound (VCs looking for "founder who really understands the frontier"), you can turn the inbound into a Seed round.
- **Insight:** **Publishing the *methodology* is worth more than publishing the *conclusions*.** In 30 days, the conclusions will be obsolete (someone will ship a new model); the methodology will still be replicable. Write for methodology-first, always.

→ Cross-link: [`§1` three-tier routing rubric](#1-three-tier-routing) · [`05` §1 hiring map](./05-career-and-startup.md#1-hiring-map) · [`04` §2 ART method as a research pattern](./04-research-progress.md#2-art-method).

---

## 4. The Sora migration weekend project (if you have Sora dependencies) {#4-sora-migration}

**What to do:** If you have *any* Sora-dependent code — even a hobby project — do the migration this weekend and publish the writeup. **The Sept 24 shutdown is a forcing function** that gives you a portfolio artifact with a real-world deadline.

### The playbook

1. **Inventory:** list every place your code calls the Sora API. Grep for `sora-2`, `sora-2-pro`.
2. **Pick a replacement:** default recommendation is **Runway Gen-4** for feature parity, **Kling 2.0** for cost, **Google Veo 3** if you're already in the Google stack.
3. **Wrap in an abstraction:** create a `video_gen.py` (or equivalent) that exposes a unified interface — `generate(prompt, duration, style, seed) → bytes`. This makes the *next* migration trivial.
4. **Backfill an eval:** ship 5 prompts + expected qualitative properties (motion smoothness, prompt adherence, no artefacts). Run against the old + new provider; publish the diff.
5. **Publish:** 800-word blog post titled "Migrating off Sora in a Weekend." Include the abstraction pattern (portable to any future deprecation).

**Sources:**
- Extends [`02` §1 Sora API shutdown](./02-new-emerging.md#1-sora-api-shutdown).

### Why it matters to you

- **Job lens:** *Every* FDE / Solutions-Engineer interview covers "walk me through a time you handled a deprecation." A published migration writeup with a real deadline is the ideal answer.
- **Startup lens:** The abstraction layer you build is the seed of the [video-gen abstraction layer](./02-new-emerging.md#1-sora-api-shutdown) wedge — LiteLLM-for-video.
- **Insight:** **Deprecations are portfolio gold** — they're rare, they have hard deadlines, and they demonstrate the "operate in production" skill that pure greenfield projects can't. Watch for the *next* frontier-lab deprecation (Gemini 1.x endpoints are due Q1 2027; expect an OpenAI GPT-4 series sunset by Q2 2027) and be ready to write the same weekend post.

→ Cross-link: [`02` §1 Sora API shutdown](./02-new-emerging.md#1-sora-api-shutdown).
