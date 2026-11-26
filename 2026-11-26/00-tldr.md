# TL;DR — 2026-11-26 (Thanksgiving Eve)

Sixty-second skim. **Anthropic is a public company. ANT priced at $83 on Nov 18, opened at $111.50 on Nov 19, raised ~$81.3B — the largest IPO on record, bigger than SpaceX if it ever lists.** OpenAI shipped **GPT-6.2 Astra + Sol on Nov 17** at the exact same $8/$40 and $2/$10 price points as Claude Fable 5.2 / Mythos 5.2 — the frontier is now explicitly priced the same by the top two labs, so the arena moves entirely to **routing, tool-use, and eval quality**. Google ran a two-model Gemini 4 drop: **Carbon (Nov 10, frontier)** and **Hydrogen (Nov 12, fast/cheap)**, with **Neon** already spotted in the Gemini web app code. Anthropic followed its own IPO week by **launching Claude Ship on Nov 23** — AI agents that **review, fix, *and* approve** pull-request changes end-to-end on GitHub (Team + Enterprise). **NVIDIA FY27 Q3 printed $115.8B revenue (+103% YoY), $107.6B Data Center (+110%), and guided Q4 to $130B** — AI infra demand did not cool one bit. Under the surface: **Mercor $750M Series D at $20B (NVDA + Salesforce + Zoom)**, **Sierra in talks at ~$30B on $1.5B (The Information)**, **a16z launched a Forward-Deployed Engineer Fellowship (Dec 31 deadline)**, **Microsoft's 60K-person voluntary buyout hit its Dec 1 deadline** (Nadella: "I wish I could say it'll all be the same — I cannot"), and **Chinese open-weight frontier compressed to Kimi K3.1 Pro / GLM-5.3 / Qwen 3.8** on the Artificial Analysis v5 index. Research-side: **DiscoveryAgent (arXiv 2611.21950)** showed audit agents help human scientists catch **14× more valid errors**; **"Agents, Think Only When It Helps" (arXiv 2611.05709)** dismantled a lot of chain-of-thought dogma for distilled agents. **FDE is still the single highest-leverage lane for a CS grad without a PhD; MCP servers + eval harnesses are still the portfolio asset to ship this weekend** — but the new skill to add is **PR-review automation** (Claude Ship + Code Review + `@claude review` triggers).

---

