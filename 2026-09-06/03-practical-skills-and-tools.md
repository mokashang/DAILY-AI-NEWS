# Practical Skills & Tools — 2026-09-06

Act on this today. **Three concrete deploys:** (1) a 3-model comparison harness (Astra / Fable 5.1 / Gemini 3.8 Flash) — this is the weekend artifact; (2) the Claude Code Sept features (`managedMcpServers`, `--permission-prompts none`, smaller binary); (3) a mandatory Sonnet-5 cost re-audit now that the promo pricing has expired. All three are shippable in one weekend.

Tags: `#practical #claude-code #mcp #orchestration #cost-audit #eval #agent-team #orchestrator-worker`

---

## 1. The 3-model comparison harness — Astra vs Opus 5 vs Gemini 3.8 Flash {#1-astra-vs-opus5}

**Why now:** All three labs shipped 1M-context flagships or workhorses inside a two-week window, and the price bands are now materially different: **Opus 5 at $5/$25**, **Gemini 3.8 Flash at ~Flash-tier**, **Astra at $10/$50**. Without your own benchmark you cannot honestly recommend one — and that recommendation is the thing FDE interviews grill on.

**The harness (2–3 hours end-to-end):**

1. **Pick one real task from your portfolio.** Best candidates: an MCP-server exercise, the dual-model sanitiser from [May 20](../2026-05-20/03-practical-skills-and-tools.md), or a repo-level refactor. Bad candidate: a toy prompt — it won't tell you anything the leaderboards don't.
2. **Fix the inputs.** Same prompt, same system message, same tools available, same context size, temperature=0. Log everything you send.
3. **Run each model 3 times** (median, not one-shot). Capture: wall-clock latency, input tokens, output tokens, total cost, correctness (pass/fail against a rubric you wrote *before* seeing outputs).
4. **Add a fourth condition: "Astra Fast off + effort=medium"** — real-world Astra is often the medium-effort variant, not the maxed-out benchmark run.
5. **Write the readme** as if it's the takeaway slide of a $300K-TC interview: 1 chart (cost/task), 1 chart (time/task), 3 sentences on *when* to pick each, 1 line on your reproducibility caveat.

**Publish** to a public gist by Monday morning. Tag `#opus-5 #gpt-6-astra #gemini-3-8-flash` for grep-ability.

