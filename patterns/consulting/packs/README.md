# Consulting subtype packs

A **pack** is a deck *subtype*: a named goal (recommendation, market study,
transformation, …) and the slice of the C-series catalog it tends to reach for.
A pack is **not a fixed deck** — it is a *palette*. A generator compiles the
selected patterns' compact fragments into the prompt and tells the model to use
what the content needs, in any order, adding a cover, dividers and other slides
the story calls for.

## Schema

```jsonc
{
  "id": "recommendation",          // canonical subtype id (matches the generator's option)
  "family": "consulting",
  "label": "Recommendation",       // UI label
  "hint": "Answer first, then the case",
  "desc": "One-line description shown in the picker.",
  "order": 1,                       // sort order in the goal list (general = 0)
  "default": true,                  // optional — marks the neutral default goal
  "patterns": ["C02", "C05", "..."],// the C-series ids this goal favours (see ../../index.json)
  "note": "Design rationale (humans + capable assistants)."
}
```

## Files

| File | Goal | Best paired style |
| --- | --- | --- |
| `general.json` | General (neutral default) | Boardroom Classic |
| `recommendation-deck.json` | Recommendation | Boardroom Classic / Operator Redline |
| `market-study.json` | Market study | Operator Redline / Modern Insight |
| `transformation-roadmap.json` | Transformation | Systems Blueprint |
| `research-readout.json` | Research readout | Modern Insight / Research Bureau |
| `executive-briefing.json` | Exec briefing | Executive Brief |

## How a generator uses them

It resolves the chosen pack's `patterns` to their `compact_prompt` fragments in
[`../../index.json`](../../index.json), drops any with `converter_ready: false`
(held back until the converter lowers them — e.g. C08 waterfall), and inlines the
rest under the family rule + the chosen archetype's tone. Budget for a whole
pack: ~500–1,500 tokens. It **never fetches this repo at run time** — the
fragments are compiled in ahead of time.
