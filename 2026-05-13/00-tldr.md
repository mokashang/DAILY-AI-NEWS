# TL;DR — 2026-05-13

Sixty-second skim. Read in order; jump to the deep file if a bullet grabs you.

---

1. **Anthropic launches "Claude for Legal" — 12 practice-area plugins + 20+ MCP connectors** — Commercial, Employment, Litigation, M&A, IP, Privacy, AI Governance, Regulatory, plus Box / DocuSign / Ironclad / iManage / NetDocuments / LexisNexis / Thomson Reuters / Everlaw. Thomson Reuters CoCounsel Legal is now **rebuilt on Claude Agent SDK** (bidirectional: CoCounsel calls Claude, Claude calls CoCounsel as a tool). First time Anthropic has gone vertical with this level of integration breadth. → [`01-big-lab-moves.md`](./01-big-lab-moves.md#1-claude-for-legal) `#anthropic #legal #mcp #vertical`
2. **Google Threat Intel: first AI-built zero-day caught in the wild** — Hacker group used an LLM to discover + weaponize a 2FA-bypass zero-day for a mass-exploitation campaign against a sysadmin tool. Google says its proactive discovery prevented the event. Vindicates Anthropic's Mythos caution; **Google explicitly said it was not Gemini**. → [`01-big-lab-moves.md`](./01-big-lab-moves.md#2-google-ai-zero-day) `#security #policy #mythos`
3. **Meta delays Avocado (next flagship LLM) + closed-source pivot confirmed** — Avocado (world-model reasoning text LLM, the de-facto Llama 5) slips again; Mango (image/video) on similar schedule. Zuckerberg confirmed Superintelligence-class models will *not* ship open-source. End of an era for Meta's open-weights leadership. → [`01-big-lab-moves.md`](./01-big-lab-moves.md#3-meta-avocado-delay) `#meta #open-source #strategy`
4. **Wispr Flow in talks to raise $260M at ~$2B valuation** — Bloomberg confirms Menlo Ventures-led; ~3× from last round (Nov 2025 at $700M). Voice AI moving past dictation — Wispr is now positioning as "Voice OS". 2.5M downloads, hundreds of enterprise orgs. → [`02-new-emerging.md`](./02-new-emerging.md#1-wispr-2b) `#voice #funding #consumer-ai`
5. **Judgment Labs closes $32M Seed + Series A** — Lightspeed Venture Partners doubles down inside 6 months. Three 22–23 yo cofounders. Solving the "evaluation for deep agents" problem (long trajectories, tool use, memory). Direct competitor lane to Braintrust + LangSmith. → [`02-new-emerging.md`](./02-new-emerging.md#2-judgment-labs) `#agents #eval #seed`
6. **"Towards a Science of AI Agent Reliability" published (arXiv 2602.16666)** — 12 concrete metrics across consistency / robustness / predictability / safety. The headline finding: **18 months of capability progress, almost zero reliability progress**. Required reading if you're shipping agents. → [`04-research-progress.md`](./04-research-progress.md#1-agent-reliability) `#research #agents #reliability`
7. **Q1 2026 tech layoffs: 78,557 cuts, 47.9% AI-attributed** — Tom's Hardware reporting. GM cut hundreds of IT roles this week to re-hire AI-skilled engineers. **Meta's 8,000-person May 20 cut is one week away.** Atlassian: cutting in QA/content/PM, hiring 800 in AI engineering. → [`05-career-and-startup.md`](./05-career-and-startup.md#1-q1-layoffs) `#jobs #layoffs #ai-displacement`
8. **Cursor confirmed at ~$2B annualized revenue** — and Claude Code Skills + Subagents are the two highest-leverage workflows for new MLE/SWE candidates in 2026. Concrete weekend project recipe below. → [`03-practical-skills-and-tools.md`](./03-practical-skills-and-tools.md#1-cursor-2b) `#cursor #claude-code #skills #subagents`

---

## One thing to DO this week

→ **Ship a vertical MCP server + Claude Skill in 48 hours**, modeled on the "Claude for Legal" playbook. Pick a domain you actually know (your school's course catalog, your campus job board, a public-records dataset, your bank's CSV exports). Publish on GitHub with: (a) MCP connector code, (b) one Skill file, (c) a 60-second demo video. This is the *exact pattern* Anthropic just legitimized at the vertical-application layer, and any employer hiring "AI integration engineers" can grade your repo in 5 minutes. Cost: a weekend. Compounding return: this becomes your interview portfolio asset for the next 12 months.

## Watchlist deltas

- 🆕 **Claude for Legal:** new thread — first major Anthropic vertical with deep partner integration. Watch which other industries (healthcare, finance, defense) get the same playbook next
- 🆕 **AI-built zero-day in the wild:** new thread — the Mythos-caution debate is now post-theoretical; real exploits are happening
- ⬆️ **Wispr / Voice OS:** valuation 3× in 6 months; voice is the next platform category
- ⬆️ **Q1 layoff data finalized:** 78,557 / 47.9% AI-attributed (was 52,050 in earlier May 12 reporting — revised up)
- ⬆️ **Meta open-source pivot:** confirmed at C-suite level for superintelligence-class models
- ⬇️ **Llama 5 / Avocado timing:** delayed yet again; Q2 2026 launch now in question
- ⬇️ **Anthropic $50B raise:** still no term sheet — board decision was "expected this week" per yesterday's TechCrunch, now slipping toward late May

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + `01-big-lab-moves.md` first two stories |
| 20 min | Pick one of the 5 category files and read deep |
| Weekend | `03-practical-skills-and-tools.md` action + WATCHLIST refresh |

Source-confidence legend used throughout today's files: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[rumor]` leaked / unconfirmed.
