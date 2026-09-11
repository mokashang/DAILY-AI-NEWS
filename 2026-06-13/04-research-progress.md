# Research Progress — 2026-06-13

The benchmark wave that started with MCP-Atlas / Toolathlon ([2026-05-22/04](../2026-05-22/04-research-progress.md)) now has a **public leaderboard for real agent work**: **Terminal-Bench 2.0** (89 hard tasks, no model finishes all of them) is live and frontier labs are reporting on it weekly. Alongside, two newer agent benchmarks — **Workspace-Bench** (20K+ interconnected files) and **APEX-Agents** (long-horizon cross-application tasks built by I-banking analysts / consultants / lawyers) — push the eval frontier into the *messy professional reality* that distinguishes a deployable agent from a demo.

Tags: `#research #benchmarks #terminal-bench #workspace-bench #apex-agents #arxiv #agents #evaluation #scaffolding`

---

## 1. Terminal-Bench 2.0 — the public leaderboard for real agent work {#1-terminal-bench-2}

**What it is:** **Terminal-Bench 2.0** (Snorkel AI + Stanford + Laude Institute) — **89 carefully curated hard tasks** in real Unix terminal environments, each with a unique env, a human-written reference solution, and execution-based tests. v1.0 became the de-facto agent benchmark in 2025; **v2.0 (Nov 2025)** fixed quality + reproducibility issues that surfaced over six months of heavy lab use, and the public leaderboard now publishes frontier results.

**Current leaderboard (June 2026 — for the agent-team conversation in your interviews):**

| Model | Terminal-Bench 2.0 score |
|---|---|
| **GPT-5.5 (OpenAI)** | **82.0%** |
| Gemini 3.5 Flash | 76.2% |
| Claude Opus 4.8 | 74.6% |
| *(Fable 5 numbers landing this week — likely 78–82% range based on SWE-Bench Pro delta)* | — |

