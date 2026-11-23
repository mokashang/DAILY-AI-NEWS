# Practical Skills & Tools — 2026-06-23

The skill of the week is **model re-routing under capacity pressure**, not new prompting. Two acute tasks today: (1) re-route your model defaults given the Fable 5 plan-limit removal in [`01` §1](./01-big-lab-moves.md#1-fable-5-plan-removal); (2) try Daybreak's Codex Security plugin (free tier in research preview) on your own repos before the partner-program closes the door on individual users. Both are ~30-minute actions you can take tonight.

Tags: `#tools #skills #claude-code #cost #routing #cybersecurity #codex`

---

## 1. The model re-route playbook for the next ~2 weeks {#1-reroute}

**The acute problem:** Until today, **Claude Fable 5 on a Pro / Max plan was effectively unlimited heavy-model usage** for daily dev work. As of this morning, Fable 5 bills against credits at **$10/M in · $50/M out** (2× Opus 4.8) — so if your routine was "use Fable 5 by default in Claude Code / Cursor / your harness," you're now paying premium-token rates without realizing it. **Set the default down a tier today.**

### The 30-minute fix

**Step 1 — set defaults (5 min):**

```bash
# Claude Code (CLI): set the project default
# In .claude/settings.json (per-project) or ~/.claude/settings.json (global):
{
  "model": "claude-sonnet-4-6",       # NOT fable-5
  "fallback_models": ["claude-opus-4-8"]
}
```

For Cursor: `Cmd+Shift+P → Cursor: Select Model → claude-sonnet-4-6` and pin it.

For your own SDK harness: set `model="claude-sonnet-4-6"` as the explicit default in your `client.messages.create()` calls. Only escalate to Opus 4.8 / Fable 5 with a routing rule, not by accident.

**Step 2 — declare a routing rule (10 min):**

The pattern that survives the capacity squeeze is:

| Step type | Model | Why |
|---|---|---|
| **Planning / decomposition** | **Opus 4.8** | One-shot, expensive but worth it for the plan quality |
| **Worker / implementation** | **Sonnet 4.6** | The vast majority of tokens. Cheap enough to be the daily driver. |
| **Verifier / judge / eval** | **Fable 5** (or Haiku 4.5) | Per-step, low input/output ratio — Fable 5's 2× cost amortizes over many cheap-worker rollouts; Haiku 4.5 is the budget alternative |
| **High-risk one-shot** (security audit, vulnerability patch) | **GPT-5.5-Cyber** (see [`§2`](#2-codex-security)) | Domain-finetuned; treat as a specialty tool, not a default |

Reference: the **Opus-orchestrator + Sonnet-worker** pattern that was already saving ~40% in [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) — Fable 5 now moves *out* of the orchestrator slot and *into* the verifier slot. That's the only meaningful structural change to last month's playbook.

**Step 3 — log cost per step (15 min):**

Wrap your model client to log `(model, prompt_tokens, completion_tokens, dollars, step_role)` for one week. The simplest implementation in Python:

```python
import json, time
from anthropic import Anthropic
client = Anthropic()

PRICES = {  # USD per 1M tokens, June 23 2026
  "claude-fable-5":    {"in": 10.00, "out": 50.00},
  "claude-opus-4-8":   {"in":  5.00, "out": 25.00},
  "claude-sonnet-4-6": {"in":  1.00, "out":  5.00},
  "claude-haiku-4-5":  {"in":  0.20, "out":  1.00},
}

def call(model, role, messages, **kw):
    r = client.messages.create(model=model, messages=messages, **kw)
    p = PRICES[model]
    cost = (r.usage.input_tokens * p["in"] + r.usage.output_tokens * p["out"]) / 1e6
    with open("cost.jsonl", "a") as f:
        f.write(json.dumps({
            "t": time.time(), "model": model, "role": role,
            "in": r.usage.input_tokens, "out": r.usage.output_tokens, "$": round(cost,4)
        }) + "\n")
    return r
```

(Prices listed are illustrative API list rates; verify against [Anthropic pricing](https://www.anthropic.com/pricing) tonight. The point isn't the exact numbers — it's that you have a `cost.jsonl` to grep at the end of the week.)

### Why this is the actual practical skill of June 2026

- **Without the log**, you can't see when a "cheap" agent is silently calling Fable 5 in a sub-tool. (This is the dominant cost-blow-up failure mode for agent frameworks right now.)
- **With the log**, you can ship a chart in your portfolio that says *"my agent stack cost $X.YY per task on average, with Z% of spend at the verifier step"* — which is the answer to the FDE/Solutions-Engineer interview question **"how would you think about cost on a production deployment?"**
- This is the **artifact** to ship this weekend — see [ME.md "active portfolio artifacts"](../ME.md). One week of `cost.jsonl` + a 1-page writeup = a real interview talking point.

### Sources for the routing pattern
- [Anthropic — Claude pricing](https://www.anthropic.com/pricing) `[primary]`
- [Anthropic — Building agents with the Claude API](https://docs.anthropic.com/en/docs/agents-and-tools) `[primary]`
- [Anthropic — Prompt caching guide](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching) `[primary]` — still the best ROI mitigation; 60–90% input savings ([2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md))
- [Developers Digest — Fable 5 Leaves Your Claude Plan on June 22](https://www.developersdigest.tech/blog/claude-fable-5-june-22-deadline) `[analysis]`

### Cross-links
[`01` §1 Fable 5 plan removal driving this](./01-big-lab-moves.md#1-fable-5-plan-removal) · [2026-05-22/03 §1 the orchestrator/worker baseline](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [2026-05-21/03 the orchestration stack writeup](../2026-05-21/03-practical-skills-and-tools.md).

---

## 2. Try OpenAI's Codex Security plugin on your repos — free tier is still open {#2-codex-security}

**The opportunity:** OpenAI's **Codex Security plugin update yesterday** ([§2 in 01](./01-big-lab-moves.md#2-openai-daybreak)) is in **research-preview tier** for individual / small-team accounts before the **partner-program rollout closes the discount window**. If you do it this week, you get to put **"shipped a vuln-patch PR validated by Codex Security against an open-source repo"** on your portfolio for free.

### What to do (45 minutes total)

1. **Pick an open-source project** you've already cloned and use. Bonus if it has any kind of historical CVE — a Node/TS web app with `axios`-version-constrained deps, or a Python service with old `requests`. (Avoid huge monorepos; you want a clean scan.)
2. **Install the Codex Security plugin** from the OpenAI dashboard → Codex section → "Codex Security (Research Preview)". Connect the repo. Trigger a scan.
3. **Read the report.** Pick **one** vulnerability whose proposed patch is non-trivial (not just a version bump). Apply the patch in a branch.
4. **Run the project's tests** (or write a 5-minute smoke test if there are none). **Document what changed** in a short README. Push the branch.
5. **Write a one-paragraph reflection**: where did Codex Security's reasoning hold up, where did it propose a fix that regressed behavior, where did your own test catch something the plugin missed.

That's a defensible mini-artifact: **"I evaluated GPT-5.5-Cyber-backed patch suggestions on a real open-source repo and shipped the validated change"** — and it directly resumes the dual-model sanitiser project you've been carrying since [2026-05-20/05 §3](../2026-05-20/05-career-and-startup.md#3-safety-project).

### Why this is timely vs. evergreen

- The **partner program** will likely raise the price (or close the free preview) within 60–90 days as Daybreak rolls out commercially.
- The **EO cyber-clearinghouse half** ([2026-05-22/01 §1](../2026-05-22/01-big-lab-moves.md#1-eo-postponed)) is the most likely policy track to survive — being **publicly on-the-record** as having done this kind of work in **June 2026** is a real differentiator if you apply to an AI-cyber role in Q3/Q4 ([`05` §2](./05-career-and-startup.md#2-cyber-lane)).
- The **Anthropic-Mythos jailbreak** that triggered today's Fable 5 plan-pull originated from a *narrow* vulnerability-disclosure demo — i.e., the same kind of work you'd be doing. You'd want to be on the *defender* side of that conversation.

### Sources
- [OpenAI — Daybreak (product page)](https://openai.com/daybreak/) `[primary]`
- [OpenAI — Daybreak: Tools for securing every organization in the world](https://openai.com/index/daybreak-securing-the-world/) `[primary]`
- [Help Net Security — OpenAI wants AI to fix vulnerabilities, not just find them](https://www.helpnetsecurity.com/2026/06/23/openai-expanded-daybreak-cybersecurity-initiative/) `[secondary]`
- [Cybersecurity Insiders — OpenAI Daybreak: AI Security Moves From Discovery to Patch Velocity](https://www.cybersecurity-insiders.com/openai-daybreak-ai-security-patching-codex-security/) `[analysis]`

### Cross-links
[`01` §2 the Daybreak expansion](./01-big-lab-moves.md#2-openai-daybreak) · [`05` §2 the AI-cyber hiring lane](./05-career-and-startup.md#2-cyber-lane).

---

## 3. The "OpenAI Codex-Maxxing for Long-Running Work" pattern (lighter-weight read) {#3-codex-maxxing}

**What it is:** On **June 22, OpenAI published an "AI Adoption" piece titled "Codex-Maxxing for Long-Running Work"** — a tactical write-up of patterns OpenAI's own engineers use to keep Codex on-task on multi-hour / multi-day workstreams (the same long-horizon pattern Anthropic calls "Managed Agents" / "Dreaming"). Practical patterns called out:

- **Plan-mode first, implement-mode second** — don't let the agent fuse the two; treat planning as a separate phase you review (same shape as the "Address all notes, don't implement yet" reliability loop from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)).
- **Checkpoint files** at each major boundary so the agent can resume from state, not from scratch.
- **Async + email-style updates** — long-running runs notify you via push/email on completion, not by streaming chat tokens.
- **Treat `samsung-style` mobile deployments as a first-class control surface** (per the Samsung-Electronics ChatGPT+Codex rollout on June 21) — i.e., the phone is now the cockpit for an async coding agent.

### How to use it tonight

Pick the one Claude Code session you ran for >15 minutes last week. Re-run it with:
- An explicit `PLAN.md` written first (commit before any code change)
- A `CHECKPOINTS.md` file the agent appends one line to at each major step
- Final notification via a push hook (Codex / Claude Code both support `Stop` and `SessionEnd` hooks — see [Claude Code docs](https://docs.anthropic.com/en/docs/claude-code/hooks))

Tag the resulting agent run on your portfolio. This is the same shape you'd build at an FDE role; the muscle memory pays off in interviews.

### Sources
- [OpenAI News — Codex-Maxxing for Long-Running Work (June 22 2026)](https://openai.com/news/) `[primary]`
- [OpenAI News — Samsung Electronics is bringing ChatGPT and Codex to employees](https://openai.com/news/) `[primary]`
- [Anthropic — Claude Code hooks docs](https://docs.anthropic.com/en/docs/claude-code/hooks) `[primary]`
