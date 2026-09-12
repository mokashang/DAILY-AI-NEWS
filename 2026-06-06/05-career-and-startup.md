# Career & Startup — 2026-06-06

Three hiring waves are about to break in the same fortnight. **Anthropic's S-1 filing (June 1)** is the formal *open* of the structured-hiring window — the next 6–9 months are an unusually disciplined apply cycle, the public S-1 (15-day pre-roadshow) will be the highest-fidelity org-by-revenue map you'll get, and the post-S-1 applicant flood arrives in ~2 weeks. **Project Glasswing's partner roster** ([2026-06-06/01 §2](./01-big-lab-moves.md#2-glasswing-self-coding)) is now a literal **150-org direct-apply list** for AI-security-engineering roles. And **WWDC Monday June 8** is the trigger for the iOS-27-Extensions sub-lane inside AI Integration Engineer. *Saturday is for shipping one artifact; Sunday is for applying once.*

Tags: `#career #jobs #anthropic #fde #integration-engineer #solutions-engineer #cyber #glasswing #wwdc #apple #hark #hardware #startups #applications`

---

## 1. Anthropic S-1 filing → apply this weekend, before the post-S-1 application wave {#1-anthropic-hiring}

**The situation:** Anthropic confidentially filed an S-1 on **June 1** ([`01` §1](./01-big-lab-moves.md#1-anthropic-s1)), on the back of a **$65B Series H at $965B post-money** and **~$47B ARR (4.7× YoY)**. The Rule 135 announcement is unusual — it telegraphs the IPO timeline to the public earlier than most filers — which means:

- **The applicant flood hasn't arrived yet, but it's coming.** Tech press will compound the story for ~2 weeks; LinkedIn searches for "Anthropic Solutions Engineer" will spike measurably this month.
- **The post-public-S-1 hiring map is ~3 weeks out** (15 days pre-roadshow + ~1 week of roadshow scheduling). When it lands, you want to be *in process*, not *applying cold*.
- **Anthropic has been growth-hiring for 90+ days** with the **Colossus 1 tenancy + Glasswing partner roster + Tokyo event** all reinforcing the *Solutions/FDE/Integration/Customer Engineering* hiring lanes.

### Do this — apply once this weekend

**Priority order (1 of these = win):**

1. **Anthropic Solutions Engineer** — the senior generalist FDE/Solutions role; the one closest to your ME.md focusing decision.
2. **Anthropic Customer Engineering** — junior-friendly entry into the same org; new-grad-shaped.
3. **Anthropic Applied AI — Mission Programs / Solutions (Health / Education)** — the Gates Foundation work ([2026-05-17/01 §1](../2026-05-17/01-big-lab-moves.md)) is now staffed by a category of roles; less crowded than the standard FDE queue.
4. **Anthropic Glasswing Solutions / Security Mission roles** — the Mythos/Glasswing partner program ([`01` §2](./01-big-lab-moves.md#2-glasswing-self-coding)) implies a hiring lane to staff the *customer-side* of the program; check for "Solutions Engineer — Security" or "Mission Engineer — Critical Infrastructure" titles.

**What to attach (use what you've built):**
- The **dual-model sanitiser / 3-provider router** weekend artifact ([`03` §1](./03-practical-skills-and-tools.md#1-failover-router)) — the README answers orchestration + cost + verification in one repo.
- A **one-line reference to Agent² RL-Bench** ([`04` §1](./04-research-progress.md#1-agent2-rl-bench)) and the *single-agent-beats-multi-agent-at-matched-compute* finding ([`04` §2](./04-research-progress.md#2-single-beats-multi)) — these are the two papers most directly relevant to the work the team is publicly doing.
- A **specific reference to the Karpathy pre-training-automation hire** ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)) — by *function*, not by personality.

### Why it matters to you

- **Job lens:** Three concrete reasons the *Anthropic-stack focusing decision* in ME.md is now stronger, not weaker, than it was 2 weeks ago: (1) **a $965B valuation + $47B ARR + S-1 filed** = the strongest possible evidence the platform you're investing in is durable; (2) **the public-S-1 hiring map** in ~3 weeks will tell you *exactly* which orgs are growing (and which aren't) — for the first time; (3) **the post-IPO equity narrative changes** how Anthropic offers compete with OpenAI offers — RSUs at a public co are priceable in a way private-co equity isn't.
- **Startup lens:** A staged IPO calendar at a frontier lab usually pulls forward **partner-program intensity** — Glasswing-shaped initiatives, Solutions-led co-builds, Solopreneurship-style accelerators — because the prospectus benefits from a visible enterprise-revenue mix. Watch for **new partner programs to ship in the next 30 days**, and if your wedge fits one of them, apply to the *program*, not the role.
- **Insight:** **Apply once, well, with the artifact attached.** The shotgun-applying signal-to-noise is brutal at a lab everyone wants into. One *specific* application with a *specific* artifact attached is worth ~20 generic submits.

→ Cross-link: [`01` §1 Anthropic S-1](./01-big-lab-moves.md#1-anthropic-s1) · [ME.md focusing decision](../ME.md#current-focusing-decision-re-evaluate-monthly) · [APPLICATIONS.md](../APPLICATIONS.md).

---

## 2. The Glasswing partner roster = a direct apply-list of ~12 anchor companies + ~150 partner orgs {#2-glasswing-apply-list}

**The situation:** Glasswing's launch partners include **AWS, Apple, Broadcom, Cisco, CrowdStrike, Google, JPMorganChase, Linux Foundation, Microsoft, NVIDIA, Palo Alto Networks** — all of whom now have a **named, funded, AI-cybersecurity workstream** with a **150-org expansion roster** of customer-side participants. The named expansion partner this round is **Cohesity**.

### Do this — bookmark + filter the apply list (15 min, Sunday)

Add a column to your [APPLICATIONS.md](../APPLICATIONS.md) for **"Glasswing-tagged roles"** — any "AI Security Engineer / AI Vulnerability Analyst / Mythos Integration Engineer / Patch-Pipeline Engineer / AI Security Solutions" role at any of these 12 launch partners. Sub-priority order based on your CS-grad profile + Anthropic-stack focusing decision:

| Priority | Company | Why |
|---|---|---|
| 1 | **JPMorganChase** | Public commitment to AI risk + pre-deployment review; clearest "AI assurance" career path; bank-AI-assurance lane was flagged [2026-05-21/05 §3](../2026-05-21/05-career-and-startup.md#3-eo-lane). |
| 2 | **CrowdStrike** | Most direct fit between "frontier AI agents" and existing detection workflow; will hire fastest into the Mythos-output triage layer. |
| 3 | **Palo Alto Networks** | Similar fit; less crowded than CrowdStrike for new-grad applications. |
| 4 | **Cisco / Linux Foundation** | Infra-side; the patch-pipeline + open-source coordination role. |
| 5 | **AWS / Microsoft / Google / Apple / NVIDIA / Broadcom** | Hyperscaler/platform Glasswing teams; usually the **internal AppSec org**, not the AI org — find the seam between them. |
| 6 | **Cohesity** | Smaller, growing fastest off Glasswing access; less crowded queue. |

**Don't overlook:** the **boutique AI-security startup layer** that will build picks-and-shovels around Glasswing output — see Exaforce ([2026-05-22/02 §2](../2026-05-22/02-new-emerging.md#2-exaforce)) as the archetype. Add a "next round in the AI-SOC / agentic-cyber category" row to WATCHLIST.md if not already there.

### Why it matters to you

- **Job lens:** A 12-company anchor list with active, named, AI-funded security workstreams **is** the apply-list. Filter for "AI Security Engineer / Vulnerability Triage / Patch Pipeline / Mythos Integration" titles weekly. New-grad-friendly variants exist at JPMorgan and the platforms; senior-only at CrowdStrike/Palo Alto.
- **Startup lens:** The 12-company Glasswing roster ≈ the **reference-customer slide** every founder in agentic cyber will pitch with for the next 12 months. If you're building, your TAM is no longer hypothetical — name the partners.
- **Insight:** **Treat published partner rosters as job lists, not press lists.** Every multi-company AI program (Glasswing, the future Apple-Extensions launch partners on Monday, the Tomoro-FDE network at OpenAI Deployment Co) is also a hiring list for the integration roles attached to the program.

→ Cross-link: [`01` §2 Glasswing expansion](./01-big-lab-moves.md#2-glasswing-self-coding) · [2026-05-22/02 §2 Exaforce / agentic-SOC](../2026-05-22/02-new-emerging.md#2-exaforce) · [2026-05-21/05 §3 bank-AI-assurance lane](../2026-05-21/05-career-and-startup.md#3-eo-lane).

---

## 3. Hark + Brett-Adcock pattern: the personal-AI-hardware lane (apply if you bridge ML × hardware) {#3-hark-lane}

**The situation:** Hark's **$700M Series A at $6B post** ([`02` §1](./02-new-emerging.md#1-hark)) is funded with **NVIDIA + AMD + Intel + Qualcomm** all in the syndicate — and it's **pre-product**. That makes the first-50-engineer cohort the most leveraged hiring cohort in any AI startup right now.

### Do this — only if you fit (otherwise: track, don't apply)

**Apply only if at least two of these are true:**
- You have **embedded / on-device-inference / OS / firmware** experience (Coursework + 1 project counts as "experience" at the staffing stage of a pre-product company).
- You have a **multimodal ML project** that runs on constrained compute (the Karpathy `CLAUDE.md` template applied to a vision/voice project counts).
- You're willing to **move to wherever Hark is staffing** (Adcock's prior companies were SF Bay + LA; Hark is likely the same).

If yes: apply to **"Founding ML Engineer / Embedded ML / On-Device Multimodal / Edge Inference"** roles. If no: **track** by adding "Hark first-product ship" to WATCHLIST.md (target: summer 2026 per Adcock's stated roadmap) and re-evaluate after the first hardware reveal.

### Why it matters to you

- **Job lens:** This is the **most ML-skill-tree-shaping career bet of June** for the right candidate. For the rest of us, the right move is to **upskill on the on-device-ML stack** (quantization, distillation, on-device inference engines, the Apple Core ML / Qualcomm Neural Processing SDK / NVIDIA TensorRT layer) **before the demand wave hits**. 12-month bet, not a 4-week bet.
- **Startup lens:** Brett Adcock has now founded **three** capital-intensive hardware-adjacent companies (Figure, Archer, Hark) — that's a **founder pattern** worth studying: same playbook (concentrated founder capital → branded multi-round → silicon-partner syndicate). It's not directly portable to a software founder, but the *partner-syndicate-as-distribution-moat* lesson is.
- **Insight:** The **silicon-vendor syndicate (NVIDIA+AMD+Intel+Qualcomm)** is the loudest signal in the deal. Four direct competitors paid up for optionality on **the same edge-compute target** — that's the chip layer saying "we don't yet know which device wins, but we know the next device exists." Build skills for **the post-phone device layer**, not the phone you've already shipped to.

→ Cross-link: [`02` §1 Hark](./02-new-emerging.md#1-hark) · STARTUPS.md (add personal-AI-hardware wedge row).

---

## 4. WWDC Extensions = an "AI Integration Engineer — iOS 27" sub-lane (expect job posts within 30 days of Monday) {#4-extensions-lane}

**The situation:** Monday's WWDC keynote ([`01` §3](./01-big-lab-moves.md#3-wwdc-extensions)) is expected to launch an **Extensions SDK** that lets Claude, ChatGPT, and Gemini plug into Siri / Writing Tools / Image Playground / etc.

### Do this — Tuesday, after the keynote

1. **Update LinkedIn skills with the *real* on-stage SDK terms** (lesson learned from I/O — [2026-05-20/01 §1](../2026-05-20/01-big-lab-moves.md#1-io-scorecard)). Likely candidates: "App Intents Extensions," "Apple Intelligence SDK," "Siri Extension," "Foundation Model Extension." Wait for the real names.
2. **Add "iOS 27 Extensions integration"** as a search column in your apply list — at Anthropic, OpenAI, Google, *and* at every vertical-SaaS company that will scramble to ship an Extension in Q3.
3. **(Optional) — build one tiny Extension** in the SDK's first developer beta. The Monday-after-WWDC weekend is the highest-EV time-window of the entire summer to be one of the first 100 builders on a new Apple SDK surface.

### Why it matters to you

- **Job lens:** "AI Integration Engineer — iOS 27" did not exist as a category last week and will be a real LinkedIn search term by July. Be among the first 100 LinkedIn profiles to have it listed in skills.
- **Startup lens:** Two Extension-shaped wedges from [`02` §3](./02-new-emerging.md#3-ios-extensions): the **context-bridge Extension** and the **per-vendor cost-router Extension**. Either is a weekend build with a real shot at App Store featuring.
- **Insight:** The **fastest career lane growth comes from being in the first cohort of people who learn a new SDK well enough to be hireable on it before recruiters have a screen for it.** Apple SDKs have a clean track record of producing this dynamic; the iOS 27 Extensions surface is the next one.

→ Cross-link: [`01` §3 WWDC preview](./01-big-lab-moves.md#3-wwdc-extensions) · [`02` §3 Extensions as a distribution surface](./02-new-emerging.md#3-ios-extensions) · [`03` §3 WWDC live-monitoring discipline](./03-practical-skills-and-tools.md#3-wwdc-discipline).

---

## 5. The Saturday artifact — one repo, three interview answers {#5-saturday-artifact}

**Ship today / tomorrow:** the **3-provider failover router + per-request cost log** described in [`03` §1](./03-practical-skills-and-tools.md#1-failover-router). One repo. One README. One demo gif.

The README must answer three questions in three paragraphs:

1. **Provider outage handling** — failover policy + the June 5 Claude outage as the worked motivation.
2. **Cost control** — per-request cost-per-model row and a monthly rollup.
3. **Routing decision** — the rule + the observed mix on a real-traffic day.

Then **link the repo in the [§1](#1-anthropic-hiring) Anthropic application this weekend**, in your LinkedIn featured section, and at the top of [APPLICATIONS.md](../APPLICATIONS.md) as the **"this is the artifact I'm attaching to FDE applications this month"** entry.

**One artifact a weekend. Cadence > intensity.** ([ME.md personal rules](../ME.md#personal-rules))
