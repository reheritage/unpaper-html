---
id: C02
family: consulting
name: Executive summary
version: 1
status: shipped
unpaper_level: L2
supported_by_current_template: true
converter_ready: true
tokens_compact: 47
---

# C02 · Executive summary

State the answer first. One slide that gives a busy reader the whole argument:
the recommendation in a single bold line, then the 3–5 findings that defend it.
Everything after this slide is supporting evidence for what it claims.

## Use when

- The audience is senior and time-poor — they want the conclusion before the build-up.
- The deck makes a single recommendation that a handful of reasons support.
- You want the storyline auditable: each summary point maps to a later evidence slide.

## Do not use when

- There is no single answer yet (the deck explores rather than recommends) — use an
  agenda/storyline (C03) instead.
- The reasons are themselves numbers worth charting — lead with C06/C10.

## Structure

- An **action title** (`h2.title`) that is the recommendation written as a full
  sentence ("Enter Germany through a channel partner, not a direct build").
- The recommendation restated as one bold opening line, then **3–5 supporting
  findings** as a numbered list (`<ol>`) — or a KPI stat row (`.stats`) when the
  reasons are numeric anchors.
- Optionally a `data-unpaper-lay="2l"` split: the recommendation + reasons on the
  wide left, a single proof figure or stat row on the narrow right.
- Keep it to one screen — if the reasons don't fit, the recommendation is too broad.

## unPaper primitives

- `h2.title` → native title text
- `<ol><li>` → native numbered list · or `.stats` → native stat shapes + text
- optional `data-unpaper-lay="2l"` two-column grammar

## Conversion

Every part is native and editable: the title and list become native text boxes,
a stat row becomes native shapes + text. No converter gap — this is layout
discipline, not a new exhibit.

## Prompt fragment (compact)

> Executive summary: open with the recommendation in one bold line, then 3-5
> supporting findings as a numbered list or a stat row. State the answer first;
> the rest of the deck defends it.

## HTML skeleton (illustrative)

```html
<h2 class="title">Enter Germany through a channel partner, not a direct build</h2>
<p class="lede">A partner reaches scale 18 months sooner at a third of the risk.</p>
<ol>
  <li>The direct build needs €40M and three years to reach break-even.</li>
  <li>Two qualified partners already cover 60% of the target accounts.</li>
  <li>A partner-first entry preserves the option to acquire later.</li>
</ol>
<p class="source">Source: market model, internal cost base, Q1 2026.</p>
```

## Checks

- The title is the recommendation as a sentence, not a topic label.
- There are 3–5 reasons, each a claim the deck later proves — not background.
- It fits one slide; nothing reflows or overflows the box.
