# Practical Skills & Tools — 2026-05-18

Monday is the **pre-stage day** of the week. Tomorrow's I/O keynote is your single highest-leverage 4-hour artifact window of the month; everything you can finish *before* the keynote starts is pure capacity bought back. Plus: a small but high-ROI Anthropic-account setting most readers haven't toggled yet that bites on June 15.

Tags: `#io2026 #playbook #agent-sdk #pre-stage #prompt-caching #claude-md #live-blog`

---

## 1. The Pre-I/O Pre-Stage — 45 Minutes Tonight That Save 2 Hours Tomorrow {#1-io-prestage}

**Why now:** I/O 2026 keynote is **Tuesday May 19, 10 AM PT / 1 PM ET.** Every CS-grad-going-after-Vertex-FDE candidate in the world will be watching. The *first* in your network to publish a structured comparison wins the LinkedIn / X attention — and yesterday's [`03` §4 viewing playbook](../2026-05-17/03-practical-skills-and-tools.md#4-io-viewing-playbook) had a 1-page comparison as the Tuesday-afternoon target. Tonight, you pre-stage everything you can.

### The 45-minute checklist (do tonight, in this order)

**Block 1: Create the comparison doc skeleton (15 min)**

Open a new markdown file titled `gemini-vs-claude-vs-gpt-2026-05-19.md`. Paste this template:

```markdown
# Gemini 4 / 3.2 Flash vs Claude Opus 4.7 vs GPT-5.5 — Post-I/O Comparison

*Published 2026-05-19, [TIME] PT. Based on Google I/O 2026 keynote announcements.*

## Models at a glance

| | Gemini [NAME] | Claude Opus 4.7 | GPT-5.5 |
|---|---|---|---|
| **Context window** | [GEMINI] | 1M tokens (Sonnet 4.6 + Opus 4.7, extended thinking) | 1M+ |
| **Multimodal IO** | [GEMINI] | text + image + audio | text + image + audio + code |
| **Native tool use** | [GEMINI] | yes (Tool Use API + Computer Use) | yes (Responses API) |
| **Agent SDK** | [VERTEX_AGENT_SDK_DETAIL] | Claude Agent SDK (meter live June 15) | Assistants / Responses API |
| **API price — input / output per M tokens** | [GEMINI_PRICING] | $5 / $25 | $10 / $30 |
| **Available** | [today/preview/waitlist] | GA across Anthropic API + Bedrock + Vertex AI + MS Foundry | GA |
| **One-line strategic read** | [WRITE_AT_11:30_AM_PT] | Frontier-capability + agent-SDK leader; passing OpenAI on enterprise adoption | Frontier scale + multimodal breadth; Codex Mobile launched May 14 |

## What Google shipped

1. **[FLAGSHIP_NAME].** [2 sentences on what's new.]
2. **Gemma 4 open-weights.** [1 sentence.]
3. **Vertex AI Agent SDK.** [1 sentence on pricing + capability vs Claude Agent SDK.]
4. **Android 17 SDK.** [1 sentence on agent hooks.]
5. **Aluminium OS / Googlebook.** [1 sentence on dev SDK + OEM ship windows.]
6. **Android XR Gen 2.** [1 sentence on dev SDK.]
7. **[ONE_UNEXPECTED_THING].**

## My honest read

[3 short paragraphs.]
- **Capability:** [Is Gemini closer to or further from Mythos / GPT-5.5 than expected?]
- **Distribution:** [Did Google bet on consumer-Gemini-everywhere or enterprise-Vertex-Agent-SDK?]
- **For builders right now:** [What should you do with the new SDKs this week?]

## What to watch in the next 7 days

- Vertex Agent SDK pricing vs Claude Agent SDK after June 15 metering
- First independent Gemma 4 fine-tune to cross 1K GitHub stars (likely by Thursday)
- Code w/ Claude London on Wednesday — Anthropic's counter-response
- Any update to the Anthropic $30B raise term sheet

[Sources: io.google/2026, official Google / Anthropic / OpenAI press kits, ai.google.dev]
```

