# Practical Skills & Tools — 2026-11-11

Six hands-on items you can act on this week. **Theme:** model-choice is now a 4-dimensional tunable (model × effort × fast-mode × cache state), MCP is maturing from "wrap an API" to "stateful + bounded + audited," and Anthropic's Skills / Plugins / Connectors just merged — Enterprise admins have **19 days** to flip Skills ON before Claude Desktop plugins stop working (Nov 30 cutover).

Tags: `#practical #claude-code #mcp #skills #plugins #router #caching #effort-levels #fast-mode`

---

## 1. Skills → Plugins merger: Enterprise admin cutover Nov 30, 2026 {#1-skills-plugins}

**What:** Anthropic is folding **Skills, Connectors and Plugins** into a single **Plugins page** in Claude. Enterprise org admins **must flip "Skills = ON" by Nov 30, 2026** or lose plugins in Claude Desktop. Free / Pro / Max / Team / Ultra started rollout **Oct 29**.

**How to enable:**
- Admin → Organization settings → **Features** → enable **"Skills"** and **"Plugins".**
- Install from **`@anthropics/skills`** marketplace, or drop folders into **`~/.claude/skills/`**.
- Each skill = a folder with `SKILL.md` + optional scripts / resources. Claude loads only when relevant (composable).

**Pricing math (skill cost savings):** A single swap of "always-on 8K instructions in system prompt" → on-demand 2K-token skill saves **$0.80/day** at 100 Sonnet 5.5 calls (8K × 100 × $1/1M = $0.80). Over a year, one skill ≈ **$290 saved per 100-call-daily account.**

