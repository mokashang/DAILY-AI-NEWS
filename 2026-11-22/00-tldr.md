# TL;DR — 2026-11-22 (Sunday)

Sixty-second skim. **This was the IPO week — Anthropic priced on Wednesday, debuted on Thursday, and the whole market re-priced around it.** On **Nov 18 Anthropic priced the ANT IPO at $83** (above the $70–78 range), selling 980M shares to raise **$81.3B — the largest US tech IPO ever**. **Nov 19 Nasdaq debut opened at $111.50 (+34%)**, closed day one at **$97.17 (+17%)**, giving the lab a **~$1.5T intraday mark** (then settled lower day two, trading near $85). Same week, **NVIDIA reported FQ3'27 at $115.8B revenue (+103% YoY)**, said **Vera Rubin NVL72 is in the fastest product ramp in company history** (racks at CoreWeave, Azure, OCI, Nebius, SpaceX), guided **$130B** for next quarter, and now has **$390B of supply commitments on the books**. **OpenAI shipped GPT-6.2 Astra and Sol on Nov 17** — Astra at the same **$8/$40 per M** pricing Anthropic set with Fable 5.2, and **the first OpenAI model rated "High" on AI Self-Improvement** under the Preparedness Framework — plus a **NATO Daybreak partnership, ChatGPT Wallet (agentic card-token purchases with biometric approval), an Accounting plugin, and MedChemBench**. **Google shipped Gemini 4 Neon on Nov 18** (fourth Gemini 4 model in under two months, slotting between Carbon and Hydrogen). Funding underneath: **Isomorphic Labs $5B Series C (Sequoia + Greenoaks, ~$50B), Model ML $250M Series B (General Atlantic + QED), LanceDB $57.5M (Bessemer), Linq $90M (a16z)**. **Kimi K3.1 Pro weights are live on Hugging Face**, extending the non-US open-weight lead at coding. Practical: **Claude Code 2.1.328** adds mcp_tool `onFailure: block` hooks + skill-hook limits + SessionStart skill rescan; **AWS re:Invent kicks off Nov 30**. For you: **the Anthropic lockup clock just started — Q2 2027 is officially the biggest "ex-Anthropic researcher" seed window of the cycle**, FDE comp bands crystallized with **Levels.fyi median $225K TC**, and the **MSFT Dec 1 buyout deadline is 9 days away**. If you're applying anywhere, this week is the window.

---

1. **Anthropic prices ANT at $83, debuts Nov 19 at $111.50 (+34%), ~$1.5T intraday mark, $81.3B raised — largest US tech IPO ever.** Sale of 980M shares priced above the $70–78 range. Day-one close $97.17 (+17%). Day-two drift ~9% lower but held above the offering price. Last private mark was ~$965B (Series H, May), so the IPO priced **~55% above** the last private round. **Lockup clock officially starts Nov 19 — Q2 2027 (May) is the "ex-Anthropic researcher" seed window.** → [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo) `#anthropic #ipo #comp #lockup`

2. **NVIDIA FQ3'27 (Nov 17): $115.8B revenue (+103% YoY), Vera Rubin NVL72 is the fastest ramp in company history.** Data center $107.6B (+110% YoY). Q4 guide **$130B**. Supply commitments jumped to **$390B** (from $279B). Vera Rubin racks live at **CoreWeave, Google Cloud, Azure, OCI, Nebius, SpaceX**. Management says supply is a **bottleneck through end of FY28**. → [`01` §2](./01-big-lab-moves.md#2-nvidia-fq3) `#nvidia #earnings #rubin #infra`

