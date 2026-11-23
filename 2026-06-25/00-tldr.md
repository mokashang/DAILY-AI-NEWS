# TL;DR — 2026-06-25 (Thursday)

**30-second read:** Anthropic just made the **distillation war public** (Alibaba: 28.8M Claude queries via ~25K fake accounts, the largest known attempt), Google is **bleeding senior AI talent** to Anthropic and OpenAI (four senior departures in six days; ~$225B wiped off Alphabet), and **Claude Opus 4.8 + Claude Tag** put a multiplayer agent inside Slack. Underneath, **EU AI Act enforcement is T-38 days**, **SpaceX bought Cursor for $60B**, and the **AI Engineer job market** is louder than ever — but only **2.5% of postings target 0–2 years of experience.**

Sixty-second skim. The labs aren't just competing on models anymore — they're competing on **who gets the talent, who owns the agent surface, and who can keep their weights from being copied.** For you: the **Anthropic-stack focusing decision keeps paying off** (talent + Slack-as-distribution + Opus 4.8), the **entry-level mismatch** is a real number you should plan around (2.5%), and the **distillation story is the cleanest "frontier IP is now a security problem"** framing you'll see this year — write about it.

---

1. **Anthropic accuses Alibaba of the largest known distillation attack — and tells the White House.** Apr 22 → Jun 5, 2026: **28.8M exchanges via ~25K fraudulent accounts**, targeting Claude's **software-engineering and agentic-reasoning** capabilities. Letter explicitly notes Alibaba "ignored the Trump Administration's warnings." Follows February's three "industrial-scale" campaigns (DeepSeek, Moonshot, MiniMax). → [`01` §1](./01-big-lab-moves.md#1-alibaba-distillation) `#anthropic #china #ip #policy #security`

2. **Google's AI talent exodus — four senior departures in six days.** Today: **Jonas Adler (Gemini AI coding) + Alexander Pritzel (Gemini training)** to Anthropic. This week also: **Nobel laureate John Jumper** to Anthropic, **Noam Shazeer** to OpenAI. Alphabet **down ~5% on the day = ~$225B in market cap.** Bankers cite the **pre-IPO equity payday** at OpenAI/Anthropic. → [`01` §2](./01-big-lab-moves.md#2-google-exodus) `#google #anthropic #openai #talent`

3. **Claude Opus 4.8 + Claude Tag for Slack ship.** Opus 4.8 lands as the new flagship; **Claude Tag** is a *team-shared* agent inside Slack (one Claude per channel, multiplayer context, ambient proactive updates, async task handoff). **65% of Anthropic's own product-team code is written by their internal Claude Tag** (per Anthropic) — the loudest dogfood number of 2026. → [`01` §3](./01-big-lab-moves.md#3-claude-tag) · [`03` §1](./03-practical-skills-and-tools.md#1-claude-tag) `#anthropic #opus #slack #agents`

