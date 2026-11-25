# TL;DR — 2026-11-21 (Saturday)

Sixty-second skim. **This is the week the AI market got a public price tag.** On **Nov 18 Anthropic priced its IPO at $83/share (above the $70–78 range), raised ~$81.3B, and debuted Nov 19 on Nasdaq as ANT** — biggest IPO on record, ~**$1.5T fully-diluted at pricing**, ~**$2.1T intraday peak**, closing +17% at **~$97**. Day-1 close is now the public comp anchor every private frontier lab and senior AI hire will quote. The same week: **NVIDIA posted Q3 FY2027 revenue of $115.8B (+103% YoY), with Vera Rubin ramping to ~$20B in its first production quarter — the fastest ramp in the company's history — under interim CEO Colette Kress** (Jensen Huang resigned Nov 12, ⚠️ a story the 2026-11-14 edition missed). **Microsoft Ignite (Nov 17–20) folded Office INTO Copilot** ("Word/Excel/PowerPoint inside Copilot"), the explicit counter-shot at Anthropic's Nov 10 Whiteboards/Sheets/Data/Meetings surface. Underneath: **Ramp Nov 11 AI Index: Anthropic 49.3% token-spend share**, company-adoption lead over OpenAI (44.8% vs 40.6%), **median firm $16.32/employee/month vs top-1% $10,199 (~625×)**. Funding: **Model ML $250M at $1.5B** (AI agents for bankers/consultants), **BrightAI $97M at $750M** (physical AI), **Noeri $110M** (Stanford Yejin Choi + Guestrin, "living AI systems"), **Perplexity crosses $1B ARR**, **Decagon in talks at $4–5B**. Tooling: **Claude Code 2.1.327 → 2.1.328** (Auto Mode default on Opus 4.6 / Sonnet 4.6; **hook failures can now BLOCK actions** — the gate that makes "tests-as-spec" enforceable), **llama.cpp v1.0.0** (stability contract), **SGLang v1.0 + Consortium + Miles v0.2** at the first SGLang Summit. Research: **Gamer VLA for long-horizon games**, **Apple Depth Pro 2**, **π⁴ (4D geometry+motion)**, **Jeveration (parallel image gen, 512×512 in 78ms)**, **"Agents construct their own self-improvement algorithm"**. Career: **tech layoffs crossed 200K YTD with AI cited in 36% of filings**, **FDE postings grew 42× 2023→2025**, **Anthropic FDE $280–320K base**, **Microsoft 60K buyout Dec 1 deadline**.

---

1. **Anthropic IPO priced Nov 18 at $83, debuted Nov 19 on Nasdaq as ANT — biggest IPO on record.** ~**$81.3B raised**, **~7× oversubscribed**, implied **~$1.5T market cap** at pricing, intraday peak **~$2.1T**, open $111.50 (+34%), day-1 close ~$97.17 (+17%). ~980M shares. Tops SpaceX June 2026 listing. Offering closed Fri Nov 20. **The lockup clock starts today → Q2 2027 is the hottest "ex-Anthropic seed" window of the cycle.** → [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo-priced) `#anthropic #ipo #comp`

