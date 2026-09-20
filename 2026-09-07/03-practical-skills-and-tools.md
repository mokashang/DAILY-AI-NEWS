# Practical Skills and Tools — 2026-09-07

Things you can act on **this week**. Every item here has a concrete artifact you can ship in one sitting. Framing: *four frontier launches created four immediate portfolio moves — turn each into a repo, a screenshot, or a customer conversation.*

Tags: `#skills #cache-pricing #prompt-caching #model-router #claude-code #subagents #lean #prove2me #labor-day-artifact`

---

## 1. Cache reprice — migrate a real workload to Fable 5.1 caching tonight {#1-cache-reprice}

**The move (Anthropic Fable 5.1, Sept 1):** 75% cheaper cache reads ($1.00 → $0.25/M input tokens). Anthropic's own claim: **~25% cheaper typical / ~45% cheaper agentic**. Verify it on your own workload.

**Concrete 30-minute recipe:**

1. Pick one workload you already run against Claude (a long-doc Q&A, a support-classification loop, an eval run, a RAG pipeline, whatever).
2. **Turn prompt caching on.** In the API, set `"cache_control": {"type": "ephemeral"}` on the largest stable prefix (system prompt + tools + retrieved context). 5-min cache is $12.50/M writes; 1-hr cache is $20/M writes; **cache reads are now $0.25/M**.
3. Run **100 real requests** with caching off; record total input tokens + total cost.
4. Run **100 real requests** with caching on; record total input tokens (should look similar) + total *billed* cost (should collapse).
5. Screenshot the delta. That's your **portfolio artifact and interview soundbite** for the week.

**Where the numbers are best:**
- **Long stable prefix + short suffix** (system prompt ≫ user message). Cache hit rate approaches 100% on the prefix.
- **Multi-turn tool-using threads.** Every tool response gets cached; the model re-reads the full trajectory cheap.
- **Batch evals** where you rotate the last 200 tokens across many rows against the same 20K-token instructions block.

**Where it's a wash:**
- Single-shot chat with short context.
- Prompts that mutate every request (dynamic RAG concatenation with fresh chunks each time).

**Cross-lab equivalents to demo alongside:**
- **Gemini 3.8 Flash** — implicit caching + `thinking budget` control. $0.75/$3.75 through 12-31. Same workload on Flash for a Q4 cost floor.
- **OpenAI GPT-6 Astra** — prompt caching + `effort` toggle. Get the exact number for your workload.
- **Muse Spark 1.3** — Meta's tokens/tool-calls efficiency is *implicit* rather than a caching knob. Compare the total-cost bar.

