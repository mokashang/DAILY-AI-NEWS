# Practical Skills & Tools — 2026-10-13

Act-on-this-today. Four hands-on sections: Haiku 5.5 economics, the memory-aware extraction harness (your Tuesday ship), a policy-literate agent checklist for the Sept-29-accord era, and a short note on the Claude Code gateway + the four-vendor router update.

Tags: `#claude-haiku-5-5 #prompt-caching #memory #mcp #evals #claude-code #gateway #policy`

---

## 1. Claude Haiku 5.5 — the 1M-context + adaptive-thinking price point {#1-haiku-55}

**What shipped (Oct 7):** Anthropic released **Claude Haiku 5.5**:

- **Context window:** **1,000,000 tokens** (10× prior Haiku)
- **Max output:** **128,000 tokens**
- **Thinking:** **adaptive, adjustable effort** (short/medium/long, programmatically picked)
- Target: high-volume **summarization, classification, extraction** workloads
- Same-day: **Sonnet 5.5 cache-read price cut** + **expanded browser / computer-use** in SDK and Managed Agents
- **Claude Code 2.1.296** (Oct 10) ships **agent, workflow, gateway** controls

The design read: Anthropic is explicitly building Haiku 5.5 as the **batch-workhorse** tier. Not a flagship. Not a reasoning engine. The cheapest-fastest-best-small model, with enough context to swallow a whole PDF corpus in one call.

