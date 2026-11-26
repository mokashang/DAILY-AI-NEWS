# Practical Skills & Tools — 2026-11-17

Act-on-this-today file. Four items this edition: **(1) audit `.claude/settings.local.json` on every repo you own tonight and rotate exposed creds**, **(2) lock in Gemini 4 Carbon workflows on the intro rate before Dec 1**, **(3) align your MCP server work to the new 6-month cadence (next spec window: Tue 2027-03-31)**, and **(4) a 15-minute RLI dashboard that gives you a buyer-side benchmark story in interviews**.

Tags: `#claude-code #security #gemini #mcp #benchmarks #rli`

---

## 1. Tonight: audit `.claude/settings.local.json` and rotate secrets (5 min + remediation time) {#1-audit-claude-settings}

**What happened:** Apiiro (security researchers Shmulik Cohen + Matan Giladi) published on **Nov 5–7, 2026** that **Claude Code's "Yes, and don't ask again"** approval option saves the full approved command — including any secrets typed into it — as a permission rule in **`.claude/settings.local.json`**. The researchers found **104,185 copies of the file on public GitHub**, of which **1,122 contained real secrets** (one count); a second audit including git history + shared settings + agent transcripts raised the tally to **2,539 exposed secrets**. Anthropic has acknowledged + is working on secret-scrubbing + recommending auto-mode.

**Why it's bad:** The file stores `allow` rules shaped like `Bash("curl -H 'Authorization: Bearer <key>' ...")` — so your bearer token / API key / database password is sitting as an exact string in a rule object.

### Do this tonight (5 min + rotation):

```bash
# 1. Scan every repo you own for the file
cd ~/code  # or wherever your repos live
find . -name 'settings.local.json' -path '*/.claude/*' -not -path '*/node_modules/*' 2>/dev/null

# 2. For each hit, inspect — look for anything that looks like a key, token, password, URL with creds
grep -E '(Bearer|api[_-]?key|password|secret|token|ghp_|sk-)' ~/code/**/.claude/settings.local.json 2>/dev/null

# 3. Check if ANY of these files landed on GitHub
for repo in ~/code/*/; do
  cd "$repo" && git log --all --oneline -- .claude/settings.local.json 2>/dev/null | head -5
done

# 4. If you find anything, assume it leaked. Rotate the creds NOW.
#    Deleting the file or rewriting git history does NOT revoke an exposed key.
#    Only the issuer's rotate endpoint revokes it.
```

**Then add to every repo:**
```gitignore
# .gitignore
.claude/settings.local.json
```

**Anthropic-side mitigation:** switch Claude Code into **auto-approved mode for *read-only* bash commands only**, and never for commands that pass secrets as inline flags. Use **environment variables** read via `$VAR` — Claude Code doesn't expand the variable into the stored rule, it stores the literal `$VAR`.

