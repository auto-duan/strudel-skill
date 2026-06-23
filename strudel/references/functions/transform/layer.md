---
name: layer
category: transform
signature: "layer(...funcs: ((p: Pattern) => Pattern)[]): Pattern"
aliases: []
tags: [accumulation, layering, layer, transform]
related: [superimpose, off]
source: https://strudel.cc/learn/accumulation/
status: verified
---

Layers the result of the given function(s); like `superimpose`, but without the original pattern.

## Parameters
- `...funcs` (function) — one or more functions that each take a pattern and return a transformed pattern to be layered

## Returns
Pattern — a stack of the results of applying each function to the pattern, without the original

## Examples
```js
"<0 2 4 6 ~ 4 ~ 2 0!3 ~!5>*8"
  .layer(x=>x.add("0,2"))
  .scale('C minor').note()
```

## Gotchas
- Unlike `superimpose`, the original (untransformed) pattern is NOT included in the output.
- Each function operates on the original pattern.

## See also
- `superimpose` — like `layer`, but keeps the original pattern too
- `off` — layers a function result delayed by a given time
