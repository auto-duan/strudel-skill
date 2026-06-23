---
name: someCycles
category: transform
signature: "someCycles(f: Pattern => Pattern): Pattern"
aliases: [somecycles]
tags: [random, conditional, probability, cycle, transform]
related: [someCyclesBy, sometimes, every]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Applies the given function to whole cycles with a 50% chance.

## Parameters
- `f` (function) — the transformation to apply, e.g. `x => x.speed("0.5")`.

## Returns
Pattern — the pattern with `f` applied to about half of its cycles at random.

## Examples
```js
// from official docs
s("bd,hh*8").someCycles(x=>x.speed("0.5"))
```

## Gotchas
- Shorthand for `someCyclesBy(0.5, f)`.
- The decision is per cycle, so all events in a chosen cycle are transformed together.

## See also
- `someCyclesBy` — set an explicit probability
- `sometimes` — decides per event instead of per cycle
