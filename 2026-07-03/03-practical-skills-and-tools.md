# Practical Skills & Tools — 2026-07-03

Three things you can do this weekend. **§1 is the highest-ROI portfolio artifact of the week** — deploy Anthropic's new gateway on a personal AWS/GCP account, log the setup, and you have both an interview demo and a startup dev-log. §2 uses the fresh Claude-Code-Artifacts feature. §3 updates your routing table to reflect this week's neocloud reality.

Tags: `#practical #claude-code #gateway #artifacts #routing #cost #agents`

---

## 1. Deploy the Claude apps gateway on your own AWS or GCP account this weekend — the FDE demo of Q3 {#1-gateway-deploy}

**What / how:** Anthropic shipped the **Claude apps gateway** as a single stateless container + PostgreSQL, and published the protocol. You can stand up a working instance on **AWS Fargate + RDS Postgres** or **GCP Cloud Run + Cloud SQL** in an afternoon. Suggested build steps:

1. **Provision infra** (Terraform module — Anthropic docs include a reference). One Fargate/Cloud Run service, one small Postgres, one secret store entry for the upstream credential.
2. **Wire your IdP.** For a personal demo, use **Google Workspace SSO** or **GitHub OAuth**; document the trust flow.
3. **Point at Bedrock and Vertex** (both) with **automatic failover.** Simulate a Bedrock outage by revoking the IAM role and watch the gateway route to Vertex.
4. **Enforce a $10/day spend cap on your own user.** Blow through it deliberately; screenshot the block + `429`-with-`retry-after` behavior.
5. **Export the collector data** to a **CSV or a small Datadog / Grafana Cloud dashboard**. This is your interview screen-share.
6. Write a **1-page README + 90-second Loom** describing the deploy, the outage-drill, and one thing you'd change (e.g., "I'd add per-model spend caps in v2 — the protocol permits it but the reference container doesn't ship the UI").

