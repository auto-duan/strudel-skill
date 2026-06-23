---
name: coarse
category: sound
signature: "coarse(factor: number | Pattern): Pattern"
aliases: []
tags: [sound, distortion, lofi, samplerate, waveshaping]
related: [crush, distort, shape]
source: https://strudel.cc/learn/effects/
status: verified
---

Fake-resampling that lowers the effective sample rate for a lo-fi, gritty sound.

## Parameters
- `factor` (number | Pattern) — resampling factor, `1` and up. `1` = no effect; higher = more degradation.

## Returns
Pattern — the pattern with reduced sample rate.

## Examples
```js
// from official docs
s("bd sd [~ bd] sd,hh*8").coarse("<1 4 8 16 32>")
// progressively cruder, more aliased sound
```

## Gotchas
- `coarse(1)` is a no-op; the effect only appears at values above 1.
- Reduces sample rate (aliasing) rather than bit depth — that's `crush`.

## See also
- `crush` — bit-depth reduction (bit crusher).
- `distort` — wave-shaping distortion.
