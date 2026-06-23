---
name: struct
category: transform
signature: "struct(pattern: string | Pattern): Pattern"
aliases: []
tags: [structure, rhythm, gate, binary]
related: [mask, euclid, reset, when]
source: https://strudel.cc/learn/conditional-modifiers/
status: verified
---

Applies the rhythmic structure of a binary pattern to the source pattern, replacing the source's own structure with new attack points.

## Parameters
- `pattern` (string | Pattern) — a binary pattern of `x` (trigger) and `~` (silence); only the structure matters, not the values.

## Returns
Pattern — the source pattern re-triggered according to the binary structure.

## Examples
```js
note("c,eb,g").struct("x ~ x ~ ~ x ~ x ~ ~ ~ x ~ x ~ ~").slow(2)
// chord triggered on the non-uniform Euclidean-like grid
```

## Gotchas
- `struct` replaces the source pattern's timing entirely; `mask` keeps the source timing and only silences events.
- An `x` in the binary pattern triggers the event; anything else (including `~`) produces silence.
- Values in the binary pattern are ignored — only the presence/absence of events counts.

## See also
- `mask` — keeps source structure, silences events where mask is 0/`~`.
- `euclid` — generates a Euclidean binary structure automatically.
- `when` — conditionally applies a function based on a binary pattern value.
