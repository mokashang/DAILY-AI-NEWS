# New & Emerging — 2026-06-14 (Sunday)

`#funding #emerging #agents #security #verticals`

What's funded, what's launching, what's quietly changing the map.

---

## 1. Funding-week roundup: agentic-security keeps compounding {#1-funding-week}

The week of **June 8–13** saw the **agentic-security** category continue the compounding pattern that started with [Exaforce $125M on May 12](../2026-05-22/02-new-emerging.md#2-exaforce). Three notable closes plus a Series A at the agentic-infra layer:

| Date | Company | Round | Lead / notable | Category |
|---|---|---|---|---|
| **Jun 10** | **Pi Security** | $35M (stage unspecified, likely Series A) | Undisclosed (SF; see [`aifundingtracker`](https://aifundingtracker.com/ai-startup-funding-news-today/)) | Agentic AI security |
| **Jun 10** | **Trustap** (Dublin) | $10M | Undisclosed | Payments + autonomous agent transactions |
| **Jun 12** | **Poetic** | $50M Series A | Undisclosed | Agentic infrastructure (per `mean.ceo` June digest) |
| (Jun 10) | **Rebar** | $14M Series A | Undisclosed | Vertical AI (HVAC / electrical / plumbing AI OS) |
| (Jun 10) | (Vertical AI) | $43M Series B | Threshold Ventures + NEA co-lead | Industry-vertical agent OS |

**The pattern.** Every public security incident — viral jailbreaks, prompt-injection campaigns, the Fable 5 shutdown — pushes the next agentic-security round. Pi Security is **the cleanest line drawn from the May 22 Exaforce round to this week's news**: builder-side SOC tooling (Exaforce) → AI-system-side hardening (Pi). Expect a third $100M-class round in agentic security by **end of July 2026** — that's the funding-cycle period from incident to mega-round in this category.

**Sources.**
- `[aggregator]` [AI Funding Tracker — Today's Deals & Rounds 2026](https://aifundingtracker.com/ai-startup-funding-news-today/)
- `[aggregator]` [mean.ceo — AI Startup Funding News June 2026](https://blog.mean.ceo/ai-startup-funding-news-june-2026/)
- `[analysis]` [Product Leaders Day — The AI Agent Funding Bubble No VC Will Admit (June 2026)](https://productleadersdayindia.org/blogs/multi-agent-orchestration-news/ai-agent-startup-funding-news.html)

**Why it matters to you.**

- **Job ·** Pi Security / Poetic / the vertical-Series-B class will all post 5–10 engineering roles within 30 days of close. The early-stage cap-table-disadvantage at these companies maps to **less-credentialed-but-shippable candidates** — exactly your delivery-evidence-over-credentials lane.
- **Startup ·** The funding bubble note in the Product Leaders piece is real — **"Series A investors are demanding proprietary multi-agent routing engines and security gates,"** and startups without them face down-rounds. This is also the **wedge for your portfolio**: a mid-stage startup looking for a routing/security gate would hire (or even acqui-hire) for that capability.
- **Insight ·** Every Tier-1 VC now has at least one position in agent security; the consolidation is starting. Look for the first $300M+ agentic-security M&A by Q4 2026.

`#funding #security #agents #soc #series-a`

---

## 2. The model-release pipeline this week: Gemini 3.5 Pro + Grok 5 / SpaceXAI V9-Medium {#2-model-pipeline}

**What's coming.**

- **Gemini 3.5 Pro** (`Google DeepMind`) — slated for **June launch**; **2M-token context**, **"Deep Think" reasoning mode**, frontier multimodal. Prediction markets concentrate the release on **June 23 or June 30**. Pricing tier expected higher than the [Gemini 3.5 Flash $1.50 / $9.00](../2026-05-20/01-big-lab-moves.md) baseline. The Fable 5 shutdown is the **biggest narrative gift Google could ask for** — every Anthropic enterprise customer is now an open bid for Gemini 3.5 Pro the day it ships.
- **Grok 5 / SpaceXAI V9-Medium** (`SpaceXAI`, formerly xAI; absorbed Feb 2026) — **mid-June launch** expected. **1.5 trillion parameters** (3× the current production model), targeting **Claude's coding benchmark lead**, trained on **Cursor developer workflows**. Polymarket / Kalshi prediction markets currently give **~33% probability** of shipping by June 30. **The structural concern:** since SpaceX absorbed xAI in Feb '26, **50+ researchers have departed**, including pre-training lead Juntang Zhuang. The pre-training group is reportedly down to "a handful of people." The launch will ship; the post-launch capability arc is the real question.

**Sources.**
- `[secondary]` [TechTimes — Google Gemini 3.5 Pro Nears June Launch With 2M Token Context](https://www.techtimes.com/articles/317919/20260606/google-gemini-35-pro-nears-june-launch-2-million-token-context-deep-think-reasoning.htm)
- `[analysis]` [WaveSpeed — Gemini 3.5 Pro Is Coming Next Month](https://wavespeed.ai/blog/posts/gemini-3-5-pro-coming-next-month/)
- `[aggregator]` [Polymarket — Next Google Gemini Pro Model Released](https://polymarket.com/event/next-google-gemini-pro-model-released-onptptpt)
- `[secondary]` [TechTimes — Grok AI New Model Triples Parameter Count, Targets Coding Lead: Release Expected Mid-June](https://www.techtimes.com/articles/317328/20260528/grok-ai-new-model-triples-parameter-count-targets-coding-lead-release-expected-mid-june.htm)
- `[analysis]` [MindStudio — xAI's Grok Roadmap: 7 Models in Training, Grok 5 at 10 Trillion Parameters](https://www.mindstudio.ai/blog/xai-grok-roadmap-7-models-training-grok-5-10-trillion)

**Why it matters to you.**

- **Job ·** Google Cloud + Vertex Agent Platform have a 2-week window to sign Anthropic-stack enterprise customers — expect aggressive Solutions Engineering hiring at GCP for June–July. Watch for "Gemini Customer Engineering" / "Vertex Forward Deployed" listings.
- **Startup ·** A `wait-and-route` wedge: a thin migration toolkit that takes a Claude prompt + an MCP server bundle and produces (a) a Gemini-3.5-Pro-equivalent harness, (b) a `grok-5` parallel run for benchmarking. **Ship the toolkit within 7 days of Gemini 3.5 Pro launch** to capture the migration wave. (This pairs cleanly with the [Fable-5 dependency audit](./03-practical-skills-and-tools.md#2-anthropic-stack-hedge) and is a viable portfolio artifact.)
- **Insight ·** The Anthropic-stack-committed candidate (you) needs a 1-page "Gemini 3.5 Pro vs Claude Opus 4.8 vs GPT-5.5" comparison table published within **24 hours of Gemini 3.5 Pro launch**. This was already an open artifact in [ME.md — "One-page Gemini-vs-Claude-vs-OpenAI agent comparison"](../ME.md#active-portfolio-artifacts). It's now also a hedge: it demonstrates multi-vendor fluency the day your default vendor went dark.

`#gemini #grok #spacexai #model-pipeline #migration`

---

## 3. Microsoft + Google take on Anthropic / OpenAI in AI coding {#3-coding-race}

**What happened.** Per **CNBC (Jun 1)**, the AI-coding market — where Anthropic has built a commanding lead via Claude Code — is now seeing **Microsoft and Google take direct shots**. The reporting frames Claude Code as the single biggest contributor to Anthropic's "zoom ahead of the field" position; Microsoft (GitHub Copilot post-Gemini-3.5-Flash GA integration) + Google (Antigravity 2.0 + Managed Agents) are both pushing competing agentic coding stacks. **The Fable 5 shutdown widens the opening by exactly the duration of the suspension.**

**Sources.**
- `[secondary]` [CNBC — Microsoft and Google take on Anthropic and OpenAI in AI coding models](https://www.cnbc.com/2026/06/01/microsoft-and-google-take-on-anthropic-and-openai-in-ai-coding-models.html)
- `[analysis]` [SemiAnalysis — Claude Code commit-share trends](https://newsletter.semianalysis.com/) (track for an update post-Gemini 3.5 Pro)
- `[secondary]` Cross-reference: [Anthropic Code w/ Claude London](../2026-05-22/01-big-lab-moves.md) (May 19) + [Antigravity 2.0 + Managed Agents at I/O](../2026-05-20/01-big-lab-moves.md)

**Why it matters to you.**

- **Job ·** GitHub Copilot Solutions / DevRel and Google Antigravity Solutions hiring will both accelerate. Track "Copilot Customer Engineering," "Antigravity Adoption Engineer," "DevTools Solutions" — these are FDE-adjacent roles at the platform layer.
- **Startup ·** The migration wedge in §2 is the same wedge here. **One toolkit, two market openings** — Anthropic shutdown + Gemini 3.5 Pro launch.
- **Insight ·** The "AI coding model" market structure is going to look very different by Aug 2026: today it's Claude-as-default; tomorrow it's a 3-way fight where reliability + price + jurisdiction-availability all matter more than peak benchmark.

`#claude-code #copilot #antigravity #coding-agents #competitive`

---

## 4. Live cross-thread: agentic AI funding has cooled by ~58% YoY {#4-funding-cool}

**What happened.** **Tracxn / agentic AI sector data through June 2026** shows total funding of **$2.66B for the year-to-date** in agentic AI — versus the **$6.42B 2025 total**. The pattern: **bigger checks into fewer winners**, plus **244 companies at Series A+, 130 at Series B+** in the cumulative agentic-AI cohort. Median pre-money: seed **~$17.9M**, Series B **~$143M**.

The "no VC will admit it" bubble framing (Product Leaders Day) calls out the **routing-and-security-gate gate** as the new Series A bar — startups without these features face cold fundraising and down-rounds.

**Sources.**
- `[aggregator]` [Tracxn — Agentic AI 2026 Market & Investments Trends](https://tracxn.com/d/sectors/agentic-ai/__oyRAfdUfHPjf2oap110Wis0Qg12Gd8DzULlDXPJzrzs)
- `[analysis]` [eqvista — AI Startup Fundraising Trends 2026 (Seed to Series B)](https://eqvista.com/ai-startup-fundraising-trends/)
- `[analysis]` [Product Leaders Day — The AI Agent Funding Bubble No VC Will Admit (June 2026)](https://productleadersdayindia.org/blogs/multi-agent-orchestration-news/ai-agent-startup-funding-news.html)
- `[aggregator]` [Crescendo AI — Latest VC Investment Deals in AI Startups](https://www.crescendo.ai/news/latest-vc-investment-deals-in-ai-startups)

**Why it matters to you.**

- **Job ·** Series A startups that survive the bar will be **selectively hiring engineers who can ship a multi-agent routing engine + security gate** — that's the specific skill bar to clear in the interview loop for any "Founding ML Engineer / Founding AI Engineer" role this quarter.
- **Startup ·** If you're a founder-track candidate: your **wedge must include both a routing engine and a security gate**, or you're below the Series A bar. (Aligns with the [STARTUPS.md](../STARTUPS.md) "anchor competitors" methodology — anchor your wedge below your security model, not above it.)
- **Insight ·** A consolidation phase is starting. Track Q3 2026 for the first agentic-startup acqui-hire bigger than $300M — that's the inflection.

`#funding #agentic-ai #series-a #consolidation #vc`

---

## Cross-page

- See [`01` §1](./01-big-lab-moves.md#1-fable-shutdown) for the shutdown that created the migration wedge described here.
- See [`03` §3](./03-practical-skills-and-tools.md#3-routing-gate-recipe) for the **"routing engine + security gate" Series-A-bar checklist** as a buildable artifact.
- See [`05` §3](./05-career-and-startup.md#3-application-prep) for the **week-of-Jun-15 application list** updated for the post-shutdown market.
