# TL;DR — 2026-06-30 (Tuesday)

Sixty-second skim, **with a 39-day gap-recovery preface** because this archive last published on 2026-05-22.

**One paragraph for the gap:** Since May 22, the two threads that bent the whole year are: (1) **Anthropic raised $65B at $965B post (Series H, May 28)** — now the most valuable AI startup, ahead of OpenAI's $852B — and **shipped the Mythos-class tier (Fable 5 + Mythos 5, June 9)**, the first model architecture above Opus 4.8. (2) **The US government temporarily blocked Mythos 5 + Fable 5 under export-control rules (June 12)**, then **cleared Mythos 5 back to ~100 vetted US critical-infrastructure orgs on June 27** — Fable 5 remains restricted. The IPO thread inverted with it: **OpenAI is now leaning toward a 2027 listing** (NYT, June 26), reversing the May-22 "Sept 2026" framing. Everything else in this edition is downstream of those three facts.

---

**Today's headline:** **The frontier is now released by the U.S. government, not by the labs.** Commerce Secretary Howard Lutnick's June 27 letter — a **bilateral, per-organization clearance** of Mythos 5 to a named list of ~100 institutions — is the **operating precedent** for how the next model tier ships. OpenAI's GPT-5.6 (Sol/Terra/Luna, June 26) launched into the *same* regime: limited preview at the U.S. government's request, partner list shared with the government. **The pre-deployment-evaluation lane I flagged in May is no longer hypothetical — it's the binding constraint on frontier release.**

---

