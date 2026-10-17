# Practical Skills & Tools — 2026-07-27

Three ships this week that directly turn into portfolio artifacts before Friday. **(1) Kimi K3 open weights** — 30-minute smoke test on your existing Claude prompt library becomes an interview-ready A/B write-up. **(2) MCP 2026-07-28 migration day** (tomorrow) — the deadline the [07-25 edition](../2026-07-25/03-practical-skills-and-tools.md#2-mcp-migration) told you was coming. **(3) Mid-conversation tool changes** just went beta on Claude — a small refactor that cleans an old branch out of your agent loop. All three are the same shape: **read one changelog, ship one artifact, screenshot for interviews.**

Tags: `#playbook #kimi-k3 #mcp #stateless #migration #claude #tool-changes #portfolio #cost #interview-prep`

---

## 1. Kimi K3 30-minute smoke test — run it TONIGHT while the drop is fresh {#1-kimi-k3-run}

The weights hit HuggingFace at **00:00 UTC 2026-07-27** — a few hours ago. In 30 minutes you can produce a **dated, current, non-generic portfolio artifact** that answers the single most-asked interview question of the next two weeks: *"Have you compared the open-weights frontier to Claude / GPT?"*

**The smoke-test recipe (30 min, works with API access — self-hosting is a follow-on):**

1. **Pick 5 prompts you already run against Claude Opus 5.** Ideally: 1 SWE-bench-style code repair, 1 long-context (>100K tokens) research task, 1 tool-use / MCP call, 1 creative-writing task, 1 domain-specific reasoning task from your CS coursework or research.
2. **Get Kimi K3 API access** via [platform.moonshot.ai](https://www.kimi.com/blog/kimi-k3) (public API, $0.20 in / $2.00 out per MTok as of the release), OR route through **Together AI** (already stood up a hosted endpoint per their [blog](https://www.together.ai/blog/announcing-our-series-c)), OR through **HuggingFace Inference** if you want the vanilla-weights numbers.
3. **Run each prompt through 3 endpoints:** Claude Opus 5 (`effort=medium`), GPT-5.6 Sol (default), Kimi K3 (default). Log for each: **input tokens, output tokens, wall-clock, task-passing (your judgment; note where it's borderline), and one concrete failure mode.**
4. **Write a 1-page README** with a 5×3 grid, dated 2026-07-27, and one paragraph per model titled "where this model wins" and "where this model loses."
5. **Publish as a public gist or repo**, tag `#kimi-k3 #model-comparison #agent-eval`, and drop a screenshot into your resume portfolio section.

**Critical caveat to note in your write-up (this is the *smart* observation, not the vanilla one):** The **hosted Kimi K3 API and the open weights are not the same product.** Independent testers report ~51% hallucination on the vanilla weights vs. much better on the hosted API — meaning Moonshot ships **additional post-training + retrieval scaffolding** in their hosted endpoint. If you test against the API you're testing the closed product; test both if you want the full story. This is the single most defensible observation in the whole write-up.

**One-hour extension (do it Wednesday):** Add the **cost-per-passing-task metric** — total $ spent / count of tasks passed. This turns your smoke test into a *procurement* artifact, which is the FDE conversation with an enterprise buyer.

**Sources:**
- [Moonshot AI — Kimi K3 Tech Blog](https://www.kimi.com/blog/kimi-k3) `[primary]`
- [ExplainX — Run Kimi K3 Locally: July 27 Prep](https://explainx.ai/blog/kimi-k3-run-locally-open-weights-desktop-july-2026) `[analysis]`
- [Nathan Lambert — Kimi K3: The open-weights escalation (Interconnects)](https://www.interconnects.ai/p/kimi-k3-the-open-weights-escalation) `[analysis]`
- [Kimi-K2.org — Kimi K3 Open Weights July 27: What You Can Use Today](https://kimi-k2.org/blog/31-kimi-k3-open-weights-july-27) `[secondary]`

### Why it matters to you

- **Job lens:** *"Ran a 5-prompt comparison across Opus 5, GPT-5.6 Sol, and Kimi K3 on release day, here's the cost/quality table"* is the resume line that gets you past a screener. **It's specific, current, and reproducible** — three things a generic "familiar with LLMs" bullet is not. This is a stronger artifact than the Opus 5 effort-toggle write-up the 07-25 edition suggested; ship both, but ship this one first.
- **Startup lens:** Every Claude-for-X founder in your peer group is running the same test in the next 48 hours. **Publishing yours by Wednesday puts you in the top 5% by speed**; publishing a *rigorous* one (with the vanilla-vs-hosted caveat, and the cost-per-passing-task metric) puts you in the top 1%. Founder-network-visibility matters and this is a low-cost, high-signal move.
- **Insight:** The **first day of an open-frontier release** is the highest-signal moment for benchmarking — before the community has papered over failure modes, before the hosted API changes, before Moonshot fine-tunes based on early feedback. Your July 27 numbers will be the *canonical* numbers for this checkpoint. Save the exact prompts + responses; they'll be a citable dataset for a follow-up post in October when the community has "learned" to prompt K3.

→ Cross-link: [`01` §1 the release itself](./01-big-lab-moves.md#1-kimi-k3) · [2026-07-25/03 §1 the parallel effort-toggle artifact](../2026-07-25/03-practical-skills-and-tools.md#1-opus-5-effort).

---

## 2. MCP 2026-07-28 migration: the PR that ships tomorrow (draft tonight) {#2-mcp-migration-day}

The [full 7-step server-author checklist](../2026-07-25/03-practical-skills-and-tools.md#2-mcp-migration) is in Saturday's edition. Today's job is narrower: **make the PR** so it merges Tuesday when the spec finalizes.

**Tonight's 60-minute session (assumes you did the reading Saturday):**

1. **`git checkout -b mcp-2026-07-28-migration`** on your public MCP server repo.
2. **Rip out session state.**
   - Delete `Mcp-Session-Id` header code.
   - Delete any in-memory / DB session store.
   - Convert every "look up session, then process" handler to **stateless: process request, read `request._meta` for client metadata.**
3. **Add OAuth 2.1 for connection.**
   - Configure Google (or GitHub) as identity provider.
   - Serve `.well-known/oauth-authorization-server` if you're the auth provider; otherwise register with an existing one.
4. **Publish your Server Card at `/.well-known/mcp-server-card`.**
   - JSON manifest: name, description, tools, auth requirements, categories.
   - This is what clients read to discover you *before* connecting.
5. **Update response headers:** add `MCP-Protocol-Version: 2026-07-28`; accept `Mcp-Method` and `Mcp-Name` on incoming requests so an LB / API gateway can route per tool.
6. **Refactor interactive prompts** to return `InputRequiredResult { inputRequests, requestState }`. Client re-issues the original call with responses populated. (This replaces any SSE-based prompt-input flow.)
7. **Run the new [MCP conformance test suite](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) against your server** — it's published with the RC and will be the gate for the "MCP 2026-07-28 compatible" badge in the registry.
8. **PR title:** `feat: migrate to MCP 2026-07-28 stateless spec`. **PR description:** list the 7 changes above verbatim, link the spec RC, and note "will merge on 2026-07-28 spec finalization."

**Concrete follow-up (Tuesday):** merge the PR when [blog.modelcontextprotocol.io](https://blog.modelcontextprotocol.io/) posts the spec-finalization post. Screenshot the merge diff — it belongs in your portfolio README as "MCP 2026-07-28 shipped-day-one server author."

**Sources:**
- [Model Context Protocol Blog — The 2026-07-28 MCP Specification Release Candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) `[primary]`
- [Model Context Protocol Blog (index)](https://blog.modelcontextprotocol.io/) `[primary]`
- [Microsoft Community Hub — MCP Just Went Stateless — What the 2026 Spec Changes About Scaling on App Service](https://techcommunity.microsoft.com/blog/appsonazureblog/mcp-just-went-stateless-%E2%80%94-what-the-2026-spec-changes-about-scaling-on-app-servic/4530222) `[secondary]`
- [The Register — Model Context Protocol prepares to break with its stateful past](https://www.theregister.com/devops/2026/07/23/model-context-protocol-prepares-to-break-with-its-stateful-past/5276722) `[secondary]`
- [Digital Applied — MCP Goes Stateless July 28: What Breaks, What Gets Cheaper](https://www.digitalapplied.com/blog/mcp-2026-07-28-spec-stateless-migration-guide) `[analysis]`
- [WorkOS — The biggest MCP spec update ships July 28: What changes for AI agent authentication](https://workos.com/blog/mcp-2026-spec-agent-authentication) `[analysis]`
- [Stacktree — MCP 2026-07-28 spec: what changed, what breaks](https://stacktr.ee/blog/mcp-2026-spec-changes) `[analysis]`
- [Developers Digest — The MCP 2026-07-28 Rewrite: What Breaks and How to Migrate](https://www.developersdigest.tech/blog/mcp-2026-07-28-breaking-changes) `[analysis]`

### Why it matters to you

- **Job lens:** "MCP 2026-07-28 spec-day-one server author, PR merged on the day of finalization" is a **date-stamped**, **verifiable**, **rare** artifact. Very few candidates you'll interview against will have this in their portfolio by end of week; **first-mover on a public protocol is a resume gift** — take it.
- **Startup lens:** If your product exposes an MCP server (for Anthropic Cowork discovery, Claude Desktop, Claude Code), **being late to migrate is a distribution risk**, not just a code-hygiene one. The Anthropic MCP registry will surface `2026-07-28`-compatible servers preferentially in Cowork and Claude Desktop discovery flows. Being late = losing top-of-funnel.
- **Insight:** **The Tuesday finalization is the last time the migration is "in the news."** By August, migrated servers are baseline; by September, un-migrated servers are the exception. Do it tonight while it's a *story* you can talk about, not a *task* you're behind on.

→ Cross-link: [2026-07-25/03 §2 the full 7-step checklist and rationale](../2026-07-25/03-practical-skills-and-tools.md#2-mcp-migration) · [`02` §4 mid-conversation tool changes cleanup that pairs with this](./02-new-emerging.md#4-tool-change-beta).

---

## 3. Mid-conversation tool changes: delete an if-branch from your agent loop {#3-tool-change-refactor}

**Anthropic moved mid-conversation tool changes to beta** on Fable 5, Mythos 5, Opus 4.8, Opus 5 ([`02` §4](./02-new-emerging.md#4-tool-change-beta)). This is a small refactor with an outsized clean-up effect on almost any agent loop written before July 2026.

**The old pattern (still in most tutorials):**
```python
# on tool-set change:
if tools_changed(new_tools, previous_tools):
    conversation = start_new_conversation(messages, new_tools)  # ← throws away conversation history
    previous_tools = new_tools
```

**The new pattern (as of July 2026 beta):**
```python
# on tool-set change:
if tools_changed(new_tools, previous_tools):
    conversation.update_tools(new_tools)  # ← keeps history, keeps cache
    previous_tools = new_tools
```

**What you get:**
- **Cache preserved.** Every prompt-cached prefix stays warm — massive cost win on long agent runs.
- **History preserved.** No "the agent forgot what it just did" bug.
- **~15–40 lines of orchestration glue deleted** in most codebases.

**Concrete this week (Tuesday, 30 min):** find the `start_new_conversation` / `reset_conversation` branch in your public MCP agent or Claude Code project; replace it with the `update_tools` call; note the LoC-deleted in the PR title. This is a **free README/CHANGELOG bullet** — "reduced orchestration glue by ~30 lines using 2026-07 mid-conversation tool-change beta."

**Sources:**
- [Anthropic — Claude News (July 2026 changelog)](https://www.anthropic.com/news) `[primary]`
- [Anthropic Platform Docs — Prompting Claude Opus 5](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/prompting-claude-opus-5) `[primary]`
- [Releasebot — Anthropic July 2026 changelog aggregation](https://releasebot.io/updates/anthropic) `[aggregator]`
- [Simon Willison — Claude Skills are awesome, maybe a bigger deal than MCP](https://simonw.substack.com/p/claude-skills-are-awesome-maybe-a) `[analysis]`

### Why it matters to you

- **Job lens:** "I read the changelog, deleted 30 lines of glue" is the exact posture of an Applied AI Engineer. It's not glamorous; it's the daily-work signal an interviewer weights heavily. Include the deletion in your PR history.
- **Startup lens:** Every quarter Anthropic API adds features that let you delete a slice of your orchestration layer. **Cadence: refactor once a quarter, not once a year.** Set a reminder for Oct 27 to re-scan the changelog.
- **Insight:** **The delta between a great Claude engineer and a mediocre one in 2026 is who reads the changelog on Friday.** New features move from beta → GA in ~60 days. The engineer who wired mid-conversation tool changes to their agent loop in the last week of July has a 60-day head-start on the one who reads about it when it GAs.

---

## 4. This weekend's artifact — the "AI safety at C+" one-pager (do it Friday night) {#4-this-weekends-artifact}

The [FLI Summer 2026 Safety Index](./01-big-lab-moves.md#4-fli-safety-index) is the interview conversation of the fall. The **one-page memo you'll want in your back pocket** is the deliverable to build this weekend.

**Structure (1 page, ~600 words, publish as a public gist):**

1. **What the index actually measured** — 37 indicators, 6 domains, 9 labs graded.
2. **The specific grades** — Anthropic C+, OpenAI C, Google DeepMind C, Meta D+, xAI F. **No lab earned A or B in any domain.**
3. **The military-use reversal** — Anthropic + OpenAI + DeepMind + Meta all rolled back prior restrictions between 2024 → 2026; all four are now actively pursuing defense contracts.
4. **Your take (this is the paragraph interviewers will screen for):**
   - What does C+ mean as a buyer? (Answer with the DigitalApplied buyer-readout framing.)
   - What does the military-use reversal say about the safety-vs-capability trade the labs have already made?
   - How would you, personally, work at a C+ lab in 2026? (This is where you demonstrate honest reasoning, not talking-points.)
5. **The one thing you'd change** — pick something specific: e.g., "third-party red-team access to pre-deployment weights, independently funded" or "public deprecation policy tied to safety-eval regressions." **Interviewers respect a specific ask more than a general concern.**

**Sources to cite in the memo:**
- [FLI — AI Safety Index Summer 2026](https://futureoflife.org/ai-safety-index-summer-2026/) `[primary]`
- [FLI — Full PDF](https://futureoflife.org/wp-content/uploads/2026/07/AI-Safety-Index-Summer-2026-Digital.pdf) `[primary]`
- [DigitalApplied — AI Safety Index 2026: A Buyer's Guide](https://www.digitalapplied.com/blog/fli-ai-safety-index-2026-enterprise-buyer-readout) `[analysis]`
- [Seoul Economic Daily — Global Big Tech Retreats on AI Safety Pledges](https://en.sedaily.com/technology/2026/07/08/global-big-tech-retreats-on-ai-safety-pledges-experts-warn) `[secondary]`

### Why it matters to you

- **Job lens:** This is the artifact that **converts the safety question from a landmine to a story you tell on offense**. Anthropic and OpenAI both interview for values fit; the FLI memo signals you engage the actual data, not the marketing.
- **Startup lens:** Enterprise procurement in Q4 2026 will start asking safety-vendor questions on RFPs; having a **house view** — even in your own head — that you can express to a security-conscious customer is a founder skill worth 15 minutes on Friday.
- **Insight:** The **best AI-safety take in 2026 is not "AI is dangerous" or "AI is fine" — it's "here's what the labs have already priced, and here's what I'd change."** Specific, current, informed. That's what "senior thinking" looks like at a lab or an AI-serious startup; ship the memo, keep the take.
