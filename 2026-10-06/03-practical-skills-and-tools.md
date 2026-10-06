# 03 — Practical Skills & Tools — 2026-10-06

Today's useful work. Three artifacts to ship this week: (1) an MCP server for one of your workflows, (2) an updated router with Argon added, (3) a pre-staged S-1 reading template.

---

## 1. Ship an MCP server this week — the 2026 portfolio minimum {#1-mcp-server}

**Why now**
- MCP is **97M+ monthly downloads** and **Linux-Foundation-stewarded** (per [`02` §1](./02-new-emerging.md#1-mcp-linux-foundation)). It's the one agent-stack skill where the market has fully consolidated — no "will this win?" risk.
- Every **FDE / AI Integration Engineer / Solutions Engineer** job posting at Anthropic, OpenAI, Google, PwC, and the AI-native startups lists MCP (or MCP-adjacent) experience as a want.
- Zero portfolio minimum is 2024; one MCP server in 2026 is the new floor.

**What to ship**
A **public, documented, tested MCP server** with:
1. **3 tools** that do something non-trivial from your actual life (your Gmail inbox + Google Drive are already connected in this environment — think a researcher's clipping-notebook, or a daily-standup composer, or a competitor-intel scraper).
2. **5-case eval suite** (one happy path, two edge cases, two adversarial — prompt injection, missing auth).
3. **README** with: install, config, example `claude mcp add` command, screenshots of Claude Code using it.
4. **A 90-second demo GIF.**
5. **One real customer** (even a friend) who uses it weekly.

**Pattern (minimal)**
```python
# server.py
from mcp.server.fastmcp import FastMCP
mcp = FastMCP("research-notebook")

@mcp.tool()
async def save_quote(source_url: str, quote: str, tags: list[str] | None = None) -> dict:
    """Save a quote with its source into my research notebook."""
    # ... implementation that writes to a local SQLite + exports a markdown digest
    return {"id": "...", "digest_path": "..."}

@mcp.tool()
async def search_notebook(query: str, limit: int = 10) -> list[dict]:
    """Fuzzy-search saved quotes."""
    ...

@mcp.tool()
async def compose_weekly_digest(theme: str) -> str:
    """Generate a weekly markdown digest filtered by theme."""
    ...

if __name__ == "__main__":
    mcp.run()
```
Then register it:
```bash
claude mcp add research-notebook python /path/to/server.py
```

**Resume line that works in 2026**
> *Authored and open-sourced an MCP server (`research-notebook`, 3 tools, 5-case eval suite, 90-sec demo) used in production for personal research pipeline; integrated with Claude Code via `claude mcp add`.*

**Why it matters to you**
- **Job:** The MCP server is the **2026 equivalent of a well-named GitHub project**. Interviewers can see the code, run the demo, grep your eval suite. It beats any claim of "I know agents."
- **Startup:** Your MCP server is also a **product discovery vehicle** — the moment a friend asks "can I use this at my job?", you've found a wedge.
- **Insight:** The agentic stack rewards **people who ship small, composable, well-tested pieces**. The era of "I built the whole platform" solo-founder narrative is over; the era of "I built the five best pieces in this niche" is now.

→ Cross-link: [2026-05-15 `CLAUDE.md` Karpathy pattern](../2026-05-15/03-practical-skills-and-tools.md) · [2026-09-10 Claude Code decision tree](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree)

**Tags:** `#mcp #claude-code #portfolio #evals`

---

## 2. Update your router — add Gemini 4 Argon, re-benchmark cost per task {#2-router-updated}

**Why now**
- You (or at least this edition's assumed persona) shipped the **router + 5-case eval suite** last month per [`03` §3`` 2026-09-10](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact).
- **Gemini 4 Argon shipped Sept 30** (see [`01` §3](./01-big-lab-moves.md#3-gemini-4-argon)). Your router needs an Argon entry and a re-run of the 5-case suite.
- Pricing/perf data will not be settled until mid-month; the **artifact of value is the methodology**, which is model-agnostic.

**30-min update checklist**
1. **Add Argon route** — long-horizon coding + cybersecurity, cheap tier for enterprise summaries.
2. **Re-run 5 eval cases** (coding, long-context Q&A, cheap batch summary, agentic tool-use, prompt-injection-resistance) across:
   - `claude-fable-5.1` (Anthropic) · `gpt-6-astra` (OpenAI) · `gemini-4-argon` (Google) · `muse-spark-1.3` (Meta)
3. **Log per-request cost** (input + output + cache-read if applicable). Fable 5.1's **$0.25/1M cache-reads** often wins the batch-summary case; Argon may or may not beat on coding — the eval is what tells you.
4. **Publish the table.** Markdown table on GitHub README + one-paragraph interpretation.

**Resume / interview use**
> *Maintain a public router + eval suite covering four frontier models; re-benchmarked within 7 days of each new model release. Median per-task cost reduction vs single-model baseline: X% (depends on your workload).*

**Why it matters to you**
- **Job:** This artifact is **the single most-cited portfolio piece** in FDE interviews this quarter. The reason: when a prospect asks "which model should we use?", a candidate who can **answer with their own numbers from their own eval suite** is categorically different from one who quotes LLM Arena.
- **Startup:** The router becomes a **customer trust artifact** when you sell agentic software — "here's how we picked the model, here's the eval, here's the cost per task."
- **Insight:** **The eval suite is the artifact, not the router.** The router is the shim; the suite is the thing you keep updating and that keeps gaining value. If you only ship the shim, you've built a toy. Keep the suite public, keep adding adversarial cases.

→ Cross-link: [2026-09-10 router artifact](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact)

**Tags:** `#router #evals #model-fluency #cost-optimization`

---

## 3. Pre-stage the Anthropic S-1 reading protocol {#3-s1-reading-protocol}

**Why now**
- The **Anthropic prospectus is expected on the roadshow docket this week** (per [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo-roadshow)). When it drops, you want to be **ready to extract value in 90 minutes**, not spend 4 hours surveying the document.

**The template to pre-write tonight**

Create a file `anthropic-s1-notes.md` (private) with these pre-formed sections you'll fill in during the read:

```markdown
# Anthropic S-1 — read on [DATE]

## Revenue by segment (table)
| Segment | FY25 | FY26 TTM | YoY | % of total |
|---|---|---|---|---|
| API ("Claude API, direct") | | | | |
| Claude Code | | | | |
| Enterprise (Claude for X — Legal, Finance, SMB) | | | | |
| Managed Agents / Deployment Co | | | | |
| Other | | | | |

## Customer concentration (top-10 % of revenue)

## R&D spend / revenue, past 3 years

## Compute commitments (total $, by vendor)
- Nvidia / Blackwell
- Google TPU (per 2026-05-08 $200B deal)
- xAI Colossus 1 tenancy (per 2026-05-21: $1.25B/mo through 2029)
- AMD MI450 (per 2026-07 $5B equity + offtake)

## Headcount by function
- Research
- Product + Eng
- Sales / Solutions / FDE
- Policy / Trust & Safety

## Risk-factor extraction (the actually-interesting ones)
- Competition — specifically how they describe OpenAI, Google
- Compute single-source risk — do they call it out?
- Litigation — anything on Apple-adjacent, labor, copyright
- Model-safety / regulatory

## Executive comp (grant structure)
- CEO
- CTO
- Head of Research

## 1-page comparison vs OpenAI S-1 (Q4 target)
- Revenue growth rate
- Gross margin
- R&D intensity
- Enterprise mix vs API mix
- Compute cost / revenue
```

**Publish timeline**
- Day 0 (prospectus drops): 90-min read, fill the template.
- Day 1 evening: 1-page LinkedIn post with the 3 most surprising findings.
- Weekend: Full comparison vs the 2026-05-22 OpenAI IPO narrative (and any live OpenAI S-1).

**Why it matters to you**
- **Job:** When Anthropic lists, **you will be in conversations where S-1 fluency is the differentiator** — every AI-adjacent interviewer will ask "what did you learn from the Anthropic S-1?" The candidate with specific numbers + an opinion wins.
- **Startup:** The S-1 is **the richest competitive-intelligence document** anyone in AI will have access to this year. Revenue mix tells you where the real demand is; risk-factors tell you where Anthropic itself thinks the walls are.
- **Insight:** **Pre-staging the template is the trick.** The S-1 will be 300+ pages. People who try to read it top-to-bottom will drown. People who have a 10-question extraction grid pre-written will have a **publishable artifact within 2 hours of filing**.

**Tags:** `#anthropic #ipo #s1 #interview-prep #competitive-intel`

---

## 4. Daily hygiene — one new habit this week

**Habit:** When you read any AI news this week, note **two things** before closing the tab:
1. **Which category does it fit?** (big-lab-move / new-emerging / practical / research / career)
2. **What's the one next action for me?** (apply, build, read, email, nothing)

Keep a one-line note per item in a running `inbox.md`. By weekend, your WATCHLIST / ACTIONS / APPLICATIONS files should pull from that inbox — not from re-reading the news. This is the **Mollick "notice-and-note" habit** applied to AI news.

**Tags:** `#habit #productivity #information-hygiene`

---

## Threads to carry forward

- **Prompt caching + Fable 5.1 $0.25/1M cache-reads (from 2026-09-10):** verify your bill reflects the discount this month; if not, your SDK/version may not be picking it up.
- **Agent SDK June 15 metering (from 2026-05-16):** 4 months in; audit your Claude Code vs Agent-SDK vs API-direct usage split monthly.
- **The 4-primitive Claude Code decision tree (from 2026-09-10):** Hooks / Skills / Subagents / CLAUDE.md — if any of your projects still has rules embedded in prompts, migrate them.
