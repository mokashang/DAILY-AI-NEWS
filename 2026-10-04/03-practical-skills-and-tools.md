# Practical Skills & Tools — 2026-10-04

Three artifacts to ship this weekend, in order of ROI: **(1) your first Claude Code mod — a secrets-redaction mod — on GitHub by Sunday**; **(2) the updated 5-primitive Claude Code decision tree, as a diagram on your LinkedIn/blog**; **(3) a 60-line GPT-6.1 Sol migration shim + a 5-case regression eval for one agent in your portfolio**. Each is defensible in a Monday interview; each takes 90–180 minutes.

Tags: `#claude-code #mods #skills #decision-tree #openai #gpt-6 #sol #migration #router #evals #temporal #supabase`

---

## 1. Ship your first Claude Code mod — the secrets-redaction mod {#1-mods}

**What it is:** A **small TypeScript module** that runs inside Claude Code and intercepts internal events (prompts, tool calls, UI renders). Mods ship inside plugins; install path = `claude plugin install <mod-name>`. They run with the **same local access as Claude Code** — not sandboxed. The full capability list (from Anthropic's Oct 1 announcement):

- Rewrite prompts before they reach the model
- Block or retry tool calls
- Approve or deny permission requests
- Redact secrets from tool output
- Replace or edit UI elements
- Add new features

**The 90-minute weekend artifact — a secrets-redaction mod:**

```ts
// claude-mod-redact-secrets/index.ts
import { defineMod } from "@anthropic/claude-code-mods";

const SECRET_PATTERNS: [RegExp, string][] = [
  [/sk-[A-Za-z0-9]{32,}/g, "[REDACTED_OPENAI_KEY]"],
  [/sk-ant-[A-Za-z0-9-]{40,}/g, "[REDACTED_ANTHROPIC_KEY]"],
  [/AKIA[0-9A-Z]{16}/g, "[REDACTED_AWS_KEY]"],
  [/ghp_[A-Za-z0-9]{36}/g, "[REDACTED_GITHUB_PAT]"],
  [/-----BEGIN [A-Z ]+PRIVATE KEY-----[\s\S]+?-----END [A-Z ]+PRIVATE KEY-----/g, "[REDACTED_PRIVATE_KEY]"],
];

function redact(text: string): string {
  return SECRET_PATTERNS.reduce((acc, [pat, repl]) => acc.replace(pat, repl), text);
}

export default defineMod({
  name: "redact-secrets",
  version: "0.1.0",
  description: "Redacts common secret patterns from tool output before the model sees them.",

  // Intercept tool-call RESULTS (after Bash/Read/etc. runs, before the model reads it)
  async onToolResult(event) {
    if (typeof event.result?.content === "string") {
      event.result.content = redact(event.result.content);
    }
    return event;
  },

  // Also intercept prompts the user types — paste a secret, it never leaves this machine in context
  async onPrompt(event) {
    event.prompt = redact(event.prompt);
    return event;
  },
});
```

**Package it:** `plugin.json` with `{"name": "redact-secrets", "entry": "index.ts", "scope": ["pre_tool_result", "pre_prompt"]}`.

**Ship checklist (Saturday afternoon):**

1. Repo on GitHub: `yourhandle/claude-mod-redact-secrets` (MIT license).
2. README: what it does, how to install, limitations (regex-based not entropy-based; add OSS entropy-scan as a v0.2).
3. Three test cases — pastebin an OpenAI key, run a `Bash` tool that cats a `.env`, run a `Read` on a private key — show redaction in each.
4. Short demo GIF (asciinema → gif).
5. Submit to the Claude directory for discovery.
6. LinkedIn post (400 words): "Why I built this + what Claude Code mods unlock + 3 mods I'll build next."

**Three next mods to queue (declare on your LinkedIn post, build over the next 3 weeks):**

- **cost-router mod** — intercepts `onModelRequest`, re-routes between Claude Fable 5.1 / Opus 5.5 / GPT-6.1 Sol based on task type + logs per-task cost (ties your Sept 10 router artifact in).
- **deterministic-replay mod** — captures (prompt, tool-results, model-response) tuples; `--replay` flag re-runs with saved tool outputs for reliable eval.
- **red-team-fuzzer mod** — injects canonical prompt-injection payloads into tool results during dev-mode runs; logs if the model gets diverted.

**Sources:**
- [Anthropic — Claude Code mods announcement](https://x.com/AGTPinsights/status/2105768033419743253) `[primary]`
- [Post-Cutoff — Mods for Claude Code](https://postcutoff.com/e/2026-10-01-claude-code-mods/) `[secondary]`
- [Runtimewire — Mods rewrite prompts + approve tool permissions](https://runtimewire.com/article/anthropic-claude-code-mods-typescript-permissions) `[secondary]`
- [SuperpowerDaily — Mods that can rewrite prompts](https://superpowerdaily.com/posts/anthropic-adds-claude-code-mods-that-can-rewrite-prompts-and-replace-built-in-features) `[aggregator]`

### Why it matters to you

- **Job lens:** Mods are **the single-best weekend artifact you can ship this quarter.** It's defensible in every FDE / Solutions / AI Engineer interview — mods demonstrate (a) you understand the agent's internal event bus, (b) you can design permission boundaries, (c) you write TypeScript to a production bar. Attach the mod repo link to your resume + LinkedIn header this week.
- **Startup lens:** The "**first killer mod**" slot is open. Pick one of the next-three (cost-router, deterministic-replay, red-team-fuzzer) and own it. First one to 1,000 installs is a GTM anchor for an enterprise mod-pack company inside 6 months.
- **Insight:** The mod is the **only Claude Code primitive that can change what the agent IS** (vs. what it knows or how it's constrained). Treat it that way — mod design is agent design, not scripting.

→ Cross-link: [`01` §3 mods announcement](./01-big-lab-moves.md#3-claude-code-mods) · [2026-09-10/03 §2 the four-primitive decision tree](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree).

---

## 2. The 5-primitive Claude Code decision tree (updated for mods) {#2-decision-tree-updated}

**The map, updated Oct 2026:**

| Primitive | What it changes | Deterministic? | Shared with team? | Install path |
|---|---|---|---|---|
| **Hooks** | Enforcement at tool boundaries (approve/deny/transform) | Yes — no model call | Yes (settings.json / repo-level) | Repo + settings |
| **Skills** | Contextual knowledge, loaded JIT when the task matches | No (model-mediated) | Yes (`.claude/skills/`) | Repo + plugin |
| **Subagents** | Delegation boundary — independent context, scoped tools | No (model-mediated) | Yes (`.claude/agents/`) | Repo + plugin |
| **CLAUDE.md** | Always-on project guidance (loaded on every turn) | No (model-mediated) | Yes (repo-level) | Repo file |
| **Mods** 🆕 | **The agent itself** — intercepts/rewrites events | **Depends on the mod** | Yes (plugin via Claude directory) | `claude plugin install` |

**The decision tree (what to use when):**

```
Problem?
├─ "The agent did something I don't want it to do, at a specific boundary (ran rm -rf,
│   leaked a secret, called a prod API)." → HOOK (deterministic, no model, no bypass)
│
├─ "The agent doesn't know enough about THIS codebase / domain / API." → SKILL
│   (loaded JIT when the context matches, doesn't bloat every turn)
│
├─ "The task is big enough that I want a sub-task with its own context and tools,
│   and I want the parent agent not to see the sub-task's internal mess." → SUBAGENT
│
├─ "I want a rule the agent should always follow for this project
│   (naming conventions, which libraries, which coding style)." → CLAUDE.md
│
└─ "I want to change HOW CLAUDE CODE ITSELF WORKS — the event flow, the UI,
    the tool-call lifecycle, the model-request pipeline." → MOD
```

**Common wrong defaults to catch (every grad student I know has at least one of these):**

- "I put the API-key-redaction logic in CLAUDE.md" → **Wrong primitive.** CLAUDE.md is advisory; the model can ignore it. Use a **mod** or a **hook** (deterministic).
- "I put the 'always run tests before pushing' rule in a subagent prompt" → **Wrong primitive.** Use a **hook** on `post_tool_use` for `git push`.
- "I made a subagent for 'knowledge about our Postgres schema'" → **Wrong primitive.** Use a **skill** (loaded JIT when SQL is in context).
- "I made a hook that calls the model to decide if a tool should run" → **Wrong primitive.** You want a **mod** or a **subagent** (model-mediated); hooks should be deterministic.

**Weekend 60-min deliverable:**

Draw this as a **diagram** (Mermaid works; or free-draw in Excalidraw / tldraw / draw.io). Post it on LinkedIn/your blog. This is the single most-shared Claude Code artifact of October 2026 that doesn't exist yet.

**Sources:**
- [Anthropic — Mods announcement](https://x.com/AGTPinsights/status/2105768033419743253) `[primary]`
- [Daily AI Digest — How to use the new mods](https://buttondown.com/dailyaidigest/archive/dad-claude-code-becomes-customizable-how-to-use/) `[aggregator]`
- Internal cross-link: [2026-09-10/03 §2 — the four-primitive version](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree) (what you're updating)

### Why it matters to you

- **Job lens:** A 1-page diagram + 400-word post explaining each primitive's distinct job is a **portable interview answer** that bridges the "what's new in Claude Code" question to "how do you reason about agent architecture." Have the diagram open on your laptop during interviews.
- **Startup lens:** Diagram → tutorial → mini-course is the standard 3-step for building a devrel following that becomes customer flow for a mod-pack / enterprise-Claude-services startup. If you're not planning to monetize, cross-link to a sign-up for a free monthly mod of your own = passive distribution.
- **Insight:** Primitive sprawl is **the sign the ecosystem is maturing**, not fragmenting. Each primitive maps to a distinct engineering concept (enforcement, knowledge, delegation, convention, meta-programming). Agents that lack a clean separation of these are harder to reason about — which is exactly what the H2 2026 interview loops will probe.

→ Cross-link: [`01` §3 mods](./01-big-lab-moves.md#3-claude-code-mods) · [2026-05-21/03 §1 the orchestration stack](../2026-05-21/03-practical-skills-and-tools.md).

---

## 3. GPT-6.1 Sol migration playbook — 60-line shim + 5-case regression eval {#3-sol-migration}

**What changed:** GPT-6.1 Sol replaces GPT-6.1 Astra (cancelled) at **1/5 the input + output token prices**. Error rate dropped from 11.4% to 7.7%. **Agents API is in public beta with computer use**; **Decisions API in limited preview**. Codex is 8× faster token generation, 6× in the API.

**Why migrate now:** You're paying 5× what you need to on any Astra-targeted code. If you have an agent in prod, your bill drops ~80% on the OpenAI-leg of a multi-provider router with ~zero quality cost **on evaluated workflows** (the 5-case eval is how you *prove* the "zero" claim).

**The 60-line shim (TypeScript):**

```ts
// gpt-6-sol-shim.ts — swap this in as your OpenAI client wrapper
import OpenAI from "openai";

type Lane = "cheap" | "default" | "high-stakes" | "coding";

const MODEL_FOR_LANE: Record<Lane, string> = {
  cheap: "gpt-6.1-sol",         // 1/5 the price, 7.7% err
  default: "gpt-6.1-sol",       // migrated from gpt-6.1 (which was gpt-6 before DevDay)
  "high-stakes": "gpt-6-astra", // still available; use for the ~5% of calls where it matters
  coding: "gpt-6.1-sol",        // sol has 8x codex throughput — use unless proven weaker
};

const PRICE_PER_1M = { // dollars per 1M tokens; keep this in a .json you refresh weekly
  "gpt-6.1-sol": { in: 1.00, out: 5.00 },  // placeholder — replace from https://openai.com/pricing
  "gpt-6-astra": { in: 5.00, out: 25.00 }, // 5x sol per DevDay
};

const client = new OpenAI();

export async function run(lane: Lane, prompt: string, maxOut = 2000) {
  const model = MODEL_FOR_LANE[lane];
  const t0 = Date.now();
  const resp = await client.responses.create({ model, input: prompt, max_output_tokens: maxOut });
  const dt = Date.now() - t0;

  const { input_tokens: ti, output_tokens: to } = resp.usage;
  const { in: pi, out: po } = PRICE_PER_1M[model];
  const costUsd = (ti * pi + to * po) / 1_000_000;

  console.log(JSON.stringify({ lane, model, ti, to, ms: dt, costUsd }));
  return resp;
}
```

**The 5-case regression eval:**

| # | Prompt type | Expected (Astra) | Pass criteria for Sol |
|---|---|---|---|
| 1 | Short Python refactor (~50 LOC) | Correct, tests pass | Tests pass, diff ≤ 1.3× Astra size |
| 2 | Long-context summary (~50K tokens in) | Hits key facts (10-point rubric) | Score ≥ 90% of Astra |
| 3 | Tool-call sequence (3-step: fetch → parse → write) | Correct tool order, no retries | Same |
| 4 | Adversarial prompt-injection (hidden instructions in a webpage) | Refuses / asks user | Same or better |
| 5 | Open-ended planning (break a feature into tasks) | Produces 5–9 ordered tasks | Same shape; manual quality rubric ≥ 90% |

**Run both models, log per-case cost + latency + quality score** in a Google Sheet. Publish the sheet. That's your evidence this works on *your* traffic.

**Add Temporal around step 3 of the eval** (the tool-call sequence) — wrap the sequence in a Temporal workflow with explicit retry policy. That makes the artifact a **Temporal + GPT-6.1 Sol + Claude** demo, which is exactly the "modern AI stack" interview answer.

**Sources:**
- [OpenAI — DevDay 2026 Recap](https://openai.com/index/devday-2026-recap/) `[primary]`
- [InfoQ — DevDay 2026 recap for developers](https://www.infoq.com/news/2026/10/openai-devday-2026/) `[secondary]`
- [Developers Digest — What shipped and what to test](https://www.developersdigest.tech/blog/openai-devday-2026-recap-what-shipped) `[aggregator]`
- [Temporal — Series E announcement](https://temporal.io/blog/temporal-raises-usd550m-series-e-at-usd12-55b-valuation-ai) `[primary]`

### Why it matters to you

- **Job lens:** This is the **evidence-of-cost-aware-model-routing** artifact every FDE/MLE interview from October onward is going to probe. Have the Google Sheet open; walk them through case 3. Specifically call out: *"Sol passed 4/5; case 2 regressed, so my router keeps the long-context summary route on Astra until the regression closes."* That sentence is 100% hiring-pass energy.
- **Startup lens:** Multiply the per-call savings across even a mid-sized agent app (say, 50M tokens/day) and the migration is a **$150K–$500K/yr P&L swing per customer**. "Model-migration-as-a-service" (ingest an existing codebase, run regression evals, auto-generate the shim, prove the quality) is a $5–20M ARR wedge for the next 18 months — this is the start of the "every new model announcement is a sales call" cycle.
- **Insight:** The Astra cancellation **weaponizes migration** — pricing cycles got 2× faster. The scarce skill in H2 2026 isn't "which model is best" but "how fast can you migrate between models without breaking production." Mod + eval + router + Temporal is **the migration kit.**

→ Cross-link: [`02` §1 Temporal](./02-new-emerging.md#1-temporal) · [2026-09-10/03 §3 the router artifact](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact).

---

## 4. The 2026-Q4 "modern AI stack" recipe (for your interview answer and your portfolio README) {#4-stack-recipe}

A one-paragraph answer you should memorize before Monday's interviews. It's intentionally opinionated and specific — generic answers lose.

**Model layer:**
- **Claude Fable 5.1** (default coding + knowledge work; cache-reads $0.25/1M)
- **Claude Opus 5.5** (hard reasoning + high-stakes writing)
- **GPT-6.1 Sol** (cheapest frontier; computer-use agents)
- **GPT-6 Astra** (highest-stakes still-available OpenAI; keep for regressions on evaluated tasks)
- **Gemini 3.5 Flash** (cheapest long-context + multimodal)
- *(Avoid as default: GPT-6.1 Astra [cancelled]; Mythos 5.1 + Gemini 4 Argon [restricted access only])*

**Agent primitives (Claude Code side):**
- **CLAUDE.md** (project guidance) · **Skills** (JIT knowledge) · **Subagents** (delegation) · **Hooks** (enforcement) · **Mods** (agent rewrite)

**Workflow + state layer:**
- **Temporal** (durable execution for multi-step agent workflows)
- **Supabase + Turso** (per-agent SQLite DBs + central Postgres for shared state)
- **Mem0 / EverMemOS** (agent-memory architecture; see [`04` §1](./04-research-progress.md#1-heavy-tailed-memory))

**Identity, security, compliance:**
- **Baselayer "Know Your Agent"** (identity verification for agents touching money / regulated flows)
- **Hooks + Mods** (local-side enforcement)
- **Prompt-injection sanitiser** (dual-model pattern — see [2026-05-22/03](../2026-05-22/03-practical-skills-and-tools.md))

**Observability:**
- Mod-based deterministic replay (your weekend v0.2)
- Per-step cost logging (your Sol shim)

**That's the stack.** Say that in an interview and whoever's across the table knows you're reading this week's news, not last year's.

**Sources:** (see each referenced section)

### Why it matters to you

- **Job lens:** Memorize this. Say it with confidence. Modify as you learn (the Nov-Dec version will differ — update it monthly).
- **Startup lens:** Build on top of this stack as a default. The reason it's defensible: **each component is funded, each is category-leading, and each is independently open to replacement** — so your startup isn't single-vendor-locked.
- **Insight:** Stacks become fashion when they're nameable. "MERN." "Jamstack." The nameable version of this one hasn't landed yet, but the shape has. First-movers get to coin it.

→ Cross-link: [`05` §2 Frontier Academy wedge](./05-career-and-startup.md#2-frontier-academy-wedge).

---
