# Big Lab Moves — 2026-05-09

Strategy, products, policy, and power moves from the labs and companies shaping AI.

---

## 1. Anthropic Rents the Entire Colossus 1 Data Center from xAI/SpaceX — 220,000 GPUs, 300 MW

**What happened:** On May 6, Anthropic and SpaceX announced a partnership in which Anthropic gets **all of the compute capacity at Colossus 1**, the Memphis data center built by Elon Musk's xAI. The deal hands Anthropic access to **over 220,000 NVIDIA GPUs (H100/H200/GB200)** and **more than 300 megawatts of new capacity** within the month. Anthropic also publicly "expressed interest" in working with SpaceX to develop **multi-gigawatt orbital data centers**.

The deal is doing two things at once:
- **Solving a real bottleneck:** Dario Amodei said on May 8 that Anthropic's revenue and usage grew **80-fold in a single quarter on an annualized basis**, calling it "just crazy" and "too hard to handle." Demand was outstripping capacity even after the $200B Google TPU commitment.
- **Doubling Claude Code 5-hour rate limits** for Pro, Max, Team, and Enterprise customers within a month, killing peak-time throttling for Pro/Max accounts, and increasing API limits on Opus models.

The political subtext is louder than the technical one. Musk publicly backed the deal: "No one set off my evil detector." Anthropic — which sued the Trump administration over Pentagon access (see story #4) — is now a customer of Musk's infrastructure company. Strange bedfellows.

**Sources:**
- [Anthropic — Higher usage limits for Claude and a compute deal with SpaceX](https://www.anthropic.com/news/higher-limits-spacex)
- [xAI — New Compute Partnership with Anthropic](https://x.ai/news/anthropic-compute-partnership)
- [CNBC — Anthropic, SpaceX announce compute deal](https://www.cnbc.com/2026/05/06/anthropic-spacex-data-center-capacity.html)
- [Tom's Hardware — SpaceX rents 220K GPUs to Anthropic](https://www.tomshardware.com/tech-industry/artificial-intelligence/musks-spacex-has-rented-out-access-to-its-supercomputers-220-000-nvidia-gpus-and-300-megawatts-of-ai-compute-power-to-rival-anthropic-musk-says-no-one-set-off-my-evil-detector-antrhropic-also-interested-in-orbital-data-centers)
- [The Decoder — Anthropic taps Colossus-1 for 220K GPUs](https://the-decoder.com/anthropic-taps-spacexs-colossus-1-data-center-for-220000-gpus-to-power-claude/)
- [Simon Willison — Notes on the xAI/Anthropic deal](https://simonwillison.net/2026/May/7/xai-anthropic/)
- [Fortune — Anthropic 80-fold quarterly growth](https://fortune.com/2026/05/08/anthropic-80fold-growth-quarter-renting-elon-musk-data-center/)

**Why it matters to you:**
- **Job lens:** "Anthropic capacity unlock" means more Claude API requests will go through, which means **more enterprise products built on Claude that need engineers**. Watch for hiring at companies that were API-rate-limit-bound (Cursor, Windsurf, Cognition, Sierra, every vertical agent startup). Their engineering teams just got unblocked and will scale.
- **Startup lens:** If Anthropic was your bottleneck, it isn't anymore — but neither is it for your competitors. The unlock is symmetric. The advantage shifts back to **whoever has the best workflow-specific data, UX, and distribution**, not whoever could squeeze the most tokens out of the rate limit.
- **Insight:** The "neutral cloud" era is officially over. Anthropic is now financially entangled with **Google ($200B + equity), AWS ($100B+), and SpaceX (Colossus 1)** simultaneously. This isn't multi-cloud — it's "every cloud is a partner because no single one has enough power." Compute is now allocated like wartime materiel: by political relationships, not market price.

---

## 2. OpenAI Ships GPT-5.5-Cyber to Vetted Defenders — 81.9% on CyberGym

**What happened:** OpenAI announced **GPT-5.5-Cyber** on May 7–8 as part of its **Trusted Access for Cyber** program. It's a fine-tune of GPT-5.5 with **fewer guardrails** in the cybersecurity domain, available in limited preview to vetted defenders responsible for critical infrastructure.

What it can do that base GPT-5.5 won't:
- Generate **vulnerability exploitation plans** and validate them by launching simulated attacks against systems being studied
- Write **proofs of concept for discovered bugs**
- **Reverse engineer malware** without refusal patterns
- Run automated red team exercises end-to-end

Numbers:
- **81.9% on CyberGym** (1,500+ historical vulnerabilities across hundreds of OSS projects)
- Reaches "the highest tier of OpenAI's Trusted Access for Cyber"
- All Trusted Access individuals must enable **Advanced Account Security** by June 1, 2026

The release is a direct response to Anthropic's Claude Mythos preview, which OpenAI's GPT-5.5 mainline followed by cracking a 32-step end-to-end cyber-attack range three weeks after Mythos did.

**Sources:**
- [OpenAI — Scaling Trusted Access for Cyber with GPT-5.5 and GPT-5.5-Cyber](https://openai.com/index/gpt-5-5-with-trusted-access-for-cyber/)
- [Axios — OpenAI makes GPT-5.5 more widely available to cyber defenders](https://www.axios.com/2026/05/07/openai-gpt-55-cybersecurity-model)
- [Help Net Security — GPT-5.5-Cyber for permissive security workflows](https://www.helpnetsecurity.com/2026/05/08/openai-gpt-5-5-cyber-model/)
- [CNBC — OpenAI rolls out GPT-5.5-Cyber to vetted teams](https://www.cnbc.com/2026/05/07/openai-rolls-out-new-gpt-5point5-cyber-to-vetted-cybersecurity-teams.html)
- [SiliconANGLE — GPT-5.5-Cyber for high-impact security research](https://siliconangle.com/2026/05/08/openai-introduces-gpt%E2%80%915-5%E2%80%91cyber-high-impact-cybersecurity-research/)
- [UK AISI — Evaluation of GPT-5.5 cyber capabilities](https://www.aisi.gov.uk/blog/our-evaluation-of-openais-gpt-5-5-cyber-capabilities)

**Why it matters to you:**
- **Job lens:** "AI security engineer" is now a tier-1 role at every major bank, hospital network, and cloud provider. Both major labs (Anthropic Mythos, OpenAI GPT-5.5-Cyber) ship gated cyber models — that means **someone has to be the human in the loop**. If you have any background in CTF, vulnerability research, or red-teaming, pair it with prompt engineering and you have a unique resume. Security-cleared candidates are gold.
- **Startup lens:** The defensive opportunity is **"AI tooling for the SOC analyst"** — the model alone is not the product. The product is the workflow harness around it: case management, evidence chain-of-custody, audit logs, integration with SIEM/SOAR. Pick a vertical (hospitals, mid-market manufacturing, K-12 districts) where the existing security vendors are 10 years behind. Build the harness, license the model from OpenAI/Anthropic.
- **Insight:** Both labs are converging on the same gating model: **frontier capability is gated behind identity verification and audit logs**, not behind RLHF refusals. This is the future of all dual-use AI capabilities — biology, chemistry, finance, weapons. Refusals are training-time; gating is account-time. Plan accordingly.

---

## 3. Anthropic Code w/ Claude 2026 — Managed Agents, "Dreaming," and the Finance Templates Drop

**What happened:** Anthropic ran its **Code w/ Claude 2026** developer conference on May 6, headlined by three new Claude Managed Agents capabilities and ten production-ready finance agent templates.

The three new Managed Agents features:
1. **Multi-agent orchestration** — break down complex tasks across a fleet, with a lead agent assigning sub-tasks
2. **Outcomes** — declare what success looks like; Claude iterates against the criteria. Early tests show **+10 points** on task success vs. plain prompting
3. **"Dreaming"** — Claude reviews previous sessions overnight, identifies what it missed, writes plain-text learnings and structured "playbooks" for future sessions to reference. Harvey (early adopter) reported **~6× higher task completion rates** after enabling

Plus **ten ready-to-run financial-services agent templates** shipped as plugins in Claude Cowork and Claude Code, and as cookbooks for Managed Agents — extending the Wall Street push from May 5.

**Sources:**
- [Simon Willison — Live blog: Code w/ Claude 2026](https://simonwillison.net/2026/May/6/code-w-claude-2026/)
- [9to5Mac — Anthropic updates Claude Managed Agents with three new features](https://9to5mac.com/2026/05/07/anthropic-updates-claude-managed-agents-with-three-new-features/)
- [SiliconANGLE — Anthropic's "dreaming" Claude agents](https://siliconangle.com/2026/05/06/anthropic-letting-claude-agents-dream-dont-sleep-job/)
- [VentureBeat — Anthropic introduces "dreaming"](https://venturebeat.com/technology/anthropic-introduces-dreaming-a-system-that-lets-ai-agents-learn-from-their-own-mistakes)
- [Every — Inside Anthropic's 2026 Developer Conference](https://every.to/chain-of-thought/inside-anthropic-s-2026-developer-conference)
- [The Register — Anthropic unleashes finance agents](https://www.theregister.com/software/2026/05/05/anthropic-unleashes-finance-agents-for-claude/5225868)
- [Claude Managed Agents docs](https://platform.claude.com/docs/en/managed-agents/overview)

**Why it matters to you:**
- **Job lens:** The "Dreaming" feature is interesting because it's **continual learning without retraining** — agents persist learnings as text artifacts. Production ML teams will need engineers who can design, evaluate, and audit these playbook caches. New role: **"agent memory engineer"** — the person who decides what gets written to long-term memory, how playbooks are versioned, and how to roll one back when it goes wrong.
- **Startup lens:** Anthropic shipping ten finance templates is them locking in the top of the pyramid. **Don't compete with templates — compete with workflows.** A template is "here's how to summarize a 10-K." A workflow is "here's how a junior analyst at a $5B credit fund moves a deal from intake to investment committee, and the agent owns 60% of it." Templates are commodities; workflows are moats.
- **Insight:** Outcomes-based prompting (declare success criteria; let the model iterate) is going to absorb a huge chunk of "prompt engineering." If you can write a clean **eval**, you can write a clean Managed Agent. **Eval-design is the new prompt engineering.** Whoever can specify task success precisely and measurably beats whoever has the cleverer system prompt.

---

## 4. Pentagon Picks Eight AI Vendors — Anthropic Stays Frozen Out

**What happened:** The Pentagon finalized AI agreements with **OpenAI, Google, Microsoft, Amazon, Oracle, NVIDIA, SpaceX, and Reflection AI** for use in classified networks (analysis, logistics, large-scale data processing). **Anthropic was excluded** — the Pentagon labeled it a "supply chain risk," a designation previously reserved for companies tied to foreign adversaries.

The dispute is about terms of use:
- The eight vendors agreed their tools can be used for "any purpose the military deems lawful" — including autonomous weapons and mass surveillance
- Anthropic refused, citing concerns about **domestic mass surveillance and fully autonomous lethal weapons**
- Trump publicly announced he was severing ties with Anthropic over this
- Anthropic sued; a federal judge in California **blocked** the government's effort last month
- Anthropic's Mythos cybersecurity model has reportedly made the Pentagon reconsider, but the formal exclusion stands

A Pentagon official quoted in Government Executive: **"We will never again rely on a single AI provider."** Translation: the multi-vendor framework is a structural hedge — and a leverage point — against any one lab's safety policies blocking use cases.

**Sources:**
- [CNN Business — Pentagon strikes deals with 8 Big Tech companies](https://www.cnn.com/2026/05/01/tech/pentagon-ai-anthropic)
- [Government Executive — Pentagon will "never again" rely on single AI provider](https://www.govexec.com/technology/2026/05/pentagon-will-never-again-rely-single-ai-provider-official-says/413432/)
- [gHacks — Pentagon signs deals with 8 AI firms, cuts out Anthropic](https://www.ghacks.net/2026/05/04/pentagon-signs-ai-deals-with-openai-google-microsoft-nvidia-and-others-cutting-out-anthropic/)
- [Orbital Today — 8 AI companies win Pentagon classified contracts](https://orbitaltoday.com/2026/05/03/8-ai-companies-win-pentagon-classified-contracts-while-anthropic-remains-blacklisted/)
- [Let's Data Science — Pentagon signs eight AI companies, excludes Anthropic](https://letsdatascience.com/blog/pentagon-signs-eight-ai-companies-anthropic-excluded)

**Why it matters to you:**
- **Job lens:** Reflection AI being on this list is the surprise — a relatively young startup is now a federal classified-network vendor. **Defense AI is no longer the domain of just Palantir/Anduril/Scale.** If you're early career, the path of least resistance is: get clearance → join Reflection AI / Anduril / SAIC → ship something for DoD → 3 years later you're either a manager at the same place or a defense-tech founder.
- **Startup lens:** "Defense-tech infrastructure for AI deployment" is wide open. Reflection AI cracked the door because they'll sign the broad lawful-use clause. If your moral framework is compatible with that, the SBIR/AFWERX path is faster than you think — but understand what you're agreeing to.
- **Insight:** Anthropic's exclusion is the clearest demonstration yet that **safety-first positioning has a real cost**. Anthropic estimates that cost is acceptable because finance, biotech, and consumer don't care. But every founder choosing safety constraints should recognize: **constraints on use cases are constraints on customer base**. Pick deliberately, not by default.

---

## 5. Quick Scorecard: Lab Power Moves This Week (May 5–9)

| Lab | This Week's Headline | Strategic Read |
|---|---|---|
| **Anthropic** | Colossus 1 SpaceX deal + 80× quarterly growth + Code w/ Claude conf + finance templates | Solving the capacity crisis while doubling down on enterprise verticals — premium positioning, premium problems |
| **OpenAI** | GPT-5.5-Cyber preview + Trusted Access tier | Capturing the security/critical-infra vertical with a permissive-mode model — gating by identity, not refusal |
| **Google** | $200B Anthropic compute commitment locked in + CAISI | Selling shovels (TPUs) to every miner — best risk-adjusted position in the entire stack |
| **Meta** | Quiet — Muse Spark closed-source still digesting | Lost the open-weights narrative; needs a Llama-equivalent or open-source Muse to recover developer trust |
| **xAI / SpaceX** | Renting Colossus to Anthropic | Becoming a *neutral* compute supplier — Musk-as-landlord is more valuable than Musk-as-frontier-lab |
| **Reflection AI** | Pentagon classified contract | Quietly became one of 8 federally cleared frontier-AI vendors — outsized leverage for a Series B-stage startup |

**Macro pattern of the week:** **Compute is being re-allocated by relationship, not by market.** Anthropic's $200B Google deal, $100B+ AWS deal, and now 100% of Colossus 1 — three "exclusive" supplier relationships running in parallel. The labs that win the next 24 months will be the ones who can simultaneously hold contradictory partnerships without anyone walking away.
