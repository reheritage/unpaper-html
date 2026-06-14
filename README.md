# unPaper HTML

**An open format for slide decks that are a print-ready web page and a faithful
description of an editable PowerPoint file at the same time.**

Write HTML to this format and it converts to *native* PowerPoint objects —
real text boxes, tables, charts with editable data, movable shapes — predictably,
by mechanical lowering rather than guesswork. The same file opens and prints
perfectly in any browser, makes no network requests, and needs no fonts, scripts
or assets it doesn't carry inside itself.

- **The specification:** [`spec.md`](./spec.md)
- **Examples:** [`examples/`](./examples) — complete, conforming decks
- **Conformance decks:** [`conformance/`](./conformance) — focused decks that each
  exercise one feature, usable as a test suite

## Why it exists

Every other HTML→PowerPoint tool parses arbitrary HTML and tries to recover meaning
from it; the result is lossy by nature. unPaper HTML inverts the problem: the
document is *written to a spec*, so a converter lowers a known intermediate
representation into native objects. The richer the contract a deck honours
(see the conformance levels in `spec.md`), the more of it arrives editable.

The format is meant to be **generated** — typically by an AI assistant — which is
why it can demand a precision a human author would find tedious. Nothing in it is
tied to any one generator or converter.

## Conformance levels (summary)

| Level | Guarantee |
| --- | --- |
| **L0** | Always produces a file; editability varies. |
| **L1** | Fixed-size, self-contained, renders without scripts → pixel-faithful. |
| **L2** | Semantic elements → native, editable text, lists, tables, shapes. |
| **L3** | Data visuals carry their data → editable chart data, regenerable decks. |

## Implementing the format

Anyone may build software that reads or writes unPaper HTML, for any purpose,
including commercial purposes, without permission or fee. A document declares the
version it targets with `<html data-unpaper="1">`; semantic data attributes use the
`data-unpaper-` prefix. Start from [`spec.md`](./spec.md) and validate against the
decks in [`conformance/`](./conformance).

## Stewardship & licence

The unPaper HTML format is published and stewarded by **reHeritage GmbH** (Berlin,
Germany) to keep conversions interoperable. "unPaper" and "unPaper HTML" are names
of reHeritage GmbH.

The specification text and the examples in this repository are licensed
**[CC BY 4.0](./LICENSE)** — implement, copy and adapt them with attribution.

The *unPaper converter* (the software that compiles this format to PowerPoint) is a
separate product of reHeritage GmbH and is **not** part of this repository.
