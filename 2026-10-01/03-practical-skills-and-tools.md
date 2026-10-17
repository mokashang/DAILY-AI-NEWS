# Practical Skills & Tools — 2026-10-01

Three artifacts today. **One is Anthropic's own PDF: "The Complete Guide to Building Skills for Claude."** The other two are things *you* ship by tonight: a reproducible open-weight red-team eval pack, and the 400-word Davila-ruling hiring post. All three ladder up to the same thesis — **frontier-safety / governance evaluation is the premium skill of Q4 2026.**

Tags: `#claude-code #skills #mcp #red-team #evals #artifacts`

---

## 1. "The Complete Guide to Building Skills for Claude" — Anthropic PDF, Q4 2026 edition {#1-skills-guide}

**What happened:** Anthropic published a resource-hub PDF titled **"The Complete Guide to Building Skills for Claude."** Pairs with the past 3 weeks of 2026-dated best-practice guides from the practitioner ecosystem (Firecrawl, alexop.dev, mcp.directory, Axify, Totalum, duet.so). **The four-primitive map is now consensus doctrine, with one additional surface added:**

| Primitive | What it's for |
|---|---|
| **Skills** | **How** to do something — procedural knowledge, auto-discovered by Claude per task |
| **MCP** | **Access** to external systems — one tool server at a time, prefer-lean |
| **Subagents** | **Delegation** of work to a specialist with its own context |
| **Hooks** | **Enforcement** — pre-tool / post-tool checks the harness runs, not Claude |
| **CLAUDE.md** | **Always-on** project conventions, commands, guardrails |

Rules of thumb that stuck:

- **If you ever wrote the same instructions to Claude twice**, that should have been a skill the first time.
- **SKILL.md body ≤1,500 words** — longer skills get truncated under context pressure.
- **Keep MCP stack lean** — "five well-chosen servers beat twenty."
- **Start with `/init` + CLAUDE.md** on every new project.
- **Run `/code-review` or `/security-review` before merging** any AI-written code.
- **New this quarter:** `.claude/skills/<name>/SKILL.md` with YAML frontmatter (name, description, optional argument-hint, optional tools allowlist) is now **the primary way to hold procedural knowledge**.

