# Career & Startup — 2026-06-09

Job market, VC trends, skills to build, startup playbook.

---

## 1. The Anthropic Claude Partner Network just opened a new FDE hiring lane — apply this week <a id="1-partner-network"></a>

**Context.** Anthropic announced the **Claude Partner Network (Services Track + Partner Hub)** on June 3 ([`02` §2](./02-new-emerging.md#2-partner-network)). This is the channel-side complement to OpenAI's M&A-side bet on Tomoro ([2026-05-19](../2026-05-19/02-new-emerging.md)).

**Apply table (this week — before the public S-1 wire pushes applicant volume 5×):**

| Layer | Employer type | Comp band (US, per [2026-06-08/05 §1](../2026-06-08/05-career-and-startup.md#1-fde-comp)) | What they want |
|---|---|---|---|
| **Direct** | Anthropic Solutions / Customer Engineering / FDE | $250–$400K base, **$400–500K TC at senior** ([Perspective AI 1,200-person FDE comp report](https://getperspective.ai/blog/2026-forward-deployed-engineering-compensation-report-1200-fdes)) | Top 5–10%; reference Karpathy + Series H + 80%-Claude-authored |
| **Big-4 / SI** | PwC, Deloitte, Accenture, EY AI-engineering practices | $130–$200K base, $180–$280K TC | Volume hiring toward PwC's 364K Claude-certified-global target ([2026-05-15](../2026-05-15/01-big-lab-moves.md)) |
| **Boutique** | 10–50-person Anthropic-specialist shops | $140–$220K base, $180–$300K TC + equity | Under-marketed; few applicants per role; ship-fast culture |
| **OpenAI FDE (NYC/SF)** | OpenAI Deployment Co | Per [2026-06-08/05 §1](../2026-06-08/05-career-and-startup.md#1-fde-comp); $400–500K senior TC | Tomoro integration absorbing 150 FDEs; standard FDE posting is the right entry |
| **Palantir FDE (51 open)** | Palantir | Same band; highest volume | Lane inventor; structured interview = highest-volume rep |

**Your specific play (this week):**

| Day | Action | Target |
|---|---|---|
| Tue (today) | Update LinkedIn skills: add **"Apple Intelligence Extensions"**, **"AWS MCP Server"**, **"Anthropic Claude Partner Network"** — *exact* terms (keyword precision from [2026-05-20/01 §1](../2026-05-20/01-big-lab-moves.md#1-io-scorecard)) | LinkedIn |
| Tue night | Install AWS MCP Server ([`03` §1](./03-practical-skills-and-tools.md#1-aws-mcp-setup)) — the artifact that's attached to every apply this week | Local repo |
| Wed | Apply to **1 Anthropic** Solutions / FDE / Customer Engineering role with the AWS-MCP install demo attached | Anthropic careers |
| Wed | Apply to **1 OpenAI FDE** (NYC or SF) referencing yesterday's comp report as the seniority floor | OpenAI careers |
| Thu | Apply to **2 Big-4** AI-engineering practice roles (PwC + Deloitte preferred) | Big-4 careers |
| Thu | Apply to **1 Palantir FDE** — high-volume rep target | Palantir careers |
| Fri | Send **5 cold DMs** to engineers at 2–3 Anthropic-specialist boutiques (find via Partner Hub listing) | LinkedIn |
| Sat | Ship the **MCP install + Playwright loop writeup** as a LinkedIn post; tag Anthropic + relevant partner employees | LinkedIn |

**Why this week specifically.** The Anthropic S-1 (filed Jun 1) goes public **~15 days pre-roadshow** — so probably late August / early September. **Application volume to Anthropic will 5× when the public S-1 hits the wire.** Apply now, before the rigor ratchets up.

`#anthropic #partner-network #fde #applications`

---

## 2. The 96-hour stack — interview talking points fully bracketed <a id="2-96-hour-stack"></a>

Three external events in 96 hours, each one of which an interviewer this week is likely to ask about.

| Event | When | Interview question to expect |
|---|---|---|
| **Code w/ Claude Tokyo** | Wed Jun 10 | "What did Anthropic announce in Tokyo / what does it mean for the APAC enterprise market?" |
| **SpaceX IPO pricing** ("SPCX", ~$1.75T) | Thu Jun 11 (price) / Fri Jun 12 (trade) | "What does the SpaceX print tell you about the Anthropic + OpenAI IPO multiples?" |
| **Anthropic Agent SDK metering** | Sun Jun 15 | "How would you think about cost-aware multi-vendor routing? When would you choose Opus 4.8 vs Sonnet 4.6?" |

**Your one-liners (ready to deliver):**

- **Tokyo:** *"It's Anthropic's channel-side answer to OpenAI's Tomoro M&A — Partner Network in the West, customer + partner events in APAC. Watch for any post-WWDC Extensions surface-area mention."*
- **SPCX:** *"The precedent print. Public-market AI is no longer a thought experiment as of Friday; the multiple Anthropic gets graded against in late-Q3 anchors against whatever SPCX trades at after week one."*
- **Metering:** *"Opus 4.8 orchestrator + Sonnet 4.6 worker is the published Anthropic-internal pattern — ~40% cheaper than all-Opus per [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost); pair with cost-router middleware + IAM-scoped agent permissions via AWS MCP Server for production-grade ops."*

`#interview-prep #tokyo #spacex #metering`

---

## 3. Three distribution surfaces ratified in 30 days — pick one, ship one <a id="3-three-surfaces"></a>

The map.

| Surface | Who it serves | Skill to demonstrate | Demo to ship |
|---|---|---|---|
| **Apple Intelligence Extensions** (yesterday, [`01` §1](./01-big-lab-moves.md#1-wwdc-graded)) | iOS consumers + Mac users | Multi-model routing (Claude/Gemini/ChatGPT) inside Siri | An App-Intent agent that routes by intent — pre-stage tonight ([`03` §2](./03-practical-skills-and-tools.md#2-extensions-prestage)) |
| **AWS Bedrock multi-vendor** (Jun 1–2, see [2026-06-08](../2026-06-08/01-big-lab-moves.md)) | Enterprise AWS estates | Per-call routing across Bedrock-Anthropic + Bedrock-OpenAI + direct API | A 3-provider router (extends [2026-05-10](../2026-05-10/) project) with Bedrock as the unified abstraction |
| **AWS MCP Server** (today, [`02` §1](./02-new-emerging.md#1-aws-mcp-ga)) | Anyone with AWS + Claude Code / Cursor / Codex | Agent ops + IAM-scoped agent permissions | The AWS MCP install + Playwright visual-diff loop ([`03` §1](./03-practical-skills-and-tools.md#1-aws-mcp-setup)) |

**Pick exactly one** — you cannot ship all three this week. Recommended order, given your [ME.md focusing decision](../ME.md#current-focusing-decision-re-evaluate-monthly) (Anthropic-stack + Integration Engineer):

**AWS MCP Server > AWS Bedrock multi-vendor > Apple Extensions**

(AWS MCP first because the SDK is GA *today* and ships portfolio evidence by tomorrow; Apple Extensions requires waiting for the SDK access date, which gates the ship.)

**Why specificity beats coverage.** The 2025 lesson holds in 2026: "specific tool with exact name on resume + working demo" prints interviews; "I work with AI" does not. The May 20 keyword-precision incident ([2026-05-20/01 §1](../2026-05-20/01-big-lab-moves.md#1-io-scorecard)) is the canonical case study.

`#portfolio #skills #distribution`

---

## 4. Startup wedge map — update [STARTUPS.md](../STARTUPS.md) tonight <a id="4-startup-map"></a>

**Three new entries (add):**

1. **MCP-server-as-managed-service for non-AWS estates** — Snowflake / Databricks / MongoDB Atlas / Stripe / internal services. AWS just validated demand; the long-tail is the opportunity. **Boutique consulting → product hybrid** is the cheapest entry.
2. **Agent-RBAC / agent-audit consolidated dashboard** — sits on top of CloudWatch + Azure Monitor + GCP Logging; normalizes "what did the agent do" across clouds. Security-team-facing; long sales cycle but durable contracts. Pair with an existing SOC tool (Splunk / Datadog / Wiz channel).
3. **Apple-Extensions-aware vertical apps** — short window (~6 months) before saturation. Pick a sharp vertical (focus / calendar / notes / fitness / accessibility) and ship a thin App-Intent agent. Gate decision on revenue-share % disclosure (~10 days out).

**Two wedges to mark as crowded / saturated:**

1. **CX-agent / customer-service-agent** — Hark $700M Series A at $6B + Cognition $26B + Sierra $15B confirms winner-take-most. **Do not enter as new founder without structural unfair advantage.** Lateral: **CX-agent eval / observability / safety middleware** (Judgment Labs is the closest comp at $32M).
2. **General-purpose multi-vendor router** — too many entrants; commoditized; now a *feature* of Bedrock + Vertex + Anthropic Console, not a standalone product.

`#startups #wedges #portfolio`

---

## Cross-links

- §1 pairs with [`02` §2](./02-new-emerging.md#2-partner-network) (Partner Network announcement) and [2026-06-08/05 §1](../2026-06-08/05-career-and-startup.md#1-fde-comp) (FDE comp report).
- §2 pairs with all three of [`01` §2](./01-big-lab-moves.md#2-tokyo-and-ipo) (Tokyo + SpaceX + Metering).
- §3 pairs with [`01` §1](./01-big-lab-moves.md#1-wwdc-graded), [`02` §1](./02-new-emerging.md#1-aws-mcp-ga), and [2026-06-08/01](../2026-06-08/01-big-lab-moves.md).
- §4 update goes into [STARTUPS.md](../STARTUPS.md) tonight.
