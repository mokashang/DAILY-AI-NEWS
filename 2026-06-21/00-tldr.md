# TL;DR — 2026-06-21 (Sunday)

Sixty-second skim. **The talent map snapped back, the protocol surface hardened, and the policy cliff turned into an empty room.** Three structural moves cut through the noise: **(a) Noam Shazeer — co-author of "Attention Is All You Need" and Google's Gemini co-lead — left for OpenAI on Thursday (June 18)** to lead next-gen architecture research; combined with **Karpathy → Anthropic (May 19)** the two largest talent flips of 2026 now point in *opposite* directions, which is the most-watched leading indicator for who ships the next frontier model. **(b) The MCP `2026-07-28` Release Candidate dropped Thursday** — the **Tasks** primitive, **MCP Apps**, **stateless core**, and **OAuth Resource Server hardening** — and the `@modelcontextprotocol/sdk` npm package now does **35.5M weekly downloads, more than the OpenAI and Anthropic SDKs combined**. MCP is the integration layer. **(c) Fable 5 + Mythos 5 access was restored June 18** after a 6-day US-government-forced suspension; in the *same week*, **Fable 5 took #1 on DeepSWE at 70% pass@1** and the **Artificial Analysis Intelligence Index re-weighted to 34% agents** with **Opus 4.8 at the top (65.7)**. The Anthropic stack came out of a federal speed-bump measurably stronger. **The Sunday move: ship a public MCP server *to the 2026-07-28 RC spec* (Tasks + auth profile + .mcpb bundle), post the write-up, and update the one LinkedIn skill nobody else has yet — "MCP Tasks / Apps".**

---

