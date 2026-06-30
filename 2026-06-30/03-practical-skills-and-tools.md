# Practical Skills & Tools — 2026-06-30

The five tactical things you can act on this week. Each one is either (a) a tonight-install, or (b) a weekend artifact you can pin above your resume by Sunday. The frame for this edition: **the field standardized on the 6-primitive Claude Code stack in June** — if you don't have it set up by July, you're behind the median candidate.

Tags: `#claude-code #mcp #cost-routing #skills #weekend-project`

---

## 1. Tonight (45 min): install the 6-primitive Claude Code stack on one repo {#1-claude-code-stack}

**The fact:** The June community converged on **six primitives** as the canonical Claude Code surface: **CLAUDE.md, skills, subagents, slash commands, hooks, MCP.** The Marktechpost June-14 guide ("Claude Code Guide 2026: 25 Features with Examples + Demo") is the cleanest single reference; the SaaSCity / Clarista / TrueFoundry guides cover the MCP-specific pieces. **If you do exactly one Claude Code thing this month, do this tonight.**

**The 45-min install:**

```
1.  CLAUDE.md           # Karpathy 4-rule template (carried from 2026-05-17/03 §2)
2.  .claude/skills/     # 1 skill: "code-review" — SKILL.md + scripts/run.sh
3.  .claude/agents/     # 1 subagent: "lint-then-test" — parallel work, returns report
4.  .claude/commands/   # 1 slash command: /review — invokes the skill
5.  .claude/hooks/      # 1 pre-tool-use hook that blocks rm -rf and git push --force
6.  ~/.claude.json      # 4 MCP servers: github (read-only PAT), filesystem (scoped path),
                        #                postgres (read-only), playwright (browser)
```

**Decision rules (June 2026 consensus):**

- **Slash command vs Skill vs Subagent:** Slash command for a prompt template; Skill when there's domain logic / helper files / multi-step instructions; Subagent for **isolated, parallel work** (the subagent gets its own context window, returns a structured report). The June guides converge on this taxonomy.
- **MCP transport:** **stdio** for local tools (filesystem, git, sqlite), **http** for remote services (GitHub, Linear, Notion). Verify with `claude mcp list` or the `/mcp` panel.
- **Server count:** **4–8 servers** is the sweet spot. Tool Search (default on) keeps context cost low, but only connect what you actually use this month.
- **Security:** Narrowest credential possible per server. Read-only GitHub PAT for `github-mcp`. Keep secrets in `--env`, not in committed config. Review project-scoped servers before approving — they're the most common supply-chain attack surface.

