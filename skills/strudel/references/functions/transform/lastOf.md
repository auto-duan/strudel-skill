---
name: lastOf
category: transform
signature: "lastOf(n: number, func: function): Pattern"
aliases: []
tags: [conditional, cycle, periodic, transform]
related: [firstOf, every, when]
source: https://strudel.cc/learn/conditional-modifiers/
status: verified
---

Applies the given function every n cycles, starting from the last cycle.

## Parameters
- `n` (number) — the cycle period; the function is applied once every `n` cycles.
- `func` (function) — the function to apply, e.g. `x => x.rev()`.

## Returns
Pattern — the pattern with `func` applied on the last cycle of each `n`-cycle group.

## Examples
```js
note("c3 d3 e3 g3").lastOf(4, x=>x.rev())
```

## Gotchas
- The function is applied starting from the LAST cycle of the group, in contrast to `firstOf` which starts from the first cycle.

## See also
- `firstOf` — same idea but applies from the first cycle.
- `every` — applies a function periodically.
