---
id: C15
family: consulting
name: Option comparison
version: 1
status: shipped
unpaper_level: L2
supported_by_current_template: true
converter_ready: true
tokens_compact: 38
---

# C15 · Option comparison

Lay options against criteria in a real table so the reader can weigh them
directly. When the values are concrete — cost, time, headcount, a yes/no — a clean
table beats any diagram. Mark the recommended option so the table makes a point,
not just a list.

## Use when

- 2–5 options are judged on the same set of concrete criteria.
- The values are precise (numbers, durations, yes/no) — not qualitative ratings.

## Do not use when

- The ratings are judgements (high/medium/low) — use a Harvey-ball scorecard (C16).
- There is only one criterion — rank with a bar (C11).

## Structure

- A real `<table class="tbl">`: options as rows, criteria as columns (≤ ~6 columns).
- A header row; concise, parallel cell values (same unit down each column).
- The recommended row or column **marked** (a tag, a tint, or a bold label).
- One `Source:` / basis line beneath the table.

## unPaper primitives

- `table.tbl` + `thead` + `tbody` → native editable PPTX table (fills, borders, merges)
- `.source` → native caption

## Conversion

The table lowers to a native PowerPoint table object — cells, fills, and borders
editable, columns resizable. Give cells uniform padding (the converter needs it to
map the grid); avoid putting block/atomic children inside cells (that disqualifies
the native-table lift and falls back to text + border bars).

## Prompt fragment (compact)

> Option comparison: a real <table> with options as rows and criteria as columns
> (<=6 columns); mark the recommended row or column; one source line below.

## HTML skeleton (illustrative)

```html
<table class="tbl">
  <thead>
    <tr><th>Option</th><th>Cost</th><th>Time to value</th><th>Risk</th><th>Recommended</th></tr>
  </thead>
  <tbody>
    <tr><th>Build in-house</th><td>€40M</td><td>3 yrs</td><td>High</td><td></td></tr>
    <tr><th>Channel partner</th><td>€12M</td><td>18 mo</td><td>Low</td><td>✓</td></tr>
    <tr><th>Acquire</th><td>€60M</td><td>1 yr</td><td>Medium</td><td></td></tr>
  </tbody>
</table>
<p class="source">Source: cost model + diligence, Q1 2026.</p>
```

## Checks

- It is a real `<table>`, not divs faked into a grid.
- ≤ ~6 columns; values are parallel and concrete.
- The recommended option is marked; a `Source:` line is present.
