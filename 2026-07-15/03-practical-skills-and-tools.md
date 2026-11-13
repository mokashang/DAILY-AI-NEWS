# Practical Skills & Tools — 2026-07-15

Three moves you can make today. **First and time-critical:** the [Claude Science $30K credit grant](./01-big-lab-moves.md) closes at end-of-day today — the last-mile checklist below is the difference between a submitted vs. drafted application. **Second:** the **cross-provider prompt-cache lever** got symmetric on July 9 when GPT-5.6 added explicit cache breakpoints — one shared cacheable prefix now cuts token bills on both Claude and GPT paths, if you refactor the prompt template. **Third:** with Codex Micro shipping today and Cowork mobile now GA, the **phone-plus-tactile-surface operating pattern** is finally cheap enough to actually try — a 20-minute setup that unlocks working-while-walking, not just working-while-sitting.

Tags: `#claude-science #grant #prompt-cache #openai #anthropic #cowork #codex #mobile #productivity`

---

## 1. Ship the Claude Science grant application before 11:59 PM tonight {#1-claude-science-grant}

**What:** Anthropic's **Claude Science AI for Science grant program** deadline is **today, Wednesday July 15**. Award notifications go out by **July 31**; funded projects run **September 1 – December 1**.

- **Per-project award:** up to **$30,000 in Claude API credits** + up to **$2,000 additional compute from Modal** for select recipients.
- **Number of projects funded:** ~50.
- **Priority:** biology / biomedical research, but all scientific domains explicitly accepted.
- **Application URL:** claude.com/science.
- **Best submissions open with the *novelty claim* in the first two sentences** — what becomes scientifically possible with frontier AI access that was not possible without it. Everything else is scaffolding.

