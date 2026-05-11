# Practical Skills & Tools — 2026-05-11

Hands-on workflows, tools, prompting, productivity. Act on this TODAY.

Tags: `#tools #workflows #prompting #automation #productivity`

---

## ⭐ One Thing to DO This Week

**Install Karpathy's `autoresearch`, point it at a real problem, let it run overnight.**

- Pick one open question you actually care about: "Does X technique improve Y benchmark?" / "Which prompt format works best for Z task?" / "Which open model is cheapest at 90% quality on my benchmark?"
- Let it run 100 experiments overnight while you sleep
- Write up: *what it found, what it missed, where you intervened, what surprised you*
- Push the writeup to GitHub. **This becomes the single best resume bullet of 2026.**

Recruiters at every AI-native company are listening for: "shipped an agent that ran X overnight experiments, found Y, saved Z hours of my time." It's the cleanest signal you have AGI-curiosity *and* shipping discipline. Two days of effort → permanent resume asset.

---

## 1. Karpathy's `autoresearch` — The 630-LOC Tool That Just Defined a Workflow {#1-karpathy-autoresearch}

**What happened:** Andrej Karpathy open-sourced `autoresearch` — a **630-line tool** that lets an AI agent run ~100 ML experiments while you sleep. The tool:
- Takes a research question as a prompt
- Generates an experiment plan
- Implements each variant in a fresh isolated environment
- Runs them in parallel on rented GPUs
- Aggregates results into a comparative report

The viral moment: **Shopify's CEO Tobi Lütke ran it on a recommendation-system improvement, achieving a 19% lift on the first pass.** Karpathy's framing: *"This is what 'vibe coding' becomes when you give the agent compute and time. It is not generating one solution — it is exploring a hundred."*

This is the cleanest expression of a thesis several people have been circling for a year: **the best AI workflow is not 'human in the loop' — it is 'human kicks off the loop and reads the report.'**

