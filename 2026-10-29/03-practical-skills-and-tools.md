# Practical Skills & Tools — 2026-10-29

What to ship this weekend and what to stop paying for next week. The agent-worker tier now has four distinct price points, which turns "routing" from an abstract design choice into a napkin-math exercise with four numbers.

Tags: `#router #claude #openai #google #weekend-artifact #cost-telemetry #computer-use`

---

## 1. Rebuild the router artifact — the four-model agent-worker tier (ship this weekend) {#1-router-v2}

**The setup:** The 2026-09-10 edition framed "model fatigue" with four frontier models in one week. Since then, the **agent-worker tier** (sub-$5-per-M-output, used as the per-step model in a multi-step agent loop) has consolidated to **four options**:

| Model | In / Out ($/M tokens) | Strength | Weakness |
|---|---|---|---|
| **Claude Haiku 5.5** (Anthropic) | $0.10 / $0.50 | Cheapest; 72.4% OSWorld 2.1 subset; configurable effort level; browser-use default | Weaker on long-form reasoning; shortest context among the four |
| **Gemini 4 Argon** (Google, intro period) | $2 / $10 | 1M-token output; strong cyber-defense framing; Antigravity integration | Intro pricing ends ~Nov 30, 2026 (reverts to $4/$20); limited availability (Fairwind trusted testers + Pro/Ultra) |
| **GPT-6.1 Terra** (OpenAI, standard tier) | $1 / $5 | 3× faster agents vs predecessor; computer-use first; 50% cheaper than Sol | Not available in ChatGPT Chat; tier structure (Flex/Standard/Fast) adds routing complexity |
| **Claude Opus 5.5 effort=low** (Anthropic) | ~premium with low-effort knob | Best planner at low effort; same model as the top-tier planner | Expensive per call even at low effort; only makes sense in planner slot |

**The artifact — ship it this weekend:**

1. **1 Python script** (`router.py`): takes a user task + budget, picks the right model per step. Uses the OpenAI, Anthropic, and Google SDKs; one adapter each.
2. **1 benchmark run** (`benchmark.ipynb`): 20 agent tasks across three difficulty tiers (easy toolcall, medium reasoning, hard planning+toolcall). Report per-task cost + success rate for all four models + a routed hybrid.
3. **1 blog post** (`README.md`): 500 words. Lead with the napkin math: "a 100-step agent workflow at $0.50 budget: here's how each model performs."
4. **Publish:** GitHub + a 60-second demo gif. Tweet-length teaser: `"four frontier agent-worker models. one router. one budget. results below."`

**Why ship this specific weekend:** Terra shipped Oct 26; the four-model price-point map is three days old. **Being first to publish the empirical "which model wins when" study carries recruiter signal that decays weekly.** The 2026-09-10 router mapped three models; this version is the real version.

**Risk:** Argon intro pricing ends Nov 30. If you publish the benchmark against Argon's $2/$10, note it clearly; the post-promo $4/$20 numbers will double Argon's cost column.

