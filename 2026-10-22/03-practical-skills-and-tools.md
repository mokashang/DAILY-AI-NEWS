# Practical Skills & Tools — 2026-10-22

Three things worth your Thursday: **(1) port your MCP server to the July 2026 stateless spec if you haven't** (1–2 hours, résumé-grade); **(2) tune Claude Code auto-mode defaults in your repo** (30 min; makes Haiku 5.5 + Opus 5.5-effort=low the Pareto-dominant pair for most tasks); **(3) run the 3-model Argon vs Opus 5.5 vs GPT-6 Sol price-arb sweep TONIGHT** (60 min, ~$30 at batch tier, lands a portfolio-grade artifact before the Nov 30 cliff narrows the window).

Tags: `#mcp #stateless #claude-code #auto-mode #routing #argon #opus-5-5 #gpt-6`

---

## 1. Port your MCP server to the July 2026 stateless spec {#1-mcp-stateless-port}

**Why:** The July 2026 Agentic AI Foundation (Linux Foundation) spec update ratified **stateless** as the default MCP transport. **TypeScript SDK v1.27.1, Python v1.26** are the current spec-conformant versions. Native support in Google ADK + OpenAI Agents SDK + Cursor + Windsurf + Replit.

**If your MCP server predates July 2026:** it probably uses the earlier stateful transport. This is now technical debt that reads badly on a résumé and is a liability for deployment (session management + auth are harder than stateless, and you now ship to fewer hosts without the migration).

### 30-minute diagnostic

1. Read your `server.py` / `server.ts` entry file.
2. Does the handler store any session state between requests (an in-memory dict keyed by `session_id`)? If yes → stateful. Port.
3. Are you using the HTTP+SSE transport? If yes → stateful by convention. Port to the stateless HTTP transport.
4. Are you using the stdio transport? If yes → you're probably fine; stateless by nature. Confirm by reading your tool definitions for session-dependence.

### 90-minute port (TypeScript example)

```typescript
// BEFORE (stateful HTTP+SSE)
import { Server } from '@modelcontextprotocol/sdk/server/index.js';
import { SSEServerTransport } from '@modelcontextprotocol/sdk/server/sse.js';

// AFTER (stateless HTTP)
import { Server } from '@modelcontextprotocol/sdk/server/index.js';
import { StreamableHTTPServerTransport } from '@modelcontextprotocol/sdk/server/streamableHttp.js';

const transport = new StreamableHTTPServerTransport({
  sessionIdGenerator: undefined, // stateless mode
});
await server.connect(transport);
```

- Replace SSE transport with StreamableHTTP transport.
- Remove any session-id tracking.
- If any tool was session-stateful, convert to pass the state in each request (or persist to Redis / a KV store external to the server process).
- Add a tiny health endpoint + a `GET /` discoverability route.

### Sources

