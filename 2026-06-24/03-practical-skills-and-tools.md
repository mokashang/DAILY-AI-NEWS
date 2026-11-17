# Practical Skills & Tools — 2026-06-24

Three things to do today, each in <60 minutes, each producing an artifact or a measurable cost reduction. The point: convert this week's cliffs (Fable 5 plan-cliff yesterday, Daybreak full launch 06/22, GPT-5.6 / Gemini 3.5 Pro launch windows open) into **two tangible outputs by Friday**.

Tags: `#claude-code #cost #routing #portfolio #codex-security #openai #anthropic`

---

## 1. Day-1 of the Fable 5 cliff — change defaults BEFORE checking the dashboard {#1-day-one-of-the-cliff}

**The trap to avoid:** opening your billing dashboard at noon today, seeing yesterday's bill, and *then* changing your model defaults. By that point you've already paid for the lesson. Do it now.

**Concrete steps (15 minutes total):**

1. **Open `~/.config/claude-code/settings.json`** (or your equivalent project-level config). Change the default model from `fable-5` to **`sonnet-4-6`**. If you have Opus 4.8 credits, keep Opus 4.8 as the *secondary* tier; Fable 5 becomes *tertiary*, used only when you explicitly request it.
2. **For any orchestrator harness** (Claude Code, your own subagent setup, Cursor, etc.) — set Fable 5 as **verifier-only** per the [2026-06-23 reroute playbook](../2026-06-23/03-practical-skills-and-tools.md#1-reroute). The pattern: **Opus-orchestrator + Sonnet-workers + Fable-5-judge**. Fable 5 evaluates the team's output; it does not generate the work.
3. **Add a `cost-log.md` to your project root** with two columns: *date* and *bill-since-last-reset*. Update it every Friday for 4 weeks. By the end you'll have a defensible "I cut my agent-bill from $X to $Y by re-routing to Sonnet" portfolio note.
4. **Tonight at 9pm, check the billing dashboard.** Compare yesterday (last day Fable 5 was on-plan) to today (first day off-plan, with new defaults). Log both numbers.

**Why this matters: you can build the interview talking point without paying for it.** Most candidates will pay the surprise bill *and* not learn from it. You can learn from it *and* not pay.

**Sources:**
- [2026-06-23/01 §1 — the Fable 5 plan-removal mechanics](../2026-06-23/01-big-lab-moves.md#1-fable-5-plan-removal)
- [2026-06-23/03 §1 — yesterday's reroute playbook](../2026-06-23/03-practical-skills-and-tools.md#1-reroute)
- [Anthropic — Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) `[primary]`

### Why it matters to you

- **Job lens:** "I caught and pre-empted the Fable 5 plan-cliff before my bill spiked" is a 60-second story that proves **operational discipline** — the same trait every FDE / Solutions Engineer interview is screening for. Drop it into your cover letter as a one-line note: *"Cut my Claude Code monthly bill 60% by re-routing defaults from Fable 5 → Sonnet 4.6 the day the plan-cliff landed."*
- **Startup lens:** Build for the developer-tier user who *won't* read this and *will* get the surprise bill. **A 4-week-trial Claude-bill audit + reroute tool** that connects to a user's Anthropic account, identifies their per-task model-utilization, and recommends a routing config is a $10–25/mo SaaS — and the [Agent SDK metering pause](../2026-06-21/00-tldr.md) means there's a 2026 launch window before metering proper.
- **Insight:** **Default values are the most under-priced lever in 2026 cost control.** Every developer tool ships with a default model; almost no developer overrides it; the resulting bills are 2–10× what they need to be. Skill that compounds: **always override the default, always log the reason, always re-audit monthly.**

---

## 2. Ship one Codex Security artifact this week — before the free-tier window closes {#2-codex-security-artifact}

**The opportunity:** the [Daybreak partner program expansion (Mon 06/22 — 2026-06-23/01 §2)](../2026-06-23/01-big-lab-moves.md#2-openai-daybreak) opened a window where individual developers can still touch **Codex Security** through the public docs without partner-program friction. **That window will narrow** as partner monetization kicks in. The shippable artifact:

**Concrete steps (4–6 hours total — over an evening + Saturday morning):**

1. **Pick one OSS project** you already use and care about (a Python library you've touched, a Go tool you've extended). Fork it.
2. **Run Codex Security** in patch mode on the fork: have it scan + propose fixes for a single vulnerability class (path traversal in HTTP handlers, SQL injection in ORM helpers, command injection in CLI wrappers — pick *one* narrow class).
3. **Critically verify every finding by hand.** Most will be false positives. Log: how many findings, how many real, how many false. (This is the verification skill from [2026-05-22/05 §2](../2026-05-22/05-career-and-startup.md#2-reprice) — exactly the muscle FDE/Integration-Engineer roles screen for.)
4. **For each verified finding:** apply Codex Security's proposed patch, add a regression test, file a PR upstream. Even if upstream rejects, you have a public PR with your name on it.
5. **Write a 600-word post on your blog / LinkedIn** with the title pattern: *"I ran Codex Security against [Project X] looking for [Class Y]. N findings → M verified → K PRs filed → J merged."* Cite Patch the Planet's headline numbers (30M commits / 30K codebases / 70K human-confirmed-fixed / 500K auto-fixed) as the *benchmark you're matching* at a single-developer scale.

**Why this is the right artifact this week (not next):**
- **Recruiter-legible** — a famous announcement 48 hours old that you're emulating. People will read your README.
- **Cheap** — 4–6 hours over an evening + Saturday.
- **Maps directly to job applications** — IBM Security, Trail of Bits, CrowdStrike, Wiz, Snyk, Exaforce, plus the [Glasswing coalition members](./01-big-lab-moves.md#2-daybreak-vs-glasswing).
- **Two-lab framing** — the same artifact, repeated with **Anthropic Mythos / Sonnet 4.6**, becomes the *Daybreak-vs-Glasswing* comparison post — i.e., **the FDE-shaped interview prep** for [`05` §1](./05-career-and-startup.md#1-two-cyber-markets).

**Sources:**
- [OpenAI — Daybreak (program page)](https://openai.com/daybreak/) `[primary]`
- [OpenAI — Patch the Planet: a Daybreak initiative to support open source maintainers](https://openai.com/index/patch-the-planet/) `[primary]`
- [Trail of Bits — Introducing Patch the Planet](https://blog.trailofbits.com/2026/06/22/introducing-patch-the-planet/) `[primary]`
- [Anthropic — Project Glasswing](https://www.anthropic.com/project/glasswing) `[primary]`

### Why it matters to you

- **Job lens:** This *one* artifact is the highest-conviction portfolio move I can give you this quarter. It maps to **two job markets** (Daybreak partners + Glasswing coalition) and **one founder wedge** (the middle layer between them). Most candidates will read about Patch the Planet; you will *have done it*.
- **Startup lens:** Step 3 above (the verification step) is the *product*. If your single-developer scan-verify-patch loop works for one bug class on one project, **the productized version is the Daybreak-style continuous-OSS-hardening service** for an enterprise's open-source dependencies. This is the same wedge I framed in [2026-06-24/01 §2 startup lens](./01-big-lab-moves.md#2-daybreak-vs-glasswing). The artifact is your proof-of-execution.
- **Insight:** **Recruiter-legible artifacts are produced by *copying a headline*, not by *being original*.** Don't try to find a novel use of Codex Security; **match the news cycle's pattern at your own scale**. That's the highest-return content strategy of 2026.

---

## 3. Pre-stage your launch-day publication for GPT-5.6 / Gemini 3.5 Pro {#3-launch-day-checklist}

**Both windows are open this week** ([`02` §1 GPT-5.6](./02-new-emerging.md#1-gpt-56-window), [`02` §2 Gemini 3.5 Pro](./02-new-emerging.md#2-gemini-pro-window)). Pre-staging means **you can publish the comparison ~3 hours after either model goes GA**, instead of ~36 hours.

**Concrete steps (45 minutes today):**

1. **Open a Google Doc** titled `Launch Day Bench — GPT-5.6 + Gemini 3.5 Pro vs Fable 5 + Opus 4.8`. Add the comparison-table scaffold:

   | | **GPT-5.6** | **Fable 5** | **Opus 4.8** | **Gemini 3.5 Pro** |
   |---|---|---|---|---|
   | SWE-bench Verified | TBD | ?% | ?% | TBD |
   | DeepSWE pass@1 | TBD | **70%** (06/20) | ?% | TBD |
   | FrontierMath tier-4 | TBD (leaked: improved) | ?% | ?% | TBD |
   | Context window | TBD (leaked: ~1.5M) | 1M | 1M | TBD (confirmed: 2M) |
   | $/M in | TBD | $10 | $5 | TBD |
   | $/M out | TBD | $50 | $25 | TBD |
   | Latency 10K-token task | TBD | TBD | TBD | TBD |

2. **Write the framing paragraphs *now*** — they don't depend on the numbers. Use today's templates: *"Frontier AI is now a two-axis race: capability per dollar (where Anthropic still leads on coding) and capability per token (where Google's larger context windows reframe long-doc tasks)."*

3. **Set up a 5-tab benchmark notebook** (Python or just a markdown file) that runs the same 3 prompts on each model the moment you have API access. Suggested prompts: (a) a SWE-bench problem; (b) a 10K-token long-context summarization; (c) an agent-loop with a custom MCP tool. Don't optimize the prompts; they're benchmarks, not demos.

4. **The instant the system card or release notes ship**, fill the table in. **Publish to LinkedIn and your blog within 3 hours.** Title formula: *"GPT-5.6 vs Fable 5 vs Opus 4.8: the only table that matters"* (substitute model names per which lands first).

**Sources:**
- [OpenAI Model Release Notes (live)](https://help.openai.com/en/articles/9624314-model-release-notes) `[primary]`
- [Google AI for Developers — Gemini API Release Notes](https://ai.google.dev/gemini-api/docs/changelog) `[primary]`

### Why it matters to you

- **Job lens:** A timely, sharp launch-day post = **~5,000–20,000 LinkedIn impressions** from the same engineers and recruiters who would otherwise never see your profile. The cost-per-impression of pre-staging is the **single best free recruiter-attention play** of 2026.
- **Startup lens:** If your product has a model registry, **publishing a launch-day comparison signals to investors that you have an operational routing layer** — which is the moat for any agent-shaped startup right now. The blog post *is* the seed-deck appendix.
- **Insight:** **Speed of public response is a credential**, and the launch-window structure of 2026 (two flagship windows open simultaneously) is rare. Pre-stage now; ship the moment either lands.

→ Cross-link: [`02` §1 GPT-5.6 window mechanics](./02-new-emerging.md#1-gpt-56-window) · [`02` §2 Gemini 3.5 Pro mechanics](./02-new-emerging.md#2-gemini-pro-window) · [`05` §2 the FDE pitch updates](./05-career-and-startup.md#2-keep-the-fde-track).
