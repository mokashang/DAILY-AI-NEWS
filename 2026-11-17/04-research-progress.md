# Research Progress — 2026-11-17

Weekly arXiv pull, filtered for CS-grad-relevant signal. **Three of the five November 2026 batch papers I'm tracking converge on one thesis: *evaluation* is now the bottleneck, not capability.** Headline: **SLATE** (long-horizon API-selection benchmark for e-commerce agents, replaces LLM-as-judge with a deterministic simulator), **Decision Context** (persistent behavioral learning across sessions — the "why don't agents learn from corrections" paper), and **Knowing When to Intervene** (causal evaluation of agents). Plus two secondary: **Nudging Decision Models** (steering fast generation-free agents) and **Multi-Agent Judgment Aggregation** (when multi-agent reasoning *hurts*).

Tags: `#arxiv #agents #eval #benchmarks #memory #multi-agent`

---

## 1. SLATE: long-horizon API-selection benchmark + simulator for e-commerce agents (arXiv 2611.03982) {#1-slate}

**The claim:** Existing tool-use benchmarks either (a) expose too few tools, (b) test single-step calls, or (c) grade multi-step behavior with subjective **LLM-as-a-judge** scores. **SLATE** is a public benchmark + simulator + evaluation harness for **long-horizon API selection** in e-commerce, grading agents deterministically against ground-truth trajectories.

- Submitted **2026-11-02**.
- Comes with a **released simulator** + **harness**, not just a dataset.
- Positioned as a bridge between static tool-use benchmarks (ToolFailBench, RUT-Bench) and real production workloads.

