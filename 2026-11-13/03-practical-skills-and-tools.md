# Practical Skills & Tools — 2026-11-13

Two things to actually do this weekend, both tied to news that broke this week: **(1)** re-cost your Claude Code loop and re-prune your `CLAUDE.md` on the Fable 5.2 release + 20% API cut; **(2)** build a 90-second "Claude in Google Meet" demo you can post to LinkedIn Monday morning. Plus a 15-minute **ANT tracker widget** build so you can watch IPO pricing the way an operator would.

Tags: `#claude-code #fable-52 #claude-md #meetings #demo #billing #cost`

---

## 1. The IPO-week Claude Code checklist — Fable 5.2 default + billing audit + CLAUDE.md pruning + dual-model cost-router {#1-fable-52-checklist}

**60-minute weekend reset. Highest-ROI AI-ops hour of November.**

### Step 1 — Flip your Claude Code default to Fable 5.2 (5 min)

Fable 5.2 landed **Nov 9** at **$8 in / $40 out per 1M tokens** (down from $10 / $50 on Fable 5.1 — a **~20% cut**), with **~30% faster output** and **65 on the Artificial Analysis Intelligence Index** (top of leaderboard). For most Claude Code sessions, **5.1 is strictly dominated**.

```bash
# Set in your project's .claude/settings.json or user settings
{
  "defaultModel": "claude-fable-5-2",
  "codingPairTier": {
    "orchestrator": "claude-fable-5-2",
    "worker": "claude-haiku-5-5",
    "workerEffort": "medium"
  }
}
```

**Fast mode** (`$16/$80`): reserve for interactive coding where you'll tab away between prompts. Not worth it for background runs.

**Batch mode** (`$4/$20`): use for any async pipeline where you can tolerate a few hours latency. Eval harnesses, portfolio-wide refactors, documentation generation — all batch. **Halving your output cost compounds against the already-20% API cut.**

### Step 2 — Run a 30-day billing audit (15 min)

This is the **4th-of-month ritual from your personal rules**, pulled forward 3 weeks because of the Fable 5.2 reprice.

```bash
# In your Anthropic console, export usage for the trailing 30 days
# Then group by:
#   - Model (Fable 5.1 vs Fable 5.2 vs Opus 4.7 vs Haiku 5.5)
#   - Mode (standard / fast / batch)
#   - Caller (Claude Code, Agent SDK, direct API, OpenClaw)
```

What to look for:
- **Any lingering Fable 5.1 calls** — route them to 5.2 (20% cheaper, faster, higher intelligence).
- **Any Opus 4.7 orchestrator with Fable 5.2 worker inversions** — the 2026-05-22 "Opus orchestrator + Sonnet worker ≈ 40% cheaper" rule still holds in spirit; **now the rule is "Fable 5.2 orchestrator + Haiku 5.5 worker."** Confirm you're not accidentally running Opus-only.
- **Fast mode on async paths** — move to standard or batch. Any fast-mode call that doesn't need a human watching the stream is money on fire.
- **Prompt-caching hit rate** — the 2026-05-17 playbook target was 60-90% input-cost savings. If your hit rate is <40%, your 60-min cache refresh is mis-tuned.

**Target:** Trim 25-40% off your monthly AI bill without losing any capability. Doable in an afternoon.

### Step 3 — Prune `CLAUDE.md` under 200 lines (20 min)

Per Anthropic's latest Claude Code guidance (re-emphasized across multiple November best-practice posts): **`CLAUDE.md` is always-loaded context; keep it under 200 lines and move workflow-specific guidance into on-demand skills.**

Rules of thumb:
- **Keep in `CLAUDE.md`:** project-wide invariants, naming conventions, test commands, architectural must-reads, "never do X" rules.
- **Move to skills (loaded on demand):** language-specific style guides, framework-specific patterns, the "how to deploy this service" runbook, long example blocks.
- **Delete:** anything that reads like documentation of what the code does — Claude can read the code.

Target shape:
```
CLAUDE.md
├── Project in 3 sentences (what it is, why it exists, who uses it)
├── Repository layout (one line per top-level dir)
├── Golden commands (install, test, lint, run, deploy — 4-6 lines)
├── Must-reads (3-5 file paths)
├── Never-do (5-10 bullets)
└── Links to specific skills for deeper workflows
```

If you can trim yours to 150 lines, Claude Code's first-turn performance measurably improves because the context budget for *your actual question* widens.

### Step 4 — Ship (or refresh) your dual-model cost-router (20 min)

The [2026-05-22](../2026-05-22/03-practical-skills-and-tools.md) + [2026-09-10](../2026-09-10/03-practical-skills-and-tools.md) editions prescribed a **30-line router shim with a 5-case eval suite** as the interview-differentiator artifact. **Update it this weekend** to:

