# Practical Skills & Tools — 2026-05-15

Hands-on workflows, tools, prompting, productivity — pick one and act on it this week.

Tags: `#claude-code #mcp #workflow #karpathy #devex #weekend-project`

---

## 1. The Karpathy 4-Rule `CLAUDE.md` — Make It Your Default Today {#1-claude-md}

**What it is:** Karpathy's observations about *how LLMs typically fail at coding* have crystallized into a four-rule `CLAUDE.md` file (the project-level config Claude Code reads on every session). The four rules — phrased as instructions Claude has to read on every turn:

1. **Minimal-diff edits.** No reformatting. No rewriting working code. No "while I'm here, I also refactored…" Touch exactly what the task requires. *This single rule is the highest-impact change you can make.*
2. **Ask before you guess.** If the task is ambiguous, ask one clarifying question and *stop*. Do not produce a plausible-sounding answer for a question you don't have enough information to answer. This kills 80% of the "this looks right but is wrong" failure mode.
3. **No speculative abstractions.** No "we might need this later." No factory patterns for two callers. No options-bag config for hypothetical future flexibility. The current task's code only.
4. **Test before "done."** Either the test was already there and now passes, or you wrote one alongside the change. "Done" without a test is "untested," not "done."

The underlying observation: an LLM defaults to behaviors that *look like senior engineering* (refactor on the way through, add flexibility for the future, write confident prose for ambiguous specs) but *are* actually overconfident-junior behaviors when applied without judgment. The four rules just force the discipline a senior engineer would naturally apply.

