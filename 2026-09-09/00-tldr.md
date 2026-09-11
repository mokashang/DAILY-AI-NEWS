# TL;DR — 2026-09-09 (Wednesday)

Sixty-second skim. **The frontier just made a claim on a Millennium Prize, Anthropic quietly locked in the biggest compute contract of the year, and Cognition doubled its price tag in four months.** **OpenAI claims a Navier–Stokes proof produced in 88 hours by ~10,000 agents** — the biggest "general model does open math" claim since the Erdős result in May, but overshadowed within 12 hours by a rival Buckmaster (NYU) / Alpöge (Anthropic) preprint and a public credit fight. **Anthropic × Google × Broadcom = up to 3.5 GW of next-gen TPU capacity** starting 2027 — Anthropic's biggest single compute commitment ever, sitting on top of a run rate now above $65B. **Cognition raised $2B Series E at $48B — up from $26B four months ago** — with a syndicate including a16z, Accel, Founders Fund, General Catalyst, Nvidia, and ~30 others. And after **Fable 5.1's 75% cache-read cut (Sept 1)**, the operating cost of an agent team just dropped again on the workhorse tier.

*(Previous edition: [2026-09-08](../2026-09-08/) (Mistral €3B / five-pole frontier). Today extends the Fable 5.1 + Anthropic-IPO threads and adds the Navier–Stokes head-to-head + the 3.5 GW TPU commitment.)*

---

1. **OpenAI claims a Navier–Stokes proof — 88 hours, ~10,000 concurrent agents, one unreleased model.** Configuration described: a vortex tightens and spins ever faster (finite-time blowup) with bounded energy. Verified in part; **12 hours after the OpenAI post, Tristan Buckmaster (NYU) + Levent Alpöge (Anthropic) posted their own resolution of tightly related problems**, and Buckmaster went public with accusations that OpenAI's timing pre-empted their credit. First prominent open problem where two frontier-lab pipelines converge on the same target the same week. → [`01` §1](./01-big-lab-moves.md#1-navier-stokes) · [`04` §1](./04-research-progress.md#1-math-agents) `#openai #anthropic #math #agents #ai-for-science`

