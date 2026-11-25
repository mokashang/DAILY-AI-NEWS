# Research Progress — 2026-06-14 (Sunday)

`#arxiv #benchmarks #agents #self-improvement #evals`

The weekend read. Two papers that materially upgrade how you measure or build agents, plus a survey worth one sitting.

---

## 1. τ²-Bench (Sierra) and Experiential Reflective Learning — the two papers that close the "real-tool eval" + "self-improvement" loop {#1-tau2-erl}

Tonight's two-paper weekend reading list. The first nails the measurement bar; the second nails the cheapest path to ship a self-improving agent on top of it.

### A. **τ²-Bench: Evaluating Conversational Agents in a Dual-Control Environment** (Sierra Research; arXiv:2506.07982)

**The claim.** Most conversational-agent benchmarks (including τ-bench, 2024) test agents in a **single-control** setting — the agent has tools, the user is just a prompt source. **τ²-Bench** moves to a **dual-control** Dec-POMDP: **both** the agent **and** the simulated user have tools and can modify the shared world state. Domains: **Telecom, Retail, Airline.** The agent has to (a) reason about domain constraints, (b) coordinate with the user, (c) **guide** the user through actions the agent itself cannot perform.

**Why this is important.** Pre-τ², a model could rank #1 on conversational-agent evals while being terrible at the actual production task — "talking a user through a fix" was outside the benchmark. τ² is the **first benchmark that aligns with what a real CX agent does**: the agent + the human are joint actors. The whole "AI Customer Engineer" hiring lane and the Sierra $15B valuation now have an academic anchor for the production task.

**The extensions** (a recent 2026 family that tells you where the field is moving):
- **τ-Knowledge** (arXiv:2603.04370) — adds unstructured knowledge sources (docs, KBs); evaluates whether agents retrieve correctly.
- **τ-Voice** (arXiv:2603.13686) — full-duplex voice agents on the same real-world domains.

