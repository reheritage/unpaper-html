---
id: C23
family: consulting
name: Initiative portfolio
version: 1
status: shipped
unpaper_level: L2
supported_by_current_template: true
converter_ready: true
tokens_compact: 30
---

# C23 · Initiative portfolio

Sort a set of initiatives by their value and their cost so the audience sees where
to start. Either plot them on an impact × effort 2×2, or list them as status-tagged
cards — and mark the quick wins (high impact, low effort) explicitly.

## Use when

- You have ~6–8 initiatives and need to prioritise them, not just list them.
- The decision is "which first" — and impact vs. effort (or status) is what sorts them.

## Do not use when

- There's only one initiative — it's a recommendation (C30), not a portfolio.
- You're comparing options on many criteria — use a table (C15) or scorecard (C16).

## Structure

Two valid forms:

1. **2×2** — reuse the `.matrix.axes` block (impact × effort), place each initiative
   in a quadrant, mark the quick-win cell `.hot`.
2. **Status cards** — a `.cards` grid, each card a `.ci` status tag (On track /
   At risk / Not started), a headline, and a line of detail.

Either way, the **quick wins are visibly flagged**.

## unPaper primitives

- `.matrix.axes` + `.quad` → native shapes (2×2 form)
- `.cards` + `.ci` → native card shapes + status tags (cards form)

## Conversion

Both forms are native: quads and cards lower to native rounded shapes, tags and
text to native text. No converter gap.

## Prompt fragment (compact)

> Initiative portfolio: sort ~6-8 initiatives by impact x effort on a 2x2, or as
> status-tagged cards; mark the quick wins.

## HTML skeleton (illustrative — status-cards form)

```html
<div class="cards">
  <div class="card"><div class="ci">Quick win</div><h3>Self-service refunds</h3><p>High impact, ships in a sprint.</p></div>
  <div class="card"><div class="ci">On track</div><h3>Pricing refresh</h3><p>In flight, value lands in Q3.</p></div>
  <div class="card"><div class="ci">At risk</div><h3>Vendor consolidation</h3><p>Blocked on a contract review.</p></div>
</div>
```

## Checks

- ~6–8 initiatives, sorted (not an unranked list).
- Quick wins are explicitly marked.
- Uses the 2×2 (`.matrix.axes`) or cards (`.cards`) block so it converts native.