2. **Anthropic × Google × Broadcom: multi-gigawatt TPU deal, ~3.5 GW starting 2027.** Anthropic's largest single compute commitment; vast majority sited in the US. Sits on top of the November-2025 $50B domestic-compute pledge and Anthropic's run-rate revenue (~$65B at end of July). *Reads as*: the "three-lab market" bet from [2026-07-25](../2026-07-25/00-tldr.md) is now underwritten with silicon. → [`01` §2](./01-big-lab-moves.md#2-anthropic-tpu) `#anthropic #google #broadcom #tpu #compute`

3. **Cognition raises $2B Series E at $48B — up from $26B four months ago.** Announced 2026-09-08. Andreessen Horowitz + Accel lead; Founders Fund, General Catalyst, Avenir, Benchmark, Bessemer, Kleiner, Greylock, Lightspeed, Altimeter, Bond, T. Rowe Price, DST, NVIDIA, and ~25 others participate. Run-rate revenue reportedly grew from ~$492M (May) to ~$900M. **Devin as the reference agent for full-lifecycle coding — and the price of buying "an autonomous engineer" just went up ~85%.** → [`02` §1](./02-new-emerging.md#1-cognition-2b) · [`05` §3](./05-career-and-startup.md#3-cognition-lens) `#cognition #devin #funding #coding-agents`

4. **Anthropic Fable 5.1 + Mythos 5.1 shipped 2026-09-01 — cache-read pricing cut 75%.** Cache reads now $0.25/MTok (from $1.00). Anthropic's own math: ~25% cheaper for typical workloads, **up to ~45% cheaper for highly-agentic workloads**. 1M context, 128K output, adaptive thinking on by default. Mythos 5.1 (defense/security-research gated) drops many refusal categories. **The workhorse just repriced again** — every agent workflow you built in July is now materially cheaper without a line of code change. → [`01` §3](./01-big-lab-moves.md#3-fable-51) · [`03` §1](./03-practical-skills-and-tools.md#1-cache-reads) `#anthropic #fable-51 #pricing #caching`

5. **"Model fatigue" — Anthropic, OpenAI, Meta, and Google all shipped new models the same week (early Sept).** CNBC's framing: the release cadence has outrun the enterprise adoption cycle; buyers can no longer keep up. **Ship-cadence risk is real for your resume too** — the SKU on your portfolio decays in weeks now, not quarters. Move to *capabilities* (effort routing, cache design, verifier composition) that outlive any one model. → [`01` §4](./01-big-lab-moves.md#4-model-fatigue) · [`05` §2](./05-career-and-startup.md#2-model-fatigue-lens) `#labs #models #cadence #careers`

6. **Anthropic IPO prospectus expected post-Labor Day; late-Sept / early-Oct listing window; NYT reports a possible $2T target.** Sits alongside OpenAI's own confidentially-filed S-1 targeting ~$1T. A **$15B pre-IPO credit facility** is being finalized. **Two frontier-lab IPOs inside 6 weeks would be the single biggest public-market repricing of AI since the transformer paper.** → [`01` §5](./01-big-lab-moves.md#5-ipos) · [`05` §4](./05-career-and-startup.md#4-ipo-equity-math) `#anthropic #openai #ipo #s1`

7. **The DoD/frontier-lab war-game contracts got a FOIA'd paper trail.** The Intercept obtained 400+ pages of DoD contract documents (originally awarded July 2025, ~$200M ceiling each to OpenAI, Anthropic, Google, xAI). Documents show **bidirectional data exchange** (frontier-model benchmarks shared to DoD; joint tabletop wargames). This is the operating substrate under the coming "pre-deployment eval" job market — the seam is now legible on paper. → [`01` §6](./01-big-lab-moves.md#6-dod-foia) · [`05` §5](./05-career-and-startup.md#5-dod-pipeline) `#dod #policy #safety #pre-deployment-eval`

8. **Research: (a) OpenAI's Navier–Stokes paper posted alongside Buckmaster + Alpöge's independent resolution — the "AI-for-open-math" bench is now real. (b) MCP 2026-07-28 stateless spec is now the deployment floor; the retrofits are all posted. (c) Two multi-agent papers to read this weekend: *Agentifying Agentic AI* (WMAC 2026) and *AutoNumerics* (an end-to-end PDE-solver agent).** → [`04` §1–3](./04-research-progress.md#1-math-agents) `#arxiv #benchmarks #agents #mcp`

---

## One thing to DO this Wednesday evening

→ **Do one of the two Anthropic-facing moves tonight, and one artifact this weekend.**

1. **Tonight (30 min) — enable prompt caching on your current Claude project.** Fable 5.1's 75% cache-read discount ([`03` §1](./03-practical-skills-and-tools.md#1-cache-reads)) is a free win if your prompts have any stable prefix (system prompt, tools list, examples). This is the highest-ROI single toggle in AI this month. Screenshot the per-call cost before + after for your portfolio.

2. **Tonight (10 min) — refresh your LinkedIn keyword line to include:** `Fable 5.1 · effort routing · MCP 2026-07-28 stateless · prompt caching · Anthropic Applied AI · FDE`. FDE demand is up **>1,000% YoY** and postings ~1,500 US roles at ~$300–550K TC ([`05` §1](./05-career-and-startup.md#1-fde-market)) — the SEO-match is the cheapest funnel step.

3. **Weekend (2–3 hours) — ship the "cache-first agent" artifact.** One repo: a Fable 5.1 orchestrator with a stable system prompt (cache-write once), Sonnet 5 workers hitting a fresh MCP 2026-07-28 stateless server, and a Haiku 4.5 verifier per step. Log per-call `(input_tokens, cache_read_tokens, cache_write_tokens, output_tokens, effort)` to CSV — one repo answers three FDE interview questions: orchestration, cost predictability, real-tool verification.

## Watchlist deltas since the 2026-09-08 edition

*One day forward. Threads that moved today:*

- 🆕 **Navier–Stokes / AI-for-open-math** — new thread today. First head-to-head between two frontier-lab pipelines on a Millennium-class problem, plus a public credit fight. Follow: the arXiv Alpöge/Buckmaster paper, the Terry Tao commentary thread. Extends the "Claude × Fermat's Last Theorem in Lean" thread from [2026-09-07](../2026-09-07/).
- 🆕 **Anthropic × Google × Broadcom ~3.5 GW TPU deal** — new today. Anthropic's largest single compute commitment; underwrites the five-pole frontier framing from [2026-09-08](../2026-09-08/) with Anthropic-side silicon.
- ➡️ **Fable 5.1 cache-read cut** — carrying forward from Sept 1. The 25–45% cost cut has now been publicly framed; the *migration action* is more urgent as more teams see the number. Ties directly to today's Cognition round pricing.
- 🆕 **Cognition $2B at $48B (Sept 8)** — new/updated thread; ~2× valuation in ~4 months; ARR ~$492M → ~$900M; NVIDIA in syndicate. Follow whether Devin adoption dents Claude Code / Cursor share.
- ➡️ **FDE market** — postings ~1,500 US roles, TC bands cluster $300–550K with principal >$1M. Extends [2026-09-06](../2026-09-06/)'s "982 live postings / 462 companies" trace; category is still under-supplied.
- ➡️ **Anthropic IPO** — post-Labor Day prospectus + $15B pre-IPO credit facility (Bloomberg Sept 3) + NYT $2T ceiling. Extends the S-1 thread from [2026-09-05](../2026-09-05/) and [2026-05-22](../2026-05-22/).
- 🆕 **"Model fatigue"** — new CNBC framing (Sept 6). Watch enterprise pricing power vs. release cadence.
- 🆕 **DoD/frontier-lab FOIA docs** — new thread. The pre-deployment-eval job market is now legible in contract-line detail.
- ⬇️ **MCP 2026-07-28 stateless spec** — no longer news; the operating floor. What matters now is who has migrated (see [`03` §2](./03-practical-skills-and-tools.md#2-mcp-migration)).

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Navier–Stokes in [`01` §1](./01-big-lab-moves.md#1-navier-stokes) + cache-read cut in [`03` §1](./03-practical-skills-and-tools.md#1-cache-reads) |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) (Navier–Stokes + TPU deal + Fable 5.1) + [`02` §1](./02-new-emerging.md#1-cognition-2b) (Cognition) + [`03` §1](./03-practical-skills-and-tools.md#1-cache-reads) (caching migration) — the four signals that changed your near-term plan |
| Tonight | [`03` §1](./03-practical-skills-and-tools.md#1-cache-reads) — enable prompt caching + [`05` §1](./05-career-and-startup.md#1-fde-market) — refresh LinkedIn keyword line |
| Weekend | [`03` §4](./03-practical-skills-and-tools.md#4-weekend-artifact) — ship the cache-first agent artifact |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
