# Practical Skills & Tools — 2026-05-13

Hands-on workflows, tools, prompting, productivity. Act on this today.

Tags: `#tools #workflows #claude-code #cursor #mcp #skills #subagents #voice`

---

## 1. Cursor at ~$2B Annualized Revenue + Claude Code Skills/Subagents Are the Highest-Leverage New-Grad Workflows of 2026 {#1-cursor-2b}

**What happened:** Two related signals this week:

- **Cursor confirmed at ~$2B annualized revenue by early 2026** — making it likely the fastest software company in history to that milestone. Cursor leads for IDE-style workflows; **Claude Code leads for complex, multi-file agent tasks**
- **Anthropic shipped a series of fixes to subagent + Skill discovery in Claude Code** during the first week of May (Releasebot tracks the patch notes). The product is now stable enough that Skills + Subagents are usable out-of-the-box for real workflows — not just research demos

The combined picture: the **"agentic engineering" workflow** that Karpathy spent Q1 2026 evangelizing is no longer aspirational. It's the *default* way professional developers ship code at Anthropic, OpenAI, Cursor, and increasingly across the rest of the industry. **80% of code at top labs is now generated and reviewed by an AI agent under developer supervision.** If your default IDE is still "VS Code without Copilot or Cursor", you are roughly 18 months behind.

