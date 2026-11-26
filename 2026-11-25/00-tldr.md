# TL;DR — 2026-11-25 (Tuesday, day before US Thanksgiving)

Sixty-second skim. **The biggest IPO in history priced six days ago — and today it closed below its offer price.** On **Nov 19 Anthropic (ticker ANT, Nasdaq)** priced **980M shares at $83** (above the $70–$78 range) for an **~$81.3B raise — the largest IPO on record**, opened at **$111.50 (+34%)**, and closed day one at **$97.17 (+17%)**. Six trading days later, **Tuesday Nov 24 closed at $81.91 (-6.54% on the day, -26.5% from debut, below the IPO price)** as the broader AI trade cooled. **NVIDIA's Q3 FY27 (reported Nov 19)** was objectively enormous — **$115.8B revenue, Data Center $107.6B (+110% YoY), Vera Rubin's first production quarter alone shipped ~$20B (fastest ramp in NVIDIA history), Q4 guide $130B ±3% ex-China** — and the stock *still* sold off. The pattern is the story: **fundamentals strong, multiples contracting**. Underneath: **Claude Code 2.1.319 (Nov 6) made auto-mode the default and shipped Agent SDK blocking hooks; 2.1.327 (Nov 17) cut subagent-progress token cost by using short notes instead of full transcripts; Fast mode on Opus 4.8 sunsets Nov 30**. Funding kept moving: **Isomorphic Labs closed $5B Series C (Nov 16)**; **Model ML raised $250M Series B (Nov 17)** co-led by General Atlantic + QED for financial-services AI. Research-side: **Agentic Reasoning Caching (arXiv 2611.09891, Nov 6)** compiles CPU-executable "reasoning caches" from LLM traces — the first serious attempt to decouple reasoning quality from GPU spend. For you: **FDE postings are up ~17× since 2022 (300 → 5,000+)**; **SignalFire's State of Talent 2026 confirms new-grad hiring at the 12 Tech Majors is down ~65% vs. 2019**; **the next 48 hours (pre-Thanksgiving) are a high-signal application window** before recruiters go dark through Dec 1.

---

1. **Anthropic (ANT) priced the biggest IPO ever at $83 — then fell below it inside a week.** 980M Class A shares priced above range on **Nov 19 → $81.3B raised**; opened $111.50, closed day-one $97.17; **Nov 24 close: $81.91 (-26.5% from debut, below offer)**. Fully diluted valuation reporting ranges **$1.4T–$2T**. Staggered lockup (not one-cliff SpaceX-style). On **Nov 20, Dario Amodei and Daniela Amodei each sold ≥3.37M shares to IPO underwriters at $83** per filings. → [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo-debut) `#anthropic #ipo #ant #comp`

2. **NVIDIA Q3 FY27 was a crush — and the stock sold off anyway.** Revenue **$115.8B**, EPS **$2.68** vs **$2.47** est, **Data Center $107.6B (+110% YoY)**. **Vera Rubin's first quarter of shipments alone = ~$20B** (fastest product ramp in NVIDIA history). **Q4 guide $130B ±3%** ex-China; gross margin guided **71–72%** (down from Rubin ramp). Colette Kress remains interim CEO; permanent CEO search open. **Signal: fundamentals strong, multiples contracting — classic late-cycle AI setup.** → [`01` §2](./01-big-lab-moves.md#2-nvidia-q3-fy27) `#nvidia #earnings #chips`

3. **Claude Code shipped three material updates this month.** **v2.1.319 (Nov 6)**: **Auto mode is now the default** — actions the server can't check get prompted or denied, not judged by the built-in classifier; adds MCP task support in the terminal. **v2.1.326**: **Code Mode now works with agent teams**; startup warnings catch malformed tool rules. **v2.1.327 (Nov 17)**: subagent progress summaries on Bedrock/Vertex/Foundry now use **short notes instead of full transcripts** — far fewer tokens. **Fast mode on Opus 4.8 sunsets Nov 30** (requests return an error, no fallback). → [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-nov-cluster) `#claude-code #anthropic #tools`

