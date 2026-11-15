# Practical Skills & Tools — 2026-07-09

Three concrete things to run *tonight* — a four-price routing table you can operationalize in one hour, GPT-5.6's caching contract that changes your agent-cost model, and the Claude Code MCP-and-layers stack that the practitioner community has now converged on.

Tags: `#practical #routing #caching #mcp #claude-code #cost`

---

## 1. The four-price routing table — tonight's tool {#1-cheap-tier-routing}

**What to do:** As of today, there are **four models within one factor of pricing** that each *win* on some subset of tasks. Ship a routing decision — even if it's a first draft — this week.

### The prices, straight (per 1M tokens, input / output)

| Model | Input | Output | Context / notes | Best-known win |
|---|---:|---:|---|---|
| **OpenAI GPT-5.6 Sol** | $5.00 | $30.00 | Predictable caching; on Cerebras at up to 750 tok/s | Highest-tier reasoning / agentic |
| **Anthropic Sonnet 5 (intro to Aug 31)** | $2.00 | $10.00 | 62%+ tool-use eval; jumps to $3 / $15 Sept 1 | Best per-$ mid-tier on coding + tool use |
| **OpenAI GPT-5.6 Terra** | $2.50 | $15.00 | Roughly GPT-5.5 quality at half the price | Balanced general use |
| **xAI Grok 4.5** | $2.00 | $6.00 | Cursor-trained; 4.2× fewer tokens/task on SWE-Bench Pro | Cheapest per-*completed-task* on coding |
| **OpenAI GPT-5.6 Luna** | $1.00 | $6.00 | Smallest; classification / extraction workloads | Cheapest for high-volume simple tasks |
| **Z.ai GLM-5.2 (self-hosted, MIT)** | $0 marginal + infra | $0 marginal + infra | 62.1% on SWE-Bench Pro | Best price floor + no data-egress |

**How to route (first draft):**

