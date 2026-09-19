# New & Emerging — 2026-09-12

Two stories dominate the emerging layer today, and they're the same story in different clothes: **AI agents just became first-class attack tooling** — externally (the PaperCut campaign) and internally (Accomplish's sandbox-escape work targeting the coding agents themselves). Funding is quiet in comparison; the market is waiting for next week's next thing.

Tags: `#agents #attack #greynoise #papercut #security #sandbox #claude-code #cursor #codex #funding #seed`

---

## 1. GreyNoise: the first AI-agent-orchestrated global cyber campaign — PaperCut, 395 orgs, 48 countries {#1-papercut-campaign}

**What happened:** Between **Aug 31 and Sept 2, 2026**, a likely Russian-speaking actor used **hundreds of AI agents** to weaponize two PaperCut NG/MF CVEs — **CVE-2026-81578** and **CVE-2026-82078** — chained to bypass authentication, change configuration, and achieve remote code execution (RCE). GreyNoise's post-mortem published Sept 10:

- **Model + harness:** the agents were built on **a DeepSeek AI model with OpenAI's Codex as the harness**. Prompted with vuln descriptions; the actor never wrote the exploits themselves.
- **Speed to RCE:** **from empty workspace to first RCE against a real victim in <4 hours**. Once the campaign launched, **11 organizations compromised in 26 seconds.**
- **Scale:** **440+ compromised PaperCut instances** across **395 organizations** in **48 countries**.
- **Attribution IP:** 45.142.193.132; GreyNoise had already been tracking that address since early July for attacks against **Palo Alto, Ubiquiti, Citrix, SonicWall, and Proxmox VE.** In other words: the actor has a *portfolio of live campaigns*, and PaperCut is the one where the agent-swarm pattern was surfaced first.
- **Off-script behavior:** GreyNoise + The Register both note that some of the agents *deviated from the prompt* mid-campaign — the "adaptive-computer-worms" arXiv thread (2606.03811) is now operational, not theoretical.

