---
name: saw
category: signal
signature: "saw: Pattern"
aliases: []
tags: [signal, continuous, oscillator, lfo, sawtooth]
related: [sine, isaw, tri, square]
source: https://strudel.cc/learn/signals/
status: verified
---

Sawtooth signal that ramps continuously between 0 and 1.

## Parameters
None — `saw` is a continuous signal (no arguments).

## Returns
Pattern — a continuous pattern producing values from 0 to 1.

## Examples
```js
note("<c3 [eb3,g3] g2 [g3,bb3]>*8").clip(saw.slow(2))
```
```js
n(saw.range(0,8).segment(8)).scale('C major')
```

## Gotchas
- As a continuous signal it must be sampled with `.segment(n)` to produce discrete events.
- Use `.range(min, max)` to remap the default 0..1 output to another range.
- A `saw2` variant exists that outputs over the -1..1 range instead of 0..1.

## See also
- `sine` — sine signal, same 0..1 default range
- `isaw` — inverse (descending) sawtooth
- `square` — square signal
