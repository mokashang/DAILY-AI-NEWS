# TL;DR — 2026-09-13 (Sunday)

Sixty-second skim. **The story of the week is the agentic-enterprise reveal — packaged, named, priced, and about to get sued.** **Salesforce shipped seven named Agentforce agents (Casey · Paige · Carter · Hunter · Marshall · Piper · Fin) on Sept 11**, two working days before Dreamforce, and bolted on a governance layer (Trusted Enterprise AI Harness) and a **long-horizon runtime** aimed at week-scale goals, not chat turns. Underneath: **Sakana AI dropped Fugu Ultra v2 + Fugu Max (Sept 11)** — a language-model *orchestrator* over open-weight sub-models — that beat Opus 5 and Fable 5 on the Chartography visual-reasoning benchmark (48.3 vs 27.3 / 29.5), the first credible non-frontier lab to top a frontier bench in 2026. Meanwhile: **AI-coding-agent sandbox escapes** are now a named CVE class (CVE-2026-48124 in Cursor; goose/Claude Code/Codex patched; malicious `.git` configs work across seven agents), and **enterprise-AI-agent security & governance startups took $435M across 12 rounds Apr–Sept**. For you: **the agentic-enterprise stack has three new job families (agent orchestration engineer, agent-safety engineer, agent-governance PM) and one new startup wedge (agent trust infra) — all hiring or fundable right now.**

---

