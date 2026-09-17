# TL;DR — 2026-06-23 (Tuesday)

Sixty-second skim. **The June 22 Anthropic cliff lands; OpenAI plants a Daybreak flag the same week.** Two threads close on the same Tuesday: **(a)** the long-scheduled **June 22 Fable 5 subscription cliff** ([previewed since 2026-06-15](../2026-06-15/01-big-lab-moves.md)) **lands today** — Fable 5 leaves Pro / Max / Team / seat-Enterprise plan limits and bills at API rates ($10/M in · $50/M out, **2× Opus 4.8**) **— note: the broader Agent SDK metering rollout remains *paused* ([2026-06-21 watchlist](../2026-06-21/00-tldr.md)), so subscription usage of Sonnet/Opus continues unchanged; today's change is Fable-5-specific.** **(b)** Yesterday (Mon June 22) **OpenAI expanded Daybreak** into a four-piece cyber stack — **GPT-5.5-Cyber GA, Codex Security plugin update (now patches, not just scans), a partner program, and an open-source effort called "Patch the Planet."** Both moves point at the same shift: **frontier-AI margin is moving toward verified, infra-heavy use cases (cyber, agentic dev, eval)**, and the practical/portfolio move today is to **re-route Fable 5 from daily-driver to verifier** while you put one Codex-Security artifact on your portfolio before the partner-program closes the free-tier window.

---

