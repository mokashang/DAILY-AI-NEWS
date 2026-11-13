# Practical Skills & Tools — 2026-10-09

Three things worth doing today. **(1) Rebuild your router with Haiku 5.5 as the sub-$0.50/M floor** (and add the >100K-token pricing branch — this is the first "shape-aware" price in production). **(2) Prototype one Intelligent-UI-style adaptive output** on an existing project to see how the design surface feels. **(3) Ship the weekend artifact: cost-router v3 + an auto-detect cron that re-runs the eval on model-list changes** — the version that *stays* current despite the release cadence.

Tags: `#claude #haiku #pricing #routing #claude-code #ux #evals #skills`

---

## 1. The Haiku 5.5 router rebuild — shape, not size {#1-haiku-55-router}

**The practical move:** Add two things to your existing router artifact (per [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) + [2026-10-08/03 §2](../2026-10-08/03-practical-skills-and-tools.md#2-pricing-rebuild)):

**(a) The Haiku 5.5 price floor.** At **$0.10 input / $0.50 output** for prompts ≤100K tokens, Haiku 5.5 is now **~5× cheaper than Fable 5.1 cached ($0.25/1M cache reads)** on uncached calls, and **~95% cheaper than GPT-6 Sol** ($2/$10). Haiku 5.5 wins outright on summarization/compaction/classification/DB-query **unless** your prompt crosses 100K tokens.

**(b) The 100K-token branch.** When prompt length > 100K, Haiku 5.5 flips to **$0.50 / $2.50** — now priced **5× its short-prompt rate** and **4× cheaper than GPT-6 Sol in / 4× cheaper out**. Fable 5.1 cached + a cache-hit become competitive again. **This is the first production-shippable rate card that penalizes prompt length within a single model** — your router MUST branch on `prompt_tokens` not just `task_type`.

**30-line sketch (illustrative, verify prices in your platform console):**

```python
# cost_router.py — v3, 2026-10-09
PRICE = {
  "haiku-5-5-short": (0.10, 0.50),   # <=100K prompt
  "haiku-5-5-long":  (0.50, 2.50),   # >100K prompt
  "fable-5-1":       (3.00, 15.00),  # Sonnet-tier equivalent
  "fable-5-1-cache": (0.25, 15.00),  # cache-read on prompt
  "gpt-6-sol":       (2.00, 10.00),
  "gpt-6-luna":      (0.50, 2.00),   # est; Free/Go tier
  "gemini-3-8-flash":(0.75, 3.75),   # until Jan 1, then doubles
}

def route(task, prompt_tokens, est_output_tokens, needs_tools=False):
    if task in ("summarize", "classify", "db_query", "compact"):
        key = "haiku-5-5-long" if prompt_tokens > 100_000 else "haiku-5-5-short"
        return key
    if task == "code" and est_output_tokens > 4_000:
        return "fable-5-1-cache" if cache_hit_likely() else "gpt-6-sol"
    if task == "chat_cheap":
        return "haiku-5-5-short" if prompt_tokens < 50_000 else "gemini-3-8-flash"
    if needs_tools:
        return "fable-5-1-cache"  # or gpt-6-sol via Dots
    return "haiku-5-5-short"
```

**Caveats:** Prices from secondary sources; verify in Claude Console / OpenAI Platform / Google AI Studio before billing against them. GPT-6 Luna pricing is estimated; OpenAI's "GPT-6 for everyone" post didn't publish per-token API rates at the Free/Go tier. Gemini 3.8 Flash **doubles Jan 1, 2027** — plan the migration before the holiday freeze.

**Sources:**
- [AI Weekly — Introducing Claude Haiku 5.5](https://aiweekly.co/alerts/introducing-claude-haiku-55) `[aggregator]`
- [LLM Gateway — Claude Haiku 5.5](https://llmgateway.io/models/claude-haiku-5-5) `[aggregator]`
- [OpenAI — GPT-6 for everyone](https://openai.com/index/gpt-6-for-everyone/) `[primary]`
- [Artificial Analysis — Model pricing comparison](https://artificialanalysis.ai/) `[analysis]`

### Why it matters to you

- **Job lens:** FDE/AI-Engineer interviews are shifting to "show me your eval + cost dashboard across model changes." The router that **branches on prompt shape** (length, task type, tools, output size) is the answer that reads as *2026-Q4 current*. If your router only branches on model name, that reads as *2025*.
- **Startup lens:** The **shape-aware pricing dimension** is a product opportunity: an "AI bill of materials" / "cost-router-as-a-service" product that watches your actual traffic and auto-selects (not auto-generates) the model+config per request. Vellum, LangSmith, Portkey all do a version; none yet handles the `prompt_tokens > 100K` branch cleanly.
- **Insight:** The strategic read: **the frontier labs are competing on cost structure, not model quality.** Haiku 5.5's two-tier pricing is a surgical move against OpenAI's Sol/Luna segmentation. The router pattern you build this quarter will be re-run 4× in H1 2027 as Gemini 4, Fable 5.2, GPT-6.1, and open-weights (Reflection, DeepSeek V5) each ship their own price-shape. Build the automation now; the artifact is the compounding asset, not the current state of the price map.

→ Cross-link: [`05` §2 skill re-price](./05-career-and-startup.md#2-reprice).

---

## 2. Intelligent UI as a design primitive — try it on your portfolio {#2-intelligent-ui-primitive}

**The practical move:** Spend 60 minutes this weekend adding **adaptive output** to one existing project. The idea: GPT-6's Intelligent UI composes text + tappable buttons + charts + forms based on the question — you can bolt the same primitive onto any Claude/Gemini backend using structured outputs + a lightweight renderer.

**Minimal pattern (illustrative):**

1. **Define an output schema.** Instead of returning a string, return a JSON object like `{segments: [{kind: "text" | "chart" | "choices" | "table", payload: ...}]}`.
2. **Prompt the model to pick the shape.** System prompt: *"Compose the response from the following segment kinds. Use `choices` when the user needs to pick; `chart` for a trend or distribution; `table` for comparisons; `text` for everything else. Minimize `text`-only responses when a richer kind is appropriate."*
3. **Render.** A single React/Svelte component that switches on `kind` — 50 lines, no state.
4. **Instrument.** Log `kind` distribution per query type → that's the eval axis. "Did the model pick the right shape?" is now a measurable question.

**Why this is interview-ready:** 2026-Q4 FDE/Solutions roles ask about **"how would you make agent output legible to a non-expert?"**. A one-weekend demo answers the question better than any slide. Pair it with a 60-second gif on LinkedIn and `AI Engineer — adaptive output + cost routing + eval-authoring` in your headline.

**Sources:**
- [OpenAI — GPT-6 for everyone](https://openai.com/index/gpt-6-for-everyone/) `[primary]`
- [Let's Data Science — OpenAI Rolls Out GPT-6 and Intelligent UI](https://letsdatascience.com/news/openai-brings-gpt-6-and-intelligent-ui-to-chatgpt-4f0d797c) `[secondary]`
- [Ecosistema Startup (ES) — ChatGPT suma Intelligent UI con GPT-6](https://ecosistemastartup.com/?p=115735) `[secondary]`

### Why it matters to you

- **Job lens:** Adaptive output demos are **the new router-artifact-of-fall-2026** — a 1-weekend portfolio piece that is *concrete*, *shows understanding of the 2026-Q4 product surface*, and *generalizes*. Three concrete starter projects: (a) a cost-router (from §1) where the output *is* adaptive (chart of cost-per-model + choice buttons for route policy); (b) a `grep #tag`-across-this-repo tool that returns a filter-by-date table + a timeline chart; (c) a `README.md` reader that renders section anchors as tappable chips.
- **Startup lens:** The **"adaptive-output SDK" category** is unoccupied. Vercel's AI SDK + Thesys-style "Generative UI" + a tiny set of competitors; none has become the Shadcn-style default yet. Opening is the 60-day window: ship an opinionated SDK with 10 output-kind primitives, Claude + GPT + Gemini backends, and a Storybook/React Native starter. If timing is right, this is a Hacker News front page + 1,000 stars in a quarter.
- **Insight:** The real primitive here isn't "visuals" — it's **the schema contract between the model and the renderer**. Once you've written a `kind: "choice"` + a renderer for it, you've effectively specified *the agent's HCI surface*. That's a durable artifact in a way "a React component" isn't, because the schema outlives the specific model version. Build the schema; the renderer is the easy part.

→ Cross-link: [2026-10-08/03 §1 agent-runtime decision tree](../2026-10-08/03-practical-skills-and-tools.md#1-runtime-decision-tree).

---

## 3. The weekend artifact (3-hour build) — router v3 + auto-detect cron {#3-weekend-artifact}

**The ship list:** A single public repo, pushed by Sunday night, that demonstrates **you have survived four model-release weeks in a row.**

**Scope:**

1. **`cost_router.py` v3** — the shape-aware router from §1. Supports Haiku 5.5 short/long, Fable 5.1 cached/uncached, GPT-6 Sol/Luna, Gemini 3.8 Flash with Jan-1-2027 doubling pre-baked. ~60 lines.
2. **`eval_suite.py`** — 10 test cases covering: short classification, 500K-token summarization, 20K-token code generation with tool-use, structured output, cheap chat. Each case runs on 3+ models; measures accuracy (vs. reference) + cost + latency. ~120 lines.
3. **`detect_model_changes.py`** — a cron (or GitHub Actions on a schedule) that scrapes vendor pricing pages (Anthropic Console, OpenAI Pricing, Google AI Studio) *weekly*, diffs them, and opens a GitHub issue if anything changed. **This is the piece that re-prices your artifact in interviews**: "my router has survived four release weeks because it's not a snapshot — it's an auto-updating artifact."
4. **`output_renderer/`** — a tiny React/Svelte component implementing §2's adaptive output. Render the eval-suite's cost dashboard with it. The *router's own UI* uses the Intelligent-UI primitive.
5. **`README.md`** — 60-second explanation, 1 architecture diagram, 1 "how to run" block, 1 "limitations" section, 1 "next 4 weeks" section listing what you'll add when the next model ships. Last section is the *trust signal*.

**Publish:**
- Push to GitHub as `yourname/ai-cost-router-v3-oct9`.
- Record a 90-second screen-capture gif showing the eval run + the output renderer.
- LinkedIn post Monday morning: `AI Engineer | Shape-aware model routing, auto-detect cron, adaptive output rendering | Updated for Haiku 5.5 (Oct 7) + GPT-6 Intelligent UI (Oct 7)` — the dates in the headline are the signal that this is maintained.

**Time budget:** 3 hours. If the eval suite is thin, that's OK — the differentiator is the *auto-detect cron + the maintained-artifact framing*, not the volume of tests.

**Sources (reference stack):**
- [Anthropic Pricing](https://www.anthropic.com/pricing) `[primary]`
- [OpenAI API Pricing](https://openai.com/pricing) `[primary]`
- [Google AI Studio Pricing](https://ai.google.dev/pricing) `[primary]`
- [Vercel AI SDK — Generative UI docs](https://sdk.vercel.ai/) `[primary]`

### Why it matters to you

- **Job lens:** The resume line is **"I maintain a 60-line AI cost router with an auto-update cron. Survived 4 model-release weeks (Aug–Oct 2026). Repo link."** Every FDE/Solutions/AI-Engineer screener this quarter will ask about it, because *they are evaluating "can you keep a system current under pressure," not "do you know PyTorch."*
- **Startup lens:** Open-sourcing the router + auto-detect cron is a **mini-platform play**: your repo accumulates stars every time a model ships (because people find it when searching "haiku 5.5 pricing router"). After 3–6 months of steady releases, you have a cohort of GitHub stars + newsletter subscribers = the launch audience for a SaaS version of the same thing.
- **Insight:** The deeper read: **the artifact itself is doing dual duty** — portfolio piece + market-signal collector. The cron tells you *when* each lab moves on price; that's unique daily intelligence most people don't have. Fold the cron's output into this repo (your DAILY-AI-NEWS archive) as weekly "pricing diff" notes. That becomes the compounding knowledge asset for your next edition.

→ Cross-link: [2026-10-08/03 §3 weekend artifact](../2026-10-08/03-practical-skills-and-tools.md#3-weekend-artifact) — this edition's spec is the natural successor.
