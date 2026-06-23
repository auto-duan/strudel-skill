---
name: crush
category: sound
signature: "crush(depth: number | Pattern): Pattern"
aliases: []
tags: [sound, distortion, lofi, bitcrush, waveshaping]
related: [coarse, distort, shape]
source: https://strudel.cc/learn/effects/
status: verified
---

Bit crusher effect — reduces the bit depth of the signal for a lo-fi, digital-distortion sound.

## Parameters
- `depth` (number | Pattern) — bit depth, `1` to `16`. Lower values = more crushing.

## Returns
Pattern — the bit-crushed pattern.

## Examples
```js
// from official docs
s("<bd sd>,hh*3").fast(2).crush("<16 8 7 6 5 4 3 2>")
// gets progressively more lo-fi as bit depth drops
```

## Gotchas
- Counter-intuitively, *lower* numbers crush *more* (16 ≈ clean, 2 ≈ heavily destroyed).
- Reduces bit depth (quantization) rather than sample rate — that's `coarse`.

## See also
- `coarse` — sample-rate reduction.
- `distort` — wave-shaping distortion.
