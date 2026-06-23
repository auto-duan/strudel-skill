---
name: chunkBack
category: transform
signature: "chunkBack(n: number, func: function): Pattern"
aliases: [chunkback]
tags: [conditional, cycle, parts, transform]
related: [chunk, fastChunk]
source: https://strudel.cc/learn/conditional-modifiers/
status: verified
---

Like `chunk`, but cycles through the parts in reverse order. Known as chunk' in tidalcycles.

## Parameters
- `n` (number) — the number of parts to divide the pattern into.
- `func` (function) — the function applied to one part per cycle, e.g. `x => x.add(7)`.

## Returns
Pattern — the pattern where each successive cycle applies `func` to a different part, in reverse order.

## Examples
```js
"0 1 2 3".chunkBack(4, x=>x.add(7)).scale("A:minor").note()
```

## Gotchas
- Synonym: `chunkback`.
- Known as `chunk'` in TidalCycles.

## See also
- `chunk` — cycles through parts in forward order.
- `fastChunk` — like chunk but source cycles aren't repeated per chunk set.