**Sources:**
- [Anthropic — Claude Science AI workbench for scientists](https://www.anthropic.com/news/claude-science-ai-workbench) `[primary]`
- [Anthropic Help Center — Anthropic's AI for Science Program](https://support.claude.com/en/articles/11199177-anthropic-s-ai-for-science-program) `[primary]`
- [Granted AI — Claude Science: 50 teams, $30K, July 15 deadline](https://grantedai.com/blog/anthropic-claude-science-2026-30k-api-credits-50-projects-july-15-deadline-ai-for-science-researchers-strategy) `[analysis]`
- [TechCrunch — Claude Science bets on workflow, not a new model, to win over scientists](https://techcrunch.com/2026/06/30/anthropics-claude-science-bets-on-workflow-not-a-new-model-to-win-over-scientists/) `[secondary]`

### Do this today (in order)

1. **Novelty first (5 min).** Rewrite your opening two sentences so a non-domain reviewer understands the *specific scientific artifact* that becomes possible with $30K of Claude credits. "We would use Claude to explore X" is a rejection sentence. "With N Claude runs, we will produce the first Y-shaped dataset for Z, enabling the community to compare against a baseline that does not yet exist" is an acceptance sentence.
2. **Cite the workbench (2 min).** Reference the **Claude Science workbench** by name and mention **one specific integration you would use** (protein structure rendering, chemistry package, genome viewer). This shows you've read the launch post, not the aggregator summary.
3. **State the auditable artifact (3 min).** Every figure + every model output + every message history. This is the eval story Anthropic is optimizing the program for; make it explicit.
4. **Budget the credits (5 min).** Show your math: how many runs, at approximately what token count each, at what model tier. **Sonnet 5 workers + Opus 4.7 orchestrator + Haiku 4.5 verifier** is the pattern to name (three-model routing).
5. **Add a lab-partner sentence (2 min).** Even a "co-PI TBD" or an advisor's endorsement counts. Anthropic's grant is signaling into the research community; a wet-lab hook — however light — increases legibility.
6. **Submit early (before 8 PM).** Every application system slows to a crawl in its last two hours. Submit *this afternoon*, then use the evening to add supplementary materials if allowed.

### Why it matters to you

- **Job lens:** Even a *rejected* Claude Science application is a **line on your resume** ("Claude Science 2026 applicant; grant proposal on [topic]"). It also drops your name into Anthropic's grant-review pipeline, which is a real network you cannot buy access to any other way. Referenced in a cover letter for [Applied — Science](./05-career-and-startup.md#2-science-lane) roles it establishes domain fit in one sentence.
- **Startup lens:** A funded project = a **customer-development instrument** for anyone building AI-for-Science infra (eval, orchestration, verification, cost). The 50 funded projects are 50 potential design partners for an unbundled workbench tool.
- **Insight:** Grant-eligibility windows are compounding leverage — one hour of application effort produces a *durable* claim you can cite in interviews, LinkedIn, and future proposals for years. Very few career actions have this multiplier.

---

## 2. Cross-provider prompt-cache: one prefix, symmetric savings {#2-cache-lever}

**What:** GPT-5.6 (GA July 9) added **explicit prompt-cache breakpoints + 30-minute minimum cache life** — the same primitive Anthropic shipped for Claude in Q1. That means the same **cacheable-prefix template** can save tokens on *both* provider paths simultaneously, if you refactor the prompt shape.

**Cost lever math (typical):**
- Cached input tokens on Claude: ~**10% of standard input cost** (Sonnet 5 promo through Aug 31 = $2/M in, so cached ≈ $0.20/M).
- Cached input tokens on GPT-5.6: ~**10–25% depending on tier**.
- On a 40K-token system prompt hit 50×/day: standard = ~$4/day per user, cached = **~$0.40–$0.80/day per user**. That's the difference between "sustainable" and "we can't afford our own agent."

**How to structure a cache-friendly prompt (works on both providers):**

```
[STATIC PREFIX — cacheable]
  System role / persona
  Immutable domain knowledge
  Style + safety rules
  Tool schema + tool contracts (agent runs)
  Retrieved-context that is stable across the session

[DYNAMIC SUFFIX — not cacheable]
  Turn-specific user message
  Turn-specific tool results
```

Rules of thumb:
- **Never mix a timestamp into the cacheable prefix.** Even a "Today is 2026-07-15" line kills the cache after midnight. Put the date in the suffix or normalize to "today" and inject the true date via tool.
- **Order retrieved context oldest→newest.** New context appended to the *end* of the prefix means the prefix stays hot across turns.
- **Announce your cache breakpoint explicitly** on both providers — do not rely on heuristic caching. On Anthropic use `cache_control` blocks; on OpenAI use the explicit breakpoint the July 9 refresh added.

### Do this tonight

1. Pick one active agent (~any workflow you run daily) — the highest-cost one is best.
2. Print its full system prompt + tool schema; identify the stable prefix (usually ≥80% of tokens).
3. Split into `PREFIX / SUFFIX`. Move any timestamp / user-id / random-seed lines to `SUFFIX`.
4. Add explicit cache breakpoint markers on both providers you use.
5. Run 10 identical queries; log `input_tokens` (uncached) vs `cached_input_tokens`.
6. Post the before/after screenshot in your artifact repo README (this is one of the four things a July-2026 FDE interviewer looks for — [2026-07-11/03 §2 step 6](../2026-07-11/03-practical-skills-and-tools.md#2-artifact)).

**Sources:**
- [OpenAI News (GPT-5.6 refresh)](https://openai.com/news/) `[primary]`
- [Anthropic prompt-caching docs — `cache_control` blocks](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching) `[primary]`
- [buildfastwithai — AI News Today July 14 2026](https://www.buildfastwithai.com/blogs/ai-news-today-july-14-2026) `[aggregator]`

### Why it matters to you

- **Job lens:** "**Cross-provider cost engineering**" is a JD line item at every FDE / Applied AI role in H2 2026 ([2026-07-14/05 §1](../2026-07-14/05-career-and-startup.md#1-fde-quintupled)). A 5-minute demo of "here is the identical prompt, cached on both providers, at 20% of standard cost" is a top-3 impression-maker in a technical interview.
- **Startup lens:** Cheap agents beat expensive agents at the *same task*. If your unit economics don't survive standard-tier input pricing, the answer is almost always prompt refactoring, not switching models. Cache first; switch second.
- **Insight:** The GPT-5.6 refresh is the industry conceding that **cache-friendliness is a first-class product primitive**, not a nice-to-have. The next axis is **cross-provider cache-friendliness as a spec** — expect a proposal (probably from LangChain or Portkey or a neutral spec org) for a canonical prompt-cache format inside the next 60 days.

---

## 3. Phone + tactile surface: the 20-minute mobile-first agent setup {#3-mobile-tips}

**What:** With **Cowork mobile GA (July 7)** and **Codex Micro shipping today**, the "agent on my desk, notification on my phone, tactile shortcut on my Micro" pattern is finally cheap and testable. The two labs' overlapping surfaces let you build the same operational loop in either stack.

**The 20-minute setup (Anthropic-first version):**

1. **(5 min)** Install Claude Cowork on iOS/Android. Sign in. Enable push notifications.
2. **(5 min)** Set up one Routine on Claude Code on the web (see [2026-07-11/03 §2](../2026-07-11/03-practical-skills-and-tools.md#2-artifact)) — the highest-signal one is an **arxiv-scanner-for-your-subfield** or a **PR babysitter** running every 2 hours.
3. **(5 min)** Configure the Routine to *approve-required* on any output-affecting action. When Claude hits a checkpoint, the phone-push arrives; you approve or reject in one tap from your phone.
4. **(5 min)** Screenshot: the phone-notification firing + the `/usage` breakdown before/after.

**Add the Codex Micro (once it ships):** if you prefer the OpenAI stack — same loop, but the accept/reject/rewind primitives map to physical keys on the pad instead of a phone tap. Useful when you're at your desk but multi-tasking (writing, on a call). The pattern is *provider-agnostic*: pick the surface (phone / macro pad / voice) that fits the moment.

### Why it matters to you

- **Job lens:** The **four-frame FDE interview question** — orchestration + real-tool verification + cost + **mobile/operable-anywhere** — has all four boxes checkable after this 20 minutes. That is the artifact-frame from [2026-07-11/03 §2 step 6](../2026-07-11/03-practical-skills-and-tools.md#2-artifact); mobile is the box FDE candidates most often miss.
- **Startup lens:** The team that can operate an agent from *away-from-desk* moves faster than a team that has to be at a screen to approve any state change. If you're a solo founder, this is a real productivity multiplier — the agent runs a 60-minute experiment; you approve or redirect it from a coffee shop.
- **Insight:** Once phone-plus-tactile becomes normal, the **default control surface for an agent is not "chat window in a browser tab"**, it's a mix of surfaces. Anthropic and OpenAI are converging here from opposite directions (Anthropic: consumer/pro mobile-first; OpenAI: pro/hardware-first). Both will end up with all three surfaces. What differentiates in 12 months is *which surfaces have the lowest latency for approve/reject/rewind under real workload*.

**Sources:**
- [TechCrunch — Claude Cowork expands to mobile and web](https://techcrunch.com/2026/07/07/the-coding-agent-wars-are-spilling-into-the-rest-of-the-office-claude-cowork/) `[secondary]`
- [Anthropic — Claude Cowork on mobile & web](https://www.anthropic.com/news) `[primary]`
- [The Next Web — OpenAI Codex Micro](https://thenextweb.com/news/openai-codex-micro-hardware-work-louder) `[secondary]`

---

## Micro-tips (2 min each)

- **Anthropic Claude Code + Claude for Teachers skills repo:** Anthropic published the K-12 skills library on GitHub yesterday. Even non-educators can read it as **the cleanest public example of Anthropic's "skill" primitive shipped in production.** Star the repo; skim two or three skills to internalize the shape. → [`01` §3](./01-big-lab-moves.md#3-claude-for-teachers)
- **TSMC earnings tomorrow (Thu Jul 16):** if you own any AI infra thesis (career or portfolio), read the transcript for **CoWoS capacity signals** — the metric that gates every AI GPU launched this year. → [`01` §1](./01-big-lab-moves.md#1-tsmc-q2)
- **Gemini 3.5 Pro T-2 (Friday Jul 17):** if it lands, spend 30 minutes running the same 5-prompt regression against your current router (Opus 4.7 + Sonnet 5 + Haiku 4.5 + optionally Grok 4.5 or LongCat-2.0). Cheap slot in the router *always* wins if quality holds.
- **Sonnet 5 promo pricing:** $2/$10 through **Aug 31** — **T-47 days** to the standard $3/$15 shift. Every workflow you leave un-cached now overpays after that date.
