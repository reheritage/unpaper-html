# Conformance decks

Each file here is a small, self-contained unPaper HTML document that exercises one
feature of the format. Together they act as a test suite: an implementation that
converts these correctly handles the corresponding parts of the specification.

| Deck | Exercises | Spec |
| --- | --- | --- |
| `chart.html` | `data-unpaper-chart` → native, data-editable chart | §6.1 (L3) |
| `table.html` | a real `<table>` → native editable table | §5 (L2) |
| `bullets.html` | `<ul>`/`<ol>` → real bullet paragraphs | §5 (L2) |
| `notes-and-links.html` | `<aside class="notes">` / `data-unpaper-notes` and `<a href>` | §5, §6.2 |
| `icons.html` | inline `<svg>` → vector / freeform shapes | §5 (L2) |
| `gradients.html` | CSS gradients & shapes → native movable shapes | §5 (L2) |

Each deck is itself a valid Level-1 document (§4): one self-contained file, fixed
slide size, renders with scripts disabled. To check an implementation, convert a
deck and confirm the named feature arrives as the native object the spec requires.
