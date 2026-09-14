# TL;DR — 2026-09-14 (Sunday)

Sixty-second skim. **The industry blinked.** Ten days after the "four-frontier-models-in-one-week" wave and the 1,100-employee pacing petition, **Dario Amodei published "We Must Pace the Frontier" (Sept 12) — and Altman and Hassabis publicly agreed within hours.** Anthropic committed to permanent employee-level system access for third-party evaluators (METR named); OpenAI matched the first commitment; DeepMind endorsed the direction. **This is the first cross-lab pacing signal of 2026, and it changes the skill re-price.** Underneath it: **Cognition (Devin) raised $2B+ at $48B (~$900M ARR)** — the biggest coding-agent round of the year and the loudest confirmation that agent-native tooling is the layer where capital is compounding. Ramp's monthly index showed **August AI-spend-per-employee at top firms fell ~10%** while adoption still crept up — the first "cracks in the thesis" data point of the year. For you: **the "pacing" narrative widens the eval/routing lane a second time; the Cognition round tells you where the next 12 months of hiring and startup opportunity actually live.**

---

1. **Dario's "We Must Pace the Frontier" (Sept 12) — Altman + Hassabis publicly agree; METR gets permanent employee-level access.** Anthropic CEO published a ~3,800-word essay arguing labs must deliberately slow capability gains 1–2 years while safety catches up. Concrete first move: third-party evaluators get permanent employee-level system access (METR named). Sam Altman: OpenAI will match that first commitment. Demis Hassabis quote-tweeted backing "the direction." First cross-lab pacing signal of 2026 — a formal response to the [Sept 3 1,100-employee petition](../2026-09-10/01-big-lab-moves.md#1-model-fatigue). → [`01` §1](./01-big-lab-moves.md#1-pace-the-frontier) `#labs #pacing #anthropic #openai #deepmind #evals`

2. **Anthropic Sept 2026 Threat Intel — Russia GTG-20006 + China distillation attacks disrupted.** Anthropic's third public threat report named Russian espionage cluster **GTG-20006** (20+ Ukrainian/European/diplomatic victims), and disrupted seven China-based labs — **Alibaba, Moonshot, DeepSeek, Xiaomi** among them — from illicit "distillation" attacks trying to extract Claude capabilities into Qwen. Also flagged Claude use in conventional-weapons software work in China/Russia/Yemen. → [`01` §2](./01-big-lab-moves.md#2-threat-intel) `#anthropic #security #geopolitics #distillation`

