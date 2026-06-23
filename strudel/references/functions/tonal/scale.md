---
name: scale
category: tonal
signature: "scale(name: string | Pattern): Pattern"
aliases: []
tags: [tonal, scale, notes, n, pitch]
related: [n, scaleTranspose, transpose, toScale]
source: https://strudel.cc/learn/tonal/
status: verified
---

Turns numbers into notes in a named scale (zero-indexed), or quantizes existing note names to the nearest pitch in the scale. Also sets the active scale context used by `scaleTranspose`.

## Parameters
- `name` (string | Pattern) — Scale descriptor in the form `root:type` (e.g. `"C:major"`, `"F#:minor"`, `"Cb2:major"`). The root defaults to octave 3 when no octave number is given. Replace spaces in multi-word scale names with colons (e.g. `"C:bebop:major"`). Accepts a pattern of strings for a changing scale.

## Returns
Pattern — notes mapped or quantized to the given scale.

## Examples
```js
// Ascending and descending major scale via scale degrees
n("0 2 4 6 4 2").scale("C:major")
```

```js
// Alternating major/minor scale every 2 cycles; plays piano samples
n("[0,7] 4 [2,7] 4")
  .scale("C:<major minor>/2")
  .s("piano")
```

```js
// Random scale degrees from the ritusen scale
n(rand.range(0,12).segment(8))
  .scale("C:ritusen")
  .s("piano")
```

```js
// scaleTranspose works in tandem with scale
note("C1*16").transpose(irand(36)).scale('Cb2 major').scaleTranspose(3)
```

```js
// Using a compound scale name (spaces replaced with colons)
n("[0 0] [1 2] [3 4] [5 6]").scale("C:major:blues")
```

## Gotchas
- `scale` is used together with `n` (scale-degree numbers), not with `note` (absolute note names). Calling `.scale()` on a pattern of note names quantizes them rather than mapping degrees.
- Negative numbers wrap backwards in the scale: `-1` is one step below the root (in the octave below).
- Numbers that overshoot the scale length are automatically octaved up; e.g. degree `7` in a 7-note scale gives the root one octave higher.
- The root defaults to octave **3** when no octave is specified (`"C:major"` → root is C3).
- Scale names with spaces must use `:` as a separator: `"bebop major"` → `"bebop:major"`.
- The scale set here is inherited by `scaleTranspose`; calling `scale` multiple times in a chain replaces the active context.
- Available scale types: see [tonaljs scale-type data](https://github.com/tonaljs/tonal/blob/main/packages/scale-type/data.ts).

## See also
- `n` — provides the scale-degree numbers that `scale` maps to pitches.
- `scaleTranspose` — transposes notes by scale steps within the active scale.
- `transpose` — transposes by fixed semitones or interval notation, ignoring the scale.
- `toScale` — (alias / related) maps values into scale pitches.
