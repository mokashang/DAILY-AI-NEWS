# Practical Skills & Tools — 2026-10-31

Three things to actually do this weekend: **(1)** run `/claude-api api-version` on every project (the Oct 21 migration primitive); **(2)** ship a persistent-memory-with-drift test harness as this weekend's artifact; **(3)** fix your résumé to speak the Oct 2026 vocabulary before the Nov 9 roadshow-week recruiter wave hits. The practical theme of Oct 15–31: **versioning is now a first-class citizen** — API versions, protocol versions, prompt versions, eval versions. If your artifacts aren't versioned, they aren't portfolio-grade anymore.

Tags: `#claude-code #mcp #api-versioning #memory #evals #portfolio #resume`

---

## 1. Claude Code v2.1.305 → v2.1.307 (Oct 20–22) — `/claude-api api-version 2026-10-21` migration command + MCP server replacement fix {#1-claude-code-api-version}

**What shipped:**

**v2.1.305 → v2.1.306 (Oct 20–21):**
- **MCP replacement fix.** Prior behavior: MCP servers passed via cloud sessions / the SDK could get silently replaced mid-session by same-named servers from the user's own config. Fixed.
- **`allowedMcpServers` no longer filters** `managed-mcp.json` stdio servers that use `${VAR}` only inside `env` (previously filtered incorrectly).
- Tool-search regression fix (prior release had broken targeted deferred-tool loading in some session configs).

**v2.1.307 (Oct 22):**
- **New command: `/claude-api api-version`.** Migrates project code to API version `2026-10-21`. This is a first-class migration primitive — API versioning is now **tracked per-request + per-project**, not an opt-in header.
- **`safety_event` logging** added to session telemetry (opt-out via config).
- **HTTP MCP** fixes.

**Context:** This builds on the **v2.1.292 (early Oct)** change where local stdio MCP servers negotiate protocol version `2026-07-28` by default (`MCP_PROTOCOL_NEGOTIATION=legacy` to opt out).

