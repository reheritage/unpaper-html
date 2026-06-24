---
id: C05
family: consulting
name: Action-title evidence slide
version: 1
status: shipped
unpaper_level: L2
supported_by_current_template: true
converter_ready: true
tokens_compact: 63
---

# C05 · Action-title evidence slide

The workhorse of a consulting deck: one claim and the single proof that supports
it, together on one slide. The title states the finding as a complete sentence;
one chart or table proves it; a short so-what reads the evidence. Most slides in a
recommendation deck are this pattern.

## Use when

- You have one point to make and one piece of evidence that makes it — the default
  for the body of the argument.
- You want a reader to be able to flip through the deck reading only the titles and
  still follow the storyline.

## Do not use when

- The slide carries two unrelated proofs — split it (one idea per slide).
- There is no evidence yet, only an assertion — either find the proof or cut the slide.

## Structure

- An **action title** (`h2.title`): the finding as a full sentence with a verb and a
  so-what, not a noun label ("Channel costs fell 40% after automation" — not "Channel
  costs").
- A `data-unpaper-lay="2l"` split: a short **so-what** (2–3 bullets, the wide left)
  and **ONE proof object** — a `data-unpaper-chart` or a `<table>` — on the narrow
  right.
- A `Source:` line directly under the evidence.
- Exactly one big visual block per slide.

## unPaper primitives

- `h2.title` → native title · `data-unpaper-lay="2l"` two-column grammar
- `data-unpaper-chart` → native editable chart · or `table.tbl` → native table
- `.source` → native caption text

## Conversion

The title and bullets are native text, the chart converts to a native
data-editable chart (with an embedded worksheet), a table to a native PPTX table.
All native, no gap.

## Prompt fragment (compact)

> Action-title evidence slide: the title states the finding as a full sentence; use
> data-unpaper-lay='2l' with a short so-what (2-3 bullets) on the left and ONE proof
> object (chart or table) on the right; put a 'Source:' line directly under the
> evidence.

## HTML skeleton (illustrative)

```html
<h2 class="title">Automation cut cost-to-serve by 40% without lifting churn</h2>
<div data-unpaper-lay="2l">
  <div>
    <ul>
      <li>Self-service now resolves two of every three tickets.</li>
      <li>Headcount held flat through the migration.</li>
      <li>NPS rose 6 points over the same period.</li>
    </ul>
  </div>
  <div>
    <div data-unpaper-chart='{"type":"bar","categories":["FY22","FY23","FY24"],"series":[{"name":"Cost to serve","values":[100,78,60]}]}'></div>
    <p class="source">Source: ops ledger, FY22–FY24.</p>
  </div>
</div>
```

## Checks

- The title is a full sentence stating the so-what, ≤ ~8 words where possible.
- There is exactly ONE proof object (chart or table), not two stacked.
- A `Source:` line sits under the evidence.
