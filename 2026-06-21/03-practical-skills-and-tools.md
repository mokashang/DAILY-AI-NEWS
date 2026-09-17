# Practical Skills &amp; Tools — 2026-06-21

Four things you can install or change tonight, ordered by ROI: **(1) Claude Code 2.1.183** for hardened auto-mode + a real Azure Foundry cache fix; **(2) `.mcpb` bundles** as your MCP distribution format (5 of the top-10 trending Claude/MCP repos this week ship as `.mcpb`); **(3) Devin Desktop + the Agent Client Protocol (ACP)** as a pragmatic side-by-side with Claude Code; **(4) the prompt-caching base-camp pattern**, re-grounded in this week's *Lessons from building Claude Code* primary post.

Tags: `#claude-code #mcp #mcpb #acp #prompt-caching #cost #safety`

---

## 1. Claude Code 2.1.183 — hardened auto-mode + Azure Foundry cache fix {#1-cc-2-1-183}

**What happened:** Claude Code shipped **version 2.1.183** on **Thursday, June 19, 2026**. The changelog highlights:

- **Auto-mode safety defaults.** When running in auto mode (`--dangerously-skip-permissions` and equivalents), Claude Code now **blocks by default**:
  - `git reset --hard`
  - `git checkout -- .`
  - `git clean -fd`
  - `git stash drop`
  - `git commit --amend` (when the commit being amended was not authored by the agent in this session)
  - `terraform destroy` / `pulumi destroy` / `cdk destroy` (unless you named the stack)
- **Prompt-cache fixes.** Cache was previously missing on custom `ANTHROPIC_BASE_URL` deployments and on **Azure Foundry** (Azure was injecting a per-request attestation token that busted the cache key). Both fixed.
- **Write/Edit fix.** A latent bug producing **0-byte files on network drives** (NFS / SMB) was corrected.

