# Practical Skills & Tools — 2026-05-16 (Saturday)

Hands-on workflows, tools, prompting, productivity. Saturday-mode: two specific 60-minute actions, plus a tactical MCP roundup. Pick the one that matches your headspace and do it before bed.

Tags: `#claude-code #mcp #agent-sdk #cost #pricing #weekend-project #workflow`

---

## 1. Saturday Action #1 — Audit Your Claude Programmatic Spend Before June 15 {#1-billing-audit}

**Why now:** Anthropic's [June 15 metering change](./01-big-lab-moves.md#1-claude-metering) caps your programmatic Claude usage at $20/$100/$200 in credits depending on tier — billed at **full API list rates**. If you run *any* `claude -p` automations, GitHub Actions, custom Agent-SDK app, OpenClaw-style hosted scripts, or even a noisy `cron`-driven Claude Code job, your June bill is about to look very different. Do this audit *now* while you have 30 days to act.

**Recipe (60 minutes):**

**Step 1 — Inventory (10 min).** Grep your machine + repos for the surface area:

```bash
# All shell history references to claude -p
grep -rn "claude -p" ~/.zsh_history ~/.bash_history 2>/dev/null
# All repos that contain an agent SDK import
grep -rn --include="*.py" -E "from anthropic|import anthropic" .
grep -rn --include="*.ts" --include="*.js" -E "@anthropic-ai/(sdk|agent)" .
# All GitHub Actions calling Claude Code
grep -rn "anthropics/claude-code-action" .github/workflows/ 2>/dev/null
# Any local cron / launchd jobs invoking claude
crontab -l 2>/dev/null | grep -i claude
ls ~/Library/LaunchAgents/ 2>/dev/null | grep -i claude
```

Write the result down — list every file/script/workflow that hits Claude programmatically.

**Step 2 — Measure last 30 days of tokens (20 min).** For each programmatic surface:

- **Claude Code:** check usage in the web Anthropic console under *Usage & Billing → Token Usage*. Filter to the last 30 days. Note the input + output split.
- **Agent SDK / `claude -p`:** if you have stderr logs or a custom wrapper, scan them. If you don't, add a 10-line wrapper *today* that logs token counts per call — even a week's data is enough for a projection.
- **GitHub Actions:** workflow run summaries include token tallies; pull the last month.

Convert tokens → dollars at API list rates (rule-of-thumb, May 2026):

| Model | $/M input | $/M output |
|---|---|---|
| Claude Haiku 4.5 | $1 | $5 |
| Claude Sonnet 4.6 | $3 | $15 |
| Claude Opus 4.7 | $15 | $75 |

**Step 3 — Project June 15 → July 15 (10 min).** Multiply 30-day tokens × pricing × any growth multiplier you expect. Compare against your credit cap ($20 Pro / $100 Max-5x / $200 Max-20x).

**Step 4 — Choose your response (20 min).** Three patterns:

| If projected cost is… | Action | How |
|---|---|---|
| **< 50% of credit** | None — you're fine | Re-check in August |
| **50–150% of credit** | Optimize before the cutover | Prompt-caching (50–90% input cost cut on stable system prompts); model routing (route classification / extraction to Haiku, reserve Sonnet/Opus for hard tasks); batching where possible |
| **> 150% of credit** | Architectural change | Move the high-volume tier to (a) an open-source model running on Groq / Fireworks / Replicate ($0.10–$0.40/M for competent Llama-class), (b) a cheaper provider for the bulk path with Claude only on the *judgment* tier, or (c) Anthropic's standard pay-as-you-go API |

