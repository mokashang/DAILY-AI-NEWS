# TL;DR — 2026-07-03 (Friday)

Sixty-second skim. **Anthropic answered the token-billing revolt with three shipped products in 48 hours; the compute floor added a second neocloud in a week; Cloudflare put a paywall between agents and the web.** Anthropic shipped the **[Claude apps gateway for Bedrock + Google Cloud](./01-big-lab-moves.md#1-gateway)** — self-hosted control plane, SSO, spend caps, failover — plus **[Claude Science](./01-big-lab-moves.md#2-claude-science)** (AI workbench for researchers; **$30K credit grant deadline July 15**) plus **[Artifacts-in-Claude-Code + doubled rate limits](./01-big-lab-moves.md#3-limits-artifacts)** plus a **[new public constitution](./01-big-lab-moves.md#4-constitution)**. Meanwhile **[SoftBank stood up SB Neo](./02-new-emerging.md#1-sb-neo)** targeting 10 GW by 2030 (second neocloud entrant in a single week after Meta Compute), **[Together AI closed $800M at $8.3B](./02-new-emerging.md#2-together)**, and **[Cloudflare split AI traffic into Search / Agent / Training](./02-new-emerging.md#3-cloudflare)** with Sept 15 defaults blocking Agent + Training on ad-monetized pages. For you: **the gateway is the FDE demo of Q3, the neocloud lane is the second-strongest hire lane after FDE, and the $30K Claude Science grant is a real startup on-ramp with 12 days to the deadline.**

---

1. **Anthropic ships the Claude apps gateway for Bedrock + Google Cloud — the direct answer to the token-billing revolt.** Self-hosted control plane: SSO from your IdP, per-user cost attribution, org/group/user spend caps, multi-cloud failover, published open protocol. Every stalled enterprise Claude Code rollout just got unblocked. → [`01` §1](./01-big-lab-moves.md#1-gateway) `#anthropic #gateway #enterprise #fde`

2. **Claude Science + $30K credit grant — deadline July 15 (T-12 days).** New macOS/Linux beta app for researchers with **auditable, reproducible** artifacts (3D protein structures, genome tracks, chemical structures) — every figure ships with the code + environment + message history that produced it. Anthropic funds **up to 50 AI-for-Science projects × $30K credits**; bio/biomedical priority. → [`01` §2](./01-big-lab-moves.md#2-claude-science) `#anthropic #science #grants`

3. **SB Neo stood up — the *second* neocloud entrant in a single week.** SoftBank Corp + SoftBank Group (51/49) launched **SB Neo, Inc.** targeting a **10 GW US neocloud footprint by 2030**, starting FY2027. Pairs with Meta Compute (July 1) and Together AI's $800M raise → the compute floor is being commoditized. → [`02` §1](./02-new-emerging.md#1-sb-neo) `#neocloud #softbank #compute`

4. **Together AI closes $800M Series C at $8.3B — Aramco led, NVIDIA + Vista + GC in.** $1.15B annual bookings; customer list = Cursor, Cognition, Decagon. The open-model neocloud thesis is validated at Baseten-adjacent bands. → [`02` §2](./02-new-emerging.md#2-together) `#funding #open-source #compute`

5. **Cloudflare splits AI traffic into Search / Agent / Training — Sept 15 defaults will BLOCK Agent + Training on ad-monetized pages.** Site owners get a **three-way classification + Pay-Per-Crawl** rails on all tiers including Free. This changes the economics of every browser-use agent and every open-model training pipeline. → [`02` §3](./02-new-emerging.md#3-cloudflare) `#cloudflare #agents #licensing`

6. **Artifacts inside Claude Code on Pro + Max — Claude Code can now publish + update private live pages while it codes.** Directly enables long-running-agent status pages (a real interview demo). Plus doubled Claude Code 5-hour limits and 50%-higher weekly limits through July 13. → [`01` §3](./01-big-lab-moves.md#3-limits-artifacts) · [`03` §2 recipe](./03-practical-skills-and-tools.md#2-artifacts-recipe) `#claude-code #artifacts #dx`

7. **Practical you can do this weekend: DEPLOY THE GATEWAY on a personal AWS or GCP account.** 60 min build + 30 min screenshots + outage-drill Loom = the FDE interview demo of Q3. Answers three questions at once (enterprise deploy / multi-cloud failover / cost attribution to Finance). → [`03` §1](./03-practical-skills-and-tools.md#1-gateway-deploy) `#gateway #portfolio #fde`

8. **The skill re-price:** the value isn't "I built an agent" — it's **"I can prove enterprise readiness."** Gateway deploy + reproducible-artifact posture + a routing table with 5 slots (frontier reason / frontier speed / open cheap / self-hosted cheap / wholesale-compute) is what an FDE / MLE / Solutions role reads as senior. → [`05` §1](./05-career-and-startup.md#1-fde-surge) `#skills #careers`

---

## One thing to DO this Friday night → Sunday

→ **Ship the Claude apps gateway on personal AWS or GCP + one live-Artifact long-running agent, in a public repo.** Sat morning: [deploy the gateway](./03-practical-skills-and-tools.md#1-gateway-deploy) (Fargate + RDS or Cloud Run + Cloud SQL), wire SSO, cap spend at $10/day, run an outage drill. Sat afternoon: [add Artifacts-in-Claude-Code recipe](./03-practical-skills-and-tools.md#2-artifacts-recipe) — one long refactor with live status page. Sun: [rewrite routing config](./03-practical-skills-and-tools.md#3-routing) to add Together AI + Meta Compute + Cloudflare Agent identifier. Push to `personal-fde-lab` repo; attach to Monday's Anthropic FDE application. **One weekend = the strongest single artifact you can put in front of an FDE recruiter in Q3.**

## Watchlist deltas

- 🆕 **Claude apps gateway (Bedrock + Google Cloud)** — track (a) third-party gateway implementations (Databricks/Snowflake/LiteLLM/Portkey), (b) whether Anthropic ships **outcome-priced SKUs** on top of it in Q3, (c) attach rate at Fortune-1000 buyers who stalled in Q2.
- 🆕 **Claude Science + $30K AI-for-Science credit grant** — **T-12 days to July 15 deadline**. Action item on this week's calendar.
- 🆕 **SB Neo (SoftBank US neocloud)** — 10 GW by 2030 target; FY27 first-customer window. Watch US hiring page.
- 🆕 **Cloudflare AI Search/Agent/Training** — **Sept 15 defaults hard deadline** for any browser-use-agent product. Repricing event.
- 🆕 **Together AI $800M / $8.3B** — customer list = Cursor / Cognition / Decagon; hiring on infra + inference-eng.
- 🆕 **Artifacts inside Claude Code (Pro + Max)** — live status pages during long agent runs.
- 🆕 **Anthropic new constitution** — three days before UN Geneva dialogue July 6.
- ➡️ **Meta Compute** — Day 3. Carried from [2026-07-02/01 §2](../2026-07-02/01-big-lab-moves.md#2-meta-compute). Watch sticker pricing at first-customer reveal.
- ➡️ **GPT-5.6 Sol / Terra / Luna preview** — no fresh material today. Watch Cerebras 750 t/s.
- ➡️ **Fable 5 / Mythos 5 return** — Day 3. False-positive-rate data still the leading signal.
- ➡️ **Sonnet 5 promo pricing ($2/$10 through Aug 31)** — carried; T-59 days to standard $3/$15.
- ➡️ **Enterprise token-billing revolt (Uber / Lindy / Karp)** — the gateway is the counter-punch; watch whether Q3 outcome-pricing SKUs follow.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Claude apps gateway in [`01` §1](./01-big-lab-moves.md#1-gateway) |
| 20 min | [`01` §1](./01-big-lab-moves.md#1-gateway) + [`03` §1](./03-practical-skills-and-tools.md#1-gateway-deploy) — read together, deploy this weekend |
| Today | [`05` §1](./05-career-and-startup.md#1-fde-surge) — the FDE surge case for applying Monday |
| Weekend | [`03` §1 gateway](./03-practical-skills-and-tools.md#1-gateway-deploy) + [`03` §2 Artifacts recipe](./03-practical-skills-and-tools.md#2-artifacts-recipe) + [`03` §3 routing](./03-practical-skills-and-tools.md#3-routing) — the full Friday-night → Sunday build |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.

*Gap note: the last edition was 2026-07-02. No gap; daily cadence maintained.*
