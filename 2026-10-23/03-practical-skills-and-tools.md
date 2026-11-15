# Practical Skills & Tools — 2026-10-23

Hands-on workflows, tools, prompting, productivity. Act on this today.

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.

---

## 1. The Claude Duet operating playbook — be the first with a public one <a id="1-duet-playbook"></a>

**Context.** Claude Duet (Oct 21) is a research preview on Opus 5.5 with 6,000+ connectors, background polling, Stripe-Link payments, and approval gates. **No comprehensive external operator guide exists yet** — the lab's own docs are intentionally minimal because it's a preview. You can be the first with a public playbook if you join the waitlist today and publish before Monday.

**The 5-section playbook template.**

### §1 — Connectors (what you add first, what you never add)
- **Add first:** calendar, email (read-only to start), one task tracker (Linear / Asana / Todoist), one payment surface (Stripe Link is the Anthropic default).
- **Add second (week 2):** CRM (HubSpot / Pipedrive), docs (Notion / Drive), accounting (QuickBooks).
- **Never add:** any single system that holds both credentials and the ability to spend money without a secondary gate. In practice: never give Duet an API key for your production AWS, bank login, or anything with a "transfer funds" button that bypasses Stripe Link's own approval.

### §2 — Approval policy (what Duet is allowed to auto-do, with what fallback)
- **Auto-OK:** reading, summarizing, drafting (never sending), creating draft calendar invites.
- **Approval required (default):** sending any message, making any payment, signing anything, deleting anything, adding anyone to a shared doc.
- **Manual-only (never auto, never approved by one tap):** anything that moves money above a dollar threshold you set, anything that creates a legally binding commitment, anything with government or healthcare.

### §3 — Observability (your weekly Duet audit)
- **Every Friday:** screenshot Duet's week-in-review (what it did, what it asked about, what it almost did).
- **Monthly:** export Duet's action log; cross-check against your calendar, inbox, and payment history for discrepancies.
- **One-pager template:** "This week Duet handled X items, asked for Y decisions, saved Z minutes. One near-miss: ___. One lesson: ___."

### §4 — Cost / limits (Duet runs on your plan's quota)
- Duet's background polling and cloud-compute **count against your 5-hour and weekly limits**. Newly admitted users get one full reset — use it as a baseline-measurement window.
- Compare Duet-on vs Duet-off weeks of your Claude usage. If Duet consumes >30% of your weekly cap and the audit value isn't matching, scale back polling frequency or disconnect low-value connectors.

### §5 — Known rough edges (so your readers know what to expect)
- Anthropic concedes **personal errands (ticket booking) are weak** — delegate work tasks first, consumer tasks later.
- **Microsoft 365 is not yet supported** at launch per some reporting; verify in your own setup.
- Not on Team or Enterprise yet.

