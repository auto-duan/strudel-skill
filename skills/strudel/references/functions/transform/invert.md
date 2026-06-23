---
name: invert
category: transform
signature: "invert(): Pattern"
aliases: [inv]
tags: [binary, struct, rhythm, flip]
related: [struct, mask, euclid]
source: https://strudel.cc/learn/conditional-modifiers/
status: verified
---

Swaps `1`s and `0`s in a binary pattern, flipping which steps are active and which are silent.

## Parameters
None.

## Returns
Pattern — the binary pattern with all `1`/`0` values toggled.

## Examples
```js
s("bd").struct("1 0 0 1 0 0 1 0".lastOf(4, invert))
// every 4 cycles the struct mask is inverted: formerly-silent steps now trigger
```

## Gotchas
- `invert` (alias `inv`) only makes sense on binary patterns used with `struct` or similar; applying it to pitched/timbral patterns won't produce a meaningful result.
- Often used inside `firstOf`/`lastOf` to alternate between two complementary rhythms.

## See also
- `struct` — applies a binary pattern as a rhythmic gate.
- `mask` — gates events using a binary pattern.
- `firstOf` / `lastOf` — apply a function every n cycles.