1. **Noam Shazeer leaves Google for OpenAI as "Lead for Architecture Research."** Announced on X just after midnight PT, **June 18, 2026**. Google paid ~**$2.7B in 2024** to bring him back from Character.AI; Sam Altman called the hire "only 10 years in the making." The talent map now has **Karpathy at Anthropic pre-training** and **Shazeer at OpenAI architecture** — opposite poles, both seated. → [`01` §1](./01-big-lab-moves.md#1-shazeer) `#openai #talent #pretraining #architecture`

2. **MCP `2026-07-28` Release Candidate is live (June 18).** Adds **Tasks** (durable, resumable agent invocations), **MCP Apps**, a **stateless protocol core**, and **OAuth 2.1 Resource Server** classification with **resource indicators** preventing token reuse across servers. Registry now hosts **~2,000 servers**; `@modelcontextprotocol/sdk` npm: **35.5M downloads/week** (more than `openai` + `@anthropic-ai/sdk` combined). Final spec ships **July 28**. → [`02` §1](./02-new-emerging.md#1-mcp-rc) `#mcp #standards #agents #auth`

3. **Fable 5 + Mythos 5 access restored — June 18, ~6 days after the export-control suspension.** Anthropic's MD International told Seoul press hours earlier: "We are very confident that in the coming days, the models will become available again." The Public Record stands as a transparency precedent. Net effect: **policy shock survived; Seoul partner roster signed *during* the outage** — enterprise demand is not elasticity-bound by a 6-day frontier-model interruption. → [`01` §2](./01-big-lab-moves.md#2-fable-restored) `#anthropic #policy #export-controls`

4. **Fable 5 takes #1 on DeepSWE: 70% pass@1 ±4% (leaderboard updated June 20).** Long-horizon software-engineering benchmark, **113 tasks · 91 repos · 5 languages**, isolated containers + **program-based verifiers** (added after a known earlier Opus loophole). GPT-5.5 at 67% ±6%. Coding-agent SOTA visibly shifted to Anthropic during the same week Fable was *unavailable*. → [`04` §1](./04-research-progress.md#1-deepswe) `#benchmarks #claude-code #anthropic`

5. **Artificial Analysis re-weights its Intelligence Index toward agents (June 18).** New mix: **Agents 34% · Coding 24% · Scientific Reasoning 24% · General 18%** (AA-Omniscience split into Accuracy 8% + Non-Hallucination 4%). Current top: **Opus 4.8 (65.7)**, Opus 4.7 (62.5), GPT-5.5 (62.3). The industry's default "which model is best" number is now an *agent* number — exactly the skill stack you've been building. → [`04` §2](./04-research-progress.md#2-aa-reweight) `#benchmarks #methodology #agents`

6. **Practical: Claude Code 2.1.183 ships hardened auto-mode (June 19).** Blocks destructive ops by default in auto mode: `git reset --hard`, `git checkout -- .`, `git clean -fd`, `git stash drop`, un-authored `--amend`, plus `terraform/pulumi/cdk destroy` unless you named the stack. Also fixes prompt-cache misses on custom `ANTHROPIC_BASE_URL` + Azure Foundry (per-request attestation token was busting cache). **Upgrade tonight before any unattended runs.** → [`03` §1](./03-practical-skills-and-tools.md#1-cc-2-1-183) `#claude-code #safety #cost`

7. **`.mcpb` bundles are the new distribution format.** This week's #1 trending Claude/MCP repo on GitHub — **mvanhorn/last30days-skill** — ships as a one-click `.mcpb` package that installs as `/last30days`. Five of the top-10 trending repos this week are Claude/MCP tools. If your portfolio MCP server doesn't ship a `.mcpb` yet, that's the **30-minute upgrade** with the biggest distribution surface gain. → [`03` §2](./03-practical-skills-and-tools.md#2-mcpb-bundles) `#mcp #packaging #distribution`

8. **Skill read of the week:** Karpathy + Shazeer planting opposite flags, MCP becoming the OS of agent-to-tool, and DeepSWE / AA re-weighting are three faces of one shift: **the frontier-of-frontier is no longer one model — it's an *ecosystem-of-agents-on-a-protocol*.** Price your skills accordingly: **MCP authorship · agent verification · cost-aware orchestration**, in that order. → [`05` §1](./05-career-and-startup.md#1-talent-and-protocol) `#skills #careers`

---

## One thing to DO this Sunday

→ **Ship a public MCP server *to the `2026-07-28` RC spec*** — implement at least one **Task** (long-running, resumable), wire the **OAuth 2.1 Resource Server** auth profile, ship as a **`.mcpb` bundle**, and include a 5-case eval that cites the MCP-Atlas methodology ([`04` §3](./04-research-progress.md#3-mcp-atlas)). README headline: *"An MCP server built to the 2026-07-28 RC: Tasks + RS-auth + per-step cost trace."* Then **post LinkedIn + Hacker News** ([`05` §3](./05-career-and-startup.md#3-distribution)) and **queue 3 cold emails to NAVER / Samsung SDS / Anthropic Solutions for Monday-AM send** referencing the artifact. *One weekend, three interview answers (MCP authorship, real-tool eval, cost discipline) — plus a recruiter-search-keyword ("MCP Tasks") that nobody else has yet.*

## Watchlist deltas

- 🆕 **Shazeer → OpenAI (Architecture Research):** new thread. Watch (a) which Google Gemini sub-team members follow him, (b) the first OpenAI architecture paper post-arrival, (c) whether Demis publicly counter-frames. **Pair with Karpathy → Anthropic — the two largest talent flips of 2026, opposite directions.**
- 🆕 **MCP `2026-07-28` RC (Tasks · MCP Apps · stateless core · OAuth RS):** new thread. Final spec lands July 28; the 35.5M weekly SDK download number is the headline data point.
- ✅ **Fable 5 / Mythos 5 export-control suspension RESOLVED** ([2026-06-20 §2 Public Record](../2026-06-20/01-big-lab-moves.md#2-public-record)) — restored June 18. Watch persists: precedent value of the Public Record as a transparency channel; whether a similar directive lands on an OpenAI/Google peer.
- ➡️ **DeepSWE leaderboard:** Fable 5 at #1 (70%) — coding-agent SOTA shifted to Anthropic in the same week the model was offline. Track the next leaderboard refresh post-GPT-5.6.
- ➡️ **Artificial Analysis Index methodology (Agents 34% weight):** monitor whether the rest of the comparison ecosystem (LMSYS, OpenRouter, Helm) follows. Likely yes within 60 days.
- ➡️ **Anthropic Agent SDK metering:** Anthropic **paused** the June 15 rollout (per Help Center + subscriber email). Subscription usage continues unchanged *for now*. Build to the metered economics regardless — the pause is "for now," not "cancelled." Cross-link [2026-05-16/01](../2026-05-16/01-big-lab-moves.md) for the original announcement; [2026-06-16/01 §1](../2026-06-16/01-big-lab-moves.md#1-metering-day-2) was framed pre-pause.
- ➡️ **OpenAI confidential S-1 (June 8) + Anthropic confidential S-1 (June 1):** both filed; quiet-period rules now apply. Watch for first amendment filings and a public roadshow window (Sept for OpenAI / Oct for Anthropic).
- ➡️ **Anthropic Seoul partner roster:** [2026-06-20 §1](../2026-06-20/01-big-lab-moves.md#1-seoul) — NAVER, Samsung SDS, LG CNS, Nexon, Hanwha, Channel Corp. Watch for the first FDE postings tagged to APAC enterprise rollout.
- 🆕 **`.mcpb` bundles as distribution format:** new thread. Track adoption count in the MCP registry; whether Claude Desktop / Cursor / Devin standardize on `.mcpb` install.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the Shazeer hire + MCP RC in [`01` §1](./01-big-lab-moves.md#1-shazeer) and [`02` §1](./02-new-emerging.md#1-mcp-rc) |
| 20 min | [`04` §1 DeepSWE](./04-research-progress.md#1-deepswe) + [`04` §2 AA re-weight](./04-research-progress.md#2-aa-reweight) (the two benchmark moves reframe "best model") |
| Tonight | [`03` §1 Claude Code 2.1.183](./03-practical-skills-and-tools.md#1-cc-2-1-183) — upgrade + run one auto-mode session safely |
| Weekend | [`05` §3 weekend artifact](./05-career-and-startup.md#3-distribution) — ship the MCP server to the RC, post it, queue Mon-AM cold emails |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
