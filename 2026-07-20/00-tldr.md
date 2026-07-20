# TL;DR — 2026-07-20 (Monday)

Sixty-second skim. **The talent map redrew — and Anthropic won the week.** Google DeepMind lost its Nobel-laureate co-founder of AlphaFold, **John Jumper**, plus **Jonas Adler** and **Alexander Pritzel** to **Anthropic**; **Noam Shazeer** ("Attention Is All You Need") went to **OpenAI**. Combined Alphabet market-cap swing over two sessions: **≈$225–270B wiped**. In the same window, **Gemini 3.5 Pro missed its widely-reported July 17 GA target** — still in Vertex enterprise preview, reporting now points to an August window. On the other side of the ledger, **OpenAI's GPT-5.6 (Sol / Terra / Luna) is 11 days into general availability** (rolled out July 9 after a government-approved staggered release), and **Anthropic's Opus 4.7 is now the default enterprise Opus** with a **10.9-pt SWE-bench Pro jump** and a new tokenizer that quietly re-priced Claude Code bills ~30% higher per prompt. For you: **your ME.md Anthropic-stack focusing decision just got the loudest validation of 2026** — build the artifacts that assume Anthropic will out-hire and out-ship Google over the next two quarters, and price your Claude Code bill against the new tokenizer this week.

---

