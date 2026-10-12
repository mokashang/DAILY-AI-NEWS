# Practical Skills & Tools — 2026-07-23

Do-it-tonight. Two shipping features, both from Anthropic, both from the last 48 hours, both **immediately portfolio-relevant** for the FDE / Integration-Engineer lane: **Claude Security plugin** (the 6-phase multi-agent scanner you can install in a minute) and **Record a Skill** (the workflow-capture UX that turns a screen recording into a reusable Claude Skill). Ship both this week and you have two new portfolio artifacts by Monday.

Tags: `#playbook #claude-code #plugins #skills #security #portfolio #cost`

---

## 1. Install Claude Security plugin tonight — run the 6-phase scan on your public repos {#1-claude-security}

**The move:** Anthropic shipped the **Claude Security plugin (beta, free)** on July 22 — a **multi-agent vulnerability scanner** for Claude Code ([`01` §2](./01-big-lab-moves.md#2-claude-security)). It's the first shipping-in-the-wild example of the **dynamic-workflow / adversarial-verify** pattern that Anthropic's agent framework is standardizing on. That means: **installing and running it is *also* studying the reference architecture you should be building for.**

**Ninety-minute plan:**

**T + 00:00 — Install and inventory (10 min)**
```
# from any git repo
/plugin install claude-security     # in Claude Code
/claude-security                     # opens the 3-job menu
```
Pick one of your public GitHub repos — ideally your MCP-server portfolio artifact (from ME.md) or a side project you've shipped. If you don't have one, use a public OSS repo you contribute to. **Log the repo name and size (LOC) in a new `security-scan-2026-07-23.md` file** — that's your artifact starting point.

**T + 00:10 — Run "Scan codebase" (30–45 min, mostly wall-clock)**
Watch the six phases print:
1. **Inventory** — attack surface enumeration
2. **Threat model** — code-specific threat model
3. **Research** — background on relevant CVE classes
4. **Sweep** — parallel-subagent findings
5. **Panel** — cross-agent judge / dedup
6. **Adversarial** — refutation pass to kill false positives

**Screenshot every phase.** The 6-phase progress tree is your portfolio proof-of-work.

**T + 00:45 — Triage and pick one fix (15 min)**
Rank findings by (severity × exploitability × time-to-fix). Pick the **highest-severity, lowest-effort** finding.

**T + 01:00 — Generate patch + review + apply (20 min)**
```
/claude-security → Suggest patches
```
Review the `.patch` file (**never blindly apply** — this is your review skill on display), then apply. Commit with a descriptive message that credits the tool and cites the vulnerability class.

**T + 01:20 — Ship the artifact (10 min)**
Push a new file to the repo: `SECURITY-SCAN-2026-07-23.md`. Include:
- The 6-phase screenshot
- The finding you fixed (class, severity, exploit path)
- The commit link
- A one-paragraph "**how I'd wire this into a CI pipeline for a client**" note (this is your FDE close)

**Sources:**
- [MarkTechPost — Anthropic Releases Claude Security Plugin for Claude Code in Beta](https://www.marktechpost.com/2026/07/22/anthropic-releases-claude-security-plugin-for-claude-code-in-beta-a-multi-agent-vulnerability-scanner-that-runs-in-your-terminal/) `[analysis]`
- [Anthropic — Claude Code best practices](https://code.claude.com/docs/en/best-practices) `[primary]`
- [SmartScope — Claude Security Comes to Claude Code: Multi-Agent Vulnerability Scans and Reviewed Patch Suggestions](https://smartscope.blog/en/blog/claude-security-plugin-multi-agent-scan/) `[analysis]`

### Why it matters to you

- **Job lens:** This is a **single evening** for a portfolio artifact that hits three interview questions at once — (1) can you use a multi-agent tool, (2) can you review AI-generated patches critically, (3) can you talk about wiring it into a client's CI. The `SECURITY-SCAN-*.md` file is a **screenshottable, linkable portfolio piece** you can put in a cover letter as-of-this-week.
- **Startup lens:** The **6-phase adversarial-verify pattern generalizes.** Once you've watched it run, sketch a plugin skeleton for a different vertical (secrets, license, PII, cost, a11y). The plugin surface is Anthropic's distribution channel, and it's *young* — first-movers in the plugin marketplace will have the same land-grab window as early Chrome-extension developers.
- **Insight:** The plugin is **free** for a reason: Anthropic wants adoption breadth over per-plugin revenue, and it's betting the *managed enterprise version* is where the money lands. Read this as a durable pattern — for your own plugin builds, plan a **free OSS plugin → paid managed backend** GTM. It's the exact motion Anthropic just modeled.

---

## 2. This weekend: capture your best workflow as a Claude Skill (Record a Skill feature) {#2-record-a-skill}

**The move:** On **July 21**, Anthropic shipped **"Record a Skill"** (rolling out to **Claude Pro / Max / Team** via the desktop **Cowork** interface — look in the `+` menu of the Claude desktop app). You **record your screen**, **narrate what you're doing**, and Claude **compiles the recording into an executable Skill** it can run again.

This is the **workflow-capture UX** the agent ecosystem has been missing — until now, teaching Claude a repeatable task meant writing prompts + docs + eval cases. Now: **do the task once with narration, get a runnable Skill.**

**Weekend plan (2 hours):**

**Saturday (1 hour):**

1. Pick a workflow you already do that has **≥5 steps** and repeats **≥weekly**. Best candidates:
   - "Prep a weekly ML paper digest from arXiv + Hugging Face + one Substack"
   - "Generate a portfolio-review report for a public GitHub repo (structure, tests, security, README quality)"
   - "Cold-outreach prep: read a person's LinkedIn + last 3 blog posts + recent GitHub commits → draft a 3-sentence intro email"
2. Record with narration. Speak the *why* alongside the *what* — Claude's Skill compiler leans on the reasoning to generalize the workflow.
3. Test the Skill on a **new input** you didn't use during recording. That's the true test — it works on *this* case only if it generalized.

**Sunday (1 hour):**

1. Refine the Skill — either re-record or edit the auto-generated Skill definition.
2. Ship it as a **portfolio artifact**: a short blog post + the video + a `README.md` explaining the workflow and the Skill definition.
3. **Add the workflow itself to your resume-adjacent story:** "I codify my repeatable workflows as Claude Skills, both to compound my own productivity and to give clients an executable playbook they can run themselves."

**Sources:**
- [Anthropic Newsroom](https://www.anthropic.com/news) `[primary]`
- [KuCoin — Claude Launches Screen Recording Feature to Automate Workflows into Reusable Skills](https://www.kucoin.com/news/flash/claude-launches-screen-recording-feature-to-automate-workflows-into-reusable-skills) `[secondary]`
- [Dataconomy — Anthropic Adds Screen-recorded Teaching Feature To Claude AI](https://dataconomy.com/2026/07/22/anthropic-teach-claude-screen-recording-feature/) `[secondary]`
- [Search Engine Journal — Anthropic's Claude Can Now Watch A Video And Learn Your Job](https://www.searchenginejournal.com/anthropics-claude-can-now-watch-a-video-and-learn-your-job/583053/) `[secondary]`

### Why it matters to you

- **Job lens:** A **video-plus-Skill portfolio artifact** is the FDE interview close. FDE work *is* "watch what the customer does, then codify it as an executable playbook they can hand to the model." Recording a Skill *is* the FDE interview loop in miniature. Ship one for public consumption; recruiters can't unsee it once it's on your LinkedIn.
- **Startup lens:** Every vertical-agent wedge has a **playbook-library problem** — how do you get the customer's actual workflows into the product without a 3-month integration? Record-a-Skill *solves* the demo-day version of this problem. If you're prototyping a "Claude-for-vertical-X" wedge, use Record-a-Skill to **build 10 canonical workflows for your target vertical**, ship them as pre-built Skills, and use *that* library as the wedge's differentiator. The Skills library is the moat, not the prompts.
- **Insight:** The strategic frame is **procedural memory finally has a UX**. All the "agent memory" arxiv threads ([`04` §1](./04-research-progress.md#1-long-horizon)) have been trying to bridge the gap between *user shows the model a task* and *model does the task again*. Record-a-Skill collapses that gap to a five-minute recording. Track how third-party plugins wrap or extend this primitive — Skill marketplaces, Skill-versioning tools, Skill-testing harnesses. Any of them are fundable.

---

## 3. The cost lever from May 22 has a July version: add Gemini 3.6 Flash as the worker seat {#3-cost-lever-update}

The **Opus orchestrator + Sonnet worker + Haiku verifier** pattern from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) still applies. The **July refinement**: **Gemini 3.6 Flash** ([`01` §4](./01-big-lab-moves.md#4-gemini-3-6-flash)) is now competitive in the **worker seat** for a large class of bounded tasks — $1.50/M in · $7.50/M out, ~17% fewer output tokens than 3.5 Flash, and it beats 3.5 Flash on DeepSWE, OSWorld-Verified, and MLE-Bench.

**Updated routing menu:**

| Seat | 2026-05-22 pick | 2026-07-23 pick | Notes |
|---|---|---|---|
| **Orchestrator / planner** | Opus 4.7 | Opus 4.7 | Unchanged. Reasoning quality still pays for itself here. |
| **Worker (bounded subtasks)** | Sonnet 4.6 | **Sonnet 5 or Gemini 3.6 Flash** | Sonnet 5 shipped June 30 (biggest agentic gains yet). Gemini 3.6 Flash competitive at lower price. Run *both* on your workload and pick per-task. |
| **Verifier / guard** | Haiku 4.5 | Haiku 4.5 or **Gemini 3.5 Flash-Lite** | Both cheap-enough-to-run-continuously. |
| **Cyber-specific tasks** | (none) | **Claude Security plugin (§1) or Gemini 3.5 Flash Cyber pilot** | Both new this week. |

**The unchanged principle** (worth repeating because June 15 metering is now live): **the plan must be right before the workers execute**, or the cheap-worker savings amplify a bad plan.

**Sources:**
- [Anthropic Newsroom — Claude Sonnet 5 launch](https://www.anthropic.com/news) `[primary]`
- [Artificial Analysis — Gemini 3.6 Flash Intelligence, Performance & Price Analysis](https://artificialanalysis.ai/models/gemini-3-6-flash) `[analysis]`
- [MarkTechPost — Google Releases Gemini 3.6 Flash, 3.5 Flash-Lite, and 3.5 Flash Cyber](https://www.marktechpost.com/2026/07/21/google-releases-gemini-3-6-flash-3-5-flash-lite-and-3-5-flash-cyber-a-cheaper-more-token-efficient-flash-tier-built-for-agentic-workloads/) `[analysis]`

### Why it matters to you

- **Job lens:** Cross-vendor routing is now the *higher-signal* FDE skill. **Show a benchmark table** — "for our workload X, Sonnet 5 beat Gemini 3.6 Flash by Y% at Z% higher cost, so we used *this* mix" — and you've just done the exact analysis a Solutions engineer does on a client call. Add cross-vendor routing to your ME.md active-focus list.
- **Startup lens:** Multi-vendor is now table stakes for any AI-application startup. If your architecture assumes one lab, you're one API-key-cancellation, one price-hike, or one incident (see [`01` §1](./01-big-lab-moves.md#1-openai-escape)) away from a broken product. Bake vendor-agnosticism in from day one.

→ Cross-link: [2026-05-22/03 §1 the original cost-routing pattern](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [`01` §4 Gemini 3.6 Flash pricing](./01-big-lab-moves.md#4-gemini-3-6-flash).

---

## 4. Housekeeping: DeepSeek endpoint deprecation on Friday {#4-deepseek-deprecation}

If any of your side projects or evals hit the old `deepseek-chat` or `deepseek-reasoner` endpoints, **migrate today** — they retire **July 24, 15:59 UTC** (tomorrow) in favor of `deepseek-v4-pro` and `deepseek-v4-flash`. Silent 404s otherwise.

**Sources:**
- [DeepSeek API Docs — V4 Preview](https://api-docs.deepseek.com/news/news260424/) `[primary]`
