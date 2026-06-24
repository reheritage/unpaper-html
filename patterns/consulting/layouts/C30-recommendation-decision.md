---
id: C30
family: consulting
name: Recommendation / decision
version: 1
status: shipped
unpaper_level: L2
supported_by_current_template: true
converter_ready: true
tokens_compact: 33
---

# C30 · Recommendation / decision

The close. State the ask in one bold line, give the 2–3 reasons that carry it, and
name the first concrete next step — with an owner and a date. A deck that ends on a
summary slide asks for nothing; this one asks for a decision.

## Use when

- The deck has built its case and now needs a decision or an approval.
- You can name a specific first action, not just "next steps to be defined."

## Do not use when

- The work is exploratory with no ask yet — close on findings, not a decision.
- The "next step" is vague — make it concrete first, or the slide rings hollow.

## Structure

- An **action title** that is the decision/ask in one line ("Approve the channel-
  partner entry and a €12M budget").
- The 2–3 reasons (a short list, or echo the exec-summary's points).
- The **first concrete next step**: what, who owns it, by when — ideally in a
  `.callout` so it stands out.
- Optionally a `.bignum` for the single number that anchors the ask (budget, target).

## unPaper primitives

- `h2.title` → native title · `<ol>`/`<li>` → native list
- `.callout` → native shape + text (the next step) · `.bignum` → native big-number text

## Conversion

Title, list, callout, and big number all convert to native text and shapes —
fully editable. No converter gap.

## Prompt fragment (compact)

> Recommendation close: the decision/ask in one bold line, the 2-3 reasons, and the
> first concrete next step with an owner and a date.

## HTML skeleton (illustrative)

```html
<h2 class="title">Approve the channel-partner entry and a €12M budget</h2>
<ol>
  <li>Reaches scale 18 months sooner than a direct build.</li>
  <li>One third of the capital at risk, with an option to acquire later.</li>
</ol>
<div class="callout">
  <div class="ci">First step</div>
  <p>Sign the partner LOI by 15 July — owner: Corp Dev.</p>
</div>
```

## Checks

- The ask is one explicit, bold line — a decision, not a summary.
- 2–3 reasons, no more.
- The next step names a what, an owner, and a date.
