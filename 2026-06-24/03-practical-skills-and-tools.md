# Practical Skills & Tools — 2026-06-24

Two practices to install **tonight** — both directly mitigate the [Agent SDK metering ([2026-05-16/00](../2026-05-16/00-tldr.md))] reality you're now ~10 days into living with, both are interview-grade artifacts, and both let you make a tangible portfolio update before applying to the SOC lane in [`05` §1](./05-career-and-startup.md#1-soc-lane-firing).

Tags: `#claude-code #mcp #subagents #cost #orchestration #playbook`

---

## 1. Install enterprise-managed MCP (Okta-flavored) — 25 minutes, screenshot-ready {#1-enterprise-mcp}

**What's new (per Anthropic Claude release notes, ~mid-June):** **Claude added enterprise-managed MCP connector access**, starting with **Okta**, so admins provision connectors once and users get **zero-touch access on first login**. The beta covers **centralized authorization across Claude chat, Claude Code, and Cowork** for Team and Enterprise plans.

**Why this is the practical step tonight (not a marketing line):**

The 2026 MCP best-practice consensus locked in this month (Cloudflare reference architecture, CData enterprise guide, Stacklok enterprise guide): **per-request identity via OAuth 2.1 (replacing custom-keyed servers), virtual servers / RBAC per team, immutable audit logs, risk-classified tool annotations, human-in-the-loop approval for destructive operations.** Anthropic's enterprise-managed MCP ships the first piece (per-request identity + central auth) out of the box.

**Steps (tonight, 25 min):**