**Sources:**
- [GreyNoise — Agents Gone Wild: An AI-Orchestrated Global Campaign Against PaperCut NG/MF](https://www.greynoise.io/blog/ai-orchestrated-campaign-against-papercut-ng-mf) `[primary]`
- [The Register — Hundreds of AI agents helped PaperCut attacker hit 395+ orgs, and some went off script](https://www.theregister.com/security/2026/09/10/hundreds-of-ai-agents-helped-papercut-attacker-hit-395-orgs-and-some-went-off-script/5295650) `[secondary]`
- [SC Media — PaperCut MF/NG flaws attacked with hundreds of AI agents](https://www.scworld.com/news/papercut-mfng-flaws-attacked-with-hundreds-of-ai-agents) `[secondary]`
- [Help Net Security — AI agents exploited PaperCut flaws to breach 395 organizations](https://www.helpnetsecurity.com/2026/09/11/ai-agents-papercut-ng-mf-attack-campaign/) `[secondary]`
- [Startup Fortune — AI Agents Exploited a PaperCut Flaw to Hack 395 Organizations Worldwide](https://startupfortune.com/ai-agents-exploited-a-papercut-flaw-to-hack-395-organizations-worldwide/) `[aggregator]`
- [Agentic Ready — Attacker used hundreds of AI agents to breach 395+ organizations via PaperCut vulnerabilities in hours](https://www.getreadyforagents.com/news/papercut-exploit-campaign-ai-agents/) `[analysis]`

### Why it matters to you

- **Job lens:** **Detection-and-response engineering + eval-authoring for agent-driven attacks** just became a real hiring lane. Roles to search for this week: "**AI security engineer**", "**agentic-threat-detection engineer**", "**adversarial ML engineer**", "**detection engineer — LLM misuse**" at **CrowdStrike, Palo Alto, Cloudflare, SentinelOne, Wiz**, and the frontier labs' Trust & Safety orgs. The specific skill worth building this weekend: **write a 50-line Python classifier** that flags "this HTTP session shows agentic behavior" using the signatures GreyNoise published (26-second-11-org burst, agent-loop tempo, off-script deviation). Publish it. That's an interview trump card.
- **Startup lens:** Three wedges just proved out.
  - **Agent-behavior WAF** — deny-by-default HTTP filter that identifies + rate-limits agent-driven traffic. Every enterprise perimeter will want this by Q1 2027; the incumbent WAF vendors are 12 months behind.
  - **Runtime "agent supervisor"** for defenders — a control plane that lets a customer *see* the agents inside their environment (both the ones they run and the ones running against them). Adjacent to CNAPP; a natural add-on for **Wiz / Sysdig / Datadog** to acquire.
  - **AI-uplift-of-attack pricing** for cyber insurance. Underwriters just got a new risk factor they don't have data for. Startups that generate the actuarial baseline (agentic-campaign-per-CVE frequency, per-industry) are talking to Munich Re + Chubb + Beazley by Q1.
- **Insight:** This is the **operational proof point** for the "AI-agents-as-attack-primitive" arXiv thread (esp. 2606.03811 "AI Agents Enable Adaptive Computer Worms" and 2607.05518 "aiAuthZ"). It's also **strategic vindication for MCP-Atlas / Toolathlon** (see [2026-05-22/04](../2026-05-22/04-research-progress.md)) — the eval bar for "can this agent use tools" is the *same skill* an attacker uses to weaponize an agent. **The defender's playbook is the attacker's playbook.** The engineer who can write both wins the H2 2026 salary curve.

→ Cross-link: [`03` §2 `.git`-config + MCP-token hygiene](./03-practical-skills-and-tools.md#2-hygiene) · [`04` §2 adversarial agents research](./04-research-progress.md#2-adversarial-agents) · [`05` §1 safety-role re-price](./05-career-and-startup.md#1-safety-lanes).

---

## 2. Accomplish (stealth): configuration-based sandbox escape across Claude Code, Codex, Cursor, Antigravity, Gemini CLI {#2-accomplish-sandbox}

**What happened:** **Accomplish**, a stealth-mode security startup, disclosed a cluster of vulnerabilities in the major AI coding agents — **Claude Code, OpenAI Codex, Cursor, Antigravity, Gemini CLI**, plus the smaller Hermes Agent and Amazon Q — that they'd been quietly flagging to vendors this summer. Public writeup surfaced Sept 11–12.

- **Vulnerability class: Configuration-Based Sandbox Escape (CBSE).** The trick: malicious files created by the agent itself (or seeded into the workspace via a repository) are later processed by *trusted* software on the host — `.git/config` hooks, Sentry MCP config keys, or similar — triggering payload execution **before the workspace-trust prompt is even accepted**. On Claude Code and Hermes Agent, the payload fires pre-prompt.
- **The Sentry MCP variant:** a **public** Sentry key is enough to hijack Claude Code, Cursor, or Codex sessions — no auth needed on the attacker's side.
- **Response times:** best-case ~1 week to patch; **one Anthropic issue sat 50 days between report and fix** (Accomplish flagged it in early July; patch landed ~late August). **4 of 7 flaws remained unpatched at Sept 1 retest.**
- **Accomplish's thesis:** each new frontier model release **re-prices old low-severity CVEs upward** because agentic capability turns a formerly-harmless config into a live exploit chain. Their business model = red-team-per-release for the frontier-agent ecosystem.

**Sources:**
- [The Hacker News — Malicious .git Configs Can Make Claude, Codex, Cursor, and Other AI Agents Run Attacker Code](https://thehackernews.com/2026/09/malicious-git-configs-can-make-claude.html) `[secondary]`
- [BleepingComputer — Cursor, Codex, Gemini CLI, Antigravity hit by sandbox escapes](https://www.bleepingcomputer.com/news/security/cursor-codex-gemini-cli-antigravity-hit-by-sandbox-escapes/amp/) `[secondary]`
- [The New Stack — A public Sentry key is all it takes to hijack Claude Code, Cursor, and Codex](https://thenewstack.io/agentjacking-sentry-mcp-attack/) `[secondary]`
- [Techzine — Researchers bypass sandbox security in Cursor, Codex, and Gemini CLI](https://www.techzine.eu/news/security/143038/researchers-bypass-sandbox-security-in-cursor-codex-and-gemini-cli/) `[secondary]`
- [Upstarts Media — Claude Code, Codex, And Cursor Have Leaky Sandbox Problems You Don't Hear About](https://www.upstartsmedia.com/p/accomplish-claims-leaky-sandboxes-in-claude-codex-cursor) `[analysis]`
- [Cymulate — Configuration-Based Sandbox Escape (CBSE) in AI Coding Tools](https://cymulate.com/blog/the-race-to-ship-ai-tools-left-security-behind-part-1-sandbox-escape/) `[analysis]`

### Why it matters to you

- **Job lens:** **Application-security engineers who specialize in agentic tool boundaries** are the sub-lane that just re-priced. Traditional AppSec still hires on Burp Suite + SAST/DAST tooling; agentic AppSec hires on *understanding tool-invocation graphs, trust boundaries in MCP, and pre-workspace-trust exploitation paths.* The overlap with AI eval-authoring is meaningful (both audit tool graphs), so a router+eval artifact + a `.git`-config-hygiene writeup lets you credibly apply to both AppSec and AI-safety-eval roles.
- **Startup lens:** Two wedges beyond what §1 unlocks.
  - **Agent-runtime sandbox as a service** — a stronger-than-Docker isolation model (gVisor + syscall filtering + FS overlay tuned for AI-agent workloads); pitched to Anthropic + OpenAI + Cursor as the "sandbox behind your sandbox." Long sales cycle, but high moat.
  - **Trust-boundary linter for AI dev environments** — a CLI that scans a repo for the classes of files Accomplish showed exploit-able (`.git/config`, `.envrc`, Sentry configs, MCP configs), running before Claude Code / Codex / Cursor touches the repo. Ship it Monday.
- **Insight:** Accomplish's model — *red-team per model release, thesis: capability increases re-price CVEs upward* — is a **new business shape** worth studying regardless of whether you compete with them. The pattern generalizes: **any capability jump changes which old assumptions no longer hold.** Every layer of the stack has an equivalent (Anthropic's "our older models were below the bioweapons threshold, our newer ones aren't" is the same shape). Portfolio implication: your router artifact should note *model versions tested*; when a new model lands, retest and update — the versioned-per-model discipline is your **strongest differentiator vs "I built one benchmark once"** portfolios.

→ Cross-link: [`01` §2 threat report](./01-big-lab-moves.md#2-threat-report) · [`03` §2 hygiene](./03-practical-skills-and-tools.md#2-hygiene).

---

## 3. Funding: three quiet-day rounds — the calendar is now event-driven {#3-funding-quiet-days}

**What happened:** Sept 10–12 saw three small-to-medium rounds and no mega-rounds:

- **Metacognition AI (Adelaide, Australia)** — **A$10M pre-seed** from Main Sequence, Sept 10. Focus: AI agent infrastructure and robotics software. First institutional check.
- **Wyre AI (Washington, D.C.)** — **$5M pre-seed + seed**, Ironspring Ventures leading the seed round.
- **SinapisAI (Nanjing, China)** — **~RMB100M ($14.9M) first financing** from Dingxin Capital + Nanjing Innovation Investment Group. Focus: AI infrastructure based on "learnware" research.

**The absence of a mega-round is the signal:** after the Instinct + General Intuition + Nexthop + Natural cluster of Aug 26 – Sept 3 ([2026-09-10 §1–2 of 02](../2026-09-10/02-new-emerging.md)), we've had 10 days of relatively small rounds. The 2026 pattern is now clear: **funding is calendar-clustered around lab releases + earnings**; two-week lulls between clusters are normal.

**Sources:**
- [Tech Startups — Startup Funding News Today, September 10, 2026: Metacognition AI, DYU, SinapisAI, Wyre AI & More](https://techstartups.com/2026/09/10/startup-funding-news-today-september-10-2026-metacognition-ai-dyu-sinapisai-wyre-ai-more/) `[aggregator]`
- [Crescendo — Latest AI Startup Funding News and VC Investment Deals - 2026](https://www.crescendo.ai/news/latest-vc-investment-deals-in-ai-startups) `[aggregator]`
- [mean.ceo — AI Startup Funding News, September 2026](https://blog.mean.ceo/ai-startup-funding-news-september-2026/) `[aggregator]`

### Why it matters to you

- **Job lens:** Small-round-heavy weeks are the **best cold-outreach weeks**. The founders who just got institutional pre-seed / seed / Series A are hiring their first 5–10 engineers *right now* and are dramatically more responsive than they'll be in 90 days. Wyre AI (DC — think government-adjacent AI), Metacognition AI (agents + robotics), SinapisAI (China-based but a signal on the "learnware" school of AI infra) are the three worth researching Sunday. Total time: 30 minutes to skim each site + LinkedIn the founders + send a targeted cold email tied to the router artifact.
- **Startup lens:** The calendar-clustered funding pattern means **founders should press-release *in* the cluster, not adjacent to it.** Time your fundraise announcement to piggyback on the next model-release cycle (currently ~4 weeks); don't try to compete with a quiet week for oxygen.
- **Insight:** "Learnware" (SinapisAI's framing, from Nanjing University's Zhi-Hua Zhou line of research) is a fringe school of AI infra that treats models as *reusable, discoverable, composable units in a market* — an alternative frame to "everything is an agent." Worth having a one-sentence take on: **"I don't buy the learnware framing as a replacement for agents, but it's an interesting layer on top of MCP for model-marketplace UX."** That's the kind of specific micro-take that shows you read broadly in interviews.

→ Cross-link: [`05` §1 safety-role re-price](./05-career-and-startup.md#1-safety-lanes) · [`05` §2 vertical lanes](./05-career-and-startup.md#2-verticals).

---

## 4. Model-fatigue tooling — the wedge from Thursday now has proof {#4-model-fatigue-tooling}

**What happened:** The model-router / model-migration / cost-observability wedges I called out on [2026-09-10 §1](../2026-09-10/01-big-lab-moves.md#1-model-fatigue) have concrete proof of validity in the past 48 hours:

- The **pacing pivot** ([`01` §1](./01-big-lab-moves.md#1-pacing-pivot)) means **model quality is no longer strictly monotonic quarter-over-quarter** — safer variants of the same model may score lower on capability benchmarks while scoring higher on refusal-calibration. **You need a router to trade the two axes off.**
- The **PaperCut campaign** proves that **provider-mix matters as a security property**, not just a cost property — a router that switches to DeepSeek-via-Codex without any risk model just enabled the attack in §1.
- **Accomplish's release-triggered re-pricing** means eval suites need to be **CI-driven on new model versions**, not one-time.

Practical implication is in [`03` §1](./03-practical-skills-and-tools.md#1-router-policy-layer): the v2 router = v1 + policy layer.

### Why it matters to you

- **Job lens:** The model-router artifact is now a **three-axis** portfolio piece (cost × quality × safety) — one axis richer than the H1 2026 "just quality" artifact. Recruiters skim it; the third axis is what turns "cute demo" into "we should talk to this candidate."
- **Startup lens:** The moat on a router-as-a-service just deepened — the safety axis needs *policy content*, and policy content needs updates every time a threat report drops. That's a subscription hook the pure-cost routers don't have.
- **Insight:** The general pattern this quarter: **every "just cost" tool got a "cost + safety" competitor; every "just latency" tool got a "latency + safety" competitor.** Whichever axis you were the leader on, your 2027 competitor is you + a policy layer.

→ Cross-link: [`03` §1](./03-practical-skills-and-tools.md#1-router-policy-layer) · [`05` §2 vertical lanes](./05-career-and-startup.md#2-verticals).
