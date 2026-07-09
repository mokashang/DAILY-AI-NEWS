# TL;DR — 2026-07-09 (Thursday)

Sixty-second skim. **Two flagship model launches, one governance experiment, and the cheapest-model-wins market thesis all landed inside the same 24 hours.** OpenAI's **GPT-5.6 Sol / Terra / Luna went fully public today** (US Commerce Dept green-lit the general rollout); **xAI dropped Grok 4.5** the same morning with an *Opus-class* claim and a **4.2× token-efficiency edge** on SWE-Bench Pro; and this week we learned OpenAI **floated a 5% US government equity stake** (~$42.6B at $852B) modeled on the Alaska Permanent Fund — the first serious "public wealth fund" proposal from a frontier lab. Meanwhile the market voted with its wallet: **Chinese models are now 30–46% of enterprise API tokens flowing through US developer platforms**, and **GLM-5.2 became the fastest-growing model Vercel has ever tracked** (27× tokens, 80× customers in one week). For you: **the pricing race is now the product race**, and every one of your portfolio artifacts needs a cost-per-task number attached to it.

> Continues from **[2026-07-08](../2026-07-08/00-tldr.md)** ("the frontier gets repriced from three sides — capital, sovereignty, geography — in 72 hours"). Today's edition is the *day-after* on all three of yesterday's threads: the 5%-equity proposal keeps ripening, GPT-5.6 crossed from preview to general availability, and Grok 4.5 joins the pricing race with a hard 4.2× token-efficiency number to defend it.

---

