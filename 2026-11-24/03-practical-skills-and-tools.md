# Practical Skills & Tools — 2026-11-24

Hands-on workflows, tools, prompting patterns, productivity hacks. **Act on these this week.**

---

## 1. Claude Code shipped 2.1.317 → 2.1.330 this month — what to turn on tonight

**What changed.** The Claude Code changelog ran a dense cadence in November (versions 2.1.317 through 2.1.330). Four releases matter for your weekend workflow:

- **2.1.319 (Nov 6) — MCP tool calls auto-background as tasks.** When an MCP server invokes a tool call that would block, Claude Code **moves it to the background immediately** and returns the result as a `<task-notification>` when it finishes. You stop blocking the agent loop on slow tools.
- **2.1.325 — nested skill loading fix.** `.claude/skills/` inside `--plugin-dir` plugins **no longer loads from a session started above them**. Start Claude Code **inside the plugin folder** instead. Catches a silent-failure footgun.
- **2.1.329 (Nov 23) — MCP server JSON via stdin.** Pass MCP configuration **via stdin** instead of `--mcp-config` flags on the command line — so **API tokens never land in your shell history or process-list**. Required reading if you're onboarding a teammate to an MCP server with a secret.
- **2.1.330 — Enterprise sign-in, built-in charts, self-hosted runner controls, VS Code workflow tools.** The "charts in the terminal" change is the biggest quality-of-life win in months: Claude Code can now render time-series + bar charts inline without a browser tab.

