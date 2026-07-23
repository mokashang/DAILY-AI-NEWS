# TL;DR — 2026-06-09 (Tuesday)

Sixty-second skim. **The morning after WWDC: Apple shipped the Extensions framework, Anthropic's protocol just became AWS-native infrastructure, and the next 96 hours stack four hard deadlines.** **WWDC graded ~6/8 on yesterday's pre-keynote grid** ([2026-06-08](../2026-06-08/01-big-lab-moves.md#1-wwdc)): **Gemini-powered Siri confirmed** as the default backbone, **Apple Intelligence Extensions framework shipped** with a system-level **Claude / Gemini / ChatGPT picker**, **iOS 27** with 30% faster app launches, **macOS Golden Gate** dropping Intel for good — but the **revenue-share terms for Extensions are not yet public** and there's no on-stage mention of Anthropic / OpenAI shipping Extensions on day 1. Underneath: **AWS MCP Server is GA today** ([primary](https://aws.amazon.com/blogs/aws/the-aws-mcp-server-is-now-generally-available/)) — Claude Code / Cursor / Codex plug-ins on day 1, IAM-scoped agent permissions, CloudWatch per-call observability — meaning **MCP is now the de-facto agent-cloud standard across consumer browser (WebMCP), enterprise cloud (AWS MCP Server), and OS picker (Apple Extensions speaks an MCP-shaped intent grammar).** The 96-hour stack: **Code w/ Claude Tokyo (Wed Jun 10, T-1)** · **SpaceX IPO pricing Thursday (Jun 11, T-2; NASDAQ "SPCX")** · **Anthropic Agent SDK metering Sunday (Jun 15, T-6)** · **Anthropic Claude Partner Network (announced Jun 3) — the channel-side complement to OpenAI Deployment Co**. For you: **the Tuesday-morning post you queued yesterday writes itself** ([2026-06-08/03 §3](../2026-06-08/03-practical-skills-and-tools.md)); ship it before lunch and pair with the AWS-MCP install.

---

1. **WWDC GRADED: ~6/8 — Gemini-Siri + Extensions framework SHIPPED.** Gemini is the **default** Siri model, but the **Extensions picker lets users route to Claude / Gemini / ChatGPT** at the OS level (not per-app). iOS 27 ships with up to 30% faster app launches; macOS Golden Gate (macOS 27) drops Intel; Apple Intelligence expanded across Mail / Messages / Calendar / Reminders / Photos / Safari / Phone ([primary] [Apple newsroom](https://www.apple.com/newsroom/2026/06/apple-unveils-next-generation-of-apple-intelligence-siri-ai-and-more/) · [secondary] [TechRadar live blog](https://www.techradar.com/news/live/apple-wwdc-2026-live) · [secondary] [Engadget recap](https://www.engadget.com/2189698/everything-announced-at-apples-wwdc-2026-keynote/)). **What did NOT land on-stage:** revenue-share % for Extensions, day-1 partner list of which AI labs ship Extensions immediately, developer SDK availability date. → [`01` §1](./01-big-lab-moves.md#1-wwdc-graded) `#apple #wwdc #extensions #siri #graded`

2. **AWS MCP Server is GA today — Anthropic's protocol becomes AWS-native infrastructure.** Managed remote MCP server with **day-1 plugins for Claude Code, Cursor, Codex**; **IAM policy separation of human vs agent permissions** (the long-asked-for agent-RBAC primitive); **CloudWatch metrics emit MCP calls separately from direct human/SDK calls**. Pair with the May-19 **WebMCP origin trial in Chrome 149** + yesterday's WWDC Extensions = **MCP is the agent-tool-use standard across all three surfaces.** ([primary] [AWS blog](https://aws.amazon.com/blogs/aws/the-aws-mcp-server-is-now-generally-available/)). → [`02` §1](./02-new-emerging.md#1-aws-mcp-ga) `#aws #mcp #standards #infra`

3. **Anthropic Claude Partner Network — Services Track + Partner Hub (announced Jun 3).** Channel-side complement to OpenAI Deployment Co + Tomoro M&A. PwC's 30K-Claude-Code-trained group ([2026-05-15](../2026-05-15/01-big-lab-moves.md)) is the anchor; Deloitte / Accenture / EY counter-commitments expected inside 90 days; boutique Anthropic-specialist shops the under-leveraged tail. **A new high-volume FDE hiring lane just opened — apply this week before the post-S-1 application wave.** → [`02` §2](./02-new-emerging.md#2-partner-network) · [`05` §1](./05-career-and-startup.md#1-partner-network) `#anthropic #fde #partner-network`

4. **The 96-hour stack — four deadlines that fully bracket your week.** **Wed Jun 10 (T-1): Code w/ Claude Tokyo** — APAC customer presenters; expected SDK feature announcements. **Thu Jun 11 (T-2): SpaceX IPO pricing**, trading Friday on NASDAQ as "SPCX" at ~$1.75T (the precedent print for the Anthropic + OpenAI offerings). **Sun Jun 15 (T-6): Anthropic Agent SDK metering** goes live — programmatic Claude bills at API list rates. **And: by EOD today, the FDE-apply window from yesterday's post-WWDC plan** ([2026-06-08/05 §1](../2026-06-08/05-career-and-startup.md#1-fde-comp)). → [`01` §2](./01-big-lab-moves.md#2-tokyo-and-ipo) · [`05` §2](./05-career-and-startup.md#2-96-hour-stack) `#tokyo #spacex #ipo #metering`

5. **Practical: install AWS MCP Server + lock your Claude Code MCP set to 4–6.** Anthropic's updated best-practices doc explicitly recommends **picking 4–6 MCP servers, not all available options** — Cursor's 40-tool ceiling fills faster than people expect. Pair with **Playwright MCP for autonomous UI verification** in long-running agent tasks ([primary] [Claude Code best practices](https://code.claude.com/docs/en/best-practices) · [analysis] [community summary](https://mcp.directory/blog/claude-code-best-practices)). → [`03` §1](./03-practical-skills-and-tools.md#1-aws-mcp-setup) `#claude-code #mcp #install`

6. **Research: "The End of Software Engineering" (arXiv 2606.05608, Jun 5).** Provocative title; nuanced body. Claim: the unit of authored work moves from source file to *agent specification / harness*; SWE survives as a discipline but its center of gravity shifts to **agent-spec + verification + cost engineering**. **Read end-to-end before your next AI-company interview** — the calibrated take is what differentiates a strong candidate. Pair with the still-active Karpathy → Anthropic pre-training-automation thread ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)) and the new 80%-Claude-authored disclosure ([2026-06-08/01 §3](../2026-06-08/01-big-lab-moves.md#3-anthropic-self-build)). → [`04` §1](./04-research-progress.md#1-end-of-swe) `#arxiv #agents #careers`

7. **Hark $700M Series A at $6B post-money — CX-agent confirms winner-take-most.** ([2026-06-06](../2026-06-06/02-new-emerging.md) had it as Hark $700M / personal-AI-hardware via NVIDIA + AMD + Intel + Qualcomm; Tech Startups roundup confirms today.) **Do not enter as a new founder in CX-agent unless you have a structural unfair advantage.** Lateral: build CX-agent **eval / observability / safety middleware** (Judgment Labs is the closest comp). → [`02` §3](./02-new-emerging.md#3-hark) `#funding #cx-agents #wedges`

8. **Skill read of the week — three distribution surfaces ratified in 30 days.** Apple Extensions (yesterday), AWS Bedrock multi-vendor (June 1–2), AWS MCP Server (today). **Pick exactly one and ship one demo this week** ([`05` §3](./05-career-and-startup.md#3-three-surfaces)). Recommended order given your [ME.md](../ME.md) focusing decision: **AWS MCP Server > AWS Bedrock multi-vendor > Apple Extensions**. → [`05` §3](./05-career-and-startup.md#3-three-surfaces) `#skills #portfolio #distribution`

---

## One thing to DO this Tuesday

→ **Ship the Tuesday-morning WWDC scorecard post that yesterday's `00-tldr` queued** ([2026-06-08/00](../2026-06-08/00-tldr.md)) — but **don't stop there.** Pair it with a **second** LinkedIn post by 5 PM PT: *"AWS MCP Server went GA today — installed it in my Claude Code project, IAM-scoped agent permissions + CloudWatch per-call observability"* ([install in `03` §1](./03-practical-skills-and-tools.md#1-aws-mcp-setup)). **Two posts, one day, exact terms** (`Apple Intelligence Extensions` and `AWS MCP Server`) = the keyword-precision lesson from [2026-05-20/01 §1](../2026-05-20/01-big-lab-moves.md#1-io-scorecard) executed.

## Watchlist deltas

- 🟢 **Apple "Extensions" SDK:** **CONFIRMED ON STAGE** (was 🟡 from 2026-06-06 SATURDAY SORT and 2026-06-08). Multi-AI picker (Claude / Gemini / ChatGPT); Gemini default Siri. Open: revenue share %, day-1 partner labs, dev SDK access date. Status flips 🟡→🟢.
- 🆕 **AWS MCP Server GA:** new thread — Azure / GCP equivalents (90-day window); first $50M+ raise in "MCP-server-managed-service" category; whether OpenAI joins the MCP standard formally vs forks.
- 🆕 **Anthropic Claude Partner Network (Services Track + Partner Hub):** new thread — first 10 named Services-Track partners; comp bands for FDE roles inside named partners; whether Deloitte / Accenture / EY counter-commit inside 90 days.
- 🆕 **Apple Extensions ecosystem (post-WWDC):** new thread — first labs to ship Extensions on day 1; first vertical-app Extensions breakouts; revenue-share terms when published.
- ➡️ **Code w/ Claude Tokyo (Wed Jun 10):** **T-1.** Live livestream from 10 AM JST (5 PM PT Tue / 9 AM PT Wed depending on session); watch for APAC customer presenter + any post-Apple-Extensions surface-area mention.
- ➡️ **SpaceX IPO (Thu Jun 11 pricing → Fri Jun 12 trading, NASDAQ "SPCX"):** **T-2.** First-day pop is the precedent print for Anthropic + OpenAI offerings.
- ➡️ **Anthropic Agent SDK metering (Sun Jun 15):** **T-6.** Final-week toggle reminder ([2026-05-18/03](../2026-05-18/03-practical-skills-and-tools.md)); cost-router baseline data collection ([2026-06-08/03 §1](../2026-06-08/03-practical-skills-and-tools.md#1-opus-48-baseline)).
- ➡️ **Anthropic confidential S-1 (Jun 1) + Series H ($65B / $965B):** still 🟢 EXECUTING; segment-level revenue mix lands ~15d pre-roadshow.
- ➡️ **OpenAI confidential S-1 (May 22):** still in SEC review; Anthropic now timing-ahead.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + WWDC graded scorecard in [`01` §1](./01-big-lab-moves.md#1-wwdc-graded) |
| 20 min | [`01` §1](./01-big-lab-moves.md#1-wwdc-graded) (WWDC actuals) + [`02` §1](./02-new-emerging.md#1-aws-mcp-ga) (AWS MCP Server GA) + [`04` §1](./04-research-progress.md#1-end-of-swe) (End-of-SWE paper) |
| Today | "One thing to DO" above — two LinkedIn posts + AWS MCP install |
| This week | [`05` §1](./05-career-and-startup.md#1-partner-network) — apply to 1 Partner-Network-adjacent role with the AWS-MCP demo attached |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
