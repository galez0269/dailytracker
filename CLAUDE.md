# CLAUDE.md — project guide for Claude Code

This repo is a daily industry-intelligence tracker. See `README.md` for the full picture.

## Skills
- `/daily-brief` — generate today's brief, score it through the lens, save it, log to the ledger, and publish. Full spec: `.claude/skills/daily-brief/SKILL.md`.
- `/lens` — grade a single item ad hoc. Spec: `.claude/skills/lens/SKILL.md`.

## Non-negotiables
- **Registry discipline.** Only draw from sources in `sources.yaml` (or their own first-party reporting). Never cite SEO "trends" round-ups or marketing-aggregator blogs. Trends comes from cultural titles, trend studios, Substacks, and thinkers — not listicles.
- **Judgement over aggregation.** Every item carries a one-line *why-us*. If there's nothing to say, it's not a brief item.
- **Publish every brief.** After writing `briefs/YYYY-MM-DD.md` and updating `ledger.md`, always commit and push both:
  ```bash
  git add "briefs/$(date +%F).md" ledger.md && git commit -m "brief: $(date +%F)" && git push
  ```
- **Idempotent.** If today's brief already exists, replace today's file and today's ledger rows rather than duplicating.

## The lens lives in context/
`context/priorities.md` (what we care about — editable) and `context/rubric.md` (how we grade) are the single source of truth. Read both every run.