1. **Anthropic Fable 5 cliff lands TODAY** (as scheduled since June 9). Pro / Max / Team / seat-based Enterprise: continued use of Fable 5 now bills against usage credits at **API list rates** — $10/M input · $50/M output, **2× Opus 4.8**. **Sonnet 4.6 + Opus 4.8 + Haiku 4.5 stay on plans unchanged** — the **broader Agent SDK metering rollout remains paused** per the [2026-06-21 watchlist](../2026-06-21/00-tldr.md). This cliff sat in your action list since [2026-06-15/00](../2026-06-15/00-tldr.md); the action *now* is the re-route in [`03` §1](./03-practical-skills-and-tools.md#1-reroute). Fable 5 + Mythos 5 access was already **restored June 18** after the ~6-day export-control suspension. → [`01` §1](./01-big-lab-moves.md#1-fable-5-plan-removal) `#anthropic #fable-5 #capacity #pricing #plans`

2. **OpenAI Daybreak expanded — yesterday, Mon June 22.** Four pieces shipped at once: (a) **GPT-5.5-Cyber GA** (was vetted-defenders-only since May 9 — [2026-05-09/01](../2026-05-09/01-big-lab-moves.md)); (b) **Codex Security plugin update** — now patches, not just scans (30M+ commits, 30K+ codebases, 70K human-confirmed fixes, 500K+ auto-fixed since the March research preview); (c) a **partner program**; (d) **Patch the Planet** open-source effort. Headline framing: **"OpenAI wants to own the patch, not just the bug."** → [`01` §2](./01-big-lab-moves.md#2-openai-daybreak) `#openai #daybreak #codex #cybersecurity`

3. **Anthropic's compute story tightens.** Anthropic's new multi-gigawatt deal with **Google + Broadcom** = ~**3.5 GW** of TPU capacity starting **2027** (custom Broadcom-made TPUs through 2031); ARR is now **~$30B run-rate (up from ~$9B EOY 2025)**, **>1,000 business customers paying >$1M/yr (doubled in two months)**. The Fable 5 plan-removal above is the demand-side symptom of this supply story. → [`01` §3](./01-big-lab-moves.md#3-anthropic-compute) `#anthropic #compute #tpu #broadcom #revenue`

4. **Supabase $500M Series F at $10.5B (June 4).** **GIC-led**, Accel/YC/Craft/Felicis/Peak XV/Coatue all back in; **Stripe doubling down, Salesforce Ventures new.** Public framing from the company: **"Claude Code is our largest contributor since the start of the year — agents are now deploying the majority of databases on the platform."** 600% YoY database growth. The clearest single signal yet that **AI-coding tools are now driving infrastructure-tier revenue**, not just dev-tool revenue. → [`02` §1](./02-new-emerging.md#1-supabase) `#funding #supabase #agentic-infra #claude-code`

5. **Flourish $500M at $2.5B — Bezos personally ~$100M (June 4).** New York startup building **Cortex AI** — a brain-inspired model (connectomics; map real neurons and copy the algorithm). Targets **20–50 W power draw** (a laptop's worth, not a rack's). Lux Capital + GV + Catalio Capital. Founder **Thomas Reardon** (built IE; co-founded CTRL-labs, Meta acquired for ~$500M–$1B). The first credible **post-transformer architecture bet** to clear $500M in 2026. → [`02` §2](./02-new-emerging.md#2-flourish) `#funding #flourish #brain-inspired #post-transformer #power`

6. **Practical: re-route the heavy-model lane TODAY.** Fable 5 on subscription was *the* cost lever this month for orchestrator-grade work; with today's plan-limit removal, you should **demote Fable 5 to verifier / golden-eval only** and **promote Sonnet 4.6 (or Opus 4.8) back to the daily-driver** for the next ~2 weeks of capacity squeeze. The **Opus-orchestrator + Sonnet-worker** team pattern from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) is the right baseline; Fable 5 only enters the team as the *judge* model where its 2× cost is amortized over many cheap-model rollouts. → [`03` §1](./03-practical-skills-and-tools.md#1-reroute) `#claude-code #cost #routing #fable-5`

7. **Research: StateGen (arXiv 2606.16307, June 15)** — state-grounded multi-agent synthetic data for tool-augmented LLMs. The key idea: an **authoritative state manager** maintains a structured world-state across turns, enforcing **"backend-is-truth"** — eliminating tool-call hallucinations *by construction* rather than by training. Extends to multi-agent settings by declaring sub-agents as tools sharing one state object. Reads as the **synthetic-data counterpart** to the real-tool eval thread ([MCP-Atlas / Toolathlon, 2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)). → [`04` §1](./04-research-progress.md#1-stategen) `#arxiv #agents #synthetic-data #state #tool-use`

8. **Career: AI engineer is *still* the #1 fastest-growing US job title — and the data tightened.** 163% YoY growth, **~8,931 open positions across 532 companies, ~$228K average salary**, senior IC band $200K–$312K. **75%+ of postings now require domain depth, not generalist breadth.** The under-priced *thin* lane to ride this week: **AI-cybersecurity engineer** — Daybreak's launch + the EO cyber-clearinghouse half (the part of [2026-05-22/01 §1](../2026-05-22/01-big-lab-moves.md#1-eo-postponed) most likely to survive) just minted a hiring market that didn't exist in May. → [`05` §1](./05-career-and-startup.md#1-ai-engineer-market) · [`05` §2](./05-career-and-startup.md#2-cyber-lane) `#careers #jobs #fde #cybersecurity #ai-engineer`

---

## One thing to DO this Tuesday

→ **Re-route your model defaults before your next agent run.** (a) In Claude Code / Cursor / your CLI, drop the default model from **Fable 5 → Sonnet 4.6** (or Opus 4.8 if you have credits), and explicitly tag Fable 5 as **verifier-only** for now. (b) Log one week of agent runs with a per-step cost trace ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)). (c) **Apply to one AI-cybersecurity role today** (Daybreak ecosystem, Exaforce-style agentic-SOC, or a bank AI-assurance posting) — see [`05` §2](./05-career-and-startup.md#2-cyber-lane) for the targeted list. Cadence > intensity.

## Watchlist deltas

- ⏬ **Anthropic Fable 5 subscription cliff:** *landed today*, as scheduled since [2026-06-15](../2026-06-15/01-big-lab-moves.md). Status: ✅ event-passed. Track: capacity-driven plan-restoration window (no Anthropic date yet); how quickly enterprise commits absorb the freed inventory.
- 🆕 **OpenAI Daybreak as a product line (not a research project):** **GPT-5.5-Cyber GA + Codex Security patching + Patch the Planet OSS + partner program** (Mon June 22). Status: 🟢 active. Track: enterprise wins, banking-sector adoption, the EO cyber-clearinghouse alignment (the [2026-06-02 EO](../2026-06-14/01-big-lab-moves.md) cyber-clearinghouse half).
- ➡️ **Agent SDK metering — *paused*** ([2026-06-21 watchlist](../2026-06-21/00-tldr.md)): subscription usage of Sonnet/Opus unchanged. Watch for the un-pause announcement; build to metered economics regardless.
- ➡️ **Shazeer → OpenAI architecture (June 18)** + **Karpathy → Anthropic pre-training (May 19):** two largest talent flips of 2026, opposite poles. Track first paper from each side.
- ➡️ **MCP `2026-07-28` Release Candidate** (Tasks · MCP Apps · OAuth RS): final spec ships July 28. **35.5M weekly npm downloads — more than `openai` + `@anthropic-ai/sdk` combined.** Status: 🟢 on track.
- ➡️ **DeepSWE #1 Fable 5 70% pass@1 (June 20):** SOTA-shifted; next refresh post-GPT-5.6 window.
- 🟡 **Gemini 3.5 Pro (still in limited preview since May I/O):** Sundar's "give us until next month" deadline closes **June 30**. Prediction markets ~50–55% odds of GA by month-end. Status: 🟡 watch.
- ⬆️ **OpenAI confidential S-1 (June 8) + Anthropic confidential S-1 (June 1)**: both in SEC quiet period; first amendments are the next public signal. Status: 🟢 confirmed.
- 🆕 **AI super-PAC spending / midterms primary today:** $15M+ from groups tied to OpenAI/Anthropic; June 23 = primary day. Status: 🟡 watch — first political-spending precedent for AI as a sector. ([NPR](https://www.npr.org/2026/06/22/nx-s1-5856359/ai-anthropic-congress-spending-openai-midterms-election))
- 🆕 **Brain-inspired / post-transformer architecture bets ($500M floor):** Flourish (June 4) + Bezos personally ~$100M + Lux + GV. Status: 🟡 emerging. Track: first benchmarks (Cortex AI vs. transformer at matched compute).

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Fable 5 plan removal in [`01` §1](./01-big-lab-moves.md#1-fable-5-plan-removal) (today's only acute action item) |
| 20 min | [`01` §2](./01-big-lab-moves.md#2-openai-daybreak) (Daybreak as a product line) + [`02` §1](./02-new-emerging.md#1-supabase) (Supabase as "agents-build-databases" proof) — the two stories that compound |
| Today | [`03` §1](./03-practical-skills-and-tools.md#1-reroute) — change model defaults before your next agent run |
| This week | [`05` §2](./05-career-and-startup.md#2-cyber-lane) — apply to 1 AI-cyber role; the lane is fresh |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
