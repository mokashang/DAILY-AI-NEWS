# Practical Skills & Tools — 2026-06-30 (Tuesday)

Four moves, each tractable in <90 min, each tied to today's news beats. The frame: **shipping under the new state-and-federal regime requires no new framework — just a small bundle of public artifacts that prove you read the news and can build to it.**

Tags: `#claude-code #mcp #colorado #compliance #portfolio #cost-routing`

---

## 1. The Colorado AI Act Day-1 discoverability move (30 min) {#1-colorado-day1-discoverability}

**The fact:** Yesterday's one-thing-to-do ([2026-06-29/03 §1](../2026-06-29/03-practical-skills-and-tools.md#1-colorado-compliance)) was to ship a 1-page Colorado AI Act compliance memo before bed. **Today's job: make that memo *find-able* on Day 1 of the Act being live.**

**The 30-min sequence:**

```
1.  README + screenshot.
    ☐ Pin "Day 1 of Colorado AI Act (Jun 30 2026)" in the repo description.
    ☐ Date-stamped screenshot of the memo open in a browser, committed to /assets.

2.  LinkedIn discoverability (the 5-skill update).
    ☐ Add five skills (verbatim) to your LinkedIn skills section:
        • AI Compliance Engineer
        • SB24-205 / Colorado AI Act
        • NIST AI RMF (AI 600-1 generative profile)
        • Pre-deployment evaluation
        • Output provenance / model-release governance
    ☐ Post one-line note: "Day 1 of the Colorado AI Act — here's a 1-page compliance
      memo for a Claude-built agent: <repo link>"

3.  Resume headline.
    ☐ Re-title to: "AI Integration / Compliance Engineer — Anthropic stack ·
      Colorado-AI-Act-ready · NIST AI RMF · cost-aware agent design"

4.  Track inbound.
    ☐ Note any recruiter views / DMs in APPLICATIONS.md; the keyword has
      ~zero candidate competition for the next ~30 days.
```

**Why now:** the Act takes effect *today*. Hiring keywords spike on go-live dates; the Act's keyword cluster did not exist as a recruiter-search term 72 hours ago. **First-mover-in-the-keyword effect is real and short-lived.**

