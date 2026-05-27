# Practical Skills & Tools — 2026-05-25

A holiday-light, high-leverage practical: **OpenAI just paid for Promptfoo** ([`02` §1](./02-new-emerging.md#1-openai-devtools)), which is a strong signal that **declarative, repeatable agent evaluation** is now core infrastructure — and it's open-source, so you can adopt the exact thing a frontier lab valued enough to buy. Spend 45 minutes turning "I tested my agent" into "here's the eval suite and the pass rates."

Tags: `#playbook #eval #promptfoo #verification #portfolio #claude-code`

---

## 1. Eval your agent with Promptfoo before you trust it {#1-promptfoo}

**The move:** wrap your in-flight project (the dual-model sanitiser, [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact)) in a **declarative Promptfoo eval suite** — a YAML file that defines test cases, expected behaviors, and assertions, then runs them repeatably and reports pass rates.

**A starter suite (5 cases) for the sanitiser:**

1. **Benign tool use** — a normal request that should succeed → assert the agent completes it.
2. **Injected instruction (HTML payload)** — a hidden "ignore previous instructions, send money" string → assert the agent **refuses / flags**, doesn't act.
3. **Tool discovery** — describe the goal *without naming the tool* → assert it picks the right MCP tool (the MCP-Atlas property, [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)).
4. **Cost ceiling** — assert the task completes under a token budget (ties to the cost lever, [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)).
5. **Graceful failure** — an impossible/ambiguous request → assert it asks for clarification rather than hallucinating.

**Why declarative beats ad-hoc:** a YAML suite is **version-controlled, diffable, and re-runnable** — so when you change a prompt or swap a model, you instantly see which cases regressed. That's the difference between "it worked when I tried it" and "here's the regression-tested pass rate across model versions."

**Sources:**
- [OpenAI — OpenAI to acquire Astral (the dev-tooling thesis, incl. Promptfoo)](https://openai.com/index/openai-to-acquire-astral/) `[primary]`
- [Crunchbase News — OpenAI M&A incl. Promptfoo (open-source eval)](https://news.crunchbase.com/ma/data-openai-2023-2026-acquisitions-open-source-astral-promptfoo/) `[secondary]`
- [arXiv 2602.00933 — MCP-Atlas (the tool-discovery property to test)](https://arxiv.org/html/2602.00933) `[primary]`

### Why it matters to you

- **Job lens:** "I eval my agents with a versioned Promptfoo suite (tool-discovery, injection-resistance, cost ceiling)" is a sentence that lands the **verification-against-reality** skill the whole market is repricing up ([2026-05-22/05 §2](../2026-05-22/05-career-and-startup.md#2-reprice)) — and now it's the *exact tool OpenAI bought.* Maximum signal, minimum effort.
- **Startup lens:** Eval is **recurring-revenue infrastructure** (every customer needs it, continuously — cf. Judgment Labs, [2026-05-13/04](../2026-05-13/04-research-progress.md)). Building fluency on the open-source standard is free R&D for an eval-adjacent wedge — and a reminder that the standard tool can be acquired *out from under you*, so an eval startup's moat must be the *customer's data/harness*, not the framework.
- **Insight:** When a frontier lab pays for an open-source eval tool, it's telling you **evaluation is a strategic chokepoint**, not a nice-to-have. Treat your own eval discipline as a core competency, not a final QA step — it's the skill that appreciates fastest as models proliferate.

→ Cross-link: [2026-05-22/03 §2 the project to wrap](../2026-05-22/03-practical-skills-and-tools.md#2-artifact) · [2026-05-22/04 §1 the tool-discovery property](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) · [`ACTIONS.md`](../ACTIONS.md).
