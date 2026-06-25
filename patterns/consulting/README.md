# Consulting / Strategy patterns

The first deck family: slides that **convince decision-makers through structured
analysis**. The recurring grammar across public consulting decks is remarkably
stable, and most of it converts to native unPaper objects (text, rules, tables,
charts, simple SVG diagrams, speaker notes).

## The family rule (every consulting deck)

- **Action titles.** Each slide title is a full-sentence *finding*, not a label
  ("Margin recovered as volume scaled", not "Margins"). Read top to bottom, the
  titles alone tell the whole story (the *horizontal logic* test).
- **One message per slide**, even when the slide is dense.
- **Answer first** (the pyramid principle): lead with the recommendation, then the
  grouped, MECE support, then next steps.
- **Evidence beside the claim**, and a **`Source:`** line under every chart or table.
- **Colour directs attention**, it does not decorate.

## Archetypes (house styles)

Neutral, descriptive names — never a firm's name. Pick one per deck; full docs in
[`archetypes/`](./archetypes).

| Archetype | Best for | Visual language |
| --- | --- | --- |
| Boardroom Classic | recommendations, value cases, market sizing, M&A | white, restrained, dense evidence, footnotes, blue/grey |
| Modern Insight | research readouts, thought leadership | open whitespace, simple charts, one accent, small multiples |
| Operator Redline | commercial strategy, market studies | strong top rule, sparing red accent, direct ranked charts |
| Research Bureau | public research, survey decks, institute reports | chapter navigation, full-bleed dividers, methodology |
| Systems Blueprint | transformation, operating models, PMO | modular boxes, swimlanes, capability maps, diagrams |
| Executive Brief | leadership updates, macro briefings, board memos | blue/neutral accent, memo slides, exec summaries, dividers |

## Patterns (the C-series)

Composable slide layouts — the consulting equivalent of the "30 standard contract
types." The machine registry ([`../index.json`](../index.json)) carries each
pattern's support level, MVP flag, and compact prompt fragment; rich docs live in
[`layouts/`](./layouts). Support: native · partial · gap (needs converter work).

## The MVP (a recommendation deck)

C02 executive summary · C05 action-title evidence · C06 single chart proof ·
C07 small multiples · C08 waterfall · C12 market map / 2×2 · C13 issue tree ·
C15 option comparison · **C16 scorecard / Harvey balls** · C18 roadmap ·
C20 process flow · C23 initiative portfolio · C30 recommendation.

All 13 now have a rich doc in [`layouts/`](./layouts). **C16 has shipped**
end-to-end (native ring + pie freeforms; see
[`layouts/C16-scorecard-harvey-balls.md`](./layouts/C16-scorecard-harvey-balls.md)).
**C08 waterfall** is now **converter-proven** — it renders as 100% native shapes +
text with no new pass (corpus `waterfall.html`, 99.22%; see
[`layouts/C08-waterfall-bridge.md`](./layouts/C08-waterfall-bridge.md)) — but it
stays held out of the live prompt packs until the authoring teacher (a template
demo slide + a how-to that bakes the running-total geometry) ships.

## Subtype packs (planned, [`packs/`](./packs))

`recommendation-deck` · `market-study` · `transformation-roadmap` ·
`research-readout` · `executive-briefing` — each selects ~5–12 of the patterns
above so a generator inlines only what the deck needs.

## What not to do

- Don't build a full HTML template per archetype; archetypes are tone + constraint.
- Don't copy any firm's palette, logo, slide master, or name.
- Don't require AI browsing — compile the compact fragments into the prompt.
- Don't make every slide structurally different. Repeated structure reads as
  authority in a consulting deck.

## Stewardship & licence

reHeritage GmbH; text licensed **CC BY 4.0** (see [`../../LICENSE`](../../LICENSE)).
