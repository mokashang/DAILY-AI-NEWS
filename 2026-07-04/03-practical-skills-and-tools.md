# 03 — Practical Skills & Tools — 2026-07-04

Hands-on. What you can ship, run, or reconfigure **today**. Every entry ends with a completion-test so you know you actually did it.

---

## 1. Recipe — Migrate one MCP server to the 2026-07-28 stateless RC {#1-mcp-migration}

**Why now.** Spec locks **July 28 (T-24 days)**. Every production MCP server needs a migration path, and most integration teams haven't started. **This is the FDE / integration-engineer weekend project of Q3.**

**What you're building.** Take a working MCP server (yours, or a fork of a small public one like `mcp-servers/filesystem`), migrate it to the RC, publish a before/after Loom + repo. That's the artifact.

**Six-step plan (aim: 2–3 hours end-to-end).**

**Step 1 — Read the SEPs, not the summaries** (25 min).
- The [MCP blog post](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) is authoritative. Focus on SEP-2567 (sessions removed) + SEP-1865 (Apps) + Tasks extension.
- Skim [WorkOS on OAuth 2.1 hardening](https://workos.com/blog/mcp-2026-spec-agent-authentication) if your server has authz.
- Save the [beta SDK release notes](https://blog.modelcontextprotocol.io/posts/sdk-betas-2026-07-28/) as your migration checklist.

**Step 2 — Remove session state** (30 min).
- Delete the `Mcp-Session-Id` header handling.
- Delete the shared session store (Redis, in-memory dict, whatever).
- Move any per-conversation state into either (a) the client's message history, or (b) the new **Tasks** handles.
- Sanity check: your handler code should now be able to serve two consecutive requests on *different physical instances* with no coordination.

**Step 3 — Wire the required routing headers** (15 min).
- On the server: no code change needed — the SDK adds them.
- On the *load balancer / gateway* if you have one: route by `Mcp-Method` (e.g., pin `tools/call` to warm instances, cache `tools/list` at the edge) and `Mcp-Name` (per-tool rate limiting).

**Step 4 — Add caching semantics** (20 min).
- On your `tools/list` handler: emit `ttlMs` (e.g., 3600000 = 1 hour if your tool set is static) and `cacheScope: "shared"` if the list is universal, `"per-user"` if it varies.
- On your `resources/read` handler: same pattern, but `cacheScope: "per-user"` is the safe default.

**Step 5 — Migrate one long-running tool to Tasks** (30 min).
- Pick the slowest tool you have. Return a **task handle** from `tools/call` instead of the result.
- Implement `tasks/get` (return current status), `tasks/update` (emit progress events), `tasks/cancel` (return early).
- Client-side: poll `tasks/get` every 2–5s until `status: "done"`.

**Step 6 — Ship the artifact** (30 min).
- Repo: `mcp-server-<name>-stateless`. Commit history should show: `v0.x-legacy → v1.0-stateless-rc` with a clear migration commit.
- README: 200-word "why we migrated" + a **before/after wire trace** (curl request/response for both).
- 3-min Loom: **the outage-drill demo** — restart your server mid-`tasks/get`, show the client recovering. That's the credibility close.

**Completion test.** Two consecutive requests routed to different instances (kill one, restart, do the next call) both complete correctly.

**Sources.**
- **[primary]** [MCP Blog — 2026-07-28 RC](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/)
- **[primary]** [MCP Blog — Beta SDKs](https://blog.modelcontextprotocol.io/posts/sdk-betas-2026-07-28/)
- **[analysis]** [ChatForest — Builder Guide (six breaking changes)](https://chatforest.com/builders-log/mcp-spec-2026-07-28-release-candidate-stateless-breaking-changes-builder-guide/)
- **[analysis]** [byteiota — Stateless RC breaks and fixes](https://byteiota.com/mcp-stateless-2026-release-candidate/)

**Why it matters to you.** **Job:** put this at the top of your GitHub pinned repos on Monday. **Startup:** if your MVP has an MCP layer, this is your infra-hardening sprint. **Insight:** every protocol churn in the industry (LSP, JSON-RPC, gRPC, GraphQL, MCP) has minted a small population of engineers who did the migration first and got the offers.

`#mcp #migration #tasks #stateless #portfolio`

---

## 2. Recipe — Add a "LongCat-2.0" routing slot to your inference config {#2-longcat-routing}

**Why now.** LongCat-2.0 (see [`02` §2](./02-new-emerging.md#2-longcat)) is near-frontier on agentic coding, MIT licensed, hosted on **Together AI**, **Fireworks**, and **Baseten**. Adding it as a 5th slot in your routing config is a **20-minute change that repriced ~30–40% of coding workloads for cost.** Directly compounds the [Opus-orchestrator/Sonnet-worker split](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost).

**The five-slot routing config (updates the four-slot from [07-03/03 §3](../2026-07-03/03-practical-skills-and-tools.md#3-routing)).**

```yaml
routing:
  # 1. Frontier reason — for the plan/critique/verify calls
  reason:
    provider: anthropic
    model: claude-opus-4-7
    max_tokens: 8192

  # 2. Frontier speed — for real-time interactive turns
  speed:
    provider: openai
    model: gpt-5-5-mini
    max_tokens: 2048

  # 3. Wholesale compute — for scale-out
  wholesale:
    provider: together        # or fireworks / baseten
    model: meta-llama-3-1-405b-instruct
    max_tokens: 4096

  # 4. Self-hosted cheap — for redaction / classification / offline
  cheap:
    provider: vllm-local
    model: llama-3-1-8b-instruct

  # 5. NEW — Open agentic-coding — for scale-out coding + refactor
  open_coding:
    provider: together        # LongCat-2.0 on Together / Fireworks
    model: meituan/longcat-2-0
    max_tokens: 8192
```

**Which workloads route to slot 5.**
- Bulk refactors (unblock 1000-file migrations without burning frontier tokens).
- Test generation (Sonnet-quality pass rates at ~1/10 the cost).
- Doc → code (JSDoc → TypeScript, README → CLI wrappers).

**Which workloads DON'T.**
- Anything with strict data-residency (LongCat is a **Chinese-lab model**; know your compliance regime).
- Novel-architecture design (still route to `reason` for Opus 4.7).

**Completion test.** Route one non-trivial task (e.g., migrate a 20-file repo from Jest to Vitest) exclusively through `open_coding`. Compare (cost, time, pass rate) against the same run on Opus 4.7. Post a two-row table in a public Gist.

**Sources.**
- **[primary]** [Together AI model catalog](https://www.together.ai/models)
- **[secondary]** [VentureBeat — LongCat-2.0 leading OpenRouter](https://venturebeat.com/technology/meituan-open-sources-longcat-2-0-the-1-6t-near-frontier-agentic-coding-model-thats-been-leading-openrouter-trained-entirely-on-chinese-chips)
- **[aggregator]** [ThunderCompute — Best Open Source LLMs (July 2026)](https://www.thundercompute.com/blog/best-open-source-llms)
- [Prior routing recipe (2026-07-03/03 §3)](../2026-07-03/03-practical-skills-and-tools.md#3-routing)

**Why it matters to you.** **Job:** interviewers ask "when would you not use Sonnet 5?" — this is the answer. **Startup:** margins on any coding-adjacent product move by ~2× when you have a cheap-tier fallback. **Insight:** the open-weights routing slot is the single biggest cost lever in your stack for the next six months.

`#routing #cost #open-source #longcat #together`

---

## 3. Recipe — Run the July AI-spend audit (4th-of-month personal rule) {#3-spend-audit}

**Why now.** Today is **July 4**. Your [`ME.md`](../ME.md) commits to "audit AI spend monthly (4th of month)." Yesterday's Anthropic gateway shipped ([07-03/01 §1](../2026-07-03/01-big-lab-moves.md#1-gateway)) precisely because enterprises couldn't answer this question — now you get to model what the answer looks like on your own bill.

**The 30-min audit template.**

1. **Pull the raw** (10 min).
   - **Anthropic Console → Usage → Export CSV** for June + first 3 days of July.
   - **OpenAI Platform → Usage** — same export.
   - **Cursor / Windsurf / Aider** — settings → billing.
   - **Together AI / Fireworks / Baseten / Bedrock / Vertex** — same as above.
   - **Personal Stripe / bank statement** cross-check for anything you paid card-on-file.

2. **Categorize in a single sheet** (10 min):
   - **columns:** provider, model, purpose (coding / research / writing / experiments), input tokens, output tokens, cost.
   - **rows:** one per model per purpose per month. Aggregation is fine.

3. **Compute the 80/20** (5 min):
   - Which single line-item is **>25% of total**? That's the routing-config change candidate.
   - Which line-item is **<5% of total but constant**? That's the "always-on subscription" — check if the SKU still fits usage or if you can downgrade.
   - Any usage without a labeled purpose? That's **entropy** — kill or classify.

4. **Write the audit note** (5 min):
   - File: `SPEND-2026-07.md` at the repo root (create if not present).
   - 200 words: "June spend was $X. 60% Anthropic (Opus + Sonnet), 20% OpenAI (GPT-5.5), 20% Cursor. The bill is dominated by orchestrator calls; opportunity = LongCat-2.0 for bulk coding workloads (see `03 §2`). July target: -25% at same throughput."

**Completion test.** Push `SPEND-2026-07.md` before the end of Saturday. The value is not the number — it's having the muscle memory for the ritual.

**Sources.**
- [Anthropic Console — Usage export](https://console.anthropic.com/)
- [OpenAI Platform — Usage dashboard](https://platform.openai.com/usage)
- [Your `ME.md` personal rule](../ME.md)
- [Personal Claude billing audit — carried portfolio artifact from `ME.md`](../ME.md)

**Why it matters to you.** **Job:** every FDE interview asks "how do you think about cost." Your own bill is the honest answer. **Startup:** if you can't audit your own $50/mo, you cannot audit a $50K/mo customer's. **Insight:** the discipline of monthly personal-spend audits is what makes the gateway pitch ([07-03/01 §1](../2026-07-03/01-big-lab-moves.md#1-gateway)) legible to you — because you already do the same thing at 1/1000 scale.

`#spend #audit #cost #discipline #july4`

---

## 4. Quick tip — Anthropic constitution reading list before Geneva (Monday) {#4-constitution-read}

**Why now.** The [UN Geneva AI Governance Dialogue](./01-big-lab-moves.md#4-geneva) starts Monday. Anthropic's new constitution published July 3 is the **most-quoted primary source** entering that room. 20 minutes of prep this weekend = a governance-lane talking-point advantage next week.

**The 3-doc reading list.**
1. **[Anthropic — Claude's new constitution (Jul 3)](https://www.anthropic.com/news/claude-new-constitution)** — 15 min. Read for the 4-tier hierarchy (safety, ethics, compliance, helpfulness) and the reason-based (not rule-based) framing.
2. **[Anthropic — Claude's Constitution (living doc)](https://www.anthropic.com/constitution)** — skim. This is the CC0-licensed one; anyone can reuse it.
3. **[BISI — Claude's New Constitution analysis](https://bisi.org.uk/reports/claudes-new-constitution-ai-alignment-ethics-and-the-future-of-model-governance)** — 5 min. Third-party analysis; useful for interview language.

**Optional 4th doc.** [TechPolicy.Press — Three Temptations Facing the UN's First Global AI Dialogue](https://www.techpolicy.press/the-three-temptations-facing-the-uns-first-global-ai-dialogue/) — this is where the *counter-argument* lives. Read both sides.

**Completion test.** Write 3 bullet points: "what Anthropic wants Geneva to standardize," "what Geneva probably will actually produce," "what falls in the gap." Save as `2026-07-04-geneva-prep.md` in your notes.

**Why it matters to you.** **Job:** if you interview at any governance-adjacent org this month, being fluent in this doc is table stakes. **Startup:** the constitution's reason-based framing gives you a template for your own AUP if you build an AI product. **Insight:** governance vocabulary compounds — the labs that publish the language shape the RFPs that follow.

`#geneva #constitution #governance #policy #prep`

---

## Cross-refs

- [2026-07-03/03 §1 Deploy Claude apps gateway (carried; still live for this weekend)](../2026-07-03/03-practical-skills-and-tools.md#1-gateway-deploy)
- [2026-07-03/03 §2 Artifacts-in-Claude-Code recipe](../2026-07-03/03-practical-skills-and-tools.md#2-artifacts-recipe)
- [2026-07-03/03 §3 Four-slot routing config (this edition adds slot 5)](../2026-07-03/03-practical-skills-and-tools.md#3-routing)
- [2026-05-22/03 §1 Opus-orchestrator / Sonnet-worker cost split](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)
- [2026-05-17/03 Karpathy CLAUDE.md + hooks + subagents baseline](../2026-05-17/03-practical-skills-and-tools.md)
