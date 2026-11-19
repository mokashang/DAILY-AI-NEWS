# Big Lab Moves — 2026-07-29 (Wednesday)

The frontier's biggest single day this month sits inside cryptography, not inside a model release. Anthropic pushed Mythos out of preview, Google confirmed a monthly release cadence to compensate for a delayed Gemini 3.5 Pro, Musk pre-announced a 4.6 → 4.7 Grok roll in five weeks, and MCP 2026-07-28 became a shipped spec instead of a countdown. Amazon is still gone from the frontier list ([2026-07-25 §3](../2026-07-25/01-big-lab-moves.md#3-amazon-agi-lab)); no one filled the seat.

---

## 1. Mythos: Anthropic broke a NIST post-quantum finalist in 60 hours {#1-mythos-hawk}

**What happened.** Anthropic published cryptanalysis results from **Claude Mythos Preview** — the internal red-team frontier model spun out of the Red Team Blog (referenced [2026-07-25 §1](../2026-07-25/01-big-lab-moves.md)). Two headline claims, both dated 2026-07-28 → 07-29:

1. **HAWK-256 structural weakness.** Mythos found a nontrivial automorphism in HAWK's underlying lattice that enables a faster key-enumeration attack, cutting expected key-recovery cost from **~2⁶⁴ → ~2³⁸ operations**. HAWK is a NIST PQC third-round candidate; it had passed **two full years** of expert human cryptanalytic review without this being surfaced. Mythos got there in **≈60 hours** of largely autonomous work. `[primary]`
2. **7-round AES-128 speedup.** An improved meet-in-the-middle attack running **200–800× faster** than prior best-known, consuming ≈**1 billion output tokens** across ~3 days. Applies to 7 of AES-128's 10 rounds and still requires an impractical number of chosen plaintexts — **no production system is at risk today.** `[primary]`

