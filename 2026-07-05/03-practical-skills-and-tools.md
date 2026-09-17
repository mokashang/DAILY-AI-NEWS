# 03 — Practical Skills & Tools — 2026-07-05

Sunday means **finish the weekend deliverables**, not start new ones. Two things must be published today: the MCP-stateless migration writeup and (if not already sent) the Claude Science lab-partner outreach email. Everything else is bonus. This file is short by design.

---

## 1. Sunday MCP-stateless migration — publish the "before/after" writeup {#1-mcp-sunday}

**Backstory:** Saturday's edition ([2026-07-04/03 §1](../2026-07-04/03-practical-skills-and-tools.md#1-mcp-migration)) named this as the primary weekend artifact. If it's on your machine but not on GitHub, land it today.

**The minimum shippable version:**
1. **Two branches, same MCP server**: `pre-2026-07-28` (current) and `post-2026-07-28-rc` (migrated).
2. **Migration deltas the writeup must call out:**
   - Session store removed (drop the `Mcp-Session-Id` state store; route on `Mcp-Method` header).
   - `_meta` used for client info + capabilities on every request.
   - One tool wired to the **Tasks extension** (server returns a task handle, client polls via `tasks/get`).
   - One tool wired to the **Apps extension** (a small sandboxed HTML response for a data view).
   - OAuth 2.1 / OIDC path validated (SEP `iss` per RFC 9207, `application_type` on registration).
3. **90-second Loom** — run both branches side-by-side, show the migration diff, run `tasks/get` polling once.
4. **README** with a 1-paragraph "why the stateless flip matters" (route-anywhere behind a plain load balancer, cachable `tools/list` via `ttlMs`), the 5 breaking-change bullets, and the migration commit link.

