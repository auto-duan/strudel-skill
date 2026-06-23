---
name: cat
category: structure
signature: "cat(...items: Pattern[]): Pattern"
aliases: [slowcat]
tags: [combination, concatenation, cycle, sequence]
related: [seq, fastcat, stack, stepcat, arrange, timeCat]
source: https://strudel.cc/learn/factories/
status: verified
---

Concatenates patterns one after another, where each item occupies exactly one cycle.

## Parameters
- `...items` (any) — the patterns (or values) to concatenate in order; each takes one full cycle.

## Returns
Pattern — a new pattern that cycles through each item in turn, one per cycle.

## Examples
```js
cat("e5", "b4", ["d5", "c5"]).note()
// equivalent to "<e5 b4 [d5 c5]>".note()
// plays e5 for cycle 1, b4 for cycle 2, [d5 c5] for cycle 3, then repeats
```

```js
// As a chained method — appends a second pattern to an existing one
s("hh*4").cat(
  note("c4(5,8)")
)
```

```js
// Combining chord stacks across four cycles
cat(
  stack("g3", "b3", "e4"),
  stack("a3", "c3", "e4"),
  stack("b3", "d3", "fs4"),
  stack("b3", "e4", "g4")
).note()
```

## Gotchas
- `cat` is the **slow** concatenation: N items → the full loop takes N cycles. This is the key distinction from `seq`/`fastcat`, which crams all items into one cycle.
- Mini-notation equivalent: `"<x y>"` (angle brackets).
- When used as a chained method (`.cat(other)`), it appends `other` as one additional cycle after the receiver.
- Do not confuse with `stack`: `cat` serialises patterns in time; `stack` plays them simultaneously.

## See also
- `seq` / `fastcat` — same as `cat` but all items fit into **one** cycle (faster).
- `stack` — plays all items **simultaneously** (same time, same length).
- `stepcat` / `timeCat` — concatenates proportional to step count, not cycle count.
- `arrange` — concatenates over multiple explicitly-counted cycles.