4. **Isomorphic Labs $5B Series C (Nov 16).** The Alphabet / DeepMind drug-discovery spinout gets the largest biotech-AI round of the year — three-and-a-half years after the $2.1B four-corner template (Lilly + Thrive + GV + Alphabet) in 2026-05. Signal: capital for **AI-for-science** stays flowing even as application-layer wrappers get squeezed. → [`02` §1](./02-new-emerging.md#1-isomorphic-5b) `#funding #bio #science`

5. **Model ML raised $250M Series B (Nov 17)** — **General Atlantic + QED Investors co-lead**. Positions as the **financial-services-first agent platform** (data-room + model-governance for banks and asset managers). Replays the Rox/Decagon pattern in a regulated vertical where logos pay a premium. → [`02` §2](./02-new-emerging.md#2-model-ml) `#funding #fintech #agents`

6. **Google Gemini 4 Argon (launched Sep 30, 2026) continues phased rollout.** Google's DeepMind page now also surfaces **Gemini 4 Carbon** for API/Ultra; coding remains the weakest axis per third-party benchmark aggregators. Anthropic's post-IPO quiet period + Google's incremental drops = **the real Gemini-vs-Claude battleground is December**, not today. → [`01` §3](./01-big-lab-moves.md#3-gemini-4-rollout) `#google #gemini #models`

7. **NVIDIA Q4 guide ($130B) implicitly re-prices "AI chip prices will crash" takes.** Databricks CEO Ali Ghodsi publicly predicted a **"major drop in AI chip prices"** this month. The Q3 beat + Q4 guide does not support that thesis on a 2–3 quarter horizon. **Startup takeaway: don't build a business plan that requires GPU spot-price deflation before 2027H2.** → [`02` §3](./02-new-emerging.md#3-chip-price-debate) `#infra #compute #startups`

8. **Research pick of the week: Agentic Reasoning Caching (ARCs).** arXiv **2611.09891** (Nov 6) shows that LLM reasoning traces can be **compiled into robust CPU-executable caches** — first serious shot at decoupling reasoning quality from GPU spend for repeat workloads (customer support, structured extraction, recurring ops queries). If this generalizes, it reprices the "every agent needs a frontier model" assumption. → [`04` §1](./04-research-progress.md#1-arcs) `#arxiv #efficiency #agents`

9. **MCP: "A More Predictable Release Cycle" (Nov 11).** The protocol-steering group formalizes a **hard freeze one month before release** — only critical security / release-blocking correctness fixes land in that window. Signal: **MCP is treating itself as production infrastructure now**. No new spec after **2026-07-28 stateless**; next release cycle is announced-but-not-dated. → [`03` §2](./03-practical-skills-and-tools.md#2-mcp-release-cycle) `#mcp #protocol #stability`

10. **Entry-level tech hiring at the 12 Tech Majors is down ~65% vs. 2019** (SignalFire State of Talent 2026). **FDE-adjacent postings went from ~300 (2022–23) to 5,000+ (early 2026) — up 30% YoY by title count**. FDE **still requires senior + client-facing experience**, but Pragmatic Engineer's Nov read: *as product companies hire fewer new grads, FDE is the slot new grads have a realistic shot at*. → [`05` §1](./05-career-and-startup.md#1-fde-new-grad-window) `#careers #fde #new-grad`

11. **Thanksgiving-window application tactic.** US Thanksgiving is **tomorrow (Nov 26)**; recruiters go dark Thu–Sun and most of next week (Dec 1 pipelines restart). **Submit before noon ET today** so your application is at the top of the Monday Dec 1 queue when ATS filters re-engage. Priority targets this week: **Anthropic FDE/Solutions, OpenAI FDE, Glean Founding FDE, Distyl, Decagon, Sierra, Harvey**. → [`05` §2](./05-career-and-startup.md#2-thanksgiving-window) `#timing #applications #tactic`

12. **Portfolio re-check.** With ANT now public and MCP freezing into a predictable-cadence standard, **the single highest-leverage weekend artifact is unchanged**: a **public MCP server with a 5-case eval + README + demo clip**, published to GitHub with install-via-FastMCP instructions. This is what FDE/Solutions hiring managers actually ask to see on screens. See [`03` §3](./03-practical-skills-and-tools.md#3-mcp-weekend-artifact). `#portfolio #mcp #fde`

---

## One thing to DO this Tuesday (before Thanksgiving)

→ **Submit 3 FDE/Solutions applications by 12pm ET today.** Rank order: **Anthropic FDE** (newly public → hiring bar might tighten in quiet period, but reqs still open), **Glean Founding FDE** ($160–270K band from last edition), **Distyl** ($150–250K). Use the **ANT IPO + Fable 5.2 Whiteboards/Sheets/Data + Nov 17 Claude Code 2.1.327** as your "why I'm paying attention" talking points in the cover line — it proves you read primary sources. Full playbook in [`05` §2](./05-career-and-startup.md#2-thanksgiving-window).

## Watchlist deltas

- 🆕 **ANT below IPO price inside a week + staggered lockup:** new thread. Track whether the stock finds a floor before year-end and when the first lockup tranche releases (watch the S-1 for the exact schedule).
- 🆕 **NVIDIA $130B Q4 guide (ex-China) + Vera Rubin $20B first quarter:** new thread. Watch whether Q4 actual exceeds guide and whether Rubin CPX long-context SKU becomes the next price-per-ctx-token benchmark.
- 🆕 **Databricks "chip prices will crash" call:** new thread. Watch if any public analyst (SemiAnalysis, Morgan Stanley) picks it up or if NVIDIA's Q4 print kills it.
- 🆕 **Claude Code auto-mode-default + subagent short-notes:** new thread. Watch which teams publish their `.claude/settings.json` + hook templates — new baseline for "safe-by-default" agents.
- 🆕 **ARCs (CPU-executable reasoning caches):** new thread. Track replications on HumanEval+/LiveCodeBench and whether any lab publishes a pre-trained ARC release.
- 🆕 **Isomorphic $5B + AI-for-science capital tier:** new thread. Watch Xaira, EvolutionaryScale, Latent Labs as next in queue.
- 🆕 **MCP "predictable release cycle" freeze:** new thread. Watch which Tier 1 SDK (Python, TS, Go, Rust) ships first after the next spec freeze.
- ➡️ **Fable 5.2 + Whiteboards/Sheets/Data (from 2026-11-14):** quiet-period limits what Anthropic says publicly; expect enterprise rollouts to continue without blog posts until Q1 2027.
- ➡️ **Microsoft 60K buyout, Dec 1 deadline (from 2026-11-14):** **deadline is this Monday**. Expect a wave of ex-MSFT engineers hitting the market Jan 2 — rewrite your résumé top this week.
- ⬇️ **"Latest-model fluency" as a hireable skill:** further deprecated. With ANT public and a tighter frontier-model cadence predicted for 2027, **routing + eval + cost control** is the lane.
- ⬇️ **Non-staggered-lockup IPO playbook:** deprecated. Anthropic's staggered schedule is likely the new default for frontier labs.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo-debut) (ANT debut + Nov 24 selloff) |
| 20 min | [`01` §1–2](./01-big-lab-moves.md) + [`05` §1–2](./05-career-and-startup.md) — ANT + NVIDIA + FDE new-grad window + Thanksgiving tactic |
| Today | [`05` §2](./05-career-and-startup.md#2-thanksgiving-window) — 3 FDE applications before 12pm ET |
| This weekend (post-turkey) | [`03` §3](./03-practical-skills-and-tools.md#3-mcp-weekend-artifact) — ship one MCP server, now with auto-mode-default settings in `.claude/` |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
