---
id: C08
family: consulting
name: Waterfall / bridge
version: 1
status: converter-proven
unpaper_level: L3
supported_by_current_template: false
converter_ready: false
tokens_compact: 46
---

# C08 · Waterfall / bridge

> **Converter PROVEN native (2026-06-25); still held out of the live packs.** The
> converter renders a hand-authored waterfall as **100% native shapes + text** with
> NO new pass — the corpus deck `test/corpus/waterfall.html` scores 99.22% with
> zero objects flattened to a picture (every bar movable, every label retypeable).
> It works because the bars are positioned divs (→ native shapes via the shape
> pass), the connectors are thin divs (→ native shapes), and the labels are text.
> What remains before it enters the live prompt packs (and `converter_ready` flips
> true) is the **authoring teacher**: a template demo slide + a prompt how-to that
> shows a model how to compute the running-total pixel geometry, because the web
> converter runs with scripts OFF — so the bar positions must be baked into the
> markup, not computed by JS at load. Until that ships, the pattern stays gated.

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
asserts native `rect`/`roundRect` + the labels and forbids `<a:blip>`. The
remaining work is authoring guidance (a template demo slide + a how-to fragment),
not converter code.

## Prompt fragment (compact — held back until the authoring teacher ships)

> Waterfall/bridge: show how a total moves from a start value to an end value
> through +/- steps, with running-total bars and connectors; label each step's
> delta and the start/end totals.

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
- Converts to native shapes + text (corpus-proven); it is simply not yet
  auto-advertised in the live prompt packs (pending the authoring teacher).
