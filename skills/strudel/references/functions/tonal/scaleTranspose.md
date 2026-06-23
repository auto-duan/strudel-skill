---
name: scaleTranspose
category: tonal
signature: "scaleTranspose(steps: number | Pattern): Pattern"
aliases: []
tags: [tonal, scale, transpose, diatonic, steps]
related: [scale, transpose, n]
source: https://strudel.cc/learn/tonal/
status: verified
---

Transposes notes by a number of steps within the currently active scale (set by `.scale()`), keeping the result diatonic (within the scale).

## Parameters
- `steps` (number | Pattern) — Number of scale steps to shift. Positive = up, negative = down. Accepts a pattern for a time-varying step count.

## Returns
Pattern — notes shifted diatonically by the given number of scale steps.

## Examples
```js
// Descend by scale steps each cycle, using bebop major scale
"[-8 [2,4,6]]*2"
  .scale('C4 bebop major')
  .scaleTranspose("<0 -1 -2 -3 -4 -5 -6 -4>*2")
  .note()
```

```js
// Combined with transpose for chromatic offset + diatonic walk
note("C1*16").transpose(irand(36)).scale('Cb2 major').scaleTranspose(3)
```

## Gotchas
- `scaleTranspose` requires a prior `.scale()` call in the chain; without it the scale context is undefined.
- Unlike `transpose` (chromatic semitones), `scaleTranspose` moves by diatonic steps — the interval size in semitones varies depending on the scale degree.
- A step of `7` in a 7-note scale wraps to the next octave on the same root degree.

## See also
- `scale` — must be called before `scaleTranspose` to establish the active scale.
- `transpose` — semitone-based transposition, ignores scale context.
- `n` — provides scale-degree numbers that `scale` maps before `scaleTranspose` acts.