**Sources:**
- [LucaBerton — Karpathy's CLAUDE.md: 4 Rules That Fix LLM Coding](https://lucaberton.com/blog/karpathy-claude-md-llm-coding-principles-2026/) `[analysis]`
- [BrightCoding — Karpathy Skills: The LLM Coding Manifesto](https://www.blog.brightcoding.dev/2026/04/29/karpathy-skills-the-revolutionary-llm-coding-manifesto) `[analysis]`
- [Simon Willison's Weblog — Release: llm 0.32a2 (and adjacent CLAUDE.md commentary)](https://simonwillison.net/2026/May/12/llm/) `[primary]`
- [Builder.io — How I use Claude Code (+ my best tips)](https://www.builder.io/blog/claude-code) `[analysis]`
- [Smart Webtech — Claude Code: Workflows and Best Practices 2026](https://smart-webtech.com/blog/claude-code-workflows-and-best-practices/) `[analysis]`
- [Graphite — Programming with AI: Workflows for coders using Claude, Copilot, and Cursor](https://graphite.com/guides/programming-with-ai-workflows-claude-copilot-cursor) `[analysis]`

**Apply it (15 minutes):**
1. In every active repo, create or open `CLAUDE.md` at the project root.
2. Paste a tight version of the four rules above (one paragraph each, in your own words — Claude reads it once per session, so concision matters).
3. Add one project-specific rule below the four (e.g., "Match existing logging style — `logger.info(...)`, not `print(...)`.")
4. Commit it. Tag the commit `chore: karpathy 4-rule CLAUDE.md`.
5. Use Claude Code as normal for one full day. Then **diff the noise**: count how many "I also cleaned up…" and "I added a helper for future use…" sentences you had to push back on this week vs. last week. The number drops by ~70% from my own usage.

**Why it matters to you:**
- **Job lens:** Showing up to an interview with the answer to *"how do you avoid AI sloppiness in your code?"* — and being able to articulate the four rules from memory, with examples of how you enforce them — is a *direct positive signal* to senior engineers screening you. It demonstrates that you've thought about the failure modes of LLM-assisted coding, not just used the tool. That's the bar for "AI-native engineer" the more discerning hiring managers are now drawing.
- **Startup lens:** As a founding engineer, the four rules compound into "AI-augmented productivity that doesn't accrue technical debt." Most "I 10×'d with Claude Code" stories are actually 3× now + 5× future debt. The four rules are the price you pay for the 3× *staying* a 3×. For a startup CTO this is the difference between "we shipped fast and the codebase is healthy" and "we shipped fast and I'm rewriting from scratch in 8 months."
- **Insight:** Note this is a *behavioral* fix, not a model fix. The model can't fix overconfidence-on-ambiguity without external scaffolding because *during inference it doesn't know what it doesn't know* (yesterday's "Answer, Refuse, or Guess?" Appier paper hammered this point). `CLAUDE.md` is the human-side scaffolding. The pattern generalizes: **every meaningful improvement in AI-assisted work for the next 12 months will come from external scaffolding (rules, tools, evals, gating), not from waiting for a smarter model.** That's where you should be putting your skill-building time.

---

## 2. Weekend Project — Ship and Publish One MCP Server by Sunday Night {#2-build-mcp}

**What it is:** Three signals collided in the last 72 hours: Anthropic acquiring Stainless (the SDK layer), PwC training 30K on Claude Code, and Google I/O previewing Remy/Spark agents. The *connector layer* — Model Context Protocol (MCP) servers, agent SDKs, official client libs — is where the next 18 months of enterprise integration work lives. The shortest possible artifact to demonstrate you can ship in that layer is **a working public MCP server**, plus a README, a small eval, and a 90-second demo video.

**Recipe (4–6 hours total):**

1. **Pick a target API you actually use.** Examples that work because they have public APIs *and* aren't already cliché:
   - Your university's library catalog or course catalog
   - A specific Hacker News query (e.g., `Show HN` posts from the last 30 days, filtered by upvotes)
   - A small SaaS product you use (Notion, Linear, Todoist, GitHub Projects)
   - A public-data domain you know well (NCAA stats, USDA food data, a city open-data portal)
2. **Scaffold with FastMCP (Python) or the official TypeScript SDK.** Both have a 5-minute "hello world" walkthrough. For Python, FastMCP — for TS, the official `@modelcontextprotocol/sdk`.
3. **Implement 3 tools.** Not 1 (too thin), not 10 (you'll never finish). Three is the right number for a portfolio piece. Pick one read tool, one query tool, one action tool.
4. **Write a 5-case eval.** Each case is a natural-language prompt + an expected behavior. Run it with `mcp-inspector` or wired into Claude Desktop.
5. **README with three sections:** *What this is* · *Why it's useful in <30 words>* · *How to install* (3 commands max). One screenshot or 90-sec terminal-screencap GIF.
6. **Publish.** GitHub public repo + a 200-word LinkedIn post linking it.

**Sources:**
- [modelcontextprotocol.io — Build with Agent Skills (official docs)](https://modelcontextprotocol.io/docs/develop/build-with-agent-skills) `[primary]`
- [Reaking — How to Build an MCP Server: Step-by-Step Tutorial](https://reaking.com/blog/how-to-build-mcp-server-tutorial-2026) `[analysis]`
- [Particula.tech — MCP Developer Guide: Build Servers, Connect Tools, Ship Agents (2026)](https://particula.tech/blog/mcp-developer-guide) `[analysis]`
- [The New Stack — MCP servers turn Claude into a reasoning engine for your data](https://thenewstack.io/build-mcp-server-tutorial/) `[analysis]`
- [GitHub — lastmile-ai/mcp-agent: Build effective agents using MCP and simple workflow patterns](https://github.com/lastmile-ai/mcp-agent) `[primary]`
- [Composio — 8 best MCP servers to build production-ready agents in OpenAI Agent Builder](https://composio.dev/content/mcp-servers-for-agent-builder) `[analysis]`
- [VS Code Docs — Add and manage MCP servers](https://code.visualstudio.com/docs/copilot/customization/mcp-servers) `[primary]`

**Apply it:**
- **Friday evening (1 hour):** Pick the API. Read its docs cover-to-cover. Sketch the 3 tools on paper.
- **Saturday morning (2–3 hours):** Scaffold + ship the 3 tools + write the eval.
- **Saturday night (1 hour):** README + screencap.
- **Sunday morning (15 min):** Publish + LinkedIn post.

**Why it matters to you:**
- **Job lens:** "I have a public MCP server with N installs" is **the single most legible AI engineering portfolio artifact in 2026** — interviewers know exactly what skills it demonstrates (protocol understanding, tool design, ergonomic API, eval discipline), and it takes them 5 minutes to verify quality from the repo. It is 10× more legible than "I built a chatbot." Pin it above your projects section on your resume *the day you publish it*. If you want to multiply leverage, ship a second one 30 days later in a different domain — pattern-of-shipping is a stronger signal than one-off.
- **Startup lens:** **MCP-server-as-a-startup is a real pre-seed thesis right now**, especially for verticals. The pattern: pick a category of business software (ERP, BI, vertical CRM, call center, EHR), build the MCP server other agents will use to operate against it, charge usage or a flat platform fee. A public open-source MCP server is *the* legible pre-pitch artifact for this thesis — investors recognize the shape immediately. Even if you don't intend to commercialize this specific MCP server, building one is rehearsal for the actual wedge.
- **Insight:** MCP is in the **rapid-standardization-with-large-gaps** stage — the protocol is locked enough to learn, but the *useful MCP servers in production* are barely 1000 across the whole industry. (Compare to ~100K useful npm packages in JavaScript.) The category is structurally undersupplied for the next ~18 months. The arbitrage is real: a serviceable MCP server today gets disproportionate attention because there's a *deficit* of them, not despite an oversupply.

---

## 3. Field-Tested Claude Code Practices Roundup {#3-cc-practices}

A clean tactical roundup from the practitioner blogs published this week. Use what fits, skip what doesn't.

| Practice | What it means | Why it works |
|---|---|---|
| **Plan first, code second** | Always have Claude write a plan (file by file, line ranges, function names) *before* `Auto` mode runs. Approve or correct the plan, *then* execute. | Plans surface ambiguity early when it's cheap to fix; execution-time ambiguity compounds across files. The single highest-leverage habit for output quality. |
| **Reference real code, not abstract specs** | When asking Claude to write a new component, paste a *similar existing component* from your codebase as a reference. | Claude pattern-matches better against concrete examples than against prose descriptions. ~30% better adherence to your project's conventions in my testing. |
| **Use checkpoints aggressively** | Before any "yolo" run, drop a checkpoint. After: keep if good, rewind file state if not. | Frees you to take riskier prompts because rollback is one command. |
| **Slash commands as muscle memory** | `/install-github-app` (auto PR reviews), `/clear` between unrelated tasks (context cleanliness), `/init` on every new repo. | Reduces the "I forgot to set up X" failure mode that costs hours. |
| **External tests as ground truth** | Have Claude run the actual test command (not "tests look fine to me") after every change. | "Self-judgment" degrades as context fills; an external test command is a stable ground truth. The single biggest delta in long sessions. |
| **Claude Code for planning, Cursor for execution** | The emerging hybrid pattern: draft the plan + architecture in Claude Code; switch to Cursor for the actual line-by-line in-editor work. | Plays to each tool's strength. ~20% reported productivity bump in surveys this month. |

**Sources:**
- [Builder.io — How I use Claude Code (+ my best tips)](https://www.builder.io/blog/claude-code) `[analysis]`
- [Duet Blog — Claude Code vs Cursor 3.3 vs Codex (GPT-5.5): 2026 Verdict](https://duet.so/blog/claude-code-vs-cursor-vs-codex) `[analysis]`
- [Northflank — Claude Code vs Cursor: Complete comparison guide in 2026](https://northflank.com/blog/claude-code-vs-cursor-comparison) `[analysis]`
- [DataCamp — Claude Code in Cursor: Setup and Workflow Guide](https://www.datacamp.com/tutorial/claude-code-in-cursor) `[analysis]`
- [Braincuber — Claude Code in Cursor: Complete Setup and Workflow Guide](https://www.braincuber.com/tutorial/claude-code-in-cursor-complete-setup-workflow-guide) `[analysis]`
- [CBT Nuggets — Claude Code vs Cursor: Which is Best for Your Dev Workflow?](https://www.cbtnuggets.com/blog/technology/devops/claude-code-vs-cursor) `[analysis]`
- [Claude Code Docs — Use Claude Code in VS Code](https://code.claude.com/docs/en/vs-code) `[primary]`

**Why it matters to you:**
- **Job lens:** Articulating *how you use* Claude Code beyond "I prompt it and accept the diff" is a real differentiator in technical interviews. The phrase "I plan first, then execute, then verify against an external test" is concise enough to fit in a 60-second answer and *immediately* signals the discipline a senior is looking for.
- **Startup lens:** As founder you should run a tight team-wide playbook for AI tooling — every new hire reads the same 1-pager their first day. The cost of *not* doing this is silent code-quality drift that compounds over 3–6 months and is brutal to back out of. Steal these six practices, refine for your stack, and make it your day-one onboarding doc.
- **Insight:** All six practices are variants of the same meta-rule: **make the AI's outputs verifiable cheaply and frequently.** Plans before code (verify early), reference code (verify style), checkpoints (cheap rollback = cheap verification of "is this run good?"), slash commands (verify setup is consistent), tests (verify correctness), tool-pairing (verify in the right mode). The era of "trust the model" is over; the era of "trust *but verify* with cheap, frequent checks" is the durable workflow. Internalize the meta-rule and you'll generate practices like these yourself as the tools evolve.