**Sources.**
- **[primary]** [MCP — 2026-07-28 Release Candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/)
- **[primary]** [MCP — 2026 Roadmap](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/)
- **[primary]** [MCP — Development Roadmap](https://modelcontextprotocol.io/development/roadmap)
- **[analysis]** [Stacktree — MCP 2026-07-28 spec: what changed, what breaks](https://stacktr.ee/blog/mcp-2026-spec-changes)

**Why it matters to you.**
- **Job.** Attach the repo + Loom to Monday's FDE apply queue ([`05` §4](./05-career-and-startup.md#4-apply-queue)). "I shipped the migration when the protocol broke" is the *exact* FDE-hire signal for July — this is not a "nice to have" artifact.
- **Startup.** The migration writeup doubles as a **customer-education asset** for any developer-tooling wedge you'd pitch. Enterprises with existing MCP deployments will be looking for a "how do I migrate" playbook by Aug 1; ship yours first and become the search-result reference.
- **Insight.** Protocol churn = stack-relevance signal. Whoever demonstrates they can migrate cleanly *and quickly* becomes the go-to for the next protocol change. This is a career-arcing habit, not a one-off artifact.

`#mcp #migration #agents #portfolio #sunday`

---

## 2. Simon Willison's `$149.25 for sqlite-utils 4.0rc2` — a real cost datapoint (July 5) {#2-sqlite-cost-datapoint}

**What was published today.** [Simon Willison](https://simonwillison.net/) shipped **`sqlite-utils 4.0rc2`** — a release candidate of a widely-used Python library — noting it was **mostly written by Claude Fable** at a total token cost of **~$149.25**.

**Why it's an important calibration point.**
- `sqlite-utils` is not a toy: it's a real library used by tens of thousands of developers, with a decade-long release history.
- $149.25 is the **cost of an RC** — not a from-scratch build, but a substantive iteration.
- The published cost is **per-artifact**, not per-hour or per-month: it's the number an interviewer can compare directly against their own team's per-artifact budgets.

**Sources.**
- **[primary]** [Simon Willison's Weblog — sqlite-utils 4.0rc2 (July 5 2026)](https://simonwillison.net/)
- **[primary]** [GitHub — simonw/sqlite-utils](https://github.com/simonw/sqlite-utils)

**Why it matters to you.**
- **Job.** Cite this in Monday's interviews as **your reference calibration point for AI-assisted library maintenance cost**. "Simon Willison shipped a real Python library RC for $150 in Claude Fable tokens; my per-artifact cost on comparable-scale personal work is $X" is a much stronger cost story than a vague adjective.
- **Startup.** Solo-founder / small-team economics just got a public benchmark. If you're pitching a "one-person library shop" model — indie developer earning off maintenance + support of 5–10 libraries — the arithmetic is now: **~$100–$200/artifact in AI, plus a solo human's judgment time.** That reshapes what a solo AI-assisted developer can defensibly own.
- **Insight.** Notice Simon used **Fable** — a controlled-access, safety-classified model that only came back online days earlier — because it was the right tool for the job at that moment, not because he ideologically pinned it. **The correct posture is vendor-neutrality with model choice per task.** Your cost-router should default to the same posture.

`#practical #cost #simon-willison #fable #datapoint`

---

## 3. Monday Geneva monitoring — 8-min-block cadence {#3-geneva-monitoring}

**Set up tonight so Monday morning works.**

- **Bookmark**: [UN Global Dialogue on AI Governance](https://www.un.org/global-dialogue-ai-governance/en), [UN Indico overview](https://indico.un.org/event/1023375/overview), [ITU AI for Good Global Summit 2026](https://aiforgood.itu.int/).
- **Set 8-minute monitoring blocks** for Monday: (a) 08:00 PT (17:00 CEST — opening plenary), (b) 12:00 PT (21:00 CEST — Day 1 wrap), (c) Tue same schedule.
- **X list**: add UN AI Advisory Body members, ITU Sec-Gen, WSIS delegates, Anthropic policy accounts, OpenAI policy accounts. **You want the delegate-tweets, not the plenary transcripts** — that's the signal.
- **Publishing rhythm**: draft a **"Geneva Day-1 debrief"** by Mon 21:00 PT for personal notes; publishable version by Tue AM.

**Why it matters to you.**
- **Job.** A short Geneva writeup posted Monday night is the fastest way to demonstrate governance-lane fluency for Tuesday's AI Policy / T&S applications.
- **Insight.** UN dialogues produce **vocabulary, not law**. The vocabulary is the thing to capture — every AI Policy JD in H2 will use these terms.

`#geneva #monitoring #policy`

---

## 4. Spend-audit follow-up (from Saturday's 4th-of-month audit) {#4-spend-followup}

**Yesterday's audit** ([2026-07-04/03 §3](../2026-07-04/03-practical-skills-and-tools.md#3-spend-audit)) surfaced the 80/20 for June. Today: convert that finding into **one concrete action for the coming week**.

**Framework:**
- If the 80% cost was concentrated in **1 workflow**: swap that workflow's default model to a cheaper tier (e.g., Sonnet 4.6 → Fable 5 for exploration, Sonnet 5 for finalization).
- If it was **cache-miss dominated**: extend `cache_control` window to 1h; refactor system prompt into fewer stable blocks. See [2026-07-02/03 §1](../2026-07-02/03-practical-skills-and-tools.md#1-prompt-cache).
- If it was **subagent-tier misuse** (all subagents on Opus/Sonnet): apply the [Simon Willison lower-power-model pattern](../2026-07-04/03-practical-skills-and-tools.md#2-longcat-routing) for coding subagents.
- **Log the target delta** (e.g., "cut projected July spend 30%") and set a July 20 checkpoint.

**Why it matters to you.**
- **Job.** The **before/after cost chart** is the exact artifact interviewers ask about for cost-conscious FDE / Applied AI roles.
- **Insight.** Monthly audits without a follow-up action are theatre. The action is the audit.

`#spend #cost #followup #sunday`
