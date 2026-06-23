---
name: never
category: transform
signature: "never(f: Pattern => Pattern): Pattern"
aliases: []
tags: [random, conditional, probability, transform]
related: [sometimesBy, almostNever, always]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Never applies the given function (0% chance) — leaves the pattern unchanged.

## Parameters
- `f` (function) — the transformation that would be applied, but never is.

## Returns
Pattern — the original pattern, unchanged.

## Examples
```js
// from official docs
s("hh*8").never(x=>x.speed("0.5"))
```

## Gotchas
- Shorthand for `sometimesBy(0, f)` — `f` is never called.
- Mainly useful as the endpoint of the probability family or when the probability is patterned.

## See also
- `always` — 100% chance (function is always applied)
- `almostNever` — 10% chance
