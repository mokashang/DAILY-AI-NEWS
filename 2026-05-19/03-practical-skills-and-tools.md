# Practical Skills & Tools — 2026-05-19

Today is **the highest-leverage 8-hour viewing window of the spring cycle**. You have two simultaneous keynotes (Google I/O 10 AM PT + Code w/ Claude London livestream ~1 PM PT) and a 90-minute publishing window after each. This file gives you the minute-by-minute discipline that converts viewing-time into a professional-brand asset.

Tags: `#io2026 #live-monitoring #playbook #publishing #cwc-london #prompt-caching #claude-md`

---

## 1. The 15-Minute-Block I/O Live-Monitoring Discipline {#1-io-live-discipline}

**Why now:** Yesterday's pre-stage gave you the comparison-doc skeleton. Today turns the live keynote into one clean 1-page artifact and one LinkedIn/X post — published within **90 minutes of keynote end** (target: 12:30 PM PT).

### The minute-by-minute schedule

| Time (PT) | Action | Why |
|---|---|---|
| **9:00–9:50 AM** | (a) Open your pre-staged `gemini-vs-claude-vs-gpt-2026-05-19.md` from yesterday. (b) Open your Code w/ Claude London tab in a second browser. (c) Open Engadget + TechRadar live blogs in tabs 3 + 4. (d) Open a fresh `2026-05-19-io-notes.md` for raw observations. | Tooling pre-positioning |
| **9:50 AM** | Mute Slack / messages. Phone on focus mode. | Eliminate context-switching |
| **10:00 AM** | Keynote starts. Stream from [io.google/2026](https://io.google/2026/). | |
| **10:00–10:08 AM** | Watch the opener. **Write one line of classification at 10:08:** "Sundar led with [consumer / enterprise]." | This is the most predictive single signal of the next 18 months — captured before recency bias contaminates it |
| **10:08–10:25 AM** | Note model names + version numbers as they appear. Don't try to summarize meaning yet — just capture *facts*. Use the table below. | Facts first, interpretation second |
| **10:25–10:55 AM** | First product demo block. Note demo *names* and what each demo *showed*. If a benchmark slide appears, screenshot it. | The benchmark slides are the highest-decay content of the day — they disappear from public coverage by Thursday |
| **10:55–11:25 AM** | Vertex AI Agent Platform segment (or whatever the equivalent is). **This is the section you cannot skim.** Note: tier names, pricing per token, pricing per request, agent-runtime credits, integration partners named. | The single resume-keyword line item |
| **11:25–11:50 AM** | Demos + closing. Note any unexpected surprise. | The "one surprise" placeholder in your pre-staged template |
| **11:50–12:00 PM** | Keynote ends. Take a 10-minute break. **Stand up. Drink water.** | Don't write while still in "viewing" mode — let the recall consolidate |
| **12:00–12:25 PM** | Fill in the 4 placeholders in the pre-staged comparison doc: `[FLAGSHIP_NAME]`, `[CONTEXT_WINDOW]`, `[PRICING_PER_M]`, `[ONE_SURPRISE]`. Don't add anything else. | Resist scope creep |
| **12:25–12:30 PM** | Publish the markdown file to your GitHub blog OR a public Gist. | Publishing-as-discipline |
| **12:30 PM** | Cross-post the LinkedIn / X teaser with link. | First-mover window closes ~1 PM PT |
| **12:30–1:00 PM** | Lunch + skim Engadget + TechRadar to catch anything you missed. | |
| **1:00 PM** | Switch second monitor to Code w/ Claude London livestream. | See §3 below |

### The raw-observation table (paste into your `io-notes.md`)

```markdown
## 2026-05-19 Google I/O — raw observations

### Model names heard (with timestamps)
| Time (PT) | Model name | Type (LLM / multimodal / image / video / agent) | Notes |
|---|---|---|---|
| | | | |

### Benchmark slides (timestamps + claim)
| Time (PT) | Benchmark name | Score claim | vs. competitor cited |
|---|---|---|---|
| | | | |

### Pricing numbers (only as stated on stage)
| Item | Price quoted | Effective date | Conditions |
|---|---|---|---|
| | | | |

### Partner / customer logos shown
- [logo 1] — [segment named]
- [logo 2] — [segment named]

### One classification at 10:08 AM PT
Sundar led with: ___ (consumer / enterprise)

### One surprise
___
```

### The LinkedIn / X post template (paste-ready)

```text
Watched all 2 hours of Google I/O 2026.

Three takeaways for builders shipping today:

1. [FLAGSHIP_NAME] — [one sentence on what's actually new]
2. Vertex AI Agent Platform — [one sentence on pricing vs Claude Agent SDK]
3. [ONE_SURPRISE] — [one sentence why it matters]

The one thing I think most coverage will miss:
[YOUR_OWN_TAKE_2_SENTENCES_MAX]

Full 1-page comparison vs Claude Opus 4.7 + GPT-5.5: [LINK]
```

---

## 2. Code w/ Claude London — The 12-Minute Attention Slice {#3-cwc-london-monitoring}

London Day-1 livestream goes live around **1 PM PT** (9 PM London). You do not need to watch the whole thing. **Watch 12 minutes** — specifically:

| Slot | Time (PT, approx) | Why |
|---|---|---|
| **Keynote opener (3 min)** | 1:00 PM | Watch how Anthropic frames the London event vs Code w/ Claude SF — same or different? |
| **Boris Cherny on Claude Code (3 min)** | 1:15 PM (probably) | Whatever Boris demos is what the Claude Code roadmap looks like for Q3 2026 |
| **Customer-presenter intros (3 min)** | After Boris | Which customer (Asana / Cursor / GitHub / Replit / Vercel) Anthropic puts on stage *first* signals where the deepest deal lives |
| **Any post-I/O direct response (3 min)** | Mid-keynote | Anthropic likely has a slide that addresses something Google announced 3 hours earlier. Identify which one. |

Total: ~12 minutes of attention for a near-complete read of the strategic signal.

### Why this is the asymmetric play of the day

90% of US-based AI watchers will skip Code w/ Claude London entirely because of the time zone collision. The 10% who tune in get a clean read on **what Anthropic believes Google did or did not ship**. That's a 1-paragraph follow-up post you can publish by **5 PM PT** that nearly nobody else in your network will have written.

### The 5 PM PT follow-up post template

```text
3 hours after Google I/O 2026, Anthropic ran Code w/ Claude London Day-1.

Single thing Anthropic *did not* say:
[X]
(notable because Google announced [Y] this morning)

Single thing Anthropic *did* say that I think is the bigger story:
[Z]

Read both keynotes, not just one. Strategic asymmetry inside the gaps.
```

---

## 3. Prompt Caching Refresher (5-Minute Action If You Skipped Sunday's) {#2-prompt-caching}

**From the May 17 edition:** prompt caching saves 60–90% of input-token cost on multi-turn agent workflows. If you didn't enable it Sunday, do it now — the **Agent SDK metering goes live in 27 days** (June 15) and post-metering costs without caching can 2–4× a typical Claude Code session bill.

### The 5-minute install

**For Claude Code:**
```bash
# Update CLAUDE.md to opt in
# (Anthropic enabled caching by default May 8 but verify yours is on)
claude config get cache.enabled
# If false:
claude config set cache.enabled true
```

**For Claude Agent SDK / API:**
```python
# Pass cache_control on the system + tool definitions
messages.create(
    model="claude-opus-4-7",
    system=[
        {"type": "text", "text": SYSTEM_PROMPT,
         "cache_control": {"type": "ephemeral"}},
    ],
    tools=[
        {**tool_def, "cache_control": {"type": "ephemeral"}}
        for tool_def in MY_TOOLS
    ],
    messages=conversation,
)
```

**Verification:** call your highest-volume project twice in a row with identical system prompt. Second call should report `cache_read_input_tokens` > 0 in the response. If it doesn't, your system / tool blocks aren't deterministic between calls.

**Source:** [Anthropic prompt caching docs](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching) `[primary]`

→ Cross-link: see [`2026-05-17/03` §1](../2026-05-17/03-practical-skills-and-tools.md) for the long-form recipe.

---

## 4. The Two-Tab Comparison Workflow for Today and Beyond {#4-two-tab-workflow}

A standing technique you should adopt permanently after today. When two competing announcements drop in the same news cycle, do **not** read them sequentially. Open both tabs side-by-side and read **claim-by-claim**:

| Claim category | Gemini 3.5 says | Claude Opus 4.7 says | Implication |
|---|---|---|---|
| Context window | | | |
| Pricing per M (in / out) | | | |
| Multimodal scope | | | |
| Agent SDK pricing model | | | |
| Tool-use spec | | | |

This single 15-minute discipline turns "two press-release readings" into a defensible technical opinion. Save the table as `2026-05-19-gemini-claude-claim-table.md`. **Add a new row each time either lab ships an update for the rest of 2026.** By July you have a 6-month rolling claim-comparison that no analyst publication maintains — and that becomes the asset you reference in every FDE / Solutions interview from here on.

---

## 5. Tonight (Tuesday) After Both Keynotes — 30 Minutes {#5-tonight}

1. **(10 min)** Update [ACTIONS.md](../ACTIONS.md) — mark today's completed items, add tomorrow's specific tasks
2. **(10 min)** Update [WATCHLIST.md](../WATCHLIST.md) — change at least 3 thread statuses based on today's announcements
3. **(10 min)** Update [STARTUPS.md](../STARTUPS.md) — if today's keynote validated or killed any wedge you had logged, mark it

**Why this matters:** the daily editions accumulate value only if WATCHLIST + ACTIONS + STARTUPS stay synchronized. **The single behavior that turns this repo from a passive newsletter into a personal intelligence system is the 30-minute end-of-day update loop.**
