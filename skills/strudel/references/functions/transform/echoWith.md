---
name: echoWith
category: transform
signature: "echoWith(times: number, time: number, func: (p: Pattern, n: number) => Pattern): Pattern"
aliases: [echowith, stutWith, stutwith]
tags: [accumulation, echo, feedback, delay, echoWith, transform]
related: [echo, off, stut]
source: https://strudel.cc/learn/accumulation/
status: verified
---

Superimpose and offset multiple times, applying the given function each time.

## Parameters
- `times` (number) — the number of repetitions
- `time` (number) — the time offset between each repetition (in cycles)
- `func` (function) — a function `(p, n) => Pattern` applied on each repetition, where `n` is the index of the repetition

## Returns
Pattern — the pattern superimposed and offset `times` times, with `func` applied at each step

## Examples
```js
"<0 [2 4]>"
.echoWith(4, 1/8, (p,n) => p.add(n*2))
.scale("C:minor").note()
```

## Gotchas
- The applied function receives both the pattern and the repetition index `n`, allowing per-repetition transformation.
- Aliases: `echowith`, `stutWith`, `stutwith`.

## See also
- `echo` — superimpose and offset while decreasing velocity instead of applying a function
- `off` — superimpose a single transformed copy delayed by a given time