3. **OpenAI GPT-6.2 Astra + Sol (Nov 17); Astra is the first model ever rated "High" on AI Self-Improvement under the Preparedness Framework.** Astra API $8/M input, $40/M output — **exact match to Claude Fable 5.2** (flagship pricing has converged). Sol is the volume model (price not disclosed in secondary coverage). Astra's "High" threshold tripwires additional safeguards per OpenAI's own policy — **the first time a frontier model has crossed its self-improvement threshold publicly**. → [`01` §3](./01-big-lab-moves.md#3-openai-gpt-6-2) `#openai #safety #preparedness #comp`

4. **OpenAI × NATO Daybreak (Nov 17):** NATO's NCI Agency gets access to OpenAI cybersecurity models under the Daybreak program — first explicit multi-nation defense deal for a US frontier lab. **ChatGPT Wallet** (Nov 13, US Pro) lets agents buy things with card-network tokens, biometric per purchase. **Accounting plugin** Nov 18, **MedChemBench** Nov 20, **ChatGPT Space** global Plus rollout Nov 20. → [`01` §3](./01-big-lab-moves.md#3-openai-gpt-6-2) `#openai #defense #agents #payments`

5. **Google Gemini 4 Neon (Nov 18) — fourth Gemini 4 model in under two months.** Slots between **Carbon (deeper reasoning, Nov 10)** and **Hydrogen (faster execution, Nov 12)**. Rolled out via API, AI Studio, enterprise. Pichai had publicly committed to a **near-monthly Gemini cadence** — he's shipping on it. → [`01` §4](./01-big-lab-moves.md#4-gemini-4-neon) `#google #gemini #cadence`

6. **Isomorphic Labs $5B Series C (~Nov 16) at ~$50B.** Sequoia + Greenoaks co-lead. The Alphabet-spin-out drug-discovery lab is now priced at **2.4× its May 2026 $2.1B round valuation** — the fastest valuation step-up of 2026 in frontier-model-adjacent companies. **Isomorphic is now worth more than most frontier model labs other than the top three**. → [`02` §1](./02-new-emerging.md#1-isomorphic-labs) `#funding #drug-discovery #alphabet`

7. **Model ML $250M Series B at ?B (Nov 17).** General Atlantic + QED Investors co-lead. **LanceDB $57.5M Series B (Nov 17)** led by Bessemer + Innovation Endeavors — vector DB layer still has open-market headroom. **Linq $90M Series B (Nov 18)** led by a16z. → [`02` §2](./02-new-emerging.md#2-model-ml) · [`02` §3](./02-new-emerging.md#3-lancedb) `#funding #vectordb #a16z`

8. **Kimi K3.1 Pro weights land on Hugging Face (Nov 2–6, API Oct 23); Moonshot's custom "Kimi K3.1 Pro License."** Extends the non-US open-weight lead at coding first visible with Kimi K3, GLM 5.3, and Qwen 3.8. **Open-weight frontier is still non-US. The window to start a company on a Chinese open model is widening, not closing.** → [`02` §4](./02-new-emerging.md#4-kimi-k31-pro) `#china #open-weight #kimi`

9. **Research: CoMPASS multi-turn parasocial-behavior benchmark (arXiv 2611.25109);** **Pro² Agent sets new MLE-Bench record (70.7% at 24h, 76.0% at 48h);** **OpenAI claims 14% improvement over heavily-optimized baseline AMD GPU circuits (Nov 18);** **DeltaTTG token-to-go progress meter (arXiv 2610.17666);** **Tev long-horizon agentic environments with dense progress rewards (arXiv 2610.18868).** → [`04`](./04-research-progress.md) `#arxiv #benchmarks #safety #automl #hardware`

10. **Practical this week: (a) Claude Code 2.1.328** adds **`onFailure: block` for mcp_tool hooks** (parity with command + HTTP hooks) + **1,024-hook / 16,384-matcher-char limits per skill source** + **SessionStart `rescanSkills` flag** (hook-installed skills become available *in the same session*). (b) **MedChemBench** is the first OpenAI benchmark released alongside a product plug-in (Accounting) — signals "benchmarks ship with verticals" is the new pattern. (c) **ChatGPT Wallet** proves the agent-payment UX wants **per-transaction biometric**, not session-level auth. → [`03`](./03-practical-skills-and-tools.md) `#claude-code #hooks #skills #mcp #agent-payments`

11. **MSFT voluntary-buyout deadline is Dec 1 — 9 days away.** No change in the terms since Oct 26 filing; industry baseline 3–5% uptake = **1,800–3,000 ex-MSFT engineers hit the market Jan 1**. **If you haven't applied to Azure-AI-alumni-heavy startups yet, this week is the window before the January swamp.** → [`05` §1](./05-career-and-startup.md#1-msft-buyout) `#msft #timing #jobs`

12. **FDE comp bands crystallized: Levels.fyi median FDE TC $225K (Nov 2026); Palantir new grad $135–$145K base; median posted base $150–$215K across 60 US postings Oct–Nov 2026.** Post-IPO, **Anthropic FDE grants are now auditable via ANT trading price** — negotiation leverage just went up materially. → [`05` §2](./05-career-and-startup.md#2-fde-comp) `#fde #careers #comp`

13. **AWS re:Invent Nov 30 – Dec 4** kicks off the next news cycle. Five keynotes; **Bedrock + Kiro + agents** are the expected product spine. **Pre-position your interview talking points** on Bedrock multi-model routing and agent-orchestration cost control — those will be the dominant interview questions at AWS-adjacent AI startups for the next 6 weeks. → [`05` §4](./05-career-and-startup.md#4-aws-reinvent) `#aws #reinvent #interviews`

14. **The re-price of the week: the $8/$40 top-tier API pricing is now the market.** Claude Fable 5.2, GPT-6.2 Astra, and Gemini 4 Neon all converge at or near **$8 input / $40 output per M tokens**. **Pricing differentiation is dead at the frontier; routing and workflow are the remaining moats.** Skills re-pricing *up* this week: **MCP server authoring, eval harness design, agent payment-UX, GPU-kernel perf (Rubin-aware), FDE customer-discovery craft**. Re-pricing *down*: **per-model wrapper products, generic "AI accounting" apps (OpenAI owns the plugin now), raw prompting fluency**. → [`05`](./05-career-and-startup.md) `#careers #skills #reprice`

---

## One thing to DO this Sunday

→ **Send 3 cold emails to ex-Palantir / ex-Anthropic / ex-OpenAI FDEs on LinkedIn today — before the Nov 24 week starts.** Template: 2 sentences on why the Anthropic IPO changes the FDE market (lockup clock, ANT-based grants auditable), 2 sentences on your target role, 1 ask (15-min call). Then **submit 1 application to a company on the Ramp Nov 2026 top-30 AI-vendor list** — those are the only companies with confirmed revenue growth to backstop the headcount. Details in [`05` §2](./05-career-and-startup.md#2-fde-comp).

## Watchlist deltas

- 🆕 **ANT ticker live:** new thread. Track the 30-day price, lockup expiry (~May 2027), and the first wave of ex-Anthropic engineers to publicly open side-projects.
- 🆕 **GPT-6.2 Astra "High" on AI Self-Improvement:** new thread. Watch which safeguards get triggered, whether OpenAI publishes a new safety-eval card, and if any API throttling results.
- 🆕 **$8/$40 flagship pricing floor:** new thread. Watch whether Gemini 4 Hydrogen / Sol / Fable 5.2 Lite differentiate by pricing *under* that — and which labs break the convergence first.
- 🆕 **NVIDIA $390B supply commitments:** new thread. Watch whether memory or packaging (HBM, CoWoS) becomes the next-named bottleneck in Q1 earnings.
- 🆕 **OpenAI × NATO Daybreak:** new thread. Watch which EU state buys first and whether Anthropic counters with a sovereign deal (UK AISI expansion is the obvious watch).
- 🆕 **ChatGPT Wallet agent payments:** new thread. Watch Stripe / Visa / Mastercard public statements and whether Anthropic ships a payment surface for Claude Meetings.
- 🆕 **Isomorphic $50B mark:** new thread. Watch whether this re-opens the "spin-out from Alphabet" playbook — expect Google X/DeepMind side projects to get pitched to Sequoia at inflated marks.
- 🆕 **Kimi K3.1 Pro HF weights:** new thread. Track monthly downloads, first western startup to ship on it in production, and any US-side legal friction over license terms.
- 🆕 **mcp_tool `onFailure: block` + skill-hook limits:** new thread. Watch for the first open-source `.claude/hooks/` template repo over 500 stars.
- ➡️ **FDE lane (from 2026-11-14):** comp bands now crystallized via Levels.fyi. Keep applying; post-IPO Anthropic will have the most legible grants in the market.
- ➡️ **MSFT buyout window (from 2026-11-14):** 9 days left. Pre-position applications this week.
- ➡️ **Gemini 4 cadence (from 2026-11-14):** Carbon → Hydrogen → Neon in 8 days. The "well before end of 2026" promise from Kavukcuoglu is now overdelivered.
- ⬇️ **"Latest flagship fluency":** fully deprecated. Fable 5.2, Astra, Neon all at ~$8/$40. **Routing is the whole job.**
- ⬇️ **Generic AI accounting wrappers:** OpenAI shipped the Accounting plugin. Pivot to vertical finance (close automation, audit, compliance) or get run over.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo) (ANT debut) |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) + [`05` §1–2](./05-career-and-startup.md) — IPO + NVIDIA + GPT-6.2 + MSFT-wave + FDE |
| Today | [`05` §2](./05-career-and-startup.md#2-fde-comp) — 3 cold emails + 1 FDE application |
| This weekend | [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-2-1-328) — ship an MCP-hook template repo (the #1 portfolio artifact for FDE applications is now `.claude/hooks/`) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
