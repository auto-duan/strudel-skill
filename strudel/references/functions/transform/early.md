---
name: early
category: transform
signature: "early(cycles: number | Pattern): Pattern"
aliases: []
tags: [time, shift, nudge, offset]
related: [late, compress, zoom]
source: https://strudel.cc/learn/time-modifiers/
status: verified
---

Nudge a pattern to start earlier in time (equivalent of Tidal's <~ operator).

## Parameters
- `cycles` (number | Pattern) — amount of time (in cycles) to shift the pattern earlier

## Returns
Pattern — the time-shifted pattern

## Examples
```js
"bd ~".stack("hh ~".early(.1)).s()
```

## Gotchas
- The shift amount is in cycles, so `.early(.1)` nudges by a tenth of a cycle.
- `early` is the inverse of `late`.

## See also
- `late` — nudges a pattern later in time
