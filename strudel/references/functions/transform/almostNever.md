---
name: almostNever
category: transform
signature: "almostNever(f: Pattern => Pattern): Pattern"
aliases: []
tags: [random, conditional, probability, transform]
related: [sometimesBy, rarely, never, almostAlways]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Applies the given function to events very rarely (10% chance).

## Parameters
- `f` (function) — the transformation to apply, e.g. `x => x.speed("0.5")`.

## Returns
Pattern — the pattern with `f` applied to about one tenth of its events at random.

## Examples
```js
// from official docs
s("hh*8").almostNever(x=>x.speed("0.5"))
```

## Gotchas
- Shorthand for `sometimesBy(0.1, f)`.

## See also
- `rarely` — 25% chance
- `never` — 0% chance (function is never applied)
- `almostAlways` — 90% chance
