---
name: almostAlways
category: transform
signature: "almostAlways(f: Pattern => Pattern): Pattern"
aliases: []
tags: [random, conditional, probability, transform]
related: [sometimesBy, often, always, almostNever]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Applies the given function to events nearly all the time (90% chance).

## Parameters
- `f` (function) — the transformation to apply, e.g. `x => x.speed("0.5")`.

## Returns
Pattern — the pattern with `f` applied to about nine tenths of its events at random.

## Examples
```js
// from official docs
s("hh*8").almostAlways(x=>x.speed("0.5"))
```

## Gotchas
- Shorthand for `sometimesBy(0.9, f)`.

## See also
- `often` — 75% chance
- `always` — 100% chance (function is always applied)
- `almostNever` — 10% chance