**Sources.**
- [primary] [Anthropic Claude Code Changelog](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
- [aggregator] [Releasebot: Claude Code Updates — November 2026](https://releasebot.io/updates/anthropic/claude-code)
- [aggregator] [Gradually.ai: Claude Code Changelog (November 2026)](https://www.gradually.ai/en/changelogs/claude-code/)
- [analysis] [Medium / Abhinav Dobhal: What Changed for Claude Code Skills This Week](https://medium.com/@abhinav.dobhal/what-changed-for-claude-code-skills-this-week-and-what-two-trending-skill-libraries-get-right-819535ba5b93)

**Do this tonight (5 min).** Upgrade to 2.1.330, then:

```bash
claude --version   # expect 2.1.330+
# Load MCP config via stdin so tokens never hit history
cat ~/.mcp/anthropic-ant-stock-price.json | claude --mcp-config-stdin
```

Then open **one** of your existing projects and try `/plan` + a `SubagentStop` hook (shipped in 2.1.318 per the Nov 14 TLDR). The whole Nov 2026 Claude Code update is backward-compatible — don't overthink the upgrade.

**Why it matters to you.**
- **Job.** Interviewer asks "how do you keep API tokens safe when sharing MCP configs?" → you answer "stdin-JSON in 2.1.329." Zero other candidates will have that answer. Differentiator.
- **Startup.** Backgrounding MCP tool calls (2.1.319) **removes the latency tax** on multi-tool agent loops — your product's p95 just dropped without you doing anything.
- **Insight.** The release cadence is now ~weekly. Subscribe to the changelog RSS (or the Gradually.ai mirror) and **do a 10-min Friday skim**. It compounds.

`#claude-code #mcp #skills #cli`

---

## 2. Ship the "MemFail Diagnostic" MCP server this weekend — the single best FDE portfolio artifact in 2026 {#2-memfail-mcp}

**What to build.** A tiny MCP server with **three tools** that implements the failure modes from the Nov 2026 agent-memory arXiv wave (see [`04`](./04-research-progress.md)). Call it `memfail-mcp`. API shape:

```python
# memfail_mcp.py
from fastmcp import FastMCP

app = FastMCP("memfail-mcp")

@app.tool()
def simulate_memory_failure(mode: str, trace: list[dict]) -> dict:
    """
    Inject a named failure mode into an agent trace.
    Modes: 'stale' (outdated fact), 'conflict' (contradictory facts),
           'drift' (gradual value shift), 'injection' (adversarial),
           'forget' (dropped key fact). Named from arXiv 2611.14320
           and MemFail (listed Nov 24).
    """
    ...

@app.tool()
def score_recovery(before: dict, after: dict) -> dict:
    """
    Score how well an agent recovered from an injected failure.
    Returns {task_success, memory_hygiene, cost_delta}.
    """
    ...

@app.tool()
def report(run_id: str) -> dict:
    """
    Emit a BioMem-style JSON summary with per-mode error rates and
    a confidence band, suitable for pasting into a PR review.
    """
    ...

if __name__ == "__main__":
    app.run()
```

**Then ship it.** Put it on GitHub, write a 200-word README citing **BioMem (2611.13426)**, **Prospective Memory (2611.05731)**, **Evidence-Linked Memory (2611.14320)**, and **MemFail (Nov 24 listing)**. Record a 60-second Loom of it running against a toy agent in Claude Code. Link it in your LinkedIn headline.

**Why it matters to you.**
- **Job.** This single artifact checks **four 2026 FDE-interview boxes**: (1) MCP server authoring (Anthropic's most-asked), (2) eval/benchmark design, (3) agent-memory (the Nov hot lane), (4) you can read + implement from arXiv. $160–550K TC roles will **interview you faster** for this one repo than for any coursework GitHub.
- **Startup.** A **"memory hygiene" dashboard** is a plausible wedge-10 pre-seed pitch. The MCP server is the demo artifact. Three VCs this week funded adjacent theses (LanceDB $57.5M, Model ML $250M).
- **Insight.** **Running the arXiv paper against your own system beats citing it 10×.** The repo + Loom + README is 3–5 hours of work and produces an interviewable artifact that stays current for 6+ months.

`#mcp #memory #eval #portfolio`

---

## 3. Benchmark Fable 5.2 vs. Gemini 4 Neon on YOUR workflow — not on theirs

**Why.** Both vendors shipped **"we're #1 on an index"** claims in the same week (Fable 5.2 on Artificial Analysis Intelligence Index v5 at 65; Neon on Artificial Analysis Coding Agent Index at 58.64). Vendor benchmarks collapse once you measure on **your** prompts.

**Pattern (90 min).** Pick **10 prompts you actually ran this month** — real ones from your work, not textbook. For each:

1. Run `claude -p "$prompt" --model claude-fable-5-2`.
2. Run the same through `gcloud ai gemini-cli --model gemini-4-neon`.
3. Score each on **(a) task success (binary), (b) latency (ms), (c) output cost ($)**. No LLM judge — human score, 10 prompts max.
4. Dump to CSV. Chart in Claude Code's new built-in charts (2.1.330).

**Expected pattern.** Gemini 4 Neon will beat Fable on coding-agent tasks with **Google Antigravity** as the harness (SWE-sweep jumps from 12.8% → 39.0% there). Fable will beat Neon on long-form knowledge-worker tasks. Routing wins.

**Why it matters to you.**
- **Job.** This becomes a **blog post + PR-ready résumé bullet**: "I benchmarked Fable vs. Neon on 10 production prompts and documented a routing policy that cuts cost 42% without accuracy loss." Every FDE recruiter in Q1 is going to ask for exactly this.
- **Startup.** If you ship a product, **routing policy IS a core competitive asset**. Published eval = marketing moat.
- **Insight.** The harness swing is **>25pp on a single model** (Neon in mini-SWE vs. Antigravity). **The harness choice is now a more important variable than the model choice** on agentic tasks.

`#eval #routing #benchmark #fable #neon`

---

## 4. ChatGPT Wallet pattern (Nov 13) — the agent-commerce primitive, repro'd locally

**What.** OpenAI shipped **ChatGPT Wallet** — biometric purchase approval inside the chat flow, agent-initiated purchases, Pro-tier US preview. **This is the agent-commerce trigger.** For once, it's a primitive you can reproduce locally end-to-end and learn the architecture from.

**The pattern (3-tier).**

```
agent (Claude Fable 5.2)
  │
  ├─ 1. propose(intent, amount, merchant)           ← LLM planning
  │
  ├─ 2. policy_check(intent, user_rules)            ← rules engine (yours)
  │       └─ returns {allow | reject | escalate}
  │
  ├─ 3. require_biometric_approval(challenge_id)    ← platform (Apple/Android/WebAuthn)
  │       └─ returns signed JWT
  │
  └─ 4. settle(JWT, Stripe/Plaid/Adyen)             ← payment rail
```

**Build a hobby version this weekend.** Use **WebAuthn** for biometric, **Stripe test mode** for settlement, **a trivial Python policy rules engine** (max $20, whitelist merchants). Ship it as a Streamlit app. The single artifact tells an interviewer you understand (a) agent plans-vs-acts split, (b) policy enforcement at the chat layer, (c) payment-rail integration.

**Sources.**
- [primary] [OpenAI ChatGPT Release Notes (Releasebot mirror)](https://releasebot.io/updates/openai/chatgpt)
- [analysis] [ScriptByAI: ChatGPT Wallet timeline entry](https://www.scriptbyai.com/timeline-of-chatgpt/)

**Why it matters to you.**
- **Job.** Payments + AI is a **new job family** (see also LINQ in [`02`](./02-new-emerging.md) for the telephony analog). Stripe, Adyen, Plaid, Rutter are all hiring for exactly this. Pay: $220–320K base.
- **Startup.** Adjacent wedges that OpenAI will NOT ship: (a) **B2B** agent-procurement (purchase orders, approvals, audit trail), (b) **marketplace-side** APIs ("sell agent-consumable things"), (c) **fraud detection** on agent-initiated purchases.
- **Insight.** OpenAI opens a primitive, a wrapper layer dies, and **three adjacent wedges open**. Act fast on the adjacent ones.

`#chatgpt-wallet #agent-commerce #payments #primitives`

---

## 5. llama.cpp 1.0 as the serving backbone for sovereign-stack prototypes {#5-llama-cpp-1}

**What.** llama.cpp **v1.0.0 stable** this week. **Semantic versioning + 150+ model architectures** = API stability, you can **actually commit to it in prod**. (Context in [`02` §6](./02-new-emerging.md#6-llama-cpp-v1-0-0-stable--semantic-versioning--150-model-architectures).)

**Weekend recipe.** Spin up a **sovereign-stack prototype** on $5/hour hardware:

```bash
# 1. Pull a non-US frontier open-weight (Qwen 3.8, GLM 5.3, Kimi K3 70B)
huggingface-cli download Qwen/Qwen3.8-32B-Instruct-GGUF --local-dir models/qwen

# 2. Serve via llama.cpp 1.0 with OpenAI-compatible API
llama-server --model models/qwen/qwen3.8-32b-q4_k_m.gguf \
             --port 8080 --n-gpu-layers 999 --ctx-size 32768

# 3. Point any OpenAI SDK at it — client code doesn't change
export OPENAI_BASE_URL=http://localhost:8080/v1
openai api chat.completions.create -m qwen3.8-32b --role user -g 'Plan my day.'
```

**Why it matters to you.**
- **Job.** **"I run production inference on non-US open-weight models via llama.cpp 1.0"** is a résumé line that gets you into **regulated-industry AI jobs** (EU banks, healthcare systems, defense primes, DoD-adjacent consultancies) at $220–280K base. Rare in US candidates right now.
- **Startup.** **Sovereign AI** customers in Europe, Singapore, Middle East, and defense pay a premium for this stack. The *market* is already there (see [Anthropic × Singapore MOU from 2026-10-14](../2026-10-14/01-big-lab-moves.md)). The *delivery team* is what's missing.
- **Insight.** Three converging trend lines — **(a) open-weight frontier is non-US, (b) llama.cpp 1.0 API stable, (c) NVIDIA Rubin + custom silicon rack-scale deployment** — make the **sovereign-stack prototype** a credible 2027 production configuration, not a wargame.

`#llama-cpp #open-source #inference #sovereign`

---

## 6. Simon Willison's `llm` + reasoning traces + tool-use — the "pipe-native" workflow stays underrated

**What.** Simon Willison continues to publish the tightest practitioner workflows for CLI-native LLM use. **Nov 11–12 posts** cover reasoning traces, the LLM command-line tool's tool-use series, and Gemini Hydrogen as the new free-tier model powering Google Search's AI features.

**Pattern — ship one of these this week.** Pick the simplest:

```bash
# (a) Review a diff and propose a commit message
git diff HEAD | llm -m claude-fable-5-2 --system 'Write a conventional commit message.'

# (b) Triage inbound GitHub issues against your own rules
gh issue list --json title,body | llm -m gemini-4-neon --tool web_search

# (c) Turn any one-off task into a reusable `llm -t` template
llm templates edit summarize-standup
# Then: `pbpaste | llm -t summarize-standup`
```

**Sources.**
- [primary] [Simon Willison's Weblog — LLM tool-use tag](https://simonwillison.net/tags/llm-tool-use/)
- [primary] [Simon Willison's Weblog — Gemini Hydrogen post (Nov 12)](https://simonwillison.net/tags/llms+ai/)

**Why it matters to you.**
- **Job.** The *shortest* path to **"I automate my own workflow with LLMs"** that an interviewer can parse in 30 seconds is a one-screen `llm`-pipe demo in a terminal recording. Every FDE job asks for this; almost no candidate has it ready.
- **Startup.** CLI-native workflows are **where internal-tooling startups differentiate** — see also the Oct 14 Claude Haiku 5.5 "effort levels" wave, which pairs perfectly with `llm`'s per-template model selection.
- **Insight.** A new LLM product with a terminal UX **wins the practitioner mindshare faster** than the same product with a web UI. Learn why Willison's blog has outsized practitioner influence.

`#cli #llm-tool #willison #workflow`

---

## This week's action checklist (do all five)

- [ ] Upgrade Claude Code to 2.1.330; adopt **stdin-JSON MCP config** (5 min).
- [ ] Ship **memfail-mcp** on GitHub with README + Loom (5 hours — **Sat or Sun**).
- [ ] Run the **Fable vs. Neon 10-prompt benchmark** and publish the CSV + chart (90 min).
- [ ] Prototype the **ChatGPT-Wallet-pattern** biometric-approval payment flow with Stripe test mode (3 hours).
- [ ] Clone + run the **llama.cpp 1.0 + Qwen 3.8 sovereign-stack** on your own hardware or Lambda cloud (30 min).

The **#1 highest-leverage one** is the **memfail-mcp** build — it feeds directly into [`04`](./04-research-progress.md) and [`05`](./05-career-and-startup.md) and is the single most interviewable artifact on this list.
