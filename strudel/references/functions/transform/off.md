---
name: off
category: transform
signature: "off(time: number | Pattern, func: (p: Pattern) => Pattern): Pattern"
aliases: []
tags: [accumulation, layering, delay, off, transform]
related: [superimpose, echoWith, echo]
source: https://strudel.cc/learn/accumulation/
status: verified
---

Superimposes the function result on top of the original pattern, delayed by the given time.

## Parameters
- `time` (number | Pattern) — the amount of time to delay the superimposed copy by (in cycles)
- `func` (function) — a function that takes a pattern and returns the transformed pattern to superimpose

## Returns
Pattern — the original pattern stacked with a time-shifted, transformed copy

## Examples
```js
"c3 eb3 g3".off(1/8, x=>x.add(7)).note()
```

## Gotchas
- The offset copy is delayed in time, distinguishing `off` from `superimpose` (which layers without a time offset).
- `time` can itself be a pattern.

## See also
- `superimpose` — layer a transformed copy without a time offset
- `echoWith` — offset and transform multiple times in sequence
