# 05 — Career & Startup — 2026-10-30 (Friday)

Two sections, both actionable this week. **§1** anchors the market comp for the FDE lane. **§2** is the weekend-artifact plan — treat this as a 90-minute checklist with a published deliverable at the end.

---

## 1. The FDE comp anchor just surfaced — $280K–$320K base at Anthropic (US), partner-firm path still open {#1-fde-price-anchor}

**What.** Anthropic's Applied-AI **Forward Deployed Engineer** listings posted this month publicly state **$280,000 – $320,000 USD base** for SF / NY / Seattle, with **3+ years of customer-facing technical experience** as the minimum bar. Other open listings:

- **Munich (Aug 17 posting, open).** Localized comp not disclosed.
- **London (Sales track, open).** The London listing sits under Sales, which is a tell — "FDE as revenue-attached" is how the UK team is scoping the role.
- **Multi-city US (Boston / NY / Seattle / SF / DC).** Open; same qualification bar.
- **Historical Munich (April 2026).** Closed. Treat it as the comparison for how long these windows stay open.

The **Frontier Academy track** (from the Oct 2 announcement; see [2026-10-14/01 §1](../2026-10-14/01-big-lab-moves.md#1-frontier-academy)) is the pre-qualified path through Accenture / Bain / Capgemini / Commonwealth Bank / Deloitte / McKinsey / Morgan Stanley / Novo Nordisk. **The $280K–$320K base is the open-market anchor** — direct apply if your résumé reads at that bar; partner-firm residency if you need the credential first.

**One security note.** Secondary sources flag an **active recruiter-spoofing campaign** targeting FDE candidates — **Anthropic recruiters only contact from `@anthropic.com` addresses.** Reject any Gmail / Hotmail / `@anthropic-careers.com`-style sender immediately. Add this to your "spam-detection checklist" before responding to any outreach.

**Why it matters for you specifically.**

- **Your profile (CS grad student, Anthropic-committed stack, MCP + cost-aware agent design portfolio) is already shaped for this market.** The question is whether to apply direct or via partner firm. **Direct is viable if** you can show: 2+ shipped MCP servers, a public cost-router with eval, 1+ cold-email conversation with an Anthropic FDE, and the Claude Code sandbox-runtime deep-dive from [`03` §1](./03-practical-skills-and-tools.md#1-sandbox-runtime). **Partner-firm is viable if** your experience section still reads as more "studied" than "shipped" — you want 6–12 months of McKinsey / Accenture / Deloitte deployment reps before direct-apply.
- **The $280K–$320K base is the comp number to internalize.** Any FDE-adjacent role you accept this cycle should be benchmarked against it. A $200K offer at a cheaper vendor is a 25% discount; a founding-engineer offer at a Series B needs to clear ~$250K cash + 0.5%+ equity to beat it on 5-year EV.
- **The Munich + London + DC footprint is a geography-flex.** If US visa / H-1B is a constraint, Munich is the open EU posting right now. Verify EU-work-authorization requirements before investing time on the London Sales-track listing.

**What to do this week (concrete).**

1. **Update LinkedIn / résumé with the Oct-18 Opus 5.5 + Oct-26 Terra + Oct-13 Argon numbers** in your "model stack" bullet. This is the single-highest-leverage résumé edit of the quarter.
2. **Send one cold email to an Anthropic Applied-AI FDE on LinkedIn.** Opening line: "I shipped a four-tier router (Haiku 5.5 + Terra + Argon + Opus 5.5) this weekend — mind if I share the eval numbers?" (You'll have the router from `03` §2.) *Only* if you have the artifact ready — do not cold-email on promises.
3. **Apply to the SF / NY / Seattle Applied-AI FDE listing + the Munich listing + one partner-firm job** (McKinsey QuantumBlack AI Engineer, Deloitte AI Specialist, Accenture Technology Consulting — pick whichever matches your geography best).

**Sources.**
- [primary] [Anthropic Careers — Forward Deployed Engineer job pages](https://www.anthropic.com/careers/jobs/4985877008)
- [primary] [Anthropic Careers — Munich FDE](https://www.anthropic.com/careers/jobs/5012991008)
- [aggregator] [General Catalyst Jobs — Anthropic FDE listings](https://jobs.generalcatalyst.com/companies/anthropic)
- [aggregator] [Accel Jobs — Anthropic FDE listings](https://jobs.accel.com/companies/anthropic)
- [analysis] [paraform — FDE role breakdown (compensation benchmarking)](https://www.paraform.com/blog/forward-deployed-ai-engineer)
- [analysis] [paraform — What is OpenAI's Forward Deployed Engineer](https://www.paraform.com/insights/openai-forward-deployed-engineer)

`#anthropic #fde #careers #comp #partner-firms #munich`

---

## 2. Weekend artifact: the Oct-30 router rebuild → publish → cold-outreach (90-minute version, Fri or Sat) {#2-weekend-artifact}

**Goal.** Ship the four-tier router artifact from [`03` §2](./03-practical-skills-and-tools.md#2-router-rebuild). Publish it. Use it as the opener in two FDE cold emails.

**The 90-minute block.** Pick a Friday night or Saturday morning; close Slack; put phone face-down.

- **Minutes 0–15: scaffold.** Create `cost-aware-agent-router-2026-10` GitHub repo. Copy README skeleton from your Oct-14 router (if you shipped one; else from the table in [`03` §2](./03-practical-skills-and-tools.md#2-router-rebuild)). Fill in the four-tier pricing table.
- **Minutes 15–45: router + logging.** Implement `route(task) -> model_id` with the three decision rules (`single-step → Haiku`, `visual-GUI → Terra`, `long-output → Argon`, `else → Opus 5.5`). Wrap each model call with a cost logger that records `model_id, input_tokens, output_tokens, cost_usd, latency_ms, correctness`.
- **Minutes 45–75: eval run.** Run the 5-case eval (PDF extract, calendar event via connector, long-thread summarization, one-file code fix, multi-step research). Report cost / latency / correctness per case under three router configs: (a) Opus-5 baseline (if you still have the harness from Oct 14), (b) Opus-5.5-only, (c) Oct-30 four-tier router.
- **Minutes 75–90: writeup + publish.** 300-word blog post. The money sentence: **"Moving from the Oct-14 two-tier router to the Oct-30 four-tier router dropped total eval cost by X% at Y pp correctness delta, with Z% of calls routed to Terra for GUI steps."** Push to GitHub main. Tweet-thread + LinkedIn post with the one-screen table + the two numbers (cost delta + correctness delta).

**Cold-outreach plan (post-publish, Sunday).**

- **Target 1: Anthropic Applied-AI FDE** — pick one you've found on LinkedIn (preferably not a recruiter — an actual IC FDE whose work you can cite).
- **Target 2: a partner-firm AI engineer** at McKinsey / Deloitte / Accenture — one from the Frontier Academy announced list.

Both emails use the same ~90-word template:

> Hi [name] — I'm a CS grad student focused on cost-aware agent design on the Anthropic stack. This weekend I rebuilt a four-tier router around Haiku 5.5 + GPT-6.1 Terra + Gemini 4 Argon + Opus 5.5, with explicit cost + specialty routing. Repo: [link]. Eval shows [X% cost drop at Y pp correctness]. I'd love 20 minutes to hear how your team thinks about model routing in [enterprise / government / healthcare] deployments — I'll bring questions, not a pitch. Happy to work around your calendar.

**Why this works.** The artifact + the opener + the ask ("hear how your team thinks about X") is the full set of social-moves that distinguish an actual-engineer from a career-tourist. The $280K–$320K market is already paying for this profile — the question is whether you make the hiring manager's job of finding you easier than the alternatives.

**What NOT to do this weekend.**

- Don't build a *new* MCP server. The router is more valuable right now (lower effort, higher legibility, more current).
- Don't learn Argon's quirks for creative long-form. The useful specialty is structured long-output; test on that.
- Don't send more than 2 cold emails. Volume dilutes the artifact's effect; the right ratio is one artifact → two targeted conversations.

**Watchlist (for next week's edition).**

- Did Anthropic open the Claude Marketplace connectors to third-party devs? (If yes: ship a Duet-adjacent connector.)
- Did Anthropic file the public S-1? (If yes: hiring posture over the next 60 days is the signal.)
- Did a Series-B agent-governance / Terra-constraint company announce? (If yes: new target list for cold-outreach.)
- Did a vertical Duet-shaped product launch? (First copycat is probably legal or SMB finance.)

**Sources.**
- Repo + artifacts you'll ship this weekend (not published yet — your deliverable).
- Pricing anchors: see [`03` §2](./03-practical-skills-and-tools.md#2-router-rebuild) for the four primary links.
- Market comp anchor: see §1 above.

`#careers #startup #weekend-artifact #router #cold-outreach #fde`

---

**End of §05.** Return to [`00` TL;DR](./00-tldr.md).
