---
name: n
category: tonal
signature: "n(index: number | Pattern): Pattern"
aliases: []
tags: [tonal, n, scale, index, degree, sample]
related: [scale, chord, voicing, note]
source: https://strudel.cc/learn/tonal/
status: verified
---

Sets a numeric index on events. Its meaning depends on the surrounding context: with `scale` it selects a **scale degree** (zero-indexed), with `chord`/`voicing` it selects which **note of the voicing** to play, and with a sample bank it selects which **sample variant** to use.

## Parameters
- `index` (number | Pattern) — A number or mini-notation pattern of numbers. Zero-indexed. Negative numbers and numbers beyond the scale/voicing length wrap and octave-shift automatically.

## Returns
Pattern — a pattern carrying numeric index events, to be resolved by a following `scale`, `chord`/`voicing`, or sample context.

## Examples
```js
// Scale degrees mapped to pitches by scale()
n("0 2 4 6 4 2").scale("C:major")
```

```js
// Random scale degrees
n(rand.range(0,12).segment(8)).scale("C:ritusen").s("piano")
```

```js
// n selects individual notes out of a chord voicing
n("0 3 1 2").chord("<C <Fm Db>>").voicing().clip("4 3 2 1").room(.5)
```

```js
// n drives a melody over a shared chord context
let chords = chord("<F7 Bb7 F7 Cm7>")
n("7 8 [10 9] 8").set(chords).voicing().dec(.2)
```

## Gotchas
- `n` is **relative**; it needs a `scale`, `chord`/`voicing`, or sample-bank context to mean anything pitched. For absolute pitch use `note`.
- In a scale context, degree `7` in a 7-note scale yields the root one octave up; `-1` is one step below the root.
- In a sample context (e.g. `s("jazz").n("0 1 2")`), `n` chooses the sample index within the bank, not a pitch.
- With `chord`, `n` indexes into the rendered voicing — combine with `.set(chords)` to share one harmonic context across layers.

## See also
- `scale` — interprets `n` as scale degrees.
- `chord` / `voicing` — interpret `n` as indices into a voicing.
- `note` — absolute pitch alternative to `n`.
