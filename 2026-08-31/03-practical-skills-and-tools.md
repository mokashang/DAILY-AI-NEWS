# Practical Skills & Tools — 2026-08-31

Four things to actually do this week. **The effort primitive is now consumer-visible** — every product you build needs to expose it explicitly. **MCP enterprise-managed auth is live for Datadog / Notion / Slack** — the 15-minute migration is the highest-ROI hands-on move of the week. **Four viable coding agents** now exist (Claude Code / Codex-Kiro / Cursor / Muse Code) — the A/B/C/D bench is the artifact interviewers want. **Wednesday: ship the Salesforce-agents cost-log artifact** to catch the Claudeforce open-beta news wave.

Tags: `#claude-code #effort-toggle #mcp #enterprise-auth #model-router #cost-logging #artifacts`

---

## 1. Expose an "effort" toggle in every product you build {#1-effort-mainstream}

**What changed:** ChatGPT's Aug 26 update added a **per-response effort slider** (low / medium / high) for Plus and Pro users on GPT-5.6 Sol. Opus 5 added the same knob at API level on 07-24 [`2026-07-25/03` §1](../2026-07-25/03-practical-skills-and-tools.md#1-opus-5-effort). The effort primitive is now **consumer-visible on both frontier vendors**. That means users will start expecting to see it in every AI product they use.

### What to do tonight (10 minutes)

**In any Claude API call, wire per-subtask effort explicitly:**

```python
# Anthropic SDK — Opus 5 with per-request effort
resp = anthropic.messages.create(
    model="claude-opus-5",
    max_tokens=4096,
    effort="high",           # 'low' | 'medium' | 'high'
    system=SYSTEM,
    messages=[{"role": "user", "content": user_msg}],
)
# Log: cost, latency, effort → one row per call.
```

**In any user-facing UI, expose a three-option control** (not a numeric slider — three labeled buttons perform better in usability testing):

```
[ Fast ]   [ Balanced ]   [ Deep ]
  ~2s        ~6s           ~20s
  $0.003     $0.012        $0.05
```

Show **cost + latency inline**. This is the single fastest way to make a 2026-era product feel current. Users are learning this pattern from ChatGPT/Claude/Gemini and will start rejecting products that hide it.

### Why it matters to you

- **Job lens:** Add one line to your resume: *"Instrumented per-subtask effort routing on Claude Opus 5 / Sonnet 5 team, achieving X% cost reduction at matched eval quality."* This is the single most on-thesis phrase for FDE / Applied AI Engineer screens right now.
- **Startup lens:** UX pattern to steal for your product this week. Users who see the toggle *trust* the product more (they feel in control of cost), which is worth more than the cost savings on its own.
- **Insight:** The "effort primitive" isn't a feature; it's a **new UI convention.** In 12 months, products *without* it will look outdated the way products without dark mode looked in 2021.

---

## 2. Migrate one MCP server to enterprise-managed auth tonight (15 min) {#2-mcp-connectors}

**What changed:** Enterprise-managed authorization for MCP connectors went **GA on Aug 24**, adding **Datadog, Notion, Slack** to the previously supported set (Asana, Atlassian, Canva, Figma, Granola, Linear, Supabase). This is the cleanest MCP-integrator artifact of the year — it takes 15 minutes and produces a defensible portfolio piece.

### 15-minute walkthrough (Notion example)

1. In your Anthropic org console → **Connectors** → **Notion (Enterprise-managed)**. Follow the OAuth handshake; select the workspaces + page-tree scope.
2. In your local Claude Code: `claude mcp add notion --enterprise-managed`. Verify with `claude mcp status` — you should see `auth: org-managed, scopes: [read:pages, write:comments]`, token TTL, and revocation endpoint.
3. Test end-to-end: from Claude Code, ask *"summarize the last 5 pages in the 2026-Q3-Planning workspace"* — it should return without a per-user OAuth prompt.
4. **Screenshot the `claude mcp status` output + one working workflow**. That's your interview visual for the next 60 days.

### Same recipe, different connector