1. Default **orchestrator = Fable 5.2**.
2. Default **worker = Haiku 5.5 w/ `effort: medium`**.
3. Promote worker to `effort: high` if the task failure rate on the eval set exceeds 20% at `medium`.
4. Promote orchestrator to **Fast mode** only if the end-to-end wall-clock SLA is < 8 seconds.
5. Route **cyber / life-sciences** tasks to **Mythos 5.2** iff your org is verified; otherwise fall back to Fable 5.2.

Commit. Push. Add a **one-paragraph README update** that cites Nov 9 pricing + Nov 10 effort-level pattern. That README paragraph is a **recruiter-readable artifact** that proves current AI-ops literacy — more hiring signal than any coursework.

### Sources
- [Collabnix — Claude Code: The Complete Guide and Best Practices for AI-Powered Development in 2026](https://collabnix.com/claude-code-the-complete-guide-and-best-practices-for-ai-powered-development-in-2026/) `[analysis]`
- [deska.dev — Claude Code Best Practices in 2026: Mastering AI Terminal Agents](https://deska.dev/blog/claude-code-best-practices-2026) `[analysis]`
- [agentsroom.dev — 50 Claude Code Tips & Tricks: Ship 10x Faster in 2026](https://agentsroom.dev/claude-code-tips) `[analysis]`
- [diyai.io — Claude Code Best Practices: 15 Rules for Safer Agentic Coding](https://diyai.io/ai-tools/code-generation/claude-code-best-practices/) `[analysis]`
- [iwoszapar.com — Claude Code Best Practices: CLAUDE.md and Checks](https://www.iwoszapar.com/p/claude-code-best-practices) `[analysis]`
- [baeseokjae.github.io — Claude Code Best Practices 2026: 15 Habits of Developers Who Ship Faster](https://baeseokjae.github.io/posts/claude-code-best-practices-2026/) `[analysis]`

### Why it matters

- **Job:** This is the single most-recent artifact-shaped signal you can show in interviews between now and Feb. Recruiters searching "Claude Code router" / "Fable 5.2 cost optimization" / "Haiku 5.5 effort levels" land on fresh content from exactly three people this month; be one.
- **Startup:** 25-40% bill reduction extends your runway proportionally. If you're pre-seed with a $150K Anthropic bill, that's a full extra month.
- **Insight:** **AI-ops discipline is replacing raw prompting skill as the status marker in AI engineering roles.** Owning your bill is the first-order move.

→ Cross-link: [2026-09-10/03 §1 Fable 5.1 economics](../2026-09-10/03-practical-skills-and-tools.md) · [2026-05-22/03 cost-router](../2026-05-22/03-practical-skills-and-tools.md) · [2026-10-14/03 Haiku 5.5 effort levels](../2026-10-14/03-practical-skills-and-tools.md).

---

## 2. The Google-Meet-plus-Claude 90-second screencast — your Monday-morning LinkedIn demo {#2-meetings-demo}

**Why this weekend specifically:** Claude Meetings went to Google Meet **in beta today (Nov 13)** and is on **Team + Enterprise plans only**. There's a ~2-week window where very few people on LinkedIn have shipped a "here's what it looks like in practice" demo. First-mover content wins the recommender-system boost. **Build it Saturday, record Sunday, post Monday 8:30 AM PT.**

### What you need

- Access to a **Claude Team or Enterprise plan** (14-day trial is enough; if your school has institutional access via a Workday or Canva partnership, use that).
- A **Google Workspace** account that can host a Meet call.
- Two people (you + a friend) to simulate a stand-up.
- **OBS Studio** (free) or Loom to record.
- A **90-second script** that shows four moments:
  1. **Admit Claude to the call** (visible participant announces itself in chat).
  2. **Ask Claude mid-call:** "Draft a 3-week project plan from what we just discussed."
  3. **Claude posts in the meeting chat** without interrupting voice.
  4. **End the call. Open claude.ai. Show the notes + action items.**

### The 90-second script

> **(0:00)** "This is Claude joining a Google Meet. Watch the chat — it announces itself."
>
> **(0:10)** [you + friend discuss a fake product sprint for 20 seconds]
>
> **(0:30)** "Claude, draft a 3-week plan from what we just discussed — owners, blockers, test plan."
>
> **(0:35)** [Claude's reply posts in meeting chat — read the first two lines aloud]
>
> **(0:50)** "I didn't have to say 'send that as a message' — notice it doesn't speak over me."
>
> **(1:00)** "If an unauthorized external joined now, it would exit automatically. Admin-controlled."
>
> **(1:10)** [cut to claude.ai after the call ends — show notes + action items]
>
> **(1:25)** "Four minutes of meeting, zero minutes of post-meeting write-up. Shipping 2026-11-13. Link in comments."

### The LinkedIn post (what to write under the video)

```
Claude joined a Google Meet with me today.

It announced itself in chat.
Drafted a 3-week plan while we were still talking.
Posted answers in the meeting chat, not over our voices.
Left notes + action items in claude.ai after.

Beta rolled to Team + Enterprise 2026-11-13.

Three questions this raises for product design:
1. How does an AI request permission to speak?
2. What's the UX for AI-in-meetings guest permissions?
3. When notes drift from what actually happened, who owns the retraction?

Thoughts?

#AnthropicClaude #AIproduct #ClaudeMeetings
```

### What this does for you

- **Job:** A recruiter reading **"AI product thinking"** on your profile has to take your word for it. A 90-second screencast on your feed shows AI product thinking. The gap between those two is the difference between "shortlist" and "yes."
- **Startup:** If "visible AI in meetings" is adjacent to your startup thesis, this post is also a **cheap distribution test**. Comments and reactions are the market research.
- **Insight:** **The UX of "AI as visible participant" is unwritten.** The question list in your post is a thesis statement. Anyone who articulates good questions about product gaps gets attention that pure product reviews don't.

### Sources
- [TechCrunch — Anthropic launches Claude Meetings (Nov 10)](https://techcrunch.com/2026/11/10/anthropic-launches-claude-meetings-to-turn-workplace-discussions-into-plans-and-tasks/) `[secondary]`
- [Dataconomy — Claude Meetings to Google Meet in Beta (Nov 13)](https://dataconomy.com/2026/11/13/anthropic-brings-claude-meetings-to-google-meet-in-beta) `[secondary]`
- [Allwork.Space — Anthropic Brings Claude To Google Meet](https://allwork.space/2026/11/anthropic-brings-claude-to-google-meet-to-turn-workplace-conversations-into-action) `[secondary]`

→ Cross-link: [`01` §3 Claude Meetings details](./01-big-lab-moves.md#3-claude-meetings).

---

## 3. 15-minute ANT tracker widget — read the IPO like an operator, not a retail investor {#3-ant-tracker}

**Build a terminal widget by Monday evening that watches ANT.** Not for trading — for **signal density**. Pricing lands ~Nov 18 after-hours; first trade ~Nov 19 at 9:30 AM ET. You want the number *on your screen* for the next 10 business days.

### Minimal spec

```python
# ant_tracker.py — 15 lines, uses yfinance
import yfinance as yf
import time

while True:
    ticker = yf.Ticker("ANT")
    info = ticker.info
    print(
        f"ANT  ${info.get('regularMarketPrice', 'n/a'):>7} "
        f"  vs IPO $78  "
        f"  mkt cap ${info.get('marketCap', 0)/1e12:.2f}T "
        f"  volume {info.get('volume', 0):>10,}"
    )
    time.sleep(60)
```

**Wire it into your tmux / terminal multiplexer status bar** so you see it without opening it.

### Signal interpretation (not financial advice)

- **ANT prices in range ($70–$78)** → book order, normal demand.
- **ANT prices above range (>$78)** → **green-light demand** — partner-firm equity packages reset upward, Anthropic opens new reqs with a time-lag of ~30 days.
- **ANT prices below range (<$70)** → **cool reception** — Anthropic hiring freeze risk through Q1; partner-firm GenAI practices pause. Pivot your apply plan to Google / OpenAI / enterprise ML within 2 weeks.
- **First-day close** → the single most-watched number. **>$95 (~$1.25T)** = partner firms open new reqs by Dec 15. **<$70 (break-issue)** = **run** to [`05` §2 cooling-market pivot](./05-career-and-startup.md#2-apply-plan).

### Why it matters

- **Job:** You can't outperform in an Anthropic / partner-firm interview if you don't know what ANT did yesterday. This is 15 minutes of code for the next 90 days of market-aware confidence in every conversation you have with an AI recruiter.
- **Startup:** Same — any founder pitching into the AI stack this quarter needs ANT on their dashboard.
- **Insight:** **A tradable Anthropic is a gift to the operator class.** You get a public price for the thing you've been investing your career in. **Use it.**

→ Cross-link: [`01` §1 Anthropic IPO details](./01-big-lab-moves.md#1-anthropic-ipo) · [`05` §3 IPO-week moves](./05-career-and-startup.md#3-ipo-week-moves).

---

Last updated 2026-11-13. See [`01-big-lab-moves.md`](./01-big-lab-moves.md) for the news behind each tip; [`05-career-and-startup.md`](./05-career-and-startup.md) for the apply plan.
