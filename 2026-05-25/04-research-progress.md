# Research Progress — 2026-05-25

The agent-evaluation field is consolidating fast, and Monday is a good day to learn the **names** — because the benchmarks that are winning mindshare now are the ones you'll be expected to reference in interviews and the ones labs will cite in release notes. Three are worth knowing this week, and they share a theme that's been building across the archive: **evaluate agents on *realistic, executable, long-horizon* work**, not on clean synthetic puzzles. (The week's headline research result — an OpenAI model disproving an 80-year Erdős conjecture — was covered on [2026-05-21/04](../2026-05-21/04-research-progress.md); today is about how the field *measures* progress.)

Tags: `#research #benchmarks #agents #evaluation #arxiv`

---

## 1. The agent benchmarks to know by name {#1-benchmarks}

Three harnesses gaining mindshare in late May:

- **TerminalWorld** — **1,530 validated tasks reverse-engineered from real terminal recordings** for SWE/coding agents. The key word is *real*: tasks come from actual developer sessions, not synthesized prompts, so success correlates with "can this agent do what a developer actually does in a shell." This is the natural successor to Terminal-Bench, and the closest proxy yet for *real* coding-agent competence.
- **AI-Trader** — the **first fully-automated, live LLM financial-decision benchmark.** Agents make real-time trading decisions in a live environment — a brutal eval because the ground truth (did you make money?) is unambiguous and adversarial. A useful template for *any* outcome-grounded agent eval.
- **HAL / Holistic Agent Leaderboard** — accepted at **ICLR 2026**, positioned as the **missing standardized agent-eval infrastructure** (continues the [2026-05-23/04 §2](../2026-05-23/04-research-progress.md#2-eval-convergence) eval-convergence read). The "shared leaderboard everyone reports to" play — whoever owns it shapes the agenda.

**Sources:**
- [Hugging Face — Trending papers](https://huggingface.co/papers/trending) `[aggregator]`
- [Hugging Face — LLM-Agent-Harness-Survey dataset](https://huggingface.co/datasets/GloriaaaM/LLM-Agent-Harness-Survey) `[secondary]`
- [arXiv 2603.23749 — Efficient Benchmarking of AI Agents (covers Terminal-Bench 2.0 + HAL)](https://arxiv.org/html/2603.23749v1) `[primary]`

### Why it matters to you

- **Job lens:** Knowing **TerminalWorld** (real-recording-derived SWE tasks) and **HAL** (the leaderboard) by name, and being able to say *why* TerminalWorld is a better signal than synthetic SWE benchmarks (it's derived from real developer sessions), is a cheap, high-credibility interview move. Better still: run your [2026-05-23/03 §2](../2026-05-23/03-practical-skills-and-tools.md#2-artifact) mini-agent against a couple of TerminalWorld-style tasks and report the result — that's *demonstrated* familiarity, not name-dropping.
- **Startup lens:** **AI-Trader's design is the transferable idea** — *outcome-grounded* evaluation, where success is an unambiguous external result (P&L), not a model-judged score. The eval-tooling wedge that's most defensible is the one tied to a hard external outcome (did the ticket close? did the transaction reconcile? did the claim pay correctly?), because those numbers can't be gamed by a clever rubric. Score your eval wedges in `STARTUPS.md` by "how outcome-grounded is the success signal?"
- **Insight:** The pattern across TerminalWorld (real recordings), AI-Trader (live P&L), and last week's MCP-Atlas/Toolathlon (real tools) is one thing: **the field is fleeing synthetic benchmarks for reality.** As models saturate the easy evals, the *only* benchmarks that still discriminate are the ones grounded in messy real environments — and those are expensive and hard to build, which is exactly why building them is a durable skill (and a business).

→ Cross-link: [2026-05-23/04 §2 eval convergence](../2026-05-23/04-research-progress.md#2-eval-convergence) · [2026-05-24/04 §2 the Sunday research read](../2026-05-24/04-research-progress.md#2-read) · [2026-05-22/04 §1 real-tool benchmarks](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) · [`05` §1 referencing these in interviews](./05-career-and-startup.md#1-week-ahead).
