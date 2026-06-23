---
name: rootNotes
category: tonal
signature: "rootNotes(octave: number = 2): Pattern"
aliases: []
tags: [tonal, chord, root, bass, harmony]
related: [chord, voicing, note, anchor]
source: https://strudel.cc/learn/tonal/
status: verified
---

Turns chord symbols into the **root notes** of those chords in a given octave. Commonly used to build a bassline from the same chord progression that drives the harmony.

## Parameters
- `octave` (number, default `2`) — The octave in which to place each root note. Lower octaves (e.g. `2`) give bass-register roots.

## Returns
Pattern — a pattern of root-note values. Follow with `.note()` to make them sound as pitches.

## Examples
```js
// Roots of a ii–V–I-ish progression, two octave 2, as a bassline
"<C^7 A7b13 Dm7 G7>*2".rootNotes(2).note()
```

```js
// Pairing voiced chords with a root-note bass from the same symbols
let chords = chord("<Am C D F>")
$: chords.voicing().room(.5)
$: chords.rootNotes(2).note().s("sawtooth").gain(.5)
```

## Gotchas
- `rootNotes` outputs note values that still need `.note()` to be heard as pitch.
- It ignores chord quality (m, 7, b5, …) — only the root pitch class is used.
- Use a low `octave` (1–2) for bass; the default is `2`.
- For full harmony use `voicing` instead; `rootNotes` is the single-note (bass) counterpart.

## See also
- `chord` — provides the symbols whose roots are extracted.
- `voicing` — renders the full chord rather than just its root.
- `note` — needed to turn the extracted roots into audible pitches.
