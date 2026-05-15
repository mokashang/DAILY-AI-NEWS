# TL;DR — 2026-05-15

Sixty-second skim. Read in order; jump to the deep file if a bullet grabs you.

---

1. **Anthropic in advanced talks to buy Stainless for ≥$300M — i.e., Anthropic would own the SDK toolchain that ships OpenAI, Google, Cloudflare and Meta's official client libraries.** A 2× markup on Stainless's Dec 2024 $150M price; partly in Anthropic stock. The platform-vs-platform war just moved one layer down the stack. → [`01-big-lab-moves.md`](./01-big-lab-moves.md#1-stainless) `#anthropic #m-and-a #devtools #moat`
2. **PwC expands Anthropic alliance: 30,000 US staff trained + certified on Claude Code, scaling to PwC's 364,000-person global workforce; a new Claude-native Finance business group inside PwC's CFO practice.** Clients reporting "up to 70%" delivery gains (insurance underwriting 10wks→10 days). The Anthropic enterprise flywheel turns one more time after yesterday's Ramp data. → [`01-big-lab-moves.md`](./01-big-lab-moves.md#2-pwc) `#anthropic #enterprise #consulting`
3. **Google I/O is now 4 days out (May 19, 10 AM PT)** — leaks confirm Gemini 4 (native image + video gen), a "Remy" personal agent ("24/7 assistant that takes actions on your behalf"), Gemini Spark proactive background agent, Android 17 agentic SDK, and the Googlebook/Aluminium OS developer SDK. Watch the keynote live. → [`01-big-lab-moves.md`](./01-big-lab-moves.md#3-io-preview) `#google #gemini #io2026`
4. **AI Engineer is the #1 fastest-growing US job title — postings +143% YoY, average pay $206K (+$50K YoY), AI-skill wage premium jumped from 25% → 56% in 12 months.** And the title fragmented: 75%+ of listings now want a specialty (Applied ML, ML Platform, LLM Eng, AI Product Eng, Responsible AI), not a generalist. **The single most actionable signal in this entire edition for your job hunt.** → [`05-career-and-startup.md`](./05-career-and-startup.md#1-ai-engineer-fastest) `#jobs #salary #mle`
5. **Karpathy's CLAUDE.md 4-rule playbook is circulating again** — minimal-diff edits, ask before you guess, kill speculative abstractions, test before "done." A 30-minute habit shift that meaningfully raises Claude Code's output quality. Add it to your repo today. → [`03-practical-skills-and-tools.md`](./03-practical-skills-and-tools.md#1-claude-md) `#claude-code #workflow #karpathy`
6. **arXiv: "Attractor Models — Solve the Loop" (May 12)** — frames latent refinement as a fixed-point problem. Same-quality reasoning at meaningfully lower memory/compute than chain-of-thought scaling. If it generalizes, it's a new axis of cost-reduction below the model size axis. → [`04-research-progress.md`](./04-research-progress.md#1-attractor-models) `#research #reasoning #efficiency`
7. **Chapter (Medicare-navigation AI) closes $100M Series E led by Generation Investment Management** — plus Performativ €5.5M (wealth-management AI OS) and Marloo $10M (financial-adviser workflows). The vertical-AI-for-regulated-industries thesis just got three same-day data points. → [`02-new-emerging.md`](./02-new-emerging.md#1-vertical-regulated) `#seed #vertical-ai #regulated`
8. **OpenSource-MCP momentum: build-your-own-MCP-server tutorials are dominating dev-tools content this week.** The market is past "what is MCP" and into "ship one this weekend." Recipe inside. → [`03-practical-skills-and-tools.md`](./03-practical-skills-and-tools.md#2-build-mcp) `#mcp #agents #open-source`

---

## One thing to DO this week

→ **Build and publish one MCP server by Sunday night.** The Stainless acquisition + PwC training + I/O agent reveals are three independent signals that the *connector layer* (MCP, Agent SDKs, official client libraries) is where the next 18 months of enterprise integration work lives — and the *shortest possible* portfolio artifact you can produce that demonstrates you can ship in that layer is a working public MCP server with a README, an eval, and a 90-second demo video. Recipe and three "weekend-sized" ideas inside [`03`](./03-practical-skills-and-tools.md#2-build-mcp). Pin it on your resume above your projects section.

## Watchlist deltas

- 🆕 **Anthropic/Stainless acquisition:** new thread — first major Anthropic M&A move into the SDK layer. Watch for the close, and for OpenAI's response (own SDK team build-out, or competing acquisition)
- 🆕 **PwC × Anthropic 30,000-cert program:** new thread — single largest enterprise-training commitment to one AI vendor on record. Watch for Deloitte / Accenture / EY counter-moves
- 🆕 **Gemini "Remy" + "Spark" agents:** new thread — code-named, leak-confirmed, expected at I/O May 19
- 🆕 **AI-skill wage premium 25%→56%:** new thread — Dice / Lightcast data; tracks the bifurcation of the engineering labor market
- ⬆️ **Google I/O preview locked:** May 19, 10 AM PT — Gemini 4, Android 17 agentic SDK, Aluminium OS / Googlebook SDK, Android XR glasses Gen 2, "Remy" + "Spark" agents
- ⬆️ **On-Policy Distillation sweep:** "Many Faces of OPD" (arXiv 05-11) extends the May watchlist thread with a unified failure-mode taxonomy
- ➡️ **Meta May 20 layoffs (8,000):** 5 days out — talent flight window opens May 21
- ➡️ **Anthropic $30–50B raise at ~$950B:** no term-sheet news today; still active

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + `01-big-lab-moves.md` Stainless story |
| 20 min | `05-career-and-startup.md` (today's career signals are the strongest in 2 weeks) |
| Weekend | `03-practical-skills-and-tools.md` action: ship and publish one MCP server |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
