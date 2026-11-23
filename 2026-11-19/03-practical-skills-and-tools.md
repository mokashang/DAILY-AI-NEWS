# Practical Skills & Tools — 2026-11-19

Quiet-week on the framework side (no LangChain / LlamaIndex / Pydantic AI / Instructor release in the window; no Simon Willison `llm` bump past 0.37), but two deadlines that matter: **Claude Code 2.1.325 / 2.1.326 flipped the default start mode to Code Mode**, and **Opus 4.8 fast-mode will hard-error on Nov 30** — your one immovable migration deadline this month. On the eval side, **GDPval-AA v2.1** is now the leaderboard to cite in cover letters (**Claude Opus 5.5 Max #1 at 1866**), **GAIA appears compromised** (a single audit agent scored ~98% via exploit — quietly drop GAIA from your résumé), and **PIPETTE (arXiv 2611.24362)** is a ready-made prompt-injection purple-teaming harness you can wrap around any MCP server as a portfolio evidence artifact.

Tags: `#claude-code #opus-4-8 #breaking-change #gdpval #evals #prompt-injection #mcp #resume-copy`

---

## 1. Claude Code 2.1.325 / 2.1.326 — Code Mode is the new default {#1-claude-code-code-mode}

**What's new:**
- Trackers report **"agent teams now start in Code Mode automatically"** as the headline substantive change in **2.1.325 (Nov 13) / 2.1.326 (~Nov 16)**.
- The default shifts from "chat first, tools second" to **"tool-plan first, chat as fallback"** — matches the agentic-engineering frame from Karpathy / Willison.
- Prior November context: **2.1.316** added `CLAUDE_CODE_SUBAGENT_EFFORT` env var; **2.1.317** added gateway cost reporting + Agent SDK hard-block-on-failure hooks; **2.1.318** added claude.ai sign-in-expiry early warnings.

**Sources:**
- [Havoptic — 2.1.326 release notes](https://www.havoptic.com/r/claude-code-2.1.326) `[aggregator]`
- [claude-world — November 2026 Claude Code roundup](https://claude-world.com/articles/claude-code-november-2026-whats-new/) `[aggregator]`

### How to actually use it this week

1. **Update your `.claude/CLAUDE.md`** to reflect Code Mode as default: add a top-section instruction like *"Operate in Code Mode by default; use chat only for clarification or explanation."*
2. **Add a `.claude/hooks/pre-tool-use.sh`** gate that logs tool calls to `.claude/logs/` — cheap observability for the Code Mode default.
3. **Rename** any portfolio README references from "LLM-powered" or "vibe-coded" to **"agentic engineering"** (per §5).

### Why it matters to you

- **Job lens:** Hiring managers at Anthropic / Glean / Distyl this month expect the **"agentic engineering" vocabulary** — hooks, skills, subagents, MCP servers as named primitives. If your résumé still says "prompt engineering" or "LLM-powered app," rewrite it tonight.
- **Startup lens:** Code Mode as default means **every Claude Code demo at your next investor meeting will skip past chat-ui theater** and go straight to tool execution. Update your demos accordingly — the "wow" moment is now the tool trace, not the chat.
- **Insight:** **Default start-mode is a hiring-vocabulary signal.** When Anthropic defaults the agent to Code Mode, it's telling the market: **your product is a tool-use system first, a chat interface second**. Everyone copying Anthropic's product shape (Glean, Distyl, Decagon, Sierra) will follow within 60 days.

---

## 2. Opus 4.8 fast-mode sunsets Nov 30 — ship your migration this week {#2-opus-48-sunset}

**What's happening:**
- **Opus 4.8 fast-mode is deprecated** — scheduled removal **Nov 30, 2026**.
- After cutoff, `opus-4.8-fast` requests will **hard-error, not fall back** to the base model.
- Deprecation was quietly announced in **2.1.316 release notes**.

**Sources:**
- [claude-world — Claude Code November 2026 roundup](https://claude-world.com/articles/claude-code-november-2026-whats-new/) `[aggregator]`

### Migration decision tree

```
If your workload uses `opus-4.8-fast`:
  ├── Latency-sensitive + budget-sensitive? → Fable 5.2 (faster + newer + priced at $8/$40 per M)
  ├── Latency-sensitive + accuracy-first?    → Opus 5.5 w/ effort="low" (Haiku-tier latency, Opus reasoning)
  └── Not latency-sensitive?                 → opus-4.8-base (works post-cutoff; more expensive)
```

**Write a one-paragraph migration doc in your README** that says which path you took and why. That doc is cover-letter evidence of "ships through breaking changes" — Anthropic hiring managers explicitly read for it.

### Why it matters to you

- **Job lens:** **Shipping through a breaking change in a public repo is now the highest-density FDE résumé artifact of November** — cheaper than building an MCP server from scratch, and it shows you keep production systems alive. Add it to your "evidence of maturity" bucket.
- **Startup lens:** If you built anything that routes to `opus-4.8-fast` under the hood, verify your **routing fallbacks** and **error logs** before Nov 30. A silent cutoff in a demo environment is a founder-level embarrassment.
- **Insight:** **Public-company Anthropic will be more disciplined about deprecations.** Expect one breaking-change cycle per quarter, called out with 2-week minimum notice. Build the migration muscle now while the stakes are low.

---

## 3. GDPval-AA v2.1 is the leaderboard to cite — GAIA appears compromised {#3-gdpval-aa}

**What happened:**
- **GDPval-AA v2.1** (Artificial Analysis, built on OpenAI's GDPval, 44 occupations / 9 industries): **Claude Opus 5.5 Max #1 at 1866**, ahead of **Kimi K3.1 Pro + Meta Muse Wonder Full (Max)**.
- **BenchLeader** (meta-aggregator) tracks **256 benchmarks from 47 publishers** (vs 255/46 on Nov 9). Gemini 4 Carbon (High) now leads **HLE-Diamond** at **69.1%**.
- **GAIA appears compromised** — one audit agent scored **~98% via exploit** in Nov tracking. GAIA has quietly ceased being a usable ranking benchmark.

**Sources:**
- [Artificial Analysis — GDPval-AA](https://artificialanalysis.ai/evaluations/gdpval-aa) `[primary]`
- [BenchLeader — 255 benchmarks snapshot (Nov 13)](https://agentmarketcap.ai/blog/2026/11/13/benchleader-255-benchmarks-gemini-4-carbon-hle-diamond) `[analysis]`

### What to do with it this week

- **Delete GAIA citations** from any public repo README / portfolio / LinkedIn post. Replace with GDPval-AA or BenchLM.
- **Write one cover-letter sentence** that cites GDPval-AA by name when applying to applied-AI / FDE roles — it's the leaderboard that maps to "does this agent actually do a work task," which is what customers of FDE teams care about.
- **Add a BenchLeader link** to your portfolio footer as your "I watch the meta-benchmark landscape" signal.

### Why it matters to you

- **Job lens:** GDPval-AA citations are **this quarter's version of citing Terminal-Bench in cover letters** — the hiring-manager vocabulary turns over faster than résumé updates. Rotate yours.
- **Startup lens:** If you're pitching an agentic-product wedge, **GDPval-AA by occupation and industry is your TAM-defense slide**. Pull the occupation-level scores for the one profession you serve; show the gap between frontier and your own fine-tune.
- **Insight:** **Benchmarks become unusable within weeks of becoming popular** — GAIA's compromise is the second benchmark in six months to collapse to an exploit. Design your own evals around your product; cite public benchmarks but don't trust them to differentiate.

---

## 4. PIPETTE: prompt-injection purple-teaming harness (arXiv 2611.24362) {#4-pipette}

**What it is:**
- **PIPETTE** — a **purple-team framework for prompt injection on LLM agents**, published to arXiv this week (2611.24362).
- Combines **red-team adversarial inputs + blue-team detection** on a single evaluation substrate; benchmarks across agent configurations and MCP tool-call paths.
- Ready to wrap around an existing agent or MCP server as an eval suite.

**Sources:**
- [arXiv 2611.24362 — PIPETTE](https://arxiv.org/abs/2611.24362) `[primary]`

### How to use it as portfolio evidence

1. **Fork PIPETTE** (assuming open-source release — check the paper's repo link).
2. **Wrap it around your public MCP server** (the one you built for the Nov 14 edition's FDE portfolio).
3. **Publish one failure trace** with a fix PR. That's an FDE-grade security demonstration.
4. **Cite PIPETTE** in your README as your prompt-injection methodology.

### Why it matters to you

- **Job lens:** **Security-aware agent engineers get paid 20–40% more than agent engineers who don't ship security eval**. FDE roles at frontier labs now screen for "has thought about prompt injection in production" — PIPETTE is the quickest way to prove that without a security research role.
- **Startup lens:** If you're building an agent that handles user data or external tool calls, **running PIPETTE monthly is your 2026 version of running SOC 2 audits**. Customers at Anthropic / Glean / Harvey will ask.
- **Insight:** **Prompt injection is the one agent-safety topic that has moved from research-paper abstraction to procurement-checklist mandate in 2026.** Get in front of it.

---

## 5. Language shift: "agentic engineering," not "vibe coding" {#5-agentic-engineering}

**What's happening:**
- Karpathy's **"vibe coding → agentic engineering"** evolution (from April–May 2026) is now the vocabulary consensus among hiring managers, blog writers, and Anthropic / Glean / Distyl job postings.
- Willison's **"vibe engineering"** post (Oct 2025) frames the ceiling-raising discipline that complements vibe-coding's floor-raising ease-of-use.

**Sources:**
- [Simon Willison — Vibe engineering](https://simonwillison.net/2025/Oct/7/vibe-engineering/) `[primary]`
- [signals.aktagon — Karpathy's agentic-engineering frame](https://signals.aktagon.com/articles/2026/05/from-vibe-coding-to-agentic-engineering-andrej-karpathy-on-the-evolution-of-ai-assisted-programming/) `[secondary]`

### Why it matters to you

- **Job lens:** **Your résumé / LinkedIn / portfolio bios should say "agentic engineering" or "vibe engineering" — not "vibe coding"** when describing work you own. Vibe coding is a floor-raising practice; agentic engineering is the ceiling-raising discipline hiring managers pay for.
- **Startup lens:** If you're pitching "we use AI to build faster," spell it as **"agentic engineering"** on slide 1 of your deck. Investors have heard "vibe coding" too many times to find it credible.
- **Insight:** **Hiring-manager vocabulary turns over every 3–6 months in AI** — "prompt engineering" → "LLM-powered app" → "agent framework" → "agentic engineering." The next one will be "agentic systems" or "agent-ops"; watch Willison's and Karpathy's blogs for it first.

---

## 6. The ship-this-weekend artifact {#6-ship-artifact}

Given that this is a Thursday edition and the weekend is one day away, here's a **two-hour build** that captures 3 of this week's threads at once:

**"Opus 4.8 Migration Playbook (with PIPETTE eval)"** — a public GitHub repo containing:

1. **A `/migrations/opus-4.8-sunset/` directory** with:
   - A one-paragraph decision-tree doc (from §2).
   - A 20-line script that greps a codebase for `opus-4.8-fast` references.
   - A `before.yaml` and `after.yaml` showing what you changed.
2. **A `/evals/pipette-harness/` directory** with:
   - PIPETTE wrapped around one MCP tool call.
   - One documented failure trace + fix PR link.
3. **A README** that:
   - Cites GDPval-AA v2.1 (not GAIA).
   - Says "agentic engineering" (not "vibe coding").
   - Links to this week's §1 as your source of the breaking-change deadline.

Post it tonight. It touches the four most hireable vocabularies of the month in one artifact: **breaking-change discipline, PIPETTE/security-eval, GDPval-AA citation, agentic-engineering frame**.

Cross-link: [`05` §1 — ANT Day 1 actions](./05-career-and-startup.md#1-ant-day-one) · [`05` §2 — FDE census pivot](./05-career-and-startup.md#2-fde-census)
