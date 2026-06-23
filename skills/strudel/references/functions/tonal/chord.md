---
name: chord
category: tonal
signature: "chord(symbol: string | Pattern): Pattern"
aliases: []
tags: [tonal, chord, harmony, voicing]
related: [voicing, rootNotes, anchor, mode, n]
source: https://strudel.cc/learn/tonal/
status: verified
---

Sets chord symbols on a pattern so that `.voicing()` (or `.rootNotes()`) can interpret them as harmonic content. When passed a pattern of strings directly, those strings are treated as chord symbols.

## Parameters
- `symbol` (string | Pattern) — A chord symbol string or pattern of strings. Each symbol is a root pitch followed by a chord quality suffix from the supported dictionary (e.g. `"C"`, `"Am"`, `"G7"`, `"Bb^7"`, `"Dm7b5"`). Alternation, polymeter, and other mini-notation syntax are supported.

## Returns
Pattern — a pattern carrying chord symbol events, ready to be passed to `.voicing()` or `.rootNotes()`.

## Examples
```js
// Basic four-chord progression voiced automatically
chord("<Am C D F Am E Am E>").voicing().room(.5)
```

```js
// Jazz blues in F: chords reused for melody, comping, and bassline
let chords = chord(`<
F7 Bb7 F7 [Cm7 F7]
Bb7 Bo F7 [Am7 D7]
Gm7 C7 [F7 D7] [Gm7 C7]
>`)
$: n("7 8 [10 9] 8").set(chords).voicing().dec(.2)
$: chords.struct("- x - x").voicing().room(.5)
$: n("0 - 1 -").set(chords).mode("root:g2").voicing()
```

```js
// chord() combined with n() to arpeggiate individual voicing notes
n("0 3 1 2").chord("<C <Fm Db>>").voicing()
  .clip("4 3 2 1").room(.5)
```

```js
// ireal-style dictionary with layer for comping + bass
chord("<C^7 A7b13 Dm7 G7>*2")
  .dict('ireal').layer(
    x => x.struct("[~ x]*2").voicing(),
    x => n("0*4").set(x).mode("root:g2").voicing()
      .s('sawtooth').cutoff("800:4:2")
  )
```

## Gotchas
- `chord` sets the harmonic context; `.voicing()` must follow to actually render notes.
- Supported chord quality suffixes are defined by the active voicing dictionary (default or custom via `.dict()`). See the [voicing dictionary reference](https://strudel.cc/understand/voicings/).
- Synonymous symbols: `"-"` = `"m"` (e.g. `C-7` = `Cm7`), `"^"` = `"M"` (e.g. `C^7` = `CM7`), `"+"` = `"aug"`.
- The root pitch is required before the quality suffix: `"D7#11"` not just `"7#11"`.
- There is no international standard for chord symbol notation; Strudel follows ireal-pro conventions.

## See also
- `voicing` — renders chord symbols as actual note events with smooth voice leading.
- `rootNotes` — extracts only the root note of each chord symbol.
- `anchor` — sets the reference pitch for voicing selection.
- `mode` — controls how the voicing aligns to the anchor (below/above/duck/root).
- `n` — when combined with `chord`, selects individual notes from the voiced chord.
