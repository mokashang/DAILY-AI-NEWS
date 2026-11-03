# Practical Skills & Tools — 2026-11-03

The week has a **hard migration deadline** (Opus 4.8 fast-mode retires Nov 30), a **new API primitive** (beta message threads), a **named artifact to ship** (cost-per-deployment calculator), and the **ongoing vertical-MCP-server lane** — carried forward from the Nov-1 edition because the field is still open, and the Warren letter + Bloomberg $895B framing just made "cost-per-deployment" the hirable framing of Q4.

Tags: `#practical #opus #sunset #api #threads #cost #mcp #portfolio`

---

## 1. Opus 4.8 fast mode retires Nov 30 — audit tonight, migrate this week {#1-opus-48-sunset}

**What happened (2026-11-02, Claude Developer Platform release notes):** Anthropic's release notes announced that **fast mode for Claude Opus 4.8 will be removed on 2026-11-30**, and users should migrate to **Claude Opus 5.5**. This is the first forced-migration deadline since the API `2026-10-21` cutover ([2026-11-01/03 §1](../2026-11-01/03-practical-skills-and-tools.md)); it is explicit (specific sunset date, specific migration target) rather than deprecation-with-grace-period.

**What migration involves (expected based on the Oct-21 cutover + Opus-release-notes pattern):**

- **Model id swap:** `claude-opus-4-8` → `claude-opus-5-5` in every pinned agent, Claude Code CLI config, `CLAUDE.md`, GitHub Actions workflow, and MCP tool definition.
- **Fast-mode parameter: effort levels.** Opus 5.5 uses the configurable **effort-level** API introduced with Haiku 5.5 ([2026-10-14/03 §1](../2026-10-14/03-practical-skills-and-tools.md)) in place of the earlier binary `fast: true`. Audit each call site and swap `fast: true` for the matching effort level — `low` for the previous fast-mode behavior, `medium` for default, `high` or `max` for extended-thinking paths.
- **Cost delta:** Opus 5.5 is on the API at the Nov pricing table (checking the Anthropic pricing page in the next step is required; the Nov-2 edition framed Opus 5.5 as a 2–4× premium over Haiku 5.5 / Terra / K3.1 — ensure the budget supports a model-tier audit at the same time as the sunset migration).
- **Cache compatibility:** Opus 5.5 continues the cache-read discounts introduced with Fable 5.1 / Mythos 5.1 in Sept ([2026-09-10](../2026-09-10/00-tldr.md)). Prompt caching on Opus 4.8 workloads should migrate transparently — but verify the cache-key behavior in a 1-case test before relying on it in production.

**Audit checklist (tonight):**

```bash
# Repo-wide find for pinned model ids
grep -rE 'claude-opus-4-?8|opus-4\.8' .

# Audit Claude Code config
cat ~/.claude/settings.json | jq '.model'
cat CLAUDE.md | grep -i opus

# Any GitHub Actions, Makefiles, Dockerfiles, scripts
grep -rE 'opus-4-8|opus-4\.8' .github/ scripts/ Dockerfile* Makefile* 2>/dev/null

# Any MCP server tool descriptions mentioning the model (rare but check)
grep -r 'opus-4-8' $(find . -name 'mcp.json' -o -name 'tools.json')
```

