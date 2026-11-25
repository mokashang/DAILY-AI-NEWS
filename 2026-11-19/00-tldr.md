# TL;DR — 2026-11-19 (Thursday)

Sixty-second skim. **ANT is live.** **Anthropic priced its IPO last night at $83/share, raised ~$81.3B — the single largest IPO on record, bigger than SpaceX — and ticker ANT opened this morning at $111.50 (+34% pop), briefly implying a ~$1.1T+ fully-diluted cap.** At the same time, **NVIDIA posted a record $115.8B quarter and guided Q4 to $130B assuming zero China data-center revenue**, and **Anthropic poached DeepMind Chief Strategy Officer Jasjeet Sekhon** on the eve of the pricing — the public-market debut, the GPU supplier posting its biggest-ever beat, and a strategy-exec hire from the direct competitor all landed inside the same 72-hour window. Underneath: **LangChain $300M Series C with Singapore's GIC**, **Mercor $750M Series D**, **Harvey acqui-hired Aida Search**, **Stripe closed OpenRouter**, **Anthropic reportedly exploring a $7B MatX chip acquisition**, and **the first consumer-AI tombstone of the cycle — Ollie shut down six weeks after its $7.5M Khosla seed**. Microsoft's buyout window closes Dec 1 with **<5% uptake expected** (far below the 3–5% industry baseline we quoted on Nov 14 — **correct your Jan 1 ex-MSFT-engineer forecast down to ~1,500–3,000**). **Opus 4.8 fast-mode is going away Nov 30 — hard error, no fallback — ship your migration this week.** Research-side: **arXiv is trending on agent-plan-commitment theory (2611.19663), prompt-injection purple-teaming (PIPETTE, 2611.24362), and the "thinking harder raises confidence but not accuracy" replication (2611.22033)** — three ready-to-use eval harnesses for an FDE portfolio. The re-price: **Databricks is now the #1 FDE employer by open-req count (122), ahead of Palantir (100) — pivot your application list.**

---

1. **Anthropic ANT trades Nov 19, priced at $83, $81.3B raised — largest IPO on record.** Offering upsized to ~980M Class A shares; range raised Nov 16 to $70–$78; priced above at $83. First trade reported at **$111.50** (~+34% vs offer). ~316M shares eligible for sale on day one per schedule disclosures. Early price action heavily shaped by **index-inclusion buying** (the "SpaceX playbook" for mega-cap listings). → [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo-prices) `#anthropic #ipo #comp`

