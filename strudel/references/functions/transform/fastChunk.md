---
name: fastChunk
category: transform
signature: "fastChunk(n: number, func: function): Pattern"
aliases: [fastchunk]
tags: [conditional, cycle, parts, transform]
related: [chunk, chunkBack]
source: https://strudel.cc/learn/conditional-modifiers/
status: verified
---

Like `chunk`, but the cycles of the source pattern aren't repeated for each set of chunks.

## Parameters
- `n` (number) — the number of parts to divide the pattern into.
- `func` (function) — the function applied to one part per cycle, e.g. `x => x.color('red')`.

## Returns
Pattern — the pattern with `func` applied to a different part each cycle, without repeating source cycles per chunk set.

## Examples
```js
"<0 8> 1 2 3 4 5 6 7".scale("C2:major").note().fastChunk(4, x => x.color('red')).slow(2)
```

## Gotchas
- Synonym: `fastchunk`.
- Unlike `chunk`, the source pattern's cycles are not repeated for each set of chunks.

## See also
- `chunk` — repeats source cycles for each chunk set.
- `chunkBack` — cycles through parts in reverse order.