**Sources:**
- [Get CO/AI — Mollick/Karpathy and the autoresearch tool](https://getcoai.com/news-letter/ethan-mollick-karpathy-bots-jobs/)
- [Karpathy on X (search "@karpathy autoresearch")](https://x.com/karpathy)
- [Simon Willison — ai-assisted-programming tag](https://simonwillison.net/tags/ai-assisted-programming/)

**Why it matters to you:**
- **Job lens:** Showing that you've used `autoresearch` (or built a similar pattern) is the **single most differentiated thing on a 2026 new-grad resume**. Every CS grad has done a coding bootcamp project. Maybe 1 in 100 has shipped an agentic experiment system. That ratio is the gap.
- **Startup lens:** The tool itself is a wedge for a productized version: "autoresearch as a service" for non-engineering domains. Marketing teams running 100 ad variants overnight. Quant funds backtesting 100 hypotheses. Drug discovery teams. **The pattern generalizes** — be the team that productizes it for one vertical.
- **Insight:** The reason this works is that **iteration is cheap and patience is rare**. An agent has infinite patience. You get a year's worth of compounding insights in one night. The constraint becomes *picking the right question*, not *executing the test.* This is a permanent change to how research and product development gets done.

---

## 2. Ethan Mollick's "Which AI to Use Right Now" — Updated Guide (May 2026)

**What happened:** Ethan Mollick released his 8th iteration of *An Opinionated Guide to Using AI Right Now*, and it represents a meaningful break from prior versions. Headlines:

- **"Using AI" no longer means typing into a chatbox.** It means delegating tasks to an agent that uses tools as appropriate. The chat-prompt era is closing.
- **His recommended model picks for May 2026:**
  - **Highest reasoning:** Claude Opus 4.7 (Max mode) or GPT-5.5 (xhigh)
  - **Best coding agent:** Gemini 3.1 Pro (head-to-head best in coding-arena)
  - **Best math:** GPT-5 (perfect AIME 2026)
  - **Best for everyday "just answer this":** Claude Sonnet 4.6 or Gemini 3.1 Flash
  - **Best free option:** Gemini 3.1 Flash-Lite or Qwen3.5 (locally hostable)
- **His workflow recommendation:** Use Claude Code or Codex for any task that involves files. Use Claude Mythos or ChatGPT Agent Mode for any task that involves browser actions. Use a Realtime voice model for any task that involves talking. The chat window is now your *outline tool*, not your *execution tool*.

**Sources:**
- [One Useful Thing — Using AI Right Now: A Quick Guide](https://www.oneusefulthing.org/p/using-ai-right-now-a-quick-guide)
- [One Useful Thing — An Opinionated Guide to Using AI Right Now](https://www.oneusefulthing.org/p/an-opinionated-guide-to-using-ai)
- [One Useful Thing — A Guide to Which AI to Use in the Agentic Era](https://www.oneusefulthing.org/p/a-guide-to-which-ai-to-use-in-the)
- [Valence — Mollick on AI agents and the future of work](https://www.valence.co/ai-and-the-workforce/ai-agents-agentic-work-the-future-of-work-ethan-mollick)

**Why it matters to you:**
- **Job lens:** Your interview will increasingly include "show me your tool-use stack." Memorize Mollick's matrix and customize it with one specific anecdote per row ("I used Gemini 3.1 Pro for coding because…"). This signals deliberate practice, not just consumption.
- **Startup lens:** The agentic shift means **multi-model orchestration is no longer optional**. Build your product with LiteLLM or OpenRouter as your inference router from day one. Allow your customers to pick the model they trust. **Never become a single-model wrapper.**
- **Insight:** The chat-window era is closing. The interface of 2026 is *file system + browser + voice + scheduled execution*, not "I type, it types back." Adjust your product, your portfolio projects, and your demo videos accordingly.

---

## 3. Workflow of the Week: Multi-Provider Routing in 12 Lines

**The skill:** Build a multi-provider router for your own AI projects, so you can A/B test model quality and never get locked in.

```python
# requirements: pip install litellm
from litellm import completion

PROVIDERS = {
    "code":       {"model": "gemini/gemini-3.1-pro",      "temperature": 0.1},
    "reasoning":  {"model": "anthropic/claude-opus-4-7",  "temperature": 0.2},
    "fast":       {"model": "openai/gpt-5.5-instant",     "temperature": 0.3},
    "cheap":      {"model": "openrouter/qwen-3.5-32b",    "temperature": 0.3},
}

def ask(task_kind: str, prompt: str) -> str:
    config = PROVIDERS[task_kind]
    response = completion(messages=[{"role": "user", "content": prompt}], **config)
    return response.choices[0].message.content

print(ask("code", "Write a Python function to fetch arxiv papers tagged cs.AI"))
```

This pattern lets you swap providers without rewriting calling code. Combine with `tenacity` for retries and `langfuse` or `langsmith` for tracing.

**Sources:**
- [LiteLLM docs](https://docs.litellm.ai/docs/) (official)
- [OpenRouter — multi-provider gateway](https://openrouter.ai/)
- [Artificial Analysis — pricing & benchmarks](https://artificialanalysis.ai/)

**Why it matters to you:**
- **Job lens:** Knowing LiteLLM / OpenRouter at a non-trivial level shows you've actually shipped LLM products vs. just played with ChatGPT. Add a side project that uses 3+ providers and benchmarks them on a domain task. This is **the cheapest, highest-signal portfolio addition you can make this month.**
- **Startup lens:** Customers in regulated industries will demand on-prem or sovereign models in 12–24 months. If your code already routes through an abstraction layer, that's a one-week migration. If it's hard-coded to OpenAI, it's a six-month rewrite. **Pay the abstraction cost early.**
- **Insight:** Single-provider lock-in is the most expensive technical-debt category in AI products of 2026, because pricing and model rankings change every 6 weeks. Always be one config-flag away from a different vendor.

---

## 4. Tip: The "Five Tabs" Habit for Staying Current Without Burning Out

A discipline several frontier engineers have publicly adopted (Simon Willison, Vicki Boykis, Nathan Lambert):

Every morning, before email, open **exactly five tabs in this order**:
1. **[Hugging Face Papers](https://huggingface.co/papers/trending)** — what the community thinks is hot today
2. **[arXiv cs.AI recent](https://arxiv.org/list/cs.AI/recent)** — all today's submissions in your area
3. **[LLM Stats / AI News](https://llm-stats.com/ai-news)** — model releases tracker
4. **One primary lab blog you trust** (rotate: OpenAI, Anthropic, DeepMind, Mistral, Meta)
5. **[Simon Willison's blog](https://simonwillison.net/)** — practitioner-grade reality check on hype

Spend **10 minutes total**, no more. Anything that matters will come back to you 3 more times this week from other sources — that's your filter for "actually important."

**Why it matters to you:**
- **Job lens:** Coming into interviews with the ability to name 3 papers from the past 30 days that excited you, with a *specific* reason why, is unusually impressive. "I read everything OpenAI posts" is not a credential. "I noticed Hugging Face's `ml-intern` last month and tried it on a project" is.
- **Startup lens:** Founder pattern-matching gets sharper the more you read in the trough. The cost of *missing* a 6-week trend is much higher than the cost of skim-reading.
- **Insight:** The half-life of AI news is ~2 weeks. If a story is important enough to act on, you will see it three times in your sources within that window. **Skimming widely + acting on repetition is a higher-EV strategy than deep-reading rare hot takes.**

---

## 5. Quick-Hit Tools Worth Trying This Week

| Tool | Use Case | Free / Paid |
|---|---|---|
| [Karpathy `autoresearch`](https://x.com/karpathy) | Overnight ML experimentation | OSS |
| [HuggingFace ml-intern](https://aitoolly.com/ai-news/article/2026-04-25-hugging-face-launches-ml-intern-an-open-source-ai-agent-for-machine-learning-engineering-tasks) | Auto ML engineering agent | OSS |
| [Parallel Web](https://parallel.ai/) | Programmable browser-as-an-agent | Paid (free tier) |
| [Together AI](https://together.ai/) | Cheapest hosted Qwen / DeepSeek inference | Paid |
| [alphaXiv](https://www.alphaxiv.org/) | arXiv + community annotations | Free |
| [LiteLLM](https://docs.litellm.ai/) | Multi-provider routing in 12 lines | OSS |
| [LangFuse](https://langfuse.com/) | Free open-source LLM observability | OSS / Paid |