The structural finding worth knowing: **frontier models score 65–73% direct; only orchestration + scaffolding pushes them above 80%.** Scaffolding is the scarce skill — i.e., your agent-team architecture ([`03` §1](./03-practical-skills-and-tools.md#1-t-2-metering)) literally is the thing that earns the top scores on the public leaderboard.

The realism cost is part of the value: tasks require **exploring unknown environments, running commands, validating results autonomously** — not the canned mock-tool environments of the old benchmark generation. This is the closest public proxy for "can your agent run on a customer's actual shell?"

**Sources:**
- [Snorkel AI — Terminal-Bench 2.0: Raising the bar for AI agent evaluation](https://snorkel.ai/blog/terminal-bench-2-0-raising-the-bar-for-ai-agent-evaluation/) `[primary]`
- [arXiv 2601.11868 — Terminal-Bench: Benchmarking Agents on Hard, Realistic Tasks in CLIs](https://arxiv.org/abs/2601.11868) `[primary]`
- [Morph LLM — Terminal-Bench 2.0 Leaderboard (2026): 89 tasks no model can finish](https://www.morphllm.com/terminal-bench-2) `[aggregator]`
- [BenchLM — Terminal-Bench 2.0 Benchmark 2026: 27 model averages](https://benchlm.ai/benchmarks/terminalBench2) `[aggregator]`
- [explainx.ai — Terminal-Bench 2.0: the AI agent benchmark that actually matters](https://explainx.ai/blog/terminal-bench-2-0-ai-agent-benchmark-evaluation) `[analysis]`

### Why it matters to you

- **Job lens:** Drop a Terminal-Bench 2.0 task into your Saturday artifact ([`03` §2](./03-practical-skills-and-tools.md#2-artifact)) and you have a portfolio piece that *uses the same eval harness the labs use*. Interview line: *"I ran my agent team against one of the 89 tasks — here's the score, the per-step cost, and the failure mode."* That's three concrete numbers a hiring manager can read.
- **Startup lens:** **Public leaderboards are the cheapest moat-buster for an agent startup.** If your wedge can't post a Terminal-Bench number (or a Toolathlon/Workspace-Bench number) at-or-above frontier baseline, the buyer will assume it can't. Lead with the score, defend with the workflow.
- **Insight:** *Scaffolding wins.* The 65–73% direct → 80–82% scaffolded gap is the single most-actionable research finding of Q2 2026: it says **the value migration is from "smarter model" to "better agent program."** That maps directly onto your skill bet (orchestration + verification + cost — see [`03`](./03-practical-skills-and-tools.md) and [2026-05-22/05 §2](../2026-05-22/05-career-and-startup.md#2-reprice)). Keep investing there; it's where the public leaderboard actually rewards effort.

→ Cross-link: [2026-05-22/04 §1 prior benchmark wave](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) · [`03` §2 weekend artifact](./03-practical-skills-and-tools.md#2-artifact).

---

## 2. Workspace-Bench + APEX-Agents — agent evaluation goes professional {#2-workspace-apex}

Two June-window benchmarks worth knowing for interview vocabulary:

- **Workspace-Bench 1.0** — measures an agent's **"Workspace Learning"** ability in a realistic environment of **20,476 interconnected files, chats, and artifacts (up to 20GB), across five distinct user profiles.** The point isn't the size — it's that the agent has to *learn the workspace* (file conventions, chat history, project-specific norms) before it can do tasks well. This is closer to *how knowledge workers experience* an agent than any prior benchmark. `[arXiv 2605.03596]`
- **APEX-Agents** — long-horizon, **cross-application tasks created by investment banking analysts, management consultants, and corporate lawyers.** Agents have to navigate realistic work environments, files, and tools — the *expensive-professional-services* counterpart to Toolathlon's enterprise-tool focus. The eval reality: **professional-services tasks are the hardest because their success criteria are *judgment calls*, not unit tests.**
- **Efficient Benchmarking of AI Agents** (Franck Ndzomga) — a methodological piece showing that **filtering tasks to those with historical pass rates 30–70% reduces the eval set by 44–70% while preserving rank fidelity** under scaffold/temporal shifts. Useful when you build your own eval harness — *you do not need to run every task to learn from a benchmark.* `[arXiv 2603.23749]`

**Sources:**
- [arXiv 2605.03596 — Workspace-Bench 1.0: Benchmarking AI Agents on Workspace Tasks with Large-Scale File Dependencies](https://arxiv.org/html/2605.03596v1) `[primary]`
- [arXiv 2603.23749 — Efficient Benchmarking of AI Agents (Ndzomga)](https://arxiv.org/abs/2603.23749) `[primary]`
- [Kili — AI Benchmarks 2026: Top Evaluations and Their Limits](https://kili-technology.com/blog/ai-benchmarks-guide-the-top-evaluations-in-2026-and-why-theyre-not-enough) `[analysis]`
- [arXiv 2507.21504 — Evaluation and Benchmarking of LLM Agents: A Survey](https://arxiv.org/html/2507.21504v1) `[primary]`

### Why it matters to you

- **Job lens:** APEX-Agents is **the FDE/Solutions interview benchmark you should reference**: it was built by the *exact buyer personas* you'll deliver to (investment banks, consulting firms, law firms). If you can speak to "I tested my agent on an APEX-Agents-style task" you've spoken to the hiring manager's actual day. Workspace-Bench is the **Tomoro / OpenAI Deployment Co** benchmark (per [2026-05-19/05 §2](../2026-05-19/05-career-and-startup.md#2-openai-deployment-co)): productivity agents that have to navigate a real user's file system.
- **Startup lens:** The **Workspace-Bench framing — agents have to *learn* the workspace first** — is a wedge. A startup whose product *bootstraps an agent into a customer's workspace* (file conventions, chat history, project glossary) is selling something Anthropic's hosted agent can't yet do well at the SMB scale. That's a moat for the application layer.
- **Insight:** Three benchmarks shipped in two months. Each one harder, more realistic, more professional. **The eval pace is now the field's actual pace** — read benchmark releases the way you used to read model releases. The benchmarks tell you what the field *wishes* the models could do; the leaderboards tell you what the models *actually* do.

→ Cross-link: [2026-05-22/04 §2 the agentic-reasoning survey](../2026-05-22/04-research-progress.md#2-agentic-reasoning-survey) · [`03` §2 use one of these for the weekend artifact](./03-practical-skills-and-tools.md#2-artifact).
