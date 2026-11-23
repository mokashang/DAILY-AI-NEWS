# Practical Skills & Tools — 2026-09-17

Three practical shifts to fold into your workflow this week: (1) the **one-Claude prompt-as-router** pattern that ships tonight because the UI already routes for you; (2) **EFS setup + a security-questionnaire template** you can hand any regulated buyer this weekend; (3) a **recap of Fable 5.1 cache-hit economics** because your dashboard should have absorbed the price cut by now, and if it hasn't, that's your Sunday hour.

Tags: `#claude #cowork #docs #slides #skills #prompt-engineering #efs #compliance #pricing #caching`

---

## 1. The "one Claude" workflow — prompt-as-router {#1-one-claude-workflow}

**Context:** Anthropic collapsed Cowork + chat + Design into a single interface and shipped **Docs + Slides in beta** (see [`01` §1](./01-big-lab-moves.md#1-one-claude)). The user no longer picks the tool; **Claude picks it from the prompt.** That changes the shape of the prompt.

**The new rule:** State the **deliverable** in the first sentence of the prompt. Then attach context. Then constrain the output. Claude routes to Docs / Slides / Design / chat based on the deliverable name.

**Concrete template:**
```
Deliverable: {one of: memo | investor slides | hero image | quick Q | spreadsheet | dashboard}
Context: {attach the source materials — one link per line}
Constraints: {length, style, brand-colors, tone, do-not-include list}
Output: {finished .pdf | finished .pptx | finished .png | inline answer | finished .xlsx}
```

**Five workflows worth committing as Skills** *(pick your top 3 this weekend):*
1. **Weekly investor update.** Input: last-week's metrics + goals. Output: Slides deck exported to .pptx with your fund's branding.
2. **Deal memo.** Input: pitch deck link + founder LinkedIn + market notes. Output: 1-page Docs export to .pdf with your firm's memo template.
3. **Board pre-read.** Input: prior-quarter deck + this-quarter metrics + open questions. Output: Docs with an executive summary + open-questions section.
4. **Feature-launch one-pager.** Input: PR draft + eng-lead's design doc. Output: Docs with a copy block, hero image via Design, and comparison table.
5. **Interview prep for one lab.** Input: JD + your resume + last-30-days news. Output: Docs with 20 likely questions, 5 mock answers, 3 clarifying questions to ask them.

**Sources:**
- [TechCrunch — Anthropic merges Claude chat and Cowork in one interface](https://techcrunch.com/2026/09/16/anthropic-merges-claude-chat-and-cowork-in-one-interface/) `[secondary]`
- [SiliconANGLE — Anthropic brings Cowork directly inside Claude's chat interface](https://siliconangle.com/2026/09/16/anthropic-brings-cowork-directly-inside-claudes-chat-interface/) `[secondary]`
- [Firecrawl — 14 Best Claude Code Skills for Developers in 2026](https://www.firecrawl.dev/blog/best-claude-code-skills) `[analysis]`
- [Totalum — Claude Code Skills in 2026: The Complete Guide (vs Hooks, vs Subagents, vs MCP)](https://www.totalum.app/blog/claude-code-skills-totalum) `[analysis]`
- [SmartScope — Claude Code Advanced Best Practices: 11 Practical Techniques](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[analysis]`

### Why it matters to you

- **Job lens:** Shipping **3 Skills as a public template pack** by Sunday is a portfolio artifact that predates 99% of applicants for productivity-adjacent AI roles. Post it as **"one-Claude workflow templates I use"** on GitHub + LinkedIn. Watch for it to be linked into interview prep threads within 3 weeks.
- **Startup lens:** **Every recurring corporate workflow** (weekly update, board pre-read, quarterly review, monthly compliance report) is now a **buy-not-build** Skill purchase. Founder wedge: **"Claude Skill Marketplace for Corporate Workflows"** — 200 curated Skills across HR / Finance / Legal / Sales / Product, priced $50 one-time or $10/month/team. The **first 100 workflows** shipped inside 30 days = the moat. Content is the product; the technical build is trivial.
- **Insight:** The **prompt is the interface** was the 2022–2025 thesis. The **deliverable is the interface** is the 2026 thesis. Your prompts should now read like **spec documents**, not conversations.

→ Cross-link: [`01` §1 one Claude](./01-big-lab-moves.md#1-one-claude) · [2026-09-10/03 §2 Claude Code decision tree](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree).

---

## 2. Enterprise Frontier Safeguards (EFS) — 5-min setup that unlocks regulated deals {#2-efs-setup}

**Context:** Anthropic replaced ZDR with **EFS** (see [`01` §4](./01-big-lab-moves.md#4-efs)). Storage moves to **your S3 / Azure Blob / GCS**; misuse monitoring stays but **no human review by Anthropic employees**; **free**; phased rollout later this fall.

**The 5-minute setup:** (this is what to write into a security-questionnaire response *tonight*)

1. **Pre-work.** Have an S3/GCS/Azure bucket ready with **customer-managed keys (KMS or equivalent) + strict IAM policies**. Log everything, retain per your compliance clock (7yr for financial, 6yr for HIPAA-adjacent, etc.).
2. **Sign up for the EFS wave.** Contact your Anthropic Solutions/Enterprise rep. Ask for the **EFS onboarding form** — Anthropic is developing the tooling with 100+ customers first.
3. **Set your storage target.** Point EFS at your bucket + key ARN + role assumption. Anthropic never touches the encryption keys.
4. **Configure the misuse-monitoring policy.** Automated scans only — decide category thresholds (cyber, bio, self-harm, election, etc.).
5. **Answer the security questionnaire.** Copy-paste template:

```
Data Retention & Privacy
Our AI usage runs on Anthropic Claude with Enterprise Frontier Safeguards (EFS)
enabled. Under this configuration, no conversation data or completion outputs are
retained by Anthropic. All data is stored in our own cloud infrastructure
({S3 | Azure Blob | GCS}) under encryption keys and IAM policies that we control.
Anthropic performs automated safety monitoring for misuse detection; there is no
human review of our data by Anthropic personnel. Retention, deletion, and access
policies are governed by our internal information-security policy
{link to policy}.
```

**Caveat to write into the questionnaire honestly:** *"Anthropic retains the technical ability to read data in the misuse-detection pipeline; human review does not occur under our EFS configuration."*

**Sources:**
- [Anthropic — Enterprise Frontier Safeguards (official)](https://www.anthropic.com/news/enterprise-frontier-safeguards) `[primary]`
- [MindStudio — Anthropic's Zero Data Retention: What It Really Means for Your Data](https://www.mindstudio.ai/blog/anthropic-zero-data-retention-enterprise-safeguards) `[analysis]`
- [MarkTechPost — Anthropic Introduces Enterprise Frontier Safeguards (EFS)](https://www.marktechpost.com/2026/09/02/anthropic-enterprise-frontier-safeguards-efs/) `[secondary]`
- [The Register — Anthropic promises zero data retention – but customers must check it worked](https://www.theregister.com/ai-and-ml/2026/09/02/anthropic-promises-zero-data-retention-but-customers-must-check-it-worked/5293789) `[secondary]`

### Why it matters to you

- **Job lens:** Any FDE / Solutions / Enterprise / Applied-AI JD in a regulated vertical (finance, healthcare, gov, insurance, legal) now expects **fluency in EFS setup**. Include an **"EFS-ready reference app"** in your GitHub — a small Claude API app that reads/writes only through a customer-owned S3 bucket + KMS key. That artifact alone will filter you through 90% of top-of-funnel Solutions interviews.
- **Startup lens:** Two immediate wedges: (a) **EFS-shape compliance-questionnaire auto-fill** — every AI vendor except Anthropic will need to answer "do you support this?" within 90 days; automating the response is a $50–200K ARR-per-vendor wedge; (b) **EFS-audit tools** — the Register's angle ("customers must check it worked") is a wedge: independent verification that misuse-monitoring did what Anthropic said, without human review. Compliance-tech-for-AI is a category that will 10× in 2026–2027.
- **Insight:** **"BYO-cloud + provider-monitoring"** is the pattern the whole industry lands on within 12 months — it's the honest compromise between vendor-side safety and customer-side data control. Learn it once; apply it everywhere.

→ Cross-link: [`01` §4 EFS launch](./01-big-lab-moves.md#4-efs) · [2026-05-13/01 Claude for Legal + 20+ MCP connectors](../2026-05-13/01-big-lab-moves.md).

---

## 3. Fable 5.1 cache-hit economics — the recap you owe your dashboard {#3-fable-51-cache-recap}

**Context:** Since Sept 1, **Claude Fable 5.1 dropped prompt-cache-reads from $1.00 to $0.25 per 1M tokens** — a 75% cut on cache reads while base pricing ($10 input / $50 output per 1M) is unchanged. New rates: **cache writes at $12.50/MTok (5-min TTL) or $20/MTok (1-hour TTL); cache hits/refreshes at 0.025× base input price.** Anthropic estimates **~25% cost reduction on typical workloads, ~45% on heavy-agentic workloads.**

**If you set up prompt caching per [2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md), your bill dropped automatically.** If you haven't, this weekend's hour:

1. **Identify your longest reused prompt prefixes** — system prompts, long context docs, retrieval-shaped RAG chunks.
2. **Enable caching on those prefixes** with a 1-hour TTL if they're stable across a session or a 5-min TTL if they refresh per-turn.
3. **Instrument per-request cost** — log cache-hit vs cache-miss vs cache-write per call.
4. **Track weekly** — the 45% delta on heavy-agentic loads shows up fastest in an agent that makes 50+ tool calls per user request.

**A worked number:** an agent that reads a 100K-token system+context prompt 50 times per user request. Old cost per user request (Fable 5, no caching, all input): 50 × 100K × $10/MTok = **$50 per request**. With caching at old $1/MTok cache read: 100K × $10/MTok + 49 × 100K × $1/MTok = **$5.9 per request** (~88% cut). With Fable 5.1's new $0.25/MTok cache read: 100K × $10/MTok + 49 × 100K × $0.25/MTok = **$2.225 per request** (~62% further cut on top of caching). **At 1M requests/mo:** old-Fable-5-cached = $5.9M; new-Fable-5.1-cached = $2.225M. **Margin swing: $3.675M/mo.**

**Sources:**
- [Anthropic Pricing (platform docs)](https://platform.claude.com/docs/en/about-claude/pricing) `[primary]`
- [VentureBeat — Anthropic's Claude Fable 5.1 and Mythos 5.1 arrive with a 75% cost reduction for Fable cache reads](https://venturebeat.com/technology/anthropics-claude-fable-5-1-and-mythos-5-1-arrive-with-a-75-cost-reduction-for-fable-cache-reads) `[secondary]`
- [Codersera — Claude Fable 5.1: Benchmarks, Pricing & What Changed (2026)](https://codersera.com/blog/claude-fable-5-1-complete-guide-2026/) `[analysis]`
- [Merito — Claude Fable 5.1 Cache Pricing and Your Real AI Bill](https://www.merito.com/resources/blogs/what-the-claude-fable-51-cache-price-cut-actually-does-to-your-ai-bill) `[analysis]`
- [LLM Stats — Claude Fable 5.1 Benchmarks, Pricing & Context Window](https://llm-stats.com/models/claude-fable-5-1) `[aggregator]`

### Why it matters to you

- **Job lens:** **Cost-aware agent engineering** is the single highest-leverage skill in an FDE interview. Walk into an interview with a **cost trace of your own agent** (per-request, per-model, per-cache-hit) and you're differentiated from 90% of candidates who quote list prices without ever running the numbers.
- **Startup lens:** **Cost observability for agent apps** is still an under-founded category (Merito is early). If you can build a **1-file drop-in wrapper** that logs cache hit/miss + tokens by model per request, and export it as an OpenTelemetry span, that's a **DX wedge worth open-sourcing** to get inbound VC.
- **Insight:** **The base-price is now a lever labs stopped pulling.** Cache pricing, batch pricing, priority-tier pricing, and *fine-tuning-your-own-tier* pricing are where the labs compete now. Reprice your mental model: **"is X too expensive?" is always answered by "have you audited your caching strategy?"**

→ Cross-link: [2026-05-17/03 prompt caching setup](../2026-05-17/03-practical-skills-and-tools.md) · [2026-09-10/03 §1 Fable 5.1 economics](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics).

---

## 4. Micro-tips {#4-micro-tips}

- **`grep` your archive.** With today's tags, `grep -rn "#efs" .` and `grep -rn "#ads" .` and `grep -rn "#docs" .` all become useful queries. If a tag doesn't return 3+ hits by end of month, it wasn't a real thread.
- **The "one Claude" mental model for chatting quickly:** if you'd normally open a new tab, don't. Type the deliverable name inline: "quick answer" / "draft this into Docs" / "make me Slides for this."
- **When you attach files:** describe them once in the prompt ("Q3 metrics CSV attached — treat it as source-of-truth"). Anthropic's routing doesn't yet re-read the file every message; state its role early.
- **Compare quickly against your last month's bill.** If you have any single-prompt-prefix that consumes >10% of your usage, cache it today. This has been true since May and it's still true this week.

**Tags:** `#tips #workflow #grep #caching #one-claude`
