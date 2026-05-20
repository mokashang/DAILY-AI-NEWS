# Career & Startup — 2026-05-20

Today's the day two macro forces become actionable at once: **Meta's 8,000 are being notified right now** (your outreach window opens tomorrow 8 AM PT), and **Gemini 3.5 Flash's price shot** just re-priced which skills are scarce. The thread to internalize: the frontier moved from "smartest model" to "cheapest-good-enough + best agent rails + safe under autonomy" — and *that* reshuffles the job market in your favor if you lean into cost-aware, safety-aware agent engineering.

Tags: `#meta-layoff #outreach #fde #cost-aware #agent-safety #webmcp #price-war #playbook`

---

## 1. Meta — Outreach Window Opens Tomorrow 8 AM PT {#1-meta-outreach}

The cut is executing today (details in [`01` §4](./01-big-lab-moves.md#4-meta-executing)). The **new** detail that changes the playbook: **~7,000 workers are being redirected** into newly created AI teams — **Applied AI Engineering · Agent Transformation Accelerator XFN · Central Analytics** — *not* let go. So the Thursday wave splits three ways, not two:

| Pool | Who | Your move |
|---|---|---|
| **(a) Genuinely displaced — MLE/Research** | Superintelligence Labs reorg fallout | Compete pool — these chase the same lab roles you want; don't mine for warm intros |
| **(b) Genuinely displaced — SDE / RL / ads / global ops** | Reality Labs, FoA, recruiting, sales | **Your target pool** — future founders + hiring managers at the next startup wave |
| **(c) Redirected into AI teams (~7,000)** | moved to Applied AI Eng / Agent Transformation Accelerator | **Warm-network pool** — still at Meta, now doing agent work; connect, don't pitch |

**Pool (c) is the new opportunity:** these people just got re-pointed at *exactly* the agent-deployment work you're skilling into. They're not job-hunting — so a no-ask connection now (congratulate the new team, share one relevant artifact) builds a relationship with people who will be hiring-influencers inside Meta's agent org within a quarter.

### Thursday May 21 playbook (refreshed)

**8 AM PT — outreach hour (10 DMs max):**
- Opener that performs ~3×: *"Saw the news. Not asking anything Meta-confidential — just sharing two things I think you'd want based on your work on [specific project]."* → (a) one technical thing you built this month (your I/O comparison table or dual-model sanitiser demo), (b) one role/company-relevant link.
- **For pool (c)** (people who *moved* to AI teams, not out): *"Congrats on the move to [Applied AI Engineering / Agent Transformation]. I've been shipping on Managed Agents — would love to compare notes sometime, no agenda."*
- Reply-rate target: 3/10 (layoff-week baseline runs higher than normal).

**Friday May 22 — 30-min reply window:** never lead with "are you hiring." Lead with *"15-min chat next week? One specific question about [their stack] that's hard to answer publicly."*

**Log everything in [APPLICATIONS.md](../APPLICATIONS.md):** Name · Sub-org · Pool (a/b/c) · DM date · Reply · Status.

**Sources:** see [`01` §4](./01-big-lab-moves.md#4-meta-executing) for the full confirmed-detail source list.

### Why it matters to you

- **Job lens:** Distinguishing pool (b) from (c) is the edge. Most people will blast generic "sorry about the layoff" DMs to *everyone*. You'll send congratulations to (c) and substance to (b) — two different, correct messages. That precision is itself the signal.
- **Startup lens:** Meta-alumni founder formation runs **60–90 days** post-layoff. Start `meta-alumni-tracker.md` today; by Aug 1 track 10–15 new startups, by Oct the first will raise seed. Pool (b) is your future-cofounder/early-hire pipeline.
- **Insight:** Meta funding an **$145B** AI build with a 10% cut, while *redirecting* 7,000 into agent teams, is the cleanest public demonstration yet of **headcount-to-compute substitution with internal reskilling**. The 2027 read: expect Microsoft/Salesforce/Oracle to copy the *redirect-not-just-cut* move — which means the durable internal roles are the **agent-transformation / applied-AI** ones. Skill toward those, not toward roles AI is substituting.

---

## 2. The Gemini 3.5 Flash Price War Re-Prices Your Skills {#2-price-war}

When the frontier shifts from "smartest" to "cheapest-good-enough + best rails," the **scarce, well-paid skills shift too.** Here's the re-rank:

| Skill | Before I/O | After Gemini 3.5 Flash | Why |
|---|---|---|---|
| **Cost-aware agent design / routing** | nice-to-have | **scarce & valuable** | $1.50/1M Flash makes routing the obvious architecture; few can actually build + measure it |
| **Agent-safety / IPI defense** | niche | **rising fast** | autonomous web agents + live attacks = every deployment needs it |
| **Raw "I can prompt GPT/Claude"** | common | **commoditized** | the models are cheap and everywhere; this is no longer a differentiator |
| **MCP / WebMCP integration** | strong | **stronger** | now an open web standard with a Chrome ship date |
| **Multi-vendor evaluation** | useful | **useful+** | choosing Flash-vs-Claude-vs-GPT per step *is* the job now |

**Your concrete move:** the cost-router + per-step cost chart from [`03` §4](./03-practical-skills-and-tools.md#4-cost-routing) is now your **single most resume-relevant artifact**. It demonstrates the exact skill the price war just made scarce. Build it this week; lead your portfolio with it.

### Why it matters to you

- **Job lens:** Rewrite your headline around the *scarce* skills: **"Cost-aware & safety-aware agent engineering · MCP/WebMCP · Claude Agent SDK + Gemini Managed Agents · multi-vendor routing."** Avoid the commoditized framing ("prompt engineer," "ChatGPT power user").
- **Startup lens:** A startup whose only edge was "cheap inference" got squeezed; a startup whose edge is **"we route intelligently + prove the savings + keep it safe"** got *more* defensible. The model-router wedge (with your own billing-audit data as validation) is the cleanest SDE-founder play on the board this week.
- **Insight:** Every previous compute-price drop expanded the *application* layer faster than it compressed the *infra* layer. Flash at $1.50 means a whole class of agent products that were uneconomical last week are viable this week — **the application-builder (you) is the winner of a price war, not the loser.**

---

## 3. The 1-Evening Agent-Safety Portfolio Project {#3-safety-project}

**The artifact:** the dual-model sanitiser demo from [`03` §3](./03-practical-skills-and-tools.md#3-dual-model) — agent-with-injection (vulnerable) vs. agent-with-sanitiser (defended), both traces published.

**Why it's the highest-ROI 3 hours this week:**
- It answers the **single most likely 2026 agent-deployment interview question** ("how do you stop prompt injection?") with running code, not theory.
- It rides a *this-week* primary-source catalyst (Google's IPI report) → SEO + recency signal.
- It demonstrates the convergence thesis ([`04` §2](./04-research-progress.md#2-convergence)) — verifier/sanitiser/eval all being one primitive — which reads as senior-level synthesis.
- It's a **defensive-security artifact on your own test page** — fully authorized, no targeting of real systems.

**Repo:** `README.md` (threat + defense + cite Google report) · `vulnerable.py` (~30 lines) · `defended.py` (~30 lines, Flash/Haiku sanitiser) · `traces/` · one diagram. Pin it above generic LangChain demos.

→ Cross-link: [`04` §1 IPI report](./04-research-progress.md#1-ipi-wild) · [`03` §3 implementation](./03-practical-skills-and-tools.md#3-dual-model).

---

## 4. Application & outreach status — what's live this week {#4-applications}

| Item | Status | Action this week |
|---|---|---|
| OpenAI FDE role (beat Tomoro-integration flood) | open | Apply **today** — [2026-05-19/05 §2](../2026-05-19/05-career-and-startup.md#2-openai-deployment-co) |
| Anthropic Solutions/Integration (cite OpenAI-Deployment-Co framing) | open | Apply this week |
| Isomorphic Labs eng (London/Cambridge/Lausanne) | open | Within 30 days of Series B close |
| Workday × Anthropic Solopreneurship Accelerator (15 slots) | open | Draft wedge → apply Sat |
| OpenAI Residency / Anthropic Fellowship / DeepMind Early Career | open | Submit this month |
| Tomoro FDE LinkedIn connections (20) | in progress | Send 5 connects |

**New this week given I/O:** add **Google Cloud — Agent / Antigravity Solutions** roles to the apply list. Google just stood up an enterprise-agent platform (Antigravity 2.0 + Managed Agents + Gemini Enterprise Agent Platform) — that org *will* staff a Solutions/FDE-equivalent function, and being early (before the role pages fill out) is the thin-queue advantage you exploited with OpenAI.

---

## 5. The Week Ahead — One-Glance {#5-week-ahead}

| Day | Highest-leverage 1-hour action |
|---|---|
| **Today (Wed 5/20)** | Publish the filled-in I/O comparison table; update LinkedIn skills to real terms (Antigravity/Managed Agents/WebMCP); apply to 1 OpenAI FDE + 1 Anthropic Solutions |
| **Thu 5/21** | 8 AM PT Meta outreach hour (10 DMs, split pools b/c); log in APPLICATIONS.md; watch any Tomoro-FDE accepts |
| **Fri 5/22** | Ship the dual-model sanitiser safety project to GitHub; 30-min Meta reply window |
| **Sat 5/23** | WebMCP origin-trial demo (or the "what I'll build when Chrome 149 lands" post); Workday Accelerator application |
| **Sun 5/24** | Weekly review: WEEK-2026-05-18.md rollup; ACTIONS.md cleanup; STARTUPS.md re-rank (agent-identity/WebMCP to top) |

**The week's one-sentence thesis:** *Google made models cheap and agents standard — so the scarce, paid skill is no longer "use a model," it's "route models cheaply, supervise them safely, and integrate them through open standards." Build the three artifacts (comparison table, cost-router, dual-model sanitiser) and you've demonstrated exactly that.*
