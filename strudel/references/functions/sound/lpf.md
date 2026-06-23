---
name: lpf
category: sound
signature: "lpf(frequency: number | Pattern): Pattern"
aliases: [cutoff, ctf, lp]
tags: [sound, filter, lowpass, eq]
related: [lpq, hpf, bpf, lpenv, lpattack]
source: https://strudel.cc/learn/effects/
status: verified
---

Applies the cutoff frequency of the low-pass filter, removing frequencies above the cutoff.

## Parameters
- `frequency` (number | Pattern) — cutoff frequency in Hz, `0` to `20000`. Accepts an optional `:lpq` value (e.g. `lpf("1000:10")`).

## Returns
Pattern — the filtered pattern.

## Examples
```js
// from official docs
s("bd sd [~ bd] sd,hh*6").lpf("<4000 2000 1000 500 200 100>")
// sweeps the filter down, getting progressively darker
```

## Gotchas
- The colon form sets resonance too: `lpf("1000:10")` is `lpf(1000).lpq(10)`.
- Named `cutoff` historically; `lpf` is the most common form.

## See also
- `lpq` — resonance (Q) of the low-pass filter.
- `hpf` — high-pass filter (removes lows).
- `bpf` — band-pass filter.
