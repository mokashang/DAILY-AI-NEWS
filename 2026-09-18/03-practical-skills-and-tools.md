# Practical Skills & Tools — 2026-09-18

Three tactics that convert this week's news into a Sunday-night artifact. All three take under 4 hours; all three signal to a Q4 recruiter or a Q1 co-founder that you're operating at the frontier's altitude, not lagging it.

Tags: `#claude-code #mcp #agents #oversight #practical #eval #tokens`

---

## 1. Instrument your own agent project with Anthropic's three metrics {#1-three-metrics-template}

**Why:** Anthropic just published a metric template (see [`01` §1](./01-big-lab-moves.md#1-anthropic-metrics)); every buyer and every hiring loop will start using its vocabulary within 90 days. Getting there first — on your own portfolio project — is the single fastest resume-signal upgrade available this week.

**The template (Anthropic's three metrics, translated to your project):**

| Metric | Anthropic's number (Aug 2026) | Your version | How to measure |
|---|---|---|---|
| **AI-led share of work** | 26% of R&D | % of merged PRs / issues / tickets whose primary author was Claude / Cursor / Codex | Tag commits `agent:` when the agent produced the primary diff; divide by total commits in a week. |
| **Agent-operation coverage + intercept rate** | 100% monitored, 0.002% intercepted | % of your agent's tool calls that pass through a guard (permission check, dry-run, human review); % blocked | A single-file middleware in your MCP server or Claude Code hook that logs and counts every tool call + every block. |
| **Compute-to-safety allocation** | 6% of R&D compute (12% for AI-led R&D) | % of your infra cost this month spent on eval / regression tests / adversarial suites vs. shipping features | A tag on every cloud-cost line item + a monthly rollup. |

**The deliverable:** A **single dashboard page** (Streamlit, Notion, or a plain HTML file) with three numbers. Screenshot it. Put it at the top of your GitHub README and link from your LinkedIn.

**Concrete recipe (90 min):**
1. Add a tiny middleware to your existing agent / MCP server that logs every tool call to a JSONL file. `[15 min]`
2. Add a simple decision hook: any tool call matching a pattern (write to prod, delete data, external POST) prints a warning and requires `y/N`. Count intercepts. `[20 min]`
3. Tag every commit in your project with `agent:` or `human:` for the last four weeks (a `git filter-branch` shortcut is not needed — just re-tag going forward and note the retroactive gap). `[10 min]`
4. Set up a monthly `costs.md` that splits AWS/GCP/API bills by tag `feature` vs. `eval`. `[15 min]`
5. Build the 3-number dashboard. `[30 min]`

**Sources / prior art:**
- [Digital Applied — Anthropic's Three Numbers on Agent Oversight (coverage / latency / escalation)](https://www.digitalapplied.com/blog/anthropic-agent-oversight-metrics-coverage-latency-escalation) `[analysis]`
- [SiliconANGLE — Anthropic details practical metrics](https://siliconangle.com/2026/09/17/anthropic-details-practical-metrics-to-help-monitor-the-speed-of-ai-development/) `[secondary]`

### Why it matters to you

- **Job lens:** In a 30-min interview, "here are my three numbers on the agent I ship, updated weekly" is the highest-signal five minutes you can spend. Anthropic Applied AI / OpenAI FDE / Sierra Customer Engineer loops all now ask about agent oversight explicitly (see [`05` §1](./05-career-and-startup.md#1-market)). Show, don't tell.
- **Startup lens:** If your product idea is agent-shaped and you can't tell an enterprise buyer what your three numbers *would be*, you're not ready to sell into regulated industries. Build the dashboard for your prototype now; it becomes the security-questionnaire response later.
- **Insight:** Metric adoption is a **one-way door** — once buyers see labs publish these numbers, they can't unsee them. The next 6 months of enterprise-AI RFPs will contain a "supply your three-metric snapshot" clause. Be the vendor / candidate who already has it.

→ Cross-link: [`01` §1 Anthropic's three metrics](./01-big-lab-moves.md#1-anthropic-metrics) · [2026-09-17/03 §2 EFS setup](../2026-09-17/03-practical-skills-and-tools.md#2-efs-setup).

---

## 2. The Claude Code context-hygiene playbook Anthropic quietly published this month {#2-context-hygiene}

**Why:** Anthropic's own docs shipped an updated Claude Code best-practices set in September that codifies the token-economics tricks the top-1% of Claude Code users have been running informally since June. If you're paying for Claude Code, you're overpaying without these; if you're presenting it as a skill in an interview, this is now the baseline.

**The five rules that actually matter:**

1. **Ship a concise `CLAUDE.md` in every repo, ≤200 lines.** Purpose: seeds every session with essential project context automatically. Don't repeat what's in `README.md` — put invariants (build command, coding style, no-go paths) and *only* invariants. Karpathy's `CLAUDE.md` (tracked at [2026-05-15](../2026-05-15/) → ~109K stars) is the reference template.
2. **Run Claude Code from the sub-directory closest to the task**, not the repo root. This truncates the auto-loaded file tree to the relevant slice and can 3–5× your effective context budget on large repos.
3. **`/clear` between tasks, `/compact` inside long tasks, `/resume` to continue a prior thread.** Three commands, one rule: **the default is not what you want.** Anthropic's Sept guidance: "context hygiene is a habit, not a config."
4. **Prefer focused subagents over one bloated all-purpose agent.** A subagent with 20 lines of prompt + 3 tools outperforms a generic agent on the same task 4× out of 5 (Anthropic's own eval numbers).
5. **Match effort to complexity.** Fable 5.1 has explicit effort tiers; a routine formatting task on the highest effort tier costs ~7× more with zero quality gain. Set a default effort in `CLAUDE.md` and override only when needed.

**The 30-min action:** Open your top project's `CLAUDE.md` right now. Delete anything not an invariant. Add: build command, test command, no-go paths, effort default, subagent map. Commit. Repeat for your #2 project this weekend.

**Sources:**
- [Anthropic — Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Sutopo — Anthropic Shares Official Claude Code Tips to Save Tokens](https://sutopo.com/anthropic-shares-official-claude-code-tips/) `[analysis]`
- [MCP Directory — Claude Code Best Practices 2026](https://mcp.directory/blog/claude-code-best-practices) `[analysis]`
- [Remote OpenClaw — Claude Code Best Practices in 2026: What Actually Holds Up](https://www.remoteopenclaw.com/blog/claude-code-best-practices) `[analysis]`
- [Releasebot — Claude Code Updates by Anthropic, September 2026](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`

### Why it matters to you

- **Job lens:** In every Anthropic / applied-AI interview loop, "walk me through your Claude Code workflow" is now a question. If your answer doesn't include `/clear`, `/compact`, subagents, and a `CLAUDE.md` example — you sound like a 2025 user. If it does, you're speaking the same operational vocabulary as the interviewer's own team.
- **Startup lens:** Every startup you're going to work at or found is going to run Claude Code (~4% of all public GitHub commits per [2026-05-14](../2026-05-14/) — that number is materially higher today). Your team's per-eng Claude bill drops 30–60% with this playbook applied consistently. That's the founding-team-CTO checklist item that saves ~$3–4K/eng/yr.
- **Insight:** **Anthropic is codifying what used to be tacit knowledge.** That means the "tribal Claude Code power user" edge is *decaying* — the docs now teach it, so everyone has access. The new edge is one level up: **the tacit skill that will still be scarce in 6 months is the one Anthropic hasn't documented yet.** Watch the Anthropic Skills page + Anthropic Cookbook GitHub for what they *don't* teach; that's your next competitive skill.

→ Cross-link: [2026-05-17/03 Karpathy CLAUDE.md](../2026-05-17/03-practical-skills-and-tools.md) · [2026-05-15/03 CLAUDE.md 4-rule playbook](../2026-05-15/03-practical-skills-and-tools.md).

---

## 3. The 4-hour stateless-MCP port {#3-stateless-mcp-checklist}

**Why:** The 2026-07-28 MCP spec makes stateless the default. Any MCP server you or your project shipped before August was built against a bidirectional stateful assumption; enterprise buyers are increasingly refusing to install stateful servers (they can't audit them). This is the **highest-return 4-hour portfolio task** available in Q3 2026 — a real migration, a real diff, and a real production benefit.

**Checklist:**

1. **Inventory your handlers.** List every method that reads/writes a session object. If the count is ≤5, this port is 2 hours. If it's ≤15, 4 hours. `[10 min]`
2. **Move state to the client.** Every "server remembers X" becomes "client sends X in `_meta` on every request." Update your `handler` signatures.
3. **Add `_meta` on every request.** Trace-ID, tool version, correlation-ID, optional user hint. This is what the spec calls "context envelope"; enterprise auditors love it.
4. **Delete the reconnect/resume paths** for sessions. Stateless doesn't need them.
5. **Test with two clients in parallel** hitting the same server. If a request from client A affects client B, you still have hidden state; find it.
6. **Optional but recommended:** exercise **MCP Apps (SEP-1865, sandboxed HTML UI)** and the **Tasks extension** (stateless-native long-running work) — both open portfolio-differentiation surface. See [2026-09-08/03 §2](../2026-09-08/03-practical-skills-and-tools.md#2-mcp-migration-update).
7. **Ship the diff.** Write a 500-word blog post: "porting one MCP server to stateless — what took an hour, what took me longest, one gotcha." Post to LinkedIn.

**Sources / references:**
- [Model Context Protocol Blog — 2026-07-28 Specification](https://blog.modelcontextprotocol.io/posts/2026-07-28/) `[primary]`
- [The New Stack — MCP roadmap 2026](https://thenewstack.io/model-context-protocol-roadmap-2026/) `[secondary]`
- [WorkOS — Everything your team needs to know about MCP in 2026](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) `[analysis]`

### Why it matters to you

- **Job lens:** The number of engineers who have publicly ported an MCP server to the July spec is currently in the low hundreds. Being one of them + writing about it puts you in a ~200-person cohort with disproportionate LinkedIn/GitHub search visibility for MCP-adjacent roles. Recruiters at Anthropic, OpenAI DevX, GitHub, Cloudflare, Cursor are hiring against this exact keyword this quarter.
- **Startup lens:** The stateless port is the **precondition** for MCP-as-a-service platforms to onboard your server (see [`02` §3 MCP-hosting wedge](./02-new-emerging.md#3-mcp-grows-up)). If you're planning to found in this category or become a founding engineer, having personally executed the port means you can *reason* about the platform's constraints from the customer side, not just the operator side.
- **Insight:** The stateless spec is the same architectural pattern **HTTP + JWT** followed in 2010-era web infra. Every generation of infra learns this lesson: **stateless scales, stateful doesn't.** Being on the right side of that architectural transition — for MCP now, for the next agent-protocol wave in 2027 — is a durable engineering-taste signal you can talk about in interviews without sounding rehearsed.

→ Cross-link: [`02` §3 MCP grows up](./02-new-emerging.md#3-mcp-grows-up) · [2026-09-08/03 §2 the migration playbook](../2026-09-08/03-practical-skills-and-tools.md#2-mcp-migration-update).

---

## Weekly cadence reminder

- **Nightly (10 min):** open your three-metrics dashboard, log yesterday's numbers.
- **Weekend (4 h):** ship one artifact (this weekend: the stateless-MCP port + blog post OR the three-metric dashboard).
- **Monthly (4th of month, per [ME.md](../ME.md)):** re-audit your Claude / OpenAI / Gemini spend. With Fable 5.1's 75% cheaper cache-reads (see [2026-09-10/03 §1](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics)) plus these context-hygiene rules, expect month-over-month drops of 20–40%.