3. **Google commits $15.1B to Finland AI infrastructure (Sept 9)** — three new datacenters (Hamina, Kajaani, Muhos/Vaala), 22-year PPA for ~50% of Fortum's Loviisa nuclear output, +$4.2B Finnish GDP during build, ~7K permanent jobs. Largest single European AI investment of 2026; also the loudest nuclear-power-for-AI proof point since Anthropic's Colossus rental. → [`01` §3](./01-big-lab-moves.md#3-google-finland) `#google #datacenters #nuclear #europe`

4. **NVIDIA takes strategic stake in Sutskever's SSI; grants Vera Rubin access (Sept 9–10).** NVIDIA newsroom confirmed a long-term partnership with Safe Superintelligence Inc. including a substantial investment and access to Vera Rubin — SSI says this grows their compute "by an order of magnitude." First public partner disclosure since SSI's April $32B round. → [`01` §4](./01-big-lab-moves.md#4-nvidia-ssi) `#nvidia #ssi #compute`

5. **OpenAI launches ChatGPT for Financial Services with Morgan Stanley + Evercore (Sept 10).** Built on ChatGPT Work + GPT-6 Astra, aimed at junior-IB workflows (comps, pitchbooks, models) with Daloopa/PitchBook/LSEG data, citations, RBAC/audit. Direct shot at Anthropic's Claude for Financial Services and part of the Q4-IPO enterprise-revenue narrative. → [`01` §5](./01-big-lab-moves.md#5-openai-financial) `#openai #enterprise #finance`

6. **Cognition $2B+ Series E at $48B (Sept 8) — Devin's ARR jumped $492M → ~$900M in four months; a16z + Accel co-lead; NVIDIA joins as investor AND customer.** Largest coding-agent round of 2026. Devin now runs inside NVIDIA, GE Aerospace, Citi, Mercedes-Benz, Modal. **Coding-agent-as-a-service is now the category with the fastest revenue compounding of any AI vertical.** → [`02` §1](./02-new-emerging.md#1-cognition-48b) `#funding #agents #cognition #coding-agents`

7. **Positron AI $875M at $5B for memory-first inference silicon (Sept 10).** Two-tranche Series C (NEA/Atreides/Valor/Andra + Jim Clark-anchored $500M C-1). Funds the "Asimov" chip (288 GB–2.3 TB LPDDR5X per die, TSMC N3P tape-out end-2026) and "Titan" system aimed at **16T-param models + 10M-token contexts.** Signals VC conviction that inference-specialized silicon can wedge against NVIDIA. → [`02` §2](./02-new-emerging.md#2-positron) `#funding #hardware #inference`

8. **Claude Code v2.1.269 (Sept 11) — `claude plugin eval` ships.** First-class ablation harness for skills/plugins: run test cases with plugin loaded, then without, get a scored JSON+HTML diff. **The missing eval loop for anyone building `.claude/skills/`.** Also this week: tunable subagent cap (`CLAUDE_CODE_WORKFLOW_MAX_CONCURRENT_AGENTS`), prompt-cache stability fix for `--system-prompt`/subagents, MCP HTTP+SSE fallback. → [`03` §1](./03-practical-skills-and-tools.md#1-plugin-eval) `#claude-code #evals #skills #mcp`

9. **arXiv this week — Next Concept Prediction hits OLMo-3 loss at ~half the tokens; Looped Flows crosses 58.8% on ARC-AGI-1.** [NCP-ArchPreview (2609.10715)](https://arxiv.org/abs/2609.10715): 8.9B pretrain that augments NTP with concept-level predictions over the model's own quantized hidden states — same loss as OLMo-3-7B at 51.3% of tokens, +2.45 macro-avg, +5.99 GSM8K. [Thinking with Looped Flows (2609.11801)](https://arxiv.org/abs/2609.11801): latent-loop reasoning, no CoT tokens, 58.8% ARC-AGI-1 / 12.2% ARC-AGI-2. → [`04`](./04-research-progress.md) `#arxiv #pretraining #reasoning #arc-agi`

10. **Ramp AI Index Sept — first "cracks in the thesis" data point.** Top-1% AI spenders cut per-employee AI spend from **~$7,976 (Jul) → ~$7,205 (Aug)**, a ~10% drop, while overall adoption still crept up (56.0%, +0.4pt). **Anthropic 43.8% (+0.34pt) vs OpenAI 39.8% (+0.09pt).** Effective token price down **~41% in six months** ($1.15 → $0.68 per 1M avg). Paired with **6,300+ tech layoffs in Sept 1–10 (+199% vs Aug)** and **Salesforce cutting 133 more Agentforce/MuleSoft roles**, the Q4 hiring bar just went up. → [`05` §1](./05-career-and-startup.md#1-ramp-cracks) · [`05` §2](./05-career-and-startup.md#2-layoff-surge) `#adoption #hiring #layoffs`

---

## One thing to DO this Sunday

→ **Write 5 golden-case evals for one of your `.claude/skills/` and run `claude plugin eval` before/after this afternoon.** Commit the JSON+HTML diff to your repo. That's a public "we ship evals, not vibes" artifact that reads as senior-level on any FDE/AI-Engineer application — and it's the single Sept-14 news item that maps most cleanly onto your active portfolio ([`ME.md`](../ME.md) → MCP servers + cost-aware agent design). Details in [`03` §1](./03-practical-skills-and-tools.md#1-plugin-eval).

## Watchlist deltas

- 🆕 **Cross-lab pacing signal:** new thread. Track whether Anthropic's METR-access commitment gets contractual language, and whether OpenAI/DeepMind match on the *second* and *third* commitments (Amodei's essay implies more coming). If a pacing accord forms, the next model wave slows visibly — reprices "release-cadence intelligence" as a signal you can trade on.
- 🆕 **Coding-agent-as-a-service consolidation:** new thread. Cognition at $48B / ~$900M ARR = the price-anchor for the whole layer. Watch Cursor / Codeium / Zed / Replit / Vercel v0 next-round rumors — a $10B+ round at any of those in Q4 makes coding agents the highest-multiple sub-sector of AI.
- 🆕 **Inference-silicon second wind:** new thread. Positron $875M at $5B + rumored XDOF Series B = the market is funding NVIDIA alternatives again, specifically on the *inference* side, ahead of Vera Rubin.
- 🆕 **MCP moves out of dev tooling:** new thread. DaVinci Resolve 21.1 native MCP + Docusign MCP GA (Sept 30) + ReleasePad MCP = the action layer is going vertical. Every SaaS TAM > $1B is now an MCP-server opportunity.
- ➡️ **Anthropic IPO window (from 2026-09-10):** hardened by revenue/threat/pacing publicity in the same week; watch for S-1 filing.
- ➡️ **Model fatigue (from 2026-09-10):** partially answered by the pacing accord; skill re-price on router/evals holds.
- ⬇️ **"Generic FDE prep" as an application track:** softening. FDE roles are compressing to *builder* profiles (Anthropic Applied AI, Sierra Agent Engineer). Add one shipped agent artifact per week if you're serious. See [`05` §3](./05-career-and-startup.md#3-fde-hiring).

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-pace-the-frontier) (pacing accord) + [`02` §1](./02-new-emerging.md#1-cognition-48b) (Cognition $48B) |
| 20 min | [`03` §1–4](./03-practical-skills-and-tools.md) — Claude Code v2.1.267–269 (plugin eval, subagent cap, cache fix, MCP fallback) |
| Today | [`03` §1](./03-practical-skills-and-tools.md#1-plugin-eval) — write 5 golden cases + run `claude plugin eval` before/after |
| Tonight | [`04` §1](./04-research-progress.md#1-ncp) — read the NCP-ArchPreview report so you can talk about latent-concept pretraining in interviews next week |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
