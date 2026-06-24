---
id: C20
family: consulting
name: Process flow
version: 1
status: shipped
unpaper_level: L2
supported_by_current_template: true
converter_ready: true
tokens_compact: 32
---

# C20 · Process flow

Show an ordered set of steps joined by arrows. Unlike a roadmap, there's no time
axis — it's the *sequence and dependency* that matter: diagnose → pilot → scale,
or intake → triage → resolve.

## Use when

- A process or method runs in a fixed order, step depending on the one before.
- 3–5 steps tell the whole story.

## Do not use when

- The steps are timed phases — use a roadmap (C18).
- Steps branch or loop heavily — a flow line oversimplifies; consider a diagram.

## Structure

- The `.flow` block: 3–5 `.node`s joined by `svg.arrow` connectors.
- Each node: a short kicker (`.ci`) and a one-word/one-line label (`<h3>`).
- Arrows in the accent colour, pointing forward.
- Keep labels to a couple of words — the flow reads at a glance.

## unPaper primitives

- `.flow` + `.node` → native rounded shapes + native text
- `svg.arrow` (uniform stroke) → native arrow freeform in the accent

## Conversion

Nodes lower to native shapes, labels to native text, and each arrow to a native
`custGeom` freeform (not a flattened picture) — the whole flow stays editable.
Native, no gap.

## Prompt fragment (compact)

> Process flow: 3-5 ordered steps joined by arrows using the flow block; one short
> label per step; arrows in the accent colour.

## HTML skeleton (illustrative)

```html
<div class="flow">
  <div class="node"><div class="ci">Step 1</div><h3>Diagnose</h3></div>
  <svg class="arrow" viewBox="0 0 64 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="2" y1="12" x2="54" y2="12"/><polyline points="46 5 56 12 46 19"/></svg>
  <div class="node"><div class="ci">Step 2</div><h3>Pilot</h3></div>
  <svg class="arrow" viewBox="0 0 64 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="2" y1="12" x2="54" y2="12"/><polyline points="46 5 56 12 46 19"/></svg>
  <div class="node"><div class="ci">Step 3</div><h3>Scale</h3></div>
</div>
```

## Checks

- 3–5 ordered steps, joined by forward arrows.
- One short label per step; no time axis (use C18 if there is one).
- It uses the `.flow` block so nodes + arrows convert native.
