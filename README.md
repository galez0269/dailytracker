# Industry Tracker

A daily intelligence brief for sourcing, sharpening, and codifying thought leadership across the global network.

It runs on demand: you trigger it, Claude pulls and synthesises across a curated source list, grades each item through the house lens, adds a *why-us* line, and files the result so it compounds toward the year-end report. It is not a feed reader — the point is judgement, not aggregation.

---

## How to use

Two triggers, two skills:

| Say this | Skill | What happens |
|---|---|---|
| **"Run my daily brief"** | `daily-brief` | Pulls today's signal across all categories, grades it through the lens, returns a formatted brief, and files it — saving the dated brief to `briefs/` and appending high-impact items to the ledger. Filing is the built-in closing step, not a separate action. |
| **"Run my lens over [link / text / idea]"** | `lens` | Point it at anything ad hoc. It tells you where it lands (must-know / high-impact / signal / noise) and why it matters for us — and offers to log it to the ledger if it clears the bar. |

---

## What it tracks

Four categories:

- **Industry Buzz** — prevailing discourse on social, brand-building, and the questions people want answered.
- **Trends** — what's rising: Google Trends, TikTok, Instagram, Reddit, cultural moments. *Currently sourced via secondary reporting and trend-aggregators rather than raw platform scraping — see [Sources](#sources).*
- **POVs** — how industry peers are responding to the prevailing discourse.
- **Misc** — everything else worth keeping tabs on: signals that reinforce our social authority and specialism.

> *Mental Models and People are parked for now. The structure leaves clean room to add them back later as **library** skills — they accumulate and dedupe rather than refresh daily, so they behave differently from the four above.*

---

## The lens & "why us"

The lens is what separates this from an RSS reader. Every item in a brief carries a **why-us** line — why it matters for the network's thought leadership, or what we could put out in response.

Its criteria live in **`context/`**, deliberately *outside* the skills:

- **`context/priorities.md`** — the business focus, the network's throughlines, upcoming report launches, and what *why-us* means right now. **You edit this.** It's currently a placeholder, awaiting your context.
- **`context/rubric.md`** — how we grade impact (must-know vs high-impact vs signal vs noise) and the framing instincts to apply.

Both `daily-brief` and `lens` read these files, so there is one source of truth. Change your priorities in one place and every future brief reflects it. The skills are the *procedure*; context is the *content*.

---

## The archive & the year-end report

Filing is the **closing step of every `daily-brief` run**, not a separate action you trigger. Each run does **double-entry**:

1. The full brief is saved to `briefs/YYYY-MM-DD.md`.
2. Its high-impact items are appended as tagged rows to `ledger.md` — date, category, item, source, tier, theme tags, why-us.

The `lens` skill can also log a one-off item to the ledger when you run it ad hoc.

The ledger is the compounding layer. At year-end you synthesise a few hundred structured rows — which themes recurred, which POVs kept surfacing, where the network led — instead of re-reading every daily file. The archive is built *for the report* from day one.

---

## Repo map

```
industry-tracker/
├── README.md              ← you are here
├── sources.yaml           source registry: feed, access tier, category tags
├── context/
│   ├── priorities.md      ← YOU edit: business focus + what "why us" means (placeholder)
│   └── rubric.md          how we grade impact + framing instincts
├── skills/
│   ├── daily-brief/       gather → categorise → grade → draft → file (save + ledger)
│   └── lens/              standalone: grade any item; can log to ledger
├── briefs/
│   └── YYYY-MM-DD.md       dated daily outputs
├── ledger.md              cumulative tagged log → powers the year-end report
└── templates/
    └── brief.md           output format (categories + required why-us field)
```

---

## Sources

The canonical list lives in [`sources.yaml`](./sources.yaml), tagged by category and by **access tier**:

- **Clean** — RSS or reliably fetchable full text. The spine for Buzz and POVs. *(AdAge, Campaign, LBB Online, The Cut.)*
- **Framing-only** — paywalled, but headlines and the discourse *around* them are reachable, which is usually enough for "what's being discussed." *(WSJ, The Atlantic, The New Yorker.)*
- **Curated Substack** — no open index exists, but each newsletter exposes RSS at `<publication>.substack.com/feed`. Curated list only:
  - *Feed Me* — Emily Sundberg
  - *Idlegaze* — Alexi Gunner
  - *Trends Radar* — Anu *(handle to confirm)*
  - *Links I'd Gchat You* — Caitlin Dewey
  - *Link in Bio* — Rachel Karten
  - *After School* — Casey Lewis
- **Platform-gated** — Google Trends, TikTok, Instagram, Reddit. Reddit is searchable/API-able; the rest are ToS-fraught and brittle to scrape, so **Trends leans on secondary reporting** for now.

Feed URLs are marked *verify-at-build* in `sources.yaml` — I'll confirm each live one when we author `daily-brief`.

---

## Status

- ✅ Structure + README
- ✅ `context/rubric.md` — starter rubric, tunable
- ✅ `context/priorities.md` — filled (two throughline items drafted from your Q1–Q2 work, flagged for your confirmation)
- ✅ `templates/brief.md` — output format
- ⬜ Skills — `daily-brief` + `lens` specced (stubs in place), full authoring next
- ⬜ `sources.yaml` feed URLs — verify at build