**Sources:**
- [InfoWorld — Anthropic puts Claude agents on a meter across its subscriptions](https://www.infoworld.com/article/4171274/anthropic-puts-claude-agents-on-a-meter-across-its-subscriptions.html) `[secondary]`
- [The New Stack — Anthropic splits billing again: Agent SDK gets separate credit pools](https://thenewstack.io/anthropic-agent-sdk-credits/) `[secondary]`
- [Zed Blog — What Anthropic's New Claude Billing Means for Zed Users](https://zed.dev/blog/anthropic-subscription-changes) `[primary]`
- [DEV.to / Vainamoinen — What Anthropic's $200 Agent SDK Credit Means If You Run claude -p in Production](https://dev.to/vainamoinen/what-anthropics-200-agent-sdk-credit-means-if-you-run-claude-p-in-production-ce2) `[analysis]`
- [Anthropic API pricing (reference)](https://www.anthropic.com/pricing) `[primary]`

**Why it matters to you:**
- **Job lens:** The audit *is* a portfolio artifact. After you finish, write a 400-word post: *"How I cut my Claude bill from $X to $Y in two hours after the June 15 metering change."* Show the inventory step, the measurement methodology, and the routing decision. This is high-trust evidence of three skills that aren't on most candidates' resumes: cost-aware AI design, profiling discipline, and rate-card literacy. Pin it on your personal blog or Medium; link from your resume. (Bonus: it doubles as your "let me show you how I'd think about it" answer to the *"how do you keep AI costs under control?"* interview question that's appearing in MLE loops this quarter.)
- **Startup lens:** Run the same audit for *every* application-layer agent startup founder you can get on a 15-minute call this week — pitch it as a free favor. Half will tell you they have no idea what their actual API spend distribution looks like. That's market research disguised as a kindness. The biggest pain points become the pitch deck for whatever cost-routing wedge you choose ([see startup-lens in 01](./01-big-lab-moves.md#1-claude-metering)).
- **Insight:** Almost every engineer treats inference cost as an *implementation detail* until pricing changes force the issue. **Engineers who internalize the unit economics of inference *before* the forcing function arrives have a 6–12 month head start over peers** when the forcing function does arrive. That's exactly what this audit teaches you in two hours. The skill compounds for the rest of your career.

---

## 2. Saturday Action #2 — Ship One MCP Server by Sunday Night (Carried From Yesterday) {#2-ship-mcp}

**Why this is still the #1 weekend project:** Three this-week signals reinforce it — Anthropic Stainless acquisition (May 12 → still open), PwC 30K-engineer Claude Code training (May 14), Google I/O Tuesday with Remy/Spark agent SDK previews (May 19). The connector layer is the work of the next 18 months. Carrying the full recipe from yesterday, here, so you don't context-switch.

**Recipe (4–6 hours total):**

1. **Pick an API you actually use.** Examples: your university's library catalog; a Hacker News query (`Show HN` ≥50 points, last 30 days); a SaaS you live in (Notion, Linear, Todoist, GitHub Projects); a public-data domain you know (NCAA stats, USDA food data, a city open-data portal).
2. **Scaffold with FastMCP (Python) or `@modelcontextprotocol/sdk` (TypeScript).** 5-minute hello-world walkthroughs in either.
3. **Implement 3 tools.** One *read* tool, one *query* tool, one *action* tool. Three is the right number for a portfolio piece.
4. **Write a 5-case eval.** Each case: a natural-language prompt + an expected behavior. Run with `mcp-inspector` or Claude Desktop.
5. **README:** *What this is* · *Why it's useful in <30 words>* · *Install in 3 commands*. One screenshot or 90-sec terminal GIF.
6. **Publish.** GitHub public repo + 200-word LinkedIn post.

**Plus a 2026-specific best-practices layer (from this week's tutorials):**

| Practice | Why it matters |
|---|---|
| **Keep tokens out of `.mcp.json`** — use `env:` references to shell variables, not inline secrets | The file gets committed; the secret leaks. Repeatedly. |
| **Limit each MCP server to ≤8 tools** | Cursor warns past ~40 active tools across all servers; Claude Code's behavior degrades past ~50 visible. A tight tool list improves selection accuracy. |
| **Restart the agent host after every config change** | Both Claude Code and Cursor read the file at startup. Edits without restart silently no-op. |
| **`claude mcp list` / `claude mcp test <name>` after every change** | Stops "looks installed but isn't" debugging spirals before they start. |
| **Test in dev first; promote to prod with stricter auth** | Don't grant prod creds during exploratory development. Saves at least one weekend per year. |

**Sources:**
- [modelcontextprotocol.io — Build an MCP server (official docs)](https://modelcontextprotocol.io/docs/develop/build-server) `[primary]`
- [Claude Code Docs — Connect Claude Code to tools via MCP](https://code.claude.com/docs/en/mcp) `[primary]`
- [The New Stack — MCP servers turn Claude into a reasoning engine for your data](https://thenewstack.io/build-mcp-server-tutorial/) `[analysis]`
- [TrueFoundry — How to Add an MCP Server to Claude Code (Step-by-Step Guide)](https://www.truefoundry.com/blog/how-to-add-an-mcp-server-to-claude-code) `[analysis]`
- [Codersera — Best MCP Servers for Claude Code (2026)](https://codersera.com/blog/best-mcp-servers-claude-code-cursor-2026/) `[analysis]`
- [Nimbalyst — Claude Code MCP Setup: A Practical 2026 Guide](https://nimbalyst.com/blog/claude-code-mcp-setup/) `[analysis]`
- [The Prompt Shelf — Claude Code MCP Servers: The Complete Setup Guide for 2026](https://thepromptshelf.dev/blog/claude-code-mcp-setup-guide/) `[analysis]`
- [TrueFoundry — MCP Authentication in Claude Code 2026 Guide](https://www.truefoundry.com/blog/mcp-authentication-in-claude-code) `[analysis]`
- [Generect — Ultimate Guide to Claude MCP Servers & Setup 2026](https://generect.com/blog/claude-mcp/) `[analysis]`

**Why it matters to you:**
- **Job lens:** Same as yesterday — **"I have a public MCP server with N installs"** is the single most legible 2026 AI-engineering portfolio artifact. Pin above your resume's projects section the day you publish.
- **Startup lens:** Same as yesterday — vertical MCP servers are a pre-seed-fundable wedge, and the public repo is the legible pre-pitch artifact.
- **Insight:** The 2-day collision of *cost-discipline* (Action #1) and *connector-layer ship* (Action #2) is not accidental. They're the **two skills MLEs will be hired against for the rest of 2026**: can you ship the connection layer competently *and* keep its inference cost in a defensible margin. Most engineers have *one* of those skills. Cultivating both — and demonstrating both in one weekend portfolio drop — moves you ahead of ~80% of the applicant pool.

---

## 3. Personal Finance With ChatGPT — What to Steal From the OpenAI Architecture {#3-chatgpt-finance-architecture}

Even if you never use ChatGPT Personal Finance yourself, the [OpenAI Plaid implementation](./01-big-lab-moves.md#3-chatgpt-finance) is a *reference design* for AI-with-real-money. Architectural takeaways worth absorbing this weekend:

| Decision | What OpenAI shipped | Why it matters for your own agent design |
|---|---|---|
| **Read-only on first ship** | Plaid can only fetch balances/transactions/investments/liabilities; ChatGPT cannot move money. | When introducing real-money agency, *one capability axis at a time*. Earn the trust before adding write. Mirror in any high-stakes agent of your own. |
| **Pro-tier only ($100/mo)** | Plus / Free are excluded at preview. | Heavy-trust features start on the highest-paying tier where the user has demonstrated commitment + you have margin to absorb support cost. Apply: don't ship your high-trust agent feature on a free tier. |
| **Third-party middleware (Plaid) for the regulated edge** | OpenAI didn't build its own bank-data interconnect; they ride Plaid's existing trust infrastructure. | Don't recreate regulated-domain plumbing. Compose. The same pattern applies to KYC, fraud, payment processing, ID verification. |
| **Explicit "what we can / can't see" disclosure** | OpenAI explicitly states: *"ChatGPT can only read balances, transactions, investments and liabilities. It cannot see full account numbers or make changes."* | Apply this disclosure pattern verbatim in your own products' security-context disclosures. Concrete language outperforms vague reassurances. |
| **Intuit integration as the *next* surface** | Tax / income optimization is the harder, higher-trust extension layered on top of transaction visibility. | Sequenced product surface — easier features earn the right to ship harder ones. Plan your roadmap the same way. |

**Sources:**
- [OpenAI — A new personal finance experience in ChatGPT](https://openai.com/index/personal-finance-chatgpt/) `[primary]`
- [TechCrunch — OpenAI launches ChatGPT for personal finance, will let you connect bank accounts](https://techcrunch.com/2026/05/15/openai-launches-chatgpt-for-personal-finance-will-let-you-connect-bank-accounts/) `[secondary]`
- [9to5Mac — OpenAI just released new personal finance features for ChatGPT customers](https://9to5mac.com/2026/05/15/openai-just-released-new-personal-finance-features-for-chatgpt-customers/) `[secondary]`
- [Plaid Developer Docs — OAuth Quickstart (reference)](https://plaid.com/docs/auth/coverage/oauth/) `[primary]`

**Why it matters to you:**
- **Job lens:** "I can read a frontier-lab product launch and extract the architectural decisions that apply to my own work" *is* a senior-engineer skill. Practice it on this launch over the weekend by writing a 200-word personal note answering: *if I were designing a similar agent in [your favorite domain], which of OpenAI's 5 decisions would I keep, which would I change, and why?* This is the same exercise senior MLEs do in their heads on every product announcement. Cultivate it now and you'll interview as one before you have the title.
- **Startup lens:** The same architectural pattern (read-only first / paid-tier first / 3P middleware / explicit disclosure / sequenced surface) maps onto *every* high-trust vertical agent you might build — legal, medical, fiduciary, HR, regulatory compliance. Use the table as a checklist when scoping any high-trust feature in your eventual product.
- **Insight:** The frontier labs *do not* publish their internal decision criteria for high-trust features. But every product launch leaks them by demonstration. Reading product launches as *architecture documents* — not as news — is one of the cheapest ways to learn senior product judgment in 2026.

---

## 4. Tactical Roundup — Field-Tested Practices, Week of May 11–16

| Practice | What it means | Why it works |
|---|---|---|
| **Run `claude --resume` instead of starting fresh sessions** | Keeps long-running task context across days when you switch machines | Reduces re-loading file context from ~3 min to 5 sec; saves tokens on the second/third pass |
| **Pre-write your CLAUDE.md cost rules** | Add a line like *"Default to Sonnet for code edits; route classification/extraction to Haiku; only escalate to Opus when explicitly asked"* | After June 15, this single project-level rule can cut your programmatic bill by 40–60% with no quality loss on most tasks |
| **Use `/clear` between unrelated tasks, not `Ctrl-C`** | Resets context cleanly; preserves session history | Stops the "earlier task contaminates current task" failure mode that gets worse as sessions grow |
| **Treat MCP tool descriptions as prompts, not docs** | Rewrite each tool's description until Claude picks it correctly 5/5 times on adversarial test prompts | Tool selection is the highest-leverage MCP-server quality knob you control |
| **Cache the system prompt explicitly** | In API calls, mark the stable system prompt section as `cache_control: ephemeral` | 50–90% input cost reduction on repeated calls; the single highest-ROI line of code you can add this month |
| **Add a 1-line eval to every PR** | Even a single test case prompt + expected behavior in `evals/<feature>.yaml` | Forces eval discipline early; the eval suite grows as your project does, rather than being added later (when it never is) |

**Sources:**
- [Karo Zieminski — Claude for Small Business Decision-Tree Workflows](https://karozieminski.substack.com/p/claude-for-small-business-decision-tree-workflows) `[analysis]`
- [Simon Willison's Weblog — May 2026 Claude notes](https://simonwillison.net/2026/May/) `[primary]`
- [Builder.io — How I use Claude Code (+ my best tips)](https://www.builder.io/blog/claude-code) `[analysis]`
- [Anthropic Docs — Prompt caching](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching) `[primary]`
- [Anthropic Docs — Claude Agent SDK](https://docs.claude.com/en/api/agent-sdk/overview) `[primary]`

**Apply it:** Pick the *one* row above where you're currently the weakest. Do that one thing today. The other five can wait.
