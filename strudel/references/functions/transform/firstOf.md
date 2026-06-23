---
name: firstOf
category: transform
signature: "firstOf(n: number, func: function): Pattern"
aliases: []
tags: [conditional, cycle, periodic, transform]
related: [lastOf, every, when]
source: https://strudel.cc/learn/conditional-modifiers/
status: verified
---

Applies the given function every n cycles, starting from the first cycle.

## Parameters
- `n` (number) — the cycle period; the function is applied once every `n` cycles.
- `func` (function) — the function to apply, e.g. `x => x.rev()`.

## Returns
Pattern — the pattern with `func` applied on the first cycle of each `n`-cycle group.

## Examples
```js
note("c3 d3 e3 g3").firstOf(4, x=>x.rev())
```

## Gotchas
- The function is applied starting from the FIRST cycle of the group, in contrast to `lastOf` which starts from the last cycle.

## See also
- `lastOf` — same idea but applies from the last cycle.
- `every` — applies a function periodically.
