# 04 — Research Progress · 2026-10-11

What's moving the frontier (not just the price). Three threads this week: **the top-5 agentic AI papers of 2026 solidify as interview canon**, **evals go adversarial + lifelong**, and **the paper-volume signal keeps climbing**.

---

## 1. The "Top 5 Agentic AI Papers of 2026" — now interview canon {#1-top-5-agentic}

**The list.** Analytics Vidhya's "Top 5 Agentic AI Research Papers of 2026" (updated Aug 22, 2026) is the first lightly-canonical reading list for a 2026 ML-interview talk-track. The five:

1. **Agents' Last Exam** — a benchmark of **long professional workflows** (not short synthetic tasks). The eval that most clearly reflects what customers actually hire agents to do.
2. **ClawBench** — tests web agents on **live** websites, not snapshots or mocks. The 2026 successor to the mock-API benchmarks that aged out in 2025.
3. **Code as Agent Harness** — reframes the agent-vs-script distinction: the harness itself IS the agent's primary tool, and code-as-API is the right abstraction.
4. **AutoResearchClaw** — an autonomous research pipeline: literature → hypothesis → experiment → writeup.
5. **AREX** — a deep-research agent that uses **verification to improve answers** (iterative check-and-revise).

**What ties them together.** All five point at **evals that reflect reality, not toy tasks + a shift from "can the agent do a thing" to "can the agent do a thing and KNOW IT DID IT CORRECTLY"**. This is the lineage that [`2026-09-10/04`](../2026-09-10/04-research-progress.md#1-realtime-memory) picked up with evolving-envs + persistent memory.

**Volume signal.** Per one roundup covering the 2026 agentic-AI conference wave: **~9,000 agent-related papers to date, ~1,000/month new**. The fastest-growing arXiv sub-tracks: **agent safety + alignment**, which overtook agent capabilities in H1 2026.

**Sources.**
- [Analytics Vidhya — Top 5 Agentic AI Research Papers of 2026](https://www.analyticsvidhya.com/blog/2026/08/top-agentic-ai-research-papers/) `[aggregator]`
- [Besthub — Agentic AI Boom 2026: Insights from 322 Top Conference Papers](https://www.besthub.dev/articles/agentic-ai-boom-2026-insights-from-322-top-conference-papers-efa92a716ff4) `[aggregator]`
- [Hugging Face — AI Trends 2026-07 (trending agent papers)](https://huggingface.co/collections/thaki-AI/ai-trends-2026-07) `[aggregator]`
- [VoltAgent — awesome-ai-agent-papers (weekly updated 2026 list)](https://www.sourcepulse.org/projects/25814758) `[aggregator]`

**Why it matters to you (Job · Startup · Insight).**
- **Job.** Pick ONE of the five for the next week and go deep — read it, re-implement a 20-line version of its core idea, and have a 2-minute talk-track ready. Best candidate for the Anthropic FDE / Solutions interview: **AREX** (verification-driven, maps directly to the verifier-and-rollback pattern Anthropic actually ships). Best candidate for the OpenAI Deployment Engineer / Applied interview: **Code as Agent Harness** (the Codex-shaped lens).
- **Startup.** **ClawBench's "live websites" framing** is the one with the clearest commercial pull — if your startup needs to prove its agent works on *real* customer sites, build an eval on top of ClawBench's methodology instead of inventing one from scratch.
- **Insight.** When a *list* of top 5 papers stays stable from August into October, that list has become **the de facto canon**. Not reading it is a signaling miss.

`#arxiv #agents #evals #safety #interview-prep`

---

## 2. Lifelong + evolving-env + memory — the frontier moves from "can-do" to "keep-doing" {#2-lifelong}

**Thread continued.** [`2026-09-10/04`](../2026-09-10/04-research-progress.md#1-realtime-memory) called out the **"Real-Time Reasoning Agents in Evolving Environments" (arXiv 2511.04898)** and **"Memory in the Age of AI Agents" (arXiv 2512.13564)** papers as the start of this thread. Add this week:

- **SkillOpt** — self-evolving agent skills (per HF trending). The practical complement to "evolving environments": not just does the agent track a changing world, does it track and improve its own skill set.
- **ARIS** — autonomous research through adversarial multi-agent collaboration. The ARIS line that first appeared in May 2026 (see [`2026-05-19/04`](../2026-05-19/04-research-progress.md)) has matured into a stable sub-track.

**Why these three (evolving-env + memory + skill-evolution) are one thesis.** An agent in production is **a system that must keep performing under drift** — the world changes, the user changes, the agent's own repertoire has to change. All three papers are different projections of the same frontier.

**Sources.**
- [Besthub — Agentic AI Hits Breakout Year, the next research trend](https://www.besthub.dev/articles/agentic-ai-hits-breakout-year-the-next-research-trend-i-ve-captured-1e0bdea84b18) `[aggregator]`
- [Hugging Face — AI Trends 2026-07](https://huggingface.co/collections/thaki-AI/ai-trends-2026-07) `[aggregator]`
- Prior: [`2026-09-10/04`](../2026-09-10/04-research-progress.md), [`2026-05-19/04`](../2026-05-19/04-research-progress.md) (ARIS first appearance)

**Why it matters to you (Job · Startup · Insight).**
- **Job.** The **"production-ready-under-drift"** framing is a crisp answer to "what's hard about shipping agents in 2026?" — have a 60-second version ready. Mention the three papers by name.
- **Startup.** The **memory-infra + skill-registry layers** are both legitimate standalone wedges (Mem0 and EverMemOS were called out in May, see [`2026-05-10/02`](../2026-05-10/02-new-emerging.md)). Specifically watch for the "agent that gets a weekly skill-set update from its deployment telemetry" product shape.
- **Insight.** The volume signal (~1K agent papers/month) means specific papers age out fast — but **sub-tracks persist**. Index by sub-track (safety, evals, memory, skills, routing), not by paper.

`#arxiv #agents #memory #skills #drift`

---

## 3. What's underweighted this week — the Codex / coding-agent sub-track {#3-coding-agent}

**The gap.** With OpenAI segregating Codex from the GPT-6 Intelligent UI rollout (per [`01` §2](./01-big-lab-moves.md#2-gpt-6-intelligent-ui)), **coding-agent benchmarks are a lane that's currently cheaper to publish in** than agent-safety or memory. The volume isn't there yet — most 2026 agent papers are generic workflow agents, not coding specifically.

**One signal to watch.** The "**Code as Agent Harness**" paper above is the first mainstream attempt to re-ground coding-agent research. Expect follow-ons in Q4.

**Why it matters to you (Job · Startup · Insight).**
- **Job.** If you're an SDE-track applicant, a **short arXiv submission on coding-agent evaluation** is a non-trivial career differentiator — fewer competitors than agent-safety. Workshop-tier publications are reachable this quarter.
- **Startup.** The **Claude-Code / Codex / Cursor / Devin economy** needs its own benchmark provider. "ClawBench for coding agents on real repos" is a credible research-to-startup bridge.
- **Insight.** Watch for the first **"GPT-6-Codex specific" benchmark** to appear in Q4. Being the author or an early co-author would be a once-a-quarter resume moment.

`#arxiv #coding-agents #codex #claude-code`

---

## 4. For the next week — personal reading queue {#4-reading-queue}

Prioritized to fit the "20 min / day" budget:

- **AREX** (verification-driven research agent) — direct interview relevance for Anthropic.
- **ClawBench** (live-site web agent benchmark) — direct interview relevance for Sierra / Decagon / Cognigy and any customer-engineering role at an agent-platform company.
- **Agents' Last Exam** paper + benchmark description — for "what hard looks like in 2026" talk-track.
- **One of**: SkillOpt or ARIS (whichever is more aligned to your current portfolio).

**Secondary.** Scan Hugging Face's daily papers page every weekday for 5 min. Index by the sub-tracks above, not individual titles.

`#personal #reading-queue`

---

## See also

- [`01-big-lab-moves.md`](./01-big-lab-moves.md) — Haiku 5.5 + GPT-6 + WH accord
- [`03-practical-skills-and-tools.md`](./03-practical-skills-and-tools.md) — turning research into a shippable artifact
- Prior editions: [`2026-09-10/04`](../2026-09-10/04-research-progress.md) · [`2026-05-19/04`](../2026-05-19/04-research-progress.md) · [`2026-05-18/04`](../2026-05-18/04-research-progress.md)
