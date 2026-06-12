# TL;DR — 2026-06-12 (Friday)

Sixty-second skim. **Three weeks of catch-up land in one day: the frontier just turned into a state-level negotiation, a public-markets asset, and an industrial supply chain — all confirmed before noon.** Altman + Hassabis + Amodei are on a plane to **Évian for the G7 summit (Mon–Wed Jun 15–17)** — the first time all three sit at the same table with G7 heads of state. **Anthropic announced a 3.5GW Google/Broadcom TPU expansion this morning** (TPU-native, not just NVIDIA) and disclosed **run-rate revenue >$30B (≈3× since end-2025)** with **>1,000 customers spending >$1M/yr**. **OpenAI's confidential S-1 was confirmed (Jun 8)** with a ~$1T target and **Sept 2026 listing** — Anthropic's Series H closed at **$965B post-money**, now the most valuable standalone AI startup. **Bezos's Prometheus took $12B Series B at $41B** yesterday to build an "artificial general engineer." **MAI-Code-1 shipped at Microsoft Build** — Microsoft now competes directly with Codex + Claude Code. And **Claude Agent SDK metering hits Monday Jun 15** — T-minus 3 days to toggle credits or get a silent cutoff. **For you:** the public-markets turn changes equity math for any frontier-lab role; TPU-native compute opens a non-NVIDIA hiring lane; Microsoft's coding-model entry forks the Cursor/Claude/Copilot decision; and Prometheus + NEURA reframe "vertical AI" toward *physical* systems.

---

