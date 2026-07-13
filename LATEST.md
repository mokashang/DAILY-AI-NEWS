# LATEST — pointer to the most recent edition

> **2026-07-13** — see [`2026-07-13/00-tldr.md`](./2026-07-13/00-tldr.md)

This file is auto-updated every edition so a one-click read of the latest TL;DR is always at the repo root.

---

## Today's headline

**Monday — GPT-5.6 goes fully public, Meta ships Muse Spark 1.1, Anthropic's J-lens finds a "workspace" inside Claude, Anthropic × Google × Broadcom lock 3.5 GW of TPU — and today's action shrinks to two clocks.** **[Apple v. OpenAI + io Products](./2026-07-13/01-big-lab-moves.md#1-apple-openai)** — 41-page trade-secret suit filed Fri Jul 10 in NDCA names CHO Tang Yew Tan + former Apple engineer Chang Liu; 400+ ex-Apple employees at OpenAI; "show-and-tell" hardware sessions; injunction + product-redesign requested. **[GPT-5.6 fully public](./2026-07-13/01-big-lab-moves.md#2-gpt-56)** — Sol / Terra / Luna ($5/$30 · $2.50/$15 · $1/$6 per M) after Commerce-Dept pre-review; Sol ~54% more token-efficient on coding; **GPT-Live-1** ships full-duplex voice with 9 remastered voices. **[Muse Spark 1.1](./2026-07-13/02-new-emerging.md#1-muse-spark)** — Meta's first paid API ($1.25/$4.25 per M), 1M-ctx, main-or-subagent, native tool + computer use; **MCP-Atlas 88.1 · JobBench 54.7 (Opus 4.8: 48.4 · GPT-5.5: 38.3) · HLE-with-tools 62.1**. **[J-lens / J-space](./2026-07-13/04-research-progress.md#1-jspace)** — open-sourced interpretability lens; ~25-concept subspace inside Claude behaves like the global workspace of consciousness theory; live demo at **neuronpedia.org/jlens**. **[Anthropic × Google × Broadcom 3.5 GW](./2026-07-13/01-big-lab-moves.md#4-anthropic-compute)** — multi-year TPU capacity starting 2027; Anthropic run-rate **$30B** (up from ~$9B end-2025).

**For you:** the frontier converged on **three-tier agentic model families** (Luna/Terra/Sol · Sonnet/Opus/Fable · Muse-worker/orchestrator · Gemini 3.5 Flash/Pro), the FDE lane went from lab-side novelty to **global consulting hiring pattern** (TCS 5,900–8,900 unit), and **the US–China regulatory equilibrium is now visible from both sides** (US EO postponed, China MOFCOM in export-control talks). Bet on portable orchestration, not any single lab.

Full edition → [`2026-07-13/`](./2026-07-13/)

---

## One-thing-to-do (Monday July 13)

→ **Submit Claude Corps application by Thursday.** [`2026-07-13/05 §1`](./2026-07-13/05-career-and-startup.md#1-claude-corps). **T-minus 4 days** to close of Cohort 1 (Fri Jul 17). $85K, 100 slots, in-person US nonprofit placement, no degree gate. Draft essays this evening around a specific Claude-Code + MCP workflow for a chosen nonprofit vertical.

→ **Migrate DeepSeek calls before Jul 24, 15:59 UTC.** [`2026-07-13/03 §4`](./2026-07-13/03-practical-skills-and-tools.md#4-deepseek). T-minus 11 days. **`deepseek-reasoner` → `deepseek-v4-flash` (thinking), NOT `deepseek-v4-pro`** — the default alias silently downgrades heavy-reasoning workloads. `grep -r "deepseek-chat\|deepseek-reasoner" .` and remap explicitly.

→ **Publish a `ROUTING.md`** in your public agent repo showing per-role model choice + cost with the new July field (Luna/Terra/Sol · Sonnet/Opus · Muse-Spark 1.1 · Gemini 3.5 Flash/Pro-target). [`2026-07-13/03 §2`](./2026-07-13/03-practical-skills-and-tools.md#2-routing). Add a **geo-fallback line** for Chinese-open-weight models. [`2026-07-13/03 §5`](./2026-07-13/03-practical-skills-and-tools.md#5-routing-geo).

→ **Cap Claude Code at 3–6 MCP servers + enable `ENABLE_TOOL_SEARCH=true`.** [`2026-07-13/03 §1`](./2026-07-13/03-practical-skills-and-tools.md#1-mcp-hygiene). The single highest-ROI evening of infrastructure hygiene — cuts context bloat, latency, permission-prompt friction; ships a portfolio-legible `.claude/` profile.
