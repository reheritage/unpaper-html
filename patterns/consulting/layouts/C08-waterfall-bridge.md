---
id: C08
family: consulting
name: Waterfall / bridge
version: 1
status: shipped
unpaper_level: L3
supported_by_current_template: true
converter_ready: true
tokens_compact: 92
---

# C08 · Waterfall / bridge

> **SHIPPED native, live in the recommendation-deck pack (2026-06-25).** The
> converter renders a hand-authored waterfall as **100% native shapes + text** with
> NO new pass — corpus `test/corpus/waterfall.html` 99.22%, zero objects flattened
> (every bar movable, every label retypeable). The bars are positioned divs (→
> native shapes), the connectors thin divs (→ native shapes), the labels text. The
> authoring teacher is now live too: the consulting template carries a **Value
> bridge** demo slide (`data-kind="waterfall"`, tagged for recommendation /
> transformation / market-study) and the compact fragment teaches the running-total
> px geometry — the positions are baked into the markup (the web converter runs
> scripts OFF, so they can't be computed by JS). **Keep the plot within the slide:
> an auto-fit shrink would scale the slide and flatten it** (the demo uses scale
> 2.5px/unit, plot ≤ 280px tall, so it never triggers the shrink).

Walk a total from a start value to an end value through a sequence of positive and
negative steps — the "bridge" from last year's margin to this year's, or from list
price to pocket price. Each step is a floating bar; connectors carry the running
total across.

## Use when

- You explain how a total *changed*, decomposed into the moves that drove it.
- The audience needs to see which step helped and which hurt, and by how much.

## Do not use when

- You only need the start and end totals — use two stats (C10).
- The parts are a static composition of a whole, not a sequence of changes — use a
  stacked bar or a breakdown table.

## Structure

- A start total bar (grounded at the axis), then floating step bars (up = positive,
  down = negative), then an end total bar.
- Each step labelled with its **delta**; start and end labelled with their totals.
- Connector lines linking each bar's top to the next bar's base (the running total).
- A consistent colour convention (e.g. increases one accent, decreases a muted red).

## unPaper primitives (proven approach)

- a `.wf` plot box (`position:relative`, fixed height) with a baseline rule
- one absolutely-positioned `.wf-bar` per step (`.up` / `.down` / `.total`), its
  `bottom` + `height` = the running-total geometry in px → native shape (shape pass)
- thin absolute `.wf-conn` divs bridging each bar's end-level to the next → native shapes
- `.wf-val` (delta / total) and `.wf-cat` (category) labels → native text

No `data-unpaper-diagram` attribute and **no new converter pass** — the existing
shape + text passes do all the work, exactly as for the 2×2 matrix and org tree.

## Geometry (the running-total math the author must bake in)

Pick a scale `s` (px per unit) and a plot height `H`. Track the running total `c`,
starting at 0. For each element, left-to-right:

- **Start / End / subtotal** (baseline-anchored): `bottom = 0`, `height = value × s`.
  Set `c = value`.
- **Increase** `+d`: `bottom = c × s`, `height = d × s`; then `c += d`.
- **Decrease** `−d`: `c -= d`; then `bottom = c × s`, `height = d × s` (the bar spans
  the new lower total up to the old higher total).
- **Connector** into a step: a thin div at `bottom = c × s` (the total *before* the
  step), spanning the gap from the previous bar's right edge to this bar's left.

Because the positions are baked into the markup, a missing font can never re-flow
the chart, and the web converter (scripts OFF) sees the finished bars.

## Conversion (PROVEN — native, no new pass)

Each bar lowers to a native rectangle/rounded-rect with its own fill (up/down/total
colours stay editable), each connector to a native thin rectangle, and every label
to native text. Verified end to end: `test/corpus/waterfall.html`, **99.22%**, XML
asserts native `rect`/`roundRect` + the labels and forbids `<a:blip>`; the
consulting template's Value-bridge demo slide also converts native (21 text · 17
shapes · 0 flattened). No converter code was needed.

## Prompt fragment (compact — live)

> Waterfall/bridge (.wf block): walk a total from start to end through +/- steps.
> Position each bar by its running total in baked px (baseline at the plot bottom,
> scale ~2.5px/unit; .up green / .down red / .total dark); join steps with thin
> .wf-conn lines at the pre-step total; label each delta (+/-) and the start/end
> totals. Copy the Value-bridge slide's geometry and keep the plot within the slide
> so it converts to native shapes.

## HTML skeleton (illustrative — the proven markup, scale = 3px/unit)

```html
<div class="wf">                               <!-- position:relative; height:360px; baseline rule -->
  <!-- Start total 100 → baseline-anchored, height 300 -->
  <div class="wf-bar total" style="left:55px;bottom:0;height:300px"></div>
  <div class="wf-val" style="left:55px;bottom:304px">100</div>
  <div class="wf-cat" style="left:55px">Start</div>
  <!-- Price +12: 100→112, bottom 300 height 36; connector at the pre-step total (300) -->
  <div class="wf-conn" style="left:145px;width:90px;bottom:300px"></div>
  <div class="wf-bar up" style="left:235px;bottom:300px;height:36px"></div>
  <div class="wf-val" style="left:235px;bottom:340px">+12</div>
  <div class="wf-cat" style="left:235px">Price</div>
  <!-- …Mix −4, Volume +8, Cost −6… then End total 110 (baseline-anchored, height 330) -->
</div>
<p class="source">Source: margin bridge, FY23 → FY24.</p>
```

## Checks

- Start and end totals are explicit; every step shows its delta.
- Increases and decreases are visually distinct (`.up` / `.down` / `.total`).
- Bar positions are baked into the markup (no JS) so the running totals are exact
  and conversion-stable.
- Converts to native shapes + text (corpus-proven; live in the recommendation pack).
- The plot stays within the slide (no auto-fit shrink) — a scaled slide flattens.