1. **G7 SUMMIT — Évian-les-Bains, June 15–17. Altman, Hassabis, and Amodei all attending** (Macron's personal invite to Altman). First G7 with all three frontier-lab CEOs in the room with heads of state; AI regulation, infrastructure, and safety on the official agenda. → [`01` §1](./01-big-lab-moves.md#1-g7-summit) `#policy #g7 #regulation #anthropic #openai #google` `[primary]`

2. **Anthropic × Google × Broadcom: 3.5GW TPU partnership announced today.** Multi-year expansion; Broadcom CEO disclosed Anthropic's 2027 demand "in excess of 3 GW" on the most recent earnings call. **TPU-native compute is now a first-class frontier path, not NVIDIA-only.** Sites majority US. → [`01` §2](./01-big-lab-moves.md#2-anthropic-broadcom) `#anthropic #google #broadcom #tpu #compute` `[primary]`

3. **Anthropic run-rate revenue >$30B (~3.3× since end-2025); >1,000 customers >$1M/yr (doubled in <2 months); $965B post-money after $65B Series H closed late May.** Anthropic now the most valuable standalone AI startup, above OpenAI's $852B last private mark. → [`01` §3](./01-big-lab-moves.md#3-anthropic-revenue) `#anthropic #revenue #valuation` `[primary]` `[secondary]`

4. **OpenAI confidential S-1 confirmed (Jun 8); ~$1T target, Sept 2026 listing window;** Goldman + Morgan Stanley lead, JPMorgan reportedly on the syndicate. OpenAI quote: "We have not decided on timing yet" — public S-1 unblock once Musk lawsuit cleared. → [`01` §4](./01-big-lab-moves.md#4-openai-s1) `#openai #ipo #public-markets` `[primary]` `[secondary]`

5. **Prometheus (Bezos + Vik Bajaj) — $12B Series B at $41B valuation (announced Jun 11).** ~150 engineers, building an "artificial general engineer" for *physical* systems (jet engines → drug compounds). JPM, BlackRock, Goldman, DST, Arch backed; total funding now >$18B in <1 year. Adjacent signal: **NEURA Robotics $1.4B Series C** (Tether + Qualcomm + Amazon + NVIDIA). **Industrial / Physical AI is the new vertical that's actually being funded.** → [`02` §1](./02-new-emerging.md#1-prometheus) `#funding #industrial-ai #physical-ai #robotics` `[secondary]`

6. **Microsoft Build 2026 dropped MAI-Code-1 + GitHub Copilot desktop app** — Microsoft's direct shot at Codex and Claude Code. MAI-Code-1-Flash priced under Claude Haiku 4.5; Copilot app supports OpenAI / Anthropic / Google models in one picker. **The coding-agent market is now three-way (MS / Anthropic / OpenAI), not two.** → [`01` §5](./01-big-lab-moves.md#5-microsoft-mai-code-1) · [`03` §3](./03-practical-skills-and-tools.md#3-coding-agent-decision) `#microsoft #copilot #coding-agents` `[primary]`

7. **T-3 to Claude Agent SDK metering (Mon Jun 15).** Pro = $20/mo Agent SDK credit, Max 20x = $200, Team Premium = $100. Affects: Agent SDK, `claude -p`, GitHub Actions runs, OpenClaw/Conductor/Jean/Hermes/Zed-ACP. **Toggle credits tonight; silent cutoff Monday otherwise.** Carries from [2026-05-18/03](../2026-05-18/03-practical-skills-and-tools.md). → [`03` §1](./03-practical-skills-and-tools.md#1-agent-sdk-t-3) `#claude-code #agent-sdk #pricing` `[primary]`

8. **Research:** **Tool-DC** (divide-and-conquer tool selection — training-free +25.10% on BFCL/ACEBench; Qwen2.5-7B reaches o3 / Haiku-4.5 parity), **AI Co-Mathematician** (parallel agentic workbench for open math problems), **Hugging Face `ml-intern`** (open-source agent that automates LLM post-training — direct parallel to Karpathy's Anthropic team). **The "real-tool verification" thread from May 22 now has a 25% headline metric.** → [`04` §1–3](./04-research-progress.md) `#agents #tool-use #benchmarks #arxiv` `[primary]`

---

## One thing to DO this Friday

→ **(5 minutes, tonight) Toggle the Agent SDK credit setting in your Claude account before Monday.** Silent failure mode if skipped; the 5-min fix that protects every weekend project [`03` §1](./03-practical-skills-and-tools.md#1-agent-sdk-t-3). **Then (60 minutes, weekend) re-aim the dual-model sanitiser project around Tool-DC's metric** ([`03` §2](./03-practical-skills-and-tools.md#2-weekend-project)) — one artifact citing **MCP-Atlas + Tool-DC + MAI-Code-1 head-to-head + per-step cost** answers four interview questions: orchestration, verification, model selection, and cost-awareness.

## Watchlist deltas

- 🆕 **G7 Évian Jun 15–17 with Altman/Hassabis/Amodei** — first formal multilateral AI-governance moment with all three labs at the table. Watch communiqué language on pre-deployment review, frontier-model audits, and any "AI Safety Institute" coordination. Pre-deployment-eval career lane re-activates if communiqué is concrete.
- 🆕 **TPU as a first-class frontier path** — 3.5GW Anthropic deal makes Broadcom the second-largest accelerator vendor by AI-revenue (~$21B 2026 / ~$42B 2027 from Anthropic alone per Mizuho). Watch for non-NVIDIA hiring lanes (Broadcom, Marvell, Google Cloud TPU teams).
- 🆕 **Microsoft enters frontier coding-agent market** with MAI-Code-1 + Copilot desktop. The Cursor / Claude Code / Codex decision is now Cursor / Claude Code / Codex / **Copilot Desktop**.
- 🆕 **Industrial/Physical AI as a funded category** — Prometheus $41B + NEURA $1.4B = the vertical wedge of mid-2026. Bookmarked in [STARTUPS.md](../STARTUPS.md).
- ➡️ **Anthropic Agent SDK metering** — T-3 days. From WATCH to DO.
- ➡️ **OpenAI S-1 / Sept 2026 IPO ($1T)** — still live; Anthropic now ahead in private valuation ($965B). Watch which one prices first.
- ➡️ **Karpathy → Anthropic pre-training team** — confirmed last week; the **`ml-intern` open-source release** ([`04` §3](./04-research-progress.md#3-ml-intern)) is the open analogue of what that team is doing.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-g7-summit) (G7) + [`01` §2](./01-big-lab-moves.md#2-anthropic-broadcom) (TPU deal) |
| 20 min | [`01` §3](./01-big-lab-moves.md#3-anthropic-revenue) (Anthropic revenue/valuation) + [`02` §1](./02-new-emerging.md#1-prometheus) (Prometheus) + [`04` §1](./04-research-progress.md#1-tool-dc) (Tool-DC) — the three signals that re-shape the rest of the quarter |
| Tonight (5 min) | [`03` §1](./03-practical-skills-and-tools.md#1-agent-sdk-t-3) — toggle Agent SDK credit |
| Weekend (60 min) | [`03` §2](./03-practical-skills-and-tools.md#2-weekend-project) — reframed sanitiser artifact |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.

---

> Note: this edition follows a multi-week gap (last edition 2026-05-22). Stories that hardened during the gap (Series H close, S-1 confirmation, Microsoft Build) are folded into today's edition rather than backfilled day-by-day.
