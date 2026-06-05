# 03 — Practical Skills & Tools — 2026-06-05

Hands-on workflows, tools, prompting, productivity. Act on these tonight.

---

## §1 — T-10 days to June 15 Agent SDK metering — final actions {#1-june-15-final}

**The clock.** Anthropic's June 15 billing change ([first surfaced 2026-05-16](../2026-05-16/01-big-lab-moves.md)) takes effect **Sunday June 15, 2026** — that's **10 days from today**. Confirmed details:

- Programmatic Claude (Agent SDK, `claude -p`, GitHub Actions integrations, OpenClaw, anything not the chat UI) moves to a **separate monthly credit pool** at **API list rates, no rollover.**
- Tier credits: **Pro $20 / Max-5x $100 / Max-20x $200.**
- **Manual toggle still required** ([per 2026-05-18 confirmation](../2026-05-18/01-big-lab-moves.md)) — silent failure if skipped: your scripts hit a wall on June 15.

**The 4 free wins to land tonight or this weekend (sequence matters):**

1. **TOGGLE THE CREDIT POOL** in account settings. 5-minute task. Without this, your scripts break on June 15.
2. **SWITCH ORCHESTRATOR LEG TO OPUS 4.8 FAST.** New fast-mode pricing **$10/$50 per MTok = ~3× cheaper for equivalent throughput** than the prior fast tier (VentureBeat). For the **Opus-orchestrator / Sonnet-worker team** from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost), this is a **drop-in cost win** with no quality regression — Opus 4.8 outperforms 4.7 on every benchmark ([`01` §3](./01-big-lab-moves.md#3-opus-48)).
3. **ENABLE PROMPT CACHING** on the orchestrator's system prompt (the 5×-cost lever from [2026-05-17/03 §3](../2026-05-17/03-practical-skills-and-tools.md)). On Opus 4.8 cached pricing this stacks with the fast-mode discount.
4. **INSTRUMENT PER-STEP COST LOGGING** before June 15, not after. You want the **before/after metering chart** for your portfolio writeup ([2026-05-22/05 §2](../2026-05-22/05-career-and-startup.md#2-reprice) — the value is "I designed who-does-what, on which model, verified, at a predictable cost").

**Sources:**
- [Anthropic's June 15 Billing Change — Codersera](https://codersera.com/blog/anthropic-june-2026-billing-change-claude-code/) `[analysis]`
- [Anthropic splits Claude subscriptions: what changes for indie hackers on June 15 — DevtoolPicks](https://devtoolpicks.com/blog/anthropic-splits-claude-subscriptions-agent-sdk-credit-june-2026) `[analysis]`
- [Claude Code Updates by Anthropic — June 2026 — Releasebot](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Claude Platform release notes overview](https://platform.claude.com/docs/en/release-notes/overview) `[primary]`
- [claude-code CHANGELOG.md — GitHub](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md) `[primary]`

**Why it matters to you:**
- **Job:** **Cost-aware engineering is now a default interview question** (Anthropic Solutions, Sierra Customer Engineering, OpenAI FDE, Microsoft Agent 365). A real **before/after metering chart** for *your own* agent stack is a 30-second portfolio anchor that beats five generic LinkedIn bullets.
- **Startup:** If you're shipping an agent product, **your competitors are doing this audit tonight too.** Whoever lands the cost reset first publishes lower COGS first, which compounds in the next pricing comparison post (a thin window for product-marketing differentiation, see [`01` §3](./01-big-lab-moves.md#3-opus-48)).
- **Insight:** The metering is not adversarial — it's Anthropic correctly **separating the chat-UI subsidy from the API economy** so programmatic use scales without subsidizing the chat tier. Builders who treat it as Anthropic-being-greedy will miss the lesson: **the price of inference is now your problem to engineer around, not Anthropic's to absorb.**

**Tags:** `#claude-code #pricing #june15 #cost #opus48 #agent-sdk #prompt-caching`

---

## §2 — Instrument BAGEN-style budget intervals into your agent (weekend project) {#2-bagen-instrumentation}

**What it is.** The BAGEN paper (Northwestern, [`04` §1](./04-research-progress.md#1-bagen)) formalizes **budget-awareness as progressive interval estimation**: at every step of a plan, an agent should predict an **upper + lower bound on remaining budget** to complete the task, and **alert the user when completion is unlikely.**

**Why this is a 2-hour weekend project, not a research stunt.** You already have:
- An Opus-orch / Sonnet-worker team (carry from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost))
- Per-step cost logging (from `§1` above, you'll have it by Sunday)
- A real-tool MCP environment (carry from the dual-model sanitiser project)

You can add **two lines per step**:
1. At plan-step `N`, ask the orchestrator: "Estimate `tokens_remaining_lo` and `tokens_remaining_hi` to finish this task."
2. At plan-step `N+1`, compare predicted vs actual. **Log the calibration error.**

**The portfolio artifact:** a **single chart** showing "predicted budget interval vs realized cost" across 20 runs of your dual-model sanitiser. **This is the cleanest replication you can publish of a paper that came out one week ago.** Tag it as "BAGEN-style budget interval calibration on a real MCP agent."

**Why this lands.** Two compounding reasons:
- **The budget-awareness lane** ([§4 §1 BAGEN](./04-research-progress.md#1-bagen)) is **brand new** (paper published ~1 week ago). Being a top-10 implementer is **a 1-week head start, not a 6-month one.**
- It directly answers Anthropic's [§1 slowdown post](./01-big-lab-moves.md#1-anthropic-pause)'s implicit demand: **verification systems for AI completion claims.** Budget-awareness *is* a verification surface.

**Sources:**
- [BAGEN: Are LLM Agents Budget-Aware? — arXiv 2606.00198](https://arxiv.org/abs/2606.00198) `[primary]`
- [BAGEN HTML view](https://arxiv.org/html/2606.00198) `[primary]`
- [Spend Less, Reason Better: Budget-Aware Value Tree Search for LLM Agents — arXiv 2603.12634](https://arxiv.org/pdf/2603.12634) `[primary]`
- [Budget-Aware Agentic Routing via Boundary-Guided Training — arXiv 2602.21227](https://arxiv.org/pdf/2602.21227) `[primary]`
- [Northwestern's Zihan Wang introduces BAGEN — Digg](https://digg.com/ai/3xbedn99) `[analysis]`

**Why it matters to you:**
- **Job:** **"I implemented budget-interval estimation for an agent and benchmarked calibration"** is a sentence that lands cleanly in an interview screen at Anthropic (Applied AI / Solutions), Sierra (Customer Engineering), or any FDE role. It demonstrates **research-aware product engineering** in one shot.
- **Startup:** **Budget-awareness telemetry is a missing slice in the agent-observability category** (LangSmith / Arize / Helicone / OpenLLMetry). A **standalone "agent budget calibration" tool** could be a $100K-ARR side-project inside 6 months if a real customer needs to forecast monthly agent spend at SLA accuracy. Not a venture-scale wedge, but a useful credibility builder.
- **Insight:** The thing that makes BAGEN matter is not the numbers — it's that **a Northwestern PhD student, a frontier-lab safety researcher (Anthropic Institute), and an enterprise SRE all need the same thing**: a way to know when an agent is about to fail. **One primitive, three customers.**

**Tags:** `#bagen #budget #observability #agents #portfolio #weekend-project`

---

## §3 — Microsoft Agent 365 SDK GA + GitHub Copilot desktop (preview) — what to install this weekend {#3-microsoft-stack}

**Microsoft Build 2026 ([`01` §5](./01-big-lab-moves.md#5-build-2026)) shipped two surfaces worth installing as a literacy exercise — even if your day job stays on Claude.**

**Agent 365 SDK (GA).** The Microsoft answer to Anthropic Agent SDK. Observability + access controls + compliance baked in. Spend **45 minutes** building a hello-world agent that calls a Microsoft Graph tool (e.g., "summarize my calendar this week"). The *value of the exercise* is internalizing the Microsoft compliance/governance model — most Big-4 consulting AI engagements (PwC / Deloitte / Accenture / EY) will require Agent 365 fluency within 12 months.

**GitHub Copilot desktop app (preview).** Native desktop client for agentic workflows. **Spend 30 minutes** comparing the UX to Claude Code CLI on a real refactoring task in a repo you know. Note where each wins; **screenshot the comparison and post it** (this is the kind of artifact recruiters at both companies look at).

**Sources:**
- [Microsoft Build 2026 — Microsoft Newsroom](https://news.microsoft.com/build-2026/) `[primary]`
- [Building agentic apps with Microsoft Fabric — Azure Blog](https://azure.microsoft.com/en-us/blog/microsoft-build-2026-building-agentic-apps-with-microsoft-fabric-and-microsoft-databases/) `[primary]`

**Why it matters to you:**
- **Job:** **Multi-vendor fluency = the 2026 AI Integration Engineer job description** ([ME.md focusing decision](../ME.md)). Two hours this weekend = "AI Engineer skilled in Claude Agent SDK + Microsoft Agent 365 + Google Antigravity" on your LinkedIn. Each line shifts your match-rate measurably.
- **Startup:** If your agent runs on Claude in production but lacks an Agent 365 / Antigravity port, **you cannot sell into Microsoft-shop F500 buyers** without a 6-month rewrite. The cost to learn the API now (low) vs the cost to learn it under buyer pressure (high) is a **founder-skill ROI no-brainer.**
- **Insight:** The **three-platform race** (Claude / Microsoft / Google) is the production-engineering reality of 2026. You'll work with at least two of these in any senior role; you'll port between all three in any startup. Treat them like Linux distros — fluent in all, partisan to one.

**Tags:** `#microsoft #agent-365 #github-copilot #multi-vendor #portfolio`

---

## §4 — Watch: Sunday "ultracode" — Claude Code dynamic-workflow trigger rename {#4-ultracode}

**Quick literacy note.** Claude Code's dynamic-workflow trigger was **renamed `ultracode`** in the Opus 4.8 cycle. If your CLAUDE.md / hooks reference the old name, **update them before June 15** (the metering change may surface any latent bugs).

**Sources:**
- [Claude Code Updates by Anthropic — June 2026 — Releasebot](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [claude-code CHANGELOG.md — GitHub](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md) `[primary]`

**Tags:** `#claude-code #ultracode #release-notes #june15`

---

*Continue to [`04 — Research Progress`](./04-research-progress.md) → for what's moving the frontier.*
