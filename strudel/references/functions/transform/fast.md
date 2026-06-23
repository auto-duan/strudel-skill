---
name: fast
category: transform
signature: "fast(factor: number | Pattern): Pattern"
aliases: [density]
tags: [time, speed, tempo]
related: [slow, ply, hurry]
source: https://strudel.cc/learn/time-modifiers/
status: verified
---

Speed up a pattern by the given factor (repeats more times within the same duration).

## Parameters
- `factor` (number | Pattern) — speed-up factor. Can be a pattern for time-varying speed, e.g. `"<1 2>"`.

## Returns
Pattern — the sped-up pattern.

## Examples
```js
// double the speed of the whole drum pattern
s("bd hh sd hh").fast(2)

// factor is itself a pattern: 1x on cycle one, 2x on cycle two
s("bd hh sd hh").fast("<1 2>")
```

## Gotchas
- `fast(2)` is equivalent to `*2` in mini-notation, but `fast` applies to the whole pattern while `*` applies locally inside the string.
- `fast` is repeat/fill; it does NOT change pitch — don't use it for transposition.
- A value < 1 slows down, equivalent to `slow(1/factor)`.

## See also
- `slow` — inverse operation, stretches the pattern.
- `ply` — repeats **each event** rather than the whole pattern.
- `hurry` — like fast, but also raises sample playback speed proportionally (pitch shift).
