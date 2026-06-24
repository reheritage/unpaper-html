---
id: C06
family: consulting
name: Single chart proof
version: 1
status: shipped
unpaper_level: L3
supported_by_current_template: true
converter_ready: true
tokens_compact: 37
---

# C06 · Single chart proof

One chart carries the whole point. When the number is the argument, give it the
slide: a title that states what the chart proves, the chart itself at full size,
and a source line. Nothing competes with it.

## Use when

- A single trend, comparison, or distribution is the entire message.
- The chart is strong enough to stand alone — it earns the full canvas.

## Do not use when

- You need to compare several cuts of the same measure — use small multiples (C07).
- The point is qualitative — use a scorecard (C16) or a 2×2 (C12).

## Structure

- An **action title** stating the conclusion the chart supports ("Demand outran
  supply every quarter since FY23").
- ONE `data-unpaper-chart` filling the body — bar, line, area, pie, or doughnut.
- A single `Source:` line beneath it. No second visual, no decorative chrome.

## unPaper primitives

- `data-unpaper-chart` → native data-editable chart with an embedded worksheet
- `h2.title` → native title · `.source` → native caption

## Conversion

The chart lowers to a native pptxgenjs chart (bar/line/area/pie/doughnut) with an
embedded Excel worksheet — fully editable in PowerPoint, not a flattened picture.
L3 because the rendered chart frame/markers differ slightly from the authored SVG;
the data and type round-trip natively.

## Prompt fragment (compact)

> Single chart proof: one data-unpaper-chart carries the whole point; the title
> states what the chart proves; one source line below; no second visual.

## HTML skeleton (illustrative)

```html
<h2 class="title">Demand outran supply every quarter since FY23</h2>
<div data-unpaper-chart='{"type":"line","categories":["Q1","Q2","Q3","Q4"],"series":[{"name":"Demand","values":[120,140,165,190]},{"name":"Supply","values":[110,118,121,125]}]}'></div>
<p class="source">Source: order book vs. capacity model, FY23–FY24.</p>
```

## Checks

- Exactly one chart on the slide.
- The title states the conclusion, not the chart's subject.
- The chart uses `data-unpaper-chart` (so it converts native), not a hand-drawn SVG.
- A `Source:` line is present.
