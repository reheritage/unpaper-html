---
id: C13
family: consulting
name: Issue tree
version: 1
status: shipped
unpaper_level: L2
supported_by_current_template: true
converter_ready: true
tokens_compact: 53
---

# C13 · Issue tree

Break a question into mutually exclusive, collectively exhaustive (MECE) branches.
A parent box poses the question; child boxes split it into non-overlapping parts
that together cover the whole. The structure *is* the argument: it proves you've
considered everything once.

## Use when

- You need to show the problem was decomposed rigorously, not cherry-picked.
- The decomposition itself reassures the audience (board, client, regulator).

## Do not use when

- The branches overlap or leave gaps — fix the logic before drawing it (a non-MECE
  tree is worse than none).
- It would run past two levels on one slide — split or summarise (it gets unreadable).

## Structure

- One **root** node (`.org-node.root`) stating the question.
- An `.org-children` row of 2–4 child `.org-node`s, each a branch; each may add a
  one-line gloss (`<p>`). Branches connect to the root via the block's own
  pseudo-element stem + bus + risers.
- Branches must be **mutually exclusive** (no overlap) and **collectively
  exhaustive** (nothing material left out).
- Keep to one or two levels deep on a single slide.

## unPaper primitives

- `.orgtree` + `.org-node.root` + `.org-children` + `.org-node` → native boxes
- the connector stem/bus/risers (absolute pseudo-elements) → native connector shapes

## Conversion

Boxes lower to native rounded shapes and the connectors to native lines/freeforms,
so the tree stays editable. Marked *partial* in the registry only because MECE
quality is a content judgement the converter can't enforce — the geometry converts
cleanly (the bus risers were tuned to meet the outer nodes; see the converter's
`.org-children::after` fix).

## Prompt fragment (compact)

> Issue tree: break the question into MECE branches (a parent box over 2-4 child
> boxes, each splitting further if needed) using the org/tree block; branches must
> be mutually exclusive and collectively exhaustive.

## HTML skeleton (illustrative)

```html
<div class="orgtree">
  <div class="org-node root"><div class="ci">The question</div><h4>How do we grow margin?</h4></div>
  <div class="org-children">
    <div class="org-node"><div class="ci">Branch A</div><h4>Sell more</h4><p>New logos, larger deals, less churn.</p></div>
    <div class="org-node"><div class="ci">Branch B</div><h4>Charge better</h4><p>Pricing, packaging, discount discipline.</p></div>
    <div class="org-node"><div class="ci">Branch C</div><h4>Spend less</h4><p>Cost to serve, automation, vendors.</p></div>
  </div>
</div>
```

## Checks

- The branches don't overlap and together cover the whole question (MECE).
- 2–4 branches; at most two levels on one slide.
- It uses the `.orgtree` block (so boxes + connectors convert native), not a flat SVG.
