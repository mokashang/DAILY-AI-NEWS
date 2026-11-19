# TL;DR — 2026-11-15 (Sunday)

Sixty-second skim. **This isn't a shipping-news day — it's a calendar-reading day. The biggest 36-hour window for AI public-equity re-pricing in a decade starts Monday evening: NVIDIA Q3 FY27 earnings Mon Nov 17 pre-close → Anthropic (ANT) IPO pricing Tue Nov 18 → ANT first trade Wed Nov 19. Yesterday's edition said "pricing week of Nov 16"; the corrected S-1/A locks pricing on Tue Nov 18 — flag the correction, clear calendar space Tue evening + Wed morning.** ANT is **6× oversubscribed**, the FT reports banks are weighing pricing **above the $70–$78 range** → ~$1.5T fully-diluted outcome, and the **$26B Class N private placement** puts **AMD / Broadcom / Google / Micron / Microsoft / Nvidia / TSMC** on Anthropic's cap table. OpenAI extended its vertical-GPT cluster with **GPT-6 Cyber** (via Releasebot) + **ChatGPT Wallet** for US Pro (Nov 13) — the agent-payments wedge just lost its horizontal playing field. Google DeepMind's **Gemini 4 Carbon** leads Intelligence Index v5 at 59 pts, cyber-defense gated. Underneath, **LangChain closed $300M at $3B** (CapitalG), **Mirendil $1B at $5B** (agentic R&D), **Mercor $750M at $20B** (AI-training SME marketplace), **Bedrock Robotics $600M + Tutor Intelligence $75M**, **Boson AI ~$70M** (voice); M&A velocity surged (**Meta/Conductor**, **Five9/Level AI $325M**, **OpenAI/Odessia**, **Oura/Counsel Health $625M**, **Dropbox/Tigris $350M** in a 10-day window). Open-weight frontier stayed non-US (**Kimi K3.1 Pro** with revenue-share license + **Mistral Large 4** HF weights live Nov 14). Research: the **2611.xxxxx arXiv wave** crystallized around trajectory-level reliability (2611.13254), TTS as cost lever (2611.02208, 2611.01133), VLA interpretability (2611.08895), and **Anthropic's Automated Alignment Researchers** paper — **"LLM-on-alignment-work" is now a hireable job family**. Practical: **Claude Code 2.1.304** adds `InstructionsLoaded` hook + 32-skill preload cap, **MCP 2026-07-28 spec stable** (TS SDK 2.4.0 with Skills-over-MCP), **LangGraph 1.2.20 strict resume**, and **`llm` 0.37.2 shipped a security fix — upgrade now if you've ever run `llm openai endpoint add`**. Career: **Palantir is the only FDE pipeline with a structural new-grad slot**; Anthropic hires under **"Applied AI Engineer"** not "FDE" — scrape that keyword. **`AI Engineer` median TC $155.5K vs `ML/AI SWE` $250.9K** — ~$95K delta; ask for the ML/AI SWE req. **Anthropic Residency 2026 due Saturday Nov 22** — 6 days.

---

