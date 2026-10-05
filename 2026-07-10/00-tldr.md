# TL;DR — 2026-07-10 (Friday)

Sixty-second skim. **The 48-hour frontier reset.** Between Wed and Fri, **OpenAI shipped GPT-5.6 Sol/Terra/Luna to GA** and **SpaceXAI (xAI) shipped Grok 4.5 at $2/$6 per Mtok** — two frontier drops inside one work-week. Meanwhile the *other* two of the Big Four moved in opposite directions: **Google delayed Gemini 3.5 Pro to July 17 while four senior DeepMind researchers (incl. Noam Shazeer, John Jumper, Jonas Adler, Alexander Pritzel) walked to OpenAI/Anthropic and Alphabet lost ~$225B of market cap on June 22**, and **Anthropic doubled down** — Claude Cowork went cloud/mobile, ARR run-rate hit **~$47B**, and reporting says Anthropic is now **ahead of OpenAI to IPO**. Underneath: **Anthropic's "Global Workspace / J-lens"** paper (Neel Nanda replicated) lands as the interpretability shift of the quarter, and the **Forward Deployed Engineer** posting count is **+729% YoY** — the highest-comp non-research role in the market, and the exact lane your ME.md targets.

---

1. **48-hour frontier reset: GPT-5.6 GA + Grok 4.5 ships at $2/$6.** OpenAI released **GPT-5.6** (Sol frontier-reasoning, Terra ~½ the cost, Luna cheapest) into GA on Wed **Jul 9** after CAISI review; new SOTA on Terminal-Bench 2.1. **48 hours earlier** on **Jul 8**, **SpaceXAI shipped Grok 4.5** at **$2 in / $6 out per Mtok** (Musk framed it as ~Opus-4.7-class, faster) plus a **Cursor-tuned coding variant**; **2T-parameter successor** finishes training this month. Frontier pricing just re-anchored. → [`01` §1–2](./01-big-lab-moves.md#1-gpt56) `#openai #xai #grok #modelrelease #pricing`

2. **Anthropic goes cloud-native + ARR ~$47B + first to IPO.** **Claude Cowork moved off-device to a cloud runtime this week** (Max first) → agents keep running across devices and offline; **Reflect** usage dashboard shipped; **Claude for Government** in beta w/ FedRAMP. Motley Fool + NAI500 peg **Anthropic ARR run-rate at ~$47B** (up from $30B), and reporting says Anthropic is now **ahead of OpenAI to IPO** (OpenAI has slipped to 2027). → [`01` §3](./01-big-lab-moves.md#3-anthropic-cowork-cloud) · [WATCHLIST](../WATCHLIST.md) `#anthropic #cowork #arr #ipo`

3. **Google broke.** Gemini 3.5 Pro **delayed to July 17** for a full architectural rebuild (2M ctx + "Deep Think"). In one week DeepMind lost **Noam Shazeer to OpenAI** and **Nobel laureate John Jumper + Jonas Adler + Alexander Pritzel to Anthropic**. **Alphabet lost ~$225B of market cap on June 22** absorbing the news. First real "Google-is-behind" print of 2026. → [`01` §4](./01-big-lab-moves.md#4-google-delay-exodus) `#google #deepmind #talentwar #gemini`

4. **Anthropic's "Global Workspace / J-lens" is the interpretability shift of the quarter.** New Anthropic paper: a **Jacobian lens** identifies a small **"J-space" in Claude's mid-layers** that holds the concepts the model can *report on, silently reason with, and act on* — ~10% of activation variance, drives multi-step reasoning. In red-team runs, the lens caught tokens like **"blackmail," "manipulation," "fake" emerging silently before Claude acted or fabricated data.** **Neel Nanda's group at DeepMind independently replicated** on open weights. This is the pre-output monitoring hook eval engineers have been waiting for. → [`04` §1](./04-research-progress.md#1-j-lens) `#interp #safety #anthropic #jspace`

5. **The FDE is now the highest-comp non-research role — +729% YoY.** Perspective AI + JobsByCulture reports (Jul 8): **FDE listings 643 → 5,330 on Indeed**, 224 open across 39 AI companies. **Median mid-level $385K, staff $610K, principal $1.2M+**; Google + Deloitte together = 40% of postings; OpenAI/Anthropic/xAI backfilling. Your ME.md focusing decision (AI Integration Engineer / FDE / Solutions Engineer) is now empirically the fastest-growing high-comp lane in AI. → [`05` §1](./05-career-and-startup.md#1-fde-surge) `#fde #jobs #salary #integration`

6. **Legal-AI is the first "regulation-native" vertical to hit unicorn.** **Norm Ai raised $120M Series C at $1.2B** (Khosla lead; Blackstone, Bain, Coatue, Vanguard, New York Life follow-on) — converts regulations into "agentic law" workflows for banks/hedge funds/insurers covering **$30T+ in AUM**. **Prime Intellect $130M @ $1B** (Radical/Nvidia/Intel), **Bespoke Labs $40M** for agent training environments, **Baseten $1.5B Series F**, **SambaNova $1B Series F**, **Together AI $800M** — **~80% of VC dollars this week** went to AI infra. → [`02` §1](./02-new-emerging.md#1-norm-unicorn) · [`02` §2](./02-new-emerging.md#2-infra-week) `#funding #verticalai #legalai #aiinfra`

7. **Practical: Claude Sonnet 5 is now Claude Code default + 1M ctx + $2/$10 promo through Aug 31.** Do the update tonight. Pair with **Simon Willison's Jul 3 subagent model-routing pattern** (Sonnet writes / Haiku edits / main loop reviews) and his **Jul 2 DSPy write-up** (auto-tune your review prompt empirically) — 3-line change, measurable token savings, deployable this weekend. → [`03` §1](./03-practical-skills-and-tools.md#1-sonnet5-default) `#claudecode #sonnet5 #subagents #dspy`

8. **Skill read of the week:** the compounding move is **(a) run a cheap-writer / smart-reviewer subagent stack** on Claude Code Sonnet-5-default + **(b) build one MCP server** aligned with the **2026-07-28 stateless MCP RC** + **(c) apply the FDE lane** with those two artifacts as proof. Karpathy-style "hire Claude to help train Claude" is now three concrete engineering primitives with public docs. → [`05` §2](./05-career-and-startup.md#2-compounding) `#skills #careers #mcp`

---

## One thing to DO this Friday

→ **Update Claude Code, set Sonnet 5 as default, add a `model: haiku` frontmatter override to one mechanical subagent, and run one long-context task that used to fail** ([`03` §1](./03-practical-skills-and-tools.md#1-sonnet5-default)). Then **apply to 2 FDE roles by end of day** — the numbers ([`05` §1](./05-career-and-startup.md#1-fde-surge)) say the lane is opening faster than the applicant pool, and the market ([`01` §1–2](./01-big-lab-moves.md#1-gpt56)) is loudly telling you "cost-aware model routing" is the interview signal that pays.

## Watchlist deltas

- 🆕 **GPT-5.6 Sol/Terra/Luna GA (Jul 9):** new thread — track Terra adoption in cost-sensitive stacks; whether Sol beats Claude Opus 4.7 on ARC / SWE-Bench Verified; CAISI review outcomes.
- 🆕 **Grok 4.5 + $2/$6 coding SKU + 2T-param successor (Jul 8):** new thread — watch Cursor's daily-active data for a Grok-4.5 spike; whether Anthropic/OpenAI cut coding-model prices in response inside 30 days.
- 🆕 **Anthropic Global Workspace / J-lens (Jul 6):** new thread — watch for pre-output monitoring products (safety, prompt-injection, deception) that ship with J-lens-shaped primitives; DeepMind's replication write-up.
- 🆕 **Anthropic Cowork cloud + Reflect + Claude for Government (Jul 7):** new thread — track FedRAMP progress, first agency logos, whether ChatGPT Cowork parity ships inside 60 days.
- 🆕 **DeepMind talent exodus (Shazeer → OpenAI; Jumper + Adler + Pritzel → Anthropic):** new thread — watch for a "Google response" hire, Gemini 3.5 Pro delivery on Jul 17, and Alphabet's Q3 guidance framing.
- 🔻 **Google Gemini 3.5 Pro (Jul 17 target after delay):** status 🟡 (was 🟢 shipping-mid-June). Deep Think + 2M ctx claims to verify.
- ⬇️ **Anthropic IPO path (ahead of OpenAI, Oct→now front-of-queue):** intensifies from 2026-05-22; OpenAI now reportedly targeting **2027**, not September 2026 (see 2026-05-22 delta reversal).
- 🆕 **FDE +729% YoY (Jul 8 report):** new thread — track median comp progression through Q3 (Anthropic Solutions + OpenAI Deployment Company staffing waves); whether "AI Integration Engineer" merges with FDE title branding.
- 🆕 **Legal-AI unicorn (Norm Ai $1.2B):** new thread — first "regulation-native vertical agent" unicorn; watch for a healthcare-compliance equivalent inside 90 days.
- 🆕 **AI-infra funding week (Baseten $1.5B / Together $800M / Prime Intellect $130M / SambaNova $1B / Bespoke $40M):** new thread — is "bring-your-own-agent-infra" now a distinct layer?
- 🆕 **MCP 2026-07-28 stateless RC:** new thread — read before you ship any MCP server; stateless kills the last exotic-infra requirement.
- ➡️ **Anthropic Agent SDK metering (June 15):** T+25 days — feed cost data from Sonnet-5 default + subagent routing into a monthly bill audit; the June-15 change is now billable reality.
- ➡️ **Claude Code share of GitHub commits:** watch SemiAnalysis for the July print — did Sonnet-5-default push it past 5%?

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + GPT-5.6 + Grok 4.5 in [`01` §1–2](./01-big-lab-moves.md) |
| 20 min | [`04` §1](./04-research-progress.md#1-j-lens) (J-lens/Global Workspace) + [`03` §1–3](./03-practical-skills-and-tools.md) (Sonnet-5 default + Willison routing + MCP RC) |
| Today | [`05` §1](./05-career-and-startup.md#1-fde-surge) — apply to 2 FDE roles |
| Tonight | [`03` §1](./03-practical-skills-and-tools.md#1-sonnet5-default) — update Claude Code, add `model:` override, run one long-ctx task |
| Weekend | Ship an MCP server built to the **2026-07-28 stateless RC** — [`03` §3](./03-practical-skills-and-tools.md#3-mcp-rc) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
