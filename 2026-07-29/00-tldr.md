# TL;DR — 2026-07-29 (Wednesday)

Sixty-second skim. **A frontier model broke a NIST post-quantum finalist in 60 hours, MCP 2026-07-28 shipped on time, and the Anthropic Fellows deadline you were watching last Saturday closed on Sunday.** **Claude Mythos Preview** disclosed a HAWK-256 attack that drops key-recovery cost from ~2⁶⁴ → ~2³⁸ (plus a 200–800× 7-round AES-128 speedup) after **two years** of expert human review missed it — cryptanalysis just repriced from person-years to $/billion tokens. **MCP 2026-07-28 became a shipped spec** — stateless core, OAuth 2.1, MCP Apps/Tasks as versioned extensions. **Grok 4.6 (1.5T) + 4.7 (2.1T)** pre-announced for August. **Google DeepMind** promised monthly Gemini cadence to compensate for the 3.5 Pro delay and reported morale drag — **hiring bar is quietly softer than it's been in 24 months**. And the **Claude share-link → Google indexing incident** patched by 07-28: audit your share links today.

*(Continuation of the [2026-07-25](../2026-07-25/) edition. Threads that survived: Opus 5 effort routing, MCP migration, three-lab market. Threads that closed: Fellows deadline (missed if you didn't submit) — see `05` §1 for the recovery plan.)*

---

1. **Mythos broke HAWK-256 in ~60 hours; 7-round AES-128 attack sped 200–800×.** Anthropic disclosed 07-28/29: nontrivial lattice automorphism drops HAWK-256 key-recovery cost from ~2⁶⁴ to ~2³⁸ operations. HAWK is a NIST PQC third-round candidate; two years of human cryptanalysis missed it. Neither result breaks production systems today. **The reframe is the story:** cryptanalysis is now a compute line item, not a person-year budget. → [`01` §1](./01-big-lab-moves.md#1-mythos-hawk) · [`04` §1](./04-research-progress.md#1-llm-cryptanalysis) `#anthropic #mythos #cryptanalysis #post-quantum`

2. **MCP 2026-07-28 shipped on schedule.** Stateless core (removes session handshake), OAuth 2.1 + OIDC first-class, MCP Apps / Tasks promoted to a versioned extensions framework, `Mcp-Method` / `Mcp-Name` headers for LB-friendly routing. **400M monthly SDK downloads** (4× YoY). Migration is a one-afternoon job — playbook in `03` §2. → [`01` §2](./01-big-lab-moves.md#2-mcp-shipped) · [`03` §2](./03-practical-skills-and-tools.md#2-mcp-migration) · [`05` §4](./05-career-and-startup.md#4-migration-window) `#mcp #stateless #oauth #protocol`

3. **Grok 4.6 → 4.7 in five weeks.** Musk pre-announced 07-28: Grok 4.6 (**1.5T parameters**) ≈ Aug 7, Grok 4.7 (**2.1T parameters**) late Aug / early Sept. Model-size disclosure as a **recruiting signal** — Anthropic and OpenAI stopped publishing params years ago; Musk needs the signal because xAI mindshare trails the eval-topping labs. → [`01` §3](./01-big-lab-moves.md#3-grok-cadence) `#xai #grok #cadence #recruiting`

4. **Google DeepMind: monthly cadence promised; hiring bar quietly softer.** Sundar Pichai confirmed **Gemini 4 in pre-training** ("most ambitious pre-training run yet"); monthly Gemini releases going forward. But Gemini 3.5 Pro's delay + morale drag + AlphaFold team shutdown = **hiring urgency up**. If DeepMind is on your list, apply within the next 3 weeks — timing markets around lab-level events is real edge. → [`01` §4](./01-big-lab-moves.md#4-google-deepmind) · [`05` §3](./05-career-and-startup.md#3-deepmind-window) `#google #deepmind #gemini #hiring-window`

5. **Anthropic Fellows deadline missed (2026-07-26).** If you didn't submit: set **2026-12-01 calendar reminder** for next cohort; between now and then ship **one** alignment-adjacent artifact (the eval-design gap from `04` §1 fits perfectly). Applications with a public artifact convert 3–5× the ones without. → [`05` §1](./05-career-and-startup.md#1-fellows-retro) `#anthropic #fellows #missed-deadline #next-cohort`

6. **FDE market: fresher numbers, bigger.** [Perspective AI's 1,200-FDE comp report](https://getperspective.ai/blog/2026-forward-deployed-engineering-compensation-report-1200-fdes): median mid $385K, staff $610K, principal at frontier labs $1.2M+. **Equity now 55–70% of TC.** 224 open FDE roles across 39 AI companies. ~60% wash-out on the customer-conversation round — this is a specific practiceable skill. → [`05` §2](./05-career-and-startup.md#2-fde-market) `#fde #comp #anthropic #openai`

7. **Physical AI: Agility Robotics goes public (SPAC, $2.5B pre-money); BYD humanoid unveil in August.** Agility opens a 60,000 sq ft Physical AI hub in Fremont. BYD adds automaker-scale supply chain to the China humanoid cohort. **U.S. humanoid startups: your moat has to be software** — hardware is a losing bet against BYD's cost curve. Adjacent categories are still open (fleet ops, eval tooling, teleop-supervised RL data collection). → [`02` §1–2](./02-new-emerging.md#1-agility-spac) `#humanoid #agility #byd #physical-ai`

8. **Claude share-link Google indexing incident patched by 07-28.** 2026-07-25 Reddit users noticed `site:claude.ai/share` on Google exposed resumes, health records, patient names. Anthropic updated `robots.txt` by 07-28. **Do the 10-minute share-link audit today** — and cite this specifically in FDE / enterprise-facing interviews. → [`01` §5](./01-big-lab-moves.md#5-share-leak) · [`03` §3](./03-practical-skills-and-tools.md#3-share-audit) `#anthropic #security #enterprise-trust`

9. **Sonnet 5 promo pricing ($2/$10) ends 2026-08-31.** Standard pricing ($3/$15) takes effect 09-01 — **~50% COGS hike** if you're on Sonnet 5 default. Two moves: rerun cost/quality routing (Opus 5 `effort=low` may beat Sonnet 5 default), and front-load August traffic on the promo tier. → [`02` §4](./02-new-emerging.md#4-sonnet-pricing) `#anthropic #pricing #sonnet #cogs`

10. **Research: LLM-driven cryptanalysis crystallizes as a category; RL-compute FLOP-accounting matures.** The Mythos result's real contribution is the **eval methodology** (matched human-review baseline, controlled compute count) — that template will get cited more than the HAWK result itself. Meanwhile the RL-post-training literature converges on env-cost + episodes-to-signal as the honest way to compare runs. → [`04` §1–2](./04-research-progress.md#1-llm-cryptanalysis) `#arxiv #cryptanalysis #rl #methodology`

---

## One thing to DO this Wednesday

→ **The 10-minute share-link audit, tonight. The 3-hour MCP migration, this weekend.**

1. **Tonight (10 min).** [Audit your Claude / ChatGPT / Gemini share links](./03-practical-skills-and-tools.md#3-share-audit). Delete anything with your name + a company / résumé / client info. Rule going forward: shared = public.
2. **Today or tomorrow.** Set **2026-12-01 calendar reminder** for the next Anthropic Fellows cohort ([`05` §1](./05-career-and-startup.md#1-fellows-retro)).
3. **Friday.** Submit the [Deloitte-Anthropic FDE application](./05-career-and-startup.md#2-fde-market). Record the 2-minute customer-conversation video for your portfolio.
4. **Weekend (6–8 hrs).** Ship the [MCP-migrated agent-triangle artifact](./03-practical-skills-and-tools.md#4-this-weekends-artifact) — with the toy-cipher eval as the differentiator. Publish the 400-word migration writeup ([`05` §4](./05-career-and-startup.md#4-migration-window)).

## Watchlist deltas since 2026-07-25

- 🆕 **Claude Mythos → HAWK-256 + 7-round AES.** New thread — cryptanalysis-as-compute-line-item. Track NIST PQC responses over the next 90 days ([`04` §4](./04-research-progress.md#4-nist-pqc)).
- 🆕 **MCP 2026-07-28 shipped.** Migration window is 60–120 days; freelance and portfolio opportunities in [`03` §2](./03-practical-skills-and-tools.md#2-mcp-migration) and [`05` §4](./05-career-and-startup.md#4-migration-window).
- 🆕 **Grok 4.6 (Aug 7) + 4.7 (late Aug / early Sept) pre-announced.** Model-size-as-recruiting-signal is the sub-thread.
- 🆕 **Google DeepMind hiring window opens** post-3.5-Pro delay and AlphaFold shutdown. Apply within 3 weeks ([`05` §3](./05-career-and-startup.md#3-deepmind-window)).
- 🆕 **Claude share-link indexing incident.** Patched, but the enterprise-trust story ripples for 90 days ([`01` §5](./01-big-lab-moves.md#5-share-leak)).
- ➡️ **Opus 5 effort toggle.** Community numbers on cost/quality are now real ([`03` §1](./03-practical-skills-and-tools.md#1-opus-5-effort)).
- ➡️ **FDE market.** Confirmed and refined vs. last week: 1,200-FDE comp survey, 224 open roles. Deloitte-Anthropic apply-by-Friday still stands.
- ➡️ **YC S26.** Batch is mid-way through July–Sept run. 3 cold DMs still the action ([`05` §5](./05-career-and-startup.md#5-yc-s26)).
- ⬇️ **Anthropic Fellows Nov 2026 deadline.** Closed 07-26. Next cohort: Q1 2027.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Mythos in [`01` §1](./01-big-lab-moves.md#1-mythos-hawk) + FDE window in [`05` §2](./05-career-and-startup.md#2-fde-market) |
| 20 min | [`01` §1–4](./01-big-lab-moves.md) (Mythos + MCP + Grok + DeepMind) + [`03` §2](./03-practical-skills-and-tools.md#2-mcp-migration) (MCP migration playbook) — the four signals that changed your near-term plan |
| Tonight | [`03` §3](./03-practical-skills-and-tools.md#3-share-audit) — 10-min share-link audit; set Fellows reminder |
| Weekend | [`03` §4](./03-practical-skills-and-tools.md#4-this-weekends-artifact) — MCP-migrated agent-triangle + toy-cipher eval + 400-word migration writeup |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
