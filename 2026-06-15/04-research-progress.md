# Research Progress — 2026-06-15 (Monday)

`#tau2 #benchmarks #agent-applied #arxiv`

Short today. The substantive read was [yesterday's `04`](../2026-06-14/04-research-progress.md). Today is the **application step** — applying τ²-Bench to the router shim you shipped last night.

---

## 1. Applying τ²-Bench to the router shim (the 20-minute upgrade) {#1-tau2-applied}

**Why apply it now.** [Yesterday's `04` §1](../2026-06-14/04-research-progress.md#1-tau2-erl) introduced τ²-Bench as a dual-control conversational-agent benchmark. **Your router shim from [`03` §2](../2026-06-14/03-practical-skills-and-tools.md#2-anthropic-stack-hedge)** is the natural unit-under-test. Today's upgrade: add a 30-prompt τ²-style eval into the same repo so any change to the router (model order, new vendor added) gets graded automatically.

**The 30-prompt eval surface (20 minutes to build).**

Pick **one** τ² domain to mirror — **Retail** is the most reusable (you'll touch carts, orders, refunds, account profiles). Then build:

| Component | Implementation |
|---|---|
| **Simulated user (with tools)** | A Sonnet 4.6 mini-LLM with a single "modify_cart" tool. The simulated user is asked to e.g. "ask the agent to refund my purchase from May 28, but I have to add a new shipping address first." |
| **Agent under test (your router shim)** | Your `chat()` from `models.py` + an MCP server with `lookup_order`, `issue_refund`, `update_address`. |
| **30 task prompts** | Constructed as `(user_intent, expected_final_state_diff)`. Mirror the τ-bench format (the original 2024 paper is 130 tasks). |
| **Grading** | State-diff approach from [Agent-Diff (yesterday's `04` §2)](../2026-06-14/04-research-progress.md#2-agent-diff). Pass = the orders table + accounts table match the expected post-state. |
| **CI integration** | One `pytest` test per prompt; `make eval` runs the 30 in parallel against any committed router config. |

**Why 30 prompts is enough.** τ²-Bench's published numbers vary by single-digit percentages across runs at this scale. Statistical significance is a future-week problem; today's goal is "every router change has a measurable grade I can show in an interview."

**Sources.**
- `[primary]` [arXiv:2506.07982 — τ²-Bench](https://arxiv.org/abs/2506.07982)
- `[primary]` [GitHub: sierra-research/tau2-bench](https://github.com/sierra-research/tau2-bench) (read the README + the Retail task schema; copy the structure)
- `[primary]` [arXiv:2602.11224 — Agent-Diff (state-diff grading)](https://arxiv.org/abs/2602.11224)
- `[primary]` [τ-bench (2024 original) — arXiv:2406.12045](https://arxiv.org/abs/2406.12045)

**Why it matters to you.**

- **Job ·** "I have a τ²-Retail-style eval + state-diff grading wired into CI" is a one-sentence killer answer for Sierra Customer Engineering, Anthropic Solutions, and any vertical-CX startup interview.
- **Startup ·** Build the eval first; then build the wedge. The Retail domain you copied is intentionally generic — swap to Travel / Healthcare / Logistics as you narrow your wedge. **The eval is the moat.**
- **Insight ·** Every benchmark-paper README is a free tutorial in production-quality eval design. Read the τ²-Bench README cover-to-cover; the format is a template you'll re-use across the next year.

`#tau2 #applied #eval #portfolio-artifact`

---

## 2. Carry: this week's reading queue {#2-reading-queue}

| Paper | Priority | Why |
|---|---|---|
| **τ²-Bench** (arXiv:2506.07982) | High | Today's §1 application step. |
| **Experiential Reflective Learning** (arXiv:2603.24639) | High | Yesterday's §1; deploy-this-week self-improvement loop. |
| **Agent-Diff** (arXiv:2602.11224) | Medium | Today's §1 grading layer. |
| **Externalization in LLM Agents** (arXiv:2604.08224) | Low (vocab) | Yesterday's §3; vocabulary upgrade for architecture interviews. |
| **Agentic RL Survey** (arXiv:2509.02547) | Low (weekend) | Unified taxonomy for "agents that learn." Read if you have leisure time. |

`#reading-list #weekly`

---

## Cross-page

- See [`03` §1–2](./03-practical-skills-and-tools.md) for the router shim this page upgrades.
- See yesterday's [`04` §1](../2026-06-14/04-research-progress.md#1-tau2-erl) for the full τ²-Bench + ERL primer if you skipped it.
