# TL;DR — 2026-07-06 (Monday)

Sixty-second skim. **The frontier just came back online — with new rules.** Over the past 96 hours: **Claude Fable 5 and Mythos 5 came back from an 18-day export-control blackout** (Commerce lifted the June 12 order on June 30; Anthropic globally redeployed Fable 5 July 1 with a **new Cybersecurity Classifier + a HackerOne jailbreak-bounty program + a draft "AI jailbreak severity" framework** — a template for how future covered-model shutdowns will end). Same week: **Claude Science shipped** (a vertical Claude for pharma/labs with 60+ scientific tools; Anthropic is standing up its own preclinical drug-discovery arm for neglected diseases). **Anthropic began actively closing the Chinese-access loopholes** (Ant Group, ByteDance, transfer-station relays — 25K accounts / 28.8M exchanges detected Apr–Jun). And the IPO wave is now real: **Anthropic's confidential S-1 was filed June 1 at ~$965B**; **OpenAI's S-1 followed within a week at ~$852B**; both target **fall 2026 listings**. For you: the **model-release process is now the product**, the **vertical Claude template is your founder template**, and **~$47B → $50B ARR by end of July** is the number to remember before your next Anthropic interview.

---

1. **Claude Fable 5 REDEPLOYED globally (July 1) after US export controls lift (June 30).** Anthropic paired the return with a **Cybersecurity Classifier** (blocks vulnerability-generation abuse patterns identified in the Amazon research), a **HackerOne bug-bounty program for cyber jailbreaks**, and a **draft AI jailbreak severity framework**. Mythos 5 restored to select US orgs after June 26 approval, expanding via the Glasswing program. For Pro/Max/Team/Enterprise, Fable 5 is included up to 50% of weekly limits through July 7, then usage credits after. → [`01` §1](./01-big-lab-moves.md#1-fable-5-return) `#anthropic #policy #cybersecurity #jailbreak-severity`

2. **Claude Science shipped (June 30) — Anthropic goes vertical + starts own drug discovery.** New product for computational biology / drug development with 60+ preconfigured scientific tools + databases; can autonomously plan+run screening workflows (launch demo: 2,200 compounds screened for a PKU enzyme-stabilizer across 80 GPUs → four candidates + go/no-go memo). Anthropic simultaneously announced **in-house preclinical drug-discovery programs for neglected diseases** — "to build the right models we need to live it." → [`01` §2](./01-big-lab-moves.md#2-claude-science) `#anthropic #vertical #biotech #agents`

3. **Anthropic closes Chinese-access loopholes (July 3).** Extended rules now target **ownership structures + transfer-station relays** (Ant Group via a Singapore subsidiary; ByteDance reimbursing personal Claude subs on VPN; hundreds of relay stations reselling access with WeChat/Alipay payment). Behavioral fingerprinting (timezones + usage patterns) + government-ID/live-selfie verification for flagged accounts. Anthropic detected **~25,000 fraudulent accounts / 28.8M exchanges (Apr–Jun)** attributed to Alibaba-linked entities as "the largest distillation campaign in its history." → [`01` §3](./01-big-lab-moves.md#3-china-loopholes) `#anthropic #geopolitics #distillation #trust-safety`

4. **OpenAI GPT-5.6 preview (Sol / Terra / Luna).** Sol = new flagship, **SOTA on Terminal-Bench 2.1**; Terra = GPT-5.5-competitive at ~½ cost; Luna = fastest+cheapest. Limited API/Codex preview to trusted partners; ChatGPT Business gets a new model picker (Instant/Medium/High/Extra High/Pro Standard/Pro Extended). **OpenAI S-1 filed within a week of Anthropic's**, ~$852B, timing "still TBD." → [`01` §4](./01-big-lab-moves.md#4-gpt-56) · [`01` §5](./01-big-lab-moves.md#5-ipo-wave) `#openai #model-picker #ipo`

5. **The IPO wave is real — Anthropic's $965B S-1 (June 1) + OpenAI's $852B S-1 (~June 8) both target fall 2026.** Anthropic's **~$47B run-rate May → ~$50B end of July**; projects positive FCF by 2027 (3 yrs ahead of OpenAI's 2030 breakeven target). Two S-1s inside a week = frontier is now a public-market asset class. → [`01` §5](./01-big-lab-moves.md#5-ipo-wave) · [`02` §1](./02-new-emerging.md#1-ipo-wave-effects) `#ipo #public-markets #liquidity`

6. **Gemini 3.5 Flash GA + DeepMind's Contextual-AI acqui-hire.** Flash beats **Gemini 3.1 Pro** on Terminal-Bench 2.1 (76.2%), MCP-Atlas (83.6%), GDPval-AA (1656 Elo), CharXiv (84.2%); 1M-ctx; **AI Ultra cut $250 → $200/mo**. DeepMind licensed **20+ Contextual AI researchers for $80–90M** — the acqui-hire template continues. **Deep Research Max** (autonomous research agent) rolled out. → [`01` §6](./01-big-lab-moves.md#6-gemini-flash) · [`03` §5](./03-practical-skills-and-tools.md#5-deep-research-max) `#google #gemini #deepmind #benchmarks`

7. **New funding wave: Together AI $800M / $8.3B (Aramco Ventures lead), Shield AI $1.5B (part of $2.25B pkg, $12.7B, +140% YoY), AI2 Robotics $735M / ~$3B (Shenzhen wheeled humanoids), Venice $65M / $1B (Dragonfly; private surveillance-free AI).** **Global VC hit a record $510B in H1 2026 — OpenAI + Anthropic captured 43% alone**; **~88% of AI funding went to US-HQ'd cos.** → [`02` §2–5](./02-new-emerging.md#2-together-ai) `#funding #open-source-infra #defense #robotics #privacy`

8. **Meta Compute + xAI Voice Agent Builder — the compute market is refactoring.** Meta pivots to **renting excess compute** (Meta Compute business line under Santosh Janardhan + Daniel Gross + Dina Powell McCormick), same play as SpaceX/xAI selling capacity — while its own frontier model still lags. xAI launches **Voice Agent Builder** (no-code Grok Voice: telephony + retrieval + tools + MCP + voice cloning + SIP + observability). **Grok 5 not shipping Q3** (Polymarket closed at 3%). → [`01` §7](./01-big-lab-moves.md#7-meta-xai) · [`03` §4](./03-practical-skills-and-tools.md#4-voice-agent-builder) `#meta #xai #compute-market #voice-agents`

---

## One thing to DO this Monday

→ **Publish a one-page "Claude Fable 5 return: what changed and how I'd use it"** — treat the **Cybersecurity Classifier + HackerOne bounty + jailbreak severity framework** as a case study. It maps 1:1 to the pre-deployment-eval / AI-assurance lane you've been tracking since [2026-05-21](../2026-05-21/05-career-and-startup.md#3-eo-lane), gives you concrete vocabulary (severity taxonomy, classifier vs guardrail vs policy), and demonstrates that you read past the reversal-of-a-reversal headline. Post to LinkedIn + link from a repo README. Meanwhile, **apply this week to 2 pharma-AI / life-sciences FDE-style roles** — Claude Science just opened a category ([`05` §3](./05-career-and-startup.md#3-pharma-ai-lane)).

## Watchlist deltas

- 🆕 **Claude Fable 5 / Mythos 5 redeployment (July 1)** — the **Cybersecurity Classifier + HackerOne cyber-jailbreak bounty + severity framework** are the new artifacts to track. Status flips 🔴→🟢. This is the *template* for how future export-controlled model returns will look.
- 🆕 **Claude Science + Anthropic in-house drug discovery** — new vertical + Anthropic-as-drug-company thread. Watch for Novartis/Lilly/J&J integration announcements and the first Anthropic-authored preclinical paper.
- 🆕 **Anthropic China-access enforcement (July 3)** — 25K fake accounts / 28.8M exchanges attributed to Alibaba entities. Watch for retaliation via cutting off Anthropic's China distillation dependence + any Ant Group public response.
- 🆕 **OpenAI GPT-5.6 Sol / Terra / Luna preview** — closed API/Codex partners only. Track expansion to GA + Terminal-Bench 2.1 top-of-leaderboard fight.
- ➡️ **Anthropic S-1 ($965B, June 1) + OpenAI S-1 (~$852B, ~June 8)** — both targeting fall listings. Track roadshow windows + public financial disclosures.
- ➡️ **Karpathy @ Anthropic pre-training team (May 19 start)** — no shipping signal yet; still the loudest talent read. Watch for the first "Claude-accelerates-Claude" methodology post.
- ➡️ **Anthropic Agent SDK June 15 metering** — now 3 weeks in-market. Track the Q3 API spend patterns to see if predictions held.
- ⬇️ **Trump AI executive order** — still postponed (was signing "as soon as May 21"); the pre-deployment-eval draft survives but the timing has slipped past the summer.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Fable 5 return + Claude Science in [`01` §1–2](./01-big-lab-moves.md) |
| 20 min | [`01` §3](./01-big-lab-moves.md#3-china-loopholes) (China enforcement — the geopolitics of distillation) + [`04` §1](./04-research-progress.md#1-mcp-bench) (MCP-Bench + Toolathlon as the new eval bar) |
| Today | [`05` §1](./05-career-and-startup.md#1-class-of-2026) — read the class-of-2026 hiring numbers (+5.6% YoY, AI Engineer #1 fastest-growing) |
| Tonight | [`03` §2](./03-practical-skills-and-tools.md#2-model-routing) — refactor your project's model router around GPT-5.6 Terra + Sonnet 5 promo + Gemini 3.5 Flash |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
