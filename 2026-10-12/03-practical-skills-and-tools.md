# Practical Skills & Tools — 2026-10-12

Two concrete artifacts to ship this week — a **router update** reflecting the 5.5 line + Computer-Use leg, and a **Dots + Computer-Use demo** that shows you can build on the OpenAI DevDay platform turn. Both are small enough to fit a weekend and specific enough to lead with on an application.

Tags: `#router #claude #opus-5-5 #sonnet-5-5 #gpt-6 #computer-use #agents #cost #prompt-caching #skills`

---

## 1. Update the Sept-10 router shim for the 5.5 family {#1-router-update}

**The brief:** The Sept-10 router artifact ([`2026-09-10/03` §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact)) routed between Opus-5, Sonnet-5, Haiku-5, and GPT-5.6 Sol / Gemini 3.8 Flash. **Rebuild it** with:

| Leg | Model | $ per 1M in / out | Use case |
|---|---|---|---|
| **Reasoning (hard planner)** | `claude-opus-5-5` | $4 / $20 | Agent planner nodes, complex code review, long-chain reasoning |
| **Default worker** | `claude-sonnet-5-5` | $2 / $10 | 90% of agent steps — tool use, retrieval, summary, draft |
| **Hands-on (computer use)** | `gpt-6-astra` via **Agents API with Computer Use** | $10 / $50 | UI automation, OSWorld-style tasks, visual tool-use |
| **Cheap verifier** | `claude-haiku-5-5` (fallback: Haiku 4.5) | ~$0.25 / $1.25 est. | Pre-flight checks, prompt-injection scan, trajectory-verifier |
| **Multimodal / long-context** | `gemini-3.8-flash` | $1.50 / $9 | 1M-token document summary, cheap batch work |

**The code shape** (same as Sept-10, three new lines):

```python
# router.py — adds 5.5 family + Computer-Use leg
# ~30 LOC. Logs per-request $, latency, task_type.
def route(task_type: str, prompt: str, tools=None):
    if task_type == "reason":        return call_claude("opus-5-5", prompt)
    if task_type == "computer_use":  return call_openai_cu("gpt-6-astra", prompt, tools)
    if task_type == "verify":        return call_claude("haiku-5-5", prompt)
    if task_type == "long_context":  return call_google("gemini-3.8-flash", prompt)
    return                           call_claude("sonnet-5-5", prompt)  # default
```

**The eval**: same 5-case suite from Sept-10 + **one new case** — a "computer-use" task (open calculator, compute, paste result; or open a URL, extract one field). Log cost per case per leg; publish the diff.

### Why it matters to you

