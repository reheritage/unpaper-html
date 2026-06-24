---
id: C18
family: consulting
name: Roadmap / phases
version: 1
status: shipped
unpaper_level: L2
supported_by_current_template: true
converter_ready: true
tokens_compact: 30
---

# C18 · Roadmap / phases

Sequence the work over time. A left-to-right timeline of 3–5 phases, each with a
date label and the one or two outcomes that define "done" for that phase. It
answers "what happens, in what order, and by when."

## Use when

- The plan unfolds in distinct phases with a clear order.
- The audience needs the sequence and the timing, not task-level detail.

## Do not use when

- Activities run in parallel across lanes — use a workplan / Gantt-lite (C19).
- There is no real time dimension — use a process flow (C20) instead.

## Structure

- The `.timeline` block: 3–5 `.tl-step`s laid out left to right.
- Each step: a `.when` date/label, an `<h3>` phase name, and 1–2 outcome lines.
- A consistent horizontal rail with dots (decorative, native on conversion).
- Phrase each phase as an outcome ("Prove it", "Scale it"), not an activity list.

## unPaper primitives

- `.timeline` + `.tl-step` + `.when` → native shapes (rail + dots) + native text

## Conversion

The rail and dots lower to native shapes and every label to native text — the
timeline stays movable and retypeable. Native, no gap.

## Prompt fragment (compact)

> Roadmap: 3-5 phases over time using the timeline block, each with a date/label
> and 1-2 outcomes, laid out left to right.

## HTML skeleton (illustrative)

```html
<div class="timeline">
  <div class="tl-step"><div class="when">0–3 months</div><h3>Prove it</h3><p>One pilot, one measurable win.</p></div>
  <div class="tl-step"><div class="when">3–9 months</div><h3>Build it</h3><p>Productise, hire the core team.</p></div>
  <div class="tl-step"><div class="when">9–18 months</div><h3>Scale it</h3><p>Roll out across regions.</p></div>
</div>
```

## Checks

- 3–5 phases, ordered left to right, each with a date/label.
- Phases are outcomes, not task dumps (1–2 lines each).
- It uses the `.timeline` block so the rail + dots convert native.
