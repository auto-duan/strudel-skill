---
name: vowel
category: sound
signature: "vowel(vowel: string | Pattern): Pattern"
aliases: []
tags: [sound, filter, formant, vocal]
related: [lpf, bpf, note]
source: https://strudel.cc/learn/effects/
status: verified
---

Formant filter that makes sounds resemble spoken vowels.

## Parameters
- `vowel` (string | Pattern) — vowel to apply. Recognized values: `a e i o u ae aa oe ue y uh un en an on`.

## Returns
Pattern — the pattern shaped by the formant filter.

## Examples
```js
// from official docs
note("[c2 <eb2 <g2 g1>>]*2").s('sawtooth').vowel("<a e i <o u>>")
// gives the sawtooth a talking, vowel-like timbre
```

## Gotchas
- Works best on harmonically rich sources (e.g. `sawtooth`, `square`); it has little to filter on a pure `sine`.
- Unrecognized vowel strings produce no formant effect.

## See also
- `bpf` — generic band-pass filtering.
- `lpf` — low-pass filtering.