**Sources:**
- [Anthropic — Introducing Claude Skills](https://www.anthropic.com/news/skills) `[primary]`
- [Anthropic Support — Skills / Plugins tab consolidation](https://support.claude.com/en/articles/17740565) `[primary]`
- [VentureBeat — Anthropic launches Enterprise Agent Skills, opens the standard](https://venturebeat.com/ai/anthropic-launches-enterprise-agent-skills-and-opens-the-standard) `[secondary]`
- [The Decoder — Claude auto-picks prompts for specialized tasks](https://the-decoder.com/anthropic-launches-skills-so-claude-can-automatically-pick-prompts-for-specialized-tasks/) `[secondary]`

Tags: `#skills #plugins #anthropic #enterprise #admin #deadline`

### Why it matters to you
- **Job lens:** If your target FDE / Integration Engineer roles include **Enterprise-tenant work**, knowing the Nov 30 cutover is literal interview-prep. Add to cover letter: **"Yes, I've migrated an org from pre-merger Connectors to post-merger Plugins."** Even a one-tenant test counts.
- **Startup lens:** Skill authoring is **the new SDK distribution channel** — ship a skill, not a wrapper library. Market: 5–10K potential customers per skill if it fills a real workflow gap. Pattern: pick one vertical workflow you understand (billing audit? MCP server bootstrapping? eval-suite scaffold?), ship the skill, charge $29/mo / tenant if it's good.
- **Insight:** Anthropic unifying Skills + Connectors + Plugins into one surface = **"the agent framework is the operating system"** reading hardens. Microsoft is doing the same with Autopilot + Code + Home (see [`01` §5](./01-big-lab-moves.md#5-microsoft-copilot)). OpenAI did it with DevDay 2026. Three OS-shell theses running.

### ACT THIS WEEK
→ **Today:** Check your Claude org settings. If you don't own the tenant, ping the admin. **Ship one personal skill** (e.g., `router-haiku-starter.md` or `mcp-server-scaffold.md`) to `~/.claude/skills/`, **screenshot it loading on-demand**, and add the screenshot + folder structure to your portfolio README.

---

## 2. Claude Code v2.1.317 (Nov 2) — Agent SDK blocking hooks + per-gateway cost reports {#2-claude-code-2-1-317}

**What:** v2.1.317 adds Agent SDK hooks that **block on failure** — a pre-tool hook returning non-zero **halts the agent** (previously only warned) — plus **cost reports for gateway admins** showing per-team / per-user spend. **v2.1.318 followed Nov 3.** Platform release notes also deprecated **Opus 4.8 fast mode (removal Nov 30).**

**How:**
```bash
# Upgrade
claude --version   # confirm you see ≥ v2.1.317
# otherwise:
claude self-update

# Example blocking PreToolUse hook (.claude/settings.json)
{
  "hooks": {
    "PreToolUse": {
      "command": ".claude/hooks/no-write-outside-repo.sh",
      "blocking": true
    }
  }
}

# Gateway cost report
claude gateway stats --by user --window 7d
claude gateway stats --by team --window 30d --format csv
```

**Pricing math:** Gateway cost reports expose previously-hidden over-spenders. In a 10-person team, a single runaway user on Opus 4.8 can consume **$300–600/day** vs the **$30/day median** — the report pays for itself the first week it surfaces one.

**Sources:**
- [Claude Code — November 2026 Releases (havoptic)](https://www.havoptic.com/releases/claude-code/2026/11) `[aggregator]`
- [Platform API release notes](https://platform.claude.com/docs/en/release-notes/api) `[primary]`
- [Claude Agent SDK v0.2.84 — API-side token budgeting](https://gentic.news/article/claude-agent-sdk-v0-2-84-adds-api) `[analysis]`

Tags: `#claude-code #hooks #gateway #cost-controls #sdk #opus-4-8-deprecation`

### Why it matters to you
- **Job lens:** **Interview exhibit:** a `.claude/hooks/README.md` that documents one blocking policy (e.g., "deny writes outside $CLAUDE_PROJECT_DIR") is a portfolio piece. Pair it with a one-paragraph incident story: "Prevented an agent from writing to `~/` during a long-running task."
- **Startup lens:** **Blocking hooks = auditability-as-a-feature.** The wedge is pre-packaged hook libraries for regulated industries (healthcare, legal, finance) — HIPAA-compliant file-write gates, deny-by-default egress, PII-scrub pre-commits. $5–20K ACV, 50–200 F500 customers.
- **Insight:** Pre-tool hooks that halt = **the agent gets a Linux-style `apparmor` layer.** This is a precondition for enterprise T&S sign-off; expect every lab to ship an equivalent inside 90 days.

### ACT THIS WEEK
→ **Tonight:** `claude self-update` → ≥ v2.1.317. Add **one `PreToolUse` blocking hook** (deny file writes outside `$CLAUDE_PROJECT_DIR`). Commit `.claude/hooks/README.md` to your portfolio.

---

## 3. The Post-Cursor Router — weekend artifact, targets Mon 9 AM PT tweet to ride IPO news cycle {#3-post-cursor-router}

**What:** Public GitHub repo. Drop-in config generator that **re-routes a Cursor-shaped OpenAI-only codebase** to a 4D router: **Fable 5.2 default · Haiku 5.5 effort=low worker · Gemini 4 Argon fallback when user is Fairwind-verified · Mythos 5.2 for gated-cyber paths.** Uses Fable 5.2 **Fast Mode** as the "I actually need latency" lane.

**Why this weekend:**
- **Nov 12** is the Cursor cutoff → every OpenAI-only codebase became a migration project this week.
- **Mon Nov 16** is the tentative Anthropic IPO debut window → tweet rides the news cycle.
- **Three skills demonstrated in one repo:** cost-aware routing, eval-authoring, vendor-neutral migration tooling.

**Minimum viable repo contents:**
```
post-cursor-router/
├── README.md                      # the pitch; links to Anthropic IPO + Cursor cutoff
├── router.py                      # <50 LOC; (task, size, latency_tol) -> (model, effort, fast_mode)
├── config.example.yaml            # the drop-in config shape
├── migrate_cursor.py              # reads .cursor config, emits router config
├── evals/
│   ├── 5_cases.jsonl              # 5 gold prompts
│   ├── run_evals.py               # scores cost, latency, trajectory-reversibility (LLM-judge)
│   └── results.md                 # auto-generated before/after cost table
└── .claude/skills/router.md       # shippable skill version
```

**Rule table:**
```python
RULES = {
    # (task_type,     size,   latency)
    ("search_triage",  "any",  "any"):   ("haiku-5-5", "low",    False),
    ("summarize",      "any",  "any"):   ("haiku-5-5", "low",    False),
    ("code_edit_s",    "<50LOC", "any"): ("haiku-5-5", "high",   False),
    ("code_edit_l",    "any",  "any"):   ("fable-5-2", "medium", False),
    ("code_edit_realtime", "any", "<5s"):("fable-5-2", "medium", True),   # Fast Mode
    ("arch_plan",      "any",  "any"):   ("opus-5-5",  "high",   False),
    ("review_final",   "any",  "any"):   ("fable-5-2", "high",   False),
    ("cyber_gated",    "any",  "any"):   ("mythos-5-2","high",   False),  # if CVP-cleared
    ("defender",       "any",  "any"):   ("gemini-4-argon", None, None),  # if Fairwind-cleared
}
```

**Pricing math (sample):**
- Baseline: all-Opus 10 call sequence (5K/2K each) = **$0.75/task**
- With router (1 Opus plan + 1 Fable review + 8 Haiku workers) = **$0.062/task** → **~12× cheaper.**
- Fast Mode: 2× standard rate on the Fable call = **$0.072/task** when latency SLA matters → still 10× cheaper.

**Sources:**
- [Opus Orchestrator + Haiku Workers pattern](https://claude-skills-guide-3lc.pages.dev/opus-orchestrator-haiku-workers-pattern/) `[analysis]`
- [BuildFastWithAI — Anthropic Advisor Strategy](https://www.buildfastwithai.com/blogs/anthropic-advisor-strategy-claude-api) `[analysis]`
- [Haiku 5.5 vs Sonnet 5.5 vs Opus 5.5 for subagents](https://startdebugging.net/2026/10/claude-haiku-5-5-vs-sonnet-5-5-vs-opus-5-5-for-coding-agent-subagents/) `[secondary]`
- [Dev.to — Hybrid Sonnet→Haiku + OpenRouter, -70–85%](https://dev.to/valpere/ai-agent-cost-optimization-sonnet-hybrid-haiku-openrouter-3aa3) `[analysis]`
- Research anchors: [arXiv:2611.10193 PISA](https://arxiv.org/abs/2611.10193) · [arXiv:2611.05275 Route Anything](https://arxiv.org/abs/2611.05275) `[primary]`

Tags: `#router #post-cursor #haiku #fable #cost-aware #weekend-artifact #portfolio`

### Why it matters to you
- **Job lens:** This single artifact closes three loops — **Cursor-migration wedge, vendor-neutral router story, eval-authoring skill demo.** It is the highest-leverage weekend artifact since the dual-model sanitiser in May. Attach to all five apps in [`05` §2](./05-career-and-startup.md#2-apply-plan).
- **Startup lens:** Weekend prototype ≈ MVP for the **post-Cursor migration SaaS wedge** ([`05` §3](./05-career-and-startup.md#3-wedges)). Validate with 5 cold DMs to Cursor power users in your network after you ship.
- **Insight:** **Benchmark the artifact against the 8.82× efficiency gain reported in arXiv 2611.05275 "Route Anything" — if yours doesn't hit >6×, the rule table is wrong.** Publishable number = résumé number.

### ACT THIS WEEK
→ **Fri night:** repo scaffolded, config generator working. **Sat:** evals + README. **Sun:** finalize + schedule tweet for **Mon Nov 16, 9 AM PT.** Cross-post **Show HN** with lede: "The Cursor cutoff made every OpenAI-only codebase a migration project. Here's the 30-min version."

---

## 4. Haiku 5.5 effort levels — using the per-message beta header to keep cache valid {#4-haiku-effort-levels}

**What:** Haiku 5.5 adds `effort` as a top-level parameter with **5 levels (`low` / `medium` / `high` / `xhigh` / `max`)** — medium is default, replaces the old `budget_tokens`. Thinking + reply tokens both grow with effort. **`xhigh` / `max` only pay back when your evals confirm the quality gain.**

**How (keeping cache valid):**
```python
# WRONG — changes top-level param invalidates prompt cache
resp = client.messages.create(
    model="claude-haiku-5-5",
    effort="high",   # <- cache miss if different from previous call
    ...
)

# RIGHT — per-message effort beta header keeps cache valid mid-conversation
resp = client.messages.create(
    model="claude-haiku-5-5",
    extra_headers={"anthropic-beta": "per-message-effort-2026-11"},
    messages=[
        {"role": "user", "content": "...", "effort": "high"},
    ],
    ...
)
```
(Community-reported; verify against Anthropic docs — if the beta header isn't in your region yet, keep `effort` top-level and reset the stable prefix between calls.)

**Pricing math:**
- **$0.10/$0.50 per 1M under 100K tokens; 5× ($0.50/$2.50) above 100K.** Cache reads $0.01/1M.
- Same input text produces ~30% more tokens on Haiku 5.5 than 4.5 (per Anthropic's "what's new" page), so **cost-per-task on a worker ≈ ($0.10 × 1.3 + output × $0.50) / 1M.**
- **50K-input / 2K-output call at effort=low ≈ $0.006.**

**Sources:**
- [Prompting Claude Haiku 5.5 (Anthropic)](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/prompting-claude-haiku-5-5) `[primary]`
- [LetsDataScience — Haiku 5.5 effort controls](https://letsdatascience.com/news/anthropic-releases-claude-haiku-55-with-lower-prices-and-eff-f698c663) `[aggregator]`
- [Reading the Haiku 5.5 price table](https://braindetox.kr/en/posts/claude_haiku_5_5_release_pricing_2026.html) `[analysis]`
- [mer.vin — effort levels explainer](https://mer.vin/news/haiku-5-5-gets-effort-levels-and-a-90-percent-price-cut/) `[analysis]`

Tags: `#haiku #effort-levels #beta-header #caching #pricing`

### Why it matters to you
- **Job lens:** The "which effort" question is now a formal interview topic, not just an engineering detail. Benchmark **low vs medium vs high on 20 of your own eval inputs** and publish the token-count-per-level curve.
- **Startup lens:** Effort-level + Fast Mode + cache state is a 3D cost knob. Agent frameworks that abstract this into a single `latency_tolerance` + `quality_floor` API have a wedge — because 99% of app builders don't want to think in effort levels.
- **Insight:** **arXiv 2611.10193 (PISA / Route Anything) formalizes effort levels as a prompt-adaptive routing primitive.** The lab UX choice is now a research direction too — effort levels will outlive the "which model" question.

### ACT THIS WEEK
→ Pin `effort="low"` on every router-worker call in the weekend artifact. Benchmark low vs medium on 20 eval inputs. Publish the per-level token-count curve as a chart.

---

## 5. MCP at 10K public servers, 97M monthly SDK downloads — authoring now means stateful + bounded + audited {#5-mcp-at-10k}

**What:** Stacklok's **State of MCP 2026** reports **10,000+ active public MCP servers** and **97M monthly SDK downloads** as of October. **41% of enterprise software orgs have MCP in limited-or-broad production.** Simon Willison (Oct 22) reaffirmed MCP's core value even as Claude Code with unrestricted internet access can often skip it — the surviving MCP use case is **controlled access to secure resources.**

**The authoring recipe that still clears the "yet another API wrapper" noise floor:**
1. **Gated data source.** A sensitive customer dataset, internal document store, or regulated API.
2. **Per-tool audit log.** Every call → S3 / Loki / Datadog with request, response, user, timestamp.
3. **Short-lived credentials.** Server mints per-session tokens; no long-lived API keys handed to the LLM.
4. **Stateful session (if needed).** March 2026 MCP stateless-core update removed session context from the protocol; your server can add a session-cookie layer with a 12-month window before Anthropic re-absorbs it.

**Sources:**
- [Stacklok — State of MCP in Software 2026](https://stacklok.com/resources/state-of-mcp-in-software-2026/) `[analysis]`
- [Nordic APIs — 10 interesting MCP statistics](https://nordicapis.com/10-interesting-mcp-statistics/) `[analysis]`
- [Simon Willison — MCP under Claude Code with full internet](https://simonwillison.net/2026/sep/20/hn-49779718) `[analysis]`
- [Simon Willison — MCP tag](https://simonwillison.net/tags/mcp/) `[analysis]`
- [OSS Insight — live AI/MCP trending](https://ossinsight.io/trending/ai) `[aggregator]`

Tags: `#mcp #open-source #enterprise #adoption #authoring`

### Why it matters to you
- **Job lens:** **Your public MCP server portfolio artifact** ([ME.md](../ME.md)) needs to show the authoring recipe above, not just "3 tools, 5-case eval, README, demo gif." Add: audit log, short-lived credentials, one gated resource. **That's the version interviewers at Anthropic Solutions actually filter for in Nov 2026.**
- **Startup lens:** See [`02` §3](./02-new-emerging.md#3-mintive-agent-identity) — agent identity + stateful sessions are the two layers above MCP's core that still have wedge space. **Window closes when Anthropic ships an official stateful-session extension (watch Q1 2027).**
- **Insight:** MCP went from protocol to platform in 8 months. The "wrap an API" wave is done. **Stateful + bounded + audited** is the new authoring frontier.

### ACT THIS WEEK
→ Patch your MCP server README with a 5-line **"Vendor-neutral by design — swap backends via config"** callout. Add one **PreToolUse audit hook** that logs tool calls to a local SQLite `audit.db`. Screenshot and add to portfolio.

---

## 6. Prompt caching — the 1h TTL has to be opted into since March 2026 {#6-caching-1h-ttl}

**What:** Default cache TTL silently changed from 1h → 5m around March 2026. You now have to **explicitly set** `{"type": "ephemeral", "ttl": "1h"}` on your system prompt / stable prefix. On Claude Code subscriptions, main-conversation uses 1h automatically but **subagents are capped at 5m** — matters for long-running agent sessions.

**How:**
```python
system = [
    {
        "type": "text",
        "text": STABLE_PREFIX,
        "cache_control": {"type": "ephemeral", "ttl": "1h"},
    }
]
```

**Pricing math:**
- Per Anthropic pricing docs: 1h cache write = **2× base input**, cache read = **0.1× base.** Only worth it if the prefix is reused inside the hour.
- **Example:** Opus prefix 40K tokens, used 30×/hour. No cache = 30 × 40K × $15/1M = **$18.00**. With 1h cache = 1 × 40K × $30/1M + 29 × 40K × $1.50/1M = $1.20 + $1.74 = **$2.94 (~6× cheaper).**
- Single-use = don't bother.

**Sources:**
- [Anthropic — Reducing cost / performance with Claude Platform](https://claude.com/blog/reducing-cost-and-improving-performance-with-claude-platform) `[primary]`
- [Prompt caching production playbook (buzzai)](https://buzzai.cc/blog/anthropic-prompt-caching-playbook) `[analysis]`
- [Claude Code Prompt Cache TTL controls](https://www.developersdigest.tech/blog/claude-code-prompt-cache-ttl-controls) `[analysis]`
- [Prompt caching 2026: Anthropic vs OpenAI vs Gemini (alexcloudstar)](https://alexcloudstar.com/md/blog/prompt-caching-production-guide-2026/) `[analysis]`

Tags: `#caching #ttl #pricing #cost-aware #subagents`

### Why it matters to you
- **Job lens:** Add a `/usage` dump to your Post-Cursor Router repo showing **hit ratio before / after** caching. That's an interview exhibit at Anthropic Solutions and OpenAI FDE.
- **Startup lens:** **Billing audit as a service** ([ME.md](../ME.md) open artifact) — the 1h TTL opt-in is one of three common misses (effort-level default, cache TTL default, and prompt-cache invalidation on top-level param changes). A $500/engagement audit that saves $5–50K/yr for an SMB is a defensible wedge.
- **Insight:** Cache economics are now a **second-order cost** behind model + effort choice. Over an agent's lifetime, cache mistakes cost 2–10× more than model choice does.

### ACT THIS WEEK
→ Audit one agent's requests — grep for `cache_control` setting, ensure `ttl: "1h"` on the stable prefix. Add a `/usage` dump to the Post-Cursor Router writeup showing before / after hit ratio.

---

## Also shipped in-window (quick hits)

- **Microsoft 365 connector GA across all plans** — Word broadly available; Outlook in public beta. Local vs Anthropic-hosted modes. Entra app registration on customer tenant for enterprise. [Primary docs](https://claude.com/docs/third-party/claude-desktop/connectors-m365) · [Implicator analysis](https://www.implicator.ai/claude-taps-microsoft-365-as-the-connector-war-heats-up/). Pair with Haiku 5.5@low for inbox pre-summarization.
- **Codex "next-message suggestions" default-on for Pro (Oct 9)** — carried over from Oct 14 edition; use in combination with router's Fable 5.2 Fast Mode for latency-tight pair-programming loops.
- **Autopilot Frontier preview (Microsoft)** — Nov; watch Ignite Nov 17–20 for Autopilot $/seat pricing — the number that re-prices the agent-runtime market.

Tags: `#m365 #outlook #codex #autopilot`

---

## Thread status snapshot vs 2026-10-14

- **Router artifact (from Oct 14 §2):** 🟡 escalated — now explicitly post-Cursor + Fable-5.2 + Fast Mode + cross-vendor. Ship Sat–Sun.
- **Effort levels as routing primitive:** 🟢 confirmed by arXiv 2611.10193 + 2611.05275 (see [`04` §1](./04-research-progress.md#1-routing-arxiv-wave)).
- **Haiku 5.5 as default worker:** 🟢 operationalized — effort=low + 1h cache + gateway hooks = the production pattern.
- **Cache 1h TTL opt-in (from March):** 🟡 still a common miss; audit this quarter.
- **Skills / Plugins / Connectors unification (NEW):** 🆕 Enterprise cutover Nov 30.
