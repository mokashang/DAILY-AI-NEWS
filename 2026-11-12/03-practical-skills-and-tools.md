# Practical Skills & Tools — 2026-11-12

Two operational shifts this week that change tooling defaults. **(1) Claude Code v2.1.321 defaults to Fable 5.2** — the tier under Opus, above Haiku, with a 1M-token context window and better price/perf than Opus for most workloads. **(2) ChatGPT Advanced/Standard Voice retire Dec 11** and GPT-Live replaces them — a three-week migration window. Together these shift the practical stack in ways you should bake into the router artifact, the voice-demo artifact, and your interview answers to "what's your default model?"

Tags: `#claude-code #fable #effort-levels #gpt-live #router`

---

## 1. Claude Code defaults to Fable 5.2 — rebuild the router this weekend {#1-fable-52-default}

**What shipped (2026-11-09 to 2026-11-10):**

- **Claude Fable 5.2** (`claude-fable-5-2`) — 1M-token context, 128K max output, June 2026 knowledge cutoff. General API availability.
- **Claude Mythos 5.2** (`claude-mythos-5-2`) — same specs; **verification-gated** for Cyber + Life Sciences Verification Programs. Pricing: **$8 input / $40 output per 1M tokens** (reported by third-party trackers; verify at platform.claude.com).
- **Claude Code v2.1.321** — Fable 5.2 is now the **default model** for new sessions.

**New model lineup effective this week (three-rung + effort-level-tunable):**

| Rung | Model | Default use | Price band |
|---|---|---|---|
| Premium | Opus 4.8 / 5.5 | deep reasoning, long-horizon planning, hardest research tasks | high |
| Workhorse | **Fable 5.2** | coding, agentic workflows, most Claude Code work | mid |
| Cheap worker | Haiku 5.5 | browser-use, subagents, high-volume classification | $0.10/$0.50 per 1M |
| Verification-only | Mythos 5.2 | restricted cyber / life-sciences evaluation | $8/$40 per 1M |

