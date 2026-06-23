---
name: note
category: tonal
signature: "note(name: string | number | Pattern): Pattern"
aliases: []
tags: [tonal, note, pitch, control]
related: [n, scale, transpose, voicing]
source: https://strudel.cc/learn/tonal/
status: verified
---

Sets the pitch of events using absolute note names (e.g. `"c4"`, `"a#3"`, `"Bb2"`) or MIDI numbers. Unlike `n`, which is interpreted relative to a `scale` or `chord` context, `note` always names a concrete pitch.

## Parameters
- `name` (string | number | Pattern) — A note name in scientific pitch notation (`letter[accidental][octave]`, e.g. `"e4"`, `"f#5"`, `"Bb3"`), a MIDI number (e.g. `60` = C4), or a mini-notation pattern of either. When no octave is given, octave 3 is assumed.

## Returns
Pattern — a pattern carrying absolute pitch events.

## Examples
```js
// A simple melody from absolute note names
note("c e g b")
```

```js
// MIDI numbers also work
note("48 52 55 59")
```

```js
// note combined with transpose and a scale-quantizing step
note("c1*16").transpose(irand(36)).scale('Cb2 major').scaleTranspose(3)
```

```js
// Converting chord root notes into playable pitches
"<C^7 A7b13 Dm7 G7>*2".rootNotes(2).note()
```

## Gotchas
- Use `note` for **absolute** pitches and `n` for **scale-degree / chord-index** numbers. Mixing them up is the most common beginner error.
- A bare letter without octave defaults to octave 3 (`"c"` → C3).
- Accidentals: `#` raises, `b` lowers (`"c#4"`, `"db4"` are the same pitch).
- Many tonal helpers (`rootNotes`, `scaleTranspose`) produce numeric/relative output that needs a final `.note()` to become audible pitch.

## See also
- `n` — relative numbers interpreted in a scale or chord context.
- `scale` — quantizes notes or maps degrees within a named scale.
- `transpose` — shifts notes by semitones / interval notation.
- `voicing` — renders chord symbols into note events.
