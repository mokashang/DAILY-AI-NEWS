# 03 — Practical Skills & Tools (2026-09-01)

*Hands-on: what to do today with the tools you already have.*

---

## 1. Sonnet 5 price audit + cost-router artifact (do this today) <a id="1-sonnet-5-price-audit"></a>

**What changed.** As of 00:00 today, Sonnet 5 is **$3 / $15 per MTok** (was $2 / $10 through Aug 31). If you use Sonnet 5 as your default in Claude Code, the Agent SDK, or any MCP-connected agent, **your bill is +50% today** unless you act.

**The 3-step audit.**

1. **Open the Anthropic Console → Usage dashboard.** Sort last 7 days by model. Note the % of your spend on each of Haiku 4.5 / Sonnet 5 / Opus 5 / Fable 5.
2. **Segment your workloads.** For each recurring job (Claude Code sessions, Agent-SDK runs, MCP-agent workflows):
   - **Low-stakes / high-volume** (log summarization, doc chunk classification, cheap RAG synthesis) → **Haiku 4.5** as default.
   - **Draft-quality reasoning + tool use** (most Agent-SDK work, mid-complexity Claude Code sessions) → **Sonnet 5** — still a bargain vs. Opus 5, but no longer "obvious default." Watch cost.
   - **Critical / hard-to-recover-from steps** (planner turns, code review before merge, adversarial verifier) → **Opus 5 with `effort=medium`.** The new pricing gap means the cost jump from Sonnet 5 → Opus 5-medium is smaller than it was, and Opus 5's `effort` knob gives you dial-a-quality without a full frontier cost.
3. **Add a hard budget cap** to any Agent-SDK job that runs unattended overnight or on a schedule. `max_cost_usd` in your run config is worth 30 seconds to add and saves you from waking up to a surprise.

**Ship the cost-router artifact today.**

```python
# cost_router.py — minimal cost-aware model router
# Ship this to your portfolio; explain it in an interview; refine it over time.

from anthropic import Anthropic
client = Anthropic()

# Priced per 1M tokens; update whenever the price sheet changes.
PRICES = {
    "claude-haiku-4-5":  {"in": 1.00, "out": 5.00},
    "claude-sonnet-5":   {"in": 3.00, "out": 15.00},  # bumped 2026-09-01
    "claude-opus-5":     {"in": 5.00, "out": 25.00},
}

def route(task: dict) -> str:
    """Return a model id given task metadata.

    task = {
      "criticality": "low" | "med" | "high",
      "reasoning_load": "low" | "med" | "high",
      "budget_usd_max": float,
    }
    """
    if task["criticality"] == "high" and task["reasoning_load"] == "high":
        return "claude-opus-5"
    if task["criticality"] == "high":
        return "claude-sonnet-5"
    if task["reasoning_load"] == "low":
        return "claude-haiku-4-5"
    return "claude-sonnet-5"

def call(task, messages, effort="medium"):
    model = route(task)
    extra = {"effort": effort} if model == "claude-opus-5" else {}
    return client.messages.create(model=model, messages=messages, **extra)
```

