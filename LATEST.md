# LATEST — pointer to the most recent edition

> **2026-06-21** — see [`2026-06-21/00-tldr.md`](./2026-06-21/00-tldr.md)

This file is auto-updated every edition so a one-click read of the latest TL;DR is always at the repo root.

---

## Today's headline

**Sunday — the talent map snapped back, the protocol surface hardened, and the policy cliff turned into an empty room.** **Noam Shazeer left Google for OpenAI as "Lead for Architecture Research" (June 18)** — co-author of *"Attention Is All You Need"* and Gemini co-lead; combined with Karpathy → Anthropic pre-training, the two largest talent flips of 2026 now point in opposite directions. **MCP `2026-07-28` Release Candidate dropped Thursday** — **Tasks** primitive, **MCP Apps**, stateless core, **OAuth 2.1 Resource Server** hardening; the `@modelcontextprotocol/sdk` npm package now does **35.5M weekly downloads — more than `openai` + `@anthropic-ai/sdk` combined.** MCP is the integration layer. **Fable 5 + Mythos 5 access restored June 18** after a ~6-day US-export-control suspension; in the same week, **Fable 5 took #1 on DeepSWE (70% pass@1)** and **Artificial Analysis re-weighted its Intelligence Index to 34% agents with Opus 4.8 on top (65.7)**. The Anthropic stack came out of a federal speed-bump measurably stronger.

Full edition → [`2026-06-21/`](./2026-06-21/)

---

## One-thing-to-do (Sunday)

→ **Ship a public MCP server *to the `2026-07-28` RC spec*** — implement at least one **Task** (long-running, resumable), wire the **OAuth 2.1 Resource Server** auth profile, ship as a **`.mcpb` bundle**, include a 5-case eval citing MCP-Atlas methodology, and add a per-step `cost.md`. README headline: *"An MCP server built to the `2026-07-28` RC: Tasks + RS-auth + per-step cost trace."* See [`2026-06-21/03 §2`](./2026-06-21/03-practical-skills-and-tools.md#2-mcpb-bundles) for the 30-minute ship recipe.

→ **Post LinkedIn + Hacker News** with the artifact (45 min, end-of-day). LinkedIn skill row swap: add `MCP Tasks`, `MCP Apps`, `.mcpb packaging`, `OAuth Resource Server`. Zero-result keywords today; filterable terms in 30 days. See [`2026-06-21/05 §3`](./2026-06-21/05-career-and-startup.md#3-distribution).

→ **Queue 3 cold emails for Monday 8 AM PT send:** Anthropic Solutions / FDE recruiter · OpenAI FDE recruiter · an engineer at NAVER / Samsung SDS / Channel Corp. One paragraph each, link the bundle, reference the relevant pattern (Seoul rollout / multi-protocol portability / in-region Bedrock data-controls).

→ **Upgrade Claude Code to 2.1.183** (10 min) — hardened auto-mode defaults + Azure Foundry prompt-cache fix; re-baseline your `cost.md` post-upgrade. See [`2026-06-21/03 §1`](./2026-06-21/03-practical-skills-and-tools.md#1-cc-2-1-183).