- [Model Context Protocol — spec repo](https://github.com/modelcontextprotocol/modelcontextprotocol) `[primary]`
- [MCP Python SDK](https://github.com/modelcontextprotocol/python-sdk) `[primary]`
- [MCP TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk) `[primary]`
- [Agentic AI Foundation at Linux Foundation](https://agenticaifoundation.org/) `[primary]` *(base — look for the stateless-spec ratification announcement)*
- Prior context: 2026-10-21 §11 MCP stateless

### Why it matters to you

- **Job lens:** "Ported my MCP server to the Agentic AI Foundation stateless spec" is a 2-hour sentence that reads as "stays current with the ecosystem" on a résumé. Pair it with the Oct 21 cross-vendor note ("ships to Google ADK + OpenAI Agents SDK + Cursor + Windsurf + Replit") and you've demonstrated multi-vendor awareness in one artifact.
- **Startup lens:** If your startup's architecture includes an MCP server that integrates with multiple hosts, stateless is the only safe transport to standardize on going forward. Any new product-adjacent MCP server you ship from today onward must be stateless unless you have an explicit stateful-only use case.
- **Insight:** Protocol-level migrations like this one are the clearest signal of ecosystem maturity. The MCP spec hit "boring" status in July 2026 — statelessness is table-stakes; no feature pitch, no competitive-advantage story, just hygiene. **This is the point in an ecosystem's life where tooling + eval + deployment infrastructure startups become durable** (the protocol stops changing; the tooling around it accrues).

---

## 2. Tune Claude Code auto-mode defaults for Haiku 5.5 + Opus 5.5 effort=low {#2-claude-code-auto-mode-tuning}

**Why:** v2.1.304 (Oct 19) made auto-mode default + subagents run in background. For most tasks in most repos, the Pareto-dominant routing is now:
- **Planner tier:** Opus 5.5 at `effort=low` (reasoning always-on; cheapest effort tier of the flagship)
- **Worker tier:** Haiku 5.5 (default worker on API with 1M context)

**Measure before adopting:** your repo's task mix may differ. The pattern is strongest when your tasks are a mix of mechanical refactors (Haiku-dominant) + strategic reasoning (Opus-dominant). It's weaker if your tasks are long-horizon code generation (Sonnet 5.5 or Opus 5.5 effort=medium often beats the above split).

### 30-min tune

1. **Measure baseline:** run `/auto-mode-setup` in your repo. Record the current default model(s) + the past-week usage breakdown.
2. **Switch to the pair:** set planner to `claude-opus-5-5` with `effort=low`; set worker to `claude-haiku-5-5`.
3. **Run 3 representative tasks** against each config (6 tasks total). Record walltime + token spend + subjective quality.
4. **Pick the winner;** persist to `.claude/settings.json` as the project default. Commit.

### Sources

- [Anthropic — Claude Code release notes](https://docs.anthropic.com/claude/docs/claude-code-release-notes) `[primary]` *(base link)*
- [Anthropic — Claude Code auto-mode docs](https://docs.anthropic.com/claude/docs/claude-code-auto-mode) `[primary]` *(base link; v2.1.304 added `/auto-mode-setup`)*
- Prior context: 2026-10-21 §4 Claude Code v2.1.304

### Why it matters to you

- **Job lens:** Interview answer: *"I use Opus 5.5 at effort=low as the planner and Haiku 5.5 as the worker. I measured this against Sonnet 5.5 in my own repo; the pair gets me 2× walltime improvement at 60% of the token spend for mechanical refactor tasks. For long-horizon code generation I switch planner to effort=medium."* That is interview-ready; most of the cohort has not measured the Opus 5.5 effort=low knob in-repo.
- **Startup lens:** If your startup ships a developer tool that wraps Claude Code (or spawns Claude Code subagents), the routing primitive above is the one you should hard-code as a sensible default. "Haiku 5.5 worker + Opus 5.5 effort=low planner" has become a shorthand this week.
- **Insight:** The right unit of comparison for Q4 2026 is not **(model_a vs model_b)** — it is **{planner, worker, effort_level, task_class} tuple vs tuple**. The interviewers who are good at this will ask you to compare tuples, not models. **Prepare three tuples: the pair above (fast + cheap), Opus 5.5 effort=high solo (slow + highest quality), and the Argon-based alternative pair for comparison (next section).**

→ Cross-link: [`04` §1 alignment watch](./04-research-progress.md#1-alignment-watch) · [`05` §2 reprice](./05-career-and-startup.md#2-reprice)

---

## 3. TONIGHT — Argon vs Opus 5.5 vs GPT-6 Sol price-arb sweep {#3-tonight-argon-sweep}

**Why tonight, not the weekend:**

- **39 days left on the Argon $2/$10 intro cliff.**
- **5 days until Mistral Large 4 open weights drop, which will consume the next cycle of attention** — ship your Argon vs Opus 5.5 vs GPT-6 Sol comparison *before* that drop, or your artifact will be noise against the Oct 27 fine-tune wave.
- **A 3-model price-arb sweep costs ~$30 at batch tier.** Not an all-nighter. 60–90 min end to end.

### 60-min version

**Setup (15 min):**

```bash
pip install google-genai anthropic openai
export GEMINI_API_KEY=... # https://aistudio.google.com/apikey
export ANTHROPIC_API_KEY=...
export OPENAI_API_KEY=...
```

**Choose tasks (5 min):**
Pick 10 tasks from your existing eval harness. If you don't have one, use these:
1. Refactor a 150-line Python module into 3 helpers.
2. Extract 10 named entities from a 2-page document (ground truth available).
3. Classify a 400-word support ticket (urgency / area / next-step).
4. Summarize a 2-page technical spec in 100 words.
5. Translate a 300-word product description EN→ES, preserve brand voice.
6. Write a 20-line SQL migration for a schema change.
7. Debug a stack trace in a 100-line program.
8. Generate 10 realistic test cases for a public API.
9. Write a 500-word README for a repo given its file tree.
10. Rewrite a resume bullet point for a specific JD.

**Run (30 min):**

```python
import os, time, json, csv
from anthropic import Anthropic
from openai import OpenAI
import google.generativeai as genai

anthropic = Anthropic()
openai = OpenAI()
genai.configure(api_key=os.environ["GEMINI_API_KEY"])

MODELS = {
    "argon":  ("gemini-4-argon", "gemini"),
    "opus55": ("claude-opus-5-5", "anthropic"),
    "gpt6-sol": ("gpt-6-sol", "openai"),
}
TASKS = [...]  # as above
RESULTS = []
for name, task in enumerate(TASKS):
    for mkey, (model_id, provider) in MODELS.items():
        start = time.time()
        if provider == "anthropic":
            resp = anthropic.messages.create(
                model=model_id,
                max_tokens=2048,
                thinking={"type": "enabled", "effort": "low"},  # Opus 5.5 effort=low
                messages=[{"role": "user", "content": task}]
            )
            text = resp.content[0].text
            in_tokens, out_tokens = resp.usage.input_tokens, resp.usage.output_tokens
        elif provider == "openai":
            resp = openai.chat.completions.create(
                model=model_id,
                messages=[{"role": "user", "content": task}]
            )
            text = resp.choices[0].message.content
            in_tokens, out_tokens = resp.usage.prompt_tokens, resp.usage.completion_tokens
        elif provider == "gemini":
            model = genai.GenerativeModel(model_id)
            resp = model.generate_content(task)
            text = resp.text
            # Gemini token accounting: get from resp.usage_metadata
            in_tokens  = resp.usage_metadata.prompt_token_count
            out_tokens = resp.usage_metadata.candidates_token_count
        walltime = time.time() - start
        RESULTS.append({"task": name, "model": mkey, "walltime_s": walltime,
                        "in_tokens": in_tokens, "out_tokens": out_tokens, "text": text})

# Dump CSV
with open("sweep.csv", "w") as f:
    w = csv.DictWriter(f, fieldnames=RESULTS[0].keys())
    w.writeheader()
    w.writerows(RESULTS)
```

**Analyze (10 min):**

- For each task × model, compute `cost = in_tokens * price_in + out_tokens * price_out`.
- Pricing table in the code (as of 2026-10-22):
  - Argon intro: `$2/1M in, $10/1M out`
  - Opus 5.5: `$4/1M in, $20/1M out`
  - GPT-6 Sol: `$3/1M in, $15/1M out` (approximate; verify against your OpenAI invoice)
- LLM-judge quality: pass each triple of answers to Opus 5.5 at `effort=high` with a 1–5 rubric. Record scores.

**Publish (10 min):**

- Repo: `github.com/<you>/argon-vs-opus-vs-gpt6-price-arb` — MIT license.
- One chart: cost per task (x = task, y = $ cost; 3 bars per task). One table: quality score per task × model.
- 400-word README headline: *"Three-model cost-arb eval during the Argon $2/$10 intro window. 39 days to Nov 30. The 10 use cases where Argon dominates, the 2 where Opus 5.5 is worth the 3× price."*
- LinkedIn post + HN Show post ("Show HN: 3-model price-arb eval — Gemini 4 Argon vs Claude Opus 5.5 vs GPT-6 Sol, 10 tasks, $30 total").

### Sources

- [eesel — Gemini 4 Argon pricing](https://www.eesel.ai/blog/gemini-4-argon-pricing) `[analysis]`
- [Google AI Studio](https://aistudio.google.com/) `[primary]` *(for Argon API key)*
- [Anthropic API docs — Opus 5.5 effort levels](https://docs.anthropic.com) `[primary]`
- [OpenAI API — GPT-6 Sol](https://platform.openai.com/docs/models) `[primary]`

### Why it matters to you

- **Job lens:** The specific résumé top-line this unlocks: *"Measured Argon vs Opus 5.5 vs GPT-6 Sol on 10 production-shaped tasks during the Oct 2026 intro-pricing window; identified the Pareto frontier of {model, effort, task class} tuples."* This is the exact artifact that **re-prices your profile up by one tier** at any FDE / AI Platform / AI Integration role — because almost no one in the cohort has done the Argon work yet.
- **Startup lens:** The 3-model CSV is a starter dataset. If you want to pursue the routing-as-a-service wedge, this is the first commit. The follow-up: run the same sweep weekly through Dec 1, publish a cost-arb time series, and offer enterprises a snapshot report at $5K/mo. Routable + measurable + time-bound = a sellable wedge.
- **Insight:** When a market gives you a 39-day calendared pricing anomaly, the entire economic question is *who measures it first and publishes.* The first measurement becomes the canonical reference everyone else cites. **If you ship tonight, you're the citeable artifact.**

→ Cross-link: [`01` §1 Argon cliff](./01-big-lab-moves.md#1-argon-cliff) · [`05` §2 reprice](./05-career-and-startup.md#2-reprice)