4. **SpaceX → Cursor: $60B all-stock — largest VC-backed acquisition ever.** Closed Jun 16, days after SpaceX's IPO. Cursor was at **~$4B ARR (~$2.6B enterprise), ~⅔ of the Fortune 500** as customers. Hoffman's framing today: SpaceX/xAI is **"the IAC of AI" — buying relevance, not building it.** All 11 original xAI co-founders have departed. → [`02` §1](./02-new-emerging.md#1-spacex-cursor) `#spacex #cursor #m-and-a #xai`

5. **Funding cluster (Jun 24): two $100M+ rounds.** **Assort Health $120M Series C @ $1.2B** (Menlo lead) — voice AI for the patient journey, 190M patient interactions, 20× revenue in 15 mo. **Taktile $110M Series C** (Goldman Sachs Alternatives lead) — AI decisioning for **regulated** banking/insurance workflows (underwriting, fraud, AML, claims). Plus **Flourish $500M @ $2.5B** (Jun 4; Bezos $100M, Lux, GV) — **brain-inspired AI at 20–50W** vs gigawatts. → [`02` §2-3](./02-new-emerging.md#2-assort) `#funding #healthcare #fintech #neuromorphic`

6. **Practical: Anthropic shipped the *defensive* primitives this week.** Claude Code added **sandbox credential blocking, org model restrictions, structured output, remote MCP, session-resume fixes.** Read it as "use this *before* anyone tries the same trick on your stack." Combined with the **MCP server hygiene checklist** (≤40 active tools, narrow credentials, `CLAUDE.md ≤200 lines`, `.claude/rules/*.md`), this is your tonight setup. → [`03` §2](./03-practical-skills-and-tools.md#2-claude-code-defense) `#claude-code #mcp #security #productivity`

7. **Research: cost-aware orchestration is now its own arXiv lane.** **"Utility-Guided Agent Orchestration" (2603.19896)** picks among `respond/retrieve/tool_call/verify/stop` by balancing gain · cost · uncertainty · redundancy. **"Cost-Aware Model Orchestration" (2512.01099)** reports **~54% energy efficiency** improvement. **"Agents of Chaos" (2602.20021)** + **"Characterizing faults in agentic AI" (2603.06847)** define the failure-mode vocabulary. The skill is **routing**, and the literature finally has the names. → [`04` §1](./04-research-progress.md#1-cost-orchestration) `#arxiv #orchestration #cost #benchmarks`

8. **Career read of the week:** AI Engineer is the **#1 fastest-growing US job (+143% YoY, ~$206K avg, ~8,931 open postings @ ~$228K)** — **but only 2.5% are 0–2 yrs**. Recent-grad unemployment **5.7%, underemployment 43%, entry-level postings −35% since 2023.** The lane that's actually open: **AI Integration Engineer / FDE / Solutions** at frontier labs and at services firms hiring around Claude — keep your ME.md focusing decision. → [`05` §1](./05-career-and-startup.md#1-market) `#jobs #careers #fde #entry-level`

---

## One thing to DO this Thursday

→ **Spin up Claude Tag in a Slack workspace you control, then write the "internal Slack agent" comparison post** — pit Claude Tag (multiplayer, ambient) vs OpenAI's ChatGPT-for-work vs the build-it-yourself MCP route. Cite the **65% internal-code number** as the proof Anthropic uses on itself ([`03` §1](./03-practical-skills-and-tools.md#1-claude-tag)). One artifact = three interview answers: distribution-channel thinking, agent UX, and cost-aware routing. Also: **apply to two Solutions/FDE roles before the weekend** — the talent exodus from Google + the IPO-window comp at OpenAI/Anthropic means roles are repricing live.

## Watchlist deltas (since 2026-05-22 — 34-day gap)

- 🆕 **Anthropic vs Alibaba distillation:** new top-of-stack thread. Watch for (a) Trump admin response, (b) export-control follow-on, (c) Qwen successor model release timing.
- 🆕 **Google talent crisis:** new thread. Track who else leaves; whether GDM splits/restructures; whether Alphabet announces a counter-package.
- 🆕 **Claude Opus 4.8 + Claude Tag GA:** new thread. Track Enterprise/Team uptake, the "65% internal code" number's external corroboration, and whether OpenAI ships a Slack-native equivalent.
- ➡️ **OpenAI S-1 / IPO path** (from 2026-05-22): IPO chatter still live; **SpaceX listed June 12**, **Cursor acquired June 16** — public-market repricing is happening on schedule.
- 🔻 **Anthropic Fable 5 / Mythos 5:** **export-controlled June 11–13** (Jassy/Amazon call → Lutnick letter). Status 🟡-stalled internationally. **Watch the unwind path** — and what it does to Anthropic's revenue mix for the IPO.
- ➡️ **EU AI Act enforcement:** **T-38 days (Aug 2, 2026)** — €15M or 3% global turnover penalties activate; pre-deployment-eval/AI-assurance lane is *firming up* on the EU side even as the US EO sits postponed.
- ➡️ **Karpathy → Anthropic pre-training team** (from 2026-05-22): no public output yet; watch for the first "Claude trained Claude" announcement.
- ➡️ **Anthropic Agent SDK metering** (from 2026-05-16): in effect since June 15; combine with the orchestration arXiv lane below for tonight's setup.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. |
| 5 min | This file + the Alibaba distillation story in [`01` §1](./01-big-lab-moves.md#1-alibaba-distillation) |
| 20 min | [`01` §2](./01-big-lab-moves.md#2-google-exodus) (Google exodus) + [`03` §1](./03-practical-skills-and-tools.md#1-claude-tag) (Claude Tag setup) — the two with the highest career leverage |
| Tonight | [`03` §2](./03-practical-skills-and-tools.md#2-claude-code-defense) — turn on sandbox credential blocking + write your `.claude/rules/*.md` |
| This weekend | [`05` §3](./05-career-and-startup.md#3-action) — ship the Slack-agent comparison post + 2 FDE/Solutions applications |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
