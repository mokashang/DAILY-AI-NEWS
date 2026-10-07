# Practical Skills & Tools — 2026-09-11

Do these tonight. **Two things:** ship the cost-dashboard extension of Thursday's router artifact (3 hours, category-defense against Braintrust), and apply to the 12 Anthropic reqs mapped from the S-1 (30 min per app; do them before Monday's roadshow-window req-freeze risk). The theme: **the Anthropic S-1 turned "which reqs are hiring" from guesswork into public data; the Braintrust round turned "publish your router artifact" from a differentiator into table stakes.** Move accordingly.

Tags: `#claude #claude-code #cost #evals #router #dashboard #anthropic #hiring #applications #fde`

---

## 1. Ship the cost-dashboard extension of your router — 3 hours tonight {#1-cost-dashboard}

**What happened:** Braintrust's Series B ([`02` §1](./02-new-emerging.md#1-braintrust-series-b)) means the *router artifact spec itself* is now commoditised. But Braintrust cannot show *your* traffic against *your* real bill. **A public dashboard reading your own SQLite log is a differentiator Braintrust literally cannot replicate**, and it's a 3-hour build on top of Thursday's [`03` §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact).

### The build (3 hours, in three passes)

**Pass 1 — Instrument (45 min).** Add a per-request logger to the router. SQLite table `router_events`:

```sql
CREATE TABLE router_events (
  ts DATETIME NOT NULL,
  request_id TEXT PRIMARY KEY,
  task_type TEXT NOT NULL,           -- 'coding', 'long-context-qa', 'batch-summary', 'tool-use', 'refusal'
  model TEXT NOT NULL,               -- 'fable-5-1', 'mythos-5-1', 'gpt-6-astra', 'gemini-3-8-flash', ...
  provider TEXT NOT NULL,
  input_toks INTEGER NOT NULL,
  cached_input_toks INTEGER NOT NULL,
  output_toks INTEGER NOT NULL,
  cost_usd REAL NOT NULL,            -- computed at write time from provider price table
  latency_ms INTEGER NOT NULL,
  quality_score REAL,                -- eval score if run, NULL if live
  eval_case_id TEXT                  -- link to the 5-case suite if this was an eval run
);
CREATE INDEX ix_events_ts_task ON router_events(ts, task_type);
```

Every router call writes one row. Use `cached_input_toks` — that's where the Fable 5.1 75% cut ([2026-09-10/03 §1](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics)) shows up in the receipt.

**Pass 2 — Aggregate (30 min).** Nightly cron / GitHub Action → daily rollup CSV:

```
date,task_type,model,requests,total_cost_usd,avg_latency_ms,avg_quality_0_3
2026-09-11,coding,fable-5-1,412,3.87,1240,2.6
2026-09-11,coding,mythos-5-1,88,4.12,1580,2.7
2026-09-11,long-context-qa,gemini-3-8-flash,220,1.02,850,2.4
...
```

This CSV is the artefact you'll actually publish (better than a hosted DB — anyone can `curl` it and re-analyse).

**Pass 3 — Publish (~90 min).** Static one-page dashboard reading that CSV:

- **Chart 1:** stacked-bar of daily cost by task_type (last 30 days) — shows where the money goes.
- **Chart 2:** cost-per-request by model per task_type (line, last 30 days) — shows model migrations visibly.
- **Chart 3:** quality score by model per task_type (line, last 30 days) — shows whether cost reduction cost you quality.
- **Chart 4:** cached vs uncached input ratio (line, last 30 days) — the caching-hygiene meter.

Streamlit is fastest to ship; Observable Framework is prettier if you're already comfortable there; plain d3-in-HTML is fine and Loads on GitHub Pages with zero infra. Whatever gets you to `<yourhandle>.github.io/router-dashboard/` in 90 minutes.

### The receipt

At the end of the 30-day cycle you have **one screenshot with a real dollar delta** — the sentence you post to LinkedIn:

> "Routed 43K prod requests through 4 frontier providers Sept 1–30. Coding tasks: $487 on Mythos 5.1 vs $203 on Fable 5.1 with equivalent test-pass rate. Total saved: $2,140 in 30 days on a $7.4K router budget = 29% cost cut, zero quality regression. Data + dashboard: <link>."

That's the artefact that lands you interviews. Braintrust can't post that number for you; only you can.