1. **Read** the [Cloudflare enterprise MCP reference architecture](https://blog.cloudflare.com/enterprise-mcp/) (10 min) — it's the cleanest mental model published this month.
2. **Spin up** a personal Claude Code workspace and **connect an OAuth-authenticated MCP server** to it. Even a single connector (e.g., your GitHub + a small custom server) gets you the per-request-identity flow end-to-end.
3. **Add to your portfolio MCP server**:
   - **`tool.risk` annotations** on every tool (`"read"`, `"write"`, `"destructive"`).
   - **OAuth 2.1** authentication (not bearer-key).
   - **An immutable audit log file** (`jsonl`, one line per invocation: timestamp, identity, tool, args-hash, decision).
4. **Screenshot** the audit log + one OAuth-protected tool invocation. That's your portfolio README hero image.

**Sources:**
- [Cloudflare — Scaling MCP adoption: Our reference architecture for enterprise deployments of MCP](https://blog.cloudflare.com/enterprise-mcp/) `[primary]`
- [CData — MCP Server Best Practices for 2026](https://www.cdata.com/blog/mcp-server-best-practices-2026) `[analysis]`
- [Stacklok — MCP Security Best Practices for Enterprise Deployments (2026)](https://stacklok.com/blog/mcp-security-best-practices-what-every-enterprise-team-needs-to-know-in-2026/) `[analysis]`
- [TruFoundry — MCP Security Risks & Best Practices: Enterprise Guide](https://www.truefoundry.com/blog/mcp-security-risks-best-practices) `[analysis]`
- [WorkOS — Everything your team needs to know about MCP in 2026](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) `[analysis]`

### Why it matters to you

- **Job lens:** "OAuth-authenticated MCP with per-request identity, risk-classified tools, and an audit log" is the exact vocabulary in **AI Integration Engineer / FDE / Solutions Engineer** postings right now. Match it word for word in your README and in your application narrative.
- **Startup lens:** The empty layer is **MCP audit + compliance for SOC-2/HIPAA-bound buyers**. The architecture is now standardized; the buyer is now defined (regulated enterprises); the product is not yet shipped at startup scale. Add it to STARTUPS.md.
- **Insight:** Per-request identity changes the security model from *"this server is allowed"* to *"this user, doing this action, against this tool, right now, is allowed"* — and that's the substrate every meaningful 2026 agent product needs. Build to it now.

---

## 2. Subagent token economics: 7× total, 3–5 concurrent is the sweet spot {#2-subagent-economics}

**The data (published this month across multiple practitioner write-ups):**

- Subagent-heavy Claude Code workflows consume **roughly 7× the tokens of a single-threaded session**.
- **3 to 5 concurrent subagents** is the sweet spot — above that, summary-merging eats the parallelism gain.
- Subagents are **loaded at session start** — file-edits don't pick up until session restart (gotcha that wastes 30+ min if you don't know it).
- The right design: **one subagent → one job**. "Do-everything" subagents fail because their description matches everything and nothing.

**Pair this with the 05/22 finding** (Opus orchestrator + Sonnet workers ≈ 40% cheaper than all-Opus, [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md)). The composed rule:

> **For tasks that fan out:** Opus-4.7 orchestrator + 3–5 Sonnet-4.6 workers, each with one well-scoped job. Expect ~7× the tokens of a single thread, but with a wall-clock and quality win that justifies it on hard tasks.
>
> **For everything else:** stay single-threaded. The 7× cost without the parallelism gain is the most common metering-bill mistake of June 2026.

**Steps (tonight, 20 min):**

1. **Audit** your `.claude/agents/` folder. For each subagent: can you write its job in **one sentence with no "or"s**? If not, split or delete.
2. **Add a `cost-note.md`** to your project root that records: *which tasks I delegate to subagents (and why), which I keep single-threaded (and why)*. This is interview gold and also the artifact that catches your own drift in 4 weeks.
3. **Run one fan-out task** with 3 subagents and one with 7 — log the token bill from both. The 3-vs-7 cost differential becomes your "I optimized agent-team cost" talking point.

**Sources:**
- [Nimbalyst — Claude Code Subagents: A Practical 2026 Guide](https://nimbalyst.com/blog/claude-code-subagents-guide/) `[analysis]`
- [Totalum — Claude Code Subagents: The 2026 Production Playbook](https://www.totalum.app/blog/claude-code-subagents-totalum) `[analysis]`
- [CloudZero — Claude Code Agents In 2026: Agent View, Subagents, Teams, And What Parallel Sessions Actually Cost](https://www.cloudzero.com/blog/claude-code-agents/) `[analysis]`
- [SmartScope — Claude Code Advanced Best Practices: 11 Practical Techniques (2026)](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[analysis]`
- [Tembo — Claude Code Subagents: A 2026 Practical Guide](https://www.tembo.io/blog/claude-code-subagents) `[analysis]`
- [Anthropic — Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) `[primary]`

### Why it matters to you

- **Job lens:** "I designed a 3–5 subagent team with one-sentence-job descriptions, audited the bill, and have a cost-note explaining when I single-thread instead" is the **exact** answer to the FDE/Integration-Engineer question *"how do you control cost in production agent systems?"* — and 95% of applicants will say "use cheaper models" instead.
- **Startup lens:** Cost-observability tools that connect *agent-team design → cost outcome* are still seed-stage. Note: Anthropic's metering ([06/15](../2026-05-16/00-tldr.md)) just created a population of users who will pay $10–50/mo for this insight.
- **Insight:** Every model release **lowers per-token price** but every agentic pattern **raises per-task token count**. The two slopes can cancel — or worse, *invert* if you fan out without measuring. The skill is no longer "use the cheapest model"; it's **"design the team that costs the least to deliver the outcome."**

---

## 3. The Patch-the-Planet pattern as a portfolio artifact {#3-patch-planet-artifact}

The [Patch the Planet announcement ([`02` §1](./02-new-emerging.md#1-patch-planet-ibm-daybreak))] is also a **reproducible portfolio pattern** — and the most under-priced one this quarter.

**The pattern:**
1. Point an agent at a real OSS project's GitHub Actions / issue queue / commit history.
2. Ask it to find a class of vulnerability (e.g., *path traversal in HTTP handlers* — narrow, common, real).
3. **Verify** every finding (the verification skill from 05/22) — most findings are false positives.
4. **File only the verified ones as PRs**, with tests.
5. Publish a write-up: *"I ran an agent against project X for class Y of bugs. N findings, M verified, K PRs accepted."*

**Why it's the right artifact right now:**
- **Recruiter-legible** — there's a famous announcement two days old you're emulating; people will read your README.
- **Cheap** — pick one project, one class of bug. ~5–8 hours total.
- **Maps directly to job applications** — IBM Security, Trail of Bits, Exaforce, any Daybreak partner — see [`05` §1](./05-career-and-startup.md#1-soc-lane-firing).
- **Interview-grade story** — the verification step is where most candidates lose; if you can speak to *"the model found 17, I verified 6, I filed 4, 2 merged,"* you're already past the median FDE interviewer.

→ Cross-link: [`05` §1 SOC lane](./05-career-and-startup.md#1-soc-lane-firing) · [`02` §1 Patch the Planet (where to point at the same pattern)](./02-new-emerging.md#1-patch-planet-ibm-daybreak) · [`04` §1 verification benchmarks](./04-research-progress.md#1-planning-and-real-world-benches) for the eval vocabulary.
