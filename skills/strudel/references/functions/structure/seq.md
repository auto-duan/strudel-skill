---
name: seq
category: structure
signature: "seq(...items: Pattern[]): Pattern"
aliases: [fastcat]
tags: [combination, concatenation, cycle, sequence, fast]
related: [cat, slowcat, stack, stepcat, timeCat]
source: https://strudel.cc/learn/factories/
status: verified
---

Concatenates patterns sequentially, cramming all items into a single cycle (the fast/dense form of `cat`).

## Parameters
- `...items` (any) — the patterns (or values) to concatenate; each gets an equal time-slice within one cycle.

## Returns
Pattern — a pattern where all items play within one cycle, each occupying an equal fraction.

## Examples
```js
seq("e5", "b4", ["d5", "c5"]).note()
// equivalent to "e5 b4 [d5 c5]".note()
// all three play in a single cycle, equally divided
```

```js
// As a chained method
s("hh*4").seq(
  note("c4(5,8)")
)
```

## Gotchas
- `seq` / `fastcat` is the **fast** concatenation: N items each get 1/N of one cycle. This is the opposite of `cat`/`slowcat`, where each item gets a full cycle.
- Mini-notation equivalent: `"x y z"` (space-separated, no angle brackets).
- `seq("a","b","c")` and `cat("a","b","c")` produce the same note order but at very different tempos.
- Do not confuse with `stack`: `seq` serialises patterns in time; `stack` plays them simultaneously.

## See also
- `cat` / `slowcat` — same layout but each item takes **one full cycle** (slower).
- `stack` — plays all items **simultaneously** (same time, same length).
- `stepcat` — concatenates proportional to inferred step count, not a fixed equal slice.