1. **Anthropic ANT: $83 IPO, $111.50 open, $81.3B raised — the biggest IPO ever.** Priced above the $70–78 range on **Nov 18**, began trading **Nov 19** on Nasdaq Global Select under **ANT**, closed the offering **Nov 20**. **980M shares** sold, fully-diluted market cap near **$1.5T** at open per CNBC. **Lockup expiry ~May 2027 = Q2 2027 is still the hottest "ex-Anthropic researcher seed" window of the cycle**, now with real price discovery behind it. → [`01` §1](./01-big-lab-moves.md#1-anthropic-ant-ipo) `#anthropic #ipo #comp`

2. **OpenAI GPT-6.2 Astra + Sol ship Nov 17 — same price points as Claude Fable 5.2 / Mythos 5.2.** **Astra $8/M in, $40/M out** (frontier); **Sol $2/M in, $10/M out** (everyday). Both in ChatGPT Work, Codex, and the API as `gpt-6.2-astra` and `gpt-6.2-sol`. **Astra is the first model OpenAI has deployed that crossed its Preparedness Framework "High" threshold for AI Self-Improvement.** Independent benches: #2 overall, trails Fable 5.2 on coding-agent evals. → [`01` §2](./01-big-lab-moves.md#2-gpt-62-astra-sol) `#openai #models #pricing`

3. **Google Gemini 4 Carbon (Nov 10) + Hydrogen (Nov 12), Neon leaked.** **Carbon** = frontier long-horizon model (intro pricing through Nov 30; then **$4/M in, $20/M out**). **Hydrogen** = fast/cheap daily driver. **Neon** spotted in Gemini web-app code with no model card yet. Carbon went to a cybersecurity-defender early-access group two weeks before public GA. → [`01` §3](./01-big-lab-moves.md#3-gemini-4-carbon-hydrogen) `#google #gemini #pricing`

4. **Anthropic Claude Ship (Nov 23) — AI agents that review, fix, AND approve PRs.** Team + Enterprise plans, GitHub repos. Builds on Code Review (March 2026) + the `@claude review` command — but now closes the loop: an agent can **propose the fix, apply it on a branch, and auto-approve** when the eval gates pass. This is the first mainstream "merge-without-a-human" surface. → [`01` §4](./01-big-lab-moves.md#4-claude-ship) `#anthropic #claude-code #agents`

5. **NVIDIA FY27 Q3: $115.8B revenue (+103%), $107.6B Data Center (+110%), Q4 guide $130B.** Hyperscalers $60.1B (+71%); **AI-cloud/industrial/enterprise $47.5B (+195%)** — non-hyperscale is now the faster-growing bucket. Shipped **$2.4B Hopper to China this quarter but guides $0 China DC compute for Q4**. Vera Rubin shipping under interim CEO Colette Kress. → [`01` §5](./01-big-lab-moves.md#5-nvidia-fy27-q3) `#nvidia #chips #infra`

6. **Mercor $750M Series D at $20B — NVDA + Salesforce + Zoom join (Nov 10–11).** Valuation **doubled in a year** (Series C was $350M at $10B, Oct 2025). Round includes an undisclosed employee tender. Mercor runs the data-labor marketplace that most frontier labs quietly rely on for RLHF + eval. → [`02` §1](./02-new-emerging.md#1-mercor) `#funding #rlhf #data-labor`

7. **Sierra in talks at ~$30B on ~$1.5B round (The Information, Nov 18).** Lightspeed, Greenoaks, Benchmark as leads. **ARR hit $400M in October** (from $150M in Feb). This would be **~75× ARR** — the "enterprise-logo premium" from 2026-11-14's Rox entry has only compressed further. → [`02` §2](./02-new-emerging.md#2-sierra) `#funding #agents #customer-support`

8. **Chinese open-weight frontier now = Kimi K3.1 Pro / GLM-5.3 / Qwen 3.8.** AA Index v5 (Nov 5) rankings: **K3.1 Pro 46 / GLM-5.3 32 / Qwen 3.8-27B** in the running. Five Chinese labs have compressed into a thirty-day release window on two licensing models (modified-MIT, revenue-gated custom). **The US open-weight frontier is still not obviously best.** → [`02` §3](./02-new-emerging.md#3-china-open-weight) `#open-source #china`

9. **Microsoft 60K voluntary-buyout Dec 1 deadline passed; Nadella confirms AI is behind it.** At the Nov 19 analyst Q&A: *"I wish I could just sit here and say it'll all be the same. I cannot."* Industry 3–5% baseline uptake → **1,800–3,000 ex-MSFT engineers hit the open market by Jan 1**. The **Jan 2027 market will be flooded** — fire your apps by Dec 15 or wait until March. → [`05` §1](./05-career-and-startup.md#1-microsoft-buyout) `#msft #layoffs #timing`

10. **a16z Forward-Deployed Engineer Fellowship 2027 — Dec 31, 2026 deadline.** Eight-week fellowship for FDEs and applied-AI leaders. First institutional-VC program explicitly for the FDE track. **Combine this with the Microsoft wave and the Anthropic IPO: the FDE lane is now (a) VC-credentialed, (b) backed by public-market comps (ANT), (c) still the fastest-growing non-research AI role.** → [`05` §2](./05-career-and-startup.md#2-a16z-fde) `#fde #careers #fellowship`

11. **Research this fortnight: DiscoveryAgent + "Think Only When It Helps" + Access-Control for Agents.** (a) **DiscoveryAgent (arXiv 2611.21950)** — audit agents find **14×** more valid errors when paired with human scientists. (b) **"Agents, Think Only When It Helps" (arXiv 2611.05709)** — altering/discarding reasoning traces barely hurts distilled agent performance; implication: a lot of chain-of-thought spend is wasted on eval-passing routines. (c) **"Rethinking Access Control for AI Agents" (arXiv 2611.06764)** — the first systematic survey of what breaks when you let an agent act with a user's permissions. → [`04`](./04-research-progress.md) `#arxiv #agents #security`

12. **Practical: Claude Code 2.1.327 (Nov 17) + Claude Ship + MCP 2026-07-28 + `@claude review` triggers.** The new portfolio recipe: **(a)** publish one MCP server, **(b)** wire it to a `@claude review` GitHub trigger, **(c)** ship a Claude Ship-eligible eval gate, **(d)** show one `/skill-doctor`-clean skill that uses it. This is the current single-weekend FDE-ready portfolio stack. → [`03`](./03-practical-skills-and-tools.md) `#claude-code #mcp #fde-portfolio`

13. **The re-price of the fortnight: the frontier is now a commodity at $8/$40 (Claude Fable 5.2, GPT-6.2 Astra, Gemini 4 Carbon post-promo all at same price tier).** Three labs independently converged on the identical price point for the identical capability tier within six weeks. **Pricing is no longer a differentiator; routing / eval / vertical data / forward deployment are.** For job search: **stop benchmarking by model name**; **start benchmarking by eval-harness design + MCP surface built + PRs merged by a review-agent you configured.** → [`05`](./05-career-and-startup.md) `#reprice #careers #skills`

14. **Secondary moves worth 60 seconds each:** (a) **OpenAI raised ~$11B on Nov 6** per aggregator reporting — follows the Microsoft/Nvidia/SoftBank compute-commit chain. (b) **Fal $1.65B at $16B (Series E+F)** confirmed by Bessemer lead. (c) **Mind Robotics**, **Wayve**, **AI21 Labs** all back on the quarterly-funding leaderboard. (d) **Palantir has NOT run mass layoffs in 2026**, despite click-bait headlines — FDEs still hiring. → [`02` §4](./02-new-emerging.md#4-secondary-moves) `#funding #robotics`

---

## One thing to DO this Thursday

→ **Spend 90 minutes today setting up Claude Ship on one of your own GitHub repos. Then, in 20 minutes, draft the a16z FDE Fellowship application.** The Microsoft buyout wave + the Anthropic IPO lockup math + the a16z Dec-31 deadline + the Jan-1 flood are *all one story*: **the FDE hiring window is open right now and starts closing in six weeks**. Put ANT, GPT-6.2, and Gemini 4 Carbon through a single cost-aware router (one afternoon with LiteLLM or similar) and screenshot the cost-per-task delta — that chart is an interview answer on its own. Detailed steps in [`05` §2](./05-career-and-startup.md#2-a16z-fde).

## Watchlist deltas

- 🆕 **ANT public trading:** new thread. Track price vs. $83 IPO + opening $111.50; watch for the **May 2027 lockup expiry** and Anthropic's first earnings call cycle (probably late Feb 2027).
- 🆕 **GPT-6.2 Astra "AI Self-Improvement High" designation:** new thread. First frontier model shipped past OpenAI's own Preparedness threshold — track whether Anthropic / Google follow with similar public designations under their RSPs.
- 🆕 **Gemini 4 Carbon / Hydrogen / Neon:** new thread. Watch which model gets Antigravity integration and whether Google starts routing Workspace by SKU.
- 🆕 **Claude Ship "AI-approved merges":** new thread. First major surface where an agent *approves* (not just comments). Watch the first regulated-industry incident (fintech, healthcare) and how GitHub's required-reviewer rules evolve.
- 🆕 **NVIDIA $0 China DC guide:** new thread. First quarter with explicit $0 China data-center compute guidance — track Huawei Ascend ramps and whether Chinese labs retool around domestic silicon.
- 🆕 **Mercor $20B + NVDA/Salesforce/Zoom stakes:** new thread. Data-labor marketplaces now a top-5 AI category by valuation; track Scale AI, Surge, Toloka response.
- 🆕 **a16z FDE Fellowship:** new thread. First VC-run program for the FDE track — track admission rate, placements, and whether YC follows.
- ➡️ **Anthropic IPO window (from 2026-11-14):** resolved. Thread moves to ANT public-market trading + lockup.
- ➡️ **Microsoft 60K buyout (from 2026-11-14):** Dec 1 deadline arrives today. Watch uptake % announcement in the Nadella Dec earnings commentary.
- ➡️ **FDE lane (from 2026-10-14, 2026-11-14):** reinforced. a16z fellowship + MSFT Frontier Company (6K FDEs) + EY $1B commitment stacks.
- ⬇️ **"Latest model" fluency:** further deprecated. Three labs converged on $8/$40 within six weeks; the model-name résumé bullet is now effectively zero-signal.
- ⬇️ **Generic "AI agent" wedges:** Sierra at $30B closes the enterprise-support category for new entrants without vertical data.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-ant-ipo) (ANT trades) |
| 20 min | [`01` §1–4](./01-big-lab-moves.md) + [`05` §1–2](./05-career-and-startup.md) — IPO + GPT-6.2 + Gemini 4 + Claude Ship + MSFT-buyout + FDE playbook |
| Today | [`05` §2](./05-career-and-startup.md#2-a16z-fde) — draft the a16z FDE Fellowship app before Dec 31 |
| This weekend | [`03` §2](./03-practical-skills-and-tools.md#2-claude-ship-setup) — wire Claude Ship into one of your own repos + screenshot one merged agent-approved PR for your portfolio |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