1. **Salesforce ships seven "job-ready" Agentforce agents + a long-horizon runtime (Sept 11, T-2 to Dreamforce).** Casey / Paige / Carter / Hunter / Marshall / Piper / Fin — one per business function; six generally available, Hunter piloted through Nov. New "Trusted Enterprise AI Harness" governance layer (six pillars). Cumulative Agentforce + Slack usage passed **7B "Agentic Work Units"**; 3.2B in Q2 alone. → [`01` §1](./01-big-lab-moves.md#1-agentforce-seven) `#salesforce #agentforce #enterprise #agents`

2. **Sakana AI: Fugu Ultra v2 + Fugu Max beat Opus 5 and Fable 5 on Chartography (Sept 11).** Not a bigger model — a **language-model orchestrator** that routes tasks across a fixed pool of open-weight and specialized models. **48.3 on Chartography vs 27.3 (Opus 5) and 29.5 (Fable 5).** First 2026 non-frontier lab to top a frontier benchmark. Confirms the "layer above the model" thesis from [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact). → [`02` §1](./02-new-emerging.md#1-fugu) `#sakana #orchestration #open-weights`

3. **Anthropic's global-expansion trace: Bengaluru open, Seoul + Paris + Munich queued, EMEA revenue 9× YoY.** India is Claude's **second-largest market globally**; workforce tripling internationally. Second-order: **the international FDE/Solutions hiring wave is now measurable** — this is where new-grad reqs will land next. → [`01` §2](./01-big-lab-moves.md#2-anthropic-global) `#anthropic #hiring #international #careers`

4. **AI-coding-agent sandbox escapes graduate to a CVE class (September 2026).** CVE-2026-48124 in Cursor (Claude-hooks config exec); malicious `.git` configs run attacker code across Claude Code / Codex / Cursor / goose / Antigravity; Accomplish's disclosure catalog is now the public tracker. **OpenAI published three CVEs same-day for Codex.** → [`03` §1](./03-practical-skills-and-tools.md#1-sandbox-escapes) `#security #cve #coding-agents`

5. **Enterprise-AI-agent security & governance = $435M / 12 rounds, Apr–Sept 2026.** Nine rounds specifically on "safe enough to run inside a business." **Euno $23M Series A (Sept 9)** — enterprise data infra for agent context; **Clay $115M (Sequoia + a16z)** — revops workflow automation; **CloudNC $20M** — vertical AI for CNC. The picks-and-shovels barbell has a third pole now: **agent trust infra.** → [`02` §2](./02-new-emerging.md#2-agent-trust-funding) `#funding #agent-safety #vertical-ai`

6. **Salesforce's Trusted Enterprise AI Harness = the first named governance framework of the agentic-enterprise era.** Six pillars: Trusted Context / Agency / Action / Governance / Security / Models. **This is the customer-visible artifact your résumé needs to speak to** if you're targeting Solutions / FDE / Integration roles in H2. → [`03` §2](./03-practical-skills-and-tools.md#2-trusted-harness) `#governance #enterprise #careers`

7. **Best-practice: audit your Claude Code sandbox this weekend.** Read the malicious-`.git`-config write-up. Patch Claude Code + Cursor + Codex to latest. Turn off "auto-execute git commands." **Take 20 minutes; ship a public repo with a hardening checklist** — this becomes the artifact you cite in security-focused FDE interviews for the rest of Q4. → [`03` §3](./03-practical-skills-and-tools.md#3-hardening-checklist) `#claude-code #security #artifact`

8. **Research: Fugu paper + the memory-benchmarks class of 2026 (MemoryArena, AMA-Bench, agent-native memory systems).** The frontier of agent research has moved *decisively* to **orchestration + memory** — not bigger single models. The eval-authoring skill your résumé needs now includes: a memory eval (retrieval, test-time learning, long-range understanding, selective forgetting) and an orchestration eval (task routing under budget). → [`04` §1](./04-research-progress.md#1-fugu-orchestration) `#arxiv #agents #memory #orchestration`

9. **Career: AI Engineer $145K–$310K (real offer data); MLE $128K–$186K base; remote +21% premium.** LinkedIn 2026 Jobs on the Rise: **AI Engineer is #1**; 7 of 10 fastest-growing tech roles are AI-related. The Salesforce Agentforce launch just opened a fourth job family: **agent orchestration engineer** — internal at every F500 by end-2027. → [`05` §1](./05-career-and-startup.md#1-hiring-map) `#careers #salary #ai-engineer #mle`

10. **The re-price of the week:** *building a chatbot* lost value again (Sakana's orchestrator was built by ~30 people); **governance / safety / orchestration** all gained value. The scarce hire is now the person who can (a) route a task across 3 models, (b) prove it's safe with an eval, (c) explain it to compliance. All three fit in one weekend artifact. → [`05` §2](./05-career-and-startup.md#2-reprice) `#skills #careers #artifact`

---

## One thing to DO this Sunday

→ **Ship a "trusted-agent starter" repo: a 3-model router + a 5-case eval suite + a 6-item hardening checklist matching Salesforce's Trusted Enterprise AI Harness.** Build it against Fable 5.1 / GPT-6 Astra / Gemini 3.8 Flash. Publish under your GitHub with a README that names the six pillars. This becomes your interview trump card at Anthropic-Solutions, OpenAI-FDE, Salesforce-Agentforce, and any AI Engineer role at a F500 for the rest of Q4. Details in [`03` §3](./03-practical-skills-and-tools.md#3-hardening-checklist).

## Watchlist deltas

- 🆕 **Agentic-enterprise packaging (Salesforce Agentforce named agents):** new thread. Track: (a) Dreamforce follow-through (Sept 15–17); (b) whether Microsoft / Google / ServiceNow ship named-agent equivalents this month.
- 🆕 **Orchestrator-language-model class (Sakana Fugu):** new thread. Watch whether the OSS community forks the orchestrator idea onto open-weight sub-models this quarter — the "compiler layer" for LLMs is being born.
- 🆕 **AI-coding-agent sandbox CVE class:** new thread. Track vendor patch cadence and whether cyber-insurance carriers begin requiring proof-of-patch on AI agent tooling by year-end.
- 🆕 **Agent trust infra funding pole (~$435M / 12 rounds):** new thread. If this holds two more quarters, "AI-agent-security engineer" is a hire-in-2027 job family; the wedge is fundable now.
- ➡️ **Anthropic IPO window (from 2026-09-10):** unchanged — filing expected September. IPO + international-office wave = compensation reset trigger for the whole sector.
- ➡️ **Model-fatigue (from 2026-09-10):** intact — Fugu Ultra v2 became the newest data point, but the story stays.
- ⬇️ **"Which model is best" as a career skill:** further deprecated by Fugu (the *orchestrator* now decides). Router + evals + governance are the new fluency.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-agentforce-seven) (Agentforce seven) + [`02` §1](./02-new-emerging.md#1-fugu) (Fugu Ultra v2) |
| 20 min | [`03` §1–3](./03-practical-skills-and-tools.md) — sandbox CVE class + Trusted Harness + hardening checklist |
| Today | [`03` §3](./03-practical-skills-and-tools.md#3-hardening-checklist) — build and publish the trusted-agent starter |
| Tonight | [`04` §1](./04-research-progress.md#1-fugu-orchestration) — read the Fugu technical report + one MemoryArena-class paper |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