**Sources:**
- [Claude Code Changelog (docs)](https://code.claude.com/docs/en/changelog) `[primary]`
- [anthropics/claude-code GitHub Releases](https://github.com/anthropics/claude-code/releases) `[primary]`
- [Releasebot — Claude Code Updates June 2026](https://releasebot.io/updates/anthropic/claude-code) `[secondary]`

### Why it matters to you

- **Job lens:** "I run Claude Code in auto mode on real production repos" is now a credible interview claim *because* of these defaults — pre-2.1.183 it was reckless. Lead the next FDE / Applied-AI interview answer with: *"After 2.1.183 I let Claude Code auto-mode the boring 80% of a deploy script — the new destructive-op blocks make it safe; I keep the verifier loop in front of `terraform apply` myself."* That's the dialect a hiring manager wants to hear.
- **Startup lens:** If your product is an agent that *uses* Claude Code as a runtime, the safety defaults are your friend — they reduce your **observable customer-incident surface** by an order of magnitude. Lean into "auto-mode-by-default" as a product positioning now; pre-2.1.183 it would have been malpractice.
- **Insight:** The **prompt-cache fix for Azure Foundry** is the under-reported half of this release. Enterprise Anthropic deployments are increasingly Azure-tenanted (Microsoft Office GA, [2026-06-20/02 §2](../2026-06-20/02-new-emerging.md#2-office)). If your previous cost model assumed cache hits on Azure-tenanted Claude calls and you weren't seeing them, *that's why* — and your June bill just got smaller without you doing anything. **Re-baseline your `cost.md` per project against last week's numbers.**

→ Cross-link: [`04` §1 DeepSWE — the benchmark that rewards exactly the kind of unattended auto-mode runs 2.1.183 makes safe](./04-research-progress.md#1-deepswe) · [2026-06-16/03 §1 meter-aware starter kit](../2026-06-16/03-practical-skills-and-tools.md#1-meter-aware-starter).

### Tonight's 10-minute install

```bash
# 1. Upgrade
npm install -g @anthropic-ai/claude-code@2.1.183

# 2. Verify
claude --version  # should print 2.1.183 or later

# 3. Re-baseline your cost dashboard
claude api cost --since=7d --by=model --by=cache_status \
  | tee ./cost-snapshots/$(date +%F)-post-2-1-183.md

# 4. (Azure-tenanted only) re-run yesterday's highest-volume project and
#    confirm cache_read_input_tokens > 0 in the next response
```

If `cache_read_input_tokens` is still 0 after the upgrade on Azure: open an issue on `anthropics/claude-code` with the redacted request — the fix landed, but enterprise edge cases continue to surface.

---

## 2. `.mcpb` bundles — the distribution format for MCP servers {#2-mcpb-bundles}

**What happened:** This week's **#1 trending Claude / MCP repo on GitHub** is **`mvanhorn/last30days-skill`**, distributed as a **`.mcpb` bundle**: one file, one click, installs as `/last30days` in the Claude desktop client and registers as an MCP server. **Five of the top-10 trending Claude/MCP repos this week ship as `.mcpb`.** The format is the emerging distribution standard for skills + servers + prompts as a unit.

The `.mcpb` format is:

- A **single zip-shaped artifact** containing the MCP server, its manifest (`mcpb.json`), an embedded `CLAUDE.md` (or skill prompt), optional sample data, and a signature.
- **Trust profile:** signed, single-source; the host client can verify the signature and enforce the manifest's declared scopes (filesystem read/write, network egress, env-var access) before install.
- **Cross-host:** Claude Desktop ships first-party; Cursor + Devin Desktop are adding installers; the **MCP `2026-07-28` RC's "MCP Apps" surface ([`02` §1](./02-new-emerging.md#1-mcp-rc))** is the cross-host generalization.

**Sources:**
- [GitHub — mvanhorn/last30days-skill](https://github.com/mvanhorn/last30days-skill) `[primary]`
- [Model Context Protocol Blog — `2026-07-28` RC (MCP Apps section)](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) `[primary]`
- [andrew.ooo — Headroom (reversible context compression, ~262 stars/month) review](https://andrew.ooo/posts/headroom-context-compression-llm-agents-review/) `[analysis]`

### Why it matters to you

- **Job lens:** "I ship MCP servers as `.mcpb` bundles" is a one-line resume bullet that demonstrates **you ship the whole thing**, not just the code. Pair it with a registry-listed bundle and a 30-second demo gif and you're inside the top 5% of MCP-adjacent applicants.
- **Startup lens:** **The MCP registry is the App Store of agent tools, with the same first-mover dynamics.** Pick a vertical that doesn't have a quality `.mcpb` yet — *legal-discovery*, *medical-records-summary*, *robotics-controller-debug*, *vertical-CRM-actions* — and ship one this weekend. The registry will accept duplicates, but citations and download counts compound for the *first credible* server in a slot.
- **Insight:** **Distribution is the moat now, not code quality.** A `.mcpb` bundle with a credible README, a 60-second demo, and a clean install path will out-distribute a more sophisticated unbundled server 10:1 in the first 90 days. **Optimize for friction-to-install before optimizing for capability depth.**

→ Cross-link: [`02` §1 MCP `2026-07-28` RC adds MCP Apps as the cross-host generalization](./02-new-emerging.md#1-mcp-rc) · [`05` §3 Sunday distribution playbook](./05-career-and-startup.md#3-distribution).

### Tonight's 30-minute bundle ship

```bash
# 1. Scaffold an .mcpb bundle from an existing MCP server
npx @modelcontextprotocol/mcpb-cli init ./my-mcp-server

# 2. Edit mcpb.json to declare scopes minimally (least-privilege)
#    - filesystem: read-only on the smallest subtree that works
#    - network:    declare each domain explicitly
#    - env:        the smallest set of env vars

# 3. Build + sign
npx @modelcontextprotocol/mcpb-cli build --sign

# 4. Verify locally (Claude Desktop or Cursor)
open ./dist/my-mcp-server.mcpb

# 5. Submit to the public registry
npx @modelcontextprotocol/mcpb-cli publish
```

Then commit the source repo with a README headline that names the spec version explicitly: *"MCP server, built to the 2026-07-28 RC."* That's the LinkedIn keyword nobody else has on June 21.

---

## 3. Devin Desktop + the Agent Client Protocol (ACP) {#3-devin-acp}

**What happened:** On **June 2, 2026**, Cognition rebranded **Windsurf as Devin Desktop** and shipped:

- **Agent Client Protocol (ACP)** — a separate protocol from MCP, focused on **multiple coding agents coexisting inside one editor**. Codex, Claude Agent, OpenCode, and custom agents can run side-by-side in the same editor session under ACP.
- **Spaces** — feature-branch-scoped collections of agent sessions, PRs, and files.
- **Devin Local** — the replacement for Cascade with subagent support. Claims **~30% fewer tokens** per equivalent task.

ACP is **not** a competitor to MCP — they sit at different layers. MCP is **agent ↔ tools/servers**; ACP is **editor ↔ multiple agents**. A serious 2026 builder should know both surfaces.

**Sources:**
- [ChatForest — Windsurf Is Now Devin Desktop](https://chatforest.com/builders-log/windsurf-devin-desktop-rebrand-devin-local-acp-builder-guide/) `[secondary]`
- [apidog — What's new in Devin 2026](https://apidog.com/blog/whats-new-in-devin-2026/) `[secondary]`
- [The New Stack — Claude Code vs. Cursor vs. Codex vs. Antigravity, six months in](https://thenewstack.io/claude-code-vs-cursor-vs-codex-vs-antigravity-2026/) `[analysis]`

### Why it matters to you

- **Job lens:** Interview answer: *"My default IDE is Claude Code; I keep Devin Desktop open for tasks I want to run on a non-Claude agent in parallel — ACP lets the two coexist."* That single sentence shows you've internalized the protocol-fragmentation reality and built a workflow around it. **Don't** say "I switched from Cursor to Devin Desktop"; say "I use both Claude Code and Devin Desktop for different jobs, mediated by their respective protocols."
- **Startup lens:** ACP's existence reinforces the **multi-agent IDE side-channel** wedge — there's room for a small product that *bridges* MCP and ACP so a single tool surface can be called from both Claude Code (MCP) and Devin Desktop (ACP) without rewriting. Founder bet, weekend project, or both.
- **Insight:** With **Cursor → SpaceX** ([`02` §2](./02-new-emerging.md#2-cursor-stable)), the coding-agent IDE market is now four distinct vendors (Claude Code, Devin Desktop, Codex, Cursor-under-xAI) on **two protocols** (MCP, ACP). **Don't bet on which vendor wins. Bet on the protocol that connects them.** That's MCP.

→ Cross-link: [`02` §2 SpaceX → Cursor as the IDE-vendor catalyst](./02-new-emerging.md#2-cursor-stable).

---

## 4. Prompt-caching base-camp pattern — re-grounded {#4-prompt-caching}

**What happened:** Anthropic published a primary write-up titled *"Lessons from building Claude Code: prompt caching is everything"* (it's been quietly the most-cited single blog post in the practitioner community this June). The actionable distillation:

- **Cached input bills at ~10% of standard input.** Cache writes cost ~25% more (one-time).
- **TTL is 5 minutes**, reset on each cache hit — long-running sessions stay cached as long as you keep using them.
- **Cache is keyed per (model, API key, organization).** Mixing API keys or rotating models busts the cache. **Standardize on one model + one key per project** for the duration of a session.
- **Place stable content at the top of the prompt** — `CLAUDE.md`, large reference files, system prompt — as your "base camp." Volatile content (the user's latest turn) goes at the bottom.

This is the same pattern that gives a well-structured Claude Code session a **10× cost advantage** over a naive multi-turn loop on the same task.

**Sources:**
- [Anthropic — Lessons from building Claude Code: prompt caching is everything](https://claude.com/blog/lessons-from-building-claude-code-prompt-caching-is-everything) `[primary]`
- [Claude API Docs — Prompt caching](https://platform.claude.com/docs/en/build-with-claude/prompt-caching) `[primary]`
- [MindStudio — Prompt caching to cut Claude Code token costs](https://www.mindstudio.ai/blog/prompt-caching-cut-token-costs-claude-dynamic-workflows) `[analysis]`

### Why it matters to you

- **Job lens:** The right one-line answer to "how do you keep Claude Code costs under control?" is *"base-camp ordering, one model per project, prompt caching, and the Opus-orchestrator / Sonnet-worker split — measured per-step in a `cost.md` checked into the repo."* That sentence does the work of an entire interview round.
- **Startup lens:** A 10× cost lever on every Claude API call is the difference between an Anthropic-stack product that's structurally unprofitable and one that's structurally a margin business. **Bake the base-camp pattern into your product's prompt-construction layer from day one.** Don't retrofit it later.
- **Insight:** The 2.1.183 Azure Foundry cache fix ([`§1`](#1-cc-2-1-183)) and the base-camp pattern combine to a single rule: **if your `cache_read_input_tokens` is < 60% of your input tokens on a steady-state session, you're leaving money on the table.** This is the single most measurable optimization you can run *this Sunday* against your last week of usage logs.

→ Cross-link: [`§1`](#1-cc-2-1-183) — the 2.1.183 Azure cache fix · [2026-06-16/03 §1 meter-aware starter kit (orchestrator + worker)](../2026-06-16/03-practical-skills-and-tools.md#1-meter-aware-starter).
