---
title: Scale-Degree Melody
tags: [melody, scale, tonal, n]
description: Turns plain numbers into an in-key melody by mapping scale degrees through scale().
source: https://strudel.cc/learn/tonal/
---
# Scale-Degree Melody

Writing melodies by absolute note name is error-prone. Instead, write scale
*degrees* as numbers with `n()` and let `scale()` map them to pitches that always
stay in key — change the scale and the whole melody re-keys itself.

## Pattern
```js
n("0 2 4 6 4 2").scale("C:major")
```

A randomized variant over a pentatonic-style scale, played on piano:
```js
n(rand.range(0,12).segment(8)).scale("C:ritusen").s("piano")
```

## What it demonstrates
- `n()` supplies zero-indexed scale degrees; `scale("root:type")` resolves them to pitches.
- Degrees beyond the scale length octave-shift automatically (`7` → root, one octave up).
- Swapping `"C:major"` for `"C:minor"` or `"C:ritusen"` re-keys the same number sequence.
- `rand.range(0,12).segment(8)` generates 8 random degrees per cycle for generative melodies.
- `s("piano")` selects the instrument; pitch comes from the `n`/`scale` pair.
