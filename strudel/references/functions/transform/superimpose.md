---
name: superimpose
category: transform
signature: "superimpose(...funcs: ((p: Pattern) => Pattern)[]): Pattern"
aliases: []
tags: [accumulation, layering, superimpose, transform]
related: [layer, off, echoWith]
source: https://strudel.cc/learn/accumulation/
status: verified
---

Superimposes the result of the given function(s) on top of the original pattern.

## Parameters
- `...funcs` (function) — one or more functions that each take a pattern and return a transformed pattern to be layered on top of the original

## Returns
Pattern — the original pattern stacked together with the results of applying each function to it

## Examples
```js
"<0 2 4 6 ~ 4 ~ 2 0!3 ~!5>*8"
  .superimpose(x=>x.add(2))
  .scale('C minor').note()
```

## Gotchas
- Unlike `layer`, the original pattern is kept in the output in addition to the transformed copies.
- Each function operates on the original pattern, not on the result of the previous function.

## See also
- `layer` — like `superimpose`, but without the original pattern
- `off` — superimposes a function result delayed by a given time