1. **Anthropic captures a Nobel laureate + 3 senior DeepMinders in one stretch.** **John Jumper** (2024 Chemistry Nobel, AlphaFold), **Jonas Adler** (Google AI coding), **Alexander Pritzel** (pretraining) → Anthropic. **Noam Shazeer** → OpenAI. Google previously paid **~$2B** for Shazeer via the Character.ai acqui-hire. Employees cite **bureaucratic culture** and **compute-allocation fights** (a Shazeer project reportedly had chips reassigned). → [`01` §1](./01-big-lab-moves.md#1-deepmind-exodus) `#deepmind #anthropic #openai #talent`

2. **Gemini 3.5 Pro missed the July 17 GA target.** Full architectural rebuild (Google scrapped 2.5 Pro after "structural failures in recursive tool-calling and SVG generation"). Still limited-preview on Vertex; reporting now points to **August window**. Reported specs (2M-token context, Deep Think reasoning layer) remain **unconfirmed** — no model card, no pricing post. → [`01` §2](./01-big-lab-moves.md#2-gemini-35-pro-slip) `#google #gemini #execution-risk`

3. **OpenAI GPT-5.6 (Sol / Terra / Luna) is 11 days into GA** (July 9). Three-tier lineup: **Sol** $5 / $30 per 1M in/out for hardest reasoning + agent workflows; **Terra** ~2× cheaper than GPT-5.5 at competitive quality; **Luna** the cost floor. Preceded by a **Commerce-Department CAISI capability review** under Trump's June 2 executive order — the first US-model release *cleared* by federal pre-deployment review. → [`01` §3](./01-big-lab-moves.md#3-gpt-56-ga) `#openai #gpt-5-6 #policy #release-review`

4. **Anthropic Opus 4.7 = the new enterprise default.** **SWE-bench Pro 53.4 → 64.3** (+10.9), **SWE-bench Verified 80.8 → 87.6** (+6.8), **GDPVal-AA Elo 1,753** (vs GPT-5.4 1,674, Gemini 3.1 Pro 1,314). New `xhigh` effort setting + task budgets + 2,576-px vision. **Watch the new tokenizer: ~30% more tokens per prompt at unchanged $5/$25 per 1M** — your Claude Code bill just got repriced. → [`01` §4](./01-big-lab-moves.md#4-opus-47-default) · [`03` §3](./03-practical-skills-and-tools.md#3-tokenizer-cost) `#anthropic #opus #tokenizer #pricing`

5. **Emerging: the vertical-AI funding wave keeps compounding.** **Harvey $200M Series C @ $2.1B** (legal), **Lovable $200M Series B @ $2.8B** (app-gen), **Glean $180M Series D @ $2.7B** (enterprise search), **Hebbia $130M Series B @ $1B**, **Neko Health $700M Series C** (preventive health imaging), **Emergent $130M Series C** (AI coding), **Oak $60M seed** (AI-native identity). Agent-startup deals hit **$1.8B across 12+ rounds** in July. → [`02` §1](./02-new-emerging.md#1-vertical-funding) `#funding #vertical-ai`

6. **Research: three real-agent benchmarks that will show up in your interview loop.** **Holistic Agent Leaderboard (HAL)** — the missing multi-model, multi-benchmark, cost-normalized infra. **HAS-Bench** — human-agent systems with configurable human participation. **AlphaEval** — production-agent evaluation. Ties directly to the "verify against real tools" thread from [2026-05-22/04](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks). → [`04` §1](./04-research-progress.md#1-agent-benchmarks) `#benchmarks #agents #arxiv`

7. **Practical: three Claude Code habits that repay in a week.** (1) **3–5 parallel sessions in git worktrees** (native support); (2) **Plan mode (Shift+Tab) before every non-trivial edit** — enforced read-only sandbox; (3) **Verification is the #1 tip** — make Claude check its own output every task. → [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-playbook) `#claude-code #workflow #verification`

8. **Career: AI Engineer is the #1 fastest-growing US job (+143% YoY), avg $206K, 3.4 open roles per qualified candidate.** California = 33% of postings. Azure + AWS still lead the required-cloud line. Also: **AI-Engineer-adjacent premium** (AI skill on any SWE JD) jumped 25% → 56% in 12 months. → [`05` §1](./05-career-and-startup.md#1-ai-engineer-market) `#jobs #ai-engineer #salary`

---

## One thing to DO this Monday

→ **Audit your Claude Code bill against the Opus 4.7 tokenizer change.** Pull last 7 days of Claude Code spend, divide input+output tokens by 1.30, compare to what an identical week would have cost pre-tokenizer. If the delta is >15% of your monthly budget, add **Sonnet-worker routing to any subagent that doesn't need Opus's reasoning depth** (the Opus-orchestrator/Sonnet-worker pattern from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) — same primitive, more urgent now). Ship the audit as a public gist by Friday — it doubles as a **portfolio artifact for AI-Integration-Engineer interviews** and as **customer-discovery evidence for the cost-router startup wedge** ([STARTUPS.md](../STARTUPS.md)).

## Watchlist deltas

- 🆕 **DeepMind → Anthropic talent flow (Jumper + Adler + Pritzel):** new thread. Validates the ME.md Anthropic-focus decision. Watch what these three ship — Jumper's specialty (protein structure via attention) is a plausible tell for **Anthropic in scientific-agent territory** (Isomorphic Labs, [2026-05-19/02](../2026-05-19/02-new-emerging.md)).
- 🆕 **Shazeer → OpenAI:** new thread. Two of the transformer paper's most famous names now sit at OpenAI + Anthropic; **Google's talent pipeline for the frontier is measurably weaker than 3 months ago.**
- 🆕 **Gemini 3.5 Pro slippage past July 17:** new thread. Reporting says August; Google has not officially rescheduled. **Every day of slip is a week of Anthropic + OpenAI market share.**
- 🆕 **GPT-5.6 GA (July 9) — first "government-reviewed" US frontier release:** new thread. The **Trump EO of June 2** made CAISI pre-deployment review real; GPT-5.6 is the first cleared release. **The pre-deployment-eval career lane I flagged as "delayed" on [2026-05-22/01 §1](../2026-05-22/01-big-lab-moves.md#1-eo-postponed) is now shipping.**
- 🆕 **Opus 4.7 tokenizer re-pricing:** new thread. Same $/M, ~30% more tokens per prompt. **Everyone running Claude Code without cost telemetry is now overpaying by 15–30%.**
- 🆕 **Harvey $200M / Lovable $200M / Neko $700M / Emergent $130M / Oak $60M week:** new thread. Vertical AI + preventive-health + AI-native-identity — three of the four "picks-and-shovels for the real world" lanes.
- ➡️ **Karpathy → Anthropic pretraining team ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)):** still live. **Now paired with Jumper + Adler + Pritzel** — Anthropic's pretraining bench is materially deeper than 8 weeks ago.
- ➡️ **The IPO wave ([2026-05-22/02 §1](../2026-05-22/02-new-emerging.md#1-ipo-wave)):** OpenAI's S-1 is still confidential; roadshow window unchanged. Watch whether the DeepMind exodus surfaces in the risk factors ("dependence on key personnel" language).
- ⬇️ **Agent SDK metering (June 15 — [2026-05-16](../2026-05-16/)):** live for 5 weeks. The tokenizer change makes the cost lever from that thread even more valuable.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the DeepMind exodus + Gemini 3.5 Pro slip in [`01` §1–2](./01-big-lab-moves.md) |
| 20 min | [`01` §1](./01-big-lab-moves.md#1-deepmind-exodus) (talent map) + [`04` §1](./04-research-progress.md#1-agent-benchmarks) (HAL/HAS-Bench/AlphaEval) |
| Today | [`03` §3](./03-practical-skills-and-tools.md#3-tokenizer-cost) — the Opus 4.7 tokenizer audit (1 hour, ships as a gist) |
| Tonight | [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-playbook) — set up parallel worktree sessions if you haven't |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
