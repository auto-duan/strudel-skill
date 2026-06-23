---
name: when
category: transform
signature: "when(binary_pat: Pattern, func: function): Pattern"
aliases: []
tags: [conditional, binary, mask, transform]
related: [mask, struct, firstOf, lastOf]
source: https://strudel.cc/learn/conditional-modifiers/
status: verified
---

Applies the given function whenever the given pattern is in a true state.

## Parameters
- `binary_pat` (Pattern) — a binary (true/false, 1/0) pattern that gates when the function is applied.
- `func` (function) — the function applied while the binary pattern is true, e.g. `x => x.sub("5")`.

## Returns
Pattern — the pattern with `func` applied during the true regions of `binary_pat`.

## Examples
```js
"c3 eb3 g3".when("<0 1>/2", x=>x.sub("5")).note()
```

## Gotchas
- Only events that fall within a true region of the binary pattern are transformed; others pass through unchanged.

## See also
- `mask` — silences instead of transforming when the gate is 0.
- `struct` — applies a rhythmic structure to a pattern.
