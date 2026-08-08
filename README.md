# Seed Return Model

A single-page calculator for what a seed check actually returns once dilution, liquidation preference, and time are accounted for.

**Live:** https://felixmto.github.io/return-calculator/

## What it does

- **Priced round or SAFE** — model either structure. The SAFE mode handles both post-money and pre-money caps, and shows whether you convert at the cap or the discount.
- **Dilution** — compounds across future rounds rather than adding, which is the mistake most back-of-envelope math makes.
- **Liquidation preference** — 1x participating or non-participating, simplified to a single pari-passu class.
- **Time** — gross IRR alongside the multiple, because a 7x over seven years and a 7x over twelve are different outcomes.
- **Probabilities** — weight a set of outcomes to get an expected multiple, instead of a single point estimate that hides the odds.
- **Glossary** — every term has a `?` explainer. Declutter hides them all.

## Running it

No build step, no dependencies, no server. Open `index.html` in a browser.

The only external requests are Google Fonts, so it works offline apart from the typography.

## Editing

Everything lives in `index.html` — styles at the top, markup in the middle, logic in the `<script>` at the bottom.

Common changes:

| To change | Look for |
|---|---|
| Default values | `value="..."` on the inputs |
| Glossary text | the `GLOSSARY` object |
| Probability rows | the `OUTCOMES` array |
| Colors | the CSS variables in `:root` |
| The maths | `entry()`, `finalOwnership()`, `proceedsAt()`, `irr()` |

## Caveats

Gross of fees and carry. Initial check only — no follow-on reserves, so a position you defend through later rounds will show a better multiple here than it earns in reality. The preference waterfall assumes one class at 1x; real stacks have seniority, multiples, and participation caps. Management carve-outs, escrows, and anti-dilution are not modelled.

It's a thinking tool for screening, not a substitute for a real model on a deal you're actually doing.