**Sources:**
- [MarkTechPost — Claude Code Guide 2026: 25 Features with Examples + Demo](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[primary-guide]`
- [Computing for Geeks — Claude Code Cheat Sheet 2026](https://computingforgeeks.com/claude-code-cheat-sheet/) `[secondary]`
- [SaaSCity — Best MCP Servers for Claude Code in 2026 (+ Exact Setup Commands)](https://saascity.io/blog/best-mcp-servers-claude-code-2026) `[secondary]`
- [Clarista — Claude Code MCP Servers & Plugins: The Complete 2026 Guide](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) `[secondary]`
- [TrueFoundry — MCP Authentication in Claude Code 2026 Guide](https://www.truefoundry.com/blog/mcp-authentication-in-claude-code) `[secondary]`
- [CodeWithMukesh — Claude Code Tutorial for Beginners: Complete 2026 Guide](https://codewithmukesh.com/blog/claude-code-for-beginners/) `[secondary]`
- [Codegen — Build Claude Code Agent: Step-by-Step Beginner Guide](https://codegen.com/guides/building-first-agent/) `[secondary]`
- [Codegen — Claude Code MCP Servers: How to Connect External Tools](https://codegen.com/guides/connecting-mcp-servers/) `[secondary]`

### Why it matters to you

- **Job lens:** Every Anthropic Solutions / FDE / Integration JD in 2026 names some subset of these six primitives. Having a public repo where every primitive is wired and demonstrated (with a 60-second Loom) **answers the interview directly** — "show me a Claude Code workflow you've built" no longer requires hand-waving.
- **Startup lens:** This is the surface you'd integrate with to ship "Claude inside a vertical." Knowing it cold = your founder/founding-engineer pitch becomes "I've already shipped on this stack" instead of "I'd need to learn it."
- **Insight:** The convergence to six primitives is the **most important agent-engineering milestone of Q2 2026.** It means the surface is now stable enough to specialize on — you can build deep, not just wide. **Skill, hook, and MCP-server design are the three specializations that compound.** Slash commands and CLAUDE.md are tablestakes; subagents are the cost lever.

→ Action: marked in [`ACTIONS.md`](../ACTIONS.md) for tonight (Tue June 30).

---

## 2. The Terra cost-audit playbook (3-hour, billable shape) {#2-terra-audit}

**The fact:** GPT-5.6 **Terra** ([`01` §2](./01-big-lab-moves.md#2-gpt56)) ships at **$2.50 input / $15 output per 1M** — ~2× cheaper than GPT-5.5 at the same capability tier. For any team running existing GPT-5.5 production volume, **a Terra re-route audit prints money** the day it ships.

**The 3-hour playbook (a portfolio + paid-engagement shape):**

```
Hour 1 — Pull the trace.
  ☐ Export last 30 days of GPT-5.5 API usage (or simulate from a hot path).
  ☐ Bucket by prompt class (e.g. summarize-doc, classify-ticket,
    code-review, agentic-research, voice).
  ☐ Compute per-bucket: call count, p50/p95 latency, mean tokens in/out, $/call.

Hour 2 — Tag eligibility.
  ☐ Tag each bucket: Terra-eligible (mid-difficulty, no hard-mode reasoning) /
    Sol-required (hard reasoning, code-from-scratch, biology) /
    Luna-eligible (cheap classification, voice glue, high-volume).
  ☐ Conservatism rule: when in doubt, leave on Sol. Don't optimize into a regression.

Hour 3 — Simulate + write.
  ☐ Re-cost each tagged bucket at the new tier's price.
  ☐ Produce: monthly $ delta, % savings, expected p95-latency change,
    and the eval suite needed to verify safety of the migration.
  ☐ One-page memo with: assumption list, savings number, eval plan, rollback plan.
```

**For your portfolio:** anonymize the trace (mock if needed), publish the playbook as a public repo, link it on your AI Integration Engineer applications. The structure mirrors what a working FDE produces in the first week of an engagement.

**For paid work:** an SMB with $5K+/mo of GPT-5.5 spend will pay $2K–$5K for this audit. That's a one-weekend contract that doubles as a portfolio piece and a customer-discovery conversation.

**Sources:**
- [OpenAI — Previewing GPT-5.6 Sol (pricing table)](https://openai.com/index/previewing-gpt-5-6-sol/) `[primary]`
- [DataCamp — GPT-5.6 Sol, Terra, and Luna (capability/cost positioning)](https://www.datacamp.com/blog/gpt-5-6-sol-luna-terra) `[secondary]`
- [Artificial Analysis](https://artificialanalysis.ai/) `[primary-data]` — for benchmark + price-per-task cross-checks
- Carry-over: [2026-05-20/03 §4 the cost-router pattern](../2026-05-20/03-practical-skills-and-tools.md#4-cost-routing)

### Why it matters to you

- **Job lens:** This is the single most credible artifact to produce in interview prep for **OpenAI Deployment Company FDE** or **Anthropic Solutions** roles — both companies' first-customer conversations are some shape of this audit. Walking in with a public playbook is rare.
- **Startup lens:** "Cost-audit-as-a-service" is a genuine wedge in the cleared-customer regime — every customer running cleared models is doing a budget review against the Sol-vs-Terra-vs-Mythos cost surface. Two-customer engagement is enough to validate a productized version.
- **Insight:** The Terra price is **not a price cut** — it's a **capability cut packaged as a new SKU**. The discipline this requires is the discipline that becomes the job: knowing which workloads can step down a tier without a regression. Cost-routing is *the* skill, not *a* skill.

---

## 3. The cross-cloud Claude routing pattern (now that Foundry is GA) {#3-cross-cloud-routing}

**The fact:** With Claude now generally available in **Microsoft Foundry on Azure** ([`01` §4](./01-big-lab-moves.md#4-claude-foundry)) alongside **AWS Bedrock** and **Google Cloud Vertex**, you can build a **cross-cloud Claude router** that picks an endpoint by:

- **Customer data-residency / sovereignty requirements** (US data-zone in Foundry vs EU residency in Bedrock vs Google sovereign-cloud).
- **Latency** (per-region health).
- **Burst-pricing arbitrage** when one cloud has spot capacity.

**The 4-hour weekend build:**

```python
# Router contract (toy version)
class ClaudeRouter:
    def route(self, request) -> Endpoint:
        # 1. Residency hard-filter
        eligible = [e for e in self.endpoints
                    if e.region in request.allowed_regions]
        # 2. Soft preferences (cost, latency, current health)
        return min(eligible,
                   key=lambda e: e.cost * 0.6
                               + e.p95_latency_ms * 0.3
                               + e.health_penalty * 0.1)
```

**Pin in the public repo:** routing rules, the constraints they encode, and a per-cloud cost-and-latency dashboard. The README sells it as **"agnostic Claude deployment for compliance-constrained customers."**

**Sources:**
- [Anthropic Newsroom — Microsoft Foundry GA](https://www.anthropic.com/news) `[primary]`
- [Releasebot — Anthropic Release Notes (June 2026)](https://releasebot.io/updates/anthropic) `[aggregator]`

### Why it matters to you

- **Job lens:** Cross-cloud Claude routing is **rare-skill territory** at the new-grad level. Every major customer eventually hits a residency / sovereignty / regulator constraint; almost nobody at your level has built the pattern. One public router repo = a Tier-1 differentiator.
- **Startup lens:** The router can wrap into a SaaS for mid-market customers who don't want to negotiate three separate cloud-marketplace contracts and three FedRAMP boundaries. The wedge is **compliance simplification**, not cost arbitrage.
- **Insight:** The cross-cloud move is the **flip side of the release-by-Washington regime** ([`01` §1–2](./01-big-lab-moves.md)). The labs are constrained by Washington at release; the *clouds* are not. Microsoft selling Claude is the proof. Your skill stack should reflect the new shape of the industry — vendor-agnostic, region-aware, compliance-first.

---

## 4. Weekend project: a Claude Tag-shaped Slack demo {#4-claude-tag-demo}

**The fact:** Claude Tag ([`02` §3](./02-new-emerging.md#3-anthropic-product)) puts Claude into a Slack workspace as a tagged team member. **Building a public demo of this in a public Slack + linking the repo is the single most-credible "AI Integration Engineer" portfolio piece of June 2026.**

**The 4-hour build:**

```
1. Public Slack workspace (free tier).
2. Two channels: #engineering-ops, #customer-support.
3. Claude Tag wired (Enterprise beta access; or a stand-in via the Bolt SDK
   + Anthropic API if you don't have beta access).
4. Three workflows:
     - @claude triage  — summarize the channel's last hour, surface action items.
     - @claude oncall  — answer technical questions from a CLAUDE.md context file.
     - @claude digest  — daily 8 AM summary message.
5. A cost log: per-channel spend, per-user delegation pattern, refusal rate.
6. README + 60-second Loom + screenshots.
```

**Sources:**
- [Anthropic — Introducing Claude Tag](https://www.anthropic.com/news/introducing-claude-tag) `[primary]`
- [Slack Bolt SDK](https://slack.dev/bolt-python/) `[primary]` (for stand-in if no beta access)

### Why it matters to you

- **Job lens:** Identical-shape to the workflow an AI Integration Engineer ships on Day 5 of a new engagement. Pin above all other projects in your portfolio for AI Integration / Solutions roles.
- **Startup lens:** The cost-log piece is the actual product — "Claude Tag spend & policy console for Slack admins." That's a $50/seat-month SaaS the moment Claude Tag goes GA. **Pre-build the customer side of the unfunded wedge from [`02` §3](./02-new-emerging.md#3-anthropic-product).**
- **Insight:** The first products on top of any new Anthropic surface accumulate distribution before competitors get the brief. Claude Tag is two weeks old; you have a four-hour window to be early.

---

## 5. One thing to read: the new June Claude Code best-practices stack {#5-reading}

**Reading menu (~90 min total):**

1. **[MarkTechPost — Claude Code Guide 2026 (25 features + demo)](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/)** — the canonical reference.
2. **[BuildFastWithAI — June 26 AI News](https://www.buildfastwithai.com/blogs/ai-news-today-june-26-2026)** — the 15-story cross-check on the labs section.
3. **[Latent Space — GPT-5.6 release writeup](https://www.latent.space/p/ainews-openai-gpt-56-sol-terra-luna)** — for the swyx/Alessio framing on the limited-preview regime.
4. **[Anthropic Series H announcement](https://www.anthropic.com/news/series-h)** — read primary-source framing once before any application this week.

These four close the gap to the field's current best practices in under 90 minutes.
