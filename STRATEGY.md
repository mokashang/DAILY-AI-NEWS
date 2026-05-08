# Curation Strategy

The thinking behind DAILY-AI-NEWS — refined so the system is reproducible, opinionated, and high-signal for *one specific reader*: an ambitious CS grad student aiming at both a startup and an SDE/MLE/AI role.

---

## Reader Model

Everything in this repo answers to one persona:

- **Background:** CS grad student, technically literate, knows the basics of LLMs/transformers/PyTorch
- **Time budget:** 5–25 minutes/day; an hour on weekends
- **Twin objectives:**
  1. Build a startup (or join an early team and learn the playbook)
  2. Land a top-tier SDE / MLE / AI Engineer role
- **Key risk being managed:** missing a wave (capability shift, cost shift, distribution shift) that changes which jobs are safe and which startup ideas are doomed

This means a piece of news only earns a spot if it changes:
- a job you should apply for / a skill you should add
- a startup wedge that just opened or closed
- a tool to actually use this week
- a research direction worth tracking for thesis or portfolio

If a story doesn't pull at least one of those levers, skip it — no matter how much engagement it has online.

---

## The Five Buckets (Why These, and No Others)

| # | File | Question it answers | Length target |
|---|---|---|---|
| 01 | `01-big-lab-moves.md` | "Which way is the river flowing?" | 4–6 stories |
| 02 | `02-new-emerging.md` | "What didn't exist last week?" | 4–6 items |
| 03 | `03-practical-skills-and-tools.md` | "What can I act on this weekend?" | 4–6 items |
| 04 | `04-research-progress.md` | "What should I read or cite?" | 5–8 papers / benchmarks |
| 05 | `05-career-and-startup.md` | "What does this mean for *me*?" | mixed: jobs + wedges + action items |

**Why not more buckets?** Cognitive load. Five is the most a human can hold without re-reading the index.
**Why not fewer?** Each bucket optimizes for a different *time horizon*: 01 is multi-year strategy, 02 is months, 03 is this weekend, 04 is months-to-years, 05 is now.

---

## The Three-Part Anatomy of Every Entry

Every story (across all five files) is structured the same way:

1. **What happened** — the verifiable fact, not the spin.
2. **Sources** — ≥2 sources for non-primary claims, primary source if possible. If only one source exists, say so explicitly.
3. **Why it matters to you** — *direct* implication. Always include at least one of:
   - **Job lens** (skill, role, employer, interview question)
   - **Startup lens** (wedge, moat, distribution channel, exit path)
   - **Insight** (why the story is *actually* about something else)

If a "Why it matters" reads like a generic AI-newsletter take, it gets rewritten until it reads like a private message from a mentor.

---

## Source-Quality Rules

1. **Primary > secondhand.** OpenAI's blog beats TechCrunch's coverage of OpenAI's blog.
2. **Two-source rule for claims about $$, layoffs, deals, partnerships.** If only one outlet is reporting it, mark it `[reported by single source — verify]`.
3. **arXiv preprints are claims, not facts** — flag as preprint, link to the paper, note if it's been independently replicated.
4. **X / Twitter posts are leads, not citations.** Use them to find the official announcement, then cite that.
5. **Aggregator sites** (Crescendo, llm-stats, etc.) are good for *spotting* news; always click through to the primary source for the actual entry.
6. **No paywalled-only stories** unless paired with a free corroborating source. If The Information is the only source, link a secondary outlet that confirms.

---

## Daily Workflow (so this is reproducible without me)

**Sweep order, ~30 min total when warmed up:**

1. **Primary lab feeds** (5 min): OpenAI, Anthropic, Google DeepMind, Meta AI, xAI, Mistral, Hugging Face — scan for posts dated today.
2. **arXiv** (5 min): cs.AI, cs.LG, cs.CL recent — note 1–3 papers that look impactful.
3. **Funding + lab moves** (5 min): TechCrunch AI, The Information, Crescendo AI, The Decoder, Bloomberg tech.
4. **Live trackers** (5 min): HF Trending Papers, GitHub Trending, Artificial Analysis, llm-stats.
5. **Operator X feeds** (5 min): @sama, @darioamodei, @demishassabis, @karpathy, @simonw, @emollick, @ylecun — for tone and hot-take signals.
6. **Cluster & write** (5 min): map ~15 candidate items → 5 buckets → cut to 4–6 per bucket → write entries to the three-part anatomy above.

**Two-source rule trigger checklist** — before publishing, verify any of these claims have ≥2 independent sources:
- Dollar amounts (deals, raises, ARR)
- Hiring / layoff numbers
- Quotes attributed to executives
- Capability claims (e.g., "X% on benchmark Y")

---

## Editorial Voice

- **Direct and confident.** "This is the wedge of 2026" beats "this could potentially be relevant."
- **Specific, not generic.** "Add this skill: MCP server authoring" beats "develop AI skills."
- **Numbered, dated, sourced.** No "recently" — say "April 24" or "this week."
- **Always concrete.** If the entry doesn't end with a thing the reader can *do*, it gets a TODO line.
- **No hedge-everything language.** "Probably," "may," "could" are fine — "potentially could possibly maybe" is not.

---

## What This System Is Not

- **Not a news ticker.** If you want the firehose, use TLDR AI or llm-stats.
- **Not balanced reporting.** This is a personal intelligence digest with an agenda (your career + your startup).
- **Not exhaustive.** Missing a story is fine; including a low-signal story is not.
- **Not consumer-facing.** If your friend reads it and says "this is too dense," good — it's tuned to a builder.

---

## Failure Modes to Avoid

| Failure | What it looks like | Fix |
|---|---|---|
| **Aggregator soup** | "TechCrunch reports that..." with no original sourcing | Click through to primary; rewrite |
| **Headline rewriting** | Restating the title as the entry | Add the *implication* — what changes for you |
| **Too-broad insight** | "AI is changing everything" | Cut. Replace with a specific actionable line |
| **Overcoverage of one lab** | 4 of 5 stories are Anthropic | Force diversity: ≥3 different orgs per file |
| **Hype without numbers** | "Massive valuation, huge round" | Get the actual $ + valuation + investors |
| **Acting on rumor** | Citing only a single anonymous-source piece | Add the `verify` flag, find a corroborating source |

---

## Roadmap (Reasonable Next Improvements)

- [ ] **Weekly digest** every Sunday: distillation of the 5 stories of the week that *actually* mattered, with action items
- [ ] **Monthly skills-stack diff**: what got hot / cooled / commoditized this month
- [ ] **Job board changelog**: track what's appearing on the speedyapply / jobright AI college lists weekly
- [ ] **`/wedges`** subdirectory — running list of startup wedges seen, alive vs. dead
- [ ] **`/papers-i-actually-read`** — curated subset of the arXiv firehose I followed end-to-end, with notes
- [ ] **`/tools-i-actually-use`** — running personal stack with cost/value notes after each tool migration

---

## How to Use This Repo (Reading Strategy)

**5 minutes/day (minimum):**
- Read just the bold headlines in each of the day's 5 files

**20 minutes/day (recommended):**
- Read one full file deeply. Rotate through the 5 over the week.

**Weekend (1 hour):**
- Pick one item from `03-practical-skills` and actually do it (ship the project, install the tool, write the MCP server).
- Skim one paper from `04-research-progress` — abstract + figures + tables only.

**End of month:**
- Re-read all `05-career-and-startup` from the month back-to-back. Patterns will jump out.

The whole point: **read less, do more, never miss the wave.**
