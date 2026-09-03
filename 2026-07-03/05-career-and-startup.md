# Career + Startup — 2026-07-03

Five threads reshape the week's hiring + startup map: **the Anthropic gateway ship creates an immediate FDE surge**; **two neocloud entrants (SB Neo + Meta Compute)** and **Together AI's $800M raise** open a real MLE/infra hiring lane you can target within 30 days; **the $30K Claude Science credit grant** is now T-12 days; **AI-content licensing** is a new career sub-lane after Cloudflare's July 1 shift; and the **AI-assisted vulnerability discovery** signal (1,500 CVEs in June alone) opens a **security-eng-with-AI** lane you'd previously have written off as "not for a CS grad."

Tags: `#career #fde #mle #neocloud #startups #security #grants #compensation`

---

## 1. FDE surge — every enterprise Claude buyer that stalled on SSO / cost-attribution just got unstuck {#1-fde-surge}

**What:** Yesterday's headline was Karp attacking the token model; today's headline is Anthropic shipping the **[apps gateway](./01-big-lab-moves.md#1-gateway)** — SSO, spend caps, failover, per-user attribution. **The direct hiring consequence:** every Fortune-1000 buyer that stalled on those objections now has **~90 days to design the deploy, wire the IdP, define the spend policy, and prove per-seat cost attribution to Finance.** Each of those deploys needs an FDE / Solutions Engineer / AI Integration Engineer.

Companies most likely to spin up FDE reqs in July–August:
- **Anthropic Solutions + Applied AI FDE** (roles already open per [2026-07-02/05 §2](../2026-07-02/05-career-and-startup.md#2-anthropic-fde) — the gateway ship pulls forward the hire).
- **Deloitte / Accenture / PwC / EY** — partner-network FDE.
- **Databricks / Snowflake / MongoDB** — will race to ship compatible gateway implementations under the open protocol → they'll hire "AI-cost-governance-eng."
- **Vercel / Cloudflare** — gateway-compatible edge routing is a natural product line.

Tags: `#fde #hiring #anthropic #enterprise #gateway`

### Why it matters to you

- **Do this week:**
  1. **Deploy [the gateway on a personal AWS/GCP account](./03-practical-skills-and-tools.md#1-gateway-deploy)** — Sat morning.
  2. Update your resume "AI Integration Engineer" line to reference the deploy + outage drill + spend-cap enforcement.
  3. Apply to **Anthropic FDE Applied AI** ([job board](https://job-boards.greenhouse.io/anthropic/jobs/4985877008)) and the Deloitte Anthropic-partner FDE reqs — attach the gateway repo.
- **Insight:** The gateway is a **pull-forward event for the FDE market** — it converts a soft-pipeline objection into a shipped feature, which converts "maybe next quarter" into "sign next month." The FDE demand curve was already the [strongest signal in the market](../2026-05-17/05-career-and-startup.md); it just got steeper.

---

## 2. Neocloud + open-model-cloud is now a real MLE / infra hiring lane {#2-neocloud-hiring}

**What:** In a single week: **Meta Compute announced**, **SB Neo stood up**, **Together AI raised $800M at $8.3B**. Combined: two new hyperscale entrants + one existing infra unicorn that's about to hire aggressively on inference and cluster-eng ladders. Add existing wedges — **Baseten $1.5B/$13B** ([2026-07-02/05 §1](../2026-07-02/05-career-and-startup.md#1-baseten)), Nebius, CoreWeave, Lambda, Foundry — and the **rent-a-GPU + inference lane** is the second-strongest lane after FDE.

Concrete targets:

- **Together AI careers page** — check for **inference-eng, cluster-eng, and applied-AI roles**.
- **Baseten careers** — tripling headcount.
- **SoftBank Group / SB Neo US careers** — pre-launch through Q4 2026; watch the Bright/Kubernetes/scheduler roles.
- **Meta Superintelligence Labs — Meta Compute team** under Janardhan/Gross/Powell McCormick.

Tags: `#neocloud #infra #mle #hiring #compute`

### Why it matters to you

- **Job:** The lane is **less crowded than the Claude-Code-FDE lane** because it demands a specific stack (NCCL, collectives, FSDP, vLLM/TGI/Ray, Kubernetes). If you have any HPC/systems coursework or CUDA experience from your CS grad program, this is the wedge with the least competition. Interview differentiation: **build a small vLLM serving demo on a spot-instance neocloud** (Lambda or Prime Intellect) and log unit economics.
- **Startup:** The **inference-margin** thesis ([2026-07-02/05 §1](../2026-07-02/05-career-and-startup.md#1-baseten)) is now cross-validated by four data points. Any wedge that assumes compute costs stay flat is under-priced.
- **Insight:** The neocloud lane is where **AI-eng meets systems-eng** — and CS grads (systems background + math coursework + a little PyTorch) are actually competitive here in a way they aren't in a pure MLE-PhD posting.

---

## 3. The Claude Science AI-for-Science credit grant is T-12 days — a real startup on-ramp for grad students with any wet-lab adjacency {#3-grant-deadline}

**What:** Anthropic will fund **up to 50 AI-for-Science projects with up to $30K in Claude credits each**; **applications close July 15, 2026** ([`01` §2](./01-big-lab-moves.md#2-claude-science)). Bio/biomedical priority, but computational-chem / drug-discovery / materials-science / genomics are in scope.

Application shape that lands (based on the SciAgentArena stepwise-validator framing from [2026-06-28/04](../2026-06-28/04-research-progress.md) and the [Claude Science app's auditable-artifact posture](./01-big-lab-moves.md#2-claude-science)):

1. **Pick one narrow, stepwise-verifiable workflow** — e.g., "triage single-cell RNA-seq QC flags for a small non-profit's cancer registry," "retrosynthesis QC for a chemistry lab's teaching sequence," "protein-mutation triage for undergrad genomics coursework."
2. **Define the auditable artifact** — a Claude Science-native figure with **code + environment + message history** attached.
3. **Cite AutoResearchBench + SciAgentArena** as your baseline; commit to a delta target.
4. **Name the cost budget** — "$30K credits will fund X eval runs at Y average token cost."

Tags: `#grants #anthropic #science #startup #deadline`

### Why it matters to you

- **Startup:** Even if you don't yet have a science co-founder, the **grant shape rewards a concrete workflow more than a big vision** — you can propose *one* workflow you'll run on *one* lab's data (find one professor at your school who says yes; even an undergrad lab). $30K in Claude credits is a real 6-month runway for eval work.
- **Job:** **The application itself is portfolio material.** Whether or not you win, the ~5-page write-up (workflow + eval + baseline + artifact spec) is exactly what an FDE interview would ask you to produce. Ship it either way.
- **Insight:** Anthropic's fund-shape is **50 projects × $30K** — small-batch, not one big grant. Read that as: **they're building a distribution channel**, not picking a winner. If your project lands, you also get **user-of-Claude-Science-beta** status, which is a real network entry.

**Action calendar:**
- **Sat 07-04:** find one lab partner + confirm data access.
- **Sun 07-05:** draft workflow + eval design.
- **Mon–Wed 07-06/08:** write the proposal.
- **Thu 07-09:** submit early to catch any format issues.

---

## 4. AI-content licensing is a new career sub-lane after Cloudflare's July 1 shift {#4-policy-lane}

**What:** [Cloudflare's Search/Agent/Training bot categorization](./02-new-emerging.md#3-cloudflare) — **Sept 15 defaults blocking Agent and Training on ad-monetized pages, Pay-Per-Crawl available** — has spun up a real employment sub-lane:

- **AI Content Licensing Manager / Deal Lead** — inside publishers (Reuters, NYT, Condé Nast, Bloomberg) — negotiating crawl and training licenses.
- **AI Traffic Engineer** — inside AI product companies (OpenAI, Anthropic, Perplexity) — negotiating on the other side.
- **Cloudflare / Fastly** — infra engineers building the Pay-Per-Crawl rails.

Tags: `#policy #licensing #cloudflare #careers #agents`

### Why it matters to you

- **Job:** This lane is **actively hiring** — most Big-N publishers have posted "AI Partnerships" or "AI Licensing" roles in the last 60 days. If you have any journalism / writing background alongside CS, this is a real hybrid role. Otherwise, **AI Traffic Engineer inside a Big-N lab** is a wedge role: you own the "we identify as Agent, negotiate crawl budget, cache mirrors politely" surface.
- **Startup:** "**Crawl-license as a service**" is a real wedge — an intermediary between small AI products and publisher SSPs. Modest ARR, high defensibility if you get the SSP integrations right.
- **Insight:** **September 15 is a hard deadline** for anyone whose product depends on browser-use agents. Add it to your STARTUPS.md and WATCHLIST — it's a repricing event.

→ Cross-link: [`02` §3 Cloudflare rules](./02-new-emerging.md#3-cloudflare).

---

## 5. Security-eng-with-AI is a real hire lane — 21 orgs disclosed ~1,500 CVEs in June from AI-assisted vuln discovery {#5-security-lane}

**What:** June 2026 saw **~1,500 high-and-critical CVEs disclosed across 21 organizations**, with AI-assisted discovery cited as a primary driver ([The Neuron](https://www.theneuron.ai/explainer-articles/around-the-horn-digest-everything-that-happened-in-ai-today-friday-july-3-2026/), [BuildFast AI](https://www.buildfastwithai.com/blogs/ai-news-today-july-3-2026)). Pair with the [May Google Threat Intelligence "first AI-built zero-day in active exploitation"](../2026-05-13/) and Anthropic's [GPT-5.5-Cyber / Mythos / Fable 5 track from May–July](../2026-05-09/): **AI is both increasing the vulnerability find-rate and the offensive/defensive surface itself.**

Sub-roles hiring:

- **Security Research Engineer (AI-assisted)** — Google Project Zero, Anthropic Red Team, OpenAI Safety, xAI Safety.
- **AppSec + AI-agent hardening** — at every AI-application vendor.
- **AI Assurance / Pre-deployment Eval** — the sub-lane [flagged in the postponed EO](../2026-05-22/01-big-lab-moves.md#1-eo-postponed) is materializing on the voluntary side (Anthropic's constitution + [safety events like the AI-for-Science briefing](../2026-06-30/01-big-lab-moves.md)).

Tags: `#security #safety #hiring #anthropic #openai`

### Why it matters to you

- **Job:** If security has been on your "maybe someday" list, this is your **maybe-now moment**. The lane rewards CS grads who can (a) read a CVE and reproduce it, (b) drive an agent to look for a class of bug, (c) design an eval for red-team success. Ship one small repo: **"agent-driven fuzzer for X"** where X is a small, well-scoped attack surface (SSRF, prompt-injection variants, deserialization). One repo + one CVE-adjacent writeup = interview material.
- **Startup:** **Agentic-SOC** wedges (per Exaforce, [2026-05-22/02](../2026-05-22/02-new-emerging.md)) are getting fresh tailwind — 1,500 new CVEs need triage; classic SOC teams are overwhelmed. The wedge is not "find the vuln" (Google has that) but **"triage / prioritize / auto-remediate the flood."**
- **Insight:** Security has been the **most-cited AI-adjacent-professional-services** lane in every earnings call for two quarters. The dollar spend is real; the graduate-level talent bench is thin. This is a supply-demand mismatch.

---

## Weekend action set (07-04 → 07-06)

- **Sat AM:** [Deploy the Claude apps gateway on personal AWS or GCP](./03-practical-skills-and-tools.md#1-gateway-deploy) — 60 min build, 30 min screenshots + notes, 15 min Loom.
- **Sat PM:** find one lab partner for the [Claude Science credit grant](#3-grant-deadline).
- **Sun AM:** draft the [routing table update](./03-practical-skills-and-tools.md#3-routing) + push to a public repo.
- **Sun PM:** open one bookmark tab per lane — Together / Baseten / SB Neo / Meta Compute careers + Anthropic FDE Applied AI + Deloitte partner FDE. Send **one warm outreach** to a Meta-Compute-adjacent contact.
- **Mon:** apply to Anthropic FDE with the gateway artifact + a 1-page "Karp / Uber / Lindy → gateway → what I'd do about it" writeup ([`01` §1](./01-big-lab-moves.md#1-gateway)).