1. **GPT-5.6 Sol / Terra / Luna — PUBLIC LAUNCH TODAY.** Full rollout across ChatGPT + API after US Commerce Dept clearance. **Sol $5/$30, Terra $2.50/$15, Luna $1/$6** per 1M tokens; ships with **predictable prompt caching** (explicit cache breakpoints, 30-min minimum TTL, cache writes at 1.25× uncached input, cache reads at the standard 90% discount). Cerebras hosting Sol at up to **750 tok/s** in July. → [`01` §1](./01-big-lab-moves.md#1-gpt-5-6) `#openai #gpt-5-6 #launch #pricing`

2. **Grok 4.5 — public today, "Opus-class" claim, no system card.** SpaceXAI released it 11 days after Musk's private-beta announcement; **$2 in / $6 out**, ~80 tok/s, built on the 1.5T-parameter V9 foundation and — this is the tell — **trained on data from Cursor** (SpaceX's $60B pending acquisition). Beats Opus 4.8 on **DeepSWE 1.0 + Terminal-Bench 2.1**, loses on **DeepSWE 1.1 + SWE-Bench Pro** — but reports **15,954 output tokens/task vs 67,020 for Opus 4.8 max on SWE-Bench Pro (4.2× more efficient)**. → [`01` §2](./01-big-lab-moves.md#2-grok-4-5) `#xai #grok #cursor #token-efficiency`

3. **Anthropic ships Sonnet 5 + redeploys Fable 5 + launches Claude Science.** **Sonnet 5** (default from June 30) at **intro $2/$10 through Aug 31** (then $3/$15) — near-Opus-4.8 quality; **Fable 5 redeployed globally July 1** after Commerce Dept lifted the June-12 export controls (new cybersecurity classifier added); **Claude Science Workbench** (June 30) hooks Opus 4.8 into **60+ scientific databases** for reproducible genomics/proteomics/cheminformatics pipelines — this is the "vertical Claude for X" pattern shipping as a first-party product. → [`01` §3](./01-big-lab-moves.md#3-anthropic-stack) `#anthropic #sonnet-5 #fable-5 #claude-science`

4. **OpenAI floats a 5% US government equity stake.** ~$42.6B at the $852B post-money mark; **modeled on the Alaska Permanent Fund** (oil revenue → resident dividends). Structurally: each of the largest US developers would allot 5% to a public investment vehicle. **Conceptual, would require an act of Congress**, Anthropic/Google/Meta unconfirmed. Follows the fortnight in which Commerce **lifted the Fable/Mythos export curbs** and **released GPT-5.6 for general rollout after review** — the "voluntary standards" era is *becoming* the era. → [`01` §4](./01-big-lab-moves.md#4-government-stake) `#policy #public-wealth-fund #openai`

5. **The pricing race won the product race — Chinese models are 30–46% of enterprise API tokens on US developer platforms.** **GLM-5.2 from Z.ai is the fastest-adopted model Vercel has ever tracked** (27× daily tokens, 80× customer count in its first week). Open-source Chinese models are **60–90% cheaper**; **GLM-5.2 scored 62.1% on SWE-Bench Pro, above GPT-5.5 at 58.6%, MIT-licensed.** Vercel's head of agentic infra: *"Price is doing the work here."* → [`02` §1](./02-new-emerging.md#1-glm-5-2) `#china #glm #openrouter #vercel #open-source`

6. **Meta becomes a cloud vendor.** **Meta Compute launched July 1** — Meta selling *excess AI infrastructure* to third parties, with plans to add **tens of gigawatts** of capacity this decade. First real signal that hyperscaler surplus is becoming a category (compare AWS's 2006 origin story — S3 as leftover capacity). → [`02` §2](./02-new-emerging.md#2-meta-compute) `#meta #cloud #compute-market`

7. **Practical: model-routing just got table-stakes.** The four cheap-tier models that matter as of tonight — **GPT-5.6 Luna ($1/$6), Grok 4.5 ($2/$6), Sonnet 5 intro ($2/$10), GLM-5.2 (open-weights, MIT)** — are all within a factor of 2 on price *and* now within striking distance on SWE-Bench Pro. **The skill isn't "use Opus everywhere" — it's route by task-type, verify by benchmark, log the cost per task.** → [`03` §1](./03-practical-skills-and-tools.md#1-cheap-tier-routing) `#routing #cost #benchmarks`

8. **Skill read of the week:** *the moat migrated from model quality to model economics.* Grok 4.5's 4.2× token efficiency, GPT-5.6's predictable caching, GLM-5.2's MIT-license floor, Sonnet-5's intro pricing — every big move this quarter is a **cost-per-completion** move, not a capability move. Your interview answer for "how do you build agents" needs to lead with **cost-per-task**, not "we use Claude Opus." → [`05` §2](./05-career-and-startup.md#2-cost-per-task-is-the-answer) `#skills #careers`

---

## One thing to DO this Thursday

→ **Ship the "3-model routing" comparison artifact.** Run one identical agent task (pick something from [`04` §1](./04-research-progress.md#1-mas-orchestra) or a Terminal-bench task) through **GPT-5.6 Terra + Grok 4.5 + Sonnet 5**, log **cost, tokens, wall-clock, and pass/fail** per attempt, publish the table. **This answers three interview questions in one artifact:** routing, verification, and cost. Cross-link the four-price table from [`03` §1](./03-practical-skills-and-tools.md#1-cheap-tier-routing).

## Watchlist deltas (day-after moves on [2026-07-08](../2026-07-08/))

- 🆕 **GPT-5.6 Sol/Terra/Luna generally available (July 9).** The naming pattern (Sol/Terra/Luna) is the first time OpenAI has broken from numeric-only versioning at the tier level — track whether Anthropic/xAI follow.
- 🆕 **Grok 4.5 public + Cursor-data-trained.** Cursor acquisition ($60B, announced June) means **coding-agent evals just became a partisan question** — every SWE-Bench Pro number now needs a "trained-on-what" footnote.
- 🆕 **US Commerce Dept as *de facto* AI regulator.** Fable 5 export controls (June 12) → lifted (~July 1). GPT-5.6 preview → general availability (July 9). This is the shape of "voluntary standards" in practice: **a Commerce-Dept gate on every frontier release.**
- 🆕 **OpenAI 5% government-stake proposal.** New thread — track whether Anthropic responds, whether Congress moves, and whether the "Alaska Permanent Fund for AI" frame gets adopted by any 2026 candidate.
- 🆕 **Chinese-model share on US developer platforms 30–46%.** New thread — this is the single biggest change in the practitioner stack since 2026-05-22; watch OpenRouter weekly.
- 🆕 **Meta Compute launched.** New thread — is this AWS-2006 or Vertex-2018? Track pricing and first-customer announcements.
- ➡️ **Anthropic Sonnet 5 default swap (June 30).** Continues the Anthropic-stack focusing decision from [ME.md](../ME.md) — the intro pricing (Aug-31 window) is a *forced* portfolio-shipping deadline.
- ➡️ **Anthropic Agent SDK metering (was June 15 in [2026-05-16](../2026-05-16/01-big-lab-moves.md)).** Should be live and biting by now — audit your own bill.
- ⬇️ **Trump AI executive order** — postponed 2026-05-22, replaced in practice by **Commerce-Dept-mediated voluntary review** (see [`01` §4](./01-big-lab-moves.md#4-government-stake)). The pre-deployment-evaluation lane is now real, just Commerce-flavored rather than EO-flavored.
- 🆕 **OpenAI IPO (Sept target from [2026-05-22](../2026-05-22/01-big-lab-moves.md#2-openai-s1)).** S-1 filed May 22; the 5%-stake proposal likely reshapes the roadshow.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This + [`01` §1–2](./01-big-lab-moves.md) (GPT-5.6 + Grok 4.5 launches) |
| 20 min | [`02` §1](./02-new-emerging.md#1-glm-5-2) (GLM-5.2/Vercel adoption) + [`03` §1](./03-practical-skills-and-tools.md#1-cheap-tier-routing) (routing playbook) — the two deepest signals |
| Tonight | [`03` §1](./03-practical-skills-and-tools.md#1-cheap-tier-routing) — run one Terminal-bench task through 3 models, log the cost table |
| Weekend | Turn the cost table into the "3-model routing" portfolio artifact (see "One thing to DO") |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
