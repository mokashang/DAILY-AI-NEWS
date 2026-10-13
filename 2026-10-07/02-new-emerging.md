# New & Emerging — 2026-10-07

New products, startups, funding rounds, and paradigm shifts that matter beyond the labs.

---

## 1. ChatGPT Atlas (Oct 21) — the browser becomes the next OS fight {#1-chatgpt-atlas}

**What happened.** On **Oct 21, 2025**, OpenAI launched **ChatGPT Atlas**, a Chromium-based web browser with ChatGPT embedded as a side-panel assistant and an **agent mode** that executes tasks on-page.

- **macOS first**, free to all users. Windows / iOS / Android are "coming soon."
- **Agent mode** (Plus, Pro, Business tiers only) can complete small tasks on behalf of the user in the browser — click buttons, fill forms, extract data, operate web apps.
- **Browser history as personalization layer** — Atlas remembers which sites you visit and uses that to tailor responses.
- Direct competitors: **Chrome**, **Edge** (both with Gemini / Copilot), **Perplexity Comet**, **The Browser Company's Dia**.

**Sources.**
- [primary] [OpenAI — ChatGPT Atlas launch (openai.com)](https://openai.com/live/) (Oct 21, 2025)
- [secondary] [VentureBeat — OpenAI releases ChatGPT Atlas](https://venturebeat.com/ai/openai-releases-chatgpt-atlas-an-ai-enabled-web-browser-to-challenge-google)
- [secondary] [SCMP — OpenAI launches AI-powered ChatGPT Atlas browser](https://www.scmp.com/tech/big-tech/article/3329867/openai-launches-ai-powered-chatgpt-atlas-browser-challenge-google)
- [analysis] [PureAI — OpenAI Launches ChatGPT Atlas](https://pureai.com/Articles/2025/10/21/OpenAI-Launches-ChatGPT-Atlas.aspx)

**Why it matters to you.**
- **Job.** Browser-agent is **the next tooling-layer surface for FDE / Integration-Engineer roles** — enterprises will want "Atlas inside the firewall" tenancy, SSO + policy, logging + eval. Companies that already sell Chrome extensions become acquisition targets. Watch job titles like "Browser Agent Integration Engineer" by Q1 2026.
- **Startup.** The browser is now **a platform surface, not a shell**. Three near-term wedges: (1) **browser-side eval + policy** (log every agent click; who-did-what for compliance); (2) **persona-switching extensions** (one Atlas, five identities with different memories — HR/engineer/customer-support); (3) **anti-prompt-injection sanitizers** for page content before it hits the agent (ties back to the May 20 prompt-injection thread).
- **Insight.** The real move is **persistent memory across sites**. For the first time, a consumer agent sees your full browsing arc, not isolated chats. That is both the Atlas moat and the next privacy-crisis vector; watch for the first opt-out tooling to appear within 30 days.

`#openai #atlas #browser #agents #comet #dia`

---

## 2. Thinking Machines Lab — Tinker ships, $50B talks open {#2-thinking-machines-tinker}

**What happened.** **Mira Murati's Thinking Machines Lab** had three major moves in the back half of 2025:

- **$2B at $12B** — initial seed round led by **a16z**, with **Nvidia, AMD, Accel, ServiceNow, Cisco, Jane Street** co-investing. One of the largest seed rounds in tech history.
- **Oct 2025 — Tinker launches.** A **managed fine-tuning API** — the first commercial product from the lab. Positioning: "fine-tuning as a service" that keeps the model behind an API rather than requiring data to leave the customer's environment.
- **Nov 2025 — new round at ~$50B reportedly in talks.** Roughly **4× in a quarter**, on **one shipped product**.

**Sources.**
- [secondary] [DealStreet Asia — Thinking Machines valued at $12B](https://media.dealstreetasia.com/stories/thinking-machines-valuation-449378)
- [analysis] [Sacra — Thinking Machines research](https://sacra.com/research/thinking-machines)
- [analysis] [Weishaupt AI — Thinking Machines Raises $2B at $12B](https://weishauptai.substack.com/p/thinking-machines-raises-2b-at-12b)
- [analysis] [Implicator.ai — Mira Murati's Thinking Machines seeks $50B](https://www.implicator.ai/mira-muratis-thinking-machines-seeks-50-billion-it-has-one-api.md)

**Why it matters to you.**
- **Job.** Thinking Machines is now **the OpenAI-alumni gravity well of 2025** — a "pre-IPO lab" that will pull senior ML talent out of OpenAI through 2026. If you want to work on frontier training infra, this is the hiring surface. (As a grad student: track their blog + Twitter for intern + residency hires in Q1.)
- **Startup.** **Fine-tuning-API is officially a category**. Expect fast followers: competitive offerings on OpenAI's platform, Anthropic's roadmap (hinted at in Fall 2025 updates), and from the open-source side (Together / Modal / Replicate / Fireworks). The wedge: whichever fine-tuning product owns **enterprise data-sovereignty + eval loop + prompt-cache + MCP tool integration** will own the mid-market.
- **Insight.** $50B on one product is not a product bet, it's **a talent-and-option-value bet**: investors are betting on Mira + the ex-OpenAI chief-scientist team as a company-level call option on a frontier lab. The signal: **frontier-AI valuations detached from revenue multiples; now priced on talent density + capital-markets access.**

`#thinking-machines #tinker #fine-tuning #funding #a16z`

---

## 3. Perplexity — $18B at +$100M {#3-perplexity-18b}

**What happened.** Perplexity AI, the AI-driven search engine, reached an **$18B valuation** after raising an additional **$100M**. The valuation **tripled in a year**, consolidating Perplexity's position as the fastest-compounding consumer-AI wedge after ChatGPT.

**Sources.**
- [secondary] [IntuitionLabs — latest AI research 2025 (coverage of Perplexity round)](https://intuitionlabs.ai/articles/latest-ai-research-trends-2025)
- [aggregator] [AI Unboxed — AI startups strike investment gold](https://aiunboxed1.beehiiv.com/p/headline-ai-startups-strike-investment-gold)

**Why it matters to you.**
- **Job.** Perplexity's Solutions Engineering team is small but structured; the application lane is less-crowded than Anthropic / OpenAI counterparts. Also check the **Perplexity Enterprise** customer-engineering hires — the kind of role where a well-made MCP server + 2 demo workflows **as a public artifact** gets you a first screen.
- **Startup.** The Perplexity story is now the **"answer-engine attach rate"** case study — their revenue model (Perplexity Enterprise, Pro subscriptions, Comet) demonstrates that **consumer-AI retention is high when the agent reduces time-to-answer**, not when it reduces time-to-draft. If your wedge is "a search / lookup / research assistant," benchmark your retention against Perplexity's.
- **Insight.** Perplexity + ChatGPT Atlas is the first time consumer-AI browsing has **two credible players with billion-dollar-plus distribution**. Chrome is no longer the only default.

`#perplexity #search #comet #consumer #funding`

---

## 4. OpenAI Apps SDK — the first MCP-native app platform {#4-apps-sdk}

**What happened (Oct 6).** As part of DevDay, OpenAI released the **Apps SDK (preview)**, which allows third-party apps to run **inside ChatGPT conversations**. Built on **MCP (Model Context Protocol)**, originally proposed by Anthropic.

Launch partners (non-EU initially): **Booking.com, Canva, Coursera, Expedia, Figma, Spotify, Zillow**.

Access pattern: users can type an app name explicitly ("Spotify, play …") or ChatGPT suggests the app based on context ("Looking at your conversation, want to book this with Expedia?").

**Sources.**
- [primary] [OpenAI Apps SDK preview page](https://openai.com/live/) (Oct 6, 2025)
- [secondary] [Forklog — DevDay 2025 inside ChatGPT](https://forklog.com/en/devday-2025-booking-com-inside-chatgpt-ai-agents-and-trillion-dollar-partnerships/)
- [analysis] [Neurond — Four Key Announcements from DevDay 2025](https://wp-media.neurond.com/?p=6234)

**Why it matters to you.**
- **Job.** Any product-engineer or FDE job involving **"integrating our product with ChatGPT"** will now ask: **do you understand MCP? Have you built an MCP server?** Shipping one MCP server to a public repo this month is a credential-maker.
- **Startup.** The **ChatGPT Apps SDK is a distribution channel**, not just a technical SDK. ChatGPT has hundreds of millions of weekly users; app discovery is routed through conversation. First-mover advantage in any workflow verb (plan a trip, learn a topic, review a design) is real and already slightly spoken for by the launch partners.
- **Insight.** OpenAI's **adoption of MCP** elevates it from "Anthropic standard" to **de-facto industry protocol**. Build on MCP for anything new; the lock-in risk is now near-zero on the protocol layer.

`#openai #apps-sdk #mcp #distribution`

---

## 5. OpenAI × AMD — ~6GW compute deal with ~10% equity warrant {#5-openai-amd}

**What happened.** Also at DevDay (Oct 6): OpenAI and AMD disclosed a multi-year deployment deal for **up to 6 gigawatts of AMD Instinct GPUs**. In return, OpenAI received warrants to acquire **up to ~10% of AMD at $0.01/share**, vesting against deployment and stock-price milestones. **AMD closed +23.7%** on the day.

**Sources.**
- [secondary] [Techmeme live-blog of OpenAI–AMD announcement](https://www.techmeme.com/251006/p21)
- [analysis] [InfoQ — OpenAI DevDay](https://www.infoq.com/news/2025/10/openai-dev-day)

**Why it matters to you.**
- **Job.** Expect **ROCm (AMD's CUDA alternative) skills** to be re-priced upward through 2026 — the fastest-compounding under-known skill right now. If you have time this fall, work through ROCm fundamentals; your MLE / infra-eng résumé will differentiate.
- **Startup.** The infra-startup picture just shifted: **GPU-cloud providers that can serve both Nvidia and AMD** (Together, Lambda, Crusoe, etc.) just gained strategic value. Vertical-AI startups should re-think "Nvidia-first" assumptions in their 24-month runway models.
- **Insight.** Compute-for-equity is now a **standard primitive of frontier-lab financing**, not an exception (Microsoft-OpenAI, Nvidia-CoreWeave, Google-Anthropic were all variants). The lab-to-chipmaker tie-up is becoming as structural as the lab-to-cloud tie-up was in 2023.

`#openai #amd #compute #equity #gpu`