**Sources:**
- [papers.cool — arXiv 2611.03982 SLATE listing](https://papers.cool/arxiv/2611.03982) `[primary]`
- [alphaxiv — ToolFailBench (arXiv 2607.04686), same lineage](https://www.alphaxiv.org/abs/2607.04686) `[primary]`
- [alphaxiv — Beyond the Leaderboard: tool-use + planning + reasoning failures (arXiv 2607.05775)](https://www.alphaxiv.org/abs/2607.05775v1) `[primary]`

### Why it matters to you

- **Job lens:** Any **FDE / solutions / applied-AI role at an e-commerce company** (Shopify, Instacart, DoorDash, Amazon, HubSpot) will touch this benchmark within 6 months. Interview prep: be able to describe **the LLM-as-judge pitfall** and **what deterministic trajectory grading fixes**.
- **Startup lens:** **E-commerce agent orchestration** is a legitimate 2027 wedge (vertical-AI, high buy-intent, measurable ROI). SLATE gives you a **shared evaluation axis** with buyers — if you can publish your numbers, you're trusted.
- **Insight:** **The benchmark stack is bifurcating.** Static benchmarks (MMLU, HumanEval) are dying; **task-simulator + harness** is the new shape (Scale AI RLI, SLATE, Tool Decathlon). Build eval harnesses as a career skill.

---

## 2. Decision Context: Persistent Behavioral Learning for AI Agents (arXiv 2611.08644) {#2-decision-context}

**The claim:** LLM agents **don't learn from corrections across sessions** — a flaw users hit repeatedly in production. The paper proposes a **decision-context** memory layer that persists behavioral corrections and surfaces them on relevant subsequent calls.

**Sources:**
- [alphaxiv — arXiv 2611.08644 Decision Context](https://arxiv.org/abs/2611.08644) `[primary]`

### Why it matters to you

- **Job lens:** **Agent memory engineering** is the hottest open applied-AI subfield. Any FDE role that touches long-running Claude agents hits this problem by week 2. Interview signal: **describe the "corrections don't persist" bug + name the current literature attacking it.**
- **Startup lens:** **Pairs with the Nov 14 edition's "Long-Lived Agent Memory" benchmark (2611.05450)** — the vertical opportunity is **"behavioral memory for Claude / GPT agents" as a middleware** (Mem0, EverMemOS, Letta are the current ecosystem). Position: **"we're the behavioral memory layer for the Claude Agent SDK."**
- **Insight:** **Correction persistence is a UX problem disguised as a technical one.** If your agent can't carry a correction across sessions, users distrust it permanently. The lab that ships this cleanly in a flagship model wins the trust layer.

---

## 3. Knowing When to Intervene: Causal Evaluation of AI Agents (arXiv 2611.09846) {#3-knowing-when}

**The claim:** Agents often call tools when they shouldn't (over-use) or skip tools when they should (under-use). The paper proposes a **causal framework** for evaluating when an agent should intervene vs. act from its own knowledge, and evaluates existing agents against it.

**Sources:**
- [arXiv 2611.09846 Knowing When to Intervene](https://arxiv.org/abs/2611.09846) `[primary]`
- Related: [alphaxiv — Self-Awareness benchmark (arXiv 2606.20661)](https://www.alphaxiv.org/abs/2606.20661) `[primary]`

### Why it matters to you

- **Job lens:** **Over/under-use of tools is the #1 cause of "agent does weird thing" tickets** in production FDE engagements. Being able to debug this with a causal framework (vs. anecdote) is a Senior+ signal.
- **Startup lens:** **Eval + observability for agents** is the Datadog of 2027. Players: Judgment Labs, Humanloop, Patronus, Freeplay. Still room for a **causal-trajectory-aware** entrant.
- **Insight:** **Causal evaluation is the "test-driven agent development" primitive.** Expect frameworks to incorporate it as `agent.verify_decision(action, counterfactual=...)` by mid-2027.

---

## 4. Nudging Decision Models (arXiv 2611.09264) {#4-nudging}

**The claim:** Classical LLM agents are slow + expensive at inference. **"Fast, generation-free" agents** (e.g., classifier + rule-based + retrieval only, no LLM call per step) are cheap but rigid. The paper proposes **digital nudges** — small, targeted prompts to the fast agent at moments where human-studied decision biases would lead it astray — as a cost-aware steering mechanism.

**Sources:**
- [arXiv 2611.09264 Nudging Decision Models](https://arxiv.org/abs/2611.09264) `[primary]`

### Why it matters to you

- **Job lens:** **Cost-aware agent design** remains a hot subfield. If you can show a project that **drops cost 5× by swapping LLM calls for a nudged classifier** on a specific sub-task, you're signaling senior-level production thinking.
- **Startup lens:** **The Decagon / Sierra / Decagon-clones model does this implicitly** — classifier + rules in front, LLM in back. Opportunity: **a "nudged-fast-agent" framework** that developers assemble cheaply.
- **Insight:** **The next capability leap is not bigger models — it's *smarter routing* between cheap agents + expensive agents.** This is where the dollar savings live in 2027.

---

## 5. Multi-Agent Judgment Aggregation (arXiv 2611.08971) {#5-multi-agent-judgment}

**The claim:** Multi-agent LLM systems that aggregate independent judgments across model instances can **introduce failures when agents reason about each other** (vs. simple independent-opinion aggregation). The paper studies when multi-agent helps vs. hurts.

**Sources:**
- [arXiv 2611.08971 Multi-Agent Judgment Aggregation](https://arxiv.org/abs/2611.08971) `[primary]`
- Related: [Stanford single-agent-beats-multi-agent recap from the May 2026 editions](../2026-05-09/04-research-progress.md) `[analysis]`

### Why it matters to you

- **Job lens:** **The multi-agent-vs-single-agent debate is now a standard interview question** for applied-AI roles. The 2026 consensus: *default to single-agent with explicit tool-use, reach for multi-agent only when the tasks are genuinely independent.* This paper reinforces that framing.
- **Startup lens:** If your pitch is "we run a swarm of agents," **be prepared to defend against this literature**. Investors + engineers both ask.
- **Insight:** **Multi-agent as a safety mechanism (ensemble voting) still works; multi-agent as a capability mechanism (debate, collaboration) often does not.** Design accordingly.

---

## Tracking threads continued from Nov 14 edition

- **Long-Lived Agent Memory benchmark** (2611.05450) — still the evaluation substrate for anyone working on persistent memory.
- **MRTPO** (2610.21439) — per-token multi-reward RL; the 2026 "best open stack" for post-training.
- **MiMo-V2.6** (2610.11959) — open RL stack, competitive with closed-source RLHF pipelines.

---

## Reading list for this weekend

If you can read only one, **read SLATE (2611.03982)** — it's the clearest statement of why *deterministic simulators* are replacing *LLM-as-a-judge* grading, which is the underlying intellectual shift behind the RLI benchmark story in `02` §1. **The research and the market are saying the same thing: evaluation infrastructure is the valuable asset.**