**Sources:**
- [Anthropic release notes (Oct 7, via Releasebot)](https://releasebot.io/updates/anthropic) `[primary]`
- [Emergent.sh — Anthropic Launches Claude Haiku 5.5 Multimodal Model](https://emergent.sh/news/anthropic-launches-claude-haiku-55-multimodal) `[secondary]`
- [Claude timeline (jqueryscript/anthropic-claude-timeline)](https://github.com/jqueryscript/anthropic-claude-timeline) `[aggregator]`
- [Releasebot — Claude October 2026 updates](https://releasebot.io/updates/anthropic/claude) `[aggregator]`

### Why it matters to you

- **Economics (concrete):** If your extraction / classification pipeline is currently on Fable-5.1 cache-reads at **$0.25/1M** (per [2026-09-10/03 §1](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics)), Haiku 5.5 is probably **2–4× cheaper per completed task** for the batch-shape loads it was built for — plus you now fit a full 1M-token corpus in one call rather than chunking + stitching. Rebench with your own 20-doc test set this week; the dashboard that proves it is itself a résumé artifact.
- **Adaptive thinking:** Set `effort: short` for straightforward extraction, `medium` for cross-doc reasoning, `long` only when a verifier catches a wrong answer. Cheap-first, expensive-on-escalation is the correct Haiku 5.5 posture.
- **1M context:** Prefer **context-stuffing with a persistent summary ledger** (per §2 below) over RAG for ≤1M-token corpora. Pure RAG becomes the right choice again above 1M or when retrieval quality is the bottleneck.

### Action for you this week

1. Rerun your current cost dashboard with Haiku 5.5 against your top-2 batch jobs (extraction + summarization). Publish numbers.
2. Add adaptive-thinking tiers to the router (see §5).
3. If you have an MCP server from May's artifact, add a Haiku-5.5-cheap-leg to it today.

---

## 2. Tuesday artifact — the memory-aware extraction harness {#2-memory-harness-artifact}

**The pitch:** On the day Meta made consumer-grade **Active Memory** a headline ([`01` §1](./01-big-lab-moves.md#1-muse-wonder)), build the developer-primitive version yourself. One repo, one eval case, one 90-second screencap, published tonight.

### Spec (50 lines of code + 50 lines of README)

**Inputs:** 10 PDFs (any corpus — your own class materials work).

**Pipeline:**
1. **Ingest** each PDF into Haiku 5.5 at `effort: short` → produce a **structured summary** per PDF (JSON with: topics, entities, dates, open-questions).
2. **Persist** summaries to a local **SQLite** `memory_store` keyed by `(user_id, doc_id, version)`. Store the raw text separately but *don't* reload it for queries.
3. **Query** with a cross-document question (e.g., "Which papers argue for test-time scaling?"). The query path only hits the summary store, not the raw PDFs, unless the summary store's confidence is below a threshold.
4. **Verify** each answer with a second Haiku-5.5 pass at `effort: medium` that *only* sees the retrieved summaries and must flag "insufficient evidence" when applicable.
5. **Scope + expire:** Every memory row has an `expires_at` and a `scope` (per-user, per-session, per-tenant). Add a `forget(user_id)` function that honestly drops rows.

**Instrumentation:**
- Per-query token count by effort tier
- Per-query cost (USD) with Haiku 5.5 pricing
- Hit rate (summary-store answers vs. full-doc fallbacks)
- Memory age distribution

**Evaluation case:**
- 10 PDFs + 10 cross-document questions + 10 gold answers (write them yourself in 15 minutes).
- Report: accuracy, median latency, median cost per query.

**Why this is the right artifact today:**
- Answers "have you shipped memory in production?" with a real repo.
- Answers "do you understand per-user scoping / expiration / forget?" (GDPR + accord-era table stakes).
- Answers "can you cost-engineer?" — your dashboard shows per-query USD.
- The three answers above are the questions every FDE / AI Integration / applied-AI role will ask in Q4.

### Why it matters to you

- **Job lens:** This single repo answers three agent-primitive questions (memory, scoping, cost) in one artifact. Pair it with the Beltic-shaped **agent-id token** on every tool call ([`02` §3](./02-new-emerging.md#3-beltic)) and you've shipped two of the three 2026 agent primitives. The third — **verification** — is the next weekend's build (see §3 + `04` §2).
- **Startup lens:** This repo *is* an early-stage startup. The gap between a 100-line harness and a $10M-ARR memory-SLA infra company is customer-shaped: find one that pays $500/mo for memory-SLA, you've found the wedge.
- **Insight:** Memory + scoping + expiration is **the unit of frontier product differentiation for the next 12 months.** The models themselves are converging; what consumers notice is whether the assistant *remembers them*. Build the primitive today, before the hiring posts catch up.

→ Cross-link: [`01` §1 Muse Wonder](./01-big-lab-moves.md#1-muse-wonder) · [`02` §3 Beltic](./02-new-emerging.md#3-beltic) · [`04` §1 memory benchmarks](./04-research-progress.md#1-memory-benchmarks).

---

## 3. Policy-literate agent checklist — the Sept-29-accord era {#3-policy-checklist}

**The pitch:** After the Sept 29 White House self-policing accord ([`01` §2](./01-big-lab-moves.md#2-wh-accord)) and the summer's sandbox-escape incidents ([`01` §3](./01-big-lab-moves.md#3-escapes)), any agent you ship — portfolio or production — should pass a short checklist before you hit "deploy." This is new baseline table stakes for interview demos.

### Pre-deploy checklist (10 items, ≤ 1 hour to retrofit a small agent)

**Identity + scoping (3):**
1. Every outbound tool call carries a signed, revocable **agent-id token** (Beltic-pattern, [`02` §3](./02-new-emerging.md#3-beltic)).
2. Every memory row has `scope` and `expires_at`; `forget(user_id)` works and is tested.
3. Secrets never enter model context; a secrets-mounting layer injects them at tool-call time.

**Isolation + logging (4):**
4. Tools run in a sandbox with **no implicit network egress** (allowlist only). The sandbox is logged; the log is externalized.
5. The agent is tested against a "sandbox escape" attempt as a routine eval (does the eval harness correctly refuse an attempt to reach a disallowed URL?).
6. **Pre-deploy evaluation record** — a stored artifact (JSONL or similar) that an auditor could read: what evals ran, which passed, which flagged, who approved.
7. **Immutable audit log** of every tool call + model output in production (prefer append-only object storage).

**Verification + rollback (3):**
8. A **verifier model** (separate call, often cheaper) re-reads critical outputs and flags "insufficient evidence" or disagreement.
9. **Kill switch** — a documented, tested procedure to pull the agent globally in ≤ 60 seconds.
10. **Retraction protocol** — if an output was wrong, you can issue a correction (per the OpenAI math walkback precedent, [`04` §2](./04-research-progress.md#2-openai-math)).

### Why it matters to you

- **Job lens:** Add "policy-literate agent design" to your LinkedIn skills row. In interviews, when asked "how would you deploy this?" walk the checklist. The 10 items above anticipate exactly the questions a Big-4-AI-practice interviewer or a frontier-lab trust-and-safety team asks.
- **Startup lens:** The checklist is a product. "Compliance.ai for frontier agents" — automate the checklist, generate the pre-deploy evaluation record. Buyer: Head of Research Engineering at any lab + any Series-B AI-first startup selling into enterprise. Price: $5–20K/mo per environment.
- **Insight:** The accord moved the Overton window on "what counts as a shipped agent." Before Sept 29, a demo was "it works." After Sept 29, a demo is "it works *and I can explain why it's not going to escape the sandbox and leak PII*." Memorize both halves.

→ Cross-link: [`01` §2 WH accord](./01-big-lab-moves.md#2-wh-accord) · [`01` §3 sandbox escapes](./01-big-lab-moves.md#3-escapes) · [`05` §2 AI assurance lane](./05-career-and-startup.md#2-assurance-lane).

---

## 4. Claude Code 2.1.296 — the gateway primitive {#4-gateway}

**What shipped (Oct 10):** Claude Code **2.1.296** adds **agent, workflow, and gateway** controls plus platform fixes. The decision-tree from [2026-09-10/03 §2](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree) still holds (enforcement → Hooks/permissions; contextual knowledge → Skills; delegation boundary → Subagents; always-on project guidance → CLAUDE.md). The **gateway** is a *new* primitive on top:

- **Gateway controls** — per-tenant / per-skill / per-agent constraints that enforce before a tool call lands. Think of it as the single-point-of-control between your Claude Code harness and the outside world.

The gateway is the mechanical implementation of the §3 checklist's isolation + logging rows. Set up a gateway with:

1. **Allowlist of tool endpoints** per agent-id.
2. **Rate-limits** per agent-id + per tool.
3. **Centralized audit log** for every call that goes through the gateway (so the §3 immutable log is one line of config, not a code change).

**Sources:**
- [Releasebot — Anthropic Oct 2026 updates (Claude Code 2.1.296, Oct 10)](https://releasebot.io/updates/anthropic/claude) `[primary]`

### Action

Add a gateway config to the memory harness in §2 before you publish — it's a 10-line yaml addition and converts the artifact from "cool demo" to "policy-literate demo." That's the thing that gets forwarded by a recruiter.

→ Cross-link: [2026-09-10/03 §2 decision tree](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree) · [`03` §3 policy checklist](#3-policy-checklist).

---

## 5. Four-vendor router update {#5-router-update}

**What's new (concrete, 20-minute task):** the three-vendor router from [2026-05-20/03 §4](../2026-05-20/03-practical-skills-and-tools.md#4-cost-routing) → [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) now needs:

1. **Haiku 5.5 as the cheap batch leg** (1M context + adaptive thinking) — displaces Fable-5.1-cache-reads for extraction/classification jobs.
2. **Sonnet 5.5 reduced cache-read pricing** — update the per-token cost table.
3. **Grok Imagine Video 1.5 Lite** as the fourth vendor for image/video tasks (see [`02` §4](./02-new-emerging.md#4-grok-video)).
4. **Adaptive-thinking tiering per task-type** — short/medium/long maps to task-complexity, not to vendor.

**Deliverable:** one updated README + one short-form blog post ("Four-vendor router after Haiku 5.5"). Pair it with the memory-harness ship from §2 for a two-artifact Tuesday night.

→ Cross-link: [2026-05-20/03 §4 cost routing origin](../2026-05-20/03-practical-skills-and-tools.md#4-cost-routing) · [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact).

---

## This-week shipping summary

| Priority | Artifact | Est. time | Why |
|---|---|---|---|
| P1 | Memory-aware extraction harness (§2) | 2 hrs | Answers 3 of this quarter's top interview questions |
| P1 | Policy checklist retrofit onto the harness (§3 + §4) | 30 min | Converts demo → policy-literate demo |
| P2 | Four-vendor router update (§5) | 20 min | Keeps the router artifact fresh with Haiku 5.5 |
| P2 | Haiku 5.5 cost-rebench blog post (§1) | 1 hr | Numbers-first content performs on LinkedIn |
| P3 | Beltic-pattern agent-id token mini-repo | 90 min | KYA before it has a category |
