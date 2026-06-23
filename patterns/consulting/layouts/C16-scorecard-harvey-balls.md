---
id: C16
family: consulting
name: Scorecard / Harvey balls
version: 1
status: shipped
unpaper_level: L3
supported_by_current_template: true
converter_ready: true
tokens_compact: 75
---

# C16 · Scorecard / Harvey balls

Compare several options against several criteria at a glance, with a *qualitative*
rating per cell — the classic consulting "Harvey ball" (empty, quarter, half,
three-quarter, full = 0 / 25 / 50 / 75 / 100%), or a red-amber-green status.

## Use when

- The decision rests on how options stack up across multiple criteria.
- The ratings are *judgements* (high / medium / low), not precise numbers.

## Do not use when

- The values are precise numbers — use C15 (option comparison) or a chart.
- There is only one criterion — use a ranked bar (C11).
- Every cell would carry the same rating — the table then says nothing.

## Structure

- A grid of options (rows) × criteria (columns) — a flex/CSS grid today, a real
  `<table>` once the converter can layer balls above a native table object (see
  Conversion). Keep to ≈6 columns × 8 rows.
- Each rating cell carries **`data-unpaper-rating`** — a number `0`–`1` (the
  fraction filled) — **and** an inline SVG Harvey ball drawn to match. Dual
  encoding, per `spec.md` §6: the SVG renders and prints, the attribute carries the
  meaning.
- A one-line legend mapping ball levels to words.
- Optionally mark the recommended option's row.
- A `Source:` / basis line beneath the table.

## unPaper primitives

- a real `<table class="tbl">` → native editable table (L2)
- per-cell `data-unpaper-rating="0..1"` + an inline `<svg>` pie (the visual encoding)
- `.legend`, `.source`

## Conversion (SHIPPED — the first consulting-visual-compiler exhibit)

Each Harvey ball lowers to **native, recolorable PowerPoint shapes**: an outline
ring plus a filled pie sector whose swept angle = `rating × 360°` (clockwise from
12 o'clock), built as `custGeom` freeforms via the proven arc/patch path — so the
build and patch passes needed no change. The labels convert as native text, and
`currentColor` drives the balls so they take the deck accent. Verified end to end
in the harness (`test/corpus/scorecard.html`, 99.50%; XML asserts `custGeom` +
`arcTo`, no `blip`). Implemented in `extract.mjs` as the `data-unpaper-rating`
pass (2026-06-23). A single native PPTX **table object** with the balls overlaid
is a planned refinement (the builder emits freeforms before tables, so a table
would occlude them); today the scorecard is a grid of native text + native ball
shapes.

## Prompt fragment (compact)

> Scorecard: a real `<table>` of options × criteria; each cell a Harvey-ball
> rating (`data-unpaper-rating` 0–1, drawn as a filled-pie SVG: empty, quarter,
> half, three-quarter, full) or a RAG colour; add a one-line legend and a source
> line. Use to compare options qualitatively at a glance.

## HTML skeleton (illustrative)

```html
<table class="tbl scorecard">
  <thead>
    <tr><th>Option</th><th>Cost</th><th>Speed</th><th>Risk</th><th>Fit</th></tr>
  </thead>
  <tbody>
    <tr>
      <th>Build in-house</th>
      <td data-unpaper-rating="0.25"><svg viewBox="0 0 24 24"><!-- quarter --></svg></td>
      <td data-unpaper-rating="0.5"><svg viewBox="0 0 24 24"><!-- half --></svg></td>
      <td data-unpaper-rating="1"><svg viewBox="0 0 24 24"><!-- full --></svg></td>
      <td data-unpaper-rating="0.75"><svg viewBox="0 0 24 24"><!-- three-quarter --></svg></td>
    </tr>
    <!-- …more options… -->
  </tbody>
</table>
<p class="legend">empty = none · half = partial · full = strong</p>
<p class="source">Source: team assessment, March 2026.</p>
```

## Checks

- It is a real `<table>`, not `<div>`s faked into a grid.
- Every rating cell has both `data-unpaper-rating` and a matching SVG ball.
- A legend explains the scale and a `Source:` / basis line is present.
- Ratings vary across the table (otherwise the comparison is empty).
