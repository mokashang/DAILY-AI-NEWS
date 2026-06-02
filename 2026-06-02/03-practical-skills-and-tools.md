# Practical Skills & Tools — 2026-06-02

Act-on-it-today. **T-13 days to June-15 Agent SDK metering.** Last week's high-leverage move was the **Opus-orchestrator / Sonnet-worker** routing table ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) — that table is now **partially obsolete** because **Claude Opus 4.8 fast mode (May 28) is 3× cheaper than 4.7's fast mode and stronger on browser/computer-use** ([`02` §1](./02-new-emerging.md#1-opus-48)). The single highest-leverage move tonight is to **re-run the routing exercise with 4.8** and capture the new cost/quality table as a portfolio artifact.

Tags: `#claude-code #cost #orchestration #opus #routing #playbook #portfolio #mcp`

---

## 1. Re-cost the routing table tonight — Opus 4.8 fast mode rewrites the worker-seat math {#1-reroute-opus48}

**The change:** On May 28, Opus 4.8 fast mode shipped at **$10 / $50 per million tokens** — **3× cheaper than 4.7's fast mode ($30/$150)** and **2.5× faster than 4.7 standard**, while *holding or beating* on the benchmarks that matter for agent work (SWE-Bench Pro 69.2%, Online-Mind2Web 84%, 4× more code flaws caught). Sonnet 4.6 is **still the cheapest-per-token worker**, and still the right default for bounded subtasks — but the **gap closed enough that some worker seats now go to Opus 4.8 fast mode by default.**

**The new routing table:**

| Seat | Old default (pre-2026-05-28) | **New default (post-Opus 4.8)** | Why |
|---|---|---|---|
| **Orchestrator / planner** | Opus 4.7 | **Opus 4.8 standard** | Same price ($5/$25), better reasoning, "dynamic workflows" mean the planner can now scope work as it goes |
| **Worker — codegen / refactor / tests** | Sonnet 4.6 | **Sonnet 4.6** (unchanged) | Bounded, well-spec'd work; cheapest per-token; parallelizable |
| **Worker — browser / computer-use** | Sonnet 4.6 | **Opus 4.8 fast mode** | 84% Online-Mind2Web is too good to leave on the bench; fast mode pricing makes it affordable per step |
| **Worker — long-horizon multi-hour refactor** | Opus 4.7 | **Opus 4.8 + dynamic workflows** | The new feature *is* the production answer to multi-hour autonomous work — let the model scope as it goes |
| **Verifier / guard (always-on)** | Haiku 4.5 | **Haiku 4.5** (unchanged) | Cheap enough to run continuously; right tool for plan-checks + injection detection |

**The reliability primitive carries forward unchanged** (still works, still required):
1. Ask the orchestrator for a plan with **no implementation yet**.
2. Open the plan in your editor; **annotate every spot it got wrong.**
3. Send it back with: **"address all notes, don't implement yet."**
4. Only after the plan is right do you let the workers execute.

**Cheap-but-required exercise tonight (30 min):**
1. Pick **one** of your existing agent-team workflows from the last two weeks.
2. Run it under **both** routing tables (old, new) on the same task.
3. Log: tokens by model by step; wall-clock time; quality delta (catch rate, success rate, or your domain metric).
4. Write a 3-line "what changed" table for the README.
5. **Commit it to your portfolio repo with today's date.** That timestamp — proof you re-cost on the day the model dropped — is the artifact.

**Sources:**
- [Anthropic — Introducing Claude Opus 4.8](https://www.anthropic.com/news/claude-opus-4-8) `[primary]`
- [Anthropic — Claude Code best practices (official docs)](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Codersera — Claude Opus 4.8 Launch Guide: Benchmarks & Pricing 2026](https://codersera.com/blog/claude-opus-4-8-launch-guide-2026/) `[analysis]`
- [WaveSpeed — Claude Opus 4.8: Release Date, Pricing, Benchmarks, and Builder Notes](https://wavespeed.ai/blog/posts/opus-4-8/) `[analysis]`
- [DataCamp — Claude Code Best Practices: Planning, Context Transfer, TDD](https://www.datacamp.com/tutorial/claude-code-best-practices) `[analysis]`
- [MCP Directory — Claude Code Best Practices: From Vibe Coding to Agentic Engineering (2026)](https://mcp.directory/blog/claude-code-best-practices) `[analysis]`

### Why it matters to you

- **Job lens:** *"On the day Opus 4.8 dropped, I re-costed our agent team — Opus 4.8 standard planner, mixed Sonnet 4.6 / Opus 4.8 fast workers, Haiku verifier — and cut browser-agent task cost ~30% while raising Online-Mind2Web success rate from X to Y."* That's an FDE / Solutions interview answer in one line, dated proof you ride the frontier rather than reading about it. Pair it with a per-step token table screenshot.
- **Startup lens:** **The platform absorbed your "we plan first" wedge** ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) — dynamic workflows is now native. Your differentiation has to climb a layer: **evaluation against the customer's real tools** (MCP-Atlas-style, [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)), **cost-budget enforcement**, and **integration depth**. Treat the May 28 release as a forcing function to renew your wedge.
- **Insight:** **The frequency of routing-table updates is the new ambient cost of being an AI engineer.** A frontier model dropping every ~6 weeks means the cost/quality table at the heart of your product (or your portfolio) has a half-life. Build the muscle: **routing-table updates as a 30-min weekly ritual**, not a quarterly project. The June-15 meter punishes anyone who treats this as optional.

---

## 2. MCP servers: the 5–8 server context-budget rule (and the one you should add this week) {#2-mcp-budget}

**The constraint that gets ignored:** Each MCP server you connect adds tool schemas that **permanently consume your context window**. A fresh monorepo Claude Code session can burn **~20K tokens** loading system prompt + tool definitions + CLAUDE.md before you type a character — and **5–8 MCP servers is the practical ceiling** before you start crowding out actual work.

**The rule:**
1. **CLAUDE.md ≤ 200 lines.** Compress prose into bullets; move detail to linked docs.
2. **Use `.claude/rules/*.md` with `paths:` globs** to scope rules per-directory instead of putting everything in CLAUDE.md.
3. **Pick your MCPs by workflow frequency** — connect what you actually touch daily (your DB, your issue tracker, your design tool). Drop anything you connected for "exploration."
4. **One MCP per workflow.** Don't connect 3 GitHub MCPs hoping one works better; pick one and learn its idiom.

**The MCP server worth adding this week** (specific to your portfolio): a **real MCP server you can demonstrate agent tool-use against** — the **MCP-Atlas / Tool Decathlon** evaluation pattern ([2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)) needs *one real server* to be credible. Pick a service you actually use (your Notion workspace, a personal Calendar, a sandbox Linear). Wire it up. Demonstrate the agent **(a)** discovering the tool, **(b)** using it correctly, **(c)** *refusing* an injected instruction. That's the dual-model "sanitiser" artifact (carried from [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact)) — but now anchored to a real tool, not a mock.

**Sources:**
- [Clarista — Claude Code MCP Servers & Plugins: The Complete 2026 Guide](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) `[analysis]`
- [TrueFoundry — Claude Code Workflow: How It Works and How to Use It in Production](https://www.truefoundry.com/blog/claude-code-workflow-guide) `[analysis]`
- [Ranjan Kumar — Claude Code Guide: Build Agentic Workflows with Commands, MCP, and Subagents](https://ranjankumar.in/claude-code-guide-agentic-workflows) `[analysis]`
- [GitHub — MuhammadUsmanGM / claude-code-best-practices](https://github.com/MuhammadUsmanGM/claude-code-best-practices) `[primary]`
- [GitHub — FlorianBruniaux / claude-code-ultimate-guide](https://github.com/FlorianBruniaux/claude-code-ultimate-guide) `[primary]`

### Why it matters to you

- **Job lens:** A portfolio that shows **one well-scoped MCP server with a clear evaluation + a refusal-of-injection demo** out-credentials a portfolio with five half-built servers. Depth > breadth in the FDE / Integration interview rubric.
- **Startup lens:** If your product is "Claude-for-X," the **context budget you spend on schemas vs work** is a direct lever on your gross margin. Customers won't see it; your token bill will.
- **Insight:** **Context is the scarce resource, not capability.** Models are cheap; context is what you're actually buying. Design every workflow that way.

→ Cross-link: [2026-05-22/03 §2 the artifact reframed around real-tool verification](../2026-05-22/03-practical-skills-and-tools.md#2-artifact) · [`04` §1 agentic-multimodal benchmarks that need real tools](./04-research-progress.md#1-agentic-multimodal) · [`ACTIONS.md`](../ACTIONS.md).