**Sources:**
- [CSOonline — Claude Code's "Don't Ask Again" button has a secrets-spilling problem](https://www.csoonline.com/article/4247336/claude-codes-dont-ask-again-button-has-a-secrets-spilling-problem.html) `[secondary]`
- [InfoWorld — Same story (Infoworld syndication)](https://www.infoworld.com/article/4247344/claude-codes-dont-ask-again-button-has-a-secrets-spilling-problem-2.html) `[secondary]`
- [Expert Insights — Claude Code "Don't Ask Again" approvals leak passwords and keys into public GitHub repos](https://expertinsights.com/?p=63836) `[secondary]`
- [Let's Data Science — Apiiro finds Claude Code approvals leak secrets](https://letsdatascience.com/news/apiiro-finds-claude-code-approvals-leak-secrets-into-public-99d400fd) `[aggregator]`
- [Yage.ai — Claude Code Don't Ask Again secret leak (incident writeup)](https://yage.ai/share/claude-code-dont-ask-again-secret-leak-en-20261111.html) `[analysis]`
- [buildmvpfast — How to check your repos](https://www.buildmvpfast.com/blog/claude-code-dont-ask-again-secrets-settings-local-json-2026) `[analysis]`
- [winzheng — Full writeup (2,539 secrets figure)](https://www.winzheng.com/en/lab/reports/claude-code-dont-ask-again-secrets-leaked-github) `[analysis]`

### Why it matters to you

- **Job lens:** This is **the first true supply-chain-grade incident for an AI dev tool**. Hiring-manager read: an eng who proactively audited + fixed this within 24 hours has a story to tell at every interview this week. **Do not bury your rotation + fix in a private commit.** Write it up on LinkedIn or a personal blog with the `settings.local.json` checklist above — this is a résumé artifact that writes itself.
- **Startup lens:** If you're building dev-tool / DevSecOps / supply-chain-security SaaS, **there's a 30-day window** to ship a scanner for AI-dev-tool permission files (`.claude/settings.local.json`, OpenAI Codex equivalent when it ships, Cursor's config). First mover gets GitHub Secret Scanning integration. Known cheap moat: **integrate with Dependabot, publish the first SARIF rules, be in the GHSA pipeline before the Big 4 catch up.**
- **Insight:** **Permission files are the new `.env`** — one more place you memorize to check. Add this to your personal **repo-hygiene preflight checklist** alongside `.env`, `*.pem`, `.aws/`, `.config/gcloud/`, `.ssh/id_*`. Every new AI dev tool will replicate some version of this mistake until the pattern becomes industry-standard.

---

## 2. Lock in Gemini 4 Carbon on the intro rate before Dec 1 (30 min this week) {#2-gemini-4-carbon-lockin}

**What's happening:** Google opened **Gemini 4 Carbon** to all paying API devs on **Nov 10**; **intro pricing $2/M input · $10/M output ends Nov 30 2026**; **Dec 1 rate is $4/$20 — a straight doubling**.

### Do this before Nov 30 (30 min):

```python
# 1. In llm (Simon Willison's CLI) — already supports gemini-4-carbon via llm-gemini 0.36
llm install llm-gemini -U
export GEMINI_API_KEY=...
llm -m gemini-4-carbon "test prompt"

# 2. For any long-context / batch workload you'd planned for Dec / Jan,
#    process it NOW on the intro rate with Google's batch API:
#    (half the sync price; stacks with the intro rate until Nov 30)
from google import genai
client = genai.Client()
batch = client.batches.create(
    model="gemini-4-carbon",
    requests=[...],
)

# 3. If you run a context-heavy agent, warm the cache ONCE before Nov 30 at the intro rate:
#    Google's context-caching discount runs against the cached-price rate, not the hot rate.
#    So a cache built Nov 29 saves you money every call through its TTL.
```

### Portfolio artifact (90-min weekend project):

Build a **"Dec 1 Gemini 4 Carbon Price Rebase: before/after" dashboard** on your personal site.

- **Input**: your actual API spend (anonymized) + a 10% sample of prompts replayed on the intro rate vs. Dec 1 rate.
- **Output**: a before/after cost chart + a "what I changed in the pipeline to absorb the 2× hike" writeup (cache, batch, prompt-compression, tool-use for retrieval).
- **Posting cadence**: Nov 20, Dec 2 (same dashboard, updated).
- **Résumé line**: *"Cut gross-margin impact of the Nov 30 Gemini 4 Carbon price-doubling from 2.0× to 1.2× through cache + batch + retrieval architecture."*

**Sources:**
- [eWEEK — Google opens Gemini 4 Carbon to businesses, but API prices double Dec 1](https://www.eweek.com/news/google-gemini-4-carbon-api-pricing/) `[secondary]`
- [braindetox.kr — Gemini 4 Carbon $2/$10 intro, $4/$20 Dec 1](https://braindetox.kr/en/posts/gemini_4_carbon_general_availability.html) `[aggregator]`
- [Let's Data Science — llm-gemini 0.36 adds access to Gemini 4 Carbon](https://letsdatascience.com/news/llm-gemini-036-adds-access-to-gemini-4-carbon-e652c564) `[aggregator]`
- [rohitai — Gemini 4 Carbon access + API pricing](https://rohitai.com/blog/gemini-4-carbon-access-api-pricing) `[analysis]`

### Why it matters to you

- **Job lens:** **"Model pricing operator"** is a specialty that hires, especially inside FDE / solutions / applied AI roles. This project gives you a tight, verifiable story to drop into interviews and screens. It also teaches the skill that **matters for Day-1 real-world Claude / Gemini / GPT work**.
- **Startup lens:** **The intro-rate → Dec 1 doubling is a template** — every vendor does this. If your gross margin is sensitive to a single model's price, you're exposed. The weekend project forces you to practice the hedge: **cache, batch, retrieval, multi-vendor fallbacks**.
- **Insight:** **Intro pricing is the vendor's price-discrimination tool, not a gift.** Google is harvesting elasticity data from devs building on the intro rate. Treat the rate as a 3-week A/B window, not a permanent price.

---

## 3. Align MCP server work to the 6-month cadence (next spec window: Tue 2027-03-31) {#3-mcp-cadence}

**What happened (2026-11-11):** The Model Context Protocol project announced — in a Nov 11, 2026 blog post — that spec releases move to **a fixed 6-month cadence, the last Tuesdays of March and September**. The **Dec 15 date shown on some release trackers is stale** (pre-cadence-change).

**Latest stable spec: 2026-07-28** — the "stateless core" update:
- **Removes the `initialize` handshake + `Mcp-Session-Id` header** — remote MCP servers get materially easier to scale behind standard load balancers.
- **MCP Apps** as a first-class extension — ships on its own cadence independent of core.
- **Formal deprecation policy** + hardened authentication.

### Do this if you're shipping an MCP server:

1. **Build to 2026-07-28 stateless** — any tutorial or sample older than July is obsolete.
2. **Target your portfolio MCP server for `2027-03-31` spec window**, not Dec. You have 4.5 months — plenty of time to ship something polished.
3. **Use FastMCP** (Python) or the official SDKs; they're already stateless-aware.
4. **Publish via the MCP Apps extension** — it's the discoverability moat.

### Minimum-viable MCP portfolio spec:

- 3 tools (e.g., `search_arxiv`, `summarize_paper`, `tag_for_startup_wedge`)
- 5-case eval suite (each an expected tool-call trajectory)
- README with a 60-second GIF + 2 "why this is cheap-to-run" callouts (stateless, OAuth via MCP Apps)
- CI: lint + eval on push
- One real integration write-up ("how I used this in my own workflow")

**Sources:**
- [Model Context Protocol blog — MCP 2026-07-28 release post](https://blog.modelcontextprotocol.io/posts/2026-07-28/) `[primary]`
- [Model Context Protocol roadmap blog](https://blog.modelcontextprotocol.io/posts/) `[primary]`
- [Composio — MCP 2026-07-28 update: statelessness, MCP Apps, better auth](https://composio.dev/blog/mcp-2026-07-28-update-statelessness-apps-auth) `[analysis]`
- [CData — The 2026-07-28 MCP release explained for enterprise teams](https://www.cdata.com/blog/mcp-2026-07-28-release) `[analysis]`
- [SDTimes — Several new updates make their way into the MCP specification](https://sdtimes.com/ai/several-new-updates-make-their-way-into-the-mcp-specification/) `[secondary]`
- [Agentic AI Foundation — MCP graduates to enterprise infrastructure](https://aaif.io/blog/mcp-graduates-to-enterprise-infrastructure-stateless-architecture-formal-governance-and-security) `[analysis]`
- [Claude blog — Bringing MCP 2026-07-28 to Claude](https://claude.com/de/blog/bringing-mcp-2026-07-28-to-claude) `[primary]`
- [oakgen.ai — MCP six-month release cycle, what to plan](https://oakgen.ai/blog/mcp-six-month-release-cycle-what-to-plan) `[analysis]`

### Why it matters to you

- **Job lens:** **An MCP server is still the #1 highest-ROI portfolio artifact for FDE / AI Integration Engineer / Solutions roles.** The 6-month cadence means your spec choice ages predictably — build on 2026-07-28, plan to migrate at 2027-03-31. **A MCP server + eval harness + 60-second demo GIF on your GitHub profile is currently worth 1–2 interview slots at every frontier lab.**
- **Startup lens:** **MCP Apps is the new App Store moment.** First-mover packaging of vertical MCP apps (legal, finance, manufacturing, healthcare) is still open. Competitive moat: **authentication + marketplace listing + a referral pipeline from the labs**, not the server code itself.
- **Insight:** **Cadence discipline matters more than keeping up with every pre-release.** Build on stable → migrate at the window → stop. Chasing pre-releases is a tax; the cadence announcement is a gift because it removes that tax.

---

## 4. 15-minute RLI dashboard for your job-search dashboard {#4-rli-dashboard}

**What happened:** Fable 5.2 hit 41.3% on the Scale AI × CAIS Remote Labor Index (see `02` §1). **Buyers now cite RLI scores first** when evaluating vendors — not MMLU, not HumanEval.

### Do this (15 min):

1. Bookmark the RLI leaderboard page.
2. Add a weekly cron to your "job-search dashboard" (Notion / Obsidian / GitHub Pages) that pulls:
   - Current top RLI score + model.
   - Delta vs. 30 days ago.
   - Which companies' tech-blog posts cite RLI this week.
3. In **every cover letter / outreach note** this week, lead with a one-line RLI reference: *"With Fable 5.2 at 41.3% on the Remote Labor Index, the question for a vertical AI product manager is no longer 'can the model do it' but 'where in the task does the model break, and what routes to a human.'"*

### Why RLI specifically (and not Artificial Analysis / LM Arena):

- **RLI is dollar-denominated.** Every task has a real freelance budget. Enterprise buyers understand "41.3% of jobs" instantly; they skip over Elo scores.
- **RLI ≠ production.** Client comms, negotiation, scope-change management are outside the benchmark. **This is where your job lives.** Lead with that framing in interviews.

**Sources:**
- Same as [`02` §1](./02-new-emerging.md#1-rli-41).

### Why it matters to you

- **Job lens:** Lead-with-RLI is a **buyer-fluency signal** interviewers pick up on in the first 30 seconds. It's the single highest-leverage piece of vocabulary to update this week.
- **Startup lens:** **Design your pitch around "what's the RLI gap we close"** rather than "what tasks does our model automate." Investors are starting to use the framing.
- **Insight:** **Benchmarks are social objects** — the one that enterprise buyers adopt wins, regardless of technical rigor. RLI won the fall. **Track the next benchmark that takes share** (likely a RLI-successor with multi-agent + client-comm scope by mid-2027).
