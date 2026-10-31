# Practical Skills & Tools — 2026-09-30

Three things to actually build or read tonight. All are 30–90 minutes; all sit on this week's news; each produces a public artifact by Sunday. The frame: **your peers are going to spend the week arguing about Opus 5.5 vs Sol on Twitter. You are going to ship the router, publish the S-1 post, and re-run your cost dashboard on Sonnet 5.5.** That is a full one-week career acceleration for ~4 hours of work.

Tags: `#claude-code #hooks #skills #subagents #mcp #pricing #cost #routing #s-1 #artifact`

---

## 1. Sonnet 5.5 economics — the free ~30% cost cut waiting in your existing code {#1-sonnet-55-economics}

**What happened:** Claude Sonnet 5.5 (Sept 28) ships at the **same $2/$10 per 1M in/out list price** as Sonnet 5 — but multiple sources (Anthropic's own product page, TechCrunch, SiliconANGLE) report **30%+ faster completion** and, more importantly, **meaningfully fewer steps, tokens, and tool calls on multi-step agent workloads** — a "behavior-price cut" rather than a list-price cut.

**Concrete cost model (per-agent, illustrative):**

| Regime | Model | Steps per task | Tokens per step | Cost per task (rough) |
|---|---|---|---|---|
| Baseline | Sonnet 5 | 12 | ~2,000 in / ~500 out | ~$0.014 |
| Sept-30 default | Sonnet 5.5 | 9 (–25%) | ~1,800 in / ~450 out (–~10%) | **~$0.009 (–~36%)** |

For an agent running 10,000 tasks/day, that's ~$50/day → ~$18K/yr savings **for no code change** (assuming caching stays constant; more if cache hits improve).

**Action:**

1. Point one of your existing Sonnet-5 agent projects at Sonnet 5.5 today.
2. Rerun a 100-task representative benchmark.
3. Log: **tokens/task, steps/task, cost/task, wall-clock/task, task success rate.**
4. Post the delta table (three numbers × two models = six cells) to your GitHub repo README **as a diff.**

Total time: ~90 minutes. Output: a public artifact showing you (a) knew the release happened within 48 hours and (b) can quantify a business-relevant delta. That is a top-decile signal in the FDE/AI-Eng interview funnel.

**Sources (as [`01` §4](./01-big-lab-moves.md#4-sonnet-55)):**
- [Anthropic — Introducing Claude Sonnet 5.5](https://www.anthropic.com/claude-sonnet-5-5) `[primary]`
- [TechCrunch — Anthropic releases Sonnet 5.5, which it calls a significantly cheaper, faster work partner](https://techcrunch.com/2026/09/28/anthropic-releases-sonnet-5-5-which-it-calls-a-significantly-cheaper-faster-work-partner/) `[secondary]`
- [SiliconANGLE — Anthropic debuts Claude Sonnet 5.5 running 30% faster](https://siliconangle.com/2026/09/28/anthropic-debuts-claude-sonnet-5-5-running-30-faster-than-the-previous-generation-ai-model/) `[secondary]`
- [GitHub Changelog — Claude Sonnet 5.5 in GitHub Copilot](https://github.blog/changelog/2026-09-28-claude-sonnet-5-5-in-github-copilot/) `[primary]`

### Why it matters to you

- **Job lens:** The single fastest way to look "AI-native in 2026" is to publish **model-diff cost analyses** the week a new model ships. Sonnet 5.5 is the free entry-ticket to this cadence — no new code, real numbers. Do this every Sonnet / Opus / GPT-6 tier release and you have a **six-artifact portfolio by Christmas** that reads like a full-time AI-Engineer's dashboard.
- **Insight:** Behavior-price cuts (fewer steps) compound differently than list-price cuts (lower $/token). If you had already optimized your agent's step count, list-price cuts hit you harder. If you were leaving steps on the table, behavior-price cuts hit you harder. **The "who benefits more" delta is now a diagnostic on your own optimization state.** Run it.

---

## 2. The 2026 Claude Code primitive map — updated for the Sept skills-pack pattern {#2-primitive-map}

**What happened:** The 2026 Claude Code best-practice consensus has matured further this month. Guides published mid-to-late September (Firecrawl "14 Best Claude Code Skills for Developers"; OkhlopkovOK's "My Claude Code Setup After 4 Months of Daily Use"; SmartScope's "Advanced Best Practices"; MCP.directory) all converge on the same **four-primitive map** we've been building toward since spring:

| Concern | Primitive | Why this one |
|---|---|---|
| **Enforcement — rules that MUST fire every time** | **Hooks** (PreToolUse/PostToolUse/UserPromptSubmit) | Runs deterministically outside the model loop; the only guardrail the model can't skip |
| **Contextual knowledge — instructions loaded on-demand** | **Skills** (folder-based, `SKILL.md` + optional scripts) | Agent loads them by inspecting the folder; scales past what fits in CLAUDE.md |
| **Delegation boundary — separate context or specialization** | **Subagents** | New context, task-scoped tool access, clean handoff |
| **Always-on project guidance — stable rules everyone reads** | **CLAUDE.md** | Read first, kept short; the "constitution" of the repo |
| **External tool access — data + APIs you don't want to embed** | **MCP** (`claude mcp add --transport http ...`) | Standard protocol; add one server at a time; prove context-switch removal before adding more |

**The Sept-2026 delta from the May version:**

- **`Skills` is now the primary way to hold procedural knowledge** — the "on-demand instruction pack" pattern beats CLAUDE.md for anything longer than ~20 lines. Move procedures into `.claude/skills/<name>/SKILL.md` files this weekend.
- **The permission mode has hardened** — most guides now recommend running in **plan mode by default** with hooks catching mistakes before disk writes, rather than free-run with prompt-based safety.
- **MCP-server minimalism has become a first-order style choice.** Add one at a time; if it doesn't remove a real context switch, delete it.

**Sources:**
- [Firecrawl — 14 Best Claude Code Skills for Developers in 2026 (Sept 2026)](https://www.firecrawl.dev/blog/best-claude-code-skills) `[analysis]`
- [okhlopkov.com — My Claude Code Setup After 4 Months of Daily Use (2026)](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) `[analysis]`
- [SmartScope — Claude Code Advanced Best Practices: 11 Practical Techniques for Hooks, Subagents & Context Management (2026)](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[analysis]`
- [MCP.directory — Claude Code Best Practices: From Vibe Coding to Agentic Engineering (2026)](https://mcp.directory/blog/claude-code-best-practices) `[analysis]`
- [MarkTechPost — Claude Code Guide 2026: 25 Features with Examples](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[analysis]`
- [Totalum Blog — Claude Code Skills in 2026: The Complete Guide (vs Hooks, vs Subagents, vs MCP)](https://www.totalum.app/blog/claude-code-skills-totalum) `[analysis]`
- [Blake Crosley — Claude Code CLI: The Complete Guide — Hooks, MCP, Skills](https://blakecrosley.com/guides/claude-code) `[analysis]`
- [GitHub — MuhammadUsmanGM/claude-code-best-practices (wiki)](https://github.com/muhammadusmangm/claude-code-best-practices) `[analysis]`
- [GitHub — shanraisshan/claude-code-best-practice](https://github.com/shanraisshan/claude-code-best-practice) `[analysis]`

### Concrete migration — the weekend rewrite

Pick one existing project. In one 3-hour block:

1. **Extract every "always follow rule X" line from your prompts into a Hook.** If it fires as a shell command, it's a hook.
2. **Move every "here's how we do multi-step task Y" chunk into `.claude/skills/y/SKILL.md`.** One file per procedure.
3. **Shorten CLAUDE.md to <60 lines** — only stable rules, never how-tos.
4. **Add exactly one MCP server** for a tool your project actually uses (calendar, DB, docs). If you can't name the context-switch it removes, don't add it yet.
5. **Push it.** Public repo. `README` explains the four-primitive rationale in five bullets.

**That repo becomes your Claude-Code-fluency artifact** — recruiters and hiring managers who use Claude Code themselves will recognize the layout in 20 seconds.

### Why it matters to you

- **Job lens:** Every AI-Engineer / FDE hiring loop in Q4 2026 now includes "walk me through a Claude Code / agent setup you've built." The four-primitive answer is the *current* answer. Rebuild your repo tonight and you get 60 days of interview-ready ammunition.
- **Insight:** The maturity of the primitive map — one primitive per concern, no overlap — is the first sign that Claude Code has hit "framework-shape" rather than "wrapper-shape." When the abstractions stabilize this cleanly, the layer below (multi-agent orchestrators, agent build systems) will start to consolidate too. Watch for the "build system for agents" category to have a name-brand player before EOY 2026.

→ Cross-link: [`02` §1 Ema (workflow-first) → also uses agent-primitive discipline](./02-new-emerging.md#1-ema-b) · [2026-09-10/03 §2 the earlier version of the decision tree](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree).

---

## 3. Tonight's artifact — the 200-word Anthropic S-1 post {#3-s1-post}

**What happened:** The Anthropic S-1 leak on Sept 28 ([`01` §1](./01-big-lab-moves.md#1-anthropic-s1)) is **the single highest-leverage interview-prep primary source of Q4 2026** — and 90% of your applicant-pool peers won't have read it.

**The artifact spec** (45 minutes, LinkedIn or personal blog):

- **Headline:** "*Reading Anthropic's leaked S-1 risk section: what enterprise buyers should actually be asking.*"
- **Body (200 words):**
  1. **Fact 1:** Anthropic filed its S-1 confidentially with the SEC on June 1, 2026; the draft leaked Sept 28. Revenue $4.6B, loss $42B, 1,088% YoY growth. Nasdaq listing shifted from Oct to Nov 2026 per WSJ.
  2. **Fact 2:** Quote **one specific disclosure line** from Fortune's coverage — pick from: "resist shutdown" / "conceal or manipulate information" / "resembling blackmail."
  3. **Your read (three sentences):** Enterprise buyers should update their AI procurement checklists to reference the S-1's own risk categories, because a lab that discloses X in a filing is legally *saying* their tests can produce X, and no vendor-signed MSA saying "our model would never do X" outranks the vendor's own SEC filing.
  4. **What you'd do next:** Publish a template Q&A your team would run against any frontier-lab vendor, keyed to the S-1 disclosure categories.
- **CTA:** *"DM me if you want the Q&A template — I'll send it, no gate."* (You'll draft it later this week; the ask itself is your outreach engine.)

**Why the S-1 post works better than the router repo this week:**

- The router repo is content-fit for AI-Engineers who read code.
- The S-1 post is content-fit for hiring managers, VPs Engineering, VP Product, and *specifically* Solutions/FDE recruiters at frontier labs — who read prose and don't have time to open your GitHub.
- The router repo takes ~4 hours to build. The S-1 post takes ~45 minutes to write.

**Sources:**
- [TechCrunch — Anthropic's prospectus details losses, growth, and, yes, a warning that its AI could end humanity](https://techcrunch.com/2026/09/28/anthropics-prospectus-details-losses-growth-and-yes-a-warning-that-its-ai-could-end-humanity/) `[secondary]`
- [Fortune — Anthropic's IPO filing details steep losses, rapid growth, and a fear that AI could end humanity](https://fortune.com/2026/09/29/anthropic-leaked-ipo-prospectus-losses-growth-ai-end-humanity/) `[secondary]`
- [Financial Samurai — IPO Quiet Period Explained](https://www.financialsamurai.com/ipo-quiet-period/) `[analysis]` (context: what Anthropic can and cannot say once the filing is public)

### Why it matters to you

- **Job lens:** The S-1 post is **content marketing for yourself.** Recruiter DMs from Anthropic Solutions, OpenAI Trust & Safety, and enterprise-AI GTM roles are the direct read on it. Cost: 45 minutes. Realistic outcome: 3–10 DMs in 10 days.
- **Startup lens:** The Q&A template (the "DM me" hook) is a **founder-artifact seed** — if you develop it into a real 20-question enterprise-procurement checklist keyed to S-1 language, you have the seed of a **security-review / vendor-assessment SaaS** wedge for AI. This is not speculative; every F500 GC will need this by mid-2027.
- **Insight:** The **"read the primary source, translate it for a specific reader"** pattern is a durable career move for the next 5 years of AI news. Anthropic's S-1 is the first genuinely deep primary source; OpenAI's Q4 S-1 will be the second; xAI + Mistral + DeepSeek eventual filings will follow. **Own this pattern and you never run out of high-leverage posts.**

→ Cross-link: [`01` §1 the S-1 leak](./01-big-lab-moves.md#1-anthropic-s1) · [`05` §2 the skill re-price](./05-career-and-startup.md#2-reprice).

---

## 4. Adjacent quick wins — 30 minutes each {#4-quick-wins}

For the days when 90 minutes isn't there:

- **Add a `.claude/skills/router/SKILL.md`** to your last agent project. Put the 5-line routing rule from your Sept-10 router artifact into it. Pushes the "skills-pack" pattern onto muscle memory.
- **Update your LinkedIn skills line.** Add: **"cache-aware agent design", "S-1 primary-source analysis", "model routing", "eval design", "MCP", "Claude Skills", "cost-per-task dashboards".** Remove any 2024-era buzzwords ("prompt engineering", "vector DB tuning", "LangChain").
- **Fork one of the September best-practice repos** ([Muhammad Usman](https://github.com/muhammadusmangm/claude-code-best-practices) or [Shanraisshan](https://github.com/shanraisshan/claude-code-best-practice)) and star-diff one section of the CLAUDE.md template against your own. **Force yourself to write down what you disagree with**; that's the top of your next blog post.
- **Watch the docket:** Apple Inc. v. Liu, 5:26-cv-07078 on [CourtListener](https://www.courtlistener.com/docket/73602437/apple-inc-v-liu/) tomorrow morning. Screenshot the order once it hits; that's your Thursday LinkedIn post.