**Sources:**
- [Anthropic — Introducing the Claude apps gateway](https://claude.com/blog/introducing-the-claude-apps-gateway) `[primary]`
- [Claude Code docs — apps gateway](https://code.claude.com/docs/en/claude-apps-gateway) `[primary]`
- [Clauding — protocol walk-through](https://clauding.de/en/posts/claude-apps-gateway-bedrock-google-cloud) `[analysis]`
- [DevOps.com — SSO/policy/spend-cap overview](https://devops.com/anthropic-adds-enterprise-gateway-to-simplify-claude-code-access-on-aws-and-google-cloud/) `[secondary]`

Tags: `#gateway #fde #portfolio #aws #gcp #sso`

**Why-it-matters:** This single artifact answers **three FDE interview questions at once** — (a) "have you deployed Claude Code in an enterprise-grade environment?" (b) "how do you handle multi-cloud failover?" and (c) "how do you show cost attribution to Finance?" Ship it and you'll have Anthropic Solutions/FDE recruiters replying warm, not cold — see [`05` §1](./05-career-and-startup.md#1-fde-surge). Even if you never talk to Anthropic, the artifact reads as *senior* to any AI-adjacent CTO hiring an FDE at Sierra, Decagon, Cursor, or Baseten.

---

## 2. Use Artifacts-in-Claude-Code to publish a live agent status page during long runs {#2-artifacts-recipe}

**What / how:** With today's [Artifacts-in-Claude-Code](./01-big-lab-moves.md#3-limits-artifacts) rollout on Pro + Max, Claude Code can now **create, publish, and update a private HTML/Markdown artifact while it continues coding.** Recipe for a long-running agent:

1. In your `CLAUDE.md`, add: `When you begin a long task, create an Artifact called "Run Status" summarizing (i) the plan, (ii) files touched, (iii) commands run, (iv) test status. Update it after every 5 tool calls.`
2. Have the agent post the Artifact URL to a Slack webhook / email on start.
3. Use the Artifact as the **crash-recovery breadcrumb** (parallels the [initializer + progress-file pattern](../2026-07-02/03-practical-skills-and-tools.md#2-long-running) but with a *shared, visible* surface).
4. Instrument the Artifact to also show **cumulative token spend + $/hr rate** — pulling from the [gateway's per-user collector](#1-gateway-deploy) if you deployed one; otherwise Claude Code's own cost log.

**Sources:**
- [Anthropic — Claude Code Artifacts](https://releasebot.io/updates/anthropic) `[aggregator]`
- [Anthropic Engineering — Effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) `[primary]`

Tags: `#claude-code #artifacts #agents #observability`

**Why-it-matters:** "A visible, live status page an agent updates as it works" is the **counter-example to the black-box-agent fear** that comes up in every enterprise sales call — and every founding-engineer interview. Ship one this weekend and you have a legible answer to "how do you supervise an autonomous agent?"

---

## 3. Update your routing table — add SB Neo (2027), Together AI, Meta Compute, and a Cloudflare-Agent-friendly fetch policy {#3-routing}

**What / how:** This week reshaped the compute layer. Rewrite your routing config so the 5-min-cost decision reflects real 2026 Q3 economics.

**A. Model routing (cheap-fallback stack).** Add or update:

| Slot | Choice (as of 2026-07-03) | Note |
|---|---|---|
| Frontier reasoning | **Claude Sonnet 5** ($2/$10 through Aug 31 — see [2026-07-01/01 §1](../2026-07-01/01-big-lab-moves.md#1-sonnet-5)) | Default. |
| Frontier speed | **GPT-5.6 Terra ($2.50/$15) when GA** ([2026-07-01/01 §4](../2026-07-01/01-big-lab-moves.md#4-gpt-56)) or **Gemini 3.5 Flash ($1.50/$9)** ([2026-05-20/01](../2026-05-20/01-big-lab-moves.md)) | Terra is preview-only today — Flash is the shippable slot. |
| Cheap-fallback (open) | **Together AI-hosted DeepSeek V4 or LongCat 2.0** | New: Together's $8.3B round ([`02` §2](./02-new-emerging.md#2-together)) is the ratification. |
| Cheap-fallback (self-hosted) | **Muse Spark on Meta Compute when live** ([`01` §5](./01-big-lab-moves.md#5-meta-compute-day3)) | Track sticker price when it lands. |
| Compute wholesale (2027) | **SB Neo** ([`02` §1](./02-new-emerging.md#1-sb-neo)) | Not-yet-shipping; add to your infra deck as a Q1-27 option. |
| Coding agent | **Claude Sonnet 5** in Claude Code | Confirmed default. |

**B. Cloudflare Agent policy.** For any browser-use agent you run, add a policy layer:

1. Identify explicitly as **`Agent`** in the `User-Agent` and any `crawler-hints` you emit.
2. On `403` from a Cloudflare-guarded origin, do **not retry blindly** — respect `retry-after`, log the origin, and route to a cached / permitted mirror if one exists.
3. If the agent is browsing on behalf of a paying user, consider **negotiating a Pay-Per-Crawl allowance** per [Cloudflare's new options](./02-new-emerging.md#3-cloudflare).

**C. Gateway routing.** If you deployed [§1 the gateway](#1-gateway-deploy), point it at **Claude API + Bedrock + Vertex** with priority `Claude API > Bedrock > Vertex` — this gives you three-way failover with the shortest tail latency on the primary path.

**Sources:**
- [Together AI — Series C announcement (customer list)](https://www.together.ai/blog/announcing-our-series-c) `[primary]`
- [Cloudflare — three-way AI traffic categories](https://blog.cloudflare.com/content-independence-day-ai-options/) `[primary]`
- [Anthropic — apps gateway routing + failover docs](https://code.claude.com/docs/en/claude-apps-gateway) `[primary]`
- [Northflank — Claude 2026 pricing map](https://northflank.com/blog/claude-rate-limits-claude-code-pricing-cost) `[analysis]`

Tags: `#routing #cost #agents #open-models #cloudflare`

**Why-it-matters:** A routing table with **five slots (frontier reason / frontier speed / open cheap-fallback / self-hosted cheap-fallback / wholesale-compute)** is the operational answer to the [Karp / Uber / Lindy token-billing revolt](../2026-07-02/01-big-lab-moves.md#5-token-attack). Interview-ready framing: **"here's my routing table, here's my per-workflow unit economics, here's the failover drill I ran."**

---

## Friday-night 90 minutes (all three, sequenced)

1. **60 min** — deploy the gateway (§1). Take screenshots at each step; commit a `notes.md` alongside.
2. **20 min** — turn on Artifacts-in-Claude-Code (§2), add the `CLAUDE.md` line, run one long refactor task with a live Artifact URL.
3. **10 min** — update your routing config to include Together + Cloudflare Agent identifier (§3).

Push all three into a single public repo — **`personal-fde-lab`** or similar — and you have next week's application material.
