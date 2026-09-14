# Practical Skills & Tools — 2026-06-27

Five act-on-tonight items, ranked by effort × leverage. The unifying theme: **per-step cost attribution + multi-model fallback** is the skill the market is now paying for. The Anthropic Agent SDK metering change (June 15) is 12 days old; the responses are starting to land in tools.

---

## <a id="1-claude-code-week26"></a>1. Claude Code Week 26 — `claude mcp login`, cross-repo subagents GA, `/usage` per-agent cost

**Effort:** 15 min · **Leverage:** ⭐⭐⭐⭐⭐

**What shipped (week of June 22–26):**

| Feature | What it does | Why now |
|---|---|---|
| `claude mcp login <server>` / `claude mcp logout <server>` | Authenticate OAuth-gated MCP servers from the shell | Was clunky inside `/mcp` menu; this enables scripting + CI flows |
| **Cross-repo subagents (GA)** | Subagents operate across multiple local repos in one session — synchronized dep bumps, client/server API contract checks, coordinated tags | Was beta; production-ready now |
| **Nested subagents (3 levels GA)** | A subagent can spawn a subagent can spawn a subagent | Required for the "orchestrator routes to specialists" pattern |
| **`/usage` per-agent cost attribution** | See which subagent is burning Pro/Max quota in real time | Direct response to June 15 metering — diagnose before you overspend |
| **Shell mode auto-explain** | `! pytest -x` no longer needs a follow-up prompt; Claude reads the output and continues | Removes the "now look at the error" prompt cycle |
| **`/rewind` recovers state from before `/clear`** | The recovery you wished you had | Quality-of-life, but ships now |
| **Background-subagent permission surfacing** | Permission prompts appear in the main session rather than silently deny | Removes silent-failure mode for orchestrators |

**Tonight (15 min):**
1. Upgrade: `npm i -g @anthropic-ai/claude-code@latest` (≥ v2.1.185).
2. `claude mcp login <any OAuth MCP you've been re-authing manually>`.
3. Open your top-2 repos in one Claude Code session; run a cross-repo refactor as a single command.
4. After the run, `/usage` to see which subagent burned what — **screenshot it for your portfolio writeup**.

