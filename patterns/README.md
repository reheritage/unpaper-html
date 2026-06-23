# unPaper HTML — Pattern Library

The **pattern library** is the professional slide *grammar* that sits on top of
the [unPaper HTML format](../spec.md): a small, open, versioned set of
**composable slide patterns** (layout logic) and **archetypes** (tone + visual
constraint), grouped by **deck family** (consulting, board, research, …).

The format (`spec.md`) says *how a slide converts*. The pattern library says
*which slide to reach for, when, and what a good one looks like* — the design
knowledge that turns a generic AI into a competent deck author.

## Why it lives here

Pattern knowledge is part of the standard's ecosystem, not one tool's UI:

- It is **open** (CC BY 4.0, like the spec) so anyone can read, target and adapt it.
- It is **forkable**: an organisation keeps its own house archetypes and layouts
  in a fork (`patterns/<org>/`), authored in the same open format.
- It is **independent of any generator**: patterns describe slides, not prompts
  for one assistant.

## How a generator uses it (the reliability rule)

A generator (such as an AI prompt builder) **compiles the selected patterns'
compact fragments into the prompt it gives the user's AI**. It **MUST NOT**
require the assistant to fetch this repository at run time — many assistants
cannot browse, and the format's promise is that it works on the AI you already
have, offline and private. Links to this library are **optional enrichment for
capable assistants and human readers**, never a dependency.

So each pattern carries two forms:

- a **rich Markdown doc** (this repo) — for humans and high-capability assistants;
- a **compact fragment** in [`index.json`](./index.json) — ~1–2 sentences a tool
  inlines into a prompt (budget: a whole selected pack ≈ 500–1,500 tokens).

## Layout

```
patterns/
  README.md            ← this file
  index.json           ← machine registry (families, archetypes, patterns, compact prompts)
  consulting/          ← the first deck family
    README.md
    archetypes/        ← neutral house styles (tone + visual language)
    layouts/           ← the C-series slide patterns (rich docs)
    packs/             ← deck-subtype pattern selections (e.g. recommendation-deck)
    examples/          ← complete conforming example decks
```

## Status

| Family | Status |
| --- | --- |
| `consulting` | in progress — 6 archetypes + a 13-pattern MVP (see [`consulting/`](./consulting)) |
| board, research, sales, training, … | planned |

## Conventions

- Patterns are **composable**, not whole decks. A deck is assembled from patterns.
- Semantic attributes use the `data-unpaper-` prefix (see `spec.md` §8).
- Archetypes use **neutral, descriptive names** — never the name of any firm.
  Public decks inform the *grammar*; this library copies no firm's template, logo,
  palette, or wording.
- A pattern is advertised to a generator only at the conformance level the
  converter actually supports. Patterns with a converter gap carry
  `"converter_ready": false` and are held back from prompt packs until ready.

## Stewardship & licence

Published and stewarded by **reHeritage GmbH**. Text licensed **CC BY 4.0** (see
[`../LICENSE`](../LICENSE)); the names "unPaper" / "unPaper HTML" are reHeritage
GmbH's, and the converter is a separate product.
