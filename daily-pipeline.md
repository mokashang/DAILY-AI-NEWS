# daily-pipeline.md — How the daily edition is produced

So a fork or handoff can keep the cadence without re-deriving the workflow.

---

## Inputs

1. **Yesterday's edition's `Watchlist deltas`** — open threads to advance.
2. **Live web sources** — see [SOURCES.md](./SOURCES.md), tier-by-tier.
3. **[ME.md](./ME.md)** — the profile every edition is written *to*.
4. **[ACTIONS.md](./ACTIONS.md), [STARTUPS.md](./STARTUPS.md), [APPLICATIONS.md](./APPLICATIONS.md), [WATCHLIST.md](./WATCHLIST.md)** — trackers to update from the day's stories.

## Workflow (60–120 min)

1. **Scan primary sources** (Tier 1 in SOURCES.md):
   - Anthropic / OpenAI / DeepMind / Meta / Microsoft / xAI / Mistral / Hugging Face news pages
   - Anthropic Red Team Blog
   - Ramp AI Index (Mondays)
2. **Live news searches** (Tier 2–4) for: lab moves · funding · arXiv · benchmarks · jobs/hiring data.
3. **Cross-confirm** any single-source claim with at least one independent outlet before marking `[secondary]`. Single-source = `[rumor]`.
4. **Filter through the three lenses** (Job · Startup · Insight). If a story doesn't touch any of the three, demote to a one-line "Other" or drop.
5. **Write the 6 files** (`00`–`05`). Order: `01`–`05` first, then write `00-tldr.md` last.
6. **Update trackers**:
   - WATCHLIST.md → add/promote/close threads
   - ACTIONS.md → add this week's tasks
   - STARTUPS.md → file new wedges, re-rank if needed
   - APPLICATIONS.md → log any new applications planned this week
   - ME.md → only if a focusing-decision shift was earned this week
7. **Update [LATEST.md](./LATEST.md)** to point at today.
8. **Update [README.md](./README.md)** Editions table with today's row.
9. **Commit, push, PR, merge to main.** No per-edition approval required (per [ME.md](./ME.md) repo conventions).

## Quality checklist (before merge)

- [ ] Every claim has a source link.
- [ ] Source-confidence tag on every primary claim (`[primary]` / `[secondary]` / `[analysis]` / `[aggregator]` / `[rumor]`).
- [ ] Every story ends with **Job · Startup · Insight** lensed implications.
- [ ] Tags applied (`#topic`) so the archive remains grep-able.
- [ ] `00-tldr.md` Watchlist deltas updated against yesterday's.
- [ ] Cross-links between the 6 files where useful.
- [ ] Reading guide on `00-tldr.md` matches today's actual content.

## Anti-patterns to avoid

- **Backfilling stale news after a gap.** Note the gap once (see today's TL;DR footer) and write to current-state-of-play instead.
- **Generic AI news.** If a story doesn't touch the [ME.md](./ME.md) profile, drop it.
- **One-source rumors as fact.** Tag them `[rumor]` or omit.
- **Tracker drift.** If editions accumulate threads but trackers don't update, the system breaks.