**Sources:**
- [Colorado SB24-205](https://leg.colorado.gov/bills/sb24-205) `[primary]`
- [NIST AI RMF 1.0 + AI 600-1](https://www.nist.gov/itl/ai-risk-management-framework) `[primary]`
- Carries from [2026-06-29/03 §1](../2026-06-29/03-practical-skills-and-tools.md#1-colorado-compliance)
- Carries the assurance-keyword tree from [2026-06-29/05 §3](../2026-06-29/05-career-and-startup.md#3-assurance-lane)

### Why it matters to you

- **Job lens:** Day-of-news-event keywords are the rare signal that lets a new-grad candidate look "first-mover" on a topic that an experienced candidate would have to back-fill. Use it.
- **Startup lens:** The act of dating the memo is the act of standing up the customer-facing identity — *you* become someone the deployer-side wedge ([`02` §2](./02-new-emerging.md#2-deployer-wedge)) can find.
- **Insight:** This is one of the few times "be early to the keyword" is a defensible career move and not a marketing tactic. Be early.

---

## 2. Build a 1-page mock impact assessment for a Claude-built agent (60 min) {#2-mock-impact-assessment}

**The fact:** The Colorado AI Act's compliance posture is built around **annual impact assessments** for high-risk AI systems. **You can write a mock impact assessment in 60 minutes** — and almost no candidate at the new-grad level will have one.

**The 60-min outline (use as a template):**

```
1.  System summary.
    ☐ Name + version of the Claude-built agent (e.g. "HR-screen-bot v0.1").
    ☐ Decision class: employment (high-risk under SB24-205).
    ☐ Deployer + developer responsibilities mapped to the Act's two-sided model.

2.  Intended use, foreseeable risks.
    ☐ Adverse impact analysis — protected-class disparity probes.
    ☐ False-positive/-negative cost surface — labor-market consequence.
    ☐ Out-of-scope behaviors — what the model is instructed NOT to do.

3.  Risk management mapped to NIST AI RMF.
    ☐ Govern: human-in-the-loop policy; appeal pathway; logging discipline.
    ☐ Map: data lineage of training/eval data; system boundary diagram.
    ☐ Measure: eval suite (adversarial probes + protected-class fairness).
    ☐ Manage: rollback plan; incident-response shape.

4.  Consumer-rights workflow.
    ☐ Notice copy template (English + Spanish).
    ☐ Explanation-of-adverse-decision copy template.
    ☐ Right-to-correct and appeal-to-human flow diagram.

5.  Eval evidence.
    ☐ Per-prompt eval traces from a small open-source benchmark
      (e.g., a HELM safety slice or HuggingFace eval-trace bundle).
    ☐ Sampled adversarial probe transcripts.

6.  Documentation footer.
    ☐ Authoring date + review cadence (annual minimum per Act).
    ☐ "This is a mock for portfolio use; not for production deployment."
```

**Output:** a public PDF + Markdown repo. Link from the README. **Pin above resume projects.**

**Sources:**
- [NIST AI RMF 1.0](https://www.nist.gov/itl/ai-risk-management-framework) `[primary]`
- [NIST AI 600-1 Generative AI profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) `[primary]`
- [HELM](https://crfm.stanford.edu/helm/) `[primary]` — for the eval-evidence layer

### Why it matters to you

- **Job lens:** This artifact answers the *exact* interview prompt a deployer-side AI Risk & Compliance Engineer role asks ("walk me through how you'd structure an impact assessment under Colorado SB24-205"). 60 minutes to produce the answer that almost no candidate has.
- **Startup lens:** The template generalizes — same structure works for NYC AEDT bias-audit law, EU AI Act high-risk system docs, and (soon) NY/CA AI bills. **A productized version of this template is the §2 wedge from `02`** — but even without productizing, having the template means you can produce real customer artifacts the day you start.
- **Insight:** Impact assessment as a *technical document* (not a legal one) is an under-built skill. The candidates who own it become the bridge function on every regulated-AI deployment team.

---

## 3. The pre-IPO 60-day Claude Code cost-router refresh (45 min) {#3-cost-router-refresh}

**The fact:** The 60-day pre-IPO calendar from [2026-06-28/05 §3](../2026-06-28/05-career-and-startup.md#3-ipo-window-plan) puts your portfolio on a clock. **One cheap refresh that lifts every other artifact: re-run your cost-router benchmarks against the *current* model lineup.**

The current lineup (as of June 30):

| Tier | Anthropic | OpenAI | Google |
|---|---|---|---|
| Flagship | Fable 5 ($10/$50 per M, restricted) / Opus 4.8 ($15/$75) | Sol ($5/$30, limited preview at U.S. gov request) | Gemini 3.5 Pro |
| Mid | Sonnet 4.6 | Terra ($2.50/$15) | Gemini 3.5 Pro (cheaper tier) |
| Budget | Haiku 4.5 ($1/$5) | Luna ($1/$6) | Gemini 3.5 Flash ($0.30/$2.50) |
| Open | (—) | (—) | (—) |
| Open / cheap | GLM-5.2 (MIT, 753B MoE, 1M ctx, 62.1 SWE-Bench Pro, $1.40/$4.40 per M) | (—) | (—) |

**The 45-min update:**

```
1.  Re-tag your 3-provider router with the current model IDs.
2.  Add GLM-5.2 as an open-source / cheap-Opus-fallback leg
    (the SemiAnalysis-noted ⅙-of-Opus-cost lane).
3.  Run a 50-prompt benchmark mix (1/3 summarize, 1/3 classify,
    1/3 small code-edit), log per-step token + $$.
4.  Publish a table to the README. One line per model:
    p50 latency · cost per 50-prompt run · qualitative win-rate vs Opus 4.8.
5.  Push to GitHub.
```

**Why now:** the cost-router skill is now table-stakes for FDE/Solutions; the differentiator is whether you've benchmarked against *this month's* lineup, not last month's.

**Sources:**
- [Artificial Analysis](https://artificialanalysis.ai/) `[primary-data]`
- [OpenRouter rankings](https://openrouter.ai/rankings) `[primary-data]`
- Carries from [2026-05-20/03 §4 cost-router pattern](../2026-05-20/03-practical-skills-and-tools.md#4-cost-routing)
- Carries from [2026-06-27](../2026-06-27/03-practical-skills-and-tools.md) for the GLM-5.2 noting

### Why it matters to you

- **Job lens:** Hiring-manager interviews increasingly ask "walk me through your cost-routing thinking" — having a benchmark from *this week* makes you concrete instead of theoretical.
- **Startup lens:** A current cost-router with GLM-5.2 included is genuinely useful for SMB customers without an FDE attached. Pair with the [Terra cost-audit playbook from May](../2026-05-20/03-practical-skills-and-tools.md#4-cost-routing).
- **Insight:** Re-benchmarking is a 45-minute habit, not a project. Do it monthly the first of the month.

---

## 4. Build the trusted-channel proxy for one more input source today (30 min) {#4-trusted-channel-proxy-extend}

**The fact:** Sunday's [trusted-channel proxy ([2026-06-28/03 §1](../2026-06-28/03-practical-skills-and-tools.md#1-trusted-channel-proxy))] sanitizes Sentry / GitHub / npm input streams before a Claude Code agent reads them — the 90-min, ~50-LOC mitigation for agentjacking ([2026-06-28/02 §1](../2026-06-28/02-new-emerging.md#1-agentjacking)). Today's extension:

**Add one more input source — the one you actually use.** Likely candidates:

- **Linear / Jira ticket bodies** (markdown often injected by users).
- **Slack channel content** (if you wire Claude Tag in).
- **Email body** (if you wire Claude into an inbox).
- **PR review comments** (richer than commit messages; high injection-surface).

Same shape: parser strips/quarantines markdown image tags, fenced code with dangerous flags, and HTML; logs each sanitization to a sidecar file.

### Why it matters to you

- **Job lens:** Trusted-channel proxy is the most directly-citable "I built the standard mitigation for agentjacking" artifact. Two input sources covered > one — shows engineering breadth.
- **Startup lens:** This generalizes into a **multi-source trusted-channel SDK** — sold to Linear/Jira/Slack/Sentry as a sanitizer endpoint. A weekend MVP.
- **Insight:** The agentjacking class of attack will compound as agents become more autonomous. Earlier you wire the proxy into your stack, the lower the surface area when the next disclosure lands.
