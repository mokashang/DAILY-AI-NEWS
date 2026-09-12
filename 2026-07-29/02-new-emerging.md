# New & Emerging — 2026-07-29 (Wednesday)

Physical-AI capital is loudest today: **Agility Robotics** going public via SPAC at a $2.5B pre-money, **BYD** teasing a humanoid for August, and a **60,000 sq ft** Physical AI hub opening in Fremont. On the software side, one large open-source training-platform round ([Together AI, $800M Series C](../2026-07-25/02-new-emerging.md) continues to define the "picks and shovels" tier), and MCP's stateless spec — now shipped — is quietly re-drawing the hosting map.

---

## 1. Agility Robotics goes public via Churchill Capital XI (SPAC) at $2.5B pre-money {#1-agility-spac}

**What happened.** [Humanoid Global press release, 2026-07-28](https://www.globenewswire.com/news-release/2026/07/28/3333986/0/en/Humanoid-Global-Provides-Update-on-Agility-Robotics-Public-Listing-Opens-Silicon-Valley-AI-Hub-to-Scale-Digit-Deployments.html) `[primary]`:
- **Agility Robotics** (makers of **Digit**) enters a definitive business-combination agreement with **Churchill Capital Corp XI**.
- **Pre-money equity value: US$2.5B.**
- Expected **>US$620M in gross proceeds.**
- **New 60,000 sq ft Physical AI hub in Fremont, CA** to scale Digit deployment.

**Why it matters.**
- **First mainstream humanoid to list.** Agility joins the very short list of humanoid-robotics companies with a public-market data point. That reprices the entire private cap-table in the segment (Figure, 1X, Apptronik, and the crop of Chinese entrants).
- **SPAC vehicle is telling.** The public market is not yet ready to underwrite a traditional IPO for a humanoid company; a SPAC gets the ticker on the tape without the S-1 disclosure grind. Read this as "capital is available, but scrutiny is deferred."
- **60,000 sq ft in Fremont** is a labor-market signal: engineers within an hour of Fremont just gained a large local hardware employer. If you're within commuting distance and interested in embodied AI, apply.

**Job · Startup · Insight.**
- **Job.** Agility Robotics careers page will be hiring aggressively post-close — mechanical, controls, and *especially* **perception / policy-learning engineers**. This is one of the fastest-scaling embodied-AI hiring pipelines in the U.S.
- **Startup.** Adjacent categories that will re-rate: **fleet-operations software for humanoids** (imagine "Rippling for a Digit fleet"), **failure-mode annotation / eval tooling** for humanoid deployment, and **teleop-supervised RL data collection**. All three are within a solo/duo founder's reach.
- **Insight.** The SPAC route means you can watch Agility's opex, deployment counts, and unit economics on public filings — a level of transparency the private humanoid market never had. Read the first two 10-Q filings carefully; they're the industry's first public financial baseline.

`#agility #humanoid #spac #embodied #physical-ai`

---

## 2. BYD humanoid unveil confirmed for August (Di Space) {#2-byd-humanoid}

**What happened.** [CnEVPost, 2026-07-28](https://cnevpost.com/2026/07/28/byd-confirms-plan-humanoid-robot-aug/) `[secondary]` — BYD confirmed it will show its first humanoid at "**Di Space**" in August. Adds BYD to the growing list of Chinese automakers moving into robotics (Xpeng, GAC, Chery already announced; BYD is the largest by revenue).

**Why it matters.** The **China humanoid-robot cohort is now automaker-led**, not startup-led — a structurally different capital base than the U.S. side (Figure, 1X, Agility). Chinese automakers have:
- Existing high-volume actuator supply chains,
- Battery and power-electronics expertise,
- Ability to subsidize humanoid economics from EV margins.

That is the same playbook that beat Western EV startups. Watch it here.

**Insight.** The competitive line in humanoids is going to look like the competitive line in EVs by 2028: U.S. software / vertical-integration play vs. Chinese cost / scale play. If you're founding in this space in the U.S., **the moat has to be software** (policy, safety, fleet ops) — hardware is a losing bet against BYD's cost curve.

**Job · Startup · Insight.**
- **Job.** Not directly hireable (China-domestic), but the *reaction* moves — expect U.S. humanoid startups to defensively raise and hire aggressively over the next 60 days.
- **Startup.** If your idea is "American humanoid hardware startup," reconsider. If it's "the software layer any humanoid needs," you're in a much better spot.
- **Insight.** Automakers-into-humanoids is the year's most under-discussed strategic shift.

`#byd #china #humanoid #ev #automaker`

---

## 3. MCP hosting: 2026-07-28 turned "stateless-native hosting" into an obvious market gap {#3-mcp-hosting}

**What happened.** [01 §2](./01-big-lab-moves.md#2-mcp-shipped) covers the spec. Emerging angle: **who runs your MCP server** is now an addressable question. Because the spec is stateless, the deploy target is trivially any of:

- Cloudflare Workers / Vercel Edge / AWS Lambda@Edge
- Fly.io / Railway / Render (region-pinned or global)
- Kubernetes with a plain round-robin service
- Serverless Postgres + a stateless handler (state moved to your database)

None of these has an MCP-native developer experience yet. **"Vercel-for-MCP"** is now a real category — one PR flow for tools/prompts/resources, OAuth 2.1 baked in, MCP Apps rendering handled, per-tool metrics.

**Sources.** [modelcontextprotocol.io spec announcement](https://blog.modelcontextprotocol.io/posts/2026-07-28/) `[primary]` · [Explainx.ai deep-dive](https://explainx.ai/blog/mcp-2026-07-28-stateless-spec-july-2026) `[analysis]`

**Why it matters.** The most under-priced startup opportunities are the ones that only become possible the day a protocol becomes deployable at global scale — which happened yesterday. **YC S26 RFS** ([`05` §5](./05-career-and-startup.md#5-yc-s26)) explicitly calls out "**infrastructure that makes agents safer**" as a category. This slots in cleanly.

**Job · Startup · Insight.**
- **Job.** Frame your MCP portfolio server as "deployed on Cloudflare Workers with OAuth 2.1 and MCP Apps" — this is the exact shape hiring managers will start asking about within the month.
- **Startup.** The 6-month wedge: **managed MCP hosting with a first-class developer experience**. Charge per active-tool-call, subsidize the free tier from OSS goodwill. If nobody ships this by October, it's a durable gap.
- **Insight.** MCP is going through the same "protocol → platform" cycle HTTP went through 1993 → 1998. Someone got very rich building Netscape's server; someone will get very rich building this one.

`#mcp #hosting #infra #startup-opportunity`

---

## 4. Sonnet 5 pricing sunset: $2/$10 → $3/$15 on 2026-09-01 {#4-sonnet-pricing}

**What happened.** [Anthropic release notes via Releasebot](https://releasebot.io/updates/anthropic/claude) `[primary]` confirmed: **Sonnet 5's promotional pricing ($2 in / $10 out per MTok) expires 2026-08-31**. Standard pricing ($3 / $15) takes effect 2026-09-01. Combined with [Opus 5 landing at 4.8 pricing](../2026-07-25/01-big-lab-moves.md#1-opus-5), the Anthropic lineup Sep 1 will be:

| Tier | In / Out per MTok |
|---|---|
| Opus 5 | $5 / $25 |
| Sonnet 5 | $3 / $15 (promo ends 08-31) |
| Haiku 4.5 | $0.80 / $4 |

**Why it matters.** If you're running an app on Sonnet 5, your COGS goes up **~50%** on 09-01. Two moves this week:
1. Re-run your cost/quality routing (the [effort toggle](./03-practical-skills-and-tools.md#1-opus-5-effort) may make Opus 5 low-effort cheaper than Sonnet 5 default for some workloads).
2. Front-load August traffic on the promo tier if you can — cache aggressively, re-generate expensive artifacts *now*.

**Insight.** Promotional pricing endings are recurring events for the frontier tier. Add "**check upcoming promo expirations**" to your monthly cost audit ([ME.md](../ME.md) rule) — 30-day heads-up on a 50% cost hike is worth the calendar reminder.

**Job · Startup · Insight.**
- **Job.** Ability to speak fluently about tier-vs-effort routing is a differentiator in AI-Eng interviews. Have concrete numbers.
- **Startup.** If your unit economics only work at $2/$10 Sonnet 5, you don't have unit economics. Fix now.
- **Insight.** The frontier's "workhorse" price floor is settling at ~$3 in / $15 out. Build models of your product's economics against that.

`#anthropic #pricing #sonnet #cogs`

---

## 5. Emerging platform: `robots.txt` as a security boundary is officially dead {#5-robots-txt}

**What happened.** The Claude share-chats incident ([`01` §5](./01-big-lab-moves.md#5-share-leak)) is the third mainstream "public URL got indexed" story in 2026 (Notion, Google Docs, now Claude). The industry-level takeaway: **"unlisted URLs behind a share flow" is not a working security model anymore.** Crawlers are aggressive; anyone can `site:` a subdomain.

**Emerging category:** *AI-artifact sharing hygiene* — a governance surface that didn't exist 12 months ago. Every enterprise Chief Data Officer will be asked this question within 90 days.

**Why it matters.** New product category = new startup opportunities and new interview talking points. The category has three natural entry points:
- **Scanner**: "point at your workspace, show every publicly reachable link, one-click revoke."
- **Policy engine**: "block share-outside-org, force expiration, log every share."
- **Migration**: "help teams move off public-by-default sharing on legacy AI tools."

**Insight.** Enterprise trust in AI products lives or dies on defaults. The next 12 months of AI enterprise procurement will be dominated by "what's your default posture?" not "what can you do?"

`#security #enterprise #governance #category`