1. **Anthropic (ANT) IPO date correction + 6× oversubscribed.** Pricing **Tue Nov 18**, first trade **Wed Nov 19** (NOT Nov 16 as yesterday's edition said). Range **$70–$78 / 825M Class A**; FT says bank syndicate weighing pricing *above* range → **~$1.5T fully-diluted**. **$26B Class N private placement** to **AMD/Broadcom/Google/Micron/Microsoft/Nvidia/TSMC**. Roadshow pitch: **49 compute mentions**, **35% long-term operating-margin target**, **"safety + no jerks"** culture. Lockup ~6mo → **mid-May 2027 = ex-Anthropic seed window**. → [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo) `#anthropic #ipo`

2. **NVIDIA Q3 FY27 earnings Mon Nov 17 — the single biggest datapoint of the week.** Guide $108.0B ± 2%, GM 74.0%. **Rubin CPX status is the open question** (Buck pulled it at GTC; Kuo reports HBM4 revival Q1 CY27). Jensen's framing: **$40B/GW Rubin vs $25B/GW Blackwell**. If CPX is shelved, router/long-context-arbitrage startups re-price DOWN; if revived, re-price UP. → [`01` §2](./01-big-lab-moves.md#2-nvidia-q3) `#nvidia #earnings #rubin`

3. **OpenAI weekend cluster — GPT-6 Cyber (Releasebot Nov 14) + ChatGPT Wallet (Nov 13 US Pro).** GPT-6 Cyber: **48.5% ExploitGym** vs GPT-5.6 Cyber 32.1%; Preparedness Framework **High → Critical**; narrow-gated to Daybreak Red. ChatGPT Wallet: biometric-approved purchases inside ChatGPT. **Kills the horizontal Stripe-for-agents pitch dead.** → [`01` §3](./01-big-lab-moves.md#3-openai-weekend) `#openai #cyber #payments`

4. **Google DeepMind Gemini 4 Carbon leads Intelligence Index v5 at 59 pts** (Argon → Carbon, two-week cadence). Cyber-defense gated, long-running agent workflows. **The top of the frontier is now three vertical cyber flagships: Claude Mythos 5.2, GPT-6 Cyber, Gemini 4 Carbon.** → [`01` §4](./01-big-lab-moves.md#4-gemini-4-carbon) `#google #gemini #cyber`

5. **Moonshot Kimi K3.1 Pro open weights (Nov 2–4) + revenue-share license (30% above $20M ARR).** First open-weight commercial model that resembles app-store economics. Western open-weight frontier is non-US (plus **Mistral Large 4** with weights live Nov 14). → [`01` §5](./01-big-lab-moves.md#5-kimi-k31-pro) · [`02` §3](./02-new-emerging.md#3-mistral-large-4) `#open-source #china #europe`

6. **LangChain $300M Series C at $3B — CapitalG leads (Nov 13).** Google hedging across ADK + LangChain. Framework-agnosticism is now the smart founder posture. Pure-framework pitches are closed. → [`02` §1](./02-new-emerging.md#1-langchain) `#funding #langchain`

7. **Mirendil $1B Series A at ~$5B (Nov 12)** for agentic R&D workflows (Kleiner Perkins + Clearlake) + **Mercor $750M Series D at ~$20B** (talent-marketplace-for-AI-training-data). "Agentic AI for R&D" is the week's new thesis. **Mercor is the highest-leverage side gig for a technical CS grad — $150–400/hr for coding/eval SME work.** → [`02` §4](./02-new-emerging.md#4-mirendil) · [`02` §5](./02-new-emerging.md#5-mercor) `#funding #mercor #mirendil`

8. **M&A velocity: 5+ AI deals in 10 days.** Meta/Conductor, Five9/Level AI $325M, OpenAI/Odessia, Oura/Counsel Health $625M, Dropbox/Tigris $350M. **The exit path for 2026 AI startups is strategic acquisition, not IPO.** → [`02` §6–10](./02-new-emerging.md#6-meta-conductor) `#mna`

9. **Robotics/voice capital spike: $1.03B into 6 robotics rounds in one week** (Bedrock $600M, Tutor Intelligence $75M) + **Boson AI ~$70M** (voice foundation models, pairs with Claude Meetings). → [`02` §7–8](./02-new-emerging.md#7-robotics-rounds) `#robotics #voice`

10. **The 2611.xxxxx arXiv wave crystallizes.** **Dependable Long-Horizon Agents (2611.13254)** → mid-trajectory verifier middleware wedge; **Ask2Decide (2611.13015)** → clarification-ranker middleware opportunity; **RLiD (2611.02455)** → 99.3% ALFWorld via decision-plane RL, **replicable this weekend**; **Peer Memory (2611.09990)** negative result **kills the "shared-memory smarter swarm" pitch**; **OpenVLA goal editing (2611.08895)** opens VLA interpretability as a safety lane. → [`04`](./04-research-progress.md) `#arxiv #agents #tts #vla`

11. **Anthropic alignment landed two big ones:** **Reliable Safety Evaluations** guidance (Nov 13, multi-turn + grader safeguards) + **Automated Alignment Researchers paper** — Opus 4.8 beats 28 human researchers' one-shot ideas on characterized failures. **"LLM-on-alignment-work" is now a hireable job family** without a safety PhD. → [`04` §16–17](./04-research-progress.md#16-anthropic-safety-evals) `#anthropic #alignment`

12. **Practical: Claude Code 2.1.304 + MCP 2026-07-28 + LangGraph 1.2.20 + `llm` 0.37.2 security fix.** New Claude Code `InstructionsLoaded` hook (missing piece for repo-wide context injection); MCP 2026-07-28 spec stable with TS SDK 2.4.0 (**Skills-over-MCP**); LangGraph strict resume closes a HITL race-condition bug class; **`llm` 0.37.2 fixes a CVE — upgrade if you ever ran `llm openai endpoint add`**. → [`03`](./03-practical-skills-and-tools.md) `#claude-code #mcp #langgraph #llm #security`

13. **Career: Palantir has the only new-grad FDE pipeline**; Anthropic hires under **"Applied AI Engineer"**. **MSFT buyout India window closes Dec 1**, US/UK/Canada "early December" — ~1,200–3,000 ex-MSFT engineers hit market Jan 1. **Ramp AI Index: Anthropic 49.3% (down 3.9pt), OpenAI 46.1%, SpaceXAI #1 growth** → **hedge the all-Anthropic focusing decision**. → [`05`](./05-career-and-startup.md) `#fde #msft #ramp #comp`

14. **Comp data: `AI Engineer` median $155.5K vs `ML/AI SWE` $250.9K — ~$95K delta.** Ask recruiters for the ML/AI SWE req, not AI Engineer. Also improves H-1B odds (wage-weighted lottery). → [`05` §3](./05-career-and-startup.md#3-comp-data) · [`05` §8](./05-career-and-startup.md#8-h1b-opt) `#comp #h1b`

15. **Anthropic Residency 2026 — apps due Saturday Nov 22.** The single highest-signal direct Anthropic entry point for someone without an alignment track record. 6 days. Cite Mech Interp Survey (2611.08438) + Automated Alignment Researchers in statement. → [`05` §4](./05-career-and-startup.md#4-anthropic-residency) `#anthropic #residency #deadline`

---

## One thing to DO this Sunday

→ **Clear 2 hours this afternoon. Ship one MCP server on TS SDK 2.4.0 — 3 tools, 5-case eval, README, demo gif, pushed to GitHub by 10 pm.** Add one bonus commit: the server routes across **both Anthropic and OpenAI** (hedges the Ramp share-erosion signal + strong interview line). This is the single highest-leverage artifact of the week — 90 min of work = 3 FDE / Applied-AI résumé lines, and the publish window lines up with the Anthropic IPO news cycle (Tue–Wed) when FDE recruiters are actively scanning LinkedIn. Details in [`03` §2](./03-practical-skills-and-tools.md#2-mcp-2026-07-28).

**Bonus (if time):** draft the **Anthropic Residency 2026 application** (due Nov 22 — 6 days) tonight at 60% quality; polish and submit Tuesday. Statement should cite **Mech Interp Survey (2611.08438)** + **Automated Alignment Researchers** + **one portfolio artifact** (your MCP server from the first action, or a mid-trajectory verifier from 2611.13254). [`05` §4](./05-career-and-startup.md#4-anthropic-residency).

## Watchlist deltas

- 🔄 **Anthropic IPO date CORRECTION:** yesterday's edition said "pricing week of Nov 16" — corrected S-1/A locks **pricing Tue Nov 18**, **first trade Wed Nov 19**. Day-1 and above-range pricing are the two watch items.
- 🆕 **NVIDIA Q3 FY27 earnings Mon Nov 17:** new thread. Rubin CPX long-context SKU status is the key question.
- 🆕 **$26B Class N Anthropic private placement to the semi+hyperscaler stack:** new thread. AMD/Broadcom/Google/Micron/Microsoft/Nvidia/TSMC all have a direct stake in Claude-stack job demand.
- 🆕 **OpenAI GPT-6 Cyber + ChatGPT Wallet:** new thread. Watch for the horizontal payments-for-agents startups (Natural, Parallel) pivot.
- 🆕 **Gemini 4 Argon → Carbon 2-week cadence:** new thread. SKU specialization is now faster than flagship versioning.
- 🆕 **Kimi K3.1 Pro revenue-share license:** new thread. First "app store"-style open-weight commercial model.
- 🆕 **Mistral Large 4 open weights (Nov 14):** new thread. Europe has a frontier open-weight flag again.
- 🆕 **LangChain $300M at $3B (CapitalG):** new thread. Google hedging ADK + LangChain simultaneously.
- 🆕 **Mirendil $1B / Mercor $750M / Bedrock Robotics $600M:** new threads. Agentic-AI-for-R&D as a $5B+ category; robotics capital deployment accelerating.
- 🆕 **Meta/Conductor + Five9/Level AI + OpenAI/Odessia + Oura/Counsel Health + Dropbox/Tigris M&A cluster:** new thread. 2026 exit vintage = strategic acquisition.
- 🆕 **Ramp AI Index Nov: Anthropic 49.3% (−3.9pt), SpaceXAI #1 growth:** new thread. Watch Dec Index — if Anthropic stays above 45% through IPO, moat holds.
- 🆕 **"LLM-on-alignment-work" as hireable job family (Automated Alignment Researchers paper):** new thread. Residency conversion rate becomes the leading indicator.
- 🆕 **Anthropic Residency 2026 — Nov 22 deadline:** new thread. 6 days.
- 🆕 **MSFT buyout India sub-wave Dec 1:** new thread. Indian ex-MSFT competition for FDE/MLE reqs spikes first.
- 🆕 **Reversal pattern — Salesforce + Ford rehiring after AI-replacement cuts:** new thread. "Agent + human-in-loop" job family firming up.
- ➡️ **FDE lane (from 2026-11-14):** still hot, but **Palantir is the only one with structural new-grad pipeline**; Anthropic's keyword is **"Applied AI Engineer"**. OpenAI at ~34 reqs, Palantir at 70 (31 new-grad / internship).
- ➡️ **MCP server as #1 FDE portfolio artifact:** still true; TS SDK 2.4.0 just made it 2× faster to ship.
- ⬇️ **Horizontal "Stripe-for-agents" payments wedge:** closed by ChatGPT Wallet. Vertical-only from here.
- ⬇️ **Horizontal CX-agent wedge:** closed by Five9/Level AI consolidation. Vertical-only from here.
- ⬇️ **"Shared memory = smarter swarm" pitch:** killed by 2611.09990 negative result. Justify memory ROI with evals.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo) (the IPO date correction + 6× oversubscription) |
| 20 min | [`01` §1–4](./01-big-lab-moves.md) + [`05` §1–5](./05-career-and-startup.md) — the IPO + Carbon + NVIDIA + MSFT + Ramp + FDE cluster |
| Today | [`03` §2](./03-practical-skills-and-tools.md#2-mcp-2026-07-28) — ship one MCP server before Sunday 10pm |
| By Nov 22 | [`05` §4](./05-career-and-startup.md#4-anthropic-residency) — Anthropic Residency 2026 application |
| Tue–Wed Nov 17–19 | [`01` §1–2](./01-big-lab-moves.md) — NVIDIA earnings + ANT pricing + ANT first trade (36-hour re-pricing window) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