**Block 2: Fill in the rows you already know (10 min)**

Fill the **Claude Opus 4.7** column and the **GPT-5.5** column tonight. Numbers you already know:
- **Claude Opus 4.7:** 1M context (extended thinking), $5 input / $25 output per M tokens, GA on Anthropic API + Bedrock + Vertex AI + MS Foundry
- **GPT-5.5 (default ChatGPT model since May 5):** 1M+ context, $10 input / $30 output per M tokens, AIME 2025 81.2 / MMMU-Pro 76
- **Mythos:** restricted-access (Anthropic-approved orgs only) — note that publicly

Tomorrow you only have to fill the Gemini column + the strategic-read paragraphs.

**Block 3: Pre-write the LinkedIn / X teaser (5 min)**

Open a draft. Paste this template:

```
Just watched the Google I/O 2026 keynote.

3 things I'm taking away as a CS grad heading into the AI-engineering job market:

1. [FLAGSHIP_NAME]: [one line]
2. Vertex AI Agent SDK: [pricing vs Claude Agent SDK — one line]
3. [ONE_SURPRISE]: [one line]

Full 1-page comparison (Gemini vs Claude Opus 4.7 vs GPT-5.5) here: [LINK_TO_BLOG_OR_GIST]

This morning's pre-keynote take was [LINK_TO_YOUR_TIMESTAMPED_MONDAY_POST]; my call for tonight: [YES/NO/PARTIAL] on whether Google has closed the frontier-capability gap to Mythos + GPT-5.5.

#GoogleIO2026 #Gemini #Anthropic #AIEngineer #ForwardDeployedEngineer
```

**Block 4: Toggle the Agent SDK credit setting (5 min)**