**Sources:**
- [Anthropic Prompt Caching Docs](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching) `[primary]`
- [Anthropic — Fable 5.1 announcement (cache pricing)](https://www.anthropic.com/claude-fable-and-mythos-5-1) `[primary]`

### The artifact you post

A repo (`fable-5-1-cache-reprice-demo`) with:
- Two runnable scripts (`with_cache.py`, `without_cache.py`) against a real workload.
- A `results.md` with the cost table + a screenshot of your Anthropic Console usage graph.
- A 90-sec Loom explaining the delta.

**Post caption:** *"Migrated a real workload to Claude Fable 5.1 with prompt caching on. 100 real requests, X% cheaper. Anthropic claimed 25–45%; here's what I got on my workflow. Repo + Loom in comments."* — that's a peak FDE signal.

---

## 2. The 4-lab model-router upgrade — this week's config change {#2-model-router-updates}

**The move:** Four flagships shipped in 72 hours. Your model-router needs to know about all of them and route on cost + capability. Concrete update:

**Add these SKUs to your router (in preference order for typical Applied-AI-Engineer routing):**

| Model | ID | In $/M | Out $/M | Notes |
|---|---|---|---|---|
| **Claude Fable 5.1** | `claude-fable-5-1` | $10 | $50 | Cache reads $0.25/M — default for reasoning + long-thread tool use |
| **Claude Mythos 5.1** | `claude-mythos-5-1` | — | — | Restricted; do NOT reference in public code unless approved |
| **Claude Opus 5** | `claude-opus-5` | $5 | $25 | Cheap coding workhorse. Per-request `effort` toggle |
| **Claude Haiku 4.5** | `claude-haiku-4-5-20251001` | ~ | ~ | Verifier / cheap classifier |
| **Meta Muse Spark 1.3** | (paid API) | — | — | Best token-efficiency; agentic SWE workhorse |
| **Google Gemini 3.8 Flash** | `gemini-3-8-flash` | $0.75 | $3.75 | **Q4 only** — locks 1/1/27 to $1.50/$7.50 |
| **Google Gemini 3.8 Flash Cyber** | (Cyber envelope) | — | — | Restricted; vetted defenders only |
| **OpenAI GPT-6 Astra** | (rolling) | — | — | Best cyber + math + reasoning; `effort` toggle; Daybreak-gated for advanced cyber |
| **OpenAI GPT-5.6 Sol** | — | — | — | Previous frontier; still a good cost-perf point below Astra |

**Routing rules that ship today:**
- **Long-thread agentic + heavy tool use** → **Fable 5.1** (cache pays off).
- **Cheap coding subtasks + verification** → **Opus 5 low effort** or **Haiku 4.5**.
- **Q4 batch jobs, high-volume eval, dataset generation** → **Gemini 3.8 Flash** (Dec 31 price cliff = free arbitrage).
- **Long-horizon SWE tasks with unclear reqs** → **Muse Spark 1.3** (asks for clarification; ~25% fewer tokens).
- **Reasoning-heavy math / CTF / cyber redteam (with proper clearance)** → **Astra** through Daybreak; otherwise Fable 5.1 or Opus 5 at high effort.
- **Public inference with security constraints (no cyber SKU access)** → the general (safe-subset) SKU of whichever frontier lab your compliance stack allows.

**Cost log to add per call:**

```json
{
  "sku": "claude-fable-5-1",
  "effort": "medium",
  "input_tokens": 8421,
  "input_tokens_cached": 7900,
  "output_tokens": 512,
  "estimated_cost_usd": 0.0316,
  "task": "step_3_verify_extraction",
  "trajectory_id": "trj_abc"
}
```

Aggregate per-trajectory total cost. That number is what you show a customer.

**Sources:** all model-card links in [`01`](./01-big-lab-moves.md) sections 1–4.

---

## 3. Claude Code — September update batch, three switches to flip today {#3-claude-code-september-updates}

**What shipped** (Sept 2026 Claude Code release notes, aggregated):

1. **`/skill-doctor`** — shows which loaded skills are unused and how much context they cost. **Run it today.** Trim any skill that's costing >2K context tokens and hasn't been invoked in your last 20 sessions. Typical savings on a bloated `.claude/` dir: 10–20K context tokens, i.e., 5–10% of a Fable window.
2. **`--append-subagent-system-prompt-file`** — read the subagent system prompt from a **file** rather than passing it inline. Fixes the long-prompt CLI truncation bug. Move any long subagent system prompt to `.claude/subagents/<name>/system.md` and reference it via this flag.
3. **`bashOutputMaxChars` and `taskOutputMaxChars`** — raise how much command / task output is inlined before spilling to file. Ceiling is **128K characters**. Bump to 32K for typical dev, 128K for long build logs / eval runs. Setting: `.claude/settings.json`:
   ```json
   {
     "bashOutputMaxChars": 32000,
     "taskOutputMaxChars": 32000
   }
   ```
4. **Bug fix** — a subagent that resumed another via `SendMessage` never got woken by the resumed agent's completion. If you had a flaky multi-agent handoff, it's likely fixed now.

**Extra: subagent text streaming + background-agent reliability fixes** (from the [2026-07-25 Opus 5 launch week](../2026-07-25/#1-opus-5) release notes — still live and worth re-verifying).

**Sources:**
- [Claude Code Changelog (September 2026)](https://www.gradually.ai/en/changelogs/claude-code/) `[secondary]`
- [Claude Code Updates by Anthropic - September 2026 - Releasebot](https://releasebot.io/updates/anthropic/claude-code) `[primary-adjacent]`
- [Claude Code Changelog Docs](https://code.claude.com/docs/en/changelog) `[primary]`
- [Totalum — Claude Code subagents: the 2026 production playbook](https://www.totalum.app/blog/claude-code-subagents-totalum) `[analysis]`

### Why it matters to you

- **Job lens:** A public `.claude/` config in your GitHub with `/skill-doctor` output shown as pruned + subagent system prompts as separate `.md` files under version control is a concrete, shareable "I know Claude Code deeply" signal. FDE loops will ask about your `.claude/` — have one ready.
- **Startup lens:** If you're building on Claude Code as your dev-loop substrate, these updates are cost-out. Turn them on across your team.
- **Insight:** The **skill-loading cost** is now measurable. Watch for a wave of "which skills should I load per project" advice content; the good version of that is your own pruned config.

---

## 4. The Fermat-in-Lean lesson — what Prove2Me actually did, and how to steal the pattern {#4-multi-agent-lean-lessons}

**The move (Anthropic + Prove2Me, blog Sept 4):** Claude formalized Fermat's Last Theorem in Lean in ~11 days, ~6B output tokens, 13M lines, ~29,000 supporting theorems, dozens of agents.

**What actually made it work — the transferable primitives:**

1. **The verifier is external and cheap.** Lean's kernel is the verifier; every candidate step gets checked *by a compiler, not by another LLM.* The LLM writes; a compiler judges. **Rate:** kernel checks are near-free vs. LLM inference — you get truthful rejection at low marginal cost.
   - **Steal this:** in any agent loop where you can get an external, cheap, machine-verifiable check (a `mypy` pass, an `sql` explain plan, a unit test, an eval harness), put it after every generation step.
2. **Multi-agent decomposition matches problem decomposition.** Dozens of agents, each on a sub-theorem or a definition. **Not a general "manager + worker"** shape — problem-graph-shaped.
   - **Steal this:** *Don't spin up N generic subagents.* Instead, decompose the problem into a DAG first, then spin up one subagent per DAG node with a scoped context. This is what Prove2Me's harness does — it's *proof-graph-shaped*.
3. **Failure is cheap; retry is cheap.** ~6B output tokens is a lot in absolute terms, but per-step cost is tiny (Haiku- or Fable-tier verifier + main agent). The economics work because failed attempts cost pennies.
   - **Steal this:** engineer for a **10× retry budget** on hard subtasks, with the verifier deciding retry/quit. This is compatible with the [Opus 5 `effort` toggle](../2026-07-25/#1-opus-5) and per-tool effort budgets.
4. **Limited human input, but not zero.** The blog phrasing is "limited high-level input from humans" — read: the human role is the **theorem statement + the sub-goal graph shape**, not the proof steps.
   - **Steal this:** in your agent-team demo, expose the problem decomposition as the *human-authored artifact* (a `plan.md` or a `graph.yaml`), then let agents fill it.

**The artifact you can ship this week — the Labor Day repo:**

`agent-team-with-verifier` — one repo:
- **Planner**: Fable 5.1 (`effort=high`) reads a problem + emits a subtask graph (YAML).
- **Workers**: Muse Spark 1.3 or Gemini 3.8 Flash (whichever your budget allows) execute each subtask node.
- **Verifier**: Haiku 4.5 + a **domain-specific machine check** (e.g., Python `pytest`, or SQL `EXPLAIN`, or a `zod` schema validator on JSON, or an actual formal verifier if you can plumb Lean).
- **Cost log per step**: SKU, effort, tokens, retries, verifier verdict.
- **README**: cite Prove2Me + Anthropic blog; call the pattern "graph-shaped multi-agent with external verifier."
- **Post caption**: *"Rebuilt the Fermat/Prove2Me pattern on my own workload. External verifier + graph-shaped agents. Per-step cost log inside."*

That's **three FDE interview answers** in one repo: multi-model routing, verifier-loop design, cost predictability.

**Sources:**
- [Anthropic — Formalizing Fermat's Last Theorem (blog)](https://www.anthropic.com/research/formalizing-fermats-last-theorem) `[primary]`
- [Anthropic — Formalizing Fermat's Last Theorem in Lean (PDF)](https://www-cdn.anthropic.com/9e431dff043da6538d99d6c2d231b670aa3da263.pdf) `[primary]`
- [Xena Project (Kevin Buzzard) — FLT: Anthropic has beaten me to it](https://xenaproject.wordpress.com/2026/09/04/flt-anthropic-has-beaten-me-to-it/) `[expert-commentary]`
- [SiliconANGLE — Anthropic uses Claude to formalize proof of Fermat's Last Theorem](https://siliconangle.com/2026/09/04/anthropic-uses-claude-to-formalize-proof-of-fermats-last-theorem/) `[secondary]`
- [Tech Times — Fermat's Last Theorem Machine-Checked: Claude Completes in 11 Days What Took Years to Plan](https://www.techtimes.com/articles/326745/20260905/fermats-last-theorem-machine-checked-claude-completes-11-days-what-took-years-plan.htm) `[secondary]`

### Why it matters to you

- **Job lens:** The verifier-in-the-loop pattern is *the* pattern FDE teams are building right now. Nail it on your own workload; the Prove2Me writeup is your reference.
- **Startup lens:** Any vertical-agent startup can inherit this pattern. Substitute the verifier for a **domain-specific machine check** (a compliance-rule engine, a chemistry validity check, a legal citation resolver). That's a defensible moat.
- **Insight:** **The verifier IS the moat.** Whoever ships a cheaper/more-precise verifier for a domain wins the agent-team competition in that domain, regardless of frontier-model horsepower. This is why the Prove2Me demo is such a big signal — Lean's kernel *is* the ideal verifier for math. Ask yourself: what's the Lean-kernel-equivalent for the vertical I care about?

---

## 5. One-liners: things to do this week regardless {#5-one-liners}

- **Lock a Gemini 3.8 Flash Q4 batch job.** Anything you were going to run at Fable output rate, if quality is acceptable at Flash, do it at $3.75/M output before Jan 1.
- **Turn on your Anthropic MCP server registry.** If you had one before Sept 1, it now benefits from cache reads at $0.25/M — free money on every tool discovery pass.
- **Add `effort` and `thinking_budget` per-tool to your router log.** Table stakes; recruiters will ask.
- **Watch [Anthropic Fellows](https://alignment.anthropic.com/2025/anthropic-fellows-program-2026/)** every Monday for the Cohort-3 form. Have your 1-pager pre-written. See [`05` §1](./05-career-and-startup.md#1-fellows-reopens).
- **Save the [karpathy/autoresearch](https://github.com/karpathy/autoresearch) repo.** If you have GPU time (Colab Pro / a rented A100), give it a Labor Day evening. That's a `#reproducing-karpathy` post you can turn into interview conversation.

---

_See_: [`01`](./01-big-lab-moves.md) for the model-release detail behind the router changes · [`04`](./04-research-progress.md) for the research angle on Fermat + verifier design · [`05`](./05-career-and-startup.md) for how to convert this week's skills into applications.
