# Big Lab Moves — 2026-10-05

Last month was the model-flood ([2026-09-10/01 §1](../2026-09-10/01-big-lab-moves.md#1-model-fatigue) — four frontier models in a week). This month is the counter-move: **the labs stopped shipping models and started shipping the deployment surface**. **OpenAI** shipped **dots** (always-on agents on their own cloud computers), **GPT-6.1 Sol** (near-Astra quality at ~⅕ price), **Ultrafast** (8× Codex / 6× API), **Codex-in-the-cloud**, and **ChatGPT Space/Pages**. **Anthropic** shipped **Claude Code mods** (TypeScript plugins that can rewrite the agent itself), the **Barclays bank-wide rollout** (50% of devs on Claude Code by EOY), and the **Claude Frontier Academy** ($100M for 10,000 FDE credentials by end of 2027). **Google**'s recap: **Gemini 4 Argon** (1M-token *output*, cyber-defense tilt), **3.8 Flash + Flash Cyber**, **Live Avatar**, **SynthID Bio**, **Googlebook pre-order**. **The theme: in the deployment layer, the primitives are agents (dots), the plug-in surface (mods), the trained human (FDE), and the vertical landing zone (Barclays).** Each lab is picking which of those four to lead with.

Tags: `#labs #openai #anthropic #google #devday #dots #claude-code #mods #fde #enterprise #gemini`

---

## 1. OpenAI DevDay 2026 — dots, GPT-6.1 Sol, Ultrafast, Codex cloud, ChatGPT Space + Pages {#1-devday}

**What happened:** OpenAI's annual developer conference landed **Tuesday Sept 29** in San Francisco with **20+ announcements**. Four matter enough to internalize this week:

### 1a. "Dots" — always-on ChatGPT agents, each on its own cloud computer

- Each dot runs on **GPT-6 Astra** (the model introduced Sept 3; see [2026-09-10/01 §1](../2026-09-10/01-big-lab-moves.md#1-model-fatigue)) and gets **its own cloud computer and browser**.
- Interactable via **ChatGPT, Slack, or Teams** once configured.
- Takes on ongoing tasks across **4,000+ connected apps** — OpenAI's internal demo: a dot that investigates bugs when they are mentioned in Slack, builds a working app when a design is marked ready, notices an unsent invoice and drafts it for approval.
- **Custom Rules** per dot: what it may do unattended, what it must ask first, what it must never do.
- Each dot's cloud computer is **inspectable at any time**; linking a personal computer is off by default.
- Pricing: **1 dot included in ChatGPT Pro ($100/mo)**; more on Business Premium.

### 1b. GPT-6.1 Sol — "Astra at ⅕ the price"

- Near-Astra benchmark quality at **~20% of Astra's token price** (Astra available now; Sol *coming soon*, pricing live first).
- OpenAI positions Sol as the **cheap workhorse** of the GPT-6 family; **Astra remains the frontier for the hardest tasks.**
- Direct implication for mixed-model stacks: a two-model router (**Astra for frontier, Sol for routine**) now has ~5× cost headroom.

### 1c. Ultrafast — a premium speed tier

- Claims: **up to 8× faster generation in Codex, up to 6× in the API.**
- Live on **GPT-6 Astra** for **Pro 500 ($500/mo) and Enterprise** tiers.
- The lever: inference-time compute allocation + custom decoding — OpenAI did not detail the mechanism, but the primary buyer is **agentic workloads where latency on the critical path is the UX bottleneck.**

### 1d. Codex-in-the-cloud + voice; ChatGPT Space; Pages

- **Codex** now runs in the cloud — startable from any device, including your phone. The command-line tool now accepts **voice instructions**.
- **ChatGPT Space** = a shared workspace for a team *and its dots*.
- **Pages** = a shared document editor built for humans + dots to co-author.
- Together, these are the Microsoft 365 Copilot shape, but **dots-first instead of document-first.**

**Sources:**
- [BGR — Everything OpenAI Announced At DevDay 2026, Including Its Muse Alternative](https://www.bgr.com/2272332/openai-devday-2026-announcements/) `[secondary]`
- [CNBC — OpenAI DevDay 2026 recap](https://www.cnbc.com/2026/09/29/openai-devday-2026-live-updates.html) `[secondary]`
- [9to5Mac — OpenAI makes 20+ announcements at DevDay event including always-on agents called dots](https://9to5mac.com/2026/09/29/openai-teases-20-announcements-at-devday-watch-live/) `[secondary]`
- [Axios — The 5 biggest announcements from OpenAI's blockbuster AI conference](https://www.axios.com/2026/09/29/openai-dev-day-2026-dots-space-sol) `[secondary]`
- [Learnetto — OpenAI DevDay 2026: every announcement](https://learnetto.com/openai-devday-2026-announcements) `[aggregator]`
- [betanews — OpenAI launches dots, always-on ChatGPT agents with their own computers](https://betanews.com/article/openai-dots-agents-chatgpt/) `[secondary]`
- [Reworked — OpenAI DevDay 2026 Highlights: Dots, Agents and a $500 Plan](https://www.reworked.co/ai-news/the-biggest-announcements-from-openai-devday-dots-agents-new-500-plan/) `[secondary]`
- [9to5Google — OpenAI launches Dots, new 'always-on agents' you can assign tasks to](https://9to5google.com/2026/09/29/openai-dots-agent/) `[secondary]`

### Why it matters to you

- **Job lens:** The role you want for the Dots era is **"agent operator"** — someone who can scope a dot's responsibilities, write its Custom Rules, instrument its cloud computer, and own the on-call rotation when it misbehaves. This is a *new* job family, not a renamed one. It will be posted at both the labs (OpenAI, Anthropic, Google) and at the first-wave adopters (banks, consulting firms). Build the credential by running **one dot (or Claude-subagent-equivalent) end-to-end this week** on a workflow you own, and publish the Custom Rules + an incident log. That artifact outperforms a chatbot repo by an order of magnitude for FDE/Applied-AI roles.
- **Startup lens:** The dots launch opens three near-term wedges. **(a) Dot-telemetry / observability** — same Datadog shape, dots-shaped data (what the dot did, how long it took, which Custom Rules were tripped). **(b) Dot-marketplace** — pre-built dots for specific job functions (recruiting-coordinator dot, infra-SRE dot, customer-support-tier-1 dot), sold on retainer. **(c) Dot-safety / audit** — SOC2/HIPAA/PCI-friendly log retention, access control, incident replay. Expect a $20–40M Series A to land in one of these three categories inside 90 days.
- **Insight:** Note the pricing math. **ChatGPT Pro $100/mo = 1 dot included.** That number sets the floor: a dot is being priced like an *employee-grade subscription*, not an API line item. Compared with the June-15 Anthropic Agent SDK metering ([2026-05-16](../2026-05-16/)), OpenAI's bet is that **unmetered-ish, task-scoped agent pricing** beats **tokens-per-step metering** in the consumer and SMB tiers — Anthropic's bet is the inverse. The next 90 days will show which model wins; recurring-revenue-per-agent is the metric to watch.

→ Cross-link: [`03` §2 dots-as-a-direct-report playbook](./03-practical-skills-and-tools.md#2-agent-direct-report) · [`05` §3 the skill re-price](./05-career-and-startup.md#3-reprice).

---

## 2. Anthropic ships Claude Code **mods** — the agent itself is now moddable {#2-claude-code-mods}

**What happened:** Oct 1 — **Claude Code v2.1.287** shipped **mods**, announced by **@ClaudeDevs on X**. The posture: *"No reason why everyone should have an identical Claude experience"* (Anthropic, via The New Stack).

**What a mod can do (per Anthropic's docs + press):**
- **Draw panes and bands** in the Claude Code UI.
- **Restyle any part** of the Claude Code interface.
- **Intercept tool calls** — answer them without running the underlying tool (useful for stubbing/offline mode/safety wrappers).
- **Forward a request to a different model** (routing live, inside the agent).

**Distribution:** Mods ship **inside plugins**, installed via `/plugin` in the CLI or desktop app. Users can keep mods private or submit them to the **Claude directory** (public mod registry).

**Opening demo mods:**
- **Token Weather** — a status-bar sparkline of context-window usage over the last 12 turns.
- **Blast Radius** — flags potentially risky shell commands before execution and shows which files/resources they would affect in a side pane.

**Explicit Anthropic warning:** *"Mods receive the same access to a user's machine as Claude Code; install only from trusted sources."*

**Sources:**
- [The New Stack — "No reason why everyone should have an identical Claude experience": Anthropic's mods let you change Claude Code's look and behavior](https://thenewstack.io/anthropic-claude-code-mods-plugins/) `[secondary]`
- [Crypto Briefing — Anthropic adds Claude Code mods for behavior and interface changes](https://cryptobriefing.com/anthropic-claude-code-mods-customization/) `[secondary]`
- [Cellcog.ai — Claude Code Mods: What They Can Do and What They Can Reach](https://cellcog.ai/blog/claude-code-mods/) `[analysis]`
- [SuperPower Daily — Anthropic Adds Claude Code Mods That Can Rewrite Prompts and Replace Built-in Features](https://superpowerdaily.com/posts/anthropic-adds-claude-code-mods-that-can-rewrite-prompts-and-replace-built-in-features) `[secondary]`
- [Pasquale Pillitteri — Claude Code Gets Mods, Plugins That Rewrite the Agent](https://pasqualepillitteri.it/en/news/19871/claude-code-mods-plugins) `[analysis]`

### Why it matters to you

- **Job lens:** A **public mod with real users is a 100× better artifact than a chatbot** for any Anthropic / FDE / Developer-Tools role. Why: it signals you can read the Claude Code internals, write TypeScript against a non-trivial agent runtime, and reason about safety ("same machine access as Claude Code" is a *claim you have to earn by thinking it through*). Target: one mod before Friday, directory submission before Sunday. Minimum-viable mod ideas in [`03` §1](./03-practical-skills-and-tools.md#1-mods-tonight).
- **Startup lens:** Three fundable wedges open the moment mods ship. **(a) Enterprise mod bundles** — audit-logging mod + policy-enforcement mod + redaction-at-tool-boundary mod + support SLA, sold as a per-seat subscription to regulated verticals (law/finance/health). **(b) Mod-security-review** — a Veracode/Snyk-style static analysis of mods, licensed to enterprises who want to admit directory mods under policy. **(c) Mod-telemetry** — Datadog for mods: usage counts, performance regressions, failure modes. **The mod ecosystem is a browser-extension-grade distribution channel**; whoever builds the trust/safety layer around it in Q4 2026 captures a durable moat.
- **Insight:** Watch the next 90 days for the **first malicious-mod incident**. It is coming. Anthropic's advisory on "same host access" is a tell: they know the attack surface. The right founder read is to **sell the solution before the breach happens**, not after. Chrome extensions, VS Code extensions, npm packages — every one of them had a trust-channel crisis in the first 18 months. Mods will be no different.

→ Cross-link: [`03` §1 publish-a-mod-this-week playbook](./03-practical-skills-and-tools.md#1-mods-tonight) · [`02` §3 model-fatigue tooling thesis (2026-09-10)](../2026-09-10/02-new-emerging.md#3-model-fatigue-tooling).

---

## 3. Barclays goes bank-wide on Claude — 50% of developers by EOY 2026 {#3-barclays-bankwide}

**What happened:** Oct 1 — Anthropic + Barclays expanded their strategic partnership from pilot to bank-wide, with four load-bearing numbers:

- **50% of Barclays's software developers on Claude Code by end of 2026.**
- **Majority of software engineers by 2027.**
- **~120,000 client emails/day** already triaged on Anthropic models inside Barclays Markets.
- **16,000+ Barclays UK staff** using the **Colleague Knowledge Assistant** (live since 2025), **1M+ searches** logged.

Sits inside a **multi-year ~£2B Barclays efficiency program**; Claude is positioned as a load-bearing lever.

**Sources:**
- [Anthropic — Barclays scales Claude to upgrade operations and improve client experience](https://www.anthropic.com/news/barclays-scales-claude) `[primary]`
- [Bloomberg — Barclays Expands Use of Anthropic's Claude in Efficiency Push](https://www.bloomberg.com/news/articles/2026-10-01/barclays-expands-use-of-anthropic-s-claude-in-efficiency-push) `[secondary]`
- [Crowdfund Insider — Barclays Extends Anthropic's Claude Across Engineering, Markets, User Support](https://www.crowdfundinsider.com/2026/10/314977-barclays-extends-anthropics-claude-across-engineering-markets-user-support/) `[secondary]`
- [The Asian Banker — Barclays expands Anthropic's Claude Code to support software development and legacy modernisation](https://www.theasianbanker.com/updates-and-articles/barclays-expands-anthropic-s-claude-code-to-support-software-development-and-legacy-modernisation) `[secondary]`
- [Channel Insider — Barclays Expands Claude Across Banking](https://www.channelinsider.com/channel-business/news-barclays-anthropic-claude-banking-emea-uk/) `[secondary]`
- [Crypto Briefing — Barclays targets 50% developer adoption of Claude by end of 2026](https://cryptobriefing.com/barclays-claude-developer-adoption-2026/) `[secondary]`

### Why it matters to you

- **Job lens:** Barclays bank-wide is a **concrete hiring pipeline**, not a logo. A 50%-of-developers-on-Claude-Code commitment implies thousands of **Claude Code enablement roles** inside Barclays and inside its SIs — Accenture, Deloitte, PwC, EY, McKinsey — over the next 15 months. Target **three application lanes**: (1) Barclays direct (Claude platform team, London), (2) Big-4 "Claude practice" roles (which the Oct 2 Frontier Academy §4 will directly feed), (3) **Anthropic Solutions / FDE roles with a banking vertical specialty** (the Barclays account is now a Solutions-staffing magnet). The Big-4 lane is the easiest-to-enter today because the Frontier Academy hasn't credentialed anyone yet.
- **Startup lens:** The Barclays shape sets the **enterprise reference-architecture template** — 120K emails/day through an agent, 16K staff on a knowledge assistant, developers on Claude Code — against which the 15 other European universal banks (BNP, HSBC, Deutsche, ING, UBS, Santander, Lloyds, SocGen, etc.) will be benchmarked. If you can **sell the integration layer** between Claude and (your-bank's) core-banking stack / policy engine / core-messaging rails, you have a $10–30M ARR vertical SaaS wedge. The incumbent-SI replacement angle is less interesting; the data-residency + regulatory-posture angle is where the moat lives.
- **Insight:** Note the asymmetry with Anthropic's May narrative. In [2026-05-14](../2026-05-14/) the thesis was *"Anthropic overtakes OpenAI in US business adoption"*; today's confirmation is *"Anthropic overtakes in EU regulated verticals too, Barclays flagship."* The next thread to watch: **does OpenAI's new Dots feature land a bank account?** If not within 90 days, Anthropic's banking lead is structural (regulatory posture + Claude Code's auditability edge).

→ Cross-link: [2026-05-14 — Anthropic adoption crossover](../2026-05-14/00-tldr.md) · [`05` §1 Frontier Academy hiring signal](./05-career-and-startup.md#1-frontier-academy-signal).

---

## 4. Anthropic launches the **Claude Frontier Academy** — $100M for 10,000 FDE residencies by end of 2027 {#4-frontier-academy}

**What happened:** Oct 2 — Anthropic announced the **Claude Frontier Academy**, a **$100M commitment** to credential **10,000 Frontier Deployed Engineers (FDEs)** by **end of 2027**.

**Program shape (per Anthropic + CNBC):**
1. **Simulated enterprise deployment**, with a **graded assessment**.
2. A **residency modeled on medical training** — engineers practice on casework before being assessed and credentialed.
3. Organizations **nominate** their strongest professionals; each returns with a **specific Claude project to lead.**

**First cohorts (announced):** **Accenture · Bain · Deloitte · McKinsey · Morgan Stanley.** All five are also Barclays-adjacent (SIs or capital-markets peers).

**Sources:**
- [Anthropic — Claude Frontier Academy: $100M to train 10,000 engineers](https://www.anthropic.com/news/claude-frontier-academy) `[primary]`
- [CNBC — Anthropic to invest $100 million to train AI engineer talent](https://www.cnbc.com/2026/10/02/anthropic-to-invest-100-million-to-train-ai-engineer-talent.html) `[secondary]`
- [Benzinga — Anthropic Launches $100M Academy to Train 10,000 AI Engineers](https://www.benzinga.com/markets/tech/26/10/62151067/anthropic-100-million-claude-frontier-academy) `[secondary]`
- [Unite.AI — New Anthropic Academy Backs 10,000 Engineer Residencies With $100M](https://www.unite.ai/new-anthropic-academy-backs-10-000-engineer-residencies-with-100m/) `[secondary]`
- [Yahoo Finance — Anthropic Is Training 10,000 Engineers to Install Claude Inside the World's Largest Enterprises](https://finance.yahoo.com/technology/ai/articles/anthropic-training-10-000-engineers-232515047.html) `[secondary]`
- [FourWeekMBA — Anthropic's Frontier Academy: $100M to Train 10,000 Engineers](https://fourweekmba.com/ai-anthropic-claude-frontier-academy-100m-10000-engineers-resid/) `[analysis]`
- [Data Studios — Anthropic launches Claude Frontier Academy with $100M to train 10,000 enterprise AI engineers](https://www.datastudios.org/post/anthropic-claude-frontier-academy-100m-10000-enterprise-ai-engineers) `[analysis]`

### Why it matters to you

- **Job lens:** This is **the single clearest validation of the FDE / AI Integration Engineer lane** that has been forming across 2026 ([2026-05-16/05 §1](../2026-05-16/05-career-and-startup.md#1-integration-engineer) · [2026-05-17/05 FDE postings +800% YoY](../2026-05-17/00-tldr.md) · [2026-05-19/05 §2 OpenAI Deployment Company + Tomoro 150 FDEs](../2026-05-19/05-career-and-startup.md#2-openai-deployment-co)). Anthropic has now put **$100M of balance-sheet capital** behind the thesis that *the scarce factor is not models, it is people who can deploy them*. Three immediate moves: (1) **Apply to the Frontier Academy** the moment individual applications open — expect a window inside 60 days, likely routed through the Big-5 partners first (one application lane: ask Deloitte/Accenture/Bain contacts about internal nominations). (2) **Pre-position:** change your LinkedIn skills row to the vocabulary that cohort nominees will carry — *simulated enterprise deployment, Claude residency, FDE casework, Claude project lead.* Even without the credential, nominating-adjacent language signals "I know what the shape of this role is." (3) **Build the artifact a Frontier Academy nominee would build on day one** — a 1-page "Claude-at-{enterprise}" proposal with specific agentic workflows, cost estimates, and rollback plans. That memo doubles as your portfolio and your interview artifact.
- **Startup lens:** The Academy's existence tells you *where the pricing power inside enterprise AI deployment is going*. If **Anthropic itself is willing to pay 10,000 engineers' residency to produce supply**, demand must be at least an order of magnitude higher. **Vertical FDE agencies** (law FDE, pharma FDE, defense FDE, biotech FDE) are now a venture-fundable business — one certified lead engineer + a bench of five enterprise-ready engineers can bill $500K/mo on day one. Expect the first "specialist FDE boutique" to raise a Series A inside 90 days.
- **Insight:** Compare the economics against the GPT-6.1 Sol / Fable 5.1 price cuts. **Compute per task is approaching free; human-plus-model deployment is becoming the capex line.** This is the exact inversion that happened at the end of the first SaaS cycle (2010s): the software commoditized, the implementation partner (NetSuite PS, Salesforce implementations, SAP system integrators) captured the margin. **The FDE role is the AI-era system integrator**, and Anthropic is building Deloitte Consulting a decade ahead of schedule.

→ Cross-link: [`05` §1 Frontier Academy as a hiring signal](./05-career-and-startup.md#1-frontier-academy-signal) · [2026-05-16/05 §1 Integration Engineer thesis](../2026-05-16/05-career-and-startup.md#1-integration-engineer) · [2026-05-19/05 §2 OpenAI Deployment Company + Tomoro](../2026-05-19/05-career-and-startup.md#2-openai-deployment-co).

---

## 5. Google's September recap — Gemini 4 Argon + 3.8 Flash + Flash Cyber + Live Avatar + Googlebook + SynthID Bio {#5-google-sept-recap}

**What happened:** Google published its monthly recap on Oct 2 summarizing the September Gemini wave (per the official blog + DeepMind newsroom):

- **Gemini 4 Argon** — new frontier reasoning model; **1-million-token *output* ceiling**; purpose-built with a **cybersecurity-defense tilt**.
- **Gemini 3.8 Flash + Gemini 3.8 Flash Cyber** — the Flash family picks up a **dedicated cyber-defense variant**.
- **Gemini 3.8 Live with Live Avatar** — expressive voice + a visually-animated face layer for Gemini Live.
- **SynthID Bio** — SynthID (provenance watermarking) extends to **biological-sequence content**.
- **Private AI compute advances** — secure server-side memory for enterprise.
- **AlphaGenome Atlas** — DeepMind's DNA-prediction foundation.
- **WeatherNext 3** — next-generation weather forecasting model.
- **Agentic video understanding** — Gemini can act on long-form video.
- **Googlebook pre-order live.**
- **Gemini app on Windows.**

**Sources:**
- [Google Blog — The latest AI news we announced in September 2026](https://blog.google/innovation-and-ai/technology/ai/google-ai-updates-september-2026/) `[primary]`
- [Google DeepMind — News](https://deepmind.google/blog/) `[primary]`

### Why it matters to you

- **Job lens:** Two sub-lanes just got clearer. **(a) AI-for-cyber-defense** — Argon + Flash Cyber + Flash Cyber (and the parallel Mythos line on Anthropic) make **"AI/ML engineer, defensive-cyber"** one of the top-5 cleanest hiring lanes of Q4 2026 (watch Google Cloud, Mandiant, CrowdStrike, Palo Alto, SentinelOne, plus the "agentic SOC" category from [2026-05-22](../2026-05-22/) — Exaforce et al.). **(b) Bio/health foundation models** — AlphaGenome Atlas + SynthID Bio pull Isomorphic Labs ([2026-05-19/02 §1](../2026-05-19/02-new-emerging.md)) + the Gates-Foundation partnership ([2026-05-17](../2026-05-17/)) into a single hiring frame. If you can read a protein and write Python, pay goes up this quarter.
- **Startup lens:** **The 1M-token output ceiling is the under-weighted detail.** Most models cap output at 32K–128K tokens; 1M *output* enables entirely new product shapes — generating a book, a codebase, a full compliance report in one call rather than a chain. For founders, that's a wedge: *vertical products whose output is traditionally a bundle of artifacts (an audit, a filing, a contract set) now ship in one invocation.*
- **Insight:** Google's deployment-surface answer differs from OpenAI's and Anthropic's. **OpenAI leads with "dot" (an agent on a cloud computer); Anthropic leads with "mod + credentialed human"; Google leads with "specialist model + Workspace/Android/XR surface area."** Three strategies, one bet: *the deployment layer is where the next 24 months of growth live.*

→ Cross-link: [2026-05-22/04 §1 real-tool benchmarks](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) · [2026-05-21/01 §1 pre-release-review EO (cyber lane)](../2026-05-21/01-big-lab-moves.md#1-eo-signing-today).

---

## 6. Claude lands in Google's Gemini Enterprise Agent Platform Model Garden {#6-claude-in-gemini}

**What happened:** Sept 28 — Google added **Anthropic's Claude models to the Gemini Enterprise Agent Platform Model Garden** — a widening of cloud procurement paths for Claude.

Backdrop: Anthropic already runs **AWS + Google Cloud + Azure** as compute providers, and now its *competitor's* enterprise agent platform ships Claude as a first-class model option. For a Google Cloud customer, there is no longer a procurement reason to prefer Gemini over Claude at the integration layer — **the choice is now capability + price, nothing else.**

**Sources:**
- [Google Cloud — Gemini Enterprise Agent Platform / Model Garden](https://cloud.google.com/products/gemini) `[primary]`
- [LLM Meter — Week of Oct 4, 2026](https://implicator.ai/llm-meter-week-of-oct-4-2026) `[aggregator]`

### Why it matters to you

- **Job lens:** **Google Cloud "Claude practice" roles** are now a real lane — Google Cloud customers who want Claude will procure through Google first. Watch Google Cloud Solutions / Antigravity / Vertex AI listings in late October for Claude-named roles.
- **Startup lens:** The multi-cloud, model-agnostic procurement reality has arrived. Build **model-agnostic** by default; your enterprise buyers will insist. The pitch deck that still says *"we are an Anthropic-exclusive stack"* loses to the one that says *"we route across Claude, GPT, Gemini based on task — here's the eval and cost graph."*
- **Insight:** This is the moment multi-cloud becomes multi-model-cloud. Prior analogue: AWS adding Oracle RDS in 2013. The incumbent's platform selling the challenger's primary input is the signal that **the layer above has become the differentiator, not the input itself.**

→ Cross-link: [`03` §3 Fable 5.1 vs GPT-6.1 Sol cost table](./03-practical-skills-and-tools.md#3-cost-table) · [`02` §3 "LLM CDN moment" thesis (2026-09-10)](../2026-09-10/02-new-emerging.md#3-model-fatigue-tooling).
