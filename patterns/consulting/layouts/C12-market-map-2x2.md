---
id: C12
family: consulting
name: Market map / 2x2
version: 1
status: shipped
unpaper_level: L2
supported_by_current_template: true
converter_ready: true
tokens_compact: 44
---

# C12 · Market map / 2×2

Position a small set of options on two named axes. The 2×2 is the consulting
reflex for "where does each option sit, and which quadrant wins" — value vs.
effort, reach vs. fit, attractiveness vs. ability to win.

## Use when

- Two dimensions genuinely drive the decision and you can name them.
- You have 4–8 items to place, and where they fall is the insight.

## Do not use when

- One axis really decides it — use a ranked bar (C11).
- You have many criteria — use an option comparison table (C15) or a scorecard (C16).
- The axes are vague or chosen to flatter a predetermined answer.

## Structure

- The `.matrix.axes` block: four `.quad` cells, the priority cell marked `.hot`.
- Each quad carries a corner label (`.ql`), a short verb headline (`<h4>`), and one
  line of guidance (`<p>`).
- Three `.mxlabel` axis labels (the two axis names + the priority direction) — these
  stay native text.
- Plot 4–8 items; name the axes so a reader knows what high/low means.

## unPaper primitives

- `.matrix.axes` + four `.quad` (one `.hot`) → four native rounded shapes
- `.mxlabel` → native axis-label text · `.ql` / `h4` / `p` → native text

## Conversion

The four quadrants lower to native rounded shapes (the priority cell tinted), and
all labels to native text — movable and retypeable in PowerPoint. Native, no gap.

## Prompt fragment (compact)

> 2x2 matrix: position options on two named axes using the matrix block
> (.matrix.axes) with four quadrants, clear axis labels, and the priority cell
> marked; plot 4-8 items max.

## HTML skeleton (illustrative)

```html
<div class="matrix axes">
  <div class="quad hot"><div class="ql">High value · Low effort</div><h4>Do now</h4><p>The obvious wins — start here.</p></div>
  <div class="quad"><div class="ql">High value · High effort</div><h4>Plan</h4><p>Worth it, but resource it properly.</p></div>
  <div class="quad"><div class="ql">Low value · Low effort</div><h4>Maybe</h4><p>Fill-ins, only if idle capacity.</p></div>
  <div class="quad"><div class="ql">Low value · High effort</div><h4>Drop</h4><p>Politely decline.</p></div>
  <div class="mxlabel top">Higher value &uarr;</div>
  <div class="mxlabel low">Lower effort</div>
</div>
```

## Checks

- Both axes are explicitly named (not just "high/low").
- The priority quadrant is marked (`.hot`).
- 4–8 items placed; each quad has a verb headline.