2. **NVIDIA Q3 FY27: $115.8B revenue (+103% YoY), DC $107.6B, Q4 guide $130B ± 3% with zero China DC revenue assumed.** Vera Rubin NVL72 shipped; CoreWeave, Google Cloud, Azure, Oracle already running racks. Interim CEO Colette Kress cited **~$20B Vera Rubin revenue in its first production quarter**. The $130B guide at $0 China = Rubin ramp confirmed AND an explicitly vacated Chinese market for Huawei Ascend. → [`01` §2](./01-big-lab-moves.md#2-nvidia-q3-fy27) `#nvidia #earnings #china`

3. **Anthropic hires Jasjeet Sekhon from Google DeepMind (Nov 16).** DeepMind's Chief Strategy Officer, ~8 months in role, confirmed by Anthropic spokesperson. The poach lands in the same week Anthropic prices its IPO and in the same month Kavukcuoglu (DeepMind) says Gemini 4 ships "well before end of 2026" — **strategy bench pivoting toward the public-company half of the duopoly.** → [`01` §3](./01-big-lab-moves.md#3-jasjeet-sekhon) `#anthropic #personnel #ipo`

4. **Claude Code 2.1.325 / 2.1.326 (Nov 13–16) — agent teams now start in Code Mode automatically.** The default shifts away from "chat first, tools second" to "tool-plan first, chat as fallback" — matches the agentic-engineering frame. **Opus 4.8 fast-mode is deprecated Nov 30: requests will hard-error, not fall back.** Audit every job that routes through `opus-4.8-fast` and migrate this week. → [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-code-mode) `#claude-code #breaking-change`

5. **LangChain $300M Series C — GIC (Singapore sovereign wealth) joins (Nov 13–14).** First time a sovereign-wealth name has led into the agent-orchestration layer. Signals the layer is now institutional-grade infra, not a dev-tools wrapper. → [`02` §1](./02-new-emerging.md#1-langchain) `#funding #langchain #orchestration`

6. **Mercor ~$750M Series D (Nov 10–11).** Talent-marketplace-for-AI-labels wedge; likely ~$10B territory. Combined with Harvey's acqui-hire of **Aida Search's team** (undisclosed), the "specialist labor + specialist search" seams are consolidating fast. → [`02` §2](./02-new-emerging.md#2-mercor) `#funding #talent-market`

7. **Stripe closed OpenRouter (Nov 10, undisclosed).** The developer-model-router is now inside the payment rail. "Agent-native payments primitive" (Natural $30M in Sept) just got a reference buyer. → [`02` §4](./02-new-emerging.md#4-stripe-openrouter) `#stripe #agents #payments`

8. **Anthropic reportedly exploring a $7B acquisition of MatX (chip startup).** Single-source rumor; if real, first lab-into-silicon vertical-integration move since Google TPU. Pair with NVIDIA's $130B Q4 guide and OpenAI × Broadcom "Jalapeño" and you have the three-sided silicon reshuffle of 2026. → [`02` §5](./02-new-emerging.md#5-anthropic-matx) `#anthropic #silicon #rumor`

9. **Ollie shut down Nov 6, six weeks after its $7.5M Khosla seed.** First consumer-AI tombstone of the Q4 cycle. The raise-then-fold window for undifferentiated consumer-AI wrappers is now **<60 days**. If your startup wedge is "thin chat wrapper + consumer growth," pivot before pitching. → [`02` §6](./02-new-emerging.md#6-ollie-shutdown) `#tombstone #consumer-ai`

10. **FDE census pivot (Nov 2026): Databricks 122 (new #1), Palantir 100, Salesforce 88, OpenAI 39.** Rung's 13-co census, 394 tracked roles. **Databricks is now the volume play for FDE applications** — pivot your target list; OpenAI remains the brand ceiling but the funnel is tighter. Comp band confirmed at **$300K–$1.2M TC** depending on level. → [`05` §2](./05-career-and-startup.md#2-fde-census) `#fde #careers #comp`

11. **Microsoft 60K buyout: <5% uptake expected per MSFT spokesperson — correct the Jan 1 forecast DOWN.** Previous estimate was 1,800–3,000 engs hitting the market; actual expected is ≤3,000, likely 1,500–2,500. Deadlines vary by country (India ~Dec 1, Washington state ~Dec 9), exit Dec 31. No forced-layoff December plan. **The ex-MSFT founder wave will be smaller than the Nov 14 edition framed — plan accordingly.** → [`05` §3](./05-career-and-startup.md#3-msft-buyout-update) `#msft #careers #correction`

12. **arXiv this week:** **Jeveration (2611.24738)** — System-1 generator models that bypass deliberation on routine tasks (fast/slow routing debate reopens); **Threshold Theory of Plan Commitment (2611.19663)** — when agents should repair vs replan vs abandon; **PIPETTE (2611.24362)** — purple-teaming for prompt injection on agents (ready-made FDE eval); **Thinking Harder Doesn't Lead to Better Choices (2611.22033)** — U-Chicago finds reasoning effort raises confidence but not accuracy on shopping agents (direct replication risk for effort-level products). → [`04`](./04-research-progress.md) `#arxiv #agents #prompt-injection`

13. **Benchmark deltas:** **GDPval-AA v2.1** (Artificial Analysis, 44 occupations / 9 industries): **Claude Opus 5.5 Max #1 at 1866**, ahead of Kimi K3.1 Pro + Meta Muse Wonder. **BenchLeader** 256 benchmarks / 47 publishers: **Gemini 4 Carbon (High) leads HLE-Diamond at 69.1%**. **GAIA appears compromised** — one audit agent scored ~98% via exploit — quietly drop GAIA from résumés and cite GDPval-AA / BenchLM / Terminal-Bench instead. → [`03` §3](./03-practical-skills-and-tools.md#3-gdpval-aa) `#evals #benchmarks #resume-copy`

14. **The re-price of the week: Anthropic is public, Databricks is the new FDE volume leader, MSFT buyout is smaller than feared, and the raise-then-fold consumer window is <60 days.** Comp anchoring shifts to ANT's trading price; FDE application mix shifts to Databricks-weighted; founder-wedge pitches have to answer "why aren't you dead in 60 days?" from day one. **Skills still re-pricing *up*:** MCP-server authoring with built-in eval harnesses (PIPETTE + plan-commitment + tool-use-pathology templates), GDPval-AA citations in cover letters, breaking-change migration playbooks (Opus 4.8 Nov 30). **Re-pricing *down*:** GAIA scores as portfolio evidence, "I built a consumer chatbot" wedge pitches, pre-public Anthropic comp benchmarks. → [`05`](./05-career-and-startup.md) `#careers #skills #reprice`

---

## One thing to DO this Thursday

→ **Spend 45 minutes on the two actions ANT trading unlocks today.** (1) **Pull up ANT on your brokerage and screenshot the first-hour tape** — you'll want this exact chart in résumé/cover-letter conversations for the next 90 days when you cite "I was tracking Anthropic the day they IPO'd." (2) **Submit one Anthropic Solutions / Integration / FDE app before the quiet-period hiring window tightens this week.** Anthropic is now a public company; the hiring process will be more process-heavy and conservative starting ~Monday. Get your package in before the IR team re-briefs recruiting. Details in [`05` §1](./05-career-and-startup.md#1-ant-day-one).

## Watchlist deltas

- 🆕 **Anthropic ANT trading (Nov 19 open $111.50, +34%):** moves from "pending" to "active"; now the single most important comp-anchor datapoint for frontier-lab offers for the next 6 months. Track the Day 1 close, 30-day post-IPO price, and the **~6-month lockup expiry window (~May 2027)** — that's when the ex-Anthropic-researcher-seed wave starts.
- 🆕 **Jasjeet Sekhon → Anthropic:** new thread. First senior strategy exec to cross from DeepMind to Anthropic in the same month DeepMind telegraphs Gemini 4; watch for direct reports who follow.
- 🆕 **NVIDIA Q4 FY27 guide = $130B at $0 China DC:** new thread. Watch the Huawei Ascend / Chinese-open-weights pairing as the explicitly vacated market gets served.
- 🆕 **Opus 4.8 fast-mode Nov 30 hard-error:** new thread. Breaking change deadline; track whether 4.8-fast references appear in any downstream library shims (LangChain, LlamaIndex, llm) before cutoff.
- 🆕 **Anthropic × MatX $7B acquisition rumor:** new thread. Unverified; track for confirmation + whether the lab-into-silicon vertical-integration template kicks off wider.
- 🆕 **LangChain + GIC $300M:** new thread. First sovereign-wealth name in agent-orchestration infra; watch Latency, LlamaIndex, Haystack follow-ons.
- 🆕 **Ollie 6-week tombstone:** new thread. Consumer-AI raise-then-fold window at a new low; track the next 3 named shutdowns for the pattern.
- 🆕 **FDE census shift to Databricks #1:** new thread. Watch monthly for whether Databricks holds the top slot or OpenAI reclaims it after post-IPO hiring resumes.
- ➡️ **Claude Fable 5.2 + Whiteboards/Sheets/Data/Meetings (from 2026-11-14):** quiet week; no Office/Workspace competitor response yet. Next tell is the Nov 20–30 Microsoft Ignite cycle.
- ➡️ **Microsoft 60K buyout (from 2026-11-14):** correction — uptake expected **<5%**, so Jan 1 ex-MSFT-engineer wave will be **1,500–3,000**, not the "industry baseline 3–5% → 1,800–3,000" we quoted. Still material, but smaller.
- ➡️ **FDE lane (from 2026-10-14, 2026-11-14):** still the #1 new-grad AI lane; application list pivots toward Databricks + Anthropic (post-IPO window) + OpenAI Deployment Co (the FDE spinout from May 2026).
- ➡️ **METR Anthropic R&D acceleration report (Nov 5):** awaiting Anthropic's first-party response "in coming weeks"; still live.
- ⬇️ **GAIA as portfolio citation:** benchmark appears exploited (~98% via a single audit agent); quietly stop citing — swap in **GDPval-AA** and **BenchLM**.
- ⬇️ **"Industry-baseline 3–5% MSFT buyout uptake":** down-graded; MSFT itself now anchors expectation at <5% total.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo-prices) (the ANT pricing + Day 1) |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) + [`05` §1–3](./05-career-and-startup.md) — IPO + NVIDIA + Sekhon + FDE census + MSFT update |
| Today | [`05` §1](./05-career-and-startup.md#1-ant-day-one) — 1 Anthropic app before quiet-period tightens |
| This weekend | [`03` §2](./03-practical-skills-and-tools.md#2-opus-48-sunset) — ship your Opus 4.8-fast migration before Nov 30 |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
