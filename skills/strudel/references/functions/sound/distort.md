---
name: distort
category: sound
signature: "distort(amount: number | Pattern): Pattern"
aliases: [dist]
tags: [sound, distortion, waveshaping, effect]
related: [shape, crush, coarse]
source: https://strudel.cc/learn/effects/
status: verified
---

Wave-shaping distortion. CAUTION: it can get loud.

## Parameters
- `amount` (number | Pattern) — distortion amount (typically `0` to `10`+). Accepts an optional `:volume` (and `:type`) suffix, e.g. `distort("10:.5")` to compensate the output level.

## Returns
Pattern — the distorted pattern.

## Examples
```js
// from official docs
s("bd sd [~ bd] sd,hh*8").distort("<0 2 3 10:.5>")
// increasing distortion; the last step also sets a post-volume of .5
```

## Gotchas
- Distortion adds gain — high amounts get loud fast. Use the `:volume` suffix (e.g. `10:.5`) to tame the output.
- The colon form is `distort("amount:volume")`.

## See also
- `shape` — an older/related distortion control (see its note on verification).
- `crush` / `coarse` — digital lo-fi degradation effects.
