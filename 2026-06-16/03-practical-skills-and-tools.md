# Practical Skills & Tools — 2026-06-16

This file is the operational baseline for **the metered-Claude regime**. As of yesterday ([`01` §1](./01-big-lab-moves.md#1-metering-day-1)) every programmatic Claude workload is on a separate credit pool at full API list rates with no rollover, and the original Claude 4 model IDs are gone from the API. The first section is the **meter-aware starter kit** you should deploy *today*, not Friday. Then: the **OpenAI Codex-in-ChatGPT** integration that quietly shipped while everyone watched the Anthropic deadline (June 2). Then the practical reads of **iOS 27 Extensions** and **Fable 5** that translate into "what do I do tonight."

Tags: `#claude-code #cost #subagents #cache #codex #chatgpt #ios27 #fable-5 #orchestration`

---

## 1. The meter-aware Claude Code starter kit (deploy tonight) {#1-meter-aware-starter}

**What to do (90 minutes, ships today):** every Claude project you maintain needs the same six pieces by end of week. Stack them in this order — each builds on the previous one.

### 1.1 Audit the API model IDs in production right now

The retirement of `claude-sonnet-4-20250514` and `claude-opus-4-20250514` (per [Make.com deprecation notice](https://help.make.com/anthropic-claude-model-deprecations-on-june-15-2026)) silently broke any code pinning those IDs as of June 15. Run:

```bash
grep -rn "claude-sonnet-4-20250514\|claude-opus-4-20250514" .
```

across every active project. **Replace with the closest live equivalent**, preferring Fable 5 + Sonnet 4.7+ unless you have a calibration reason.

### 1.2 Toggle the Agent SDK credit pool

If you missed [2026-05-18/03 §1](../2026-05-18/03-practical-skills-and-tools.md#1-agent-sdk-toggle): the Agent SDK separate credit is not automatic. Go to your Claude account settings, **enable the Agent SDK / programmatic credit**. Skipping this means programmatic calls go to your *interactive* subscription pool and get blocked when it depletes, instead of metering against the agent pool.

### 1.3 Enable prompt caching on every project >5K input tokens

From [2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md): set `cache_control` on your stable system prompt + on your tool definitions. **Confirm caching is working** by checking that the response includes `cache_read_input_tokens > 0` on the second-and-later turn. Typical savings: **60–90% input cost reduction.** Under metering economics, this single change moves you from "burning credits in a week" to "credits last the month."

### 1.4 Deploy the Opus-orchestrator / Sonnet-worker split

From [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost): **Opus runs the planner**, Sonnet workers run the executions. Empirically ~40% cheaper than all-Opus, with the plan→annotate→"address all notes, don't implement yet" reliability loop. Under the new metering economics this stops being "a clever trick" and becomes the *baseline pattern* — anyone running all-Opus through the SDK is overpaying by ~40% as of yesterday.

Add Fable 5 to the orchestrator slot for any project that *needs* the gap-widens-on-long-tasks property ([`01` §3](./01-big-lab-moves.md#3-fable-5)); keep Opus 4.8 / Sonnet 4.7 for shorter-task projects where Fable 5's premium isn't justified.

### 1.5 Add per-step cost trace as a first-class artifact

Every agent run should emit a row per LLM call: `{step_id, model, input_tokens, cached_tokens, output_tokens, cost_usd, latency_ms}`. Two reasons:

1. **Operational:** you can answer "which step burned the credit pool" in seconds, not minutes.
2. **Portfolio:** the trace becomes the artifact you attach to a "what I changed June 15" LinkedIn post. **Anyone hiring a Solutions / FDE / Integration role wants to see exactly this trace.**

### 1.6 Add Gemini 3.5 Flash as the cheap-tier leg of a 3-provider router

From [2026-05-20/03 §4](../2026-05-20/03-practical-skills-and-tools.md#4-cost-routing). Flash at $1.50/$9 is the price floor; route the cheapest task class (classification, summarization, simple extraction) to Flash. Re-route only on quality regression flagged by the trace. **The router is now the artifact, not the agent.**

### Why this matters

- **Job lens:** This single starter kit answers the entire FDE / Integration-Engineer interview surface. The day after the metering deadline, every customer conversation is some version of *"my bill 5×'d, fix it."* The six pieces above are the triage playbook, deployable in 90 minutes per customer. Ship the kit *as a public repo* with a README that says "what I changed on June 15" and link it from your resume — **the date stamps the artifact**.
- **Startup lens:** Bundle the starter kit as a free open-source `claude-cost-guardrail` package + a paid Pro SaaS that adds policy enforcement (budget caps, model whitelists, role-based routing rules). The **wedge is "the first 100 enterprises that get their Claude bill under control this quarter"**. Distribution: post-mortem the metering shock on Hacker News + LinkedIn this week while it's the hottest dev topic, drive sign-ups from the install base of programmatic-Claude users.
- **Insight:** Notice the symmetry between the starter kit and the funded picks-and-shovels ([`02` §2](./02-new-emerging.md#2-identity-and-compute)): **NewCore prices the identity layer, Hydra Host prices the compute layer, and this kit prices the orchestration layer.** All three are the same thesis — *the agent economy needs an envelope around it before it can scale*. The starter kit is the envelope a single developer can ship today.

→ Cross-link: [`01` §1 metering Day 1](./01-big-lab-moves.md#1-metering-day-1) · [2026-05-22/03 §1 the agent-team cost lever](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [2026-05-17/03 prompt caching](../2026-05-17/03-practical-skills-and-tools.md) · [2026-05-16/03 /billing audit](../2026-05-16/03-practical-skills-and-tools.md).

---

## 2. OpenAI shipped Codex inside ChatGPT (June 2) — the cross-stack workflow {#2-codex-in-chatgpt}

**What happened (June 2, 2026):** OpenAI shipped **Codex inside ChatGPT** plus **6 role-specific business plugins** (Data Analytics, Creative Production, Sales, Product Design, Public Equity Investing, Investment Banking), bundling **62 popular apps + 110 automated skills**. They also previewed **Codex Sites** (build & deploy hosted internal apps from a prompt) and added **Computer Use on Windows** (Codex can see/click/type in Windows apps while testing).

Two practical changes for *you* (the developer side, not the role-plugin side):

- **Appshots on macOS:** attach an app window to a Codex thread with a hotkey — Codex gets a screenshot + extractable text. Use case: debugging without re-explaining the UI.
- **Branch + worktree + setup-script per thread:** Codex now respects per-thread Git worktree + env-setup scripts. Use case: parallel tasks across the same repo without stepping on each other.

**Sources:**
- [9to5Mac — OpenAI putting Codex inside ChatGPT, 6 new business plugins now available](https://9to5mac.com/2026/06/02/openai-putting-codex-inside-chatgpt-app-everywhere-releasing-6-business-plugins/) `[secondary]`
- [DigitalApplied — OpenAI Puts Codex in ChatGPT With 6 Business Plugins](https://www.digitalapplied.com/blog/openai-codex-chatgpt-business-plugins-june-2026-agentic-work) `[analysis]`
- [DigitalApplied — Codex for Every Role + Codex Sites: 2026 Team Guide](https://www.digitalapplied.com/blog/openai-codex-every-role-sites-2026-team-guide) `[analysis]`
- [Releasebot — Codex Updates by OpenAI - June 2026](https://releasebot.io/updates/openai/codex) `[aggregator]`
- [OpenAI Help Center — ChatGPT release notes](https://help.openai.com/en/articles/6825453-chatgpt-release-notes) `[primary]`

### Why it matters to you

- **Job lens:** The 6 role-plugins (Data Analytics / Creative Production / Sales / Product Design / Public Equity / Investment Banking) **map to specific Solutions Engineer hiring profiles at OpenAI** — each plugin needs an FDE who can deploy it into the customer's actual workflow. **Public Equity and Investment Banking plugins are particularly thin-lane** — most candidates don't have finance domain experience. If you have *any* finance exposure (TA'd for finance, finance project portfolio, even a personal stock-trading codebase), thread that into your OpenAI FDE application this week.
- **Startup lens:** Codex Sites is a **direct threat to Lovable / v0 / Bolt** for the consumer/SMB internal-app niche. If you'd been building in that lane, **pivot or specialize fast** — the consumer "describe an app, get an app" thesis just got OpenAI-scale distribution. The defensible variant is **vertical-Codex-Sites for one industry** (e.g., "Claude/Codex Sites for solo-practitioner attorneys") where compliance/data-residency/UI constraints create a moat — i.e., the same vertical-Claude-for-X wedge from your STARTUPS.md.
- **Insight:** Read **"Codex in ChatGPT app everywhere"** structurally. OpenAI is consolidating its consumer/dev interface to a single binary — ChatGPT becomes the *desktop OS of OpenAI*. Anthropic's posture is the opposite (Claude Code is a CLI, Claude is a chat, the Agent SDK is a library). The contrast is the strategic choice each is making for the public market: **OpenAI = one product surface, Anthropic = a portfolio of surfaces**. As a builder, both have ROI; pick the one whose abstraction model matches the way you think.

→ Cross-link: [2026-05-17/01 §1 Codex on mobile origin](../2026-05-17/01-big-lab-moves.md) · [`05` §2 the three new hyperscaler roles](./05-career-and-startup.md#2-three-roles).

---

## 3. iOS 27 Extensions beta — the weekend project that maps to fall hiring {#3-ios-extension-weekend}

**What to do (weekend project):** download the **iOS 27 Beta SDK** + Apple's Extensions framework sample, build a **"Claude as default Siri" Extension** that handles one verb meaningfully (suggested: "draft a follow-up email to <contact>" — Siri intent → Claude Extension → mail draft preview). Post the code + a 30-second screen recording. Total time: one Saturday.

Why this beats every other portfolio project this week:

- **The hiring surface is thin and 90-day shovel-ready.** Anthropic, Google, and OpenAI all need engineers who can ship a high-quality Extension by Fall 2026. Applicant supply is currently low because the SDK is brand-new (June 8) and most developers haven't installed it.
- **The artifact has a known shipping date.** Recruiters see "I shipped this in the iOS 27 beta the week of WWDC" and read it as *signal* — you ship into uncertainty, you don't wait for stability.
- **It connects two of your ME.md focus areas.** Anthropic-stack skill investment ✕ AI Integration Engineer lane = a Claude-on-iPhone Extension is the literal *job to be done* for an Anthropic Mobile Solutions hire.

**Resources:**
- [Apple Developer — iOS 27 Beta + Extensions framework](https://developer.apple.com/ios/) `[primary]`
- [AI Weekly — Apple iOS 27 Extensions framework overview](https://aiweekly.co/node/2611) `[aggregator]`
- [Macworld — Where are the missing iOS 27 features (timeline)](https://www.macworld.com/article/3166087/where-are-the-missing-ios-27-features-dont-worry-theyre-still-coming.html) `[secondary]`

### Why it matters to you

- **Job lens:** This is the single highest-signal weekend project in scope this month. The Extension SDK is too new for senior engineers to have built against; the iOS 27 GA is too far for new-grad applicants to have prepared. **The window of "fewer than 200 people in the world have shipped a Claude-as-Siri-default Extension"** is open for ~30 days. Be one of them.
- **Startup lens:** A *vertical* Extension (Claude-for-Legal as solo-attorney Siri default; Claude-for-SMB-Accounting as bookkeeper Siri default) is a wedge with a fully-priced distribution channel (Apple App Store marketplace, fall 2026). The constraint is **partner relationship with Anthropic + Apple developer entitlements for the Extension category** — both of which become easier the earlier you start.
- **Insight:** This is the rare moment where a *weekend portfolio project* is also a *credible startup wedge*. The Extension SDK does most of the work; you're shipping the verticalization. Use the Tuesday-night metering shock as the conversation-starter (cost-aware Claude inside an Extension), the Saturday as the build, the Sunday as the post. **One week, three goals advanced.**

→ Cross-link: [`01` §4 iOS 27 Extensions reveal](./01-big-lab-moves.md#4-apple-extensions) · [`05` §3 portfolio shovel](./05-career-and-startup.md#3-portfolio).

---

## 4. The Gemini 3.5 Flash router slot to add this week {#4-flash-leg}

**What to do (60 minutes, ships today):** add Gemini 3.5 Flash as the **cheap-tier leg** of your 3-provider router. From [2026-05-19](../2026-05-19/01-big-lab-moves.md) and [`01` §5](./01-big-lab-moves.md#5-gemini-pending) above: **$1.50/$9 per 1M, 1M context, $0.15 cached**. Route the cheapest task classes (classification, deterministic extraction, summarization) — anything where a `task_type` label is structurally cheap to verify.

The router architecture:
1. **Task-class classifier** (cheap: Flash itself, or a rule-based heuristic for the common cases).
2. **Provider router** with a strict cost envelope per task.
3. **Quality monitor** — sample 5% of outputs, score them against a Sonnet/Opus 4.8 "judge" call, flag regressions.
4. **Trace logger** (from §1.5 above) — every row tagged with `provider` so you can answer "what % of last week's spend went to Flash."

**Why this matters under the new metering economics**: when your Claude Agent SDK pool is finite per month at full API rates, **the question is no longer "is Claude good enough?" — it's "is Flash good enough for *this class of task*."** The router is how you answer that question per-task, not per-project.

**Sources:**
- [VentureBeat — Gemini 3.5 Flash can "slash enterprise AI costs $1B+/yr"](https://venturebeat.com/) `[secondary]` (general framing)
- [Google AI Developers — Gemini API release notes](https://ai.google.dev/gemini-api/docs/changelog) `[primary]`
- [WaveSpeed — June 2026 AI Launch Wave: A Builder's Decision Map](https://wavespeed.ai/blog/posts/june-2026-ai-launch-wave/) `[analysis]`

### Why it matters to you

- **Job lens:** Three-provider routing is now an **expected** interview answer at any AI Integration role, not a bonus. Build the router publicly, post the spend-breakdown across providers as a small case study, link from your resume.
- **Startup lens:** "Router as a service" is increasingly commoditized — but **"router with budget guardrails + audit-grade trace" is not.** That's the wedge — guardrails + audit, not routing per se.
- **Insight:** Notice how **every section in this file points at the same primitive**: cost-aware orchestration. Metering deadline (§1), Codex-in-ChatGPT cross-surface (§2), Extensions verticalization (§3), Flash router (§4). The unifying skill is **"I designed who-does-what, on which model, on which surface, at a predictable cost."** That's the 2026-H2 AI Engineer job description in one line.

→ Cross-link: [2026-05-20/03 §4 cost routing original](../2026-05-20/03-practical-skills-and-tools.md#4-cost-routing) · [`01` §5 Gemini 3.5 Pro pending](./01-big-lab-moves.md#5-gemini-pending).
