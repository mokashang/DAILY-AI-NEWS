# Practical Skills & Tools — 2026-07-29 (Wednesday)

Two hands-on threads this week: the **effort toggle** on Opus 5 has produced real cost-per-quality numbers you can budget against, and the **MCP 2026-07-28 migration** finally has a "do it in one afternoon" playbook. Plus a pre-Sonnet-price-hike audit routine and this weekend's artifact idea.

---

## 1. Opus 5 effort toggle: a real cost/quality curve to plan against {#1-opus-5-effort}

Building on [2026-07-25 §1](../2026-07-25/03-practical-skills-and-tools.md#1-opus-5-effort). Four days in, a rough working table from community benchmarks + Anthropic's own release notes:

| Setting | Rel. output tokens | Rel. quality (SWE-bench delta) | When to use |
|---|---|---|---|
| `effort=low` | ~0.4× | -3 to -5 pp | High-volume routing, first-pass classification, cache-warmup gen |
| `effort=medium` | ~0.7× (default) | baseline | Default worker, most tool-use loops |
| `effort=high` | 1.5–2.5× | +1 to +3 pp | Planner, hard debug, one-shot artifact gen |

*(Numbers are indicative — run your own eval on your workload. Anthropic hasn't published official per-effort benchmarks; the community numbers were compiled from HN / r/LocalLLaMA / Latent Space posts through 07-28.)*

**Two patterns worth stealing:**

1. **Planner (high) + Worker (medium) + Verifier (Haiku).** The 3-tier architecture from [`03` §4 last week](../2026-07-25/03-practical-skills-and-tools.md#4-this-weekends-artifact). Cost is dominated by the worker; the planner runs 1× per task and the verifier is a $0.80/MTok pass. Total cost is typically 30–40% lower than "Opus 5 default for everything" at similar or better quality.
2. **Adaptive effort via task tags.** Attach a lightweight `estimated_difficulty` (0–1) to each incoming request; route to `low` if < 0.3, `medium` if 0.3–0.7, `high` if > 0.7. The classifier itself is Haiku. This gets you production-grade cost adaptability in ~200 lines.

**Sources.** [Anthropic Claude release notes](https://releasebot.io/updates/anthropic/claude) `[primary]` · [`03` §1 last week](../2026-07-25/03-practical-skills-and-tools.md#1-opus-5-effort) `[analysis]`

**Job · Startup · Insight.**
- **Job.** Write a short blog post — "How I cut my agent bill 38% with Opus 5 effort routing" — with real numbers from your side project. This is the exact shape of artifact that lands FDE interviews.
- **Startup.** Effort-routing-as-a-service ("Cursor for API cost") is not a startup, but as a **library** it's a durable open-source position.
- **Insight.** Every compiler knob eventually becomes a runtime knob. `effort` used to be model-tier selection; now it's per-request. Next: **per-tool-call effort** inside a single agent loop. Anthropic will ship it; front-run the pattern.

`#opus-5 #effort #cost-routing #agent`

---

## 2. MCP 2026-07-28 migration playbook (one afternoon) {#2-mcp-migration}

The spec shipped ([`01` §2](./01-big-lab-moves.md#2-mcp-shipped)); if you have an MCP server that still says `2025-06-18` or earlier, you have ~2 weeks before "old spec" starts showing up as a real integration friction. Here is the minimum viable migration:

**Step 1 — Strip state (30 min).**
- Delete session-init handshakes. Every request is self-contained.
- Move any per-session state into your own backing store (Postgres, Redis, D1). The MCP layer stops caring.
- Add `Mcp-Method` and `Mcp-Name` request headers to every tool call for LB-friendly routing.

**Step 2 — OAuth 2.1 / OIDC (60–90 min).**
- If you were using bearer tokens, wire an OAuth 2.1 flow. Use [Auth0 free tier](https://auth0.com/pricing) or [Clerk](https://clerk.com) to skip the auth infra grind.
- Test against the reference client. Fail-open behaviors should now fail-closed by default.

**Step 3 — Redeploy on stateless infra (30 min).**
- Push to Cloudflare Workers / Vercel Edge / Fly.io. No sticky sessions required.
- Round-robin LB in front. Cold-start is now a design consideration, not a session problem.

**Step 4 — Wire `MCP Apps` if you have UI (30–60 min).**
- The versioned Apps extension replaces the ad-hoc UI-embed patterns that shipped in 2025. If your tool returned HTML fragments, port them to MCP Apps.

**Sources.** [modelcontextprotocol.io — 2026-07-28 spec](https://blog.modelcontextprotocol.io/posts/2026-07-28/) `[primary]` · [Anthropic — Bringing MCP 2026-07-28 to Claude](https://claude.com/blog/bringing-mcp-2026-07-28-to-claude) `[primary]` · [Nerd Level Tech migration walkthrough](https://nerdleveltech.com/mcp-stateless-protocol-enterprise-authorization) `[analysis]`

**Job · Startup · Insight.**
- **Job.** A migrated `2026-07-28` MCP server with a README that walks a hiring manager through the migration is the single best MCP portfolio piece you can ship this week. Time to ship: one Saturday afternoon.
- **Startup.** Freelance MCP-migration engagements are actually being posted on Upwork this week — for ~$1.5–3K per migration. If you migrate your own server first, you have the credential.
- **Insight.** Read the errata as it lands (`blog.modelcontextprotocol.io`); the first 30 days of any spec have the highest hidden-bug density.

`#mcp #migration #oauth #stateless #portfolio`

---

## 3. Audit: kill your public Claude share links before the enterprise trust story hits your inbox {#3-share-audit}

Prompted by [`01` §5](./01-big-lab-moves.md#5-share-leak). Take 10 minutes:

1. Open [claude.ai/settings/shared-content](https://claude.ai/settings) → **Shared content** (path may vary).
2. Review every shared conversation and artifact. Un-share anything that includes:
   - Résumé / job-app material (your name + specific companies)
   - Client / employer info
   - Anything you would not want indexed on Google
3. **Rule of thumb going forward:** shared links are **public**. If a conversation contains anything you would not paste on Reddit, do not create a share link — export the artifact and send it directly.
4. Same audit for ChatGPT shared links, Gemini share, and any Notion pages backing your AI work.

**Insight.** In interviews, being able to *cite this specific incident* and describe the fix ("`noindex` header + opt-in public flag + short-lived signed URLs") is a hiring signal for AI-integration / security-adjacent roles.

`#security #hygiene #audit`

---

## 4. This weekend's artifact — updated for 2026-07-29 {#4-this-weekends-artifact}

Building on [last week's artifact spec](../2026-07-25/03-practical-skills-and-tools.md#4-this-weekends-artifact), one addition this week:

**"MCP-migrated agent triangle + Mythos-inspired eval."**

Two moves in one repo:

**A. The core artifact (Saturday):** Planner (Opus 5, `effort=high`) → Worker (Opus 5, `effort=medium`) → Verifier (Haiku 4.5). Backed by one MCP server you migrated to `2026-07-28` this week. Per-step cost log to CSV.

**B. The differentiator (Sunday):** Add a **cryptanalysis-adjacent eval** to the repo — pick one small unsolved-toy problem (e.g., a reduced-round toy cipher your worker+verifier must find a distinguisher for). Purpose: prove the harness can be applied to novel problem shapes, not just SWE-bench-flavored coding tasks. Reference [`01` §1 Mythos writeup](./01-big-lab-moves.md#1-mythos-hawk) in the README as the inspiration for the eval design (do **not** claim to have replicated Mythos's HAWK result — this is the tiny toy version).

**Repo shape:**
```
mcp-agent-triangle/
├── README.md            # architecture diagram + cost log summary + eval numbers
├── mcp-server/          # 2026-07-28 spec, OAuth 2.1, Cloudflare Worker
├── agents/
│   ├── planner.py       # Opus 5 effort=high
│   ├── worker.py        # Opus 5 effort=medium
│   └── verifier.py      # Haiku 4.5
├── evals/
│   ├── swe-bench-lite/  # standard baseline
│   └── toy-cipher/      # differentiator eval
└── costs.csv            # per-run cost & quality log
```

**Time budget.** 6–8 hours across Saturday + Sunday. Ship even if incomplete — a partial repo with a good README beats a complete-but-invisible one.

**Job · Startup · Insight.**
- **Job.** This is a single artifact that answers three separate interview questions: agent orchestration, real-tool verification, cost-aware design. It replaces 3 weaker portfolio items.
- **Startup.** The eval framework alone is worth open-sourcing under a permissive license — Anthropic explicitly rewards eval-adjacent OSS in Fellows applications and community grants.
- **Insight.** Ship the README first, code second. The README's structure — "here is the problem, here is the design, here are the numbers" — is what recruiters and founders both read.

`#weekend #artifact #mcp #agent #eval`

---

## 5. Micro-tip: `Mcp-Method` / `Mcp-Name` headers unblock plain-HTTP observability {#5-headers-observability}

**One sentence:** The new `Mcp-Method` and `Mcp-Name` request headers let your existing HTTP observability stack (Datadog / Grafana / plain nginx access logs) slice by MCP tool and method without a special-purpose collector. If you're running MCP in production, add these to your dashboards this week — you'll get per-tool latency and error rates for free.

**Insight.** Every "protocol goes stateless" moment eventually becomes an observability upgrade. This is that upgrade for MCP.

`#mcp #observability #ops`
