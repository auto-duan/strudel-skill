---
name: late
category: transform
signature: "late(cycles: number | Pattern): Pattern"
aliases: []
tags: [time, shift, nudge, offset]
related: [early, compress, zoom]
source: https://strudel.cc/learn/time-modifiers/
status: verified
---

Nudge a pattern to start later in time (equivalent of Tidal's ~> operator).

## Parameters
- `cycles` (number | Pattern) — amount of time (in cycles) to shift the pattern later

## Returns
Pattern — the time-shifted pattern

## Examples
```js
"bd ~".stack("hh ~".late(.1)).s()
```

## Gotchas
- The shift amount is in cycles, so `.late(.1)` nudges by a tenth of a cycle.
- `late` is the inverse of `early`.

## See also
- `early` — nudges a pattern earlier in time