**Sources.**
- Anthropic Console (yours; primary)
- [MarkTechPost — Sonnet 5 vs 4.6 vs Opus 4.8 benchmarks (2026-07-13)](https://www.marktechpost.com/2026/07/13/anthropic-claude-sonnet-5-vs-sonnet-4-6-vs-opus-4-8-agentic-coding-benchmarks-api-pricing-and-cost-performance-tradeoffs-compared/) `[analysis]`
- [Codersera — Claude Sonnet 5 launch guide (2026)](https://codersera.com/blog/claude-sonnet-5-launch-guide-2026/) `[aggregator]`

**Why it matters to you.**
- **Job.** In an interview, "how would you route model calls" now has a concrete answer with a script attached. Bring the artifact.
- **Startup.** Your gross margin depends on this getting right today, not next month.
- **Insight.** Model pricing is now a **quarterly event** you should budget attention for — pretend it's a bond coupon reset.

`#anthropic #sonnet-5 #pricing #cost-router #interview-artifact`

---

## 2. Claude in Chrome — the workflow patterns that pay off <a id="2-claude-in-chrome-workflows"></a>

**What's shipping.** [Claude in Chrome went GA](./01-big-lab-moves.md#4-claude-in-chrome-ga) this week. Anthropic's browser-operating agent now runs in your *own* Chrome — with your auth cookies, tabs, and extensions.

**Three patterns worth trying this weekend.**

**Pattern A — "Do this while I'm at lunch."** Long-running personal workflows that require your session cookies: expense report drafts, calendar consolidations, insurance-portal exports, university-portal registration walkthroughs. This is the sweet spot Claude in Chrome nails vs. Playwright MCP (which starts a fresh session).

**Pattern B — "Explain what I'm looking at."** A tab-context reasoning surface — "summarize this PDF I've been reading," "what's the diff from the previous version of this doc I had open," "given all my open tabs about company X, draft a one-page brief." Reads like Arc's max feature, but running against Claude's frontier reasoning.

**Pattern C — "Guarded workflow for enterprise."** For work you'd otherwise ship to Playwright MCP: use Claude in Chrome inside a **dedicated Chrome profile** with only the tools you want the agent to reach. Gives you the "user-session" semantics without exposing your personal auth.

**Not the right tool when.** Reproducible enterprise workflows that need audit logs and headless execution — use Playwright MCP + Agent SDK for those. Also not the right tool for high-volume batch scraping — Claude in Chrome is a *reasoning-heavy* surface; per-page throughput is low.

**Sources.**
- [Anthropic Newsroom — Claude in Chrome GA](https://www.anthropic.com/news) `[primary]`
- [Anthropic — Building agents that reach production systems with MCP](https://claude.com/blog/building-agents-that-reach-production-systems-with-mcp) `[primary]`

**Why it matters to you.**
- **Job.** "When would you choose Claude in Chrome vs Playwright MCP?" is a live-interview question at Applied AI teams right now. Have the taxonomy ready.
- **Startup.** Pattern A + Pattern C together = a plausible **"AI ops for legacy enterprise systems without APIs"** wedge — county assessor portals, DoD SBIR submission portals, university registrar workflows. Vertical-specific, high WTP, small install base per vertical.
- **Insight.** The browser tab is now a **first-class agent-input primitive**. Add "read from open tabs" to your mental model of what an agent can do.

`#anthropic #claude-chrome #playwright #mcp #workflow`

---

## 3. Voice-agent stack refresh: GPT-Live vs. Realtime alternatives <a id="3-voice-workflows"></a>

**What changed.** [GPT-Live shipped this week](./01-big-lab-moves.md#6-openai-astra-live) — native voice model with sub-300ms latency and emotional-nuance handling; no text pipeline. If you built a voice agent on top of Whisper + GPT + TTS three months ago, it now feels wooden by comparison.

**Practical migration checklist.**

- **Baseline your current stack.** Measure first-word latency, turn-taking accuracy, and emotional appropriateness on a fixed 30-turn conversation script. Write down the numbers before you migrate.
- **Try GPT-Live** for one workflow (say: outbound cold-call research) side-by-side with your current stack. Same eval script.
- **Watch for Anthropic's counter.** They haven't shipped a native-voice frontier model publicly yet. Multi-provider hedging in voice is worth the plumbing overhead this quarter — bet-hedge on a Realtime abstraction (LiveKit's Agents, Vocode) rather than lock into a single provider.
- **Legal / recording compliance.** Sub-300ms latency invites "record everything" architectures. Get your compliance story straight before you scale.

**Sources.**
- [OpenAI Release Notes](https://help.openai.com/en/articles/9624314-model-release-notes) `[primary]`
- [Releasebot — OpenAI Aug 2026](https://releasebot.io/updates/openai) `[aggregator]`

**Why it matters to you.**
- **Job.** Voice-agent teams (Sierra, Decagon, PolyAI, Retell, Bland) hire fast around model launches. Portfolio artifact: a 10-minute demo of your voice agent handling three "hard turns" (interruption, correction, emotional escalation).
- **Startup.** Voice-agent unit economics just changed. If your cost per minute of conversation dropped meaningfully, revisit your pricing — the market will re-price this quarter.
- **Insight.** Voice is the **highest-differentiation surface** at the moment where the "vibe" of your app depends on model quality. Great voice UX = defensible product differentiation for the next 12–18 months at least.

`#openai #gpt-live #voice #realtime #latency`

---

## 4. This weekend's artifact: Sonnet 5 → Opus 5 tiered agent + cost trace <a id="4-this-weekends-artifact"></a>

**The build.** One repo, two hours, three interview questions answered.

**Repo structure.**
```
tiered-agent-cost/
├── README.md              # what you built and why (with today's pricing table)
├── cost_router.py         # the router from §1
├── agent.py               # a small task-loop that plans (Opus 5 effort=med),
│                          # implements (Sonnet 5), verifies (Haiku 4.5)
├── mcp_server/            # a 3-tool MCP server (a real one — files, http, sqlite)
├── eval/
│   ├── tasks.jsonl        # 20 hand-crafted tasks with expected outcomes
│   ├── run_eval.py        # runs the agent against tasks, records cost per step
│   └── results.md         # cost per task, quality per task, model choice per step
└── notebook.ipynb         # 3 comparison charts:
                           #   (1) cost per task by tier vs all-Opus vs all-Sonnet
                           #   (2) quality (task success %) by tier
                           #   (3) cost / quality Pareto frontier — where the tiered
                           #       agent lands vs the single-model baselines
```

**Interview questions this artifact answers.**
1. "How do you think about cost when running an agent?" → point at `cost_router.py`, walk through the classification and the results.
2. "Give an example of an eval you designed." → point at `eval/`, walk through the 20-task grader.
3. "Where would you use Opus 5 vs Sonnet 5?" → point at the Pareto chart in `notebook.ipynb`.

**Ship steps.**
- Sat AM (2 hrs): write the router + agent + MCP server; smoke-test with 3 tasks.
- Sat PM (2 hrs): write the 20-task eval; run once end-to-end; capture cost + quality.
- Sun AM (1 hr): notebook + charts + README.
- Sun PM: post the repo link somewhere your target-lab recruiters see it (LinkedIn, X, personal blog). Add it to your [ME.md active portfolio artifacts](../ME.md#active-portfolio-artifacts).

**Sources.**
- [Anthropic — Building agents that reach production systems with MCP](https://claude.com/blog/building-agents-that-reach-production-systems-with-mcp) `[primary]`
- [Developers Digest — Claude Code Agent Teams, Subagents & MCP: The 2026 Playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) `[analysis]`
- [MakerKit — Claude Code Best Practices for Production SaaS (2026)](https://makerkit.dev/blog/tutorials/claude-code-best-practices) `[analysis]`

**Why it matters to you.**
- **Job.** One weekend, three interview-question answers, one artifact link in every application from now on.
- **Startup.** The router pattern generalizes to your own product — you'll have a live reference for your own gross-margin work.
- **Insight.** **Making the invisible visible is the highest-value skill this quarter.** Cost tracing, quality-per-step tracing, model-choice-per-step tracing are all instances of the same thing.

`#weekend-artifact #mcp #agent-sdk #cost-router #portfolio`

---

## 5. AGENTS.md + subagents + hooks — the 2026 project scaffolding <a id="5-project-scaffolding"></a>

**What's converged.** The last two months of Claude Code / Agent SDK writeups all say the same thing:

1. **Structural decisions matter more than prompts.** AGENTS.md rules, skills, MCP servers, subagents.
2. **Ship reference code first.** AI extends existing patterns; without them, it invents problematic ones.
3. **AGENTS.md gets MUST / MUST NOT rules,** not aspirational guidelines.
4. **Start with one main agent + specialists only when context separation clearly helps.** For a refactor: main (plan/integrate) + 1–2 implementation subagents (backend/frontend) + test subagent + review subagent.
5. **Hooks enforce project rules:** run tests before stopping, block edits to generated files, lint before commits, require issue IDs in branch names, run security scans after dependency changes.

**Sample `AGENTS.md` skeleton to copy tonight.**
```markdown
# Project rules for AI agents

## Must
- Update the test file when changing behavior in `src/`.
- Use the repo's typed logger — do not `print`.
- Run `make check` before proposing a commit.

## Must not
- Do not edit files in `generated/`.
- Do not add dependencies without an entry in `docs/deps.md`.
- Do not commit files matching `.env*` or `secrets/*`.

## Style
- Prefer editing over rewriting.
- Cite the file:line when you reference existing code.
- Comment only when the "why" is non-obvious.
```

**Sources.**
- [MakerKit — Claude Code Best Practices for Production SaaS](https://makerkit.dev/blog/tutorials/claude-code-best-practices) `[analysis]`
- [Developers Digest — Claude Code Agent Teams, Subagents & MCP](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) `[analysis]`
- [MCP Directory — Claude Code Best Practices 2026](https://mcp.directory/blog/claude-code-best-practices) `[aggregator]`
- [Claude Directory — Best Claude Code setups (August 2026)](https://www.claudedirectory.org/for/ai-agent-development) `[aggregator]`

**Why it matters to you.**
- **Job.** "How do you set up a repo for AI agents to work in effectively?" is a live-interview question at every Applied AI team. Have your AGENTS.md pattern language ready.
- **Startup.** These scaffolding decisions are the difference between a startup that ships weekly and one that ships monthly. Adopt the pattern once, apply to every repo.
- **Insight.** The **repo is the interface** for AI agents. Treat AGENTS.md the way you'd treat a public API's docs page.

`#claude-code #agents-md #subagents #hooks #scaffolding`