**Datadog:** operationally the most useful for MLE-lane interviews. Wire a metric query (`avg:aws.lambda.duration{env:prod}`) into a Claude Code loop that produces a summary + suggested action.

**Slack:** operationally the most useful for Claudeforce-adjacent product roles. Wire a message-scoped connector into a Claude workflow that reads a channel + drafts a response for you to approve.

### Why it matters to you

- **Job lens:** Interviewers for Applied AI Engineer / FDE / Solutions Engineer roles will start asking *"walk me through a Claude-first enterprise integration"* on every screen this month. A 15-minute artifact you built today answers it *concretely*.
- **Startup lens:** If you're building a Claude-based product for an enterprise buyer, enterprise-managed auth is now a **procurement requirement**. Migrate any user-OAuth-based MCP flow you have to enterprise-managed *before* your next sales call — otherwise the security-review round adds 2–4 weeks to your sales cycle.
- **Insight:** OAuth-per-user was fine for prosumer Claude; it does not survive enterprise procurement. Enterprise-managed auth is what makes Claude a **default-approvable vendor** in Fortune 1000 IT organizations — the same lift GitHub SSO gave GitHub in 2018.

→ Cross-link: [`02` §4 the full MCP milestone context](./02-new-emerging.md#4-mcp-enterprise).

---

## 3. A/B (well, A/B/C/D) the four coding agents on your own repo {#3-model-ab}

**What changed:** With **Muse Code** shipping Aug 5 [`01` §4](./01-big-lab-moves.md#4-meta-muse-code), the coding-agent field is now four labs deep — **Claude Code · OpenAI Codex/Kiro · Cursor · Muse Code**. Ship one shared benchmark on *your own* repo, publish the table.

### The 4-hour recipe

**Pick your repo.** Ideally something you know well but hasn't been touched in ~3 months (so no agent has memorized it from training data). ~5K–20K LOC is the sweet spot. Prefer a well-tested repo — you'll use the test suite as the eval.

**Pick 5 tasks with objective grading:**
1. Fix a real bug you know exists (does the failing test pass?).
2. Add a small feature with a clear spec (does the new test pass?).
3. Refactor one function without changing behavior (does the old test suite pass?).
4. Write documentation for one existing module (rubric-graded, do it yourself in <2 min).
5. Explain the runtime cost of one hot loop (rubric-graded).

**Run each task through each agent, single session, no human corrections.** Log **wall-clock, total tokens (in+out), $ cost, and pass/fail**.

**Publish the 4×5 table** with your interpretation. Two rules that will keep the artifact defensible:
- Report **cost, latency, and pass rate separately** — no composite scores. Composite scores hide the choice.
- Do **not** claim any agent is "best." Claim which one is best *for which task shape*.

### Why it matters to you

- **Job lens:** This is the single artifact that most directly answers *"can you make a buy decision with data?"* — the FDE / Applied AI Engineer question. Six hours of work, publish Thursday, post on LinkedIn with a note tagged `#claude #codex #cursor #musecode #cost-per-task`.
- **Startup lens:** If you're building on the Anthropic stack, having a *published* comparison table gives you air cover the next time a customer asks "why not Muse Code, it's cheaper?" — you have the actual data, on your actual workload.
- **Insight:** The most-cited technical writer in the AI-tools space over the next 6 months will be whoever publishes the **best cross-vendor coding-agent benchmark on real repos** (not on SWE-bench Verified, which is now saturated). That's a spot on the leaderboard for a solo grad student to *own* if you commit.

---

## 4. This week's artifact — Salesforce-agents cost log, Wednesday {#4-this-weeks-artifact}

**Why this week:** The **Claudeforce open beta launches in September** [`01` §1](./01-big-lab-moves.md#1-claudeforce). The optimal news-cycle window for a "here's how I built on it" post is **this Wednesday–Thursday** (before the flood of Salesforce-partner marketing kicks in).

### The artifact spec (2–3 hours)

**Repo layout:**

```
claudeforce-cost-log/
├── README.md              # 200 words + the cost-comparison table
├── planner_opus5.py       # effort=high; plans the customer-touch workflow
├── worker_sonnet5.py      # effort=medium; executes the reads/writes
├── control_musecode.py    # same workflow, Muse Code as an A/B benchmark
├── control_gpt56.py       # same workflow, GPT-5.6 Sol Ultrafast
├── salesforce_mcp/        # Salesforce read connector (MCP)
├── slack_mcp/             # Slack write connector (MCP, enterprise-managed)
└── cost_log.csv           # per-task: model, effort, tokens_in, tokens_out, latency_s, $_cost, pass/fail
```

**One workflow to run end-to-end:** "Given a Salesforce Opportunity ID, read the associated Contact + Account + last 30 days of Activity, draft a Slack DM to the account owner with a one-paragraph next-best-action recommendation, wait for `:thumbsup:` approval, then log the recommendation back to the Opportunity as a Note."

**Four runs of the same workflow** — one per model. **Cost log** for each. **Pass/fail** for each (was the recommendation coherent + actionable?).

**Publish:**
- **Repo public on GitHub** (with a `.env.example`, no secrets).
- **README with the 4-row cost table**, no editorializing.
- **LinkedIn post Thursday morning** with the table as an image; tag `#claudeforce #anthropic #mcp #cost-per-task`.

### Why it matters to you

- **Job lens:** Times the Claudeforce open-beta news cycle. Salesforce recruiters + Anthropic Alliances recruiters will be actively searching for exactly this artifact next week. You'll be at the top of the search results because almost no one will publish anything this specific this fast.
- **Startup lens:** If any of your wedge ideas touch CRM, sales enablement, or customer-success automation, this artifact *is* your pitch's demo — cheaper to build than a full product, more credible than a mockup.
- **Insight:** Publishing on the news cycle multiplies reach ~10×. The half-life of "Claudeforce-related" as a search term will be maybe 90 days; the artifact will still work forever, but its *discovery* window is now.

→ Cross-link: [`05` §2 how to apply-to-jobs alongside this artifact](./05-career-and-startup.md#2-claudeforce-hiring).

---

## 5. Bonus: five tightened Claude Code habits (post-July-28 stateless MCP era) {#5-cc-habits}

Aggregated from practitioner posts published this month. Each of these matters *more* now that MCP is stateless [`2026-07-25/03` §2](../2026-07-25/03-practical-skills-and-tools.md#2-mcp-migration) and connectors are enterprise-managed [§2](#2-mcp-connectors).

1. **Lean `CLAUDE.md`, kept current.** A stale `CLAUDE.md` is worse than none — Claude trusts it. Prune whenever the repo changes; date-stamp the file.
2. **Plan mode before any edit on non-trivial change.** Collapses ambiguous decisions into a reviewed spec at ~100% confidence per decision, then executes.
3. **Sub-agents in isolated worktrees for noisy research.** Same primitive Muse Code just shipped [`01` §4](./01-big-lab-moves.md#4-meta-muse-code). Reserves your main branch for the reviewed answer, not the exploration.
4. **Hooks as guardrails, not decoration.** A pre-commit hook that runs `pytest -x` catches ~80% of hallucination-driven regressions in practice.
5. **Tests as external truth, always.** Without them, Claude verifies its work using its own judgment, which degrades as context fills. With them, verification is O(1) regardless of session length.

**Sources:**
- [Medium — Effective Claude Code Workflows in 2026: What Changed and What Works Now](https://medium.com/data-science-collective/effective-claude-code-workflows-in-2026-what-changed-and-what-works-now-c93ebc6f8f50) `[analysis]`
- [iwoszapar.com — Claude Code Best Practices: CLAUDE.md and Checks](https://www.iwoszapar.com/p/claude-code-best-practices) `[analysis]`
- [Willow — Best Claude Code Projects & Practices August 2026](https://willowvoice.com/blog/claude-code-projects) `[aggregator]`
- [DEV Community — Claude Code Workflow: Best Practices That Ship Code](https://dev.to/galian/claude-code-workflow-best-practices-that-ship-code-na) `[practitioner]`
- [Firecrawl Blog — Best Claude Code Skills to Try in 2026](https://www.firecrawl.dev/blog/best-claude-code-skills) `[practitioner]`