- **Job lens:** The router artifact is the **single highest-leverage artifact** on your public GitHub for FDE / AI-Engineer loops this quarter. Updating it with the 5.5 line *and the Computer-Use leg* in one PR shows two things recruiters triangulate: (a) you track the frontier release-by-release, (b) you understand OpenAI's platform turn well enough to integrate it. Lead with the diff in your next cold email.
- **Startup lens:** Your router is a **free piece of market research** — the per-leg cost / latency / win-rate numbers are the data every router startup (OpenRouter and incumbents, see [`02` §4](./02-new-emerging.md#4-open-weights-infra)) sells. If your evals show something non-obvious (e.g. Sonnet-5.5 within 5% of Opus-5.5 on *your* workload at ⅕ the cost), **publish the blog post**. It'll do double duty — recruitment signal + inbound-founder signal.
- **Insight:** The *point* of the router artifact is not that your router is better than OpenRouter. The point is **the discipline of maintaining it is now the career-signalling skill** — the same way "I use git" was in 2015 and "I use Docker" was in 2018. Candidates with a maintained router + eval suite will be hired over candidates with a kitchen-sink portfolio.

**Ship it tonight.** 30 LOC + 6 cases + one blog post + one tweet.

→ Cross-link: [`01` §1 Opus 5.5 pricing](./01-big-lab-moves.md#1-opus-55) · [`01` §2 Sonnet 5.5 behavioral cost drop](./01-big-lab-moves.md#2-sonnet-55).

---

## 2. The Dots + Computer-Use demo (ship this week) {#2-dots-computer-use}

**The brief:** OpenAI's DevDay introduced two primitives you can build on *immediately*: **Dots** (persistent, always-on agents on GPT-6 Astra) and the **Agents API with Computer Use** (sandboxed computer control via SDK). Combined, they answer the single most common FDE interview question of Q4 2026 — "walk me through building a persistent agent that takes real actions."

**The artifact** (one weekend, one repo):

1. **Scaffold a Dots-style always-on agent** for a *real* workflow. Three good candidates:
   - **Receipt processor**: watches an inbox, extracts amounts, categorizes, writes to a Google Sheet. (High signal — demonstrates persistence, structured output, OAuth, long-context.)
   - **GitHub triage bot**: labels incoming issues, auto-closes duplicates, assigns reviewers. (High signal — demonstrates platform integration, deterministic output, hooks.)
   - **Calendar-conflict negotiator**: reads a user's calendar, finds a 30-min slot across 3 external invitees' availability. (High signal — multi-agent coordination, Computer-Use for scraping external calendars where no API exists.)
2. **Add a Computer-Use subagent** for one step the Agents API can't cleanly handle via tools — the point is to show you know *when* to reach for Computer-Use (brittle, expensive, powerful) vs an API call (fast, cheap, limited).
3. **Add a Claude Opus 5.5 planner** that decides between Computer-Use and API for each sub-task. This is the "best of both labs" moment that reads as architecturally mature.
4. **Record a 60-second GIF.** Push to GitHub. Tweet. LinkedIn post with the GIF.

**Why this specific combination:** Dots alone shows you know OpenAI's platform turn. Computer-Use alone shows you can control a browser. Opus-5.5 planner on top shows you understand that *the winning stack in Q4 2026 is multi-lab, not single-lab*. The three primitives together are the resume answer to "what's the agent architecture you'd pick in 2026" — and it's correct.

### Why it matters to you

- **Job lens:** This artifact threads **three** of your target job families at once. **FDE / Solutions**: it's a customer-shaped integration demo. **AI Engineer**: it's a multi-lab routing demo. **Applied-AI at a lab**: it demonstrates fluency with both labs' primitives. Fold the GitHub link into the first 100 words of every application email this month.
- **Startup lens:** The specific wedge the demo surfaces is **cross-lab orchestration** — i.e., "whose code chooses whether Dots or Claude Code runs this task?" If your demo shows a working planner that routes between labs with a cost + latency + reliability objective, you have the kernel of a Series-A pitch. Add "cross-lab agent orchestration" to [STARTUPS.md](../STARTUPS.md) as a new candidate wedge; your demo is the proof-of-concept.
- **Insight:** The *reason* this artifact lands harder than last cycle's "build an MCP server" artifact is that **Computer-Use is a durable primitive** — browser automation existed before, but putting it inside the frontier lab's SDK with sandboxed execution is new, and most engineers have not yet built with it. The ~90-day window where "I built with Computer-Use" is a differentiator closes around end-of-Q1-2027.

→ Cross-link: [`01` §3 DevDay recap](./01-big-lab-moves.md#3-openai-devday) · [`05` §2 Anthropic application plan](./05-career-and-startup.md#2-anthropic-hiring) · [STARTUPS.md](../STARTUPS.md).

---

## 3. Prompt caching on the 5.5 family — reset the cost dashboard {#3-prompt-caching}

**What changed:** The Sept-10 edition's prompt-caching reminder (Fable 5.1 cut cache reads **$1.00 → $0.25 per 1M**, a 75% reduction) still applies to Fable 5.1. For **Opus 5.5 and Sonnet 5.5**, re-check your pricing docs — the 5.5 family changed the base prices (Opus $5→$4 input), and cache-read / cache-write multipliers may have moved with them.

**Working rules of thumb** (verify against the official pricing page before relying on them):

- Cache-write typically ~1.25× base input rate.
- Cache-read typically ~0.1× base input rate.
- Default TTL ~5 min, configurable to ~1 hour.
- Break-even hit-rate for cache-write on long prompts is **~30%** — below that, caching costs you money.

**The audit** (do this in 20 minutes):

1. Pull your last 30 days of Anthropic usage from the console.
2. Compute: (cache-hit tokens × read price) + (cache-write tokens × write price) + (uncached tokens × base price), all against three scenarios: (a) current, (b) hypothetical Opus-5.5, (c) hypothetical Sonnet-5.5.
3. Write up the savings as a one-page Markdown post. **This is a legit personal portfolio piece** that reads as "I can run cost analysis on an AI workload" — a specifically-asked question in FDE interviews.

### Why it matters to you

- **Job lens:** The "I audited my own Claude bill and here's what I found" post is one of the cleanest signals you can send. Specific enough to show real usage, generalizable enough to show methodology. Keep [ME.md](../ME.md#active-portfolio-artifacts)'s "Personal Claude billing audit + writeup" item alive — ship it this quarter.
- **Startup lens:** If your audit surfaces a repeated pattern (e.g., "every multi-turn agent I built wastes 40% of its input tokens on stale tool definitions") — that's a product. Agent-cost-observability is a founder-friendly category because the TAM is directly measurable (your prospects' AI bill × 10–30% addressable savings).
- **Insight:** The cost-audit workflow is the **first application of model-fluency being commoditized** — nobody can keep track of model-by-model pricing anymore, so the *analytical skill* of running the audit is the new scarce resource. In 2027, this becomes a standard part of the AI-Engineer job (c.f. how "runs their own perf dashboard" is standard for SRE).

→ Cross-link: [ME.md](../ME.md) *Personal Claude billing audit + writeup*.

---

## 4. The 2026-Q4 Claude Code decision tree (checklist form) {#4-claude-code}

**What changed from Sept-10:** The decision tree is unchanged in principle (**Hooks for enforcement / Skills for contextual knowledge / Subagents for context isolation / CLAUDE.md for always-on project guidance**), but community guides are converging on one additional rule: **keep CLAUDE.md short.** The "600-line CLAUDE.md" is the 2026 anti-pattern. Durable rules → Hooks or `settings.json`; durable domain knowledge → Skills (one SKILL.md per concern); always-on guidance → CLAUDE.md.

**Checklist for a well-structured 2026 Claude Code project**:

- [ ] `CLAUDE.md` is **under 100 lines**. Short, imperative, project-specific.
- [ ] At least **one Hook** on `PreToolUse` that enforces a repo rule (e.g., no `--no-verify` on commits).
- [ ] At least **one Skill** in `.claude/skills/` that encapsulates domain knowledge (e.g., deployment, review checklist, repo-specific workflow).
- [ ] **Subagents** declared for exploration / review / verification roles (so the main context stays clean).
- [ ] `.claude/settings.json` with the preferred model + any per-project tool allowlists.
- [ ] `.github/pull_request_template.md` referenced by Claude when creating PRs.

### Why it matters to you

- **Job lens:** Dropping a well-structured `.claude/` folder into every project tonight is the lowest-cost high-signal portfolio polish you can do. Interviewers increasingly `git clone` candidate repos; a `.claude/skills/` folder with 2–3 skills reads as "fluent in the 2026 agentic coding workflow" instantly.
- **Startup lens:** The "keep CLAUDE.md short" convention opens a **tooling wedge** — a `.claude/` linter / audit that scores a repo's agentic-engineering hygiene and suggests fixes. Not a big product, but a sharp top-of-funnel for a bigger developer-tools play.
- **Insight:** The 2026 convention around `.claude/` is the first time an agent-tooling file layout has stabilized across many projects. In 2027, this becomes the base for a *shared registry of community skills* — the pip/npm equivalent for Claude Code. If you're thesis-shopping, "skills marketplace" is a wedge worth sketching.

**Sources (reference reading, 2026 community guides):**
- [smartscope.blog — Claude Code Advanced Best Practices (2026)](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[analysis]`
- [memx.app — Claude Code daily engineering playbook](https://memx.app/blog/claude-code-daily-engineering-playbook/) `[analysis]`
- [composio.dev — Top 10 Claude Code Skills in 2026](https://composio.dev/content/top-claude-skills) `[aggregator]`
- [mcp.directory — Claude Code best practices (updated April 2026)](https://mcp.directory/blog/claude-code-best-practices) `[aggregator]`

→ Cross-link: [`2026-09-10/03` §2 Claude Code decision tree](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree).

---

## 5. MCP servers: 6,400+ servers in the registry, build one with a sharper wedge {#5-mcp-servers}

**What changed:** The MCP registry (per mid-2026 reporting) crossed **~6,400 servers**. "Build an MCP server" is no longer enough on its own as a portfolio piece — the field is crowded. **The 2026-Q4 move: build one with a sharp vertical wedge + a 5-case eval suite + a benchmark against the two closest competitors in the registry.**

**Three sharp wedges**:

1. **A real-tool evaluator MCP server** — exposes your eval suite as tools so Claude can test *itself* on your routing / cost / reliability objectives. (Doubles as [`03` §1 Router update's](#1-router-update) harness.)
2. **A compliance / documentation MCP server** — tools that generate Article 53 model documentation on demand, per the EU AI Act GPAI enforcement window ([`01` §5](./01-big-lab-moves.md#5-eu-enforcement)). Niche but hireable; nobody has built this yet publicly.
3. **A personal-workflow MCP server** — exposes your own repo set, task tracker, inbox search as tools. Dog-fooded, so you keep improving it; dog-fooded, so you talk about it in interviews naturally.

**Testing**: Use the official MCP Inspector (`npx @modelcontextprotocol/inspector`) — the standard in community guides.

**Sources:**
- [buildfastwithai — What is Model Context Protocol](https://www.buildfastwithai.com/blogs/what-is-model-context-protocol-mcp) `[analysis]`
- [truto.one — How to Build MCP Servers for AI Agents: 2026 Hands-On Guide](https://truto.one/blog/ai-agents/) `[analysis]`
- [hermify.io — MCP Server for AI Agents: Practical 2026 Guide](https://www.hermify.io/en/blog/mcp-server-for-ai-agents) `[analysis]`
- [cosmicjs — MCP server complete guide](https://www.cosmicjs.com/blog/mcp-server-complete-guide) `[analysis]`

### Why it matters to you

- **Job lens:** An MCP server with a *distinct wedge* + its own eval suite is the **ME.md** "Public MCP server" artifact closed out. Pick #2 or #3 above; #1 overlaps with your router artifact.
- **Startup lens:** The compliance-MCP wedge connects directly to the EU AI Act thread ([`01` §5](./01-big-lab-moves.md#5-eu-enforcement)) and is a legitimate "sell to Deloitte / EY" category.
- **Insight:** 6,400 servers in the registry is the stage where **registry-level discovery and curation** becomes the next slot. If you want to found something in the MCP ecosystem, "better registry / curation / rating" is the slot a well-run GitHub-trending-shaped startup lives in.

→ Cross-link: [ME.md](../ME.md) *Public MCP server* · [`01` §5 EU AI Act enforcement](./01-big-lab-moves.md#5-eu-enforcement).
