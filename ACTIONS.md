# Actions — Personal Task Tracker

Pulled out of WATCHLIST.md so that "what am I supposed to do this week" lives in one scannable file. Cleared and refreshed weekly. Add new actions as daily editions accumulate them.

Status legend: ⚪ open · 🟡 in progress · 🟢 done · 🔴 dropped (with reason)

Last updated: **2026-06-16**

---

## This week (June 16 – June 22) — POST-METERING WEEK

### Tuesday June 16 — the day after metering went live

| Status | Action | Due | Source |
|---|---|---|---|
| ⚪ | **Run `/billing` audit + Agent SDK separate-pool dashboard; log 7-day per-task token-cost table** | Today | [2026-06-16/00 One Thing](./2026-06-16/00-tldr.md) · [2026-06-16/03 §1](./2026-06-16/03-practical-skills-and-tools.md#1-meter-aware-starter) |
| ⚪ | **Publish LinkedIn post: "What I changed June 15 — the 3 settings I flipped"** (date-stamps everything else this week) | Today | [2026-06-16/00 One Thing](./2026-06-16/00-tldr.md) · [2026-06-16/05 §5](./2026-06-16/05-career-and-startup.md#5-this-week) |
| ⚪ | **Audit prod code for `claude-sonnet-4-20250514` / `claude-opus-4-20250514` pinned IDs** — those retired yesterday; silently broken if still pinned | Today | [2026-06-16/03 §1.1](./2026-06-16/03-practical-skills-and-tools.md#1-meter-aware-starter) |
| ⚪ | **Update LinkedIn skills to FDE JD vocabulary**: LangGraph, LangChain, CrewAI, DSPy, multi-step tool-use chains, evaluation frameworks at deployment scale | Today | [2026-06-16/05 §1](./2026-06-16/05-career-and-startup.md#1-fde-tc) |

### Wednesday June 17 — the 3 hyperscaler-Claude applications + 1 Anthropic

| Status | Action | Due | Source |
|---|---|---|---|
| ⚪ | **Apply: AWS Bedrock Solutions Architect — Claude** (same artifacts across all 3) | Wed | [2026-06-16/05 §2](./2026-06-16/05-career-and-startup.md#2-three-roles) |
| ⚪ | **Apply: Google Vertex AI Customer Engineer — Claude** | Wed | [2026-06-16/05 §2](./2026-06-16/05-career-and-startup.md#2-three-roles) |
| ⚪ | **Apply: Microsoft Foundry Partner Engineer — Claude** | Wed | [2026-06-16/05 §2](./2026-06-16/05-career-and-startup.md#2-three-roles) |
| ⚪ | **Apply: 1 Anthropic Solutions / FDE / Integration role** — reference Fable 5 + meter-aware starter kit explicitly; cite $665K–$750K band in the conversation | Wed | [2026-06-16/05 §1](./2026-06-16/05-career-and-startup.md#1-fde-tc) |
| ⚪ | Deploy **Opus-orchestrator / Sonnet-worker split** on highest-volume project; add Fable 5 to orchestrator slot for long-task projects | Wed | [2026-06-16/03 §1.4](./2026-06-16/03-practical-skills-and-tools.md#1-meter-aware-starter) |
| ⚪ | Enable prompt caching on every project >5K input tokens; verify `cache_read_input_tokens > 0` | Wed | [2026-06-16/03 §1.3](./2026-06-16/03-practical-skills-and-tools.md#1-meter-aware-starter) |
| ⚪ | Add **Gemini 3.5 Flash cheap-leg** to 3-provider router | Wed | [2026-06-16/03 §4](./2026-06-16/03-practical-skills-and-tools.md#4-flash-leg) |

### Thursday June 18 — research reading day

| Status | Action | Due | Source |
|---|---|---|---|
| ⚪ | **Read "A Survey on Evaluation of LLM-based Agents" (arXiv 2503.16416)** end-to-end — trace-eval framing for FDE interviews | Thu | [2026-06-16/04 §1](./2026-06-16/04-research-progress.md#1-trace-eval) |
| ⚪ | **Read the Agentic Reasoning survey + curated list** — 3-layer taxonomy (foundational/self-evolving/collective) | Thu | [2026-06-16/04 §2](./2026-06-16/04-research-progress.md#2-agentic-reasoning) |
| ⚪ | Read AgentLAB (arXiv 2602.16901) for the long-horizon-adversarial primitive | Thu | [2026-06-16/04 §1](./2026-06-16/04-research-progress.md#1-trace-eval) |

### Friday June 19 — under-applied lanes day

| Status | Action | Due | Source |
|---|---|---|---|
| ⚪ | **Apply: NewCore (agent-identity, Tel Aviv + remote US)** — Reach Lane | Fri | [2026-06-16/05 §4](./2026-06-16/05-career-and-startup.md#4-soc-and-gpu-lanes) |
| ⚪ | **Apply: Hydra Host (GPU marketplace, Boulder + remote)** — Reach Lane | Fri | [2026-06-16/05 §4](./2026-06-16/05-career-and-startup.md#4-soc-and-gpu-lanes) |
| ⚪ | Subscribe to **AI Funding Tracker daily digest** + add weekly review block | Fri | [2026-06-16/05 §4](./2026-06-16/05-career-and-startup.md#4-soc-and-gpu-lanes) |
| ⚪ | **Ship `agent-trace-judge` GitHub repo** — small Sonnet/Flash-tier model that scores Fable-5 traces step-by-step | Fri | [2026-06-16/04 §1](./2026-06-16/04-research-progress.md#1-trace-eval) |

### Saturday June 20 — the portfolio shovel weekend

| Status | Action | Due | Source |
|---|---|---|---|
| ⚪ | **Build Claude-as-Siri-default iOS 27 Extension demo** (Siri intent → Apple Extension → Claude Agent SDK → mail draft preview, w/ per-step cost trace) | Sat | [2026-06-16/03 §3](./2026-06-16/03-practical-skills-and-tools.md#3-ios-extension-weekend) · [2026-06-16/05 §3](./2026-06-16/05-career-and-startup.md#3-portfolio) |
| ⚪ | Record 15–30 sec screen capture; push repo to GitHub | Sat | [2026-06-16/05 §3](./2026-06-16/05-career-and-startup.md#3-portfolio) |

### Sunday June 21 — distribution day

| Status | Action | Due | Source |
|---|---|---|---|
| ⚪ | **Post iOS Extension write-up** (LinkedIn + Hacker News + X) — title: *"I shipped a Claude Extension for iOS 27 the week of WWDC — here's the playbook"* | Sun | [2026-06-16/05 §3](./2026-06-16/05-career-and-startup.md#3-portfolio) |
| ⚪ | **Warm-DM 3 vertical-SaaS founders** with the Extension demo: *"I built the technical shell; would you co-found the vertical?"* | Sun | [2026-06-16/05 §3](./2026-06-16/05-career-and-startup.md#3-portfolio) |
| ⚪ | Weekly review: write `WEEK-2026-06-15.md` rollup | Sun | (weekly convention) |
| ⚪ | Cleanup ACTIONS.md (archive 🟢, move ⚪ to next week) | Sun | (this file) |

---

## Carried open from prior weeks (review weekly)

| Status | Action | Carried from | Notes |
|---|---|---|---|
| ⚪ | Ship dual-model sanitiser project reframed around real-tool verification + per-step cost | 2026-05-22 | Roll into the meter-aware starter kit deliverable |
| ⚪ | Apply to Anthropic referencing the Karpathy pre-training-automation direction | 2026-05-22 | Covered by Wed June 17 Anthropic application above |
| ⚪ | Add agentic-SOC / AI security operations (Exaforce + category) to apply/watch list | 2026-05-22 | Layer with NewCore + Hydra Host applications Friday |
| ⚪ | Workday × Anthropic Solopreneurship Accelerator application | 2026-05-19 | Application deadline check needed |
| ⚪ | Apply to Isomorphic Labs eng role | 2026-05-18 | Within original 30-day window — getting late |

---

## Archive (recently done — keep for ~30 days)

| Closed | Action | Date |
|---|---|---|
| 🟢 | Pre-stage I/O comparison doc | 2026-05-19 |
| 🟢 | Run 15-min-block I/O live-monitoring | 2026-05-19 |
| 🟢 | Watch Code w/ Claude London slice | 2026-05-19 |
| 🟢 | Toggle Agent SDK credit setting in Claude account | 2026-05-18 → 2026-06-15 deadline hit |

---

## This week (May 19 – May 25) — ARCHIVED below for reference

### Tuesday May 19 — I/O DAY (done)

| Status | Action | Due | Source |
|---|---|---|---|
| 🟢 | Run 15-min-block I/O live-monitoring discipline | Tue | [2026-05-19/03 §1](./2026-05-19/03-practical-skills-and-tools.md#1-io-live-discipline) |
| 🟢 | Publish Gemini-vs-Claude-vs-GPT comparison (real numbers now in [2026-05-20/03 §1](./2026-05-20/03-practical-skills-and-tools.md#1-comparison-table)) | Tue/Wed | [2026-05-20/03 §1](./2026-05-20/03-practical-skills-and-tools.md#1-comparison-table) |
| 🟡 | Update LinkedIn skills — **keyword corrected**: NOT "Vertex AI Agent Platform"; real terms are Antigravity 2.0 / Managed Agents (Gemini API) / WebMCP | Wed | [2026-05-20/01 §1](./2026-05-20/01-big-lab-moves.md#1-io-scorecard) |
| 🟢 | Watch Code w/ Claude London slice | Tue | [2026-05-19/03 §2](./2026-05-19/03-practical-skills-and-tools.md#3-cwc-london-monitoring) |

### Today (Wednesday May 20) — Meta cut executing

| Status | Action | Due | Source |
|---|---|---|---|
| ⚪ | **Publish the GRADED I/O comparison table** (real Flash $1.50/1M numbers) + 1-line take | Today | [2026-05-20/03 §1](./2026-05-20/03-practical-skills-and-tools.md#1-comparison-table) |
| ⚪ | Fix LinkedIn skills row to real on-stage terms (Antigravity / Managed Agents / WebMCP / Gemini 3.5 Flash) | Today | [2026-05-20/01 §1](./2026-05-20/01-big-lab-moves.md#1-io-scorecard) |
| ⚪ | Apply to one OpenAI FDE role before Tomoro-integration flood | Today | [2026-05-19/05 §2](./2026-05-19/05-career-and-startup.md#2-openai-deployment-co) |
| ⚪ | Apply to one Anthropic Solutions / Integration role | Today | [2026-05-19/05 §2](./2026-05-19/05-career-and-startup.md#2-openai-deployment-co) |
| ⚪ | Add **Google Cloud Agent / Antigravity Solutions** roles to apply list (thin queue, just stood up) | Today | [2026-05-20/05 §4](./2026-05-20/05-career-and-startup.md#4-applications) |
| ⚪ | LinkedIn-search 20 Tomoro FDEs + send connect requests | Wed | [2026-05-19/05 §2](./2026-05-19/05-career-and-startup.md#2-openai-deployment-co) |
| ⚪ | Add Gemini 3.5 Flash as cheap leg in 3-provider router + log per-step cost | Wed/this week | [2026-05-20/03 §4](./2026-05-20/03-practical-skills-and-tools.md#4-cost-routing) |

### Thursday May 21 (Meta-alumni outreach window)

| Status | Action | Due | Source |
|---|---|---|---|
| ⚪ | 8 AM PT — send 10 Meta DMs; **split pools: (a) displaced = substance, (b) redirected-to-AI = congrats/no-ask, (c) spinning-out = track** | Thu 8 AM PT | [2026-05-21/05 §1](./2026-05-21/05-career-and-startup.md#1-meta-outreach) |
| ⚪ | Add all DMs to `apps/meta-alumni-tracker.md` + APPLICATIONS.md (tag pool a/b/c, set 90-day follow-up) | Thu evening | [2026-05-21/05 §1](./2026-05-21/05-career-and-startup.md#1-meta-outreach) |
| ⚪ | Add **pre-deployment evaluation / AI-assurance** to skills vocabulary; add **bank AI-risk teams** (JPM/GS) to apply list — new lane the AI EO just opened | This week | [2026-05-21/05 §3](./2026-05-21/05-career-and-startup.md#3-eo-lane) |
| ⚪ | Keep the weekly **1 Anthropic Solutions/FDE/Integration** application (artifacts attached) — profitable-early + $15B/yr compute = growth-hire posture | This week | [2026-05-21/05 §4](./2026-05-21/05-career-and-startup.md#4-anthropic-hiring) |

### Friday May 22

| Status | Action | Due | Source |
|---|---|---|---|
| ⚪ | 30-min Meta-alumni reply window (log replies in `apps/meta-alumni-tracker.md`, set 90-day follow-up) | Fri | [2026-05-22/05 §3](./2026-05-22/05-career-and-startup.md#3-meta-followup) |
| ⚪ | **Ship the dual-model sanitiser project — REFRAMED:** Opus-planner/Sonnet-worker team + verify against **one real MCP server** (cite MCP-Atlas / Toolathlon) + **per-step token-by-model cost table** → answers orchestration + real-tool-verification + cost in one artifact | Fri night | [2026-05-22/03 §2](./2026-05-22/03-practical-skills-and-tools.md#2-artifact) · [2026-05-22/04 §1](./2026-05-22/04-research-progress.md#1-real-tool-benchmarks) |
| ⚪ | Set up the **Opus-4.7 orchestrator + Sonnet-4.6 workers** agent team (~40% cheaper) + the plan→annotate→"address all notes, don't implement yet" loop | Fri/tonight | [2026-05-22/03 §1](./2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) |
| ⚪ | Apply to 1 Anthropic role **referencing the Karpathy pre-training-automation direction specifically** (artifacts attached) — before the Karpathy-effect applicant wave | This week | [2026-05-22/05 §1](./2026-05-22/05-career-and-startup.md#1-karpathy-signal) |
| ⚪ | Add **agentic-SOC / AI security operations** (Exaforce + category) to apply/watch list — thin, two-tailwind lane (VC + EO cyber half) | This week | [2026-05-22/05 §4](./2026-05-22/05-career-and-startup.md#4-soc-lane) |
| ⚪ | Read the **"Agentic Reasoning" survey** (arXiv 2601.12538) for the 3-layer taxonomy — highest ROI-per-hour interview prep | This week | [2026-05-22/04 §2](./2026-05-22/04-research-progress.md#2-agentic-reasoning-survey) |
| ⚪ | (optional) Ship AIRS-Bench portfolio project | Fri | [2026-05-19/05 §3](./2026-05-19/05-career-and-startup.md#3-airs-bench-project) |

### Saturday May 23

| Status | Action | Due | Source |
|---|---|---|---|
| ⚪ | **Ship the hook-guarded, MCP-wired mini-agent + per-step cost trace** (orchestration + guardrails + cost-awareness in one artifact) | Sat | [2026-05-21/03 §2](./2026-05-21/03-practical-skills-and-tools.md#2-artifact) |
| ⚪ | **Ship WebMCP origin-trial demo** (or "what I'll build when Chrome 149 lands" post) | Sat | [2026-05-20/03 §2](./2026-05-20/03-practical-skills-and-tools.md#2-webmcp-demo) |
| ⚪ | Workday × Anthropic Solopreneurship Accelerator application | Sat | [2026-05-19/05 §5](./2026-05-19/05-career-and-startup.md#5-workday-solopreneur) |
| ⚪ | STARTUPS.md re-rank — agent-identity/WebMCP-tooling to top-fit | Sat | [STARTUPS.md](./STARTUPS.md) |

### Sunday May 24

| Status | Action | Due | Source |
|---|---|---|---|
| ⚪ | Weekly review: write WEEK-2026-05-18.md rollup | Sun | (new convention this week) |
| ⚪ | Cleanup ACTIONS.md (move open items to next week, archive 🟢 / 🔴) | Sun | (this file) |

---

## Active multi-week threads (no fixed due date)

| Status | Action | Carried from | Notes |
|---|---|---|---|
| ⚪ | Ship public MCP server (3 tools, 5-case eval, README, demo gif) | [ME.md](./ME.md) | Pin above resume projects |
| ⚪ | Personal Claude billing audit + writeup | [ME.md](./ME.md) | Doubles as validation for router-startup wedge |
| ⚪ | One vertical-Claude-for-X workflow library | [ME.md](./ME.md) | Doubles as Solopreneurship Accelerator application asset |
| ⚪ | Pre-built 10-Meta-engineer outreach short-list | [2026-05-18/05](./2026-05-18/05-career-and-startup.md) | Use Thursday May 21 |
| ⚪ | 5 Meta sub-org DM templates | [2026-05-18/05](./2026-05-18/05-career-and-startup.md) | Use Thursday May 21 |
| ⚪ | Read CHAL paper end-to-end + post LinkedIn paragraph | [2026-05-18/04](./2026-05-18/04-research-progress.md) | This week |
| ⚪ | Apply to Isomorphic Labs eng role (London / Cambridge MA / Lausanne) | [2026-05-18/02](./2026-05-18/02-new-emerging.md) | Within next 30 days of Series B close |
| ⚪ | Drop `CLAUDE.md` (Karpathy template) into every active project root | [2026-05-17/03](./2026-05-17/03-practical-skills-and-tools.md) | One-time install |
| ⚪ | Enable prompt caching on highest-volume project | [2026-05-17/03](./2026-05-17/03-practical-skills-and-tools.md) | Confirm via cache_read_input_tokens > 0 |
| ⚪ | Build 3-provider router (Claude + GPT + Gemini) | [2026-05-10](./2026-05-10/) | Ship to GitHub |
| ⚪ | Apply to OpenAI Residency 2026 | [ME.md](./ME.md) | Submit this month |
| ⚪ | Apply to Anthropic AI Safety Fellowship | [ME.md](./ME.md) | Submit this month |
| ⚪ | Apply to Google DeepMind Early Career | [ME.md](./ME.md) | Submit this month |
| ⚪ | Audit own model/token spend for 2 weeks | [2026-05-10](./2026-05-10/) | Doubles as validation for model-router startup |
| ⚪ | Pitch 1 local SMB on a "vertical-Claude-for-X" workflow | [2026-05-17/05](./2026-05-17/05-career-and-startup.md) | Customer discovery for startup wedge |
| ⚪ | Pick ONE of 5 AI sub-roles (Applied / Platform / LLM / Product / Responsible) | [2026-05-16/05](./2026-05-16/05-career-and-startup.md) | Then rewrite resume headline to match |
| ⚪ | Toggle Agent SDK credit setting in Claude account | [2026-05-18/03](./2026-05-18/03-practical-skills-and-tools.md) | 5-min fix, silent fail June 15 if skipped |

---

## Archive (recently done — keep for ~30 days)

(none yet — this file is new as of 2026-05-19)

---

## Notes

- **One rule:** ACTIONS.md only contains things *you* will do, not threads to watch. Watching-threads live in [WATCHLIST.md](./WATCHLIST.md).
- **Tuesday + Sunday update cadence:** Tuesday after the daily edition lands, Sunday during the weekly rollup.
- **If an action sits ⚪ for 14 days,** either upgrade to 🟡, drop to 🔴 (with a one-line reason), or move it to a `someday/` section. Don't let dead items accumulate.