**Sources.**
- [CNBC — Anthropic announces preview of Claude Duet (2026-10-21)](https://www.cnbc.com/2026/10/21/anthropic-preview-of-claude-duet-personal-ai-agent-take-on-muse-dots.html) `[secondary]`
- [TechCrunch — Claude Duet app is Anthropic's bet on agents (2026-10-22)](https://techcrunch.com/2026/10/22/claude-duet-app-is-anthropics-bet-on-agents/) `[secondary]`
- [AIWeekly — Claude Duet details](https://aiweekly.co/alerts/anthropic-opens-claude-duet-an-opus-55-agent-to-us-pro-and-max) `[aggregator]`

**Why it matters to you.**

- **Job.** The first public, searchable "Claude Duet operating playbook" ranks on Google for weeks. **Any recruiter searching "Claude Duet" during the next 60 days will find your gist first.** Zero cost, high visible craft, directly relevant to Anthropic Solutions / Integration Engineer roles.
- **Startup.** The playbook is also a **wedge for consulting-first revenue** — "I will set up Claude Duet properly for your professional-services firm, with approval policies and audit logs" is a $5–15K engagement that funds a product build.
- **Insight.** **Shipping the operating guide is the second-highest-leverage move after shipping the product itself**, and nobody at Anthropic has the time to do it in the preview window. Early-mover advantage on operating-content is massive and under-exploited.

**Tags:** `#duet #playbook #skills #approval #connectors`

---

## 2. MCP server hygiene — the frontier-lab consensus (2026 edition) <a id="2-mcp-hygiene"></a>

**Context.** The weekly MCP-related security + ops content has converged on a consistent set of practices. Here is the distillation — build this list into your `~/.claude/CLAUDE.md` or Claude Code project doc tonight.

**The 7 rules.**

1. **Only add an MCP server when it beats a Skill.** Skills are easier to inspect and version in a repo. MCP integrates with live data from other systems. Default to Skill; upgrade to MCP only when you need live state.
2. **Enable the server's read-only mode first.** For GitHub-MCP, Sentry-MCP, Linear-MCP, etc. — turn write off until you have a named workflow that needs it.
3. **Use `/permissions` to allowlist MCP tool calls per workflow.** Don't rely on the default "ask every time" prompt — you'll fatigue and start auto-approving. Allowlist only the tool calls that are known-safe within a repo.
4. **Enforce security through `settings.json` and hooks, not `CLAUDE.md`.** The agent can rewrite `CLAUDE.md` during a task; it cannot rewrite the hooks module without going through the hook permission flow.
5. **Watch context cost.** Heavy MCP tool definitions crowd out working context. Prefer narrow, custom servers over broad kitchen-sink ones. (Claude Code loads server definitions on demand, which helps, but the per-call tool spec still costs tokens.)
6. **Starter stack (consensus across guides):** Playwright for browser testing, Context7 for current library docs, Sentry for error context, Claude-in-Chrome for console-and-network debugging. Add project-specific ones only when a workflow asks for them.
7. **Audit which data each server can reach.** Who can query it? Can it take write actions? For every MCP server in the project, write a one-sentence "data access + write ability" summary in a `MCP.md` file next to `CLAUDE.md`.

**Sources.**
- [Anthropic — Claude Code Best Practices](https://www.anthropic.com/research/claude-code-best-practices) `[primary]`
- [Axify — 39 Claude Code Best Practices](https://axify.io/blog/claude-code-best-practices) `[analysis]`
- [GeneralAnalysis — Anthropic Claude Code Security Best Practices: Permissions, Hooks, MCP, Sandboxing, and CI/CD](https://generalanalysis.com/guides/anthropic-claude-code-security-best-practices) `[analysis]`
- [Claude Workshop — MCP best practices for teams](https://www.claudeworkshop.com/topics/mcp-team-skills) `[analysis]`
- [Builder.io — 50 Claude Code Tips and Best Practices](https://www.builder.io/blog/claude-code-tips-best-practices) `[analysis]`

**Why it matters to you.**

- **Job.** Interview answer that signals seniority: **"I separate stable rules (Skills) from live-data integrations (MCP), and I enforce MCP security through hooks, not CLAUDE.md."** This is specific, correct, and under-said.
- **Startup.** The **MCP-server-of-record for X vertical** opportunity is still open — most verticals have no mature MCP integration. Pick one (legal doc-review, healthcare prior-auth, construction submittals, hospitality PMS) and ship a reference MCP server + Skills bundle on your GitHub.
- **Insight.** MCP is now **a boring foundation**, not an advanced topic — which is good news for anyone who learned it early. The frontier of MCP is not "what can you connect" but "what can you connect safely with audit, revocation, and per-tool allowlisting."

**Tags:** `#mcp #claude-code #security #skills #hooks`

---

## 3. Intelligent UI as a prompting primitive — "ask ChatGPT to build you a tool" <a id="3-intelligent-ui-prompting"></a>

**Context.** GPT-6 Intelligent UI (Oct 7–8) lets you ask ChatGPT to **generate an interactive tool inside the conversation.** This is a brand-new prompt-engineering sub-discipline that almost nobody has 2 months of hands-on practice with. See [`01` §2](./01-big-lab-moves.md#2-gpt6-intelligent-ui).

**Working prompts to try tonight.**

**For yourself (job-search):**
- "Build me a résumé-skill mapper: a form where I paste a job description, paste my résumé, and get a highlighted overlap view + a 'missing skills' list."
- "Build me an interview prep flashcard with 10 common LLM-systems questions. Make the back of the card hidden until I tap."
- "Build me a cost calculator for my Claude Pro + Claude Code usage: inputs = tokens/day on Opus, Haiku, Sonnet; outputs = projected monthly spend + comparison vs Max tier."

**For your portfolio:**
- "Build me a small live demo of the router pattern from [this diagram]. Three model buttons; the user types a task; the UI picks the model and shows cost + response."
- "Build me a chart of 2026 AI model-release cadence by lab, as a tappable timeline."

**For blog posts / content:**
- "Build me a bike-vs-car-cost calculator for commute decisions in Los Angeles."
- "Build me a split-the-bill calculator with tip, tax, and per-person totals that I can show my roommates."

**The anti-patterns.**
- Don't ask for a tool when a text answer suffices — Intelligent UI is a tax on simple questions.
- Don't ask for a tool that depends on real-time external data — Intelligent UI tools don't fetch; they compute from inputs the user gives.
- Verify math. OpenAI itself concedes design judgment is weak; computational judgment can be too. **A beautiful calculator that computes the wrong formula is worse than a plain text answer.**

**Sources.**
- [TechRepublic — OpenAI Rolls Out GPT-6 Intelligent UI](https://www.techrepublic.com/article/news-gpt-6-intelligent-ui-charts-forms/) `[secondary]`
- [Yellow.com — ChatGPT's Intelligent UI Puts Charts And Calculators In Answers For 1.2B Users](https://yellow.com/news/chatgpt-intelligent-ui-charts-calculators-answers) `[analysis]`

**Why it matters to you.**

- **Job.** Spending one evening building 3 Intelligent UI tools gives you a **portfolio-ready artifact that didn't exist 3 weeks ago**. Share-link the three; drop them in your résumé. This is a one-of-few differentiator for an AI-adjacent SDE/MLE/AI-Engineer interview.
- **Startup.** The companies with **their own interactive content** (calculators, estimators, planners) built as marketing SEO plays are now **competing directly with ChatGPT**. Big implication for a startup you might build: if the SEO moat was "I rank for 'retirement calculator'" — that moat just evaporated. Build around proprietary data, not generic calculation.
- **Insight.** **ChatGPT just became a shadow dev environment for 1.2B people.** They can prompt their way to a mini-tool without writing code. The "learn to code because software is leverage" argument hasn't died, but **"software leverage" is now something you get in 30 seconds of prompting**, not 3 weeks of a bootcamp. The real skill is design judgment + prompt specificity, not syntax.

**Tags:** `#chatgpt #gpt-6 #intelligent-ui #generative-ui #portfolio`

---

## 4. Mistral Timestral — weekend forecasting-portfolio artifact <a id="4-timestral-weekend"></a>

**Context.** Mistral released **Timestral** (Oct 15) — four open time-series models (5M, 28M, 123M, 209M params), Apache-2.0 inference code, Hugging Face weights, 10–140 ms CPU inference, 32,768-step context, 21-quantile probabilistic outputs. **The first time-series foundation model you can run end-to-end on your laptop with no GPU budget.** See [`01` §4](./01-big-lab-moves.md#4-mistral).

**The weekend artifact: one notebook, one dataset, one chart.**

1. **Clone the inference repo** (Apache-2.0).
2. **Pick a dataset** — one of:
   - **M4 hourly** (standard forecasting benchmark; already pre-processed)
   - **Kaggle wiki-traffic** (interpretable + viral story)
   - **Your own Claude API spend history** (highest resume-value — "I used a 209M forecasting model to project my own LLM infra costs")
3. **Load the 209M checkpoint. Compute a 7-day-ahead forecast with 21-quantile bands.**
4. **Plot median + 10th/90th percentile band + actuals (if available).**
5. **Write 500 words:** (a) what the forecast captured, (b) what it missed and why, (c) how a 209M model compares to a classic ARIMA / Prophet baseline on the same data (one line of each, same chart).
6. **Verify the license file.** One source calls Timestral "Modified MIT with enterprise approval"; another calls it fully open. **Check the Hugging Face license file before quoting it as "open."**
7. **Publish on GitHub + a 2-tweet writeup.**

**Why this is the right portfolio piece this weekend.**
- Nobody has published a Timestral demo yet (model was released 8 days ago).
- CPU-only means you don't need a GPU budget or cloud credits.
- The forecasting lane is one of the **least-crowded corners of the AI job market** right now — most CS grads optimize for LLMs; the forecasting + probabilistic-ML lane has markedly higher comp-adjusted-for-competition.
- A notebook + 500-word writeup is an **8-hour build** at most; it fits in a weekend.

**Sources.**
- [AIWeekly — Mistral Opens Timestral](https://aiweekly.co/alerts/mistral-opens-timestral-209m-time-series-model-beating-timesfm-3) `[aggregator]`
- [LLM Reference — Timestral](https://www.llmreference.com/model-family/timestral) `[aggregator]`
- [StartupHub.ai — Mistral says 209M Timestral leads on three benchmarks](https://www.startuphub.ai/ai-news/ai-research/2026/mistral-says-209m-timestral-leads-on-three-benchmarks) `[secondary]`
- [Remio AI — Timestral deep dive](https://www.remio.ai/post/timestral-mistral-release-time-series-foundation-models-that-challenge-bigger-ri) `[analysis]`

**Why it matters to you.**

- **Job.** "I shipped a Timestral forecasting demo the week after Mistral released it" is the kind of concrete, dated, verifiable signal interviewers at MLE / applied-research roles are starved for. Doubly so if the forecast is of your own LLM spend — it folds **three** of your lanes together (ops instinct + forecasting + AI-cost awareness).
- **Startup.** Timestral + a vertical dataset is a **pre-product-market-fit MVP** for any demand-planning / inventory-prediction / small-business-forecasting startup. The forecasting-SaaS category has had the same tooling since 2019; a foundation model you can run on a CPU is genuinely new.
- **Insight.** **Open-weights frontier releases keep getting more specific** — Mistral Large 4 is "general," Timestral is "time series only," Voxtral 3 is "audio only." The one-model-one-job trend keeps intensifying. Hunt down the Mistral Hugging Face page every two weeks; it's a leading indicator for the "narrow foundation model" lane that's still under-reported.

**Tags:** `#mistral #timestral #forecasting #portfolio #weekend #open-weights`

---

## 5. Keeping Claude Code sharp — the no-regret settings for Q4 2026

**Context.** Claude Code shipped Haiku 5.5 as the default (v2.1.293, Oct 7). This has implications for Pro / Max users who haven't reconfigured since.

**Four settings worth checking tonight.**

1. **Default model.** Haiku 5.5 (`claude-haiku-5-5`) is the default worker. Opus 5.5 is the escalation. **Verify your `~/.claude/settings.json` doesn't still pin `claude-opus-4-7`** — that's a 2–5× cost increase for a 1-year-old model.
2. **Effort level.** Haiku 5.5 added **configurable effort levels** — "low/medium/high" trade token spend for capability per call. Set `effort` to `low` by default; override in-session for hard tasks. This can save 30–50% of weekly tokens on routine code edits.
3. **Permissions allowlist.** Run `/permissions` and check what MCP tool calls are already allowlisted. Prune anything you don't recognize; add anything you approve 3+ times/week.
4. **Hooks.** If you don't have a `PreToolUse` hook that logs significant file writes outside the repo, add one. Takes 10 minutes; it will catch at least one surprise action in the next 30 days.

**Why it matters to you.**

- **Job.** The effort-level dial is the single most important new concept to learn about Claude Code for Q4 2026 — effort-level routing is now a design decision in production LLM apps.
- **Startup.** The **"effort-level router" opportunity** — a thin SDK that picks the right effort level for a given prompt, like a Claude-specific version of the model-router from last edition — is a 2-weekend build and genuine value.
- **Insight.** "Which model" has been quietly deprecated as a question; it's now "which effort level on which model." The abstraction keeps shifting one layer up.

**Sources.**
- [Anthropic — Claude Code What's New](https://code.claude.com/docs/en/whats-new) `[primary]`
- [2026-10-14 §3](../2026-10-14/01-big-lab-moves.md#3-cyber-mission) and [2026-10-14 §1 Haiku 5.5](../2026-10-14/03-practical-skills-and-tools.md#1-haiku-55) for the full effort-level context.

**Tags:** `#claude-code #haiku-5-5 #effort-levels #settings`
