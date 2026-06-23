---
name: transpose
category: tonal
signature: "transpose(semitones: number | string | Pattern): Pattern"
aliases: []
tags: [tonal, pitch, semitones, interval, transpose]
related: [scale, scaleTranspose, note]
source: https://strudel.cc/learn/tonal/
status: verified
---

Transposes all notes in a pattern by the given number of semitones. Also accepts scientific interval notation (e.g. `"P5"`, `"M3"`).

## Parameters
- `semitones` (number | string | Pattern) — Number of semitones to shift up (positive) or down (negative). A pattern of numbers gives a time-varying transposition. Scientific interval notation strings are also accepted.

## Returns
Pattern — the pattern with every note shifted by the given interval.

## Examples
```js
// Transpose up by 7 semitones (a perfect fifth)
note("c3 e3 g3").transpose(7)
```

```js
// Pattern of transpositions — each cycle uses a different shift
note("c3 e3 g3").transpose("<0 2 4 7>")
```

```js
// Scientific interval notation
note("c3 e3 g3").transpose("P5")
```

```js
// Used with scale and scaleTranspose for modal melody
note("C1*16").transpose(irand(36)).scale('Cb2 major').scaleTranspose(3)
```

## Gotchas
- `transpose` works in chromatic semitones and is scale-agnostic; `scaleTranspose` moves by steps within the active scale.
- Accepts a pattern, so you can modulate transposition over time without extra nesting.
- When chained after `scale`, `transpose` still shifts by raw semitones, not scale steps.

## See also
- `scaleTranspose` — transposes by scale steps, staying diatonic.
- `scale` — sets the scale context used by `scaleTranspose`.
- `note` — the control that `transpose` operates on.