1. **Mythos 5 cleared by U.S. for ~100 critical-infra orgs; Fable 5 stays restricted (June 27).** Two weeks of daily Commerce-Anthropic talks; "no export license required" for the named partners; Fortune/Bloomberg/Axios/Forbes all confirm. The precedent: **per-organization, written clearance** is now the gate for the strongest models. → [`01` §1](./01-big-lab-moves.md#1-mythos-cleared) `#anthropic #policy #export-controls #mythos`

2. **OpenAI's GPT-5.6 (Sol / Terra / Luna) — limited preview at U.S. gov request (June 26).** Sol $5/$30 per 1M (matches GPT-5.5 flagship), Terra $2.50/$15 (~2× cheaper than 5.5), Luna $1/$6 (budget tier). **"Trusted partners only, list shared with the government."** GA "in the coming weeks." Same release-by-Washington pattern as Mythos. → [`01` §2](./01-big-lab-moves.md#2-gpt56) `#openai #gpt-5-6 #release-regime`

3. **OpenAI IPO target slipped from Sept 2026 → 2027 (NYT, June 26).** Reversal of the May-22 Sept-IPO thread. Reported drivers: post-SpaceX market cool-down, "things easier as a private company," confidential S-1 still on file from June 8. **Anthropic's October path now in doubt by association.** → [`01` §3](./01-big-lab-moves.md#3-openai-ipo-slips) `#openai #ipo #public-markets`

4. **Anthropic Series H closed: $65B at $965B post (May 28); ARR through $47B.** Altimeter/Dragoneer/Greenoaks/Sequoia lead; passes OpenAI's $852B. **One-of-a-handful Series H** (Facebook, Lyft, Discord, Slack). Re-rate from $380B Series G (Feb 2026) → $965B (May 2026) is among the steepest private re-ratings ever. → [`02` §1](./02-new-emerging.md#1-anthropic-h) `#anthropic #funding #ipo-prep`

5. **Claude in Microsoft Foundry on Azure — GA (June 2026).** Opus 4.8 + Haiku 4.5 in the Azure Messages API with native identity/billing/governance + optional US data-zone. **Anthropic now ships on all 3 hyperscalers + Azure-native.** Microsoft is *literally selling its competitor's product.* → [`01` §4](./01-big-lab-moves.md#4-claude-foundry) `#anthropic #microsoft #azure #distribution`

6. **Practical: the 6-primitive Claude Code stack (CLAUDE.md · skills · subagents · slash commands · hooks · MCP).** Marktechpost's June-14 guide canonicalized the stack; the field has converged. **Tonight's 30-min install** = start 4–8 MCP servers, narrowest-credential each, stdio for local + http for remote. → [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-stack) `#claude-code #mcp #skills #subagents`

7. **Research: "Efficient Benchmarking of AI Agents" (arXiv 2603.23749) cuts agent-eval cost 44–70% with no rank loss** — evaluate only on tasks with 30–70% historical pass rates. **Direct interview-portfolio leverage:** lets you ship credible agent comparisons on a student budget. Pair with **Holistic Agent Leaderboard** (arXiv 2510.11977) for the public framing. → [`04` §1](./04-research-progress.md#1-efficient-eval) `#arxiv #benchmarks #agents #cost`

8. **Career re-price:** AI Engineer postings **+109% YoY** (LinkedIn 2026); **FDE postings +800%, $450K+ TC**; LLM specialists **$220–280K, demand +135.8%**; AI-skills wage premium **25% → 56% in 12 months** (PwC). **"Hired on delivery evidence — repos, deployed agents, eval suites — not credentials."** The portfolio gap closed in your favor. → [`05` §1](./05-career-and-startup.md#1-market-reprice) `#jobs #fde #mle #ai-engineer`

---

## One thing to DO this Tuesday

→ **Set up the 6-primitive Claude Code stack on one repo TONIGHT** (45 min) — `CLAUDE.md` + 1 skill + 1 subagent + 1 slash command + 1 hook + 4 MCP servers. See [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-stack). Take screenshots of the working stack. **This becomes the single most-credible interview artifact you can produce in one evening**, because it touches every primitive a Claude FDE/Integration role asks about. **Also: apply to one Anthropic Mission Programs / Solutions role this week** — the Mythos-5-clearance event creates a critical-infrastructure-deployment hiring surge that will be visible by mid-July ([`05` §3](./05-career-and-startup.md#3-mission-programs)).

## Gap-recovery — what changed since 2026-05-22

| Thread | May 22 status | June 30 status |
|---|---|---|
| **Anthropic raise** | "$30–50B at ~$950B imminent" | **CLOSED May 28: $65B at $965B Series H** (Altimeter/Dragoneer/Greenoaks/Sequoia) |
| **OpenAI IPO** | "Confidential S-1, Sept 2026, $852B–$1T" | **S-1 confirmed June 8; target slipped to 2027** (NYT June 26) |
| **Anthropic IPO** | "October 2026 target" | **Confidentially submitted draft S-1**; no public date |
| **Anthropic ARR** | $44B (May 8 investor meeting) | **$47B run-rate** (May 28 disclosure) |
| **Mythos** | Restricted at launch | **Blocked June 12 (export control) → cleared June 27 to ~100 vetted US orgs** |
| **Next Anthropic model** | No leak | **Fable 5 + Mythos 5 launched June 9** (Mythos-class tier above Opus 4.8); **Opus 4.8 + Haiku 4.5 GA in Microsoft Foundry** |
| **Next OpenAI model** | No leak | **GPT-5.5 shipped early-June; GPT-5.6 Sol/Terra/Luna limited preview June 26** |
| **ChatGPT Ads** | Self-serve Ads Manager live | **$100M annualized in pilot** (announced at Cannes Lions); Anthropic ad-free pledge holds |
| **Trump AI EO** | Postponed | **Still unsigned**; the *case-by-case clearance* model is what's actually being used |
| **Karpathy → Anthropic** | Announced, just started | Quiet through June; team output still pending |

## Watchlist deltas (the high-frequency cut)

- 🆕 **Mythos 5 critical-infra clearance regime** — track which 100 orgs got named (energy, defense, finance, telco); each is a hiring surface
- 🆕 **GPT-5.6 limited-preview list** — first leaked partner names will reveal OpenAI's enterprise pecking order
- 🆕 **OpenAI Jalapeño chip (Broadcom, June 24)** — vertical-integration play; track first volume-deploy date
- 🆕 **Anthropic–Google–Broadcom multi-GW compute partnership** — pairs with the Colossus contract; total Anthropic compute commitment now >$60B over 4 yrs
- 🆕 **Alphabet $80B fundraise for AI compute** ($30B Class A/C + $10B Berkshire + $40B ATM) — public-market vote of confidence in capex thesis
- 🆕 **OpenAI 2027 IPO timeline** — reversal of the Sept-2026 thread; Anthropic October path now soft
- 🔻 **OpenAI Sept 2026 IPO** — superseded
- ➡️ **Anthropic Agent SDK metering (June 15)** — went live; the cost-routing skill is now table stakes
- ➡️ **Real-tool agent benchmarks (MCP-Atlas, Toolathlon)** — joined by **Efficient Benchmarking** (arXiv 2603.23749) and **Holistic Agent Leaderboard** (arXiv 2510.11977)

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the Mythos-5-clearance precedent in [`01` §1](./01-big-lab-moves.md#1-mythos-cleared) |
| 20 min | [`01` §1–2](./01-big-lab-moves.md) (the release-by-Washington regime) + [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-stack) (the 6-primitive stack) |
| Tonight | [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-stack) — 45 min install + screenshots |
| This week | [`05` §3](./05-career-and-startup.md#3-mission-programs) — 1 Anthropic Mission Programs application before the mid-July clearance-deployment hiring wave |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.

**Operational note on the gap:** A 39-day publishing gap means individual-day-of-the-week threads (Tuesday I/O monitoring, Thursday Meta-alumni outreach, etc.) cannot be retroactively reconstructed. This edition resumes the cadence from today; `ACTIONS.md` is reset to the week of 2026-06-30, and the May-week tasks are archived in place.