1. **Classification / extraction / short chat:** → **Luna** or **GLM-5.2**.
2. **Coding + tool use in a bounded loop:** → **Grok 4.5** (if compliance allows) or **Sonnet 5** (if you want Anthropic-stack telemetry).
3. **Long-horizon agent / research / planning:** → **Sol** or **Opus 4.8** (or **Sonnet 5** as a per-$ compromise).
4. **Regulated verticals (finance / healthcare / legal):** stay on **Sonnet 5 / Opus 4.8 / GPT-5.6 Sol** — Grok 4.5 has no system card ([`01` §2](./01-big-lab-moves.md#2-grok-4-5)); GLM-5.2 has data-residency questions.

### The one-hour exercise

Pick one Terminal-bench task ([`04` §2](./04-research-progress.md#2-terminal-bench)) or one Karpathy-style repo-refactor task. Run it through **Grok 4.5, Sonnet 5, GPT-5.6 Terra**. Log:

- Wall-clock
- **Total tokens (input + output)**
- **$ cost** (from the table above)
- **Pass / fail**
- **Failure mode** (if failed)

Publish the 3-row table as a public gist or repo. **This is your interview artifact.** Cross-link it into [APPLICATIONS.md](../APPLICATIONS.md).

**Sources:**
- [OpenAI Help Center — GPT-5.6 Sol / Terra / Luna pricing preview](https://help.openai.com/en/articles/20001325-a-preview-of-gpt-56-sol-terra-and-luna) `[primary]`
- [Anthropic — Introducing Claude Sonnet 5](https://www.anthropic.com/news/claude-sonnet-5) `[primary]`
- [TechCrunch — SpaceXAI releases Grok 4.5](https://techcrunch.com/2026/07/08/spacexai-releases-grok-4-5-which-elon-describes-as-an-opus-class-model/) `[secondary]`
- [Interconnects — GLM-5.2 is the step change for open agents](https://www.interconnects.ai/p/glm-52-is-the-step-change-for-open) `[analysis]`
- [eesel — GPT-5.6 pricing: Sol, Terra, and Luna costs explained](https://www.eesel.ai/blog/gpt-5-6-pricing) `[analysis]`

### Why it matters to you

- **Job lens:** **Grok 4.5's 4.2× token-efficiency claim is the single interview-answer to memorize this week.** If asked "how would you make agents cheaper," you can now cite a specific number: "on SWE-Bench Pro, Grok 4.5 uses 15,954 output tokens per resolved task vs 67,020 for Opus 4.8 max — a 4.2× gap that translates directly to a 4.2× cost reduction on that workload." Numbers plus a source beat any abstract argument.
- **Startup lens:** For any AI-app founder, the **caching contract in GPT-5.6** ([§2 below](#2-predictable-caching)) and the **intro window on Sonnet 5** ([`01` §3](./01-big-lab-moves.md#3-anthropic-stack)) create an **8-week arbitrage** on unit economics. Any product you launch by Aug 31 that has a **reusable system prompt** can be priced permanently against the intro rate — because your load-testing was done at that rate. Aug 31 is a *product deadline*, not a pricing deadline.
- **Insight:** **Model choice is now a systems-design problem, not a research problem.** The models are close enough on capability that the differentiator is the *plumbing* — caching, latency, telemetry, verification. Practitioners who can design that plumbing are the practitioners who get hired. Stop obsessing over which model is "smartest"; obsess over which routing decision produces the lowest cost per completed task.

→ Cross-link: [`01` §1 GPT-5.6 pricing](./01-big-lab-moves.md#1-gpt-5-6) · [`04` §2 Terminal-bench for verification](./04-research-progress.md#2-terminal-bench) · [`05` §2 cost-per-task as the interview answer](./05-career-and-startup.md#2-cost-per-task-is-the-answer).

---

## 2. GPT-5.6's predictable-caching contract — rebuild your agent's cost model {#2-predictable-caching}

**What changed:** GPT-5.6 shipped a **first-class caching contract** — not the old best-effort caching:

- **Explicit cache breakpoints** — you place them in the prompt; you know where the cache boundary is.
- **30-minute minimum TTL** — a cache read within 30 minutes is guaranteed.
- **Cache writes billed at 1.25× the uncached input rate.**
- **Cache reads at the standard 90% cached-input discount.**

### The rebuilt cost model (worked example)

Say you have an agent with a **20,000-token system prompt** that runs **10 turns per user session**, and users bounce a task around **~5 times in 30 minutes.**

- **Uncached (old world):** 5 sessions × 10 turns × 20K input × $5/1M = **$5.00** for that user's system-prompt cost alone (Sol pricing).
- **Cached (new world):** first turn writes at 1.25× → **$0.125**; the other 49 turns read at 10% → 49 × $0.10 = **$4.90 × 0.10 = $0.49**. **Total: $0.62** — an **8× cost reduction on system-prompt cost per user session.**

Multiply that by your daily active users. This is the single-biggest cost lever that landed today.

**Sources:**
- [OpenAI Help Center — GPT-5.6 caching mechanics](https://help.openai.com/en/articles/20001325-a-preview-of-gpt-56-sol-terra-and-luna) `[primary]`
- [Anthropic prompt caching docs](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching) `[primary]`
- [Finout — GPT-5.6 Pricing 2026: Sol, Terra and Luna Tiers Explained](https://www.finout.io/blog/gpt-5.6-pricing-2026-sol-terra-and-luna-tiers-explained) `[analysis]`

### Why it matters to you

- **Job lens:** **"Explain your prompt-caching architecture"** is now a real interview question, on par with "explain your database schema." Practice the answer: cache-breakpoint placement, TTL strategy, cache-miss handling. Anthropic has had this for a year ([2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md)); OpenAI now offers the same contract; **the practitioner who's designed around both is the differentiated one.**
- **Startup lens:** Any agent product with a **long, stable system prompt + many short user turns** just got 8× cheaper. Recompute your unit economics *this week* — the market will assume you have. Your pitch deck's "cost per user session" number should reflect the July 9 caching contract, not a pre-July mental model.
- **Insight:** Caching is the **first-order economics primitive** for agents in 2026. Speed, memory, and prompt engineering all trail it. Master the caching model *before* you optimize any other axis of your agent.

→ Cross-link: [2026-05-17 §3 prompt caching playbook (Anthropic side)](../2026-05-17/03-practical-skills-and-tools.md) · [`05` §2 cost-per-task as the answer](./05-career-and-startup.md#2-cost-per-task-is-the-answer).

---

## 3. The 2026 Claude Code stack — six layers, one rule {#3-claude-code-stack}

**The community-converged layered model for Claude Code — as it stands July 2026:**

| Layer | Owns | Use when |
|---|---|---|
| **CLAUDE.md** | Stable project + user context | You want *every* session to know something |
| **Output styles** | Response behavior via system prompt | You want tone or format changed globally |
| **Skills** | Reusable procedures + helper files | There is real domain logic worth naming |
| **Slash commands** | Explicit user-triggered workflows | The user needs to *invoke* a prompt template |
| **Hooks** | Deterministic lifecycle policy | You want to enforce a rule with *code*, not prompt |
| **Subagents** | Isolated work in a fresh context window | The job is big enough to protect the parent context |
| **Plugins** | Distribution of the above | You want to share a set of extensions |
| **MCP servers** | External tools, resources, prompts, durable systems | Something outside the model needs to be a first-class citizen |

**The rule (the practitioner-community consensus):** *use the smallest layer that owns the job.*

### The starting configuration (from Karpathy's + Anthropic's + Simon Willison's converged advice)

1. **`CLAUDE.md`** — 4 rules only: (a) run tests before claiming done, (b) don't touch `secrets/`, (c) prefer editing existing files, (d) verify against the actual UI when it's a UI change.
2. **One skill** for whatever repeat workflow you have — start with `verify` (drive the change end-to-end).
3. **One hook** — a `pre-commit` bash hook that runs the tests. Deterministic.
4. **One subagent** — `Explore` (or whatever your project needs) for read-only search that would blow up the parent context.
5. **One MCP server** — the one that owns your external system of record (Postgres, Notion, GitHub, whatever).

If you're still on a "one giant CLAUDE.md + everything in slash commands" pattern (which was dominant in Q1), **you're now behind the community.**

**Sources:**
- [Claude Platform Docs — Prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) `[primary]`
- [Anthropic — Claude Code overview](https://platform.claude.com/docs/en/about-claude/models/overview) `[primary]`
- [MarkTechPost — Claude Code Guide 2026: 25 Features with Examples + Demo](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[analysis]`
- [emerging.ai — Claude Changed: The July 2026 Way to Use it](https://emergingai.substack.com/p/claude-changed-the-july-2026-way) `[analysis]`
- [iwoszapar — Claude Code Best Practices: 8 Rules I Learned the Hard Way](https://www.iwoszapar.com/p/claude-code-best-practices) `[analysis]`
- [Claude Directory — Best Claude Code setups for AI & agent development (July 2026)](https://www.claudedirectory.org/for/ai-agent-development) `[aggregator]`
- [Piebald-AI/claude-code-system-prompts](https://github.com/Piebald-AI/claude-code-system-prompts) `[primary]` (community-extracted, kept current)
- [shanraisshan/claude-code-best-practice](https://github.com/shanraisshan/claude-code-best-practice) `[aggregator]`

### Why it matters to you

- **Job lens:** **Your Claude Code artifact needs at least one of each layer** — CLAUDE.md, skill, hook, subagent, MCP server — visible in a public repo, before you claim "I use Claude Code" in an interview. That's the demonstrable version of "I know the stack." Publish a demo repo this weekend.
- **Startup lens:** The **MCP server layer is the durable moat** for any AI-app founder. Your model choice will change every quarter; your MCP surface — the tools you expose to whatever model is on top — is your product. **Ship a public MCP server this week** ([ME.md](../ME.md) portfolio artifact) — 3 tools, a 5-case eval, README, demo GIF. This is the single most portable skill an AI-Integration-Engineer job or a startup founder can demonstrate.
- **Insight:** The Claude Code architecture is a direct copy of **UNIX composition principles applied to model calls** — small pieces, one job each, composed by the smallest surface. If you understand *why* this stack works, you understand the shape of every serious agent framework that will land next year. Study the *architecture* even if you don't use Claude Code.

→ Cross-link: [ME.md — public MCP server portfolio artifact](../ME.md) · [2026-05-21 §5 Claude Code orchestration stack](../2026-05-21/03-practical-skills-and-tools.md) · [`04` §1 MAS-Orchestra for multi-agent composition](./04-research-progress.md#1-mas-orchestra).