**Sources.** [Anthropic — "Cracks in HAWK and 7-round AES" (via Hacker News)](https://thehackernews.com/2026/07/claude-ai-just-cracked-post-quantum.html) `[secondary]` · [Dataconomy 07-29 write-up](https://dataconomy.com/2026/07/29/anthropic-ai-flaws-hawk-aes/) `[secondary]` · [Decrypt 07-29](https://decrypt.co/374600/claude-mythos-cracked-post-quantum-cryptography) `[secondary]` · [FourWeekMBA analysis (compute-as-line-item framing)](https://fourweekmba.com/ai-anthropic-claude-mythos-hawk-cryptanalysis-compute/) `[analysis]` · [Trending Topics EU](https://www.trendingtopics.eu/anthropics-mythos-model-finds-flaws-in-strong-encryption-algorithms/) `[secondary]`

**Why it matters.**
- **The eval question just shifted.** Two years of human review vs. 60 hours of Mythos is not a scaling story — it's an **economic** one. Cryptanalysis, previously "one team of PhDs for two years," is now a **compute line item**. Any lab that can rent Mythos-tier compute owns a discovery capability that used to be state-actor-only.
- **NIST PQC standardization gets a new stress test.** HAWK survives (attack still ≥2³⁸, and HAWK isn't a finalist selection — it's a Round 3 candidate); but every remaining candidate will now be re-evaluated with LLM-driven cryptanalysis as a first-class threat model.
- **Anthropic's "responsible disclosure" playbook is now the reference.** The scheme's designers got the vulnerability first; the write-up came after. This is the closest analog we have to what "AI-discovered zero-day disclosure" looks like at frontier scale.

**Insight.** The Anthropic Red Team was set up so that when Mythos-class capabilities arrived, the disclosure workflow already existed. Notice the shape of the org: capabilities and disclosure grew *together*. That's the transferable pattern for anyone building agentic products — instrument the harm-discovery loop **before** the capability lands, not after.

**Job · Startup · Insight.**
- **Job.** If you're targeting Anthropic (Alignment / Red Team / Frontier Safety), this is your interview cover story: read the write-up, be able to speak to *why HAWK-256's automorphism was missed* (compressed group action, symmetry Anthropic's model detected via representation-theoretic hints), and what an eval that catches this class of bug looks like. Interviewers will ask.
- **Startup.** "AI-native cryptanalysis-as-a-service" is now a real category — enterprises with proprietary crypto will pay for a Mythos-shaped assurance pass. Adjacent: **assurance tooling** for post-quantum migration audits — TAM opens up as CISOs realize their crypto agility plans just aged by a decade.
- **Insight.** The economic reframe is the real story. Any research task that was "prohibitively expensive PhD-time" is now bounded by **$ per billion output tokens**. Make your list of those tasks; go find the ones with willing buyers.

`#anthropic #mythos #cryptanalysis #post-quantum #hawk #aes #red-team`

---

## 2. MCP 2026-07-28 shipped on schedule {#2-mcp-shipped}

**What happened.** The **2026-07-28 spec is now a release, not a countdown**. Highlights:

- **Stateless core.** Session handshake removed; connections are request/response. Remote MCP servers deploy behind a plain round-robin load balancer.
- **OAuth 2.1 + OIDC** as first-class auth (Entra, Okta, Auth0 without shims).
- **MCP Apps + Tasks** promoted to a **versioned extensions framework** (interactive UIs + long-running work now have a canonical path).
- **Mcp-Method / Mcp-Name headers** for LB-friendly routing.
- **Adoption context:** MCP crossed **400M monthly SDK downloads**, 4× YoY.

**Sources.** [modelcontextprotocol.io — 2026-07-28 Specification](https://blog.modelcontextprotocol.io/posts/2026-07-28/) `[primary]` · [Anthropic — "Bringing MCP 2026-07-28 to Claude"](https://claude.com/blog/bringing-mcp-2026-07-28-to-claude) `[primary]` · [Metaverse Post](https://mpost.io/anthropic-releases-largest-mcp-update-yet-moving-protocol-to-stateless-core-for-enterprise-scale/) `[secondary]` · [Explainx.ai deep-dive](https://explainx.ai/blog/mcp-2026-07-28-stateless-spec-july-2026) `[analysis]` · [Nerd Level Tech breakdown](https://nerdleveltech.com/mcp-stateless-protocol-enterprise-authorization) `[analysis]`

**Why it matters.** [2026-07-25 §4](../2026-07-25/01-big-lab-moves.md) called this the "biggest platform migration of the summer." It arrived on schedule, and the ecosystem's Tuesday was surprisingly quiet — most large integrations had already migrated on the release candidate ([RC post](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/)). Meaning: the **window for landing a "migrated in the first 48 hours" GitHub star badge is already narrowing**. See `03` §2 for the tactical migration playbook and `05` §4 for the labor-market implication.

**Job · Startup · Insight.**
- **Job.** Any MCP server you list on your résumé should now say `spec: 2026-07-28`. Any older one is a downgrade signal.
- **Startup.** Managed MCP hosting ("Vercel for MCP servers") just got materially easier — stateless means edge/serverless is the default deploy target. There's still no dominant player.
- **Insight.** Protocols rarely make it out of "spec season" without a hidden compatibility gotcha. Watch [modelcontextprotocol.io](https://blog.modelcontextprotocol.io/) for the first week's errata — that's where your migration bug is going to come from.

`#mcp #stateless #protocol #oauth #anthropic`

---

## 3. Grok 4.6 → 4.7 in five weeks: Musk's release-cadence flex {#3-grok-cadence}

**What happened.** On 2026-07-28 Musk pre-announced:
- **Grok 4.6** ≈ August 7 — **1.5T parameters**, SFT + RL improvements over 4.5.
- **Grok 4.7** ≈ late August / early September — **2.1T parameters**, "better in every way except slightly slower to serve, with even better token efficiency."

**Sources.** [Roic News — 07-28](https://www.roic.ai/news/musk-signals-rapid-grok-rollout-46-in-two-weeks-47-a-month-later-07-28-2026) `[secondary]` · [American Bazaar — 07-28](https://americanbazaaronline.com/2026/07/28/elon-musk-says-grok-4-6-is-weeks-away-grok-4-7-to-follow-soon-485356/) `[secondary]` · [xAI Newsroom](https://x.ai/news) `[primary]`

**Why it matters.** xAI is doing what OpenAI stopped doing: **public roadmap flexing**. Two model tiers pre-announced weeks in advance, parameter counts disclosed. That's a talent-market move — xAI is showing frontier researchers "we ship faster, and we tell you what we're building." Whether the eval numbers back the parameter counts is a separate question — 4.5 landed below what public expectations set. Trust-but-verify on the Aug 7 checkpoints.

**Insight.** Model size disclosed publicly is now a **recruiting signal**, not a marketing spec. Anthropic and OpenAI stopped publishing param counts years ago and it never hurt them; Musk needs the signal precisely *because* xAI's mindshare is behind the eval-topping labs.

**Job · Startup · Insight.**
- **Job.** If your résumé mentions any xAI/Grok integration, refresh it against 4.6 the day it lands — the "already working with the newest model" data point matters for FDE/AI-Eng interviews.
- **Startup.** Grok's API pricing has been the most volatile of the frontier — do not build a product whose gross-margin math relies on Grok pricing holding for 12 months.
- **Insight.** The relevant race in xAI's cadence is not vs. Anthropic — it's vs. **Meta's Muse Spark** ([2026-05 back-catalog](../2026-05-22/) + 07-04 financials). Two labs are trying to buy talent through velocity; only one has the compute contract to back it up.

`#xai #grok #cadence #musk #recruiting`

---

## 4. Google DeepMind: monthly cadence promised; Gemini 4 in pre-training; morale as the drag {#4-google-deepmind}

**What happened.** Sundar Pichai on 2026-07-21 confirmed:
- **Gemini 4 is in pre-training** — "our most ambitious pre-training run yet," "significantly larger" than 3.x.
- Google will move to **"almost monthly" Gemini releases** going forward.
- **Gemini 3.6 Flash, 3.5 Flash-Lite, 3.5 Flash Cyber** shipped 07-21. 3.6 Flash cuts token usage ≈17% at same quality.

**But:** [Axios](https://www.axios.com/2026/07/23/googles-deep-mind-ai-model-race) and [The Agent Report](https://the-agent-report.com/2026/07/google-gemini-3-5-pro-delayed-july-2026/) confirmed that **Gemini 3.5 Pro's delay to July 17** (from a spring target) is being driven by employee frustration and a talent exodus — reportedly costing **~$225B of Alphabet market cap** since. On 07-24 Google **shut down the AlphaFold team** ([Engadget](https://www.engadget.com/2225849/google-shuts-down-alphafold/)); the surviving talent has been folded into the Gemini org.

**Sources.** [DeepMind blog](https://deepmind.google/blog/) `[primary]` · [TechCrunch — Google releases three new Gemini models](https://techcrunch.com/2026/07/21/google-releases-three-new-gemini-models-but-no-3-5-pro/) `[secondary]` · [Axios — morale drag](https://www.axios.com/2026/07/23/googles-deep-mind-ai-model-race) `[secondary]` · [The Agent Report — talent exodus](https://the-agent-report.com/2026/07/google-gemini-3-5-pro-delayed-july-2026/) `[analysis]`

**Why it matters.** The **three-lab market from 2026-07-25 (Anthropic + OpenAI + Google)** now has an asterisk on the Google leg. Frontier consolidation and internal execution risk are pulling in different directions. Monthly cadence is a promise; the exodus is a fact. If you're targeting DeepMind as a job destination, discount the "hardest place to get into" premium accordingly — hiring urgency is up.

**Job · Startup · Insight.**
- **Job.** DeepMind Early Career and Google PhD Early Career AI/ML listings are quietly the softest they've been in 24 months. Apply if you're on the fence.
- **Startup.** AlphaFold's dissolution creates a **structural-biology / drug-discovery talent liquidity event.** Founders in bio-AI: this is your recruiting window.
- **Insight.** Watch the *first* month of the promised monthly cadence. If August ships nothing new, the whole plan gets re-underwritten.

`#google #deepmind #gemini #alphafold #hiring`

---

## 5. Claude "share chat" leak → Anthropic patched by 07-28 {#5-share-leak}

**What happened.** 2026-07-25, Reddit users noticed `site:claude.ai/share` surfaces on Google contained **resumes, health records, patient names and phone numbers, financial spreadsheets, and internal company documents**. Root cause: Claude's shared-link pages lacked `noindex` HTML tags / HTTP headers. Anthropic updated `robots.txt` and other measures; results were wiped from Google by 2026-07-28. Anthropic's public line: **shared links are public by design; users should audit and unpublish.**

**Sources.** [TechCrunch — PSA](https://techcrunch.com/2026/07/27/psa-your-claude-shared-chats-and-artifacts-may-have-ended-up-on-google/) `[secondary]` · [Fortune coverage](https://fortune.com/2026/07/27/a-trove-of-users-seemingly-private-conversations-with-anthropics-claude-ai-chatbot-showed-up-in-google-search-results/) `[secondary]` · [404 Media](https://www.404media.co/tons-of-peoples-claude-chats-and-creations-are-exposed-on-google/) `[secondary]` · [Neowin](https://www.neowin.net/news/your-claude-conversations-may-have-leaked-online-if-you-did-this/) `[secondary]`

**Why it matters.** In one week Anthropic went from "trust us with your enterprise data" (see FDE growth) to "check your share links." Enterprise deals get re-underwritten every time a story like this lands — expect procurement questions on artifact-share hygiene for the next 90 days. **This is also the story you cite in interviews when asked about "responsible AI product engineering"** — it's the counter-example: a small default (no `noindex`) becomes a headline in the same week you shipped Opus 5.

**Insight.** Every public-by-URL surface is one crawler discovery away from a headline. The fix is one HTTP header. Do the audit *before* the incident, not after.

**Job · Startup · Insight.**
- **Job.** In your Anthropic FDE application (`05` §2), name this incident specifically and describe how you'd redesign the share flow (opt-in "make public," randomized long URLs are not sufficient without `noindex`).
- **Startup.** "Enterprise Claude/GPT link hygiene scanner" is a real 6-month wedge for anyone building governance tools.
- **Insight.** Robots.txt is not a security boundary. Treat every publicly reachable URL as public and secure it accordingly.

`#anthropic #security #privacy #enterprise-trust`
