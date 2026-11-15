# Research Progress — 2026-07-19 (Sunday review)

> **Continuity note:** July's research thread has covered a lot: [Ring-Zero / "context anxiety" (Jul 17)](../2026-07-17/04-research-progress.md), [Self-Evolving Anytime-Valid Certificates + Self-GC + "What LLM Agents Say When No One Is Watching" (Jul 16)](../2026-07-16/04-research-progress.md), [AgenticPay + the 44-benchmark survey (Jul 15)](../2026-07-15/04-research-progress.md), [ROMA + MAS-Orchestra + Terminal-bench (Jul 14)](../2026-07-14/04-research-progress.md), plus the [Anthropic J-lens / J-space MIT Tech Review peak (Jul 9–13)](../2026-07-13/04-research-progress.md). This file: one paper worth revisiting for the routing rule ([`03` §3](./03-practical-skills-and-tools.md#3-3-model-routing)) and one *design-research* read for the [Jul 28 spec ship](./03-practical-skills-and-tools.md#2-mcp-stateless-execution).

Tags: `#research #arxiv #ace #mcp #context-engineering #protocol-as-research`

---

## 1. Agentic Context Engineering (ACE) — the paper that makes the routing rule *self-improving* {#1-ace}

**What it is:** *"Agentic Context Engineering: Evolving Contexts for Self-Improving Language Models"* (Zhang et al., ICLR 2026, [arXiv:2510.04618](https://arxiv.org/abs/2510.04618)). ACE runs a **3-phase loop**: generate strategies from task attempts → reflect on which worked → curate the context by adding successes and removing failures. Reported: **+10.6% on coding**, **+8.6% on financial reasoning**.

**Why revisit on a Sunday:** Because the [3-model routing rule from `03` §3](./03-practical-skills-and-tools.md#3-3-model-routing) is naturally the *inner loop* that ACE's *outer loop* wraps around. Read together:

- **Inner:** each task attempted → route to a model → verify → log cost/pass/fail.
- **Outer (ACE):** after N tasks, reflect on the log → *curate* the router config (drop tools that never fire, add examples for tasks that Layer B keeps failing, adjust escalation thresholds).

**Compose the two** and you have a routing rule that gets better on its own. That is the "cost-aware agent design" from [ME.md](../ME.md#current-focusing-decision) as a *system*, not a static config.

**Related July papers worth the co-read:**

- **Meta Context Engineering via Agentic Skill Evolution** ([arXiv:2601.21557](https://arxiv.org/pdf/2601.21557)) — skill-catalog-based curation.
- **Structured Context Engineering for File-Native Agentic Systems** ([arXiv:2602.05447](https://arxiv.org/pdf/2602.05447)) — schema/format/multi-file navigation as design axes.
- **Everything is Context: Agentic File System Abstraction for Context Engineering** ([arXiv:2512.05470](https://arxiv.org/pdf/2512.05470)) — filesystem as a context primitive.

**Sources:**
- [arXiv 2510.04618 — Agentic Context Engineering](https://arxiv.org/abs/2510.04618) `[primary]`
- [Iwosz Apar — Context Engineering Research: Papers & Benchmarks (2026)](https://www.iwoszapar.com/p/context-engineering-research-2026) `[analysis]`

### Why it matters to you

- **Job lens:** In a senior interview, describing your routing rule in ACE vocabulary — *"the routing config is curated by an outer loop that reflects on last-week's per-route pass rate and drops routes that never win the verification layer"* — reads as *system* fluency, not prompt fluency. That specific phrasing is worth memorizing.
- **Startup lens:** If you're building the "context-as-a-service" wedge from [2026-07-14 or 2026-07-15 arxiv reads](../2026-07-14/04-research-progress.md), ACE is the canonical citation. Add it to your pitch deck.
- **Insight:** The deep read is that **context, tools, and memory are converging into one subsystem** — the *agent runtime* — and it's the layer where 2026-27 defensibility gets built (not model weights).

→ Cross-link: [`03` §3 routing rule](./03-practical-skills-and-tools.md#3-3-model-routing) · [Karpathy's Anthropic pre-training team](../2026-05-22/01-big-lab-moves.md#3-karpathy) (the extreme case: use the model to improve the model).

---

## 2. Reading the MCP `2026-07-28` spec as *design-research* {#2-mcp-as-research}

**What to internalize:** The MCP RC that ships Tue Jul 28 is a *design position statement*, not just a version bump. Reading it as a paper produces a durable mental model. The four positions:

1. **State lives in the environment, not the session.** Reversing the WebSockets-style position; aligning with plain HTTP + task handles + filesystems.
2. **Tool UIs are server-declared and prefetched.** Reversing the host-hand-codes-per-tool position; aligning with sandboxed iframe delivery.
3. **Long-running work is a first-class object with a handle.** Reversing the hung-tool-call position; aligning with `tasks/get` / `tasks/update` / `tasks/cancel`.
4. **User consent belongs mid-call, in the protocol.** Reversing the ad-hoc "prompt for approval" hacks; aligning with `InputRequiredResult` at the specific decision point.

Each of these is a *research position*. Expect arxiv papers within a quarter that adopt these positions as design axes and empirically test them (against latency, cost, error-recovery rate, security posture).

**Sources:**
- [MCP RC post (July 15)](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) `[primary]`
- [Developers Digest — Breaking changes](https://www.developersdigest.tech/blog/mcp-2026-07-28-breaking-changes) `[analysis]`
- [WorkOS — Auth changes](https://workos.com/blog/mcp-2026-spec-agent-authentication) `[analysis]`
- [2026-07-17/03](../2026-07-17/03-practical-skills-and-tools.md) — prior archive read `[archive]`

### Why it matters to you

- **Job lens:** A 90-min read of the spec is one of the highest-ROI research-time investments of Q3 — it gives you a mental model that reads correctly for a year regardless of which vendor's SDK you use.
- **Startup lens:** The community comment thread on the RC is your **wedge-radar** — the positions that generate the most debate are the pain points where a startup-scale tool can win. Watch specifically the *MCP Apps sandboxing* and *Tasks-extension retry policy* threads.
- **Insight:** Protocol-as-research is a real category — HTTP/1.1 was as much a set of design positions as it was a spec, and post-hoc research legitimized (or contested) those positions. MCP is doing the same for agent runtimes.

→ Cross-link: [`03` §2 migration execution notes](./03-practical-skills-and-tools.md#2-mcp-stateless-execution) · [`02` §1 open-weights + MCP convergence](./02-new-emerging.md#1-open-weights-and-mcp-stack).