**Sources:**
- [Releasebot — Anthropic Release Notes (Nov 2026)](https://releasebot.io/updates/anthropic) `[aggregator]`
- Cross-ref: [Anthropic — Model Deprecations Policy](https://docs.claude.com/en/docs/about-claude/model-deprecations) `[primary]` — always verify the sunset date against the official deprecations page.
- Prior cutover: [2026-11-01/03 §1 API 2026-10-21 cutover](../2026-11-01/03-practical-skills-and-tools.md).

### Why it matters to you

- **Job lens:** The migration itself is **a 2-hour task that writes a 500-word portfolio note**. Title the writeup: "Migrating a pinned Opus-4.8 agent to Opus-5.5 with effort-level routing (before Nov 30)." Publish on your blog + LinkedIn + a Claude Code `/skills` entry. **Why this specific writeup:** it signals three things to an FDE / Applied AI interviewer at once — (a) you follow release notes, (b) you understand model-tier routing, (c) you ship.
- **Startup lens:** If your startup has pinned agents on Opus 4.8, the migration is a **gross-margin event, not just an engineering task** — effort-level routing can cut costs materially on the paths that don't need `high`/`max`. **Run the pre/post cost comparison and publish the delta** (anonymised numbers if the raw numbers are commercially sensitive); it's a cheap but under-indexed piece of founder credibility.
- **Insight:** Model sunsets are now **quarterly events** — Haiku 4.5 → 5.5 in Oct, Opus 4.8 → 5.5 by end of Nov, API version cutover in late Oct, with Gemini 4 Carbon and GPT-6.1 Terra pricing resets layered on top. **The hirable skill is not "stay current on model names" — it is "run a sunset migration without downtime."** The résumé line is: "ran N migrations through sunset, D-days-ahead, zero regression." That's the kind of line that converts a recruiter screen into a loop.

→ Cross-link: [2026-10-14/03 §1 Haiku 5.5 effort levels](../2026-10-14/03-practical-skills-and-tools.md) · [2026-11-01/03 §1 API cutover](../2026-11-01/03-practical-skills-and-tools.md).

---

## 2. Beta message threads landed in the Claude Developer Platform (Nov 2) {#2-beta-threads}

**What happened (2026-11-02):** Anthropic shipped **beta message threads** in the Claude Developer Platform API — a server-managed primitive that holds conversation state (multi-turn history, tool calls, selective tool-result caching) under a thread id, callable through the Messages API without client-side orchestration.

**What it changes:**

- **Memory layer is now a flag, not a layer.** The previous shape — `redis` or `mem0` or a bespoke SQLite layer in your agent code — is replaceable by a `thread_id` parameter on the Messages API. For many agents, that means **~200–500 LOC of memory-plumbing code becomes a one-line param**.
- **Caching behavior is standardized.** Thread-managed caching composes with prompt caching; the net effect for a multi-turn tool-using agent is **better cache-hit rates with less cache-key engineering**.
- **The portfolio-moat on "memory engineering" just dropped.** The résumé line "I built the memory system for a multi-turn agent" is now less differentiated — the native primitive did a lot of what that line used to signal.

**What you should ship this weekend:**

- **A thread-aware eval harness.** Pick an existing eval (BizAgentBench's 601-tool corpus — see [2026-11-01/04 §1](../2026-11-01/04-research-progress.md) — or AgentLens, or Toolathlon from the May-22 edition). Rewrite the harness to use thread ids. Measure: (a) tokens / task vs client-managed memory, (b) cache-hit % vs client-managed, (c) failure modes (does the server-managed thread drop context in a way the client-managed version wouldn't?). **Publish the numbers.** That is the new memory-engineering portfolio artifact.

**Sources:**
- [Releasebot — Anthropic Release Notes (Nov 2026)](https://releasebot.io/updates/anthropic) `[aggregator]`
- Cross-ref: [Anthropic — Messages API docs](https://docs.claude.com/en/api/messages) `[primary]` — verify the exact parameter name (`thread_id` or similar) and beta-header requirements before deploying.
- Memory-landscape baseline: [2026-05-10](../2026-05-10/) (Mem0 + EverMemOS) · [2026-09-10](../2026-09-10/00-tldr.md) ("Memory in the Age of AI Agents" arXiv 2512.13564).

### Why it matters to you

- **Job lens:** **Native primitives are hiring-signal reversers**: as soon as a lab ships a native memory primitive, the "I built memory" interview answer loses points unless it's paired with a thread-vs-custom A/B. The hirable framing is now **"I benchmarked native threads against our in-house memory layer and ran the migration" or "I shipped a thread-aware eval harness that other teams in the org adopted."** For a new grad: this is the single highest-leverage weekend write-up of November.
- **Startup lens:** For startups whose moat was partly "we built the memory layer so you don't have to," native threads are a **product-strategy inflection**. The response is not to compete on memory, it's to compete on **memory + policy + attribution**. Memory is now the floor; the differentiated moat is "which turn of the conversation is responsible for which tool call outcome, and under which policy did we allow it." (That's where VETTA and the agent-security papers in [`04`](./04-research-progress.md) point.)
- **Insight:** Three native primitives have landed in the Anthropic developer surface in 60 days — effort levels (Oct 7), API 2026-10-21 cutover (Oct 21), beta threads (Nov 2) — each flattening a different custom-code layer. **The pattern: the native primitive beats the custom code when the native primitive composes with 2+ other primitives.** For a candidate reading the market: the roles that are getting easier are the "build the plumbing" roles; the roles that are getting harder (and better-paid) are the "compose the plumbing primitives into an agent that scales to a specific deployment" roles. **That's FDE.**

→ Cross-link: [2026-10-14/03 §1 Haiku 5.5 effort levels](../2026-10-14/03-practical-skills-and-tools.md) · [2026-11-01/03 §1 API cutover](../2026-11-01/03-practical-skills-and-tools.md) · [`04` §1 Agent-security papers](./04-research-progress.md#1-agent-security).

---

## 3. Weekend artifact — the cost-per-deployment calculator {#3-cost-per-deployment}

**Why ship this specific artifact this week:** Bloomberg's $895B / $17B framing didn't price capability — it priced **capital intensity per deployment**. Which means: **the next FDE / Applied AI interview will test whether you can quantify cost-per-deployment-at-scale**. Shipping a cost-per-deployment calculator this weekend puts you in front of the question before you're asked.

**Scope (4-hour version):**

- **Inputs:** model tier (Opus 5.5 / Sonnet 5.5 / Haiku 5.5 / GPT-6.1 Terra / Kimi K3.1 Pro / Mistral Large 4) × effort level (`low` / `medium` / `high` / `max`) × tokens in/out per task × tasks/day × cache-hit rate.
- **Outputs:** $ / day / deployment, $ / month, $ / 1M-task, and a *marginal* cost-per-task table that compares the current tier against the next-cheaper tier and the next-more-capable tier.
- **Scenarios bundle (ship these as presets):**
  - **Dev-tool agent** (code-gen heavy, Opus 5.5 at `medium`, 5K/5K tokens, 500 tasks/day).
  - **Browser-use subagent** (Haiku 5.5 at `low`, 2K/0.5K tokens, 2K tasks/day).
  - **Enterprise RAG+tool-call agent** (Sonnet 5.5 at `high`, 10K/2K tokens, 300 tasks/day).
  - **Multi-agent FDE deployment** (Opus 5.5 planner + Haiku 5.5 workers, mixed, 1K planner + 10× worker calls per task).
- **The one row that makes it interview-ready:** a **"frontier-vs-open-weight"** comparison row that prices a 70/30 workload (70% open-weight self-host via Mistral Large 4 / K3.1 Pro / Haiku 5.5, 30% frontier Opus 5.5 / Terra / Gemini 4 Carbon) against a 100% frontier baseline. This is the row every founder and every enterprise pricing team is actively looking at right now ([2026-11-02/02 §1 open-weight pincer](../2026-11-02/02-new-emerging.md)).

**Delivery format:**

- `calculator.html` with a `<form>` + inline JS; no server dependency; renders in Claude.ai as an Artifact and in a browser as a static page.
- Companion `README.md` with the pricing table dated **as of 2026-11-03** and a "last-verified" line pointing at each lab's pricing page.
- Companion `pricing.json` so the calc can be driven by a config file. **This is the file you'll update every time a lab reprices.**
- GitHub repo, MIT license, 3-sentence Simon-Willison-style blog post explaining the methodology, link in the README of your main portfolio.

**Why this specific artifact wins the interview:**

- It demonstrates **cost-model fluency** (the Nov-3 reprice).
- It demonstrates **model-category fluency** (effort levels, model-tier routing).
- It demonstrates **open-weight-vs-frontier fluency** (the 70/30 row).
- It is **owned content** (yours, published, Google-indexable, discoverable from your name).
- It takes 4 hours — not 40 — and ships this weekend.

**Reading list for the pricing figures (per-lab):**

- Anthropic: pricing page + Opus 5.5 release notes.
- OpenAI: GPT-6.1 Terra ($1 in / $5 out per 1M, cached $0.10) and Sol ($2 / $10) + Astra ($4 / $20).
- Google: Gemini 4 Argon ($2 / $10 intro), Carbon ($4 / $20 standard, Fairwind-only — list as "limited access").
- Moonshot: Kimi K3.1 Pro ($2 / $10).
- Mistral: Large 4 "Le Chonk" (list the self-host cost; use the Hugging Face FP8/NVFP4 inference prices and the AWS GPU-hour rate).

**Sources:**
- Model-pricing baseline from [2026-11-02/00 tldr](../2026-11-02/00-tldr.md) + [2026-11-01/00 tldr](../2026-11-01/00-tldr.md).
- [OpenAI — Pricing page](https://platform.openai.com/docs/pricing) `[primary]` (verify Terra and Sol rates before publishing).
- [Anthropic — Pricing page](https://www.anthropic.com/pricing) `[primary]`.
- [Google — Gemini models pricing](https://ai.google.dev/gemini-api/docs/pricing) `[primary]`.

### Why it matters to you

- **Job lens:** This is the single highest-leverage interview artifact of November. **The explicit interview-question-of-record for Q4 2026 Applied AI / FDE loops is "how would you cost a deployment at X scale?"** — and the correct answer is "here is the calculator I built, let's walk through it." Being able to say that in minute 20 of a loop is the 2026 equivalent of saying "I wrote a transformer from scratch" in 2021.
- **Startup lens:** A hostable version of the same calculator is a **lead-magnet** — any enterprise AI buyer searching for cost-per-deployment math lands on your page, you capture the email, you have an outbound-sales queue. Not a startup in itself, but a founder-credibility piece.
- **Insight:** Cost-model artifacts are a **meta-skill signal** — they prove you've thought about the second-order economics of what you build, not just the first-order feature. **Which, after Bloomberg's $895B framing, is the thing the market most needs to see.**

→ Cross-link: [2026-11-02/03 §2 Router v3 artifact](../2026-11-02/03-practical-skills-and-tools.md) · [`01` §1 Bloomberg $895B](./01-big-lab-moves.md#1-bloomberg-895b) · [`02` §1 Industrial AI (cost model row for the 70/30 wedge)](./02-new-emerging.md#1-industrial-ai).

---

## 4. The vertical-MCP-server lane is still open — carry-forward from Nov 1 {#4-vertical-mcp-still-open}

**Context (from [2026-11-01/03 §5](../2026-11-01/03-practical-skills-and-tools.md)):** The MCP Registry crossed 47,267 registered servers (Oct 21). Financial Cents shipped the first vertical-SaaS MCP server for accounting firms (Oct 20). **No MCP-first company in YC W26.** The field is still open for **legal practice management, dental, logistics/TMS, real-estate CRM, municipal records**, and now — new as of this edition — **industrial MES/CMMS, plant-floor historian systems, warehouse WMS**.

The Nov-1 edition proposed a 4-hour MCP-server ship as the weekend artifact. **If you did not ship it last weekend, prioritize it this weekend** — the cost-per-deployment calculator (`03` §3) is a 4-hour build and can share the day. **Ship the MCP server first, then publish the calculator.**

### Why this is still the top priority

- **Job lens:** [2026-11-01/05 §2 apply-plan](../2026-11-01/05-career-and-startup.md) names Deloitte Associate GenAI (May 2025 – May 2026 grads, Summer 2026 start) and Anthropic Applied AI Engineer, Enterprise (Oct 20). Both roles will see **shipped MCP servers in the applicant pool by Thanksgiving** — being the first one to ship + submit to AAIF (Agent Skills) still differentiates, but the window is 30–45 days, not 90.
- **Startup lens:** The vertical MCP-server is the **cheapest-to-build startup wedge** of Q4 ([2026-11-01/05 §2](../2026-11-01/05-career-and-startup.md)). The industrial / plant-floor vertical from `02` §1 adds a new target list; the earlier legal / dental / logistics / real-estate target list from the Nov-1 edition is still open.
- **Insight:** Every unshipped artifact is a résumé line that someone else is going to ship first. **This weekend you have two 4-hour artifacts to ship. Choose a vertical for the MCP server, ship both, and both go into your Dec portfolio refresh.**

→ Cross-link: [2026-11-01/03 §5 AWS Labs MCP + vertical lane](../2026-11-01/03-practical-skills-and-tools.md) · [2026-11-01/02 §3 MCP ecosystem](../2026-11-01/02-new-emerging.md) · [`02` §1 industrial-AI vertical](./02-new-emerging.md#1-industrial-ai).
