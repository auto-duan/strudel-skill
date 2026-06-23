---
name: every
category: transform
signature: "every(n: number, f: Pattern => Pattern): Pattern"
aliases: []
tags: [conditional, cycle, periodic, transform]
related: [firstOf, lastOf, when, whenmod]
source: https://strudel.cc/learn/conditional-modifiers/
status: verified
---

Applies the given function every n cycles, starting from the first cycle.

## Parameters
- `n` (number) — the period in cycles; the function is applied once every `n` cycles.
- `f` (function) — the transformation applied on the triggering cycle, e.g. `rev()` or `x => x.fast(2)`.

## Returns
Pattern — the pattern with `f` applied on every nth cycle and unchanged otherwise.

## Examples
```js
// from official docs
n("0 <[1 2] 3> ~ 4").sound("tone").every(4, rev())
```

## Gotchas
- `every` takes a function; control patterns must be wrapped, e.g. `every(4, x => x.slow(2))`.
- `every(n, f)` is equivalent to `firstOf(n, f)` — it triggers on the first cycle of each n-cycle group.
- The function passed can itself be the result of another transform call, e.g. `every(4, slow(2))`.

## See also
- `firstOf` — same behavior; `every` is its common alias
- `lastOf` — applies the function on the last cycle of each n-cycle group
- `when` — applies a function gated by an explicit binary pattern