**Sources for benchmark comparability:**
- [Vellum — GPT-6 Astra Benchmarks Explained](https://www.vellum.ai/blog/gpt-6-astra-benchmarks-explained) `[analysis]`
- [OpenRouter — GPT-6 Astra Pricing & Benchmarks](https://openrouter.ai/openai/gpt-6-astra) `[secondary]`
- [Artificial Analysis](https://artificialanalysis.ai/) `[secondary]` — cross-model latency & pricing charts
- [Anthropic — Fable 5.1 launch](https://www.anthropic.com/claude-fable-and-mythos-5-1) `[primary]`

### Why it matters to you

- **Job lens:** This artifact answers **three FDE interview questions in one repo**: "how do you pick a model for a task," "how do you reason about cost/perf tradeoffs at scale," and "how do you communicate a technical recommendation to a non-technical buyer." OpenAI FDE, Anthropic Applied AI, and Deloitte-Anthropic-FDE (extends the [2026-07-25 §5](../2026-07-25/05-career-and-startup.md#2-fde-market)) all use variations of these questions.
- **Startup lens:** If your product routes across models, this **is** your unit-economics analysis. Founders who don't have one this week are quoting margins from June, which are stale.
- **Insight:** The **hardest part is the rubric, not the code.** Writing what "correct" means for your task before running the models is 60% of the interview value; the token-cost chart is a commodity.

→ Cross-link: [`04` §4 how to use eval harnesses for research replication](./04-research-progress.md#4-eval-methodology).

---

## 2. Claude Code September updates — enterprise MCP, headless permissions, smaller binary {#2-claude-code-updates}

**What shipped (this month):**

- **`managedMcpServers` managed setting** — an admin can push HTTP/SSE MCP servers to every user in the org through a single managed config. **Deploy this to your grad-school GitHub org** (or your personal `~/.claude.json`) tonight; a single working example is a resume line.
- **`--permission-prompts none`** — for unattended headless hosts (CI jobs, cron), any tool call that would normally prompt is **denied automatically**. Pair with an explicit allowlist to run Claude Code inside a GitHub Action safely. This is the flag your `babysit-prs` cron has been waiting for.
- **`timeFormat` / `timeZone`** — 12/24-hour, UTC, custom `strftime`. Small but useful — set to your local zone for readable logs.
- **Native binary zstd-compressed** — **340 MB → ~75 MB on Linux x64**. Faster CI installs, cheaper container layers. Just re-download.
- **Notable bug fixes** — concurrent sessions no longer silently revert each other's `~/.claude.json`; workspace trust + MCP/project state now preserved; remote sessions no longer stall 60 s on stale browser-hosted MCP page.

**Deploy checklist (30 min):**

- [ ] Update Claude Code (or `brew upgrade` / equivalent) — confirm the new binary size (should be ~75 MB).
- [ ] Add one HTTP MCP server behind `managedMcpServers` — try your own MCP server or a public one (see the MCP registry).
- [ ] Add `--permission-prompts none` + a scoped `--permission-mode allow` to one CI job you own.
- [ ] Set `timeFormat` + `timeZone` to your local zone.

**Sources:**
- [Claude Code — Official Changelog](https://code.claude.com/docs/en/changelog) `[primary]`
- [Claude Code Changelog (September 2026)](https://www.gradually.ai/en/changelogs/claude-code/) `[aggregator]`
- [Claude Code Updates (Releasebot)](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`

### Why it matters to you

- **Job lens:** `managedMcpServers` is *directly* a Solutions/FDE deployment surface — this is now the shortest path to a portfolio demo that reads "enterprise-ready." Ship one and screenshot the admin setting.
- **Startup lens:** If you sell an MCP server as a product, you now have **one-config org-wide install** — write that up in your enterprise marketing.
- **Insight:** The **340→75 MB compression** is a hint about how Anthropic thinks about developer experience — they were willing to spend an eng-week on binary size because CI installs are the friction point they hear about. If you want to work at Anthropic on Claude Code, know that story.

---

## 3. Sonnet 5 promo ended Aug 31 — mandatory cost re-audit {#3-sonnet-repricing}

**What changed:** Sonnet 5's **promotional pricing of $2 / $10 per MTok ended Aug 31, 2026**; standard **$3 / $15** is now live (Sept 1 onward). Any prod bill built assuming the promo is now materially higher.

**Do this today (60 minutes):**

1. **Pull August's Anthropic bill** and pin the Sonnet 5 line-item as your baseline.
2. **Estimate September:** input tokens × $3/M + output × $15/M. Compare to August. If you're within 20% of a hard budget line, you have a problem tomorrow, not next quarter.
3. **Route decision table:**
   - **Reasoning-heavy planning subtasks** → Fable 5.1 (`effort=medium` if available; the cache-read cut to $0.25/MTok makes this cheaper than it was in July).
   - **Structured tool use / short-form generation** → Sonnet 5 at the new price (still the best price/quality for this).
   - **High-volume cheap chunking / classification** → Haiku 4.5 (or Gemini 3.8 Flash if you're comfortable cross-vendor).
4. **Turn on prompt caching** everywhere it wasn't on (the highest-ROI mitigation, first flagged in [2026-05-17](../2026-05-17/03-practical-skills-and-tools.md); still true, and Fable 5.1's cache reads are 75% cheaper than before).

**Sources:**
- [Anthropic — September 2026 Release Notes (pricing)](https://releasebot.io/updates/anthropic) `[aggregator]`
- [Anthropic — Fable 5.1 launch (cache-read pricing)](https://www.anthropic.com/claude-fable-and-mythos-5-1) `[primary]`

### Why it matters to you

- **Job lens:** A one-page **"Sonnet 5 promo-off cost audit"** on your GitHub is the most credible signal you can send to an Applied AI / FDE hiring manager that you understand real deployment economics — not just prompt engineering. Publish it.
- **Startup lens:** This is your **monthly-4th cost audit** ([per ME.md](../ME.md)), forced early. Do it, then re-run every startup projection you had that assumed Sonnet 5 promo economics.
- **Insight:** Promo-to-standard is a **specific class of cost shock** that founders under-model. The lesson to internalize: any product built on a "launch price" carries **a 20–100% margin risk** at some future date. Bake it into your default gross-margin planning.

---

## 4. This weekend's artifact — the one thing to ship {#4-this-weekends-artifact}

**Ship the 3-model comparison** (§1) as a public gist tonight, and **link it into your LinkedIn** tomorrow. That's the whole ask. Do not over-scope it — 5 tasks × 3 models × 3 runs × 3 hours of writeup is enough.

If you finish early:

- Bolt on **Astra Fast mode** as a 5th column — it's 2× the cost and (per OpenAI) faster; is it worth it on your task?
- Bolt on **Sonnet 5 at new pricing** as a 6th column — is it now dominated by Fable 5.1 for your workload?

The publishing act is the point. Even a 5-task comparison beats *no* comparison.

---

## 5. Skill re-price: what got scarcer this month {#5-skill-reprice}

- ⬆️ **Model-comparison methodology** — every hiring manager needs to know if Astra's benchmark saturation replicates on their workload. Own the vocabulary.
- ⬆️ **Customer-tenant telemetry design** — EFS created the surface; nobody is fluent yet.
- ⬆️ **Effort-adaptive routing** — the [`effort` toggle](../2026-07-25/03-practical-skills-and-tools.md) plus the Astra `Fast` toggle plus the Fable cache economics means router design is a 2-dimensional problem now.
- ⬇️ **Prompt-only engineering** — commoditized; the differentiation moved down the stack.
- ⬇️ **"Wrapper" positioning** — startup-side; if your resume says "I built a Claude/GPT wrapper" without a defensible eval, remove it.

---

*Continued: research and arXiv signal in [`04-research-progress.md`](./04-research-progress.md).*