**Sources:**
- [Anthropic — The Complete Guide to Building Skills for Claude (PDF)](https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf) `[primary]`
- [alexop.dev — Claude Code Explained (2026): MCP, Skills, Subagents, Hooks & Plugins](https://alexop.dev/posts/understanding-claude-code-full-stack/) `[analysis]`
- [Axify — 39 Claude Code Best Practices: A Guide for Engineering Teams](https://axify.io/blog/claude-code-best-practices) `[analysis]`
- [mcp.directory — Claude Code Best Practices: From Vibe Coding to Agentic Engineering (2026)](https://mcp.directory/blog/claude-code-best-practices) `[analysis]`
- [Navigo — The Complete Claude Code Guide 2026](https://navigotechsolutions.com/blog/the-complete-claude-code-guide-2026-commands-skills-mcp-servers-github-projects/) `[analysis]`
- [Duet — Claude Code Skills Complete Guide: SKILL.md, MCP, Subagents & Teams (2026)](https://duet.so/guides/claude-code-skills-complete-guide) `[analysis]`
- [Totalum — Claude Code Skills in 2026: The Complete Guide](https://www.totalum.app/blog/claude-code-skills-totalum) `[analysis]`

### Why it matters to you

- **Job lens:** This is the **"will you hire me?" litmus test** for Anthropic Solutions / FDE / Integration roles in Q4 2026. If you can't talk through the four-primitive map and give an example of each in your own workflow, you fail round 1. **Do this tonight**: pick your 3 most-reused prompts, convert them to `.claude/skills/*/SKILL.md`, commit to a public repo with a README that explains your prompt-to-skill migration. That's 90 minutes of work and the single most portable artifact for Anthropic-stack interviews.
- **Startup lens:** The skills-marketplace surface is still open and under-built. Three concrete wedges: (a) **a skills registry with provenance + rating + usage telemetry** (opt-in); (b) **skill-to-MCP-shim generator** — many "I want this as a skill" items should actually be MCP tools, and the auto-promotion is a tooling gap; (c) **enterprise skill-governance** — approval workflows, versioning, rollback across a team's skills library. Each is a $3–10M-ARR wedge inside 18 months.
- **Insight:** The primitives map is now stable *for the first time since Claude Code shipped.* **Deprecation risk is low** for the next 2 quarters — meaning time invested in skills + MCP + subagents literacy *compounds* through Q1 2027. Compare to prompt-eng library time, which has deprecated twice already in 2026. The curriculum you build around skills is the *least likely* portion of your 2026 learning to be worthless by Q1 2027.

→ Cross-link: [2026-09-30 §7 primitive map](../2026-09-30/03-practical-skills-and-tools.md#2-primitive-map) · [`03` §2 red-team artifact](#2-red-team-artifact).

---

## 2. The reproducible open-weight red-team eval pack — ship this weekend {#2-red-team-artifact}

**What happened:** Anthropic's GLM-5.3 report ([`01` §2](./01-big-lab-moves.md#2-glm-5-3)) is **a published, lab-signed methodology** for cross-model cyber-exploit evaluation at a scale a solo CS grad can reproduce for 1–2 target open-weight models over a weekend. The methodology:

1. **Build or borrow a ~400-exploit battery** (Vulnhub rooms, CTF challenges, OSS vulnerability-fix pairs with the fix stripped out). Start with 20–40; grow to 100 by Nov.
2. **Score end-to-end exploit success rate** against a target open-weight model (e.g. Qwen3, Llama 4, GLM-5.2 if 5.3 is too hot to touch).
3. **Score safeguard bypass rate** with 5–10 standard prompt-level attacks ("I'm a researcher," "This is for a Capture-the-Flag," etc.).
4. **Publish a plot**: exploit-success vs safeguard-bypass per model, color-coded by openness tier.
5. **Blog it**: ~800 words, methodology + 2 example runs + the pretty plot + a "limitations + ethical boundary" paragraph.

Scope guardrails (do not skip):

- **No zero-day disclosure of real-world systems.** Use CTF rooms + patched vulnerabilities only. Treat vulnerability candidates as "do not touch the real production system under any circumstances."
- **Rate-limit yourself** — do not test against targets you don't own.
- **Credit Anthropic's methodology** explicitly in the blog.
- **Note that this is education-only replication**; link to the Anthropic paper + NIST CAISI as the authoritative source.

**Sources:**
- [Anthropic — GLM-5.3 and the spread of advanced cyber capabilities](https://www.anthropic.com/research/glm-5-3-and-the-spread-of-advanced-cyber-capabilities) `[primary]`
- [NIST — Center for AI Standards and Innovation (CAISI)](https://www.nist.gov/caisi) `[primary]`

### Why it matters to you

- **Job lens:** This is the single most-targeted artifact for the Anthropic Frontier Red Team / OpenAI Preparedness / GDM Responsible AI hiring lane. It's **small enough to finish in a weekend, novel enough to make a recruiter screen you in, and defensive enough that nobody will think you've crossed an ethical line.** Three specific job titles to target with this artifact in your portfolio: **Research Engineer — Capability Evaluations · AI Safety Engineer · Frontier Red Team Analyst.** Current open comp range per [`05` §1](./05-career-and-startup.md#1-comp-benchmarks): **$260–330K base + $400K–800K equity** at frontier labs.
- **Startup lens:** The artifact itself can be the seed of a founder story. **"We spent the weekend reproducing Anthropic's GLM-5.3 methodology against 3 open-weight models and found $X. Here's what we'd build if we did this at commercial scale."** That's a seed deck first slide. Add a 2–3 F500 CISOs on cold calls to confirm will-they-pay; raise $2–4M, hire 3–5 engineers, you're on track for a 2027 Series A in capability-aware procurement advisory.
- **Insight:** The dual-use boundary here is sharper than code-gen. **Publish your methodology, publish your scoring, publish aggregate numbers — do not publish exploits.** You can be transparent *about method* without being irresponsible *about artifact*. This is the ethics muscle every frontier-lab Trust & Safety team is hiring for in 2026.

→ Cross-link: [`01` §2 GLM-5.3](./01-big-lab-moves.md#2-glm-5-3) · [`05` §2 skill re-price](./05-career-and-startup.md#2-reprice).

---

## 3. The 400-word "Davila ruling → hiring effect" post — publish tonight {#3-ruling-post}

**What happened:** You've got a once-this-quarter chance to be the person who *wrote the sharp hiring-angle piece on the Apple v OpenAI ruling* within hours of the ruling landing. The ingredients are already in your tabs:

**Pre-ruling draft (write by 11 AM PT):**
- 100 words — what the hearing is + why it matters (hardware access + evidence-destruction + first federal frontier-lab ruling).
- 300 words — three hiring branches (grant / deny / narrowed), each with the specific role categories affected + likely-posting-timeframe. See [`01` §1](./01-big-lab-moves.md#1-davila-hearing) for the branch map.
- Leave *one* paragraph as a 50-word placeholder: `[ACTUAL RULING SUMMARY GOES HERE AFTER 10 AM PT UPDATE]`.

**Post-ruling edit (publish by 7 PM PT):**
- Fill in the placeholder with the ruling summary + the one branch that materialized.
- Add 1–2 lines pointing to roles at Anthropic / OpenAI / etc. that just became more likely.
- Publish on your blog or LinkedIn.
- 20 minutes of work after the ruling.

**Why 400 words:** short enough to read on a phone over coffee next morning, long enough to be substantive. **Why today:** the news cycle is 48 hours. Anything published Oct 3 or later is background noise.

**Where to publish:**
- Your own blog (preferred — compounds).
- LinkedIn (best for reach to frontier-lab recruiters).
- X (best for conversation + follower velocity).
- Hacker News Show-HN if you want engineer-dense feedback.

**Sources (same as [`01` §1](./01-big-lab-moves.md#1-davila-hearing)):**
- [CourtListener — Apple Inc. v. Liu, 5:26-cv-07078](https://www.courtlistener.com/docket/73602437/apple-inc-v-liu/) `[primary]`

### Why it matters to you

- **Job lens:** Recruiters at frontier labs *skim* LinkedIn for people writing substantively about frontier-lab-adjacent news. One well-timed 400-word post → **3–10 recruiter DMs over 10 days** on average, per the pattern we've seen on prior cover-letter plays (see [2026-09-30 §10 the S-1 post](../2026-09-30/03-practical-skills-and-tools.md#3-s1-post)). This has a stronger-than-usual signal because the hearing is a *public legal event* and the hiring-effect frame is still rare.
- **Startup lens:** This is also the fastest way to signal to a founder you'd want to join: *this candidate reads primary sources, writes under time pressure, and connects legal / financial / product news to hiring effects.* That is the exact composite skill of a founding operator at an early-stage AI company. Keep a running list of founders you'd want to work with — tag them when you publish.
- **Insight:** The deeper skill is **"turn a news event into a prediction, under time pressure, with a confidence calibration."** This is the muscle every analyst / FDE / Solutions role requires. Doing it in public, with your name attached, is the only way to build it.

→ Cross-link: [`01` §1 Davila hearing](./01-big-lab-moves.md#1-davila-hearing) · [`05` §1 hiring map](./05-career-and-startup.md#1-comp-benchmarks).