**Effort levels (reminder of the five-level ladder):** `low` · `medium` (API default) · `high` · `xhigh` · `max`. Claude Code defaults to **xhigh** per community reporting; override with `/effort`. Anthropic recommends **draft on low, verify on high** as the default pattern for agentic work ([dsebastien.net](https://www.dsebastien.net/2026-10-04-claude-effort-levels-draft-on-low-verify-on-high/) `[analysis]`).

**Sources:**
- [Platform.claude.com — Fable 5.2 overview](https://platform.claude.com/docs/en/models) `[primary]`
- [Platform.claude.com — Mythos 5.2 overview](https://platform.claude.com/docs/en/models/mythos-5-2/overview.md) `[primary]`
- [Platform.claude.com — Effort levels](https://platform.claude.com/docs/en/build-with-claude/effort) `[primary]`
- [AI-TLDR — Mythos 5.2 model card](https://ai-tldr.dev/models/claude-mythos-5-2/) `[aggregator]`
- [LLM Reference — Claude Mythos model family](https://www.llmreference.com/model-family/claude-mythos) `[aggregator]`
- [Anthropic Blog — Opus 4.7 best practices with Claude Code](https://claude.com/blog/best-practices-for-using-claude-opus-4-7-with-claude-code) `[primary]`
- [VincentQiao — Claude Code /effort: Make AI Think Harder (or Faster)](https://blog.vincentqiao.com/en/posts/claude-code-effort/) `[analysis]`

### Why it matters to you

- **Portfolio action — rebuild the router artifact THIS weekend.** Last month's router (`03` §2 from 2026-10-14) was built around Haiku 5.5 as worker + Sonnet / Opus as reasoning tier. The new topology:
  - **Tier A (planning / long context):** Fable 5.2 at `high` effort
  - **Tier B (execution / tool-heavy):** Fable 5.2 at `medium` effort
  - **Tier C (subagent / bulk work):** Haiku 5.5 at `low` effort
  - **Tier D (hard reasoning / uncertain):** Opus at `xhigh` effort (rare — < 5% of calls)
  - **Verification / cyber:** Mythos 5.2, access-gated
- **Draft-on-low-verify-on-high pattern.** The best-documented 2x-cost-saving pattern this month:
  1. Prompt at `low` or `medium` to generate the first pass.
  2. Re-prompt with the first pass + "verify or correct" instruction at `high`.
  3. For *most* tasks, the verification pass either confirms or finds a single concrete issue — cheaper than generating at `high` from scratch, and often higher quality because the model has a concrete target to critique.
- **Interview talking point:** When asked "what's your default Claude model?", the right 2026-11 answer is **"Fable 5.2 at medium effort, with a routing fallback to Opus at xhigh for hard reasoning. Haiku 5.5 for subagents. The effort-level knob now carries most of the tradeoff that model choice used to."** This is a 2026-Q4 answer; a candidate still saying "Sonnet" is behind by two generations.

### Weekend artifact spec

**The router artifact v3 (publish by Sunday night):**
- **Interface:** single prompt + optional context + tier hint
- **Output:** call plan (which model, which effort) + rationale (1 sentence) + fallback path
- **Instrumentation:** per-call token + $ cost, cumulative session budget, and a `/draft-then-verify` toggle
- **Repo structure:** `/router-v3/` with README, `model_cards.json`, `effort_map.json`, `routes.yaml`, demo gif
- **Portfolio placement:** pin to GitHub profile; link from LinkedIn as "Claude router v3 (Fable 5.2 default)"

→ Cross-link: [`05` §3 interview talking points](./05-career-and-startup.md#3-today-plan).

---

## 2. GPT-Live replaces ChatGPT Advanced/Standard Voice Dec 11 — migrate audio-agent demos by Nov 25 {#2-gpt-live-migration}

**What happened:** [Releasebot](https://releasebot.io/updates/openai/chatgpt) reports that OpenAI will **retire ChatGPT Advanced Voice and Standard Voice on December 11, 2026**, replacing both with **GPT-Live** (the real-time multimodal voice primitive). Three-week notice is unusual.

**Side notes:**
- `gpt-5.5-cyber-preview` API model retires **Feb 1, 2027**.
- Images 2.6 (Nov 4): adds GIF creation + saved reference images + 2 new API models + "faster generation."

**Sources:**
- [Releasebot — ChatGPT Updates](https://releasebot.io/updates/openai/chatgpt) `[aggregator]`
- [AI Weekly — OpenAI News Nov 5](https://aiweekly.co/ai-news-today/openai-news) `[aggregator]`

### Why it matters to you

- **Portfolio action — migrate any voice-agent demo you have to GPT-Live before Nov 25.** A demo recorded on a stack that was deprecated 2 weeks after demo day reads as "late" in interviews. A demo recorded *during the deprecation window on the new stack* reads as "keeps current." Same artifact, very different interview signal.
- **New skill to pick up this quarter: real-time multimodal voice agent patterns.** GPT-Live, paired with Claude Meetings (see `01` §3), means the "live-call agent" lane has two production-quality platforms. Portfolio piece: an **"interview-coaching live voice agent"** — audible-feedback + transcript + live-notes-whiteboard — built on both platforms side-by-side would be a standout portfolio piece going into Q1 2027 recruiting cycles.
- **Insight:** OpenAI shipped **one** voice primitive (GPT-Live) to **replace two** (Advanced + Standard Voice). Anthropic shipped **one** meetings primitive (Claude Meetings) alongside Sheets + Whiteboards. The pattern: **both labs are consolidating around unified primitives rather than product-tier splits.** Fewer SKUs = clearer story to developers + cleaner API surface = faster ecosystem growth. Your takeaway: if you're building on either stack, assume 2–3 primitives per surface (voice, chat, canvas, sheet, dashboard) and build *across* them, not within one.

---

## 3. Building on Claude Workplace Suite (beta surface) — early-access patterns {#3-workplace-beta}

**What's available Nov 10+:**
- Claude Meetings beta (Team + Enterprise) — Google Meet integration
- Claude Sheets beta (paid plans) — web/desktop/mobile, Excel export
- Claude Whiteboards beta (paid plans) — in-Meetings mode
- Claude Data GA
- Adobe / Atlassian / HubSpot full-app plugins

**Early-access patterns to try this weekend:**

### (a) Meetings → task generator → Sheets logging
Pattern: Join a recurring team meeting with Claude Meetings. Have it generate action items. Pipe action items to a Claude Sheet for cross-meeting rollup. Rollup becomes the source for your weekly status.

### (b) Whiteboard-driven agent planning
Pattern: Start a Whiteboard, sketch an agent flow, prompt Claude to turn the Whiteboard into a plan + code scaffolding. This is Whiteboards as a **spec-then-code** primitive rather than a brainstorming surface.

### (c) Sheets as a cheap eval harness
Pattern: Multi-tab Sheet — tab 1: test cases; tab 2: model outputs (via formula / LLM call); tab 3: pass/fail per row; tab 4: aggregates. For portfolio-grade eval work this is a 30-minute harness vs. a day building a proper eval repo. It won't replace rigorous eval infrastructure, but for **"show me you can eval something fast"** interview prompts it's a strong artifact.

### (d) Dashboards ("Data") as a client-delivery surface
Pattern: Many Frontier Academy partner firms will standardize on Claude Data for client-delivered dashboards. If you're interviewing at one of them, **build one Claude Data dashboard** and demo it — this is the single portfolio piece most aligned to the Academy residency deliverable shape.

**Source:** [Anthropic Meetings / Sheets / Whiteboards announcement coverage](https://aiweekly.co/alerts/anthropic-rolls-out-claude-sheets-meetings-and-whiteboards) `[aggregator]` · [Anthropic Enterprise](https://www.anthropic.com/enterprise) `[primary]`

### Why it matters to you

- **Portfolio timing:** The beta window (now–Q1 2027) is when Anthropic will **cite external builders** in launch retrospectives. Ship one Workplace-Suite artifact publicly, get it noticed, and you can cite it in the Solutions/FDE interview as "I've already built on the stack you ship." This is the fastest-moving portfolio-opportunity window since Claude Code v1 launched.
- **Startup wedge reminder:** The best-shape Workplace-Suite startup this quarter is **vertical template packs** (finance ops, HR, RevOps) for Claude Sheets. No API moat but a 60-day revenue cycle — sold on Gumroad / Lemon Squeezy at $20–$100/pack.

---

## 4. Ambient tooling updates worth noting

- **Anthropic Admin API** — new sign-out endpoint lets you force-logout Enterprise members. Useful for incident response + employee offboarding.
- **Messages API** — server-side conversation threads (beta) — removes the need for local state caching in multi-turn agents.
- **Deprecation:** Claude Opus 4.8 fast mode removed Nov 30.
- **Enterprise security center** with inference hooks — audit-log webhooks + runtime policy evaluation. Security-adjacent engineers: this is your integration surface.

**Source:** [Releasebot — Anthropic](https://releasebot.io/updates/anthropic) `[aggregator]` · [Releasebot — Claude Developer Platform](https://releasebot.io/updates/anthropic/claude-developer-platform) `[aggregator]`

---

## 5. One-paragraph TL;DR for the tooling week

Your Claude Code default is now **Fable 5.2 at xhigh** out of the box; override to `medium` for most agentic tasks and only reach for `high`/`xhigh` when you measure a quality gain. Haiku 5.5 remains the subagent-and-browser-use worker, now with cheap-tier pricing that makes multi-step verification affordable. Opus is reserved for rare hard-reasoning calls. On the OpenAI side, move your voice demos to GPT-Live by Nov 25. On the workplace side, ship one Claude Sheet or Claude Data artifact publicly this weekend and link it from your portfolio.
