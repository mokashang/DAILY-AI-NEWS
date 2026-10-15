# TL;DR — 2026-06-12 (Friday)

Sixty-second skim. **Friday-after-SPCX: the public-market comp prints, the G7 weekend opens, the TPU supply chain hardens.** **SpaceX (SPCX) opened +11% at $150 on NASDAQ this morning** (priced $135 yesterday; **~$250B demand, ~3.5–4× oversubscribed** — biggest IPO ever) and that's the first live read-through to **Anthropic's $965B October S-1** ([carries from 2026-06-04](../2026-06-04/) onward) and **OpenAI's $852B June-8 filing** ([carries from 2026-06-08](../2026-06-08/01-big-lab-moves.md)). **G7 Summit Évian-les-Bains Mon–Wed Jun 15–17 — Altman, Hassabis, and Amodei all attending** (Macron's personal invite to Altman); first G7 with all three frontier-lab CEOs sharing a working-lunch table with G7 heads of state. **Anthropic announced a 3.5GW Google/Broadcom TPU expansion this morning** (multi-year, online 2027; Mizuho-modeled at **$21B 2026 / $42B 2027 from Anthropic alone**) and disclosed **run-rate revenue >$30B (~3.3× since end-2025), 1,000+ customers >$1M/yr (doubled in <2 months)**. **Bezos's Prometheus took $12B Series B at $41B yesterday** for an "artificial general engineer" + **NEURA Robotics $1.4B Series C** — **physical-AI is a funded category**. **Claude Agent SDK metering goes live Sunday Jun 15** — T-3 days, **toggle credit tonight**. **For you:** the SPCX print + Anthropic-Broadcom deal open *two* new lanes — public-market equity comp for any frontier-lab role, and a non-NVIDIA hiring path (Broadcom / Marvell / Google Cloud TPU). The Friday hand-off from yesterday's [Claude Corps post](../2026-06-11/05-career-and-startup.md#1-claude-corps) is still your single highest-leverage application move this month.

---

1. **SPCX OPENS +11% AT $150 ON NASDAQ** (priced $135 / ~$1.75T / ~$75B raised; ~$250B demand; SpaceX rings the NASDAQ opening bell). Largest IPO in history. **MSCI Global Standard Index inclusion Saturday Jun 13** = forced index demand from day two. This is the live comp Anthropic's October S-1 and OpenAI's June-8 filing get priced against. → [`01` §1](./01-big-lab-moves.md#1-spacex-first-day) `#spacex #ipo #spcx #public-markets`

2. **G7 SUMMIT — Évian-les-Bains, Mon–Wed Jun 15–17. Altman, Hassabis, Amodei all on the official list.** First G7 with all three frontier-lab CEOs in the room with heads of state; AI regulation, infrastructure, and online safety on the Wednesday working-lunch agenda. → [`01` §2](./01-big-lab-moves.md#2-g7-summit) `#policy #g7 #regulation #anthropic #openai #google` `[primary]`

3. **Anthropic × Google × Broadcom — 3.5GW TPU partnership announced today.** Multi-year expansion, online 2027; Mizuho-modeled **$21B Broadcom AI revenue from Anthropic in 2026, $42B in 2027**. **TPU is now a first-class frontier path** — not NVIDIA-only. Sites majority US. Carries Google's earlier up-to-**$40B investment** in Anthropic. → [`01` §3](./01-big-lab-moves.md#3-anthropic-broadcom) `#anthropic #google #broadcom #tpu #compute` `[primary]`

4. **Anthropic run-rate >$30B (~3.3× since end-2025); 1,000+ customers >$1M/yr (doubled in <2 months); Series H closed $65B/$965B late May.** Now the most valuable standalone AI startup. Carries from [2026-05-29](../2026-05-29/) (Series H close), [2026-06-04](../2026-06-04/) (S-1 filing), and [2026-06-11](../2026-06-11/) (SpaceX-comp framing). → [`01` §4](./01-big-lab-moves.md#4-anthropic-revenue) `#anthropic #revenue #valuation` `[primary]` `[secondary]`

5. **Prometheus (Bezos + Vik Bajaj) — $12B Series B at $41B (Jun 11). NEURA Robotics — $1.4B Series C (Tether/Qualcomm/Amazon/NVIDIA).** ~150 engineers / >$18B total at Prometheus in <1 year; mission = "artificial general engineer" for *physical* systems (jet engines → drug compounds). Two physical-AI mega-rounds in 30 days = a **category, not a coincidence**. → [`02` §1](./02-new-emerging.md#1-prometheus) `#funding #physical-ai #robotics`

6. **T-3 to Claude Agent SDK metering (Sun Jun 15).** Pro = $20/mo Agent SDK credit, Max-20x = $200, Team Premium = $100. Affects: Agent SDK, `claude -p`, GitHub Actions runs, OpenClaw/Conductor/Jean/Hermes/Zed-ACP. **Toggle credit tonight; silent cutoff Sunday otherwise.** Carries from [2026-05-18/03](../2026-05-18/03-practical-skills-and-tools.md). → [`03` §1](./03-practical-skills-and-tools.md#1-agent-sdk-t-3) `#claude-code #agent-sdk #pricing` `[primary]`

7. **Microsoft MAI-Code-1 + GitHub Copilot Desktop (carries from Jun 2 Build).** Microsoft's direct shot at Codex + Claude Code; MAI-Code-1-Flash priced under Claude Haiku 4.5; Copilot Desktop picker carries OpenAI/Anthropic/Google models. **Coding-agent market is now 4-way: Cursor / Claude Code / Codex / Copilot Desktop.** → [`01` §5](./01-big-lab-moves.md#6-microsoft-mai-code-1) · [`03` §3](./03-practical-skills-and-tools.md#3-coding-agent-decision) `#microsoft #copilot #coding-agents`

8. **Research:** **Tool-DC** — training-free **+25.10%** on BFCL/ACEBench; Qwen2.5-7B reaches o3 / Haiku-4.5 parity on tool use. **AI Co-Mathematician** (parallel agentic math workbench, follow-on to the May-21 Erdős result). **HF `ml-intern`** (open-source post-training agent — open analogue of Karpathy's new Anthropic team). → [`04` §1–3](./04-research-progress.md) `#agents #tool-use #benchmarks #arxiv` `[primary]`

---

## One thing to DO this Friday

→ **(5 minutes, tonight) Toggle the Agent SDK credit setting in your Claude account before Sunday.** Silent failure mode if skipped. [`03` §1](./03-practical-skills-and-tools.md#1-agent-sdk-t-3) **Then (60 min) continue yesterday's Claude Corps application** — [carry from 2026-06-11/05 §1](../2026-06-11/05-career-and-startup.md#1-claude-corps), submit by **June 22** before applicant volume compounds. **And (weekend) reframe the dual-model sanitiser project around Tool-DC's +25.10% metric** ([`03` §2](./03-practical-skills-and-tools.md#2-weekend-project)) — one artifact citing **MCP-Atlas + Tool-DC + MAI/Sonnet/Codex head-to-head + per-step cost** answers four interview questions: orchestration, verification, model selection, cost-awareness.

## Watchlist deltas

- 🟢 **SpaceX IPO first-day pop:** **OPEN +11% at $150 today on NASDAQ.** From "T-1 to pricing" yesterday → "live comp" today. Watch the 4 PM ET close + the MSCI Global Standard Index inclusion Saturday (forced index demand) + the read-across to Anthropic's October roadshow timing.
- 🆕 **G7 Évian Mon–Wed with Altman/Hassabis/Amodei** — first formal multilateral AI-governance moment with all three labs at the table. Watch Wednesday's communiqué language on pre-deployment review, frontier-model audits, and any AI Safety Institute coordination. Pre-deployment-eval career lane re-activates if communiqué is concrete (was parked on [2026-05-22](../2026-05-22/01-big-lab-moves.md#1-eo-postponed)).
- 🆕 **TPU as a first-class frontier path** — Anthropic × Google × Broadcom 3.5GW deal makes Broadcom structurally the secondary AI-accelerator vendor (~$21B 2026 / ~$42B 2027 from Anthropic alone per Mizuho). Non-NVIDIA hiring lanes open (Broadcom / Marvell / Google Cloud TPU). [`01` §3](./01-big-lab-moves.md#3-anthropic-broadcom)
- 🆕 **Industrial / Physical AI as a funded category** — Prometheus $41B + NEURA $1.4B = the vertical wedge of mid-2026. Bookmarked in [STARTUPS.md](../STARTUPS.md).
- ➡️ **Claude Agent SDK metering** — T-3 days (Sun Jun 15). From WATCH to DO tonight. Carries from [2026-06-11/00](../2026-06-11/00-tldr.md) (was T-4 yesterday).
- ➡️ **Visible-safeguards regime** — still live from yesterday's Anthropic Fable 5 reversal ([2026-06-11/01 §3](../2026-06-11/01-big-lab-moves.md#3-safeguards-reversal)). Watch for OpenAI / Google parity transparency.
- ➡️ **Claude Corps cohort 1 (apps close July 17)** — directly on user eligibility line. **Friday/Saturday is the cheapest week to apply.** [Source — 2026-06-11/05 §1](../2026-06-11/05-career-and-startup.md#1-claude-corps).
- ⬇️ **Cost-aware multi-provider router wedge** — window narrowed after Microsoft Copilot Desktop's model picker entered the same surface ([`01` §5](./01-big-lab-moves.md#6-microsoft-mai-code-1)).

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1 SPCX](./01-big-lab-moves.md#1-spacex-first-day) + [`01` §3 Anthropic-Broadcom](./01-big-lab-moves.md#3-anthropic-broadcom) |
| 20 min | [`01` §3](./01-big-lab-moves.md#3-anthropic-broadcom) (TPU deal) + [`02` §1](./02-new-emerging.md#1-prometheus) (Prometheus) + [`04` §1](./04-research-progress.md#1-tool-dc) (Tool-DC) — the three signals that re-shape the quarter |
| Tonight (5 min) | [`03` §1](./03-practical-skills-and-tools.md#1-agent-sdk-t-3) — toggle Agent SDK credit |
| Tonight (60 min) | Continue yesterday's [Claude Corps application](../2026-06-11/05-career-and-startup.md#1-claude-corps) |
| Weekend (60 min) | [`03` §2](./03-practical-skills-and-tools.md#2-weekend-project) — reframed sanitiser artifact citing Tool-DC |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
