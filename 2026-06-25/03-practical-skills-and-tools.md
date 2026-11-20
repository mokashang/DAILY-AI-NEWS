# Practical Skills & Tools — 2026-06-25

What to deploy *tonight*. Two big shifts this week make this section unusually actionable: **(1) Claude Tag is in Slack** (multiplayer agent — set it up before your peers do), and **(2) Claude Code shipped a defensive feature pack** in the same week Anthropic accused Alibaba of a 28.8M-query distillation attack — read that as Anthropic's *own* IR response embedded in a release. Use what they're shipping for themselves, on yourself.

Tags: `#claude-code #claude-tag #mcp #slack #security #productivity #orchestration`

---

## 1. The Claude Tag setup recipe (30 minutes tonight) {#1-claude-tag}

**Why now:** Claude Tag landed Jun 23 with the launch credit window open to Enterprise and Team customers. You're going to want it on your resume by next week. The play is **personal-prep first** so you can speak to it in interviews, then **deploy it at the first opportunity** (intern team, research lab Slack, project group chat).

**Sources:**
- [Anthropic — Introducing Claude Tag](https://www.anthropic.com/news/introducing-claude-tag) `[primary]`
- [Anthropic — Introducing Claude Opus 4.8](https://www.anthropic.com/news/claude-opus-4-8) `[primary]`
- [Kie.ai — Claude Tag Release: Anthropic's Slack Async Agent](https://kie.ai/blog/claude-tag-anthropic-slack-async-agent) `[analysis]`
- [TechRepublic — Anthropic Launches Claude Tag, Bringing AI Agents Into Slack](https://www.techrepublic.com/article/news-anthropic-claude-tag-ai-agent-slack/) `[secondary]`

### The 30-minute setup

1. **Workspace plan check** — Claude Tag requires **Enterprise or Team** at launch. Personal Slack workspaces can join *Team* for ~$30/seat/month — cheap enough to do for one weekend of practice and cancel. (If you have a student-org Slack, ask the admin.)
2. **Install Claude Tag** *(replaces the old "Claude in Slack" app — Anthropic gives admins 30 days to migrate; do it now if your org still has the legacy app)*.
3. **Pick one channel to start.** Make it a *low-stakes* channel — a project archive or a research-reading channel. **Do not** drop Claude Tag into your team-wide #general on day one.
4. **Set up MCP connections.** Claude Tag inherits your workspace's MCP config (GitHub, Linear, Notion, Sentry, etc.). Connect only what's needed for the channel — see §3 below for the hygiene checklist.
5. **Toggle "ambient mode" off for the first week.** Ambient = Claude proactively surfaces updates. Turn it on after you've watched a week of *reactive* behavior and trust the boundaries.
6. **Run the demo prompt:** `@Claude — summarize the last 2 weeks of this channel into a Notion doc, and link each bullet back to the source message.` This single command tests: read-channel-history, MCP-to-Notion, source-citation, and async-task-completion.
7. **Measure something.** Log how long *you* would have spent on Claude Tag's first 5 tasks. **That's the slide in your interview deck.**

### Why it matters to you

- **Job lens:** Within 90 days, **"experience deploying Claude Tag in a real Slack workspace"** will be a real bullet on FDE / Solutions / Integration Engineer postings at Anthropic, OpenAI, and at every consultancy hiring around Claude (PwC, Deloitte, EY, Accenture). Get the experience cheap now while the differentiator is fresh.
- **Startup lens:** The pattern Claude Tag exposes is **"AI joins the team channel where work happens, not the chat UI of a separate app."** Whatever vertical you're building in, ask: *what's the equivalent shared surface in this customer's workflow, and how do I put the agent there?* For healthcare it might be **Microsoft Teams + EMR**; for legal **iManage + Outlook**; for finance **Symphony**. The wedge is *the channel*, not the agent.
- **Insight:** **65% of Anthropic's product-team code is written by their internal Claude Tag** — that's the ceiling, not the floor. The skill that pays is **closing the gap** between that and a typical external team's 15–30% landing zone — i.e., **measurement + tuning + onboarding rituals**, not "deploy the agent."

→ Cross-link: [`01` §3 the launch details + the 65% number](./01-big-lab-moves.md#3-claude-tag).

---

## 2. Claude Code's defensive feature pack — turn these on tonight {#2-claude-code-defense}

**Why now:** Anthropic's Jun 24 Claude Code release notes ship a tightly themed bundle: **sandbox credential blocking, organization model restrictions, structured-output reliability, remote MCP, session-resume fixes, GitHub App setup improvements.** Read in the context of the Alibaba distillation accusation, it's the *security-and-governance* face of the same week. **Defaults moved.** Update yours.

**Sources:**
- [Releasebot — Claude Code Updates by Anthropic — June 2026](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Claude Help Center — Release notes](https://support.claude.com/en/articles/12138966-release-notes) `[primary]`
- [TrueFoundry — Claude Code Security Best Practices for Enterprise Teams](https://www.truefoundry.com/blog/claude-code-security-best-practices) `[analysis]`
- [Claude Code best practices guide (Anthropic docs)](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Clarista — Claude Code MCP Servers & Plugins: The Complete 2026 Guide](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) `[analysis]`

### Tonight's checklist

1. **Enable sandbox credential blocking.** This prevents Claude Code's sandbox tasks from auto-reading credentials from your shell env (the **#1 prompt-injection escape route** in agentic coding). Off → On.
2. **Set org model restrictions** — pin Claude Code to a specific Opus/Sonnet model version, blocking accidental jumps to an unfamiliar model on auto-update. Belt + suspenders for reproducibility.
3. **Test structured-output reliability.** If you've built any pipeline that parses Claude's output as JSON, run your test suite against the new build — Anthropic specifically called out reliability improvements; *don't* assume your parser is OK.
4. **Update remote MCP config.** If you've been running MCP servers locally, the remote-MCP session-handling fixes mean some patterns that needed local subprocesses now run remote. **Audit your `.mcp.json`** — see §3 below.
5. **Migrate GitHub App setup.** The June notes call out improvements; if you set up Claude Code's GitHub integration via PAT, switch to the GitHub App now (narrow scopes, easier rotation).
6. **Resume-session test.** Run a long task, interrupt the terminal, resume. Confirm session restoration works on your stack before relying on it for a deadline.

### Why it matters to you

- **Job lens:** "**I migrated our team from PAT-based to GitHub-App-based Claude Code setup, audited our `.mcp.json` against the principle of least privilege, and turned on sandbox credential blocking before the Alibaba distillation news broke**" is a real interview answer. The story you're telling: *I think defensively about agent infra without being asked.*
- **Startup lens:** Customers buying Claude Code at the enterprise tier increasingly need an answer to "**how do you stop a prompt-injected agent from exfiltrating our Postgres credentials?**" The answer involves the sandbox + org-model-restrictions + MCP credential scoping that shipped this week. Anyone selling **"Claude Code at scale" professional services** (PwC, consultancies, frontier-lab Solutions teams) now has a free thirty-minute hardening playbook to attach to their first deliverable.
- **Insight:** The releases this week tell you what Anthropic *itself worries about*. The bundle = **(input integrity: sandbox credential blocking) + (model-supply-chain control: org model restrictions) + (output integrity: structured output) + (lifecycle: session handling).** That's a *threat model*. Memorize it; it doubles as the **AI Engineer interview framework** for "how do you think about agent reliability?"

→ Cross-link: [`01` §1 the distillation context](./01-big-lab-moves.md#1-alibaba-distillation).

---

## 3. The MCP-server hygiene checklist (do this once, audit monthly) {#3-mcp-hygiene}

**Why now:** The 2026 baseline for MCP-server config has stabilized into a small set of rules. If you've been adding servers ad-hoc since 2025, you're past the threshold where Claude's tool selection degrades.

**Sources:**
- [Codersera — Best MCP Servers for Claude Code & Cursor (2026)](https://codersera.com/blog/best-mcp-servers-claude-code-cursor-2026/) `[analysis]`
- [TinyFish Blog — Best MCP Servers for Claude Code 2026: 30 Verified](https://www.tinyfish.ai/blog/best-mcp-servers-for-claude-code) `[analysis]`
- [TrueFoundry — MCP Authentication in Claude Code 2026 Guide](https://www.truefoundry.com/blog/mcp-authentication-in-claude-code) `[analysis]`
- [MCP Directory — Claude Code Best Practices: From Vibe Coding to Agentic Engineering (2026)](https://mcp.directory/blog/claude-code-best-practices) `[analysis]`

### The rules

1. **Soft ceiling of ~40 active tools across all MCP servers** (Cursor; Claude Code is similar past ~50). Beyond it, Claude *silently picks the wrong tool* — descriptions all sit in the context window and the right one gets crowded out. **Disable servers you're not actively using.**
2. **`CLAUDE.md` ≤ 200 lines.** Past that, instructions get diluted. Move long-form guidance into `.claude/rules/*.md` with `paths: globs` so only the relevant rule loads for the file you're editing.
3. **Least-privilege credentials per server.**
   - **GitHub MCP** → read-only PAT or GitHub App with scoped repos.
   - **Postgres MCP** → read-only role + statement-timeout + schema allowlist.
   - **Filesystem MCP** → restrict to a project subtree.
   - **AWS / cloud MCP** → assume an IAM role with `AdministratorAccess` *only* if you're a single human with one project; otherwise scope to a service role.
4. **Never put secrets in `.mcp.json`** — it's committed by most teams. Use `env:` blocks that reference shell env or `.envrc`.
5. **Restart the agent host after edits.** Both Claude Code and Cursor read MCP config at startup and ignore mid-session changes.
6. **Track the config as a dotfile.** Comment *why* each server is there; review on every change.
7. **Pin server versions** when shipping the config to a team — MCP servers update fast; you don't want yesterday's debugging session to be unreproducible.

### Tonight's *minimal* server set (≤ 8 tools each, ~30–40 total)

- **Filesystem** (project subtree only) · **GitHub** (read-only PAT) · **Postgres** (read-only) · **Brave Search** / **Fetch** (one, not both) · **Memory** / **Sequential Thinking** (one, not both) · **Linear** *or* **Notion** *or* **Slack** (only the team-coordination one you actually use) · **Sentry** (if you actually own a service) · **Playwright** (only when you need browser automation; disable after).

### Why it matters to you

- **Job lens:** The hygiene checklist *is* the interview answer to "how do you operationalize MCP at a team?" Each rule maps to a real failure mode you can name.
- **Startup lens:** **MCP-server-as-a-service** (hosted, scoped, audited, billable) is a real wedge — *security & compliance* on top of the open MCP protocol. Several startups (TrueFoundry, others) already orient that way. If you wanted to ship a *very small* SaaS this summer, **"managed MCP for regulated enterprises"** is on-thesis with the Anthropic Alibaba story.

---

## 4. The model-routing primitive (the 40%-cheaper Opus-orchestrator pattern, updated) {#4-orchestration}

**Carry-forward from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost):** Opus-as-orchestrator + Sonnet-as-workers ≈ 40% cheaper than all-Opus. June update: with **Opus 4.8** now GA, the same pattern *holds* — Opus 4.8 is faster and more capable than 4.7, so the orchestrator's overhead drops. **Re-measure your cost ratio this week** — anything you saw with 4.7 has likely shifted.

The arXiv side of this is now its own lane — see [`04` §1](./04-research-progress.md#1-cost-orchestration). Key idea worth borrowing into your Claude Code workflows tonight:

- **For each step, the orchestrator emits a decision:** `respond | retrieve | tool_call | verify | stop`. Don't let workers self-decide — pin the action type at the orchestrator and let workers execute.
- **Log cost per action type** (~5–10 lines of code). Once you have the histogram, the cheap-substitution opportunities reveal themselves (most `verify` steps don't need Opus; most `respond` steps don't need verification).
- **Cap retries per action.** Distillation-style traffic isn't your problem, but **runaway agent loops** are — they're how your bill quietly 5×s overnight.

**Sources:**
- [arXiv 2603.19896 — Utility-Guided Agent Orchestration for Efficient LLM Tool Use](https://arxiv.org/abs/2603.19896) `[primary]`
- [arXiv 2512.01099 — Cost-Aware Model Orchestration for LLM-based Systems](https://arxiv.org/html/2512.01099v2) `[primary]`
- [Anthropic — Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) `[primary]`

### Why it matters to you (compressed)

- **Job lens:** "I built a per-step cost log into our Claude Code workflow and saved $X by routing 60% of `verify` calls to Sonnet" is the **most concrete cost-engineering artifact** you can show. Make it a public repo.
- **Insight:** The pattern is the same across vendors — pin action type at the orchestrator, route by cost — so it's portable when you change stacks. Skill > vendor.

---

## 5. Build-it-this-week: "Slack channel topology design for Claude Tag" {#5-artifact}

**The artifact.** A 2-page PDF + a sample Slack workspace export, posted publicly, that documents:

1. **One Claude per channel, not per workspace** — why.
2. **Channel categories and their Claude-Tag mode:**
   - `#proj-*` channels → ambient ON, async delegation OK.
   - `#team-*` channels (e.g. `#team-eng`) → ambient OFF, tagged only.
   - `#general` / `#random` → **Claude Tag explicitly excluded** (cultural cost > value).
   - `#research-reading` → ambient ON for summarization, OFF for opinions.
3. **MCP server allow-list per channel** — Linear in eng channels, Notion in research, GitHub only in `#proj-eng-*`.
4. **A 90-day measurement plan** — what you'll log, how you'll attribute uplift, what counts as success.

**Why this is the right artifact this week:** It does what generic "Claude is great" posts can't — it answers the *deployment* question companies are about to start asking. Five LinkedIn impressions of this will land in front of an Anthropic Solutions recruiter before next Friday.

→ Cross-link: [`05` §3 the Thursday action](./05-career-and-startup.md#3-action).

---

## Key tags

`#claude-code #claude-tag #opus #slack #mcp #security #sandbox #orchestration #cost #routing #productivity`