**Sources.**
- `[primary]` [arXiv:2506.07982 — τ²-Bench](https://arxiv.org/abs/2506.07982)
- `[primary]` [GitHub: sierra-research/tau2-bench](https://github.com/sierra-research/tau2-bench)
- `[primary]` [τ-bench (2024 original)](https://arxiv.org/abs/2406.12045)
- `[analysis]` [arXiv:2507.02825 — Establishing Best Practices for Building Rigorous Agentic Benchmarks](https://arxiv.org/pdf/2507.02825)

### B. **Experiential Reflective Learning for Self-Improving LLM Agents** (arXiv:2603.24639)

**The claim.** A test-time self-improvement loop in which the agent **(1)** reflects on completed task trajectories, **(2)** distills heuristics into a small experiential memory, **(3)** retrieves relevant heuristics at the start of new tasks. Result: **+7.8% success rate on Gaia2** over a ReAct baseline — no parameter updates, just memory + retrieval. The lineage continues from MAR (Multi-Agent Reflexion, Dec 2025) and the broader Reflexion / Self-Improving-at-Test-Time line.

**Why this is important.** Karpathy's stated team mission at Anthropic — *"using Claude to accelerate Claude's training"* ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)) — is conceptually adjacent to ERL: take agent trajectories, distill insights, feed them back as **either** training signal **or** in-context guidance. ERL is what the cheap, deploy-this-week version of that loop looks like.

**The connecting survey.**
- **Landscape of Agentic Reinforcement Learning for LLMs: A Survey** (arXiv:2509.02547) — frames RL as the mechanism for ongoing reflection, learning from mistakes across planning, reasoning, tool use, and memory. Read this if you want the unified taxonomy.

**Sources.**
- `[primary]` [arXiv:2603.24639 — Experiential Reflective Learning](https://arxiv.org/abs/2603.24639)
- `[primary]` [arXiv:2509.02547 — Agentic RL Survey](https://arxiv.org/pdf/2509.02547)
- `[primary]` [arXiv:2510.07841 — Self-Improving LLM Agents at Test-Time](https://arxiv.org/abs/2510.07841)
- `[primary]` [arXiv: MAR Multi-Agent Reflexion (Dec 2025)](https://arxiv.org/html/2512.20845)
- `[aggregator]` [GitHub: XMUDeepLIT/Awesome-Self-Evolving-Agents](https://github.com/XMUDeepLIT/Awesome-Self-Evolving-Agents)

**Why these two matter to you.**

- **Job ·** τ²-Bench is exactly the framing **Sierra Customer Engineering interviews will gravitate to over the next 60 days** (their own benchmark!). ERL is the architecture you sketch on the whiteboard when asked "how would you make this agent improve over time without retraining" — that's a real interview question at Anthropic Solutions, OpenAI FDE, and any vertical-agent startup.
- **Startup ·** Combine them. Your wedge-vertical agent + an ERL-style memory layer + τ²-style domain eval = a measurable improvement curve. Investors fund "the curve," not "the model."
- **Insight ·** The field is converging on **eval-first agents:** the benchmark *is* the product spec. Pick a vertical, build the τ²-style eval first, then build the agent. The eval is the moat.

`#tau2 #erl #self-improving-agents #benchmarks #arxiv`

---

## 2. Agent-Diff — state-diff-based evaluation for enterprise API tasks {#2-agent-diff}

**The claim.** **Agent-Diff** (arXiv:2602.11224) benchmarks LLM agents on **enterprise API tasks** by **executing code** against real APIs and grading on the **state-diff** between expected and actual final state. Closer to "did you actually post the invoice correctly" than to "did the final response read right."

**Why important.** Enterprise FDE / Solutions roles are graded on **does the integration actually work end-to-end** — not "does the chat sound right." Agent-Diff is the academic version of that. Pair with [MCP-Atlas + Toolathlon ([2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks))] — the trio is now the **state-of-the-art real-tool evaluation stack**.

**Sources.**
- `[primary]` [arXiv:2602.11224 — Agent-Diff](https://arxiv.org/abs/2602.11224)
- `[primary]` [arXiv:2602.18998 — Benchmark Test-Time Scaling of General LLM Agents](https://arxiv.org/pdf/2602.18998)
- `[primary]` [arXiv:2604.05172 — ClawsBench: Productivity Agents in Simulated Workspaces](https://arxiv.org/pdf/2604.05172)

**Why it matters to you.**

- **Job ·** Add Agent-Diff to your eval-vocabulary alongside τ², MCP-Atlas, Toolathlon. Interview talking points for FDE-class roles.
- **Startup ·** A wedge worth scoping: **a "compliance / financial-API task" benchmark suite** built on Agent-Diff's state-diff methodology, for the regulated-vertical agent market. (Adjacent to the Claude for Finance vertical narrative.)
- **Insight ·** "State-diff-based grading" is the production-y way of measuring agents. Add it to the routing-engine eval surface from [`03` §3](./03-practical-skills-and-tools.md#3-routing-gate-recipe).

`#agent-diff #benchmarks #enterprise #api-tasks #mcp #arxiv`

---

## 3. Externalization in LLM Agents — the survey worth one sitting {#3-externalization}

**Externalization in LLM Agents: A Unified Review of Memory, Skills, Protocols and Harness Engineering** (arXiv:2604.08224). Useful framing as a **vocabulary upgrade** more than a discovery: separates "memory" (storage), "skills" (reusable competencies), "protocols" (inter-agent + tool calling), and "harness engineering" (the surrounding scaffolding). Lines up cleanly with the **Storage Is Not Memory** trichotomy from [2026-05-18/04](../2026-05-18/04-research-progress.md).

**Sources.**
- `[primary]` [arXiv:2604.08224 — Externalization in LLM Agents](https://arxiv.org/pdf/2604.08224)
- `[primary]` [arXiv:2506.11102 — Evolutionary Perspectives on the Evaluation of LLM-Based AI Agents](https://arxiv.org/pdf/2506.11102)

**Why it matters to you.**

- **Job ·** This is the **vocabulary you reach for in any "how would you architect this agent" interview.** "Externalization → memory + skills + protocols + harness" is a cleaner-than-yours mental model; steal it.
- **Insight ·** Read this if you have 40 min of weekend time after the audit + the metering toggle.

`#survey #externalization #memory #skills #protocols #harness`

---

## Cross-page

- See [`01` §1](./01-big-lab-moves.md#1-fable-shutdown) — the τ²-Bench domains (Telecom/Retail/Airline) directly inform which verticals are robust to the Anthropic-stack shutdown narrative (regulated CX vs less-regulated).
- See [`03` §3](./03-practical-skills-and-tools.md#3-routing-gate-recipe) — plug τ²-Bench / Agent-Diff into the routing-engine + security-gate eval surface.
- See [`05` §2](./05-career-and-startup.md#2-interview-prep) — the τ², ERL, and Agent-Diff vocabulary as June-15-onward interview talking points.
