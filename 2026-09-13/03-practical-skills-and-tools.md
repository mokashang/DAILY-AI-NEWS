# Practical Skills & Tools — 2026-09-13

Act on these today. The theme this Sunday: **the agentic-enterprise moment is also an agent-hardening moment.** The three items — the sandbox-CVE class, Salesforce's Trusted Enterprise AI Harness, and a hardening checklist you can publish tonight — form one connected story. The first is the threat, the second is the customer-visible framework, the third is your artifact for both.

Tags: `#claude-code #cursor #codex #security #cve #governance #agents #harness #artifact`

---

## 1. The AI-coding-agent sandbox-CVE class — what to patch, why it matters, what to check on your own machine tonight {#1-sandbox-escapes}

**What happened:** A well-documented set of AI coding-agent sandbox-escape vulnerabilities graduated to a CVE class in Sept 2026. The pattern is the same across seven agents: **the agent respects its own sandbox, but tools *outside* the sandbox (git, python venv, editor extensions) don't know the file they're about to trust was written by the agent.** The attacker doesn't need to break the sandbox — they let the agent write a poisoned file, then wait for the host to trust it.

**Concrete vulnerabilities to know:**

| Vector | Affected agents | Fix status | CVE |
|---|---|---|---|
| **Malicious `.git` config** — a `[core] hooksPath = ...` in a repo you clone triggers arbitrary code on `git status` | Claude Code / Codex / Cursor / goose / Antigravity | Partial (patched in Claude Code + Cursor + goose; other CLIs still executing repository-supplied commands as of Sept 1 retest) | Multiple |
| **Cursor Claude-hooks config exec** | Cursor <3.0.0 | Fixed in 3.0.0 | **CVE-2026-48124** |
| **`.git` metadata indirection (pointer file)** — bypass sandbox path-based rules | Multiple | Partial | — |
| **Modified venv → Python interpreter exec** | Multiple | Partial | — |
| **Codex sandbox escape family** | OpenAI Codex | 3 CVEs published same-day; fixes shipped | 3 x CVE |

**What to do tonight (15 minutes):**

1. **Update everything.** `claude update`, upgrade Cursor to 3.0.0+, `pip install -U openai-codex` (or brew, depending on your install), Antigravity to latest.
2. **Add `.git/config` to your "review before trusting" list** for any repo you didn't create. `git config --list --local` on any new clone before running an agent inside it.
3. **Turn off "auto-execute git commands"** in Cursor / Codex CLI settings. Cost: 10 seconds of extra confirmation per git operation. Value: closes the whole `.git`-config family.
4. **Isolate agent workspaces.** Run coding agents inside a container or a dedicated user account; do not let them read your home directory.
5. **Publish your patched-versions list** as a public gist. Recruiters at security-conscious labs will find it via GitHub.

