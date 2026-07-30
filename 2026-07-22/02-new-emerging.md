# New & Emerging — 2026-07-22

Two threads that matter today, both under the same umbrella: **the sandbox is not the container it claimed to be**, and **the free-national-AI arms race just picked up its first buyer**.

Tags: `#security #sandbox #agents #cursor #codex #antigravity #cve #policy #sovereignty #korea #freetier`

---

## 1. Pillar Security's "Week of Sandbox Escapes" — every coding agent you demoed is on the list {#1-pillar-sandbox}

**What happened:** Pillar Security researchers **Eilon Cohen, Dan Lisichkin, and Ariel Fogel** dropped Day 1 of a coordinated **"Week of Sandbox Escapes"** series — **one write-up per day**, targeting the coding-agent stack the CS-grad portfolio market runs on:

- **Cursor** — CVE-2026-48124, sandbox-to-host code execution. **A Claude-hooks configuration file could be crafted to run commands outside the sandbox.** **Patched in Cursor 3.0.0.**
- **OpenAI Codex CLI** — sandbox escape via agent-written files that trusted host tools later execute.
- **Google Gemini CLI** — same pattern.
- **Google Antigravity** — same pattern; Google **declined to patch** citing the "trust-issue-not-classic-escape" framing.

Pillar's taxonomy sorts **seven findings into four failure modes**:

1. **Denylists that cannot keep pace with the OS** — banning `rm -rf` doesn't ban `find … -exec rm`.
2. **Workspace config that is really code** — the Claude-hooks file in Cursor was config-as-code with execution semantics.
3. **"Safe" command lists that trust a name over its arguments** — `git` is on your allow-list; `git config --global core.pager 'sh -c …'` is not.
4. **Privileged local daemons that sit outside the box entirely** — sockets, launchers, and MCP daemons the sandbox never wrapped.

**The frame:** *"AI agents can escape sandboxes without ever breaking them"* — because the sandbox doesn't own the tools the agent writes files for.