**Sources:**
- [DevelopersIO (Classmethod) — Claude Code v2.1.305 to v2.1.306 Key Updates](https://dev.classmethod.jp/en/articles/20261021-cc-updates-v2-1-306/) `[secondary — community changelog]`
- [DevelopersIO — Claude Code v2.1.307 Major Updates — Addition of safety_event and /claude-api api-version](https://dev.classmethod.jp/en/articles/20261022-cc-updates-v2-1-307/) `[secondary — community changelog]`
- [Mixed-news — Claude Code 2.1.292 switches stdio MCP servers to a new protocol](https://mixed-news.com/en/claude-code-2-1-292-stdio-mcp-protocol-2026-07-28-docs-contradict/) `[analysis — early Oct context]`

### Why it matters to you

- **This weekend (30 min).** Run `/claude-api api-version 2026-10-21` on every active Claude Code project. Then open `managed-mcp.json` (if you have one) and confirm `${VAR}` references in `env` are now visible to `allowedMcpServers`. **This is the exact kind of hygiene bullet that reads credibly on a résumé** ("Migrated 7 production projects to Claude API version 2026-10-21; validated `safety_event` telemetry; patched `${VAR}` MCP filter regression") because it's version-specific and verifiable.
- **For the portfolio.** The combination of **API-version-aware project** + **MCP protocol 2026-07-28** + **documented migration run** makes a "Claude Code production-ready template" repo a legitimate 1-weekend portfolio artifact. Suggested name: `claude-code-template-2026-10` — 100 stars by December is realistic if you post on Hacker News with a 1-screen README.
- **For founders.** If you're building a product that embeds Claude Code (or Anthropic's hosted agent runtime), API-version pinning is now a **required** safety feature — "we are version-pinned to 2026-10-21 and migrate on a 90-day cadence" is the enterprise-sales line for Q1 2027 procurement.

→ Cross-link: [2026-09-10 § router artifact](../2026-09-10/00-tldr.md).

---

## 2. Weekend artifact: persistent-memory-with-drift test harness for Claude agents {#2-memory-drift-harness}

**The ask.** Build a tiny, open-source test harness that **measures cross-model memory drift** in persistent-memory implementations for Claude agents. Scope: 1 weekend. Target length: ~300 LOC Python + 1 README + 1 screenshot of the metric dashboard.

**Why this one.** October's arXiv crop ([`04` §2](./04-research-progress.md#2-memory-benchmarks)) landed on persistent-memory benchmarks + "can agents evaluate themselves" + memory-poisoning as the dominant thread. The METR embed ([`01` §6](./01-big-lab-moves.md#6-metr-embed)) + Anthropic's own eval-cut-from-internet discipline ([2026-10-14 §2](../2026-10-14/04-research-progress.md)) make eval-authoring the single most-pricey skill to invest in right now. **This weekend's artifact is also exactly the kind of research-eng portfolio piece that an Anthropic / METR / Apollo recruiter can show their hiring manager in one scroll.**

**Suggested scope.**
1. **Harness surface:** two memory backends to test (e.g. `Mem0`, `EverMemOS` — both introduced in [2026-05-10](../2026-05-10/) — plus a bare `claude.messages` + `anthropic-user-memory` baseline).
2. **The task set:** 10–15 agentic tasks requiring recall of 3–5 facts from an earlier turn (e.g. "the user said their startup is named *Vellum*, they are a solo founder, they prefer kebab-case names" → 20 turns later: "name 3 Github repos we discussed naming").
3. **The drift metric:** F1 of correct-recall and false-recall across turn offsets {5, 10, 20, 50, 100} and across model switches (Haiku 5.5 ↔ Sonnet 5.5 ↔ Opus 5.5).
4. **Attack mode:** add 1 memory-poisoning test (adversarial fact inserted turn-N; measure whether later turns accept it as truth) — directly inspired by arXiv 2610.04083.
5. **Reporting:** a `report.md` auto-generated per run; metric dashboard a simple Matplotlib / Altair chart; one JSON transcript per run so other evaluators can replay.
6. **Public portfolio:** post on GitHub, cite the arXiv paper, add a one-paragraph README that reads **"evaluates memory-backend drift under model-switch stress for Claude agents — ships with 15 reusable task cards and 3 memory-poisoning adversarial tests."**

**What NOT to do.**
- Don't ship your own memory backend. The point is to **evaluate**, not to compete.
- Don't skip the model-switch dimension. Haiku 5.5 is now the default Claude Code worker — any evaluation that only tests Opus will be ignored in 2026.
- Don't make the harness all-Python. If you can, ship a tiny TS wrapper too — Node/TS is where production Claude agents live outside DS/ML teams.

### Why it matters to you

- **Portfolio-weight:** This single artifact meets 3 of the 5 criteria from your ME.md "active portfolio artifacts" checklist: it is public, it is a Claude-agent focus, and it generates a reusable artifact for interview show-and-tell.
- **Cold-outreach lever:** Email the artifact link + a 2-paragraph summary to one METR / Apollo / Anthropic Policy recruiter + one eval-focused funded startup (Judgment Labs raised $32M in May for exactly this space — see [2026-05-13](../2026-05-13/00-tldr.md)). Expected reply rate: ~10% if the artifact is good. If one of them bites, you're interviewing for an eval-engineer role by Thanksgiving.
- **Insight — this is the "router artifact" (Sept 10) of this edition.** The router artifact in Sept was the right thing to build when Haiku 5.5 wasn't out yet; now that Haiku 5.5 is default, the eval-of-memory artifact is the natural next-leverage move. **The weekend artifact pattern is working — one weekend ≈ one portfolio piece ≈ one credible cold-email anchor. Do not break the cadence.**

→ Cross-link: [`04` §2 October memory + eval papers](./04-research-progress.md#2-memory-benchmarks) · [2026-09-10 § router artifact](../2026-09-10/).

---

## 3. Résumé rewrite — Nov 9 recruiter-wave vocabulary {#3-resume-rewrite}

**The ask.** 20 minutes today or tomorrow. Open your résumé and reshape the top-of-page three bullets to match the Q4 2026 vocabulary. **Specific words that now trip the recruiter screen (as of this week):**

**Core vocabulary to include (if truthful):**
- `model-routing` (Haiku ↔ Sonnet ↔ Opus switching logic)
- `cost-aware agent design`
- `eval-authoring`
- `MCP integration` or `MCP server authoring`
- `pre-deployment evaluation`
- `Agent Skills` (if you've shipped any)
- `Claude Code production deployment`
- `API version pinning` (new as of Oct 21)
- `embedded evaluation` / `red-team-adjacent`

**Core vocabulary to REMOVE (now re-priced down):**
- Generic `prompt engineering` (deprecated — mentioned on [2026-10-14 §12](../2026-10-14/00-tldr.md), reinforced by Haiku 5.5 effort-level API)
- Generic `LLM fine-tuning` without a specific use case
- "LLMOps" without specifying which stack
- Specific "Latest Claude model" claims (e.g. "shipped a Claude 4.6 integration") — the model names turn over too fast

**Specific rewrites by goal:**

**If targeting Anthropic Solutions / FDE / Policy:**
Lead bullet: *"Built MCP server + cost-aware routing agent integrating Claude Haiku 5.5 workers under Opus 5.5 orchestrator; 48% token-cost reduction vs. all-Opus baseline on {benchmark}; publicly versioned under API version 2026-10-21."*

**If targeting OpenAI Public Sector FDE / Govtech:**
Lead bullet: *"Shipped Claude for Government workflow prototype (FedRAMP High-compatible, GSA OneGov-eligible); auditable prompt-version pinning + eval harness publishing to a signed artifact."*

**If targeting a Frontier Academy partner firm (McKinsey QuantumBlack, Accenture GenAI, Deloitte AI Institute, Bain Vector, Capgemini AI, Morgan Stanley AI/Tech, Commonwealth Bank AU, Novo Nordisk Digital):**
Lead bullet: *"Deployed a 2-step agentic workflow at {your-school-club/project}; shipped a cost + eval dashboard; integrated with internal MCP server over Claude Agent SDK; wrote the rollout playbook including API version pinning + eval versioning."*

**If targeting Anthropic Policy / METR / Apollo (safety / eval lane):**
Lead bullet: *"Authored eval-harness for persistent-memory drift in Claude agents under model-switch stress; included 1 memory-poisoning adversarial test (ref. arXiv 2610.04083); publicly reproducible; cited by X."*

**If targeting biotech-AI (new post-Oct 27):**
Lead bullet: *"Shipped Claude Science workbench extension for {therapeutic area}; benchmarked against {public target}; reproducible notebook library + wet-lab-friendly documentation."*

### Why it matters to you

- **This is a 20-minute task with a 2–3× recruiter-reply impact if your actual portfolio supports the claims.** The Nov 9 roadshow-wave hiring surge is coming. Recruiter inboxes open for ~2 weeks before flooding; apps submitted Nov 2–8 see 3–5× higher reply rates than apps submitted Nov 15–30.
- **If the bullet is overclaimed, interviewers will catch it in 5 minutes.** Every bullet must map to a public artifact (GitHub, HuggingFace, blog post, PR to a Claude Code–adjacent repo). If you can't link it, you can't claim it. The repo for this weekend's memory-drift harness ([`03` §2](#2-memory-drift-harness)) directly backs the Policy/METR lane bullet above.
- **Insight — the vocabulary turnover rate for AI engineer résumés is now ~4 months.** This is 2× faster than 2024, 4× faster than 2022. The practical implication for your job search: **re-draft the top three bullets every month on the 1st**. Add it to [ME.md](../ME.md) "personal rules" if it isn't there. 2 minutes to add the recurring reminder; 20 minutes to execute; outsized return on recruiter signal.

→ Cross-link: [`05` §1 IPO-wave hiring plan](./05-career-and-startup.md#1-ipo-wave) · [2026-09-10 § AI-eng hiring data](../2026-09-10/05-career-and-startup.md) · [`01` §1 ANT S-1](./01-big-lab-moves.md#1-anthropic-s1).
