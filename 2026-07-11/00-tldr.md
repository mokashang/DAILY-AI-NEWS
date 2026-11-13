# TL;DR — 2026-07-11 (Saturday)

Sixty-second skim. **The mobile super-app war went live this week — and the Anthropic-stack focusing decision just got its strongest validation yet.** In the same 48-hour window, **OpenAI merged Codex + ChatGPT into a single "super app"** (with GPT-5.6 in three sizes: **Sol / Terra / Luna**, rolling out to Pro/Enterprise/Edu on July 9), and **Anthropic shipped Claude Cowork for iOS + Android** — mobile agentic sessions that finally cut the "desktop must stay open" constraint. Underneath the app war, three deeper signals landed: **DeepMind's talent exodus** (Noam Shazeer → OpenAI; **Nobel laureate John Jumper + Jonas Adler + Alexander Pritzel → Anthropic** — all in one week; **~$225B off Alphabet's cap**); **Anthropic Claude Science** (60+ research tools + neglected-disease drug discovery); and the **OpenAI IPO slipping to 2027** (Altman won't list below $1T). Meanwhile: **Grok 4.5 landed at #4** on the Intelligence Index (below Claude Fable 5 #1, GPT-5.5 #2, Claude Opus 4.8 #3) at ~60% of Opus/GPT-5.5 pricing; **xAI rebranded to SpaceXAI**; **Gemini 3.5 Pro delayed to July 17** (6 days out — full architectural rebuild). For you: **your mobile is now the agent surface**, **Fable 5 + Sonnet 5 at $2/$10 is the price-quality lever of the summer**, and **Anthropic just became the destination for public-market talent flight**.

---

1. **OpenAI ships the super app (Codex + ChatGPT merged) + GPT-5.6 (Sol / Terra / Luna).** July 9 rollout on web + mobile, Pro/Enterprise/Edu first, Plus/Business over the following days. New ChatGPT desktop app + hosted websites feature (build/share sites from ChatGPT Work). Framed as *"competitive with far more expensive models at 2× speed, much cheaper."* → [`01` §1](./01-big-lab-moves.md#1-openai-superapp) `#openai #gpt56 #superapp #chatgpt-work`

2. **Anthropic Claude Cowork for iOS + Android (mobile-first counter).** July 10. Removes the constraint that agentic sessions required a desktop to remain active — you delegate a long-running knowledge-work agent, close your laptop, monitor from the phone. Directly pairs with **Claude Code Routines on the web** (templated cloud agents fired by schedule / GitHub event / API) and mobile push notifications. Your phone is now the control surface. → [`01` §2](./01-big-lab-moves.md#2-cowork) `#anthropic #cowork #mobile #agents`

3. **DeepMind talent exodus — Anthropic wins the week.** Four senior DeepMind researchers left inside a single week: **Noam Shazeer (Gemini co-lead) → OpenAI**; **John Jumper (Nobel Chemistry 2024, AlphaFold) + Jonas Adler + Alexander Pritzel → Anthropic**. Markets wiped **~$225B off Alphabet's market cap**. Combined with the June arrivals (Sonnet 5, Fable 5 global redeploy), this is the **loudest destination signal since Karpathy (May 19)**. → [`01` §3](./01-big-lab-moves.md#3-deepmind-exodus) · [`05` §1](./05-career-and-startup.md#1-anthropic-destination) `#anthropic #talent #deepmind`

4. **Claude Science + drug discovery (Anthropic vertical wave, week 6).** 60+ scientific research tools bundled into Claude Pro/Max/Team/Enterprise (beta); dedicated **drug-discovery program for neglected diseases** in partnership rollout. Extends the Legal / Small Business / Finance / Gates-Foundation-health vertical arc. → [`02` §1](./02-new-emerging.md#1-claude-science) `#anthropic #verticals #science #drug-discovery`

5. **OpenAI IPO slipped to 2027 — Altman's $1T floor holds.** Bloomberg/Reuters (late June): OpenAI is now leaning toward a **2027 listing**, not September/October 2026, citing market volatility and Altman's hard floor at $1T. Financials underlying the S-1 (~$25B ARR, ~$2B/mo revenue, loses $1.22/$1 rev) leaked into the reporting. → [`01` §4](./01-big-lab-moves.md#4-ipo-slip) `#openai #ipo #public-markets`

6. **Grok 4.5 ships at #4 for ~60% off — SpaceXAI rebrand.** July 8. 1.5T-param V9 foundation, trained on **real Cursor session data** (coding + agentic); ranks **#4 on Artificial Analysis Intelligence Index (54)** behind **Fable 5 (#1) / GPT-5.5 (#2) / Opus 4.8 (#3)**; **~60% cheaper than Claude Opus 4.8 or GPT-5.5**; **54% hallucination rate** (real risk). Company rebranded **xAI → SpaceXAI** July 6 (nested logo, @SpaceXAI). Musk: *"Done with Grok Imagine."* → [`02` §2](./02-new-emerging.md#2-grok45) `#xai #spacexai #grok #benchmarks`

7. **Practical (do tonight): the code-execution-with-MCP + federated-orchestration playbook.** Anthropic's shift — expose MCP tools as *code on a filesystem*, load on demand, filter data before it reaches the model → cuts token cost + latency. Pair with the "**federated topology**" pattern (thin ingress + specialists) that replaces the anti-pattern "god orchestrator." Both are direct upgrades to the May-22 Opus-orchestrator/Sonnet-worker team; both are portfolio-artifact worthy. → [`03` §1](./03-practical-skills-and-tools.md#1-code-exec-mcp) `#mcp #agents #orchestration #cost`

8. **Research: agents that self-govern their own context (Self-GC) + anytime-valid certificates.** Two arXiv drops name the same thing that Fable 5's 1M ctx + always-on adaptive thinking hides in production: **the long-horizon agent must decide what to forget, when, with what guarantee.** Verification/routing is again the scarce skill. → [`04` §1](./04-research-progress.md#1-self-gc) `#arxiv #research #agents #memory`

---

## One thing to DO this Saturday

→ **Install Claude Cowork on your phone + build your first cloud Routine tonight** — pick one repeatable task (weekly research digest, Monday-morning inbox triage, PR-babysitter, arXiv scanner for your subfield) and wire it as a **Routine on Claude Code on the web** fired by a schedule. Add push notifications. Screenshot the run for your portfolio (job artifact: *"I built and operated an autonomous mobile-first knowledge agent"* — direct FDE / Integration Engineer interview material). Cross-link: [`03` §2](./03-practical-skills-and-tools.md#2-artifact).

## Watchlist deltas (since last edition, 2026-05-22)

- 🆕 **OpenAI super app (Codex + ChatGPT merged) + GPT-5.6 (Sol/Terra/Luna):** new thread. Watch: how fast Plus/Business tier gets the model; whether the "hosted websites" feature builds a real distribution channel; what Codex-agent-in-ChatGPT does to Cursor/Replit revenue.
- 🆕 **Anthropic Claude Cowork for mobile (iOS + Android):** new thread. Watch: adoption vs ChatGPT mobile; integration with Routines + Claude Code CLI native binaries; whether Enterprise SSO ships.
- 🆕 **Anthropic vertical wave — Claude Science + drug discovery for neglected diseases:** extends the 2026-05 vertical arc (Legal → Small Business → Finance → Gates-health → **Science/Drug Discovery**). Watch: partner disclosures, first published protocol.
- 🆕 **DeepMind → Anthropic (Jumper/Adler/Pritzel) + Shazeer → OpenAI:** new talent thread. Watch: where their first published work lands and which pre-training group at Anthropic (Karpathy's team?).
- 🔻 **OpenAI IPO:** **slipped from Sept 2026 → 2027.** Status flips 🟢→🟡. Trigger conditions: Altman signals accepting <$1T; SEC pre-effectiveness comments leak; Anthropic files first.
- 🔻 **Gemini 3.5 Pro:** delayed to **July 17** (T-6 days). Watch the launch → will inform your Anthropic-stack vs multi-vendor rebalancing.
- ➡️ **Trump AI executive order:** re-emerged as **voluntary AI-release standards** (July 3 draft) + reported **OpenAI-offered-govt-5%-stake** angle. Still 🟡. Pre-deployment-eval career lane remains live.
- ➡️ **Agent SDK metering (June 15):** now in force; the Opus/Sonnet/Haiku split you set up in May is your on-going hedge. The new [Anthropic help center](https://support.claude.com/en/articles/15036540-use-the-claude-agent-sdk-with-your-claude-plan) doc governs the separate monthly credit.
- ➡️ **Karpathy → Anthropic (pre-training / Claude-improves-Claude team):** still tracked; the Jumper/Adler/Pritzel arrivals expand the same lab. Next disclosure to watch: internal team names / paper preprints.
- 🆕 **China anthropomorphic-AI rules (effective July 15):** ByteDance/Alibaba disabling humanlike-agent features. Watch: whether US/EU adopt a mirror; downstream effect on companion-AI startups.
- 🆕 **Rankings snapshot (Artificial Analysis, July 8):** Fable 5 #1 · GPT-5.5 #2 · Opus 4.8 #3 · Grok 4.5 #4 · Gemini (all versions) below Grok 4.5. The frontier order matters for every offer you take.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1–2](./01-big-lab-moves.md) (super-app + Cowork = the mobile agent surface) |
| 20 min | [`01` §3](./01-big-lab-moves.md#3-deepmind-exodus) (talent) + [`03` §1](./03-practical-skills-and-tools.md#1-code-exec-mcp) (code-execution-with-MCP) — the two most durable signals |
| Today | [`03` §2](./03-practical-skills-and-tools.md#2-artifact) — install Cowork + ship your first Routine |
| Weekend | [`05` §3](./05-career-and-startup.md#3-weekend) — refresh the Anthropic-stack portfolio artifact against Fable 5 + Sonnet 5 pricing |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
