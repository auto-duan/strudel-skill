---
name: hpf
category: sound
signature: "hpf(frequency: number | Pattern): Pattern"
aliases: [hp, hcutoff]
tags: [sound, filter, highpass, eq]
related: [hpq, lpf, bpf]
source: https://strudel.cc/learn/effects/
status: verified
---

Applies the cutoff frequency of the high-pass filter, removing frequencies below the cutoff.

## Parameters
- `frequency` (number | Pattern) — cutoff frequency in Hz, `0` to `20000`. Accepts an optional `:hpq` value (e.g. `hpf("1000:10")`).

## Returns
Pattern — the filtered pattern.

## Examples
```js
// from official docs
s("bd sd [~ bd] sd,hh*8").hpf("<4000 2000 1000 500 200 100>")
// removes more low end as the cutoff sweeps up
```

## Gotchas
- High-pass removes lows (opposite of `lpf`). A high cutoff thins the sound dramatically.
- The colon form sets resonance: `hpf("1000:10")` is `hpf(1000).hpq(10)`.

## See also
- `hpq` — resonance (Q) of the high-pass filter.
- `lpf` — low-pass filter (removes highs).
