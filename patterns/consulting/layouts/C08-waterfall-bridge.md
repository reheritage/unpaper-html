---
id: C08
family: consulting
name: Waterfall / bridge
version: 1
status: planned
unpaper_level: L3
supported_by_current_template: false
converter_ready: false
tokens_compact: 46
---

# C08 · Waterfall / bridge

> **Converter gap — not yet a sanctioned prompt pattern.** This doc is the spec
> for the next signature exhibit (build order #2 after C16, ledger experiment
> E-6). It is documented here for humans and capable assistants; it is held OUT of
> the compiled prompt packs until its converter quartet ships (§4.4 rule). Do not
> advertise it to models yet.

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

## unPaper primitives (planned)

- `data-unpaper-diagram="waterfall"` on a container carrying the step data
- inline `<svg>` bars as the visual encoding (renders + prints), lowered by the
  converter to a **parametric group of native shapes** (every bar movable, every
  label retypeable)

## Conversion (planned — the build target)

The converter will lower the waterfall to native rectangles (one per step,
positioned at its running-total baseline) plus native connector lines, in the deck
accent — the same freeform/native-shape approach as C16. Until that pass exists,
authoring a waterfall would flatten to a picture, so the pattern stays out of the
packs. Geometry to be designed against the user's source PDFs (§9).

## Prompt fragment (compact — held back)

> Waterfall/bridge: show how a total moves from a start value to an end value
> through +/- steps, with running-total bars and connectors; label each step's
> delta and the start/end totals.

## HTML skeleton (illustrative — provisional)

```html
<div data-unpaper-diagram="waterfall"
     data-start="100" data-end="118"
     data-steps='[{"label":"Price","delta":12},{"label":"Mix","delta":-4},{"label":"Cost","delta":10}]'>
  <!-- inline <svg> bars rendered to match; the converter reads the data-* contract -->
</div>
<p class="source">Source: margin bridge, FY23 → FY24.</p>
```

## Checks

- Start and end totals are explicit; every step shows its delta.
- Increases and decreases are visually distinct.
- **Not** to be emitted into a deck for conversion until the exhibit ships.