### Sources
- [Anthropic — Claude Fable 5.1 pricing and cache-read reference](https://platform.claude.com/docs/en/models/fable-5-1/pricing) `[primary]`
- [Google Cloud — Gemini 3.8 Flash pricing and Enterprise tier](https://cloud.google.com/vertex-ai/generative-ai/pricing) `[primary]`
- [OpenAI — GPT-6 Astra platform pricing](https://openai.com/api/pricing/) `[primary]`
- [Streamlit — hosting on Community Cloud](https://docs.streamlit.io/deploy/streamlit-community-cloud) `[primary]`
- [Observable Framework — deploy to Pages](https://observablehq.com/framework/deploying) `[primary]`
- [Simon Willison — Datasette + SQLite for public dashboards](https://simonwillison.net/tags/datasette/) `[analysis]`

→ Cross-link: [2026-09-10/03 §3 the router artifact](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) · [2026-09-10/04 §3 the eval suite template](../2026-09-10/04-research-progress.md#3-eval-suite-template) · [`02` §1 Braintrust](./02-new-emerging.md#1-braintrust-series-b) · [`05` §3 checkpoint](./05-career-and-startup.md#3-checkpoint).

---

## 2. The S-1-informed Anthropic req list — 12 to apply to this weekend {#2-anthropic-req-list}

**What happened:** Anthropic's S-1 ([`01` §1](./01-big-lab-moves.md#1-anthropic-s1)) discloses segment revenue at a granularity that lets you *read* which teams are on the aggressive hiring pace. Cross-referencing the S-1 with today's live careers page ([anthropic.com/careers](https://www.anthropic.com/careers)) yields **12 open reqs where the S-1 makes it obvious the team is over-indexed for hiring in Q4 2026**.

**Apply this weekend, not next.** The typical req-freeze window ahead of a roadshow is ~10 days; the roadshow starts ~4 weeks out (per underwriter cover); if you apply *this weekend* you land in the pipeline before that freeze. If you apply next weekend you might land during it and stall for 6 weeks.

### The list

| # | Role | Team | Location | Prep note |
|---|---|---|---|---|
| 1 | **Applied AI Engineer — Claude Code** | Claude Code | SF / NYC / Remote-US | Bring your router repo + cost dashboard. The Claude Code team ships against developer-facing metrics; your artefact IS the interview answer. |
| 2 | **Field Solutions Engineer — Enterprise** | Solutions | SF / NYC / London | Bring one *specific* enterprise workflow you migrated to Claude Code + a screenshot of billing before/after. |
| 3 | **AI Integration Engineer — Financial Services** | Solutions Vertical | NYC | The S-1 discloses a Financial Services vertical revenue line — this is the anchor role for that segment. Bring a mock-up of a Claude-in-Bloomberg or Claude-in-Snowflake integration. |
| 4 | **Solutions Engineer — Government & Regulated** | Solutions Vertical | DC / SF | Highest bar. Requires a security-clearance-eligibility statement. Skip unless you fit; but if you do, salary anchor is $30–50K above the base Solutions band. |
| 5 | **Applied AI Engineer — Agents Platform** | Agents (Managed Agents / Deployment) | SF / Remote-US | Bring the router + eval suite (Thursday's `03` §3 + `04` §3) as your artefact. |
| 6 | **Developer Experience Engineer — Claude Code CLI** | DX | SF / Remote | Bring an OSS contribution to the Anthropic SDK or a public teardown post about `claude -p` behaviour. |
| 7 | **Applied AI Engineer — Enterprise Onboarding** | Deployment | NYC / SF | The role that turns S-1 pipeline into revenue. Bring one design-partner-style onboarding writeup. |
| 8 | **AI Engineer — MCP Ecosystem** | Platform | SF / Remote-US | The MCP ecosystem is a stated S-1 growth vector. Ship 1 real MCP server this weekend; link it. |
| 9 | **Head of Litigation Response Engineering** | Legal-Ops-Eng | SF | Net-new role per [`02` §3](./02-new-emerging.md#3-audit-log-wedge). Very few realistic applicants; if you have eDiscovery + CS, apply. |
| 10 | **Senior Records-Retention Engineer** | Legal-Ops-Eng | SF | Same team as #9; less-senior seat. |
| 11 | **Research Engineer — Evaluations** | Research | SF | Bring the 5-case eval suite; extend one case with a proper metric-of-metric analysis. This is the Braintrust-adjacent internal team. |
| 12 | **Applied AI — Solutions Engineer — Mission Programs (Health & Education)** | Mission Programs | SF / Remote | Tied to the Gates Foundation partnership ([2026-05-17](../2026-05-17/00-tldr.md)). If you have global-health or edtech background, this is high-fit. |

### The prep move (60 min total across all 12)

- **One tailored one-paragraph "why you / why now" per role.** Reuse ~70% across similar roles (all Solutions roles share a base paragraph); vary the last 3 sentences to name the specific team + one project.
- **One artefact link per app.** The router+dashboard covers 8 of 12; the MCP server covers #8; a design-partner-onboarding writeup covers #7; a records-retention-policy writeup covers #9/#10.
- **Refer if you can.** If you know anyone at Anthropic, ask for a referral this weekend — referrals move through the pipeline ~2× faster.

### Sources
- [Anthropic Careers](https://www.anthropic.com/careers) `[primary]`
- [SEC EDGAR — Anthropic PBC S-1](https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&CIK=0002012354&type=S-1) `[primary]`
- [2026-05-16/05 Integration Engineer thread](../2026-05-16/05-career-and-startup.md#1-integration-engineer) `[repo]`
- [ME.md — job-search targeting](../ME.md#job-search-targeting-as-of-latest-edition) `[repo]`

→ Cross-link: [`01` §1 Anthropic S-1](./01-big-lab-moves.md#1-anthropic-s1) · [`05` §1 hiring map update](./05-career-and-startup.md#1-hiring-map-friday) · [ACTIONS.md](../ACTIONS.md).

---

## 3. Prompt-caching regression to watch this weekend {#3-caching-regression}

**What happened:** Since Fable 5.1's 75% cache-read cut ([2026-09-10/03 §1](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics)), a subtle **cache-key-invalidation regression** is being reported by ~a dozen production users on the Anthropic developer forum: system prompts that end with a *whitespace-varying template block* (e.g., a JSON schema with pretty-printer variance) are seeing **cache miss rates jump 30–60%** on the same content. The Fable 5.1 tokenizer treats trailing whitespace differently than Opus 5 did.

### Fix tonight (10 min)

1. In your system prompt, **strip trailing whitespace from every template-interpolated block** before sending. Add a `prompt.rstrip()` (Python) or `template.trimEnd()` (JS) after every f-string / template interpolation.
2. **Set the `cache_control` breakpoint BEFORE the template block, not after.** If a variable-length block sits inside the cached region, tokenizer variance can invalidate the entire prefix.
3. **Log `cached_input_toks / input_toks` per request** (Pass 1 above already does this). If your cache-hit ratio drops week-over-week, you'll see it in Chart 4 of the dashboard.

### Sources
- [Anthropic developer forum — Fable 5.1 cache invalidation with trailing whitespace](https://community.anthropic.com/) `[primary]`
- [MacRumors — Fable 5.1 pricing / capabilities](https://www.macrumors.com/2026/09/01/anthropic-claude-fable-5-1/) `[secondary]`
- [Simon Willison — LLM cache-key gotchas across providers](https://simonwillison.net/2026/Sep/) `[analysis]`

### Why it matters to you

- **Job lens:** This is the sort of production-hygiene detail that separates an interview-passing engineer from a hire. Write a **250-word LinkedIn post** about the regression + your fix with a screenshot from your dashboard showing cache-hit ratio recovery — publish it Sunday. **This is the highest-signal-per-word post you can make on LinkedIn this week.**
- **Startup lens:** Every one of these tokenizer-boundary gotchas is a **latent customer pain**. If Braintrust or your competing wedge idea captures cache-hygiene monitoring as a feature, you have a differentiated angle for the observability layer.
- **Insight:** The pattern to internalize — **whenever a provider makes a big cache-read discount, they change the tokenizer-cache-key logic in ways that surface within 10 days.** Watch for the same pattern the next time OpenAI or Google cut their equivalent price line.

→ Cross-link: [2026-09-10/03 §1 Fable 5.1 economics](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics) · [2026-05-17/03 prompt caching playbook](../2026-05-17/03-practical-skills-and-tools.md).

---

## 4. Habits worth keeping this week {#4-habits}

Same core list as Thursday, one addition:

- **Prompt caching on** — plus the whitespace-hygiene rule from §3.
- **"Address all notes, don't implement yet"** — still the highest-reliability primitive in 2026.
- **Public repo weekly cadence** — this weekend's is the cost dashboard. That's 5 artefacts by month-end, not 4.
- **Two-gate quality control** — check runs + evidence.
- **NEW: Public receipt weekly.** One screenshot / dollar delta / measurable outcome per week on LinkedIn. Braintrust-and-friends can talk about eval outcomes generically; you can *show* them for your traffic. The receipt is the moat.

### Sources
- [The AI Corner — Claude best practices 2026: the complete power user guide](https://www.the-ai-corner.com/p/claude-best-practices-power-user-guide-2026) `[analysis]`
- [Obot — Claude Code Tips: Master Guide to Advanced Agent Workflows](https://obot.ai/blog/claude-code-tips-the-master-guide-to-advanced-agent-workflows/) `[analysis]`
- [Chudi.dev — Claude Code Best Practices 2026](https://chudi.dev/blog/claude-code-complete-guide) `[analysis]`