**Sources:**
- [Pillar Security — The Week of Sandbox Escapes (announcement)](https://www.pillar.security/blog/the-week-of-sandbox-escapes) `[primary]`
- [BleepingComputer — Cursor, Codex, Gemini CLI, Antigravity hit by sandbox escapes](https://www.bleepingcomputer.com/news/security/cursor-codex-gemini-cli-antigravity-hit-by-sandbox-escapes/) `[secondary]`
- [CSO Online — AI agents can escape sandboxes without ever breaking them](https://www.csoonline.com/article/4199408/ai-agents-can-escape-sandboxes-without-ever-breaking-them.html) `[analysis]`
- [Techzine Global — Researchers bypass sandbox security in Cursor, Codex, and Gemini CLI](https://www.techzine.eu/news/security/143038/researchers-bypass-sandbox-security-in-cursor-codex-and-gemini-cli/) `[secondary]`
- [Neowin — Pillar Research shows sandboxes are inadequate for agentic AI, Google decides not to patch](https://www.neowin.net/news/pillar-research-shows-sandboxes-are-inadequate-for-agentic-ai-google-decides-not-to-patch/) `[secondary]`
- [The Next Web — AI coding agents keep escaping their sandboxes, study finds](https://thenextweb.com/news/ai-coding-agents-sandbox-escapes-pillar) `[secondary]`
- [Windows Forum — Cursor 3.0.0 Fixes CVE-2026-48124 Sandbox-to-Host Code Execution](https://windowsforum.com/threads/cursor-3-0-0-fixes-cve-2026-48124-sandbox-to-host-code-execution.439817/) `[secondary]`

### Why it matters to you

- **Job lens:** The taxonomy Pillar published is essentially **a job description for the AI-security engineer role**. Every named failure mode (denylist / config-as-code / arg-blind allow-list / privileged daemon) maps onto a **specific hire** that Anthropic Trust, OpenAI Model Behavior, Palo Alto Prisma AIRS, and the ~15 mid-sized agentic-SOC startups (Exaforce et al. from [2026-05-22/02 §2](../2026-05-22/02-new-emerging.md#2-exaforce)) will make in the next two quarters. **Do this today:** save the four failure modes into your notebook, and **when a recruiter asks "what security threat model do you think about when building agents?" you list all four with citations.** You are not competing against other CS grads for that answer — you're competing against people who Googled "agent security" once.
- **Startup lens:** **Google declining to patch** the Antigravity finding is the wedge. Every enterprise that adopted Antigravity or Gemini CLI now has an **unpatched vendor issue on their risk register**. The buyer is the *enterprise IT / GRC / AppSec* team of the org that already picked Google's coding agent — and they need to explain it to the board this quarter. **Middleware startup shape:** a policy-and-audit sidecar that wraps *any* agent CLI (Claude Code / Codex / Gemini CLI / Antigravity), enforces the four Pillar failure-mode fixes, and produces an auditable log the GRC team can hand to Deloitte during their next SOC 2 review. **Price it per-seat like a security control, not per-token like an AI product.**
- **Insight:** The deep story is *config-as-code eating everything*. As agents get more capable, **the config file** (`.claude/hooks.json`, `mcp.json`, `.cursorrules`, `AGENTS.md`, `settings.json`) **becomes the highest-privilege attack surface in the developer environment** — because it's the only surface the agent can write to that later gets executed by the host. Every future coding-agent security review will start with "show me your config-file model." Build the muscle now: treat every workspace config as **untrusted input at the same security tier as user prompts**.

→ Cross-link: [`01` §1 the OpenAI × HF containment breach (the same class of failure at frontier scale)](./01-big-lab-moves.md#1-openai-hf-breach) · [`04` §1 AgentRedBench (the benchmark that measures exactly this)](./04-research-progress.md#1-agentredbench) · [`03` §1 how to write the hook that stops it tonight](./03-practical-skills-and-tools.md#1-claude-code-caps).

---

## 2. South Korea "AI for All" — first G20 nation with free national AI + agentic gov-services layer {#2-korea-aiforall}

**What happened:** The Korean **Ministry of Science and ICT** opened bidding on **July 13** for a program called **AI for All**, moving into public tender this week:

- **Every South Korean resident gets two tiers, both free and un-metered:**
  - **Tier 1:** general-purpose AI chatbot. **Public beta late September 2026, national launch before year-end.**
  - **Tier 2:** a **proactive agent** that discovers government benefits the citizen qualifies for **and files the paperwork for them.**
- **Sovereignty mandate:** ≥50% of each system must run on **certified domestic Korean models** — but reporting notes the compute layer is **still Nvidia** (Korea has no domestic equivalent).
- **Market impact:** paired with Korea's new AI Act, this is reportedly triggering **~23M ChatGPT-paying Koreans to cancel** (per Techtimes framing — read with caution).
- **The Nadella "editorially controlled" comment:** Satya Nadella publicly characterized Microsoft's Fable model as **"editorially controlled"** — the emerging PR frame for the sovereignty vs neutrality trade, and a tell that Microsoft plans to sell Fable into *exactly* the sovereign-tier tenders Korea is running.

**Sources:**
- [UPI — South Korea launches free AI agent project for all citizens](https://www.upi.com/Top_News/World-News/2026/07/13/ai-for-everyone-public-services/9121783997023/) `[secondary]`
- [TechTimes — South Korea Becomes First G20 Nation to Give All Citizens Free AI Access](https://www.techtimes.com/articles/320397/20260714/south-korea-becomes-first-g20-nation-give-all-citizens-free-ai-access.htm) `[secondary]`
- [TechTimes — Korea Pairs AI Law With Free Chatbot as 23 Million Quit Paying for ChatGPT](https://www.techtimes.com/articles/321169/20260721/korea-pairs-ai-law-free-chatbot-23-million-quit-paying-chatgpt.htm) `[analysis]`
- [Indoneo — South Korea's free AI for everyone runs on American chips it cannot replace](https://www.indoneo.com/tech-ai/south-korea-free-ai-nvidia-gpu-dependency/) `[analysis]`
- [AIToolsRecap — AI News July 22 2026: Gemini 3.6 Flash Launches, Nadella Calls Fable "Editorially Controlled", South Korea Plans Free National AI](https://aitoolsrecap.com/Blog/ai-news-july-22-2026) `[aggregator]`
- [AI in Asia — South Korea Moves to Give Every Citizen a Free AI (MSIT deep dive)](https://aiinasia.com/north-asia/south-korea-ai-for-all-free-national-chatbot-msit-north-asia-deep-dive-2026-07-15) `[analysis]`

### Why it matters to you

- **Job lens:** "Sovereign AI" as a *specific job category* just got a first-mover reference customer. If your resume lists **multilingual eval, MoE / mixed-model routing, or on-prem inference**, add **"sovereign-tier deployment"** as a keyword. The buyers over the next 24 months will be **MSIT (Korea), UK Sovereign AI Fund (already an Isomorphic Labs LP from 2026-05-19), the EU AI Sovereignty Vehicle**, and their FDE contractors (PwC, Accenture, Deloitte, EY — the same firms you already targeted, with a new line-item budget). US frontier labs will hire **"sovereign solutions engineers"** at $250K+ to service these accounts. Adjacent, less-crowded than the pure-FDE lane.
- **Startup lens:** **Tier 2 — the "proactive agent that files paperwork" — is the highest-value primitive** in Korea's plan. Nothing about that is Korea-specific. The **US and EU equivalents** ("federal benefits triage agent", "EU citizen services agent") are wedges an American CS grad can pitch to a US or EU civic-tech VC (Bloomberg Philanthropies, Kapor, Emerson Collective) with the Korean deployment as the market-validation citation. **Founder pitch line:** *"Korea just proved a state will fund a free-forever benefits-filing agent for every citizen. Here's ours for the US Medicaid renewal cliff."*
- **Insight:** Read what the Indoneo piece calls out — **the sovereignty story is 50% Korean at the model layer and 100% American at the chip layer**. Every "sovereign AI" story of the next 18 months will hit the same wall. Positioning for a job or startup: **the *interesting* sovereignty problem isn't which model — it's which compute**. If you can talk about **Nvidia export-control regime × domestic-inference-cost sensitivity** with actual numbers, you separate from every other candidate at every Anthropic / OpenAI / Google policy-adjacent interview this quarter.

→ Cross-link: [2026-05-19/02 Isomorphic Labs Series B (first Lab+VC+Sovereign+Industry four-corner deal)](../2026-05-19/02-new-emerging.md) · [`01` §3 lobbying priorities (defense procurement / cyber)](./01-big-lab-moves.md#3-anthropic-lobbying) — the US Fable-vs-open-model version of the same story.