**Sources:**
- Haiku 5.5 pricing — [Anthropic model page](https://www.anthropic.com/claude/haiku) `[primary]` (via 2026-10-14 edition)
- Argon pricing — [Google — "Google launches Gemini 4 Argon for cyber defenders first"](https://t2online.in/tech/tech-news/google-launches-gemini-4-argon-for-cyber-defenders-first/2008385) `[secondary]`
- Terra pricing — [BleepingComputer — GPT-6.1 Terra with 50% lower pricing](https://bleepingcomputer.com/news/artificial-intelligence/openai-launches-gpt-61-terra-with-3x-faster-ai-agents-50-percent-lower-pricing) `[secondary]`
- Opus 5.5 effort-level API — 2026-10-21 edition
- OSWorld 2.1 subset benchmark (Haiku 5.5) — [AlphaSignal / Anthropic](https://alphasignal.ai/) `[aggregator]`

### Why it matters to you

- **Job lens:** The router artifact goes directly into every Anthropic Solutions / FDE / Applied AI interview you'll do between now and February. The specific interview question it answers: *"show me a cost-aware agent design you've shipped."* Right now, nobody is answering that question with the four-model comparison the market just handed us. **Ship this and you're the only candidate with the empirical table.**
- **Startup lens:** The router is also a shippable product. If you have 20 Claude-first developer followers on X, the GitHub repo gets 50–150 stars inside a week. If it gets 500 stars, you have a credible pre-seed pitch for "cost-aware agent routing as a product" that is 100% directly relevant to the §1 S-1 reading (consumption-metered revenue → everyone is cost-sensitive).
- **Insight:** Routing-as-skill is now explicitly the FDE skill of this cycle. Every "which model" conversation at a $100K+ Claude account resolves to a routing decision, which resolves to a benchmark table nobody has run yet because the four price points are three days old. **Be the person with that table.**

---

## 2. Computer-use just repriced — Terra at $1/$5 vs the alternatives {#2-computer-use}

**The setup:** Three computer-use-capable frontier models are now shipping:
- **Claude Haiku 5.5** — default in Claude Code; strong browser-use loop; $0.10/$0.50.
- **GPT-6.1 Terra** — explicitly computer-use-first positioning (Oct 26); $1/$5. Reported 3× faster agents vs predecessor.
- **Gemini 4 Argon** — software-engineering-first in Antigravity; computer-use via tool-call layering; $2/$10 intro.

**What repriced this week:** Terra is now the cheapest *non-Anthropic* computer-use model. For teams that want multi-vendor exposure (every $100K+ Claude account), Terra is the OpenAI default for computer-use workloads. **Haiku 5.5 remains the cheapest option overall by 10×**, but Terra is the first OpenAI model that reads as "we can afford to run this across every PM-tool-automation workflow."

**Immediate practical implication for your Claude Code / MCP workflow:**
- **Keep Haiku 5.5 as the default worker in Claude Code.** No reason to change.
- **Add Terra as the fallback for computer-use loops that need OpenAI-ecosystem tool access** (Codex integrations, OpenAI-hosted MCP servers). Specifically useful for `playwright` + `claude code` workflows if you want A/B comparison.
- **Reserve Argon for scientific/computational workloads** in Antigravity-integrated setups. The $2/$10 intro is a short window.

**Sources:**
- [EdTech Innovation Hub — OpenAI releases GPT-6.1 Terra with improved computer use](https://edtechinnovationhub.com/news/openai-releases-gpt-61-terra-with-50-lower-api-pricing-and-improved-computer-use) `[secondary]`
- [AICatchup — OpenAI GPT-6.1 Terra: Availability, Computer Use, and API Pricing](https://aicatchup.com/news/openai-gpt-6-1-terra) `[analysis]`
- [AICybr — GPT-6.1 Terra: 1M Context, Computer Use and Coding Benchmarks](https://aicybr.com/blog/openai-gpt-6-1-terra-api-pricing-computer-use-benchmarks) `[analysis]`

### Why it matters to you

- **Job lens:** The specific interview question Terra enables: *"how would you design a multi-vendor computer-use agent that stays under $1 per task?"* The answer involves routing between Haiku 5.5 (80% of calls) and Terra (20% of calls, specifically for OpenAI-ecosystem tool access), with a budget check at each step. Have the architecture diagram ready.
- **Startup lens:** Computer-use agents are the single most under-served workflow category right now. Teams at $100K+ Claude accounts routinely say "we would deploy Claude to automate X browser workflow if we trusted it won't do Y." The gap between "model can do computer use" and "we trust it in production" is a product-shaped problem: audit trail, intervention points, replay-and-rollback. **Three-month-old startup opportunity.**
- **Insight:** Computer-use is at the "demo works, production is unsafe" stage of the model-capability curve. The person who writes the first great post on *"what breaks in a production computer-use agent and how to catch it"* becomes the authority. **Weekend writing exercise if you have a Claude Code screen-recording setup**: 10 failure modes, 3 recovery patterns, 500 words.

---

## 3. Stop paying for these this week {#3-cost-telemetry}

**The S-1 made every reader cost-conscious.** If you've been slow on your monthly AI-spend audit (the 4th of the month, per `ME.md` personal rules), use the roadshow news as the forcing function. Three specific cancellations to consider:

- **Any ChatGPT Plus subscription you have in parallel with a Claude Max or Pro.** The 2026-10-14 edition's "effort levels + Haiku 5.5" repricing already made this redundant for most workflows; Terra being developer-tier (not consumer-tier) means Plus's one remaining lever (model access) has shifted toward the API. **If you're using ChatGPT Plus for coding, migrate to Codex ($20/mo bundled with Pro) or ChatGPT Work (if you have institutional access).**
- **Any Gemini AI Pro subscription if you're not on Antigravity or using Argon's 1M-token output.** The Argon intro period ends Nov 30; a subscription you're not using monthly is a $20/mo bleed.
- **Any Perplexity Pro / Copilot Pro subscription that duplicates a Claude Max or ChatGPT Pro.** The consolidation move happens post-S-1: labs will be aggressive on bundling to beef up the subscription-revenue line (currently 20% of Anthropic's revenue mix). Expect Max tier perks to expand in Nov/Dec.

**Keep what matters:**
- **Claude Max** — base layer; Opus 5.5 + Duet waitlist access.
- **Codex / ChatGPT Pro** — Terra access + Codex specifically for OpenAI-ecosystem code tasks.
- **GitHub Copilot** — if your team uses it (habit cost of swapping > savings).

### Why it matters to you

- **Job lens:** Writing up your own cost audit is one of the public artifacts on your `ME.md` roadmap. The specific line to write: *"I audited my own AI spend monthly and dropped 2 subs after Anthropic's S-1 made consumption pricing explicit"* — that's an operator-tone sentence that reads as right-profile for Anthropic Applied AI / Solutions.
- **Startup lens:** The retail subscription-audit problem is a product. "Spindl for AI subs" is three-months-shippable; the data model is: connect accounts, aggregate monthly spend, surface overlap, suggest cancellation. Likely consumer, likely low-ACV, likely sellable to one of the agent-app vendors as an acquisition target.
- **Insight:** Consumption pricing + public market exposure (ANT ticker) means **the labs will reprice subscriptions every quarter in response to API pricing**. Being on top of your own monthly audit is both a job-signal and a startup-signal. Make it a 15-minute monthly ritual, not an annual spring clean.

---

## 4. Weekend artifacts — ranked by shippable-this-weekend {#4-weekend}

Three options for your Oct 31–Nov 1 weekend; one is the main; two are swaps.

1. **(Main — ship this)** [Four-model router artifact](#1-router-v2) with GitHub + benchmark + README. ~8 hours.
2. **(Swap A)** [Four computer-use failure modes writeup](#2-computer-use) — 500-word post + 3 recorded failure clips. ~4 hours. Right swap if you don't want to pay for all four model credits.
3. **(Swap B)** [Personal AI-spend audit writeup](#3-cost-telemetry) — public gist with your actual monthly numbers, redacted. ~2 hours. Right swap if you want a smaller artifact to pair with the main — do both this weekend if time allows.

**Publishing checklist (any of the three):**
- [ ] GitHub repo with a README that leads with the result, not the setup.
- [ ] One tweet-length teaser + the GitHub link.
- [ ] One cold-email line to drop into Anthropic Solutions / OpenAI FDE applications ("I shipped X this weekend; link below").
- [ ] One screenshot or 60-second gif for the top of the README.
