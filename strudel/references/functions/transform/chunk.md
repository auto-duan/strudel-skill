---
name: chunk
category: transform
signature: "chunk(n: number, func: function): Pattern"
aliases: [slowChunk, slowchunk]
tags: [conditional, cycle, parts, transform]
related: [chunkBack, fastChunk, every]
source: https://strudel.cc/learn/conditional-modifiers/
status: verified
---

Divides a pattern into a given number of parts, then cycles through those parts in turn, applying the given function to each part in turn.

## Parameters
- `n` (number) — the number of parts to divide the pattern into.
- `func` (function) — the function applied to one part per cycle, e.g. `x => x.add(7)`.

## Returns
Pattern — the pattern where each successive cycle applies `func` to a different part.

## Examples
```js
"0 1 2 3".chunk(4, x=>x.add(7)).scale("A:minor").note()
```

## Gotchas
- Synonyms: `slowChunk`, `slowchunk`.
- Cycles forward through the parts; use `chunkBack` to go in reverse order.

## See also
- `chunkBack` — like chunk but cycles through parts in reverse.
- `fastChunk` — like chunk but source cycles aren't repeated per chunk set.