2. **Jensen Huang resigned as NVIDIA CEO Nov 12; Colette Kress interim. ⚠️ Missed by the 2026-11-14 edition.** 8-K filed; stock -10% pre-market on the news; Huang also stepped off the board. **No permanent successor named.** Then **Nov 17: NVIDIA Q3 FY2027 revenue $115.8B (+103% YoY)**, Data Center $107.6B (+110%), **Vera Rubin ~$20B in its first production quarter = fastest ramp ever**. Q4 guide $130B ±3% (no China DC). → [`01` §2](./01-big-lab-moves.md#2-nvidia-huang-out) `#nvidia #governance #chips`

3. **Microsoft Ignite 2026 (Nov 17–20): Office folded INTO Copilot.** Nadella keynote Nov 17: Word/Excel/PowerPoint now live **inside** the Copilot super-app = Autopilot (long-running) + Code + Home (Chat + Cowork) + Office. Opened by apologizing for the Nov 10 M365 global outage. **Explicit head-to-head with Anthropic's Nov 10 Whiteboards/Sheets/Data/Meetings surface.** Agent discovery store launched. → [`01` §3](./01-big-lab-moves.md#3-microsoft-ignite) `#msft #copilot #products`

4. **OpenAI release notes Nov 17 list GPT-6.2 Astra + GPT-6.2 Sol in API** (text+images); Nov 16 CSAM image classifier; Nov 4 ChatGPT Images 2.6. Single-source lineup — treat as unconfirmed until OpenAI's own release page is re-verified. Meanwhile **OpenAI's own research-acceleration blog** reports **internal agentic use (API-equivalent) now ~2× non-equity comp per researcher**, with Safety & Alignment the largest absolute uplift. → [`01` §4](./01-big-lab-moves.md#4-openai-cluster) `#openai #products #research`

5. **Model ML raises $250M Series B at $1.5B (Nov 17), 18 months out of stealth.** General Atlantic + QED co-lead. AI agents for bankers/consultants/investors; ARR 12× YoY; total raised ~$350M. Points to the dominant **$1–1.5B Series B shape** for vertical-agent companies in Q4 2026. → [`02` §1](./02-new-emerging.md#1-model-ml) `#funding #agents #fintech`

6. **BrightAI $97M at $750M (Nov 18); Noeri $110M to launch (Nov 16).** BrightAI = physical AI on critical infrastructure (sensors/drones on pipelines, power lines); Smith Point Capital leads; GE Vernova strategic; bootstrapped to $80M rev. Noeri = Stanford Yejin Choi + Carlos Guestrin, "living AI systems" that self-improve; Menlo leads, NVIDIA/Madrona/NEA/Snowflake/Cisco in. → [`02` §2](./02-new-emerging.md#2-brightai-noeri) `#funding #physical-ai #agents`

7. **Perplexity crosses $1B ARR (Nov 16 Latent Space weekly); 4× YoY.** Nvidia–Perplexity $30B+ talks from Aug unresolved. **Decagon in talks to raise at $4–5B** (The Information, mid-Nov, not closed). Consumer AI search + vertical customer-support agents both re-marking. → [`02` §3](./02-new-emerging.md#3-perplexity-decagon) `#perplexity #decagon #arr`

8. **Ramp AI Index (Nov 11) — Anthropic takes 49.3% of token-spend share** (week ending Nov 1). **Company adoption: Anthropic 44.8% vs OpenAI 40.6%** (+1pp MoM, +13.3pp YoY). **Spend +1.65% MoM while volume rose and price/M dropped 21%** — wrapper-margin squeeze continues. **Median firm $16.32/employee/month vs top-1% $10,199 (~625×).** → [`05` §1](./05-career-and-startup.md#1-ramp-nov) `#ramp #spend #anthropic`

9. **Claude Code 2.1.327 (Nov 17) + 2.1.328 (Nov 19).** 2.1.327: `claude mcp add-json` reads JSON from stdin (tokens off the command line), shell start-up files run before first Bash approval, `/status` flags broken files/hooks. **2.1.328: Auto Mode is now DEFAULT on Opus 4.6 / Sonnet 4.6**; **hook failures can BLOCK actions** (the gate that makes tests-as-spec actually enforce red); subagent fork controls (`CLAUDE_CODE_FORK_SUBAGENT=0`). → [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-2-1-328) `#claude-code #auto-mode #hooks`

10. **llama.cpp v1.0.0 (Nov 13) + SGLang Summit → v1.0 + Consortium + Miles v0.2 (Nov 12–13 SF).** llama.cpp 1.0: the headline is a **stability contract** (semver breaking C-API bumps major), not throughput; downstream Ollama/LM Studio/Jan/LocalAI get a legitimacy stamp for local-inference procurement. SGLang 1.0 + 9-member Consortium = **first-class OSS inference stack with a governance layer.** → [`03` §2](./03-practical-skills-and-tools.md#2-llamacpp-sglang) `#oss #inference #local`

11. **⚠️ OpenAI Evals full shutdown Nov 30 (read-only since Oct 31) — export this week.** Replacements: Braintrust (~$800M post Feb $80M B), Langfuse (ClickHouse-acquired Jan 2026, still OSS), promptfoo (OpenAI-acquired Mar 2026, still MIT). Caveat: date surfaced via third-party — confirm against OpenAI release notes before Fri. → [`03` §3](./03-practical-skills-and-tools.md#3-openai-evals-shutdown) `#evals #openai #migration`

12. **Research cluster (Nov 13–19):** **Gamer** (arXiv 2611.18397 — generalist VLA with cloud-edge inference engine, skilled-player parity on 3D open-world games), **Apple Depth Pro 2** (2611.26603 — single net, metric monocular depth, images+video, code+weights), **π⁴** (2611.23144 — 4D scene geometry + motion from uncalibrated obs), **Jeveration** (2611.24738 — freezes a VLM, parallel image gen, **512×512 in 78ms, up to 122× faster**), **"Do LLM Agents Still Need to Be Told How to Self-Improve?"** (2611.23219 — agents construct their own context-based self-opt algorithm, the natural MRTPO successor). → [`04`](./04-research-progress.md) `#arxiv #vla #depth #agents`

13. **Tech layoffs crossed 200K YTD; AI cited in 36% of filings (vs 16% in 2025).** Layoffs.fyi 135K / TrueUp 205–207K through Nov 13. **SoundHound AI 8-K cuts ~27% of workforce (Nov 4).** Canva, Squarespace, Amazon, Angi, Block in Nov. **Microsoft 60K buyout Dec 1 deadline** — 3–5% uptake baseline = 1,800–3,000 engineers hit the market Jan 1. → [`05` §2](./05-career-and-startup.md#2-layoffs-200k) `#layoffs #msft #timing`

14. **FDE postings grew 42× 2023→2025 (LinkedIn); Anthropic posts "Head of FDE" role** = formal org build-out. **Anthropic FDE Sales: $280–320K base** (SF/NY/Seattle). **Epoch AI: Anthropic GTM share 17%→31%**, OpenAI 18%→28%. **New-grad AI premium at ~5× NACE CS baseline**, Entrepreneur citing "up to $400K for new grads" at hot AI startups. Levels: Anthropic SWE median ~$600K, OpenAI SWE ~$795K (not entry). → [`05` §3](./05-career-and-startup.md#3-fde-still-boom) `#fde #careers #comp`

---

## One thing to DO this Saturday

→ **Spend 60 minutes publishing a working MCP server with blocking hook support + fire 3 FDE applications to companies that just raised.** The specific target: an MCP server that wraps a sandboxed shell (Simon Willison's Nov 17 blogmark) and emits a Claude Code `SubagentStop`/`PreToolUse` hook that blocks on test failure (the 2.1.328 feature). That's **the #1 FDE portfolio artifact**, shipped in 60 minutes, positioned against exactly the roles Anthropic/Model ML/BrightAI/Noeri/Decagon are hiring for right now. Then 3 apps: **Anthropic (Head of FDE / FDE Sales), Model ML (just raised $250M), BrightAI (just raised $97M)**. Details in [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-2-1-328) and [`05` §3](./05-career-and-startup.md#3-fde-still-boom).

## Watchlist deltas

- 🆕 **ANT public comp anchor:** new thread. Track Day-5/Day-10 close vs $83 pricing, options volume, and whether short interest builds ahead of Q2 2027 lockup expiry.
- 🆕 **NVIDIA governance + Rubin ramp:** new thread. Watch (a) permanent-CEO succession, (b) whether Rubin $20B/qtr pace holds in Q4, (c) OpenAI × Broadcom Ethernet deployment start.
- 🆕 **Microsoft Copilot-as-OS vs Claude Fable:** new thread. Watch (a) Copilot super-app retention curves at Ignite +30d, (b) Google Workspace's response, (c) whether Office-inside-Copilot cannibalizes legacy license revenue.
- 🆕 **Claude Code blocking hooks + Auto Mode default:** new thread. Watch whether `.claude/hooks/pre-tool-use/` publish templates become the 2026-q4 equivalent of `.editorconfig`.
- 🆕 **OpenAI Evals shutdown Nov 30:** new thread. Watch Braintrust/Langfuse/promptfoo migration guides and whether any of the three ships an "OpenAI Evals importer" by the deadline.
- 🆕 **llama.cpp 1.0 + SGLang Consortium:** new thread. Watch whether a second OSS-inference consortium forms around vLLM and whether enterprise procurement starts citing semver compliance.
- 🆕 **"Living AI systems" (Noeri) framing:** new thread. Watch whether this becomes the agent-ops wedge VC brands in 2027 planning memos.
- 🆕 **Jeveration-style parallel image gen:** new thread. Watch whether any production T2I service ships 78ms 512×512 inference at <$0.001/image.
- ➡️ **Anthropic IPO window (from 2026-11-14):** resolved on the upside — pricing above range, biggest IPO ever, now a public company. Move to lockup-expiry countdown.
- ➡️ **FDE lane (from 2026-11-14):** still ramping — 42× growth, Anthropic opens Head of FDE role. Apply this weekend.
- ⬇️ **"Latest model fluency":** further deprecated. GPT-6.2 Astra + Sol, Gemini 4 Argon, Fable 5.2 + Mythos 5.2 — model choice is a routing/eval question, not a résumé line.
- ⬇️ **Pure wrapper-on-GPT startup pitches:** Ramp's 21% price drop + spend-flat pattern confirms the margin squeeze. Vertical + physical + regulated only.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo-priced) (the ANT pricing + Day 1 story) |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) + [`05` §1–3](./05-career-and-startup.md) — ANT + NVIDIA + Ignite + Ramp + FDE playbook |
| Today | [`05` §3](./05-career-and-startup.md#3-fde-still-boom) — 3 FDE apps (Anthropic Head of FDE, Model ML, BrightAI) |
| This weekend | [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-2-1-328) — ship a sandboxed-shell MCP server with a blocking pre-tool-use hook |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
