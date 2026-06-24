---
id: C07
family: consulting
name: Small multiples
version: 1
status: shipped
unpaper_level: L3
supported_by_current_template: true
converter_ready: true
tokens_compact: 41
---

# C07 · Small multiples

Several small charts of the *same type and scale*, side by side, so the reader
compares shapes at a glance. The repetition is the point: same axes, same units,
only the data changes — segment to segment or period to period.

## Use when

- You compare the same measure across segments, regions, cohorts, or periods.
- The comparison lives in the *shape* of each series, not in one headline number.

## Do not use when

- One chart already makes the point — use C06.
- The cuts use different units or scales — a shared scale is what makes this honest;
  without it, use separate slides.

## Structure

- 2–4 charts of **identical type and identical scale**, laid out with
  `data-unpaper-lay="2"` or `"3"`.
- The same axis range on every panel (so heights are comparable).
- One shared `Source:` line for the set.
- A title that states what the comparison reveals.

## unPaper primitives

- `data-unpaper-lay="2"` / `"3"` → equal-width grid grammar
- repeated `data-unpaper-chart` → one native chart per panel
- `.source` → one shared native caption

## Conversion

Each panel converts to its own native data-editable chart. Keep the scales equal in
the authored data — the converter preserves each chart's values, so a mismatched
authored scale stays mismatched. L3 (same chart-frame delta as C06).

## Prompt fragment (compact)

> Small multiples: 2-4 charts of the SAME type and identical scale side by side
> (data-unpaper-lay='2' or '3') to compare segments or periods; one shared source
> line.

## HTML skeleton (illustrative)

```html
<h2 class="title">Adoption follows the same S-curve in every region</h2>
<div data-unpaper-lay="3">
  <div data-unpaper-chart='{"type":"line","categories":["Y1","Y2","Y3"],"series":[{"name":"DACH","values":[5,30,70]}]}'></div>
  <div data-unpaper-chart='{"type":"line","categories":["Y1","Y2","Y3"],"series":[{"name":"Nordics","values":[4,28,66]}]}'></div>
  <div data-unpaper-chart='{"type":"line","categories":["Y1","Y2","Y3"],"series":[{"name":"Benelux","values":[6,33,72]}]}'></div>
</div>
<p class="source">Source: regional adoption tracker, Y1–Y3.</p>
```

## Checks

- All panels are the same chart type with the same scale.
- 2–4 panels, no more (beyond that the comparison blurs).
- Each uses `data-unpaper-chart`; one shared `Source:` line.
