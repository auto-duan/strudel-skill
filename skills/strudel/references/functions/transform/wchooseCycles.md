---
name: wchooseCycles
category: transform
signature: "wchooseCycles(...pairs: [any, number][]): Pattern"
aliases: [wrandcat]
tags: [random, selection, weighted, cycle, transform]
related: [chooseCycles, wchoose, choose]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Picks one of the elements at random each cycle, by giving a probability (weight) to each element.

## Parameters
- `...pairs` (array) — each argument is a `[value, weight]` array; higher weights are chosen more often.

## Returns
Pattern — a pattern that plays one weighted-random element per cycle.

## Examples
```js
// from official docs
wchooseCycles(["bd",10], ["hh",1], ["sd",1]).s().fast(8)
```

## Gotchas
- Aliased as `wrandcat`.
- Each argument must be a `[value, weight]` pair.
- Selection is made once per cycle; use `wchoose` for a continuous weighted selection.

## See also
- `chooseCycles` — unweighted per-cycle pick (alias `randcat`)
- `wchoose` — continuous weighted selection