Per [TECHSY](https://techsy.io/en/blog/claude-agent-sdk-credit) — the Agent SDK credit pool that activates June 15 **doesn't auto-activate**. You have to **manually toggle it on once in your Anthropic account settings.** If you don't, on June 15 your `claude -p` / Agent SDK / GitHub Actions calls will *fail with a billing error* instead of drawing from the new pool. The fix is one click but you have to do it ahead of time.

**Block 5: Schedule the Tuesday afternoon block (5 min)**

In your calendar, block:
- **10:00 AM PT – 1:30 PM PT** — I/O keynote viewing + live notes
- **2:00 PM – 3:30 PM PT** — Fill in the Gemini column + write the strategic read
- **3:30 PM – 4:00 PM PT** — Publish LinkedIn / X / personal blog
- **4:00 PM – 5:00 PM PT** — Apply to 1 Google Cloud FDE role using the published comparison as a proof point in your cover note

Total Tuesday afternoon: 4 hours. Total Monday pre-stage: 45 minutes. Total deliverable: **your single most-shared LinkedIn post of the month, an FDE application in-flight, and the comparison doc that recruiters will find when they search "Gemini 4 vs Claude" all week.**

### The live-note template (use during the keynote)

Same as [yesterday's `03` §4](../2026-05-17/03-practical-skills-and-tools.md#4-io-viewing-playbook). Open it in a side panel during the keynote. Don't try to listen *and* type beautifully — just dump structured one-liners under each header. Clean up during the 2 PM block.

**Sources:**
- [Google I/O 2026 official livestream link](https://io.google/2026/) `[primary]`
- [Anthropic — Pricing](https://platform.claude.com/docs/en/about-claude/pricing) `[primary]`
- [Anthropic — Introducing Claude Opus 4.7](https://www.anthropic.com/news/claude-opus-4-7) `[primary]`
- [Simon Willison — Code w/ Claude live blog (template reference)](https://simonwillison.net/2026/May/6/code-w-claude-2026/) `[primary]`
- [Yesterday's I/O viewing playbook](../2026-05-17/03-practical-skills-and-tools.md#4-io-viewing-playbook) — full live-note template

---

## 2. Toggle Your Agent SDK Credit Setting Tonight — Five-Minute Job, Bites Hard on June 15 If You Skip It {#2-agent-sdk-toggle}

**The setting:** Starting **June 15, 2026**, all Agent SDK + `claude -p` + GitHub Actions usage on your Pro / Max-5x / Max-20x plan draws from a **separate monthly Agent SDK credit pool** ($20 / $100 / $200 respectively, billed at API list rates).

**The detail nobody talks about:** **The credit pool doesn't auto-activate.** You have to **manually toggle it on once** in your account settings. If you don't toggle it before June 15, your programmatic Claude calls *will fail* on that day — they won't fall back to your interactive plan; they'll error out.

### The 5-minute fix

1. Go to [claude.com/account](https://claude.com/account) → Settings → Billing
2. Find the **"Agent SDK credit"** toggle (live in account settings as of mid-May 2026 per TECHSY)
3. Click **enable**
4. Confirm the credit allocation shows the right tier for your plan
5. Save and screenshot the confirmation for your records

That's it. You will not have to think about it again until you exceed your monthly credit (at which point you can choose to pay overage at API list rates or stop programmatic calls).

### Why this is the highest-ROI 5 minutes in this entire week's edition

- **Cost of forgetting:** every `claude -p`, every GitHub Action calling Claude, every Agent SDK script, every Cowork job *fails silently on June 15 morning*. You don't find out until your CI starts failing or your scheduled jobs don't run. Then you spend a panicked hour reading docs.
- **Cost of doing it now:** 5 minutes. Reversible.
- **Compounding benefit:** every other person on your team / in your projects who hasn't done this will also be blocked on June 15. You'll be the only one whose pipelines still run. *That's the kind of operational discipline that gets noticed in FDE interviews.*

**Sources:**
- [Anthropic — Agent SDK overview](https://code.claude.com/docs/en/agent-sdk/overview) `[primary]`
- [Anthropic — Use the Claude Agent SDK with your Claude plan (Help Center)](https://support.claude.com/en/articles/15036540-use-the-claude-agent-sdk-with-your-claude-plan) `[primary]`
- [InfoWorld — Anthropic puts Claude agents on a meter across its subscriptions](https://www.infoworld.com/article/4171274/anthropic-puts-claude-agents-on-a-meter-across-its-subscriptions.html) `[secondary]`
- [TECHSY — Claude Agent SDK Credit Explained (June 15, 2026)](https://techsy.io/en/blog/claude-agent-sdk-credit) `[analysis]` (the manual-toggle detail)
- [Apidog — How to Use the Claude Agent SDK With Your Claude Plan](https://apidog.com/blog/claude-agent-sdk-with-claude-plan-setup-guide/) `[analysis]`

---

## 3. Watching Code w/ Claude London Day 1 Livestream — How To Get Maximum Signal From an Inconvenient Time {#3-london-livestream}

**The challenge:** Code w/ Claude London Day 1 keynote livestreams Wednesday **at ~9 AM BST**, which is **1 AM PT / 4 AM ET**. That's an antisocial hour for US-based viewers. The recording will go up later — but the recording is competing with I/O fallout and Meta-layoff news, so you have to be *intentional* about extracting value if you watch async.

### Option A: Watch the opening keynote live (recommended)

Set your alarm for **12:45 AM PT** on Wednesday. Watch the opening 60–75 minutes (the keynote panel with Ami Vora + Boris Cherny + Angela Jiang). Take notes using the same live-note template you'll have already installed for I/O. Then go back to sleep.

**Why:** Three reasons:
1. **You're awake while the chat is alive.** Anthropic engineers and your potential future colleagues are *also* in chat. Ask one substantive question; get noticed.
2. **You can publish a 200-word read by 7 AM PT.** That's 4–6 hours *before* the recording goes up. You become the single sharpest take in your feed Wednesday morning, while everyone else is still waiting for the YouTube upload.
3. **It's the same 75-minute window** as the recording will be — but the social capital from watching live is non-fungible.

### Option B: Watch the recording at 6 AM PT Wednesday (recording typically posts within 2–4 hours of conclusion)

If 12:45 AM PT is genuinely impossible, set the alarm for 6 AM PT and watch the (likely-already-posted) recording at 2x. You'll be 5–6 hours behind the live cohort but still ahead of the US-business-hours wave.

### What to extract (regardless of which option)

For each of the three keynote speakers, capture:
- **One sentence each** on the most important new SDK capability they announced
- **One sentence** on the public customer story they highlighted (Asana, Cursor, GitHub, Replit, or Vercel)
- **One sentence** on what they did or didn't say about Vertex Agent SDK / Gemma 4 (Anthropic's response to I/O is the implicit subtext of the entire conference)

Then write **one paragraph** of strategic read: "*The 3 things Anthropic just shipped at Code w/ Claude London that change how I think about agentic-coding economics post-I/O are: ____, ____, ____.*"

Publish to LinkedIn / X / personal blog by 7 AM PT Wednesday.

**Sources:**
- [Anthropic — Code with Claude London (event landing page)](https://claude.com/code-with-claude/london) `[primary]`
- [Anthropic — Code with Claude SF blog (precedent format)](https://claude.com/blog/code-w-claude-sf-2026-sf) `[primary]`
- [TechFastForward — Anthropic Is Staging a Developer Revolution in Three Cities](https://techfastforward.com/articles/anthropic-code-with-claude-developer-conference-sf-london-tokyo-2026) `[analysis]`
- [Simon Willison — Code w/ Claude SF live blog](https://simonwillison.net/2026/May/6/code-w-claude-2026/) `[primary]` (format template for your London write-up)

---

## 4. The Three-Sentence Cover-Note Template for FDE / Integration-Engineer Applications {#4-fde-cover}

**Why now:** With **+800% YoY FDE postings** (yesterday's [`05`](../2026-05-17/05-career-and-startup.md#1-fde-800-percent)) + Meta-layoff-driven candidate supply spike Wednesday + Google Cloud FDE hiring wave likely after tomorrow's keynote, **the cover-note bottleneck for applications becomes binding.** You need a 60-second template you can adapt to each role.

### The template (memorize verbatim, then adapt 3 sentences per company)

```
Three artifacts that demonstrate the FDE-shaped operating discipline I'd bring to [COMPANY]'s customers:

(1) A public MCP server [LINK] — [3-word description of which API it wraps and what it does], shipped with a 5-case eval and 30-second demo gif.

(2) A `CLAUDE.md` install across my active project repos [LINK to ME.md or a representative repo] — Karpathy's 4-rule template adapted for [my stack], used to ship [X commits / Y projects].

(3) A daily AI-news brief organized around the FDE / Integration-Engineer lane [LINK to this repo] — written to the Job · Startup · Insight lens; references [SPECIFIC PRIMARY SOURCE FROM YOUR EDITION] that I'd quote in a customer-deployment conversation.

Specific to [COMPANY]: [TWO SENTENCES on a specific customer or vertical they've publicly committed to, and what your existing portfolio implies about your fit for that wedge.]
```

### Example adaptations (use as priming, not literal text)

**For Anthropic FDE — Applied AI:**

> Specific to Anthropic: I've committed to the Anthropic agentic stack as my portfolio focus through 2026 (see ME.md) and shipped under that constraint for the past 30 days. With the June 15 Agent SDK metering change, I've already audited my own programmatic spend, enabled prompt caching, and toggled the Agent SDK credit setting — the exact discipline I'd bring to a customer trying to optimize their Claude bill in week 1 of an engagement.

**For Google Cloud FDE — GenAI:**

> Specific to Google Cloud: my Monday-evening pre-staged Gemini vs Claude vs GPT comparison ([LINK]) was published 90 minutes after the I/O keynote, with a structured read on the Vertex AI Agent SDK economics relative to Claude's metered pool. That's the exact analytical surface I'd bring to a customer evaluating Vertex against the Anthropic stack — and I'd start by pricing the per-task economics on their actual workload, not by quoting list prices.

**For Sierra / Decagon / Cognition / Customer Eng:**

> Specific to [COMPANY]: I've been tracking the multi-agent topology research (DyTopo, Successor-Representation Spectrum, "Bayes-consistent orchestration") and the production-trajectory-verification literature (TrajAD, Agent Reliability framework, Constraint Decay). The 60-second read I'd bring to a customer-engineering call: *"under matched compute, single agents beat multi-agent — but the gap is closing as dynamic-topology rewiring and runtime trajectory verifiers move into production. Here's the 3 questions I'd ask before recommending an architecture for your use case."*

**Sources:**
- [Yesterday's `05` FDE landscape](../2026-05-17/05-career-and-startup.md#1-fde-800-percent) `[primary]`
- [Sundeep Teki — Definitive Guide to Forward Deployed Engineer Interviews 2026](https://www.sundeepteki.org/advice/the-definitive-guide-to-forward-deployed-engineer-interviews-in-2026) `[analysis]`
- [Datainterview — Forward Deployed Engineer Interview Prep (2026)](https://www.datainterview.com/blog/forward-deployed-engineer-interview-prep) `[analysis]`
- [Hashnode — Complete 2026 Guide to the Forward Deployed Engineer](https://hashnode.com/blog/a-complete-2026-guide-to-the-forward-deployed-engineer) `[analysis]`
- [Anthropic — Forward Deployed Engineer, Applied AI](https://job-boards.greenhouse.io/anthropic/jobs/4985877008) `[primary]`
- [Google Careers — Forward Deployed Engineer II, GenAI, Google Cloud](https://careers.google.com/jobs/results/120977245454901958-forward-deployed-engineer/) `[primary]`

---

## 5. Monday-Night Action Checklist {#5-monday-checklist}

In priority order. Time-cap: **60 minutes total**.

1. **(5 min) Toggle the Agent SDK credit setting** at [claude.com/account](https://claude.com/account) → Settings → Billing. → §2 above. *Reversible. Bites hard on June 15 if skipped.*
2. **(15 min) Create the comparison-doc skeleton** with Claude Opus 4.7 + GPT-5.5 rows pre-filled. → §1 Block 1+2.
3. **(5 min) Pre-write the LinkedIn / X teaser post template** with placeholders. → §1 Block 3.
4. **(5 min) Block 10 AM–1:30 PM PT + 2 PM–5 PM PT** Tuesday on your calendar. → §1 Block 5.
5. **(5 min) Set 12:45 AM PT Wednesday alarm** for Code w/ Claude London. → §3 Option A.
6. **(20 min) Apply to 1 FDE role** using the §4 cover template. Suggested: Google Cloud FDE GenAI or Anthropic FDE Applied AI. *Time the submission for ~9 PM PT Monday — recruiters' Tuesday-morning inboxes are quieter than the Sunday-night flood.*
7. **(5 min) Re-read [yesterday's TL;DR](../2026-05-17/00-tldr.md)** if you didn't yesterday — it sets up everything in tomorrow's keynote.

When you finish this, you'll have:
- **One billing landmine defused** (June 15 won't surprise you)
- **One pre-staged artifact** that becomes the most-shared LinkedIn post of your week
- **Two calendar blocks** locked for the highest-leverage hours of the month
- **One FDE application** in-flight ahead of the Tuesday afternoon Vertex-wave rush
- **One Code w/ Claude alarm** set so you don't sleep through the Wednesday counter-programming moment

**Total time tonight: 60 minutes. Total deliverable through Wednesday morning: ~6 hours of high-leverage work that puts you 24–48 hours ahead of your career-cohort.**

---