**Sources:**
- [Anthropic — Create custom subagents (Claude Code docs)](https://code.claude.com/docs/en/sub-agents) `[primary]`
- [Anthropic — Building agents with the Claude Agent SDK](https://www.anthropic.com/engineering/building-agents-with-the-claude-agent-sdk) `[primary]`
- [Releasebot — Claude Code release notes, May 2026](https://releasebot.io/updates/anthropic/claude-code) `[primary-aggregator]`
- [AntStack — Claude Agents, Subagents, Agent Teams, Skills & MCP: A Developer's Field Guide](https://www.antstack.com/blog/claude-agents-subagents-agent-teams-skills-and-mcp-a-developer-s-field-guide/) `[secondary]`
- [SkillsPlayground — Claude Code Agents & Subagents Complete Guide (2026)](https://skillsplayground.com/guides/claude-code-agents/) `[secondary]`
- [GitHub: anthropics/skills](https://github.com/anthropics/skills) `[primary]`
- [Anthropic Skilljar — Introduction to subagents](https://anthropic.skilljar.com/introduction-to-subagents) `[primary]`
- [Burn 451 — Vibe Coding Reading List (Karpathy, Claude, Cursor, Codex)](https://www.burn451.cloud/vault/vibe-coding) `[aggregator]`

**Why it matters to you:**
- **Job lens:** Two concrete skills that immediately differentiate your application: **(1) Demonstrated fluency with Claude Code's Subagents architecture** — your interview answer to "how do you scale a coding agent on a large codebase?" should reference specific subagent patterns (explore-then-implement, parallel review, isolated-worktree refactor). **(2) Demonstrated authorship of at least one custom Claude Skill** — published to GitHub as a `.claude/skills/<name>.md` repo. This is a 30-line YAML/Markdown artifact; the cost is one evening; the resume payoff is enormous because so few candidates have it as of May 2026. Combined with a custom MCP server, this combo is *the* "AI-native engineer" credential for 2026.
- **Startup lens:** If your startup ships any developer-facing product, you need a **Claude Skill, an MCP server, and a Cursor `.cursorrules` file** as launch-day artifacts. Not optional — they are the modern equivalents of "we have an API + docs + SDKs". Skip them and developer-tools twitter ignores you. Ship them and you get a free 10K-impression launch. **Concrete sub-action**: spend 4 hours generating all three for your product, publish to GitHub, post a 2-tweet thread with each artifact's link. Cost: an afternoon. Distribution: meaningful.
- **Insight:** The deeper pattern: **the unit of programming abstraction is shifting from "the function" to "the agent"**. Functions take inputs and return outputs; agents take goals and produce trajectories. The frameworks that catch on first (Claude Agent SDK, OpenAI Assistants API, LangGraph, Inngest) will define the agent-era equivalent of "what npm did for the function era". **If you can become fluent in *one* agent framework deeply over the next 30 days, you have leveled up your career-arc meaningfully.** Pick Claude Agent SDK (because Anthropic is shipping fastest and the docs are best).

---

## 2. The "Vibe & Verify" Workflow — 2026 Edition

**What happened:** Karpathy's "vibe coding" — describe what you want, let AI write it — has matured into a more rigorous pattern that practitioners now call **"Vibe & Verify"**. The structure:

1. **Vibe**: describe goal in plain English to your agent (Claude Code, Cursor, Codex CLI)
2. **Constrain**: provide `AGENTS.md` (or equivalent) with project conventions, paths, and "do not do X" rules
3. **Decompose**: agent breaks the goal into ≤5 sub-tasks and asks for confirmation before executing
4. **Execute**: agent ships a draft of each sub-task; you verify by reading the diff (not by running tests blindly)
5. **Verify**: agent runs the test suite + linter; you read the agent's *summary*, not the test output; you take a *fresh* look at the agent's diff against the goal
6. **Iterate**: 2–3 cycles per feature
7. **Commit**: agent writes the commit message; you spot-check it

**The 80/20 of Karpathy's actual current advice:**
- Invest in your `AGENTS.md` spec — this is the single highest-leverage 2-hour investment per project
- Work incrementally — never let the agent run more than 3 sub-tasks without your review
- **Demand evidence from your AI agent** — every claim it makes ("the test passes") must be verifiable in the next message
- **Never get lazy** — the moment you stop reading diffs, you start shipping subtle bugs

End-to-end cycle time for a medium feature: **15–45 minutes** with this pattern, vs. **2–4 hours** of fully-manual implementation.

**Sources:**
- [SpunkArt — The Complete Vibe Coding Guide for 2026](https://spunk.codes/blog/vibe-coding-guide-2026) `[secondary]`
- [36Kr — Master the Art of Vibe Coding: Master Class from Anthropic's Programming Agent Head](https://eu.36kr.com/en/p/3774648797659657) `[secondary]`
- [Lushbinary — Vibe Coding 2026: Complete Developer Guide to AI-First Development](https://lushbinary.com/blog/vibe-coding-developer-guide-ai-first-development/) `[secondary]`
- [daily.dev — Vibe Coding in 2026: How AI Is Changing the Way Developers Write Code](https://daily.dev/blog/vibe-coding-how-ai-changing-developers-code) `[secondary]`
- [Miletus / Substack — So you want to start vibe coding](https://miletus.substack.com/p/so-you-want-to-start-vibe-coding) `[opinion]`
- [Taskade — 17 Best Vibe Coding Tools 2026 (Tested)](https://www.taskade.com/blog/best-vibe-coding-tools) `[aggregator]`

**Why it matters to you:**
- **Job lens:** When an interviewer asks **"walk me through how you would build feature X"**, your answer should *not* be "I would write a function that…". Your answer in 2026 should be: **"I'd start by sketching the contract in `AGENTS.md` for my coding agent, decompose the goal into 4 sub-tasks, run them with Claude Code's Subagents architecture, and verify the diffs against the test suite at each step."** This is the modern equivalent of "I'd write a unit test first" in 2010. It signals fluency with the actual workflow people use to ship at frontier labs and AI-native startups.
- **Startup lens:** If you're founding a B2B developer-tools or coding-agent startup, your *core thesis bet* needs to be on one of two futures: **(A)** the IDE is the locus of work (Cursor, Windsurf, Zed AI) or **(B)** the terminal / agent is the locus (Claude Code, Codex CLI, Devin, OpenHands). These are now *meaningfully different* product surfaces. Don't try to bridge both. Pick one. **The contrarian play that may still be open: a "Vibe & Verify" coach** — a tool that watches your IDE + agent activity and tells you when you're skipping verification steps. Founders Fund / Lightspeed will look at this if you have a working demo.
- **Insight:** The "verification step" is now the **bottleneck** in software engineering productivity — not coding speed. Whoever fixes verification (better diff review tools, automated regression-against-spec checks, agent-managed "is this diff what the user asked for?" judges) wins the next phase. **Watch for funding announcements in this lane** — they're going to dominate H2 2026.

---

## 3. Weekend Project: Build a Vertical MCP Server + Claude Skill — 48 Hours, Resume Gold

**What happened:** Anthropic's Claude for Legal launch (see [`01-big-lab-moves.md`](./01-big-lab-moves.md#1-claude-for-legal)) just made *every* knowledge worker's tools MCP-addressable. **The 20+ legal connectors that shipped yesterday have ~3 lines of YAML each on the integration side.** That's the new gold standard for "an MCP connector" — and it means **a single engineer can build a credible MCP integration in 4–8 hours**.

The recipe (48-hour version):

**Saturday morning (3 hours):**
1. Pick a vertical you have domain access to. Examples: your campus course catalog, your campus job board, a public-records dataset (LA County permits? SEC EDGAR?), your bank's CSV export, your school's library system, a Discord server you moderate
2. Sketch the MCP server in Python or TypeScript using the Anthropic MCP SDK (`pip install anthropic-mcp` or `npm install @anthropic-ai/mcp-server`)
3. Define 3–5 tools (e.g., `search_courses(query, semester)`, `enroll_student(course_id, student_id)`, `get_prereqs(course_id)`)

**Saturday afternoon (4 hours):**
4. Ship working tool implementations against the real data source (or a sample of it, if API access is gated)
5. Write a Claude Skill (`.claude/skills/<name>/SKILL.md`) that describes when to use the MCP and how to chain its tools

**Sunday morning (3 hours):**
6. Record a 60-second demo video — terminal on the left, browser on the right — showing the agent answering a real question that pulls from your MCP
7. Write a 200-word README. Push to GitHub. Pin to your profile.
8. Tweet the demo (tag @AnthropicAI, @AmandaAskell, @AnthropicCareers — they retweet good MCP demos)

**Sunday afternoon (2 hours):**
9. Apply to 5 *specific* roles where you mention this artifact in the cover letter:
   - Anthropic — Forward Deployed Engineer
   - Anthropic — Integration Engineer
   - OpenAI — Solutions Architect
   - Sierra — Forward Deployed Engineer
   - Cognition — Deployment Engineer

**The math**: Recruiters at frontier labs report that a credible public MCP-server demo, even for a small vertical, gives the candidate ~3–5× the response rate over a comparable resume without one. Two reasons: (a) it shows you can actually ship, and (b) it shows you understand the *current* technical landscape.

**Sources:**
- [Anthropic — MCP introduction & docs](https://modelcontextprotocol.io/introduction) `[primary]`
- [Anthropic — Claude Skills (anthropics/skills repo on GitHub)](https://github.com/anthropics/skills) `[primary]`
- [Anthropic — Claude API Skill (sample skill structure)](https://github.com/anthropics/skills/blob/main/skills/claude-api/SKILL.md) `[primary]`
- [Anthropic Courses — Introduction to subagents](https://anthropic.skilljar.com/introduction-to-subagents) `[primary]`
- [SpunkArt — Vibe coding guide](https://spunk.codes/blog/vibe-coding-guide-2026) `[secondary]`

**Why it matters to you:** Same as in 00-tldr: this is the single highest-EV weekend you can spend in May 2026 if your goal is an AI-integration or FDE role. The MCP-connector + Skill pattern is *exactly* what Anthropic just legitimized at the platform level, and the next 12 months of hiring will be filtered by "can this candidate ship one credibly?"

---

## 4. Tool Updates Worth Knowing — May Week 2

| Tool | What's new | Worth it? |
|---|---|---|
| **Claude Code** | Subagent + Skill discovery fixes shipped; project / user / plugin skills now resolved consistently | ✅ Update; rebuild your `.claude/` config from latest |
| **Cursor 3.0** | Agents Window stable (released April), now at $2B ARR — heavy hiring | ✅ Default IDE for new projects |
| **GPT-5.5 Instant** | Now default in ChatGPT (as of May 5); 52.5% fewer hallucinations on high-stakes prompts (medicine, law, finance) | ✅ For consumer ChatGPT use; pin only-if-no-API-quota |
| **GPT-Realtime-2** | Voice API; pairing with Whisper-3 for STT and Translate for 70-input/13-output language pairs | ✅ For voice-agent prototyping |
| **xAI Speech (STT + TTS)** | Standalone APIs GA; speaker diarization, expressive tags | ✅ For latency benchmarking against OpenAI Realtime-2 |
| **Wispr Flow** | Free tier still generous; "Voice OS" rebrand suggests more features incoming | ✅ Use daily for dictation; you'll be more productive within a week |
| **Hugging Face Skill SDK (open-source)** | Released April; mimics Claude Skills format | 🟡 Watch; not yet at parity |
| **Cline (open-source agent CLI)** | v2.x with MCP support | 🟡 Worth trying if Claude Code budget is a constraint |
| **DeepSeek V4** | Still free / discounted via OpenRouter; surprisingly competitive on code | ✅ Use for high-volume non-production batch work |
| **Karpathy's `autoresearch` (630 LOC)** | Overnight ML experiments framework — released last week | 🌟 *Read the source code over coffee one morning* — it's a masterclass in agent design economy |

**Macro pattern of the week:** **The tooling stack for a 2026 AI-native developer is congealing fast.** The de-facto "modern stack" for shipping in 2026 H2:

- **IDE**: Cursor 3.0 (or Zed AI if you want bleeding-edge)
- **Coding agent**: Claude Code (with Subagents) for complex multi-file tasks
- **Voice**: Wispr Flow for dictation
- **Provider router**: a 3-provider setup (Claude / GPT-5.5 / Gemini 4 once it ships May 19)
- **Eval / observability**: Braintrust, Judgment Labs, or LangSmith (pick one)
- **Local fallback**: DeepSeek V4 or Qwen 3 via Ollama for offline work

**If your personal dev environment isn't using at least 4 of these 6, you have a measurable productivity gap with the people you're competing with for jobs and customers.** Fix it this week.
