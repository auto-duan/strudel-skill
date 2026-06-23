---
name: shape
category: sound
signature: "shape(amount: number | Pattern): Pattern"
aliases: []
tags: [sound, distortion, waveshaping, effect]
related: [distort, crush, coarse]
source: https://strudel.cc/learn/effects/
status: verified
---

Waveshape distortion applied to the signal. In Strudel's signal chain, `shape`
(Waveshape distortion) is a distinct stage that runs **before** `distort`
(Normal distortion) — the two are separate effects, not aliases.

## Parameters
- `amount` (number | Pattern) — waveshaping distortion amount. Small positive
  values (around `0` to `1`) give moderate shaping; larger values push harder.
  Can be a pattern for time-varying distortion, e.g. `"<0 .2 .4 .6>"`.

## Returns
Pattern — the waveshaped (distorted) pattern.

## Examples
```js
// increasing waveshape distortion across cycles
s("bd sd [~ bd] sd,hh*8").shape("<0 .2 .4 .6>")
```

## Gotchas
- `shape` (Waveshape distortion) and `distort` / `dist` (Normal distortion) are
  **two different effects** in the official signal chain. `shape` runs first.
  Use `distort` when you want the louder, more aggressive waveshaper documented
  with its own `distortion:volume:type` array syntax.
- Like most local effects, `shape` is single-use per orbit/event: repeating it in
  one chain overrides the earlier value rather than stacking.
- It can get loud quickly — ramp the amount up gradually.

## See also
- `distort` — Normal distortion, the heavier waveshaper with postgain/type options.
- `crush` — bit-depth reduction (bit crusher).
- `coarse` — sample-rate reduction (lo-fi).
