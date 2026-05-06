# Practical Skills & Tools — 2026-05-06

Hands-on stuff you can act on today. Tools, workflows, prompting, security, and productivity.

---

## 1. Cursor 3.0 Agents Window — How to Actually Use It

**What it is:** Cursor 3.0's Agents Window lets you run multiple AI agents in parallel across different repos, environments (local, SSH, cloud, worktrees), and models simultaneously.

**How to get started:**
```
1. Upgrade Cursor to 3.0+
2. Cmd+Shift+P → "Agents Window"
3. Start your first agent with a task in natural language
4. Open a second agent for a different file or parallel feature
5. Use /best-of-n to run the same task across models and compare
```

**The `/best-of-n` workflow (genuinely new):**
- Type: `/best-of-n implement the auth middleware`
- Cursor spawns the task to Claude, GPT-5.5, and Gemini simultaneously, each in an isolated worktree
- Review the 3 implementations side-by-side, pick the best or merge pieces
- This is ensemble coding without writing any orchestration code yourself

**Async multitasking pattern:**
- Start a long refactor as a background agent
- Switch to a new agent to work on a separate feature
- Background agent surfaces results in the Agents Window when done

**Sources:**
- [Cursor 3.0 changelog](https://cursor.com/changelog/3-0)
- [Digital Applied — complete guide](https://www.digitalapplied.com/blog/cursor-3-agents-window-design-mode-complete-guide)
- [DataCamp — What is Cursor 3](https://www.datacamp.com/blog/cursor-3)

**Insight:** Most developers are still using Cursor like a fancy autocomplete. The Agents Window is a fundamentally different workflow — you're now a manager of a team of agents, not a line-by-line copilot user. Shift your mental model: define the task, delegate, review, merge.

---

## 2. Vibe Coding in 2026 — The Real Risks and How to Avoid Them

**What is vibe coding?** AI-assisted development where you describe a task in natural language and the LLM generates the code. Coined by Andrej Karpathy (OpenAI co-founder) in February 2025. Now the dominant coding style for prototyping and solo projects.

**The hard data on risks:**
- A CodeRabbit analysis of 470 open-source GitHub PRs found AI co-authored code has:
  - **2.74× more security vulnerabilities** than human-written code
  - **75% more misconfigurations**
  - Higher rates of logic errors and flawed control flow
- METR study (July 2025): experienced developers were **19% slower** with AI coding tools on complex unfamiliar tasks (despite predicting they'd be 24% faster)

**But senior engineers DO benefit:**
- 3+ years experience → **40–50% productivity gain** with AI tools
- Junior engineers → only **15–25% gain** (they struggle to evaluate AI outputs)

**ACM Technology Policy Council's 2026 warning:** Vibe coding lacks key safeguards for professional software. The "just accept everything the AI generates" approach is now widely recognized as risky.

**Best practices for 2026 vibe coding:**
1. **Be explicit about security in the prompt**: "write secure code, validate all inputs, encrypt passwords, check for SQL injection"
2. **Architecture is yours, implementation is the agent's**: You define the structure; the agent fills it in
3. **Review every PR as if a junior wrote it** — because in terms of judgment, they did
4. **Add AI-aware tests**: Testing frameworks that check logic and compliance specifically for AI-generated code
5. **Never vibe-code auth, payments, or data access** — these need human review at every line
6. **Use it for prototyping aggressively, but harden before shipping**

**Sources:**
- [Daily.dev — Vibe coding 2026](https://daily.dev/blog/vibe-coding-how-ai-changing-developers-code)
- [DEV Community — Secure vibe coded applications](https://dev.to/devin-rosario/how-to-secure-vibe-coded-applications-in-2026-208d)
- [Kaspersky — Safe vibe coding guide](https://www.kaspersky.com/blog/safer-vibe-coding-2026/55677/)
- [Softr — 8 vibe coding best practices](https://www.softr.io/blog/vibe-coding-best-practices)
- [ACM — Vibe coding safeguards warning](https://www.acm.org/media-center/2026/april/techbrief-vibe-coding)
- [Medium — Is vibe coding harmful?](https://medium.com/@uday.devworks/is-vibe-coding-harmful-complete-guide-to-risks-security-issues-best-practices-7aa4564c519d)

**Insight for you as a grad student:** The 40–50% productivity gain for senior engineers comes from the ability to critically evaluate AI output. Right now, every project you build with AI tools is also training you to be a better AI output evaluator — which is the actual skill that compounds. Don't skip review.

---

## 3. Context-First AI Development — The Real Differentiator

**The finding:** A DeveloperWeek 2026 report identifies "context" as the master key for AI tools. Organizations that feed necessary industry and company context to agents beforehand — or make it available during task execution — get dramatically better results than those using generic prompts.

**What "context-first" means in practice:**

**For coding agents:**
```
Bad:  "Fix the authentication bug"
Good: "You are working in a FastAPI app (Python 3.12, PostgreSQL).
       The auth module is in /src/auth/. The issue is that JWT tokens
       are not being invalidated on logout because the blacklist check
       in /src/auth/middleware.py:validate_token() is skipped when
       the user is marked as 'admin'. Fix this specific bug without
       changing the token generation logic."
```

**For research/writing agents:**
```
Bad:  "Summarize this paper"
Good: "I am a CS grad student working on multimodal reasoning.
       Summarize this paper in 3 parts:
       1. Technical contribution (1 paragraph, assume ML background)
       2. How this relates to visual grounding in MLLMs
       3. Whether I should cite this in my related work section and why"
```

**Building a project context file:** Keep a `CONTEXT.md` in every repo with:
- What the project does and who uses it
- Key architectural decisions and their reasons
- What's in scope vs explicitly out of scope
- Current tech stack and versions

Then prefix every agent session: "Read CONTEXT.md before starting any task."

**Sources:**
- [Axify.io — AI developer productivity 2026](https://axify.io/blog/use-ai-for-developer-productivity)
- [Stack Overflow — DeveloperWeek 2026](https://stackoverflow.blog/2026/03/05/developerweek-2026/)
- [DEV Community — AI-powered dev workflow 2026](https://dev.to/devactivity/the-ai-powered-dev-workflow-reshaping-software-engineering-in-2026-1mk4)

---

## 4. The 2026 AI Developer Stack — What's Actually Worth Using

Based on independent tests, Stack Overflow surveys, and DeveloperWeek 2026 data:

| Tool | What It's For | Cost | Signal |
|---|---|---|---|
| **Cursor 3.0** | IDE + parallel agents + code review | $20/mo | 85% of developers using AI tools report it as primary IDE |
| **Claude Code** | Terminal-first, complex multi-file, SWE-bench best | Usage-based | Highest benchmark performance on autonomous coding |
| **GitHub Copilot** | Inline autocomplete, PR workflows, tight GitHub integration | $10/mo | Best for teams already in GitHub ecosystem |
| **Devin** | Fully autonomous tasks (spin up, implement, open PR) | $20/mo | Dropped from $500/mo — commoditization signal |
| **Gemini CLI** | Free 1M context window, large codebase reads | Free tier | Best free tool for reading large existing codebases |
| **Bolt.new** | Rapid prototype from description | Free tier | Fastest "idea → deployed prototype" for demos |

**The 2-tool stack that covers 90% of needs:**
- **Cursor** for day-to-day IDE work and feature development
- **Claude Code** for large refactors, ambiguous architectural tasks, and anything requiring SWE-bench-level reasoning

**Sources:**
- [DataNorth AI — Top 10 AI tools 2026](https://datanorth.ai/blog/top-10-ai-tools-for-2026)
- [Iterathon — AI developer productivity stack 2026](https://iterathon.tech/blog/ai-developer-productivity-stack-2026-complete-toolchain-guide)
- [Vibecoding.app — developer workflows](https://vibecoding.app/blog/developer-workflows-with-ai)
- [DEV Community — best AI tools for developers](https://dev.to/devin-rosario/best-ai-tools-for-developers-to-boost-productivity-in-2026-4b97)

---

## 5. MCP (Model Context Protocol) — Still the Most Important Protocol to Learn

**Status:** MCP is now effectively the universal standard for connecting AI agents to external tools, APIs, and data. Every major agent platform supports it. It originated from Anthropic but is now truly cross-platform.

**Why you need to know it today:**
- "I built an MCP server for X" is a differentiating resume line
- MCP is to AI agents what REST was to web APIs — the plumbing that makes everything composable
- Building an MCP server that exposes a domain-specific data source plugs into *every* MCP-compatible agent

**How to build your first MCP server (1 hour project):**
```bash
npx @modelcontextprotocol/create-server my-mcp-server
cd my-mcp-server
# Edit to expose a real API (arXiv papers, your GitHub issues, a database)
# Connect in Claude Code: Settings → MCP Servers
# Test: ask Claude to "list today's papers on multimodal reasoning"
```

**High-value MCP servers to build for your portfolio:**
- arXiv paper fetcher for your research area
- Personal job tracker (GitHub issues + Glassdoor/Linkedin data)
- Codebase semantic search for your thesis/project repo

**Sources:**
- [MCP spec docs](https://modelcontextprotocol.io/docs)
- [Morphllm — AI coding agents 2026](https://www.morphllm.com/best-ai-coding-agents-2026)

---

## 6. AI Workflow Automation Without Code — Gumloop and Zapier AI

**What's new:** Both Gumloop and Zapier now let you describe an automation workflow in plain English and build it automatically.

**Practical automations for a CS grad student:**
```
"When a new paper is posted on arXiv with keywords 
[your research area], summarize it and add to my Notion research DB"

"When I get an email with 'job' or 'intern' in the subject, 
extract company name, role, deadline, and add to Airtable"

"When I commit to my GitHub repo, post a summary of changes 
to my research Slack channel"
```

**Sources:**
- [Gumloop — 10 best AI workflow automation tools](https://www.gumloop.com/blog/best-ai-workflow-automation-tools)
- [Progineous — best AI tools productivity 2026](https://progineous.com/blog/en/best-ai-tools-productivity-2026)

**Insight:** A solo grad student / founder running smart automations operates with the leverage of a 3-person team. Set up one automation per week for a month and see what changes.

---

## Quick-Start Actions for This Week

| Action | Time | Payoff |
|---|---|---|
| Upgrade to Cursor 3.0, try Agents Window | 30 min | Immediate productivity |
| Add `CONTEXT.md` to your main project | 20 min | All agent sessions improve |
| Read your last vibe-coded PR for security issues | 1 hr | Find bugs before they ship |
| Build a minimal MCP server for your research area | 1-2 hr | Resume differentiator |
| Set up 1 Gumloop/Zapier arxiv automation | 45 min | Daily paper awareness |