**Sources:**
- [Claude Code release notes (rolling)](https://code.claude.com/docs/en/whats-new) `[primary]`

**Why it matters to you.**
- **Job:** "I orchestrate cross-repo subagents and attribute per-agent cost" is a real Solutions / FDE talking point — `/usage` is the proof in screenshots.
- **Startup:** If your product wraps Claude, **`/usage` data is the cost-engineering primitive** your customers will want surfaced in your dashboard. Mirror it.
- **Insight:** This is the Anthropic-stack response to the **GPT-5.6 "ultra mode"** announcement ([`01` §1](./01-big-lab-moves.md#1-gpt56)). Both labs are racing to ship the parallel-subagent UX. Whoever makes the cost attribution most legible wins.

**Tags:** `#claude-code #mcp #subagents #cost #orchestration`

---

## <a id="2-portfolio-port"></a>2. Portfolio recipe — port a 0.2–1B HF model to the browser in one evening

**Effort:** 3–4 hours · **Leverage:** ⭐⭐⭐⭐⭐ (one artifact, three interview questions)

**Recipe (after Simon Willison's June 22 walkthrough):**

1. Pick a small Hugging Face model — Willison used **Moebius 0.2B** (inpainting); good candidates: any 0.2–1B diffusion / TTS / classifier you care about.
2. Open Claude Code in one session. Prompt:
   - "Convert this PyTorch model at `<repo URL>` to ONNX. Run a parity test in Python vs the PyTorch outputs."
   - Then: "Wrap the ONNX model with onnxruntime-web for the browser. Build a minimal HTML demo with a textarea + canvas + download button."
   - Then: "Add a model-loading progress bar and OPFS caching so the second visit doesn't re-download." *(Pair with Willison's [`opfs-pyodide`](https://simonwillison.net/) for OPFS-backed Python if your model has a Python pre/post-processing step.)*
3. Deploy to Cloudflare Pages or your `username.github.io`. Tweet/X the demo with link + 2-min Loom.

**Why this artifact:**
- **Job:** Demonstrates (1) model-deployment literacy, (2) end-to-end ownership including the unsexy WASM glue, (3) shipping discipline. Hiring managers love "I shipped a working demo last weekend."
- **Startup:** **Client-side AI** is a real wedge — zero inference cost, zero data-leaves-device. Vertical play: regulated industries where data can't leave.
- **Insight:** Doing this with Claude Code = **one prompt does what used to take three days of WASM debugging.** This is the tangible proof of the productivity shift; the artifact IS the evidence.

**Sources:**
- [Simon Willison's weblog (June 22)](https://simonwillison.net/) `[primary]`

**Tags:** `#claude-code #wasm #pyodide #portfolio #ship-something`

---

## <a id="3-glm52"></a>3. GLM-5.2 — your new Claude Opus fallback at ⅙ the cost

**Effort:** 30 min · **Leverage:** ⭐⭐⭐⭐

**What:** Z.ai released **GLM-5.2** under **MIT license** (June 17, momentum still building):
- **753B MoE (~40B active)**
- **1M token context**
- **62.1 SWE-Bench Pro** (beats GPT-5.5)
- OpenRouter pricing: **$1.40 in / $4.40 out per M tokens** (≈ ⅙ of Opus 4.7)

**Tonight (30 min):**
1. Add OpenRouter API key to your env.
2. In Claude Code: configure `fallbackModel: "openrouter/zhipu/glm-5.2"` for cost-sensitive tasks.
3. Run your standard coding eval (one PR you previously had Opus handle) against GLM-5.2 via the same orchestration. Note speed and accuracy delta.
4. **Write 200-word blog post** comparing Opus vs GLM-5.2 on your specific use case — publishable Sunday.

**Why it matters to you.**
- **Job:** Multi-model routing skill keeps pricing as a first-class concern. Blog posts comparing on real evals are interview gold.
- **Startup:** GLM-5.2 collapses your inference cost line if 50%+ of your traffic doesn't need Opus tier. Bake into your COGS modeling now.
- **Insight:** **Open-weights catching up** is the single most under-priced narrative in the user-facing AI conversation. GLM-5.2 + DeepSeek-V4 + MiniMax M3 (all 2026 H1) are within 10% of frontier on the benchmarks customers care about, at one-sixth the cost.

**Sources:**
- [Simon Willison on GLM-5.2 (June 17)](https://simonwillison.net/) `[primary]`
- [VentureBeat coverage](https://venturebeat.com/) `[secondary]`

**Tags:** `#open-weights #glm #cost #routing #fallback`

---

## <a id="4-karpathy-nes"></a>4. Karpathy's `nes.py` — Natural Evolution Strategies in 50 lines

**Effort:** 30 min · **Leverage:** ⭐⭐⭐

**What:** Karpathy gist (June 21): minimal NumPy demo of **Natural Evolution Strategies** optimizing a quadratic. "min-char-rnn" treatment for gradient-free black-box optimization. Short enough to read end-to-end on a coffee break.

**Tonight (30 min):**
1. Read the gist.
2. Fork it. Swap the quadratic for a **non-differentiable objective from your work** — e.g. an agent reward signal (discrete win/lose), a sampler output you can't differentiate through, or a sim-based metric.
3. Run it overnight. Tweet/X your result with one observation.

**Why it matters to you.**
- **Job:** ES is back in fashion for RLHF-adjacent reward shaping (because you can optimize *any* reward, including human-eval scores). Adding "I implemented NES on top of a custom reward" to your repo is a credible signal.
- **Startup:** If your product has a non-differentiable success metric (engagement, conversion, downstream label quality), ES is the cleanest way to tune your prompts / model selection / pipeline parameters.
- **Insight:** Karpathy's pedagogy pattern continues — **minimal canonical reference implementation > tutorial.** Notice that all his most-shared work follows this shape (`micrograd`, `min-char-rnn`, `nanoGPT`, now `nes.py`). Imitate it in *your* domain — what's the 50-line canonical demo of the thing you know best? That's a viral repo waiting to be written.

**Sources:**
- [Karpathy `nes.py` gist (June 21, 2026)](https://gist.github.com/karpathy/) `[primary]`

**Tags:** `#karpathy #optimization #rl #reference-impl`

---

## <a id="5-cost-orchestration"></a>5. The "Opus orchestrator + Sonnet workers + GLM-5.2 batch jobs" stack

**Effort:** 2 hours (one-time setup) · **Leverage:** ⭐⭐⭐⭐⭐ (saves $$ every day forward)

**Pattern (synthesizing this week's signals):**

| Tier | Model | When to route |
|---|---|---|
| **Orchestrator** | Claude Opus 4.7 | Plan → annotate → "address all notes, don't implement yet" loop. Decides which subagent does what. |
| **Worker** | Claude Sonnet 4.6 | Per-file refactors, test writing, well-scoped subagent tasks |
| **Batch / cheap** | GLM-5.2 (or Gemini 3.5 Flash for tool use) | Doc generation, log summarization, anything where Sonnet would be overkill |
| **Sol/Mythos 5 tier** | GPT-5.6 Sol or Claude Mythos 5 | Reserved for actually-hard reasoning (cybersecurity, scientific reasoning) — *if you're on the cleared list* |

**Wire it (2 hours):**
1. Set up Claude Code with explicit subagent definitions (`.claude/agents/`).
2. Each subagent declares `model:` explicitly — don't let it default.
3. Add a cost-logging hook (post-task: append `/usage` output to `~/.claude-spend.log`).
4. End-of-week: total spend by subagent → optimize the long tail.

**Why it matters to you.**
- **Job:** This is the literal answer to "how do you control AI costs at scale?" — bring printout of your week's `~/.claude-spend.log` to your interview.
- **Startup:** Per-customer cost transparency is the difference between 40% gross margins and 90% gross margins. **Build it day one.**
- **Insight:** Both **GPT-5.6 ultra mode** and **Claude Code cross-repo subagents** ratified the multi-agent pattern this week. The work isn't using one anymore; it's deciding **who does what across which model at which cost.** That decision is the product.

**Tags:** `#orchestration #cost #subagents #routing #stack`

---

**Cross-reference threads:**
- The model lineup map (which models are even available to you given gating): [`01` §1–2](./01-big-lab-moves.md)
- Why these skills suddenly pay more (the funding signal): [`02` §1](./02-new-emerging.md#1-inference-week)
- Where to apply with this skill stack: [`05` §3](./05-career-and-startup.md#3-fde-apply)