**Sources:**
- [The Hacker News — Malicious .git Configs Can Make Claude, Codex, Cursor, and Other AI Agents Run Attacker Code](https://thehackernews.com/2026/09/malicious-git-configs-can-make-claude.html) `[secondary]`
- [BleepingComputer — Cursor, Codex, Gemini CLI, Antigravity hit by sandbox escapes](https://www.bleepingcomputer.com/news/security/cursor-codex-gemini-cli-antigravity-hit-by-sandbox-escapes/) `[secondary]`
- [Techzine — Researchers bypass sandbox security in Cursor, Codex, and Gemini CLI](https://www.techzine.eu/news/security/143038/researchers-bypass-sandbox-security-in-cursor-codex-and-gemini-cli/) `[secondary]`
- [Upstarts Media — Accomplish claims leaky sandboxes in Claude, Codex, Cursor](https://www.upstartsmedia.com/p/accomplish-claims-leaky-sandboxes-in-claude-codex-cursor) `[secondary]`
- [DevOps.com — Security Risks from AI Coding Agents Expand Beyond the Sandbox: Pillar](https://devops.com/security-risks-from-ai-coding-agents-expand-beyond-the-sandbox-pillar/) `[analysis]`
- [VibeEval — Security Harness for AI Agents, September 2026](https://vibe-eval.com/updates/security-harness-for-ai-agents-sep-2026/) `[analysis]`

---

## 2. Salesforce's Trusted Enterprise AI Harness — a six-pillar framework you can borrow verbatim for interviews {#2-trusted-harness}

**What happened:** Salesforce shipped the **Trusted Enterprise AI Harness** alongside the seven named Agentforce agents ([`01` §1](./01-big-lab-moves.md#1-agentforce-seven)). It's a six-pillar governance framework aimed at F500s already running agents from multiple vendors:

| Pillar | What it covers | What to build against it |
|---|---|---|
| **1. Trusted Context** | What data the agent can see + how it's grounded | RAG hygiene; per-agent context scopes |
| **2. Trusted Agency** | What actions the agent is authorized to take | Policy engine; role-based tool allow-lists |
| **3. Trusted Action** | Reversibility + audit of every action | Two-phase commit; action logs; undo primitives |
| **4. Trusted Governance** | Who signs off + who reviews + who audits | Approval workflow; escalation; SoD (segregation of duties) |
| **5. Trusted Security** | Sandbox integrity + secret handling | See [`03` §1](./03-practical-skills-and-tools.md#1-sandbox-escapes) sandbox CVE class + secret managers |
| **6. Trusted Models** | Which models are approved for which class of task | Model registry; per-model policy; eval-gated approval |

This is the **first widely-published governance framework for multi-vendor agents**, which is why it matters — every enterprise customer buying Anthropic + OpenAI + Google + custom is now asking their AI team to map to *some* framework, and this is the one currently the loudest.

**How to use it:**

1. **Interview language:** Learn the six pillars cold. When asked "how would you govern agents in an enterprise setting" — cite the framework, then propose your own tightening on 1–2 of the pillars. Signals fluency in the exact vocabulary customers use.
2. **Repo template:** Structure your public artifact ([`03` §3](./03-practical-skills-and-tools.md#3-hardening-checklist)) as one folder per pillar. This becomes a hire-me README even before recruiters read the code.
3. **Startup pitch shape:** If you're building anything in the [`02` §2](./02-new-emerging.md#2-agent-trust-funding) agent-trust-infra pole, mapping your product to one of the six pillars *by name* is the single fastest way to make a $23M-Series-A pitch legible to enterprise buyers.

**Sources:**
- [Salesforce Newsroom — Salesforce Expands Agentforce With a New Portfolio of AI Agents](https://www.salesforce.com/news/stories/agentforce-job-ready-ai-agents/) `[primary]`
- [Futurum — Salesforce's Job-Ready Agents Target Enterprise AI's Biggest Gap](https://futurumgroup.com/insights/salesforces-job-ready-agents-target-enterprise-ais-biggest-gap/) `[analysis]`
- [Unite.AI — Salesforce Debuts Job-Ready Agentforce Agents and Long-Horizon Runtime](https://www.unite.ai/salesforce-debuts-job-ready-agentforce-agents-and-long-horizon-runtime/) `[secondary]`

---

## 3. The trusted-agent starter — one weekend, six-pillar mapping, becomes your Q4 interview artifact {#3-hardening-checklist}

**What happened:** The convergence of §1 (a real threat) and §2 (a named framework) creates a rare artifact opportunity: **a public GitHub repo you can build in one Sunday that answers the "how would you deploy agents at an enterprise" interview question in code, not slides.**

### The repo spec (build tonight, 4 hours)

**Name:** `trusted-agent-starter` (or better, your name for it)

**What it contains:**

```
trusted-agent-starter/
├── README.md              ← names the 6 pillars, one paragraph each
├── router/
│   └── route.py           ← 3-provider router (Fable 5.1, GPT-6 Astra, Gemini 3.8 Flash)
├── evals/
│   └── suite.py           ← 5 cases: cheap-summary · long-context · coding · tool-use · refusal
├── policy/
│   └── policy.yaml        ← declared allow-lists per (agent, tool, action)
├── audit/
│   └── log.py             ← append-only JSON log of every model call + tool call
├── sandbox/
│   ├── HARDENING.md       ← the 15-minute checklist from §1 above
│   └── check_git_config.sh
└── docs/
    └── PILLAR_MAP.md      ← which folder maps to which of the six pillars
```

**The 5-case eval suite** (same as [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact), keep it): cheap-summary · long-context · coding · tool-use · refusal. Score cost + latency + quality per model. Publish leaderboard on push.

**The audit log** is the highest-signal artifact for interviewers. It answers "how would you prove the agent did what it says it did" — the question every compliance officer will ask before Q1 2027.

### Why this is the artifact of the moment

- **Answers four interview questions at once:** (1) do you route models? (2) do you write evals? (3) do you think about governance? (4) do you think about security? Every one of those is a live question at Anthropic-Solutions / OpenAI-FDE / Salesforce-Agentforce / any F500 AI team.
- **Ships in one Sunday.** ~400 lines. Uses the router from last edition as the seed. Extends into governance/security in maybe 3 additional files.
- **Names the six pillars in the README.** Recruiters find the readme in a 20-second scan; the six-pillar list is the "I speak your customer's language" signal.
- **Ages beautifully.** When Anthropic ships Fable 5.2 next month, add a row. When Salesforce ships an eighth Agentforce agent, add a mapping. The artifact stays fresh while your competitors' 2024 chatbot repos rot.

### Do this before Monday morning

- [ ] Fork last edition's router repo (or build the router first, then this)
- [ ] Add `policy/`, `audit/`, `sandbox/` folders per above
- [ ] Write the `PILLAR_MAP.md` mapping folders → pillars
- [ ] Ship the sandbox-hardening checklist from §1 as `sandbox/HARDENING.md`
- [ ] Push. Pin the repo on your GitHub profile. Link it from your LinkedIn.

**Sources:**
- [`03` §1 the sandbox-CVE class (this file)](#1-sandbox-escapes)
- [`03` §2 the Trusted Enterprise AI Harness (this file)](#2-trusted-harness)
- [2026-09-10/03 §3 the router artifact — the base you're extending](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact)
- [Salesforce — Agentforce launch (primary source for pillar naming)](https://www.salesforce.com/news/stories/agentforce-job-ready-ai-agents/) `[primary]`

---

## 4. One-line habits worth keeping this week {#4-habits}

- **Weekly `git config` audit** on every repo you didn't create. `git config --list --local` is 2 seconds; catches the whole `.git`-config-hijack class.
- **Cache-hit rate check** — a follow-through from [2026-09-10/03 §1](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics). If your cache-hit rate on long system prompts is below 70%, the volatile bits are in the wrong place; move them to the end of the message.
- **One-artifact-a-week cadence.** This week: the trusted-agent starter. Next week: a memory eval ([`04` §3](./04-research-progress.md#3-eval-suite-template)).
- **Read one arXiv paper end-to-end per week.** This week: the Fugu Technical Report ([`04` §1](./04-research-progress.md#1-fugu-orchestration)). Twenty minutes for the intro + method; skim the eval; that's enough to name-drop it well.

### Sources
- [Anthropic Engineering blog](https://www.anthropic.com/engineering) `[primary]`
- [Nimbalyst — Claude Code Skills: A Practical 2026 Guide](https://nimbalyst.com/blog/claude-code-skills-guide/) `[analysis]`
- [Firecrawl — 14 Best Claude Code Skills for Developers in 2026](https://www.firecrawl.dev/blog/best-claude-code-skills) `[analysis]`
- [AgentsRoom — 50 Claude Code Tips & Tricks: Ship 10x Faster in 2026](https://agentsroom.dev/claude-code-tips) `[analysis]`
