---
name: chooseCycles
category: transform
signature: "chooseCycles(...xs: any[]): Pattern"
aliases: [randcat]
tags: [random, selection, cycle, transform]
related: [choose, wchooseCycles, wchoose]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Picks one of the elements at random each cycle.

## Parameters
- `...xs` (any) — the values or patterns to choose from.

## Returns
Pattern — a pattern that plays one randomly chosen element per cycle.

## Examples
```js
// from official docs
chooseCycles("bd", "hh", "sd").s().fast(8)
```

## Gotchas
- Aliased as `randcat`.
- Unlike `choose`, the selection is made once per cycle rather than continuously.
- Each element has equal probability; use `wchooseCycles` to weight them.

## See also
- `choose` — continuous random selection
- `wchooseCycles` — weighted per-cycle pick (alias `wrandcat`)
