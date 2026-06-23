---
name: voicing
category: tonal
signature: "voicing(): Pattern"
aliases: [voicings]
tags: [tonal, voicing, chord, harmony, voice-leading]
related: [chord, dict, anchor, mode, rootNotes, n]
source: https://strudel.cc/understand/voicings/
status: verified
---

Turns chord symbols (set via `chord`) into actual note events, automatically choosing voicings that produce smooth voice leading — minimizing pitch jumps between consecutive chords. A *voicing* is one arrangement of a chord's notes across octaves; *voice leading* is how those arrangements connect from chord to chord.

## Parameters
`voicing()` itself takes no positional arguments; its behavior is shaped by the surrounding context:
- `chord` — the chord symbols to voice (required).
- `dict` — which voicing dictionary to draw from (e.g. `'lefthand'`, `'ireal'`, `'house'`, or a custom one).
- `anchor` — reference note that voicings are chosen relative to.
- `mode` — strategy for aligning voicings to the anchor (`below`, `above`, `duck`, `root`).
- `n` — picks individual notes out of the chosen voicing.

> Note: `voicings('name')` is an older spelling that takes the dictionary name as an argument (`.voicings('lefthand')`). The modern form is `.dict('lefthand').voicing()`.

## Returns
Pattern — note events realizing each chord symbol as a chord (or, with `n`, as selected single notes).

## Examples
```js
// Automatic smooth voice leading over a progression
chord("<Am C D F Am E Am E>").voicing().room(.5)
```

```js
// n selects degrees of each voicing for an arpeggio
n("0 1 2 3").chord("<C Am F G>").voicing()
```

```js
// Older voicings('dict') spelling, used inside a stack
"<Am7!3 <Em7 E7b13 Em7 Ebm7b5>>".voicings('lefthand')
  .superimpose(x=>x.add(.04)).note().s('sawtooth').gain(.16).cutoff(500)
```

```js
// Reusing one chord context for comping + bass
chord("<C^7 A7b13 Dm7 G7>*2").dict('ireal').layer(
  x => x.struct("[~ x]*2").voicing(),
  x => n("0*4").set(x).mode("root:g2").voicing().s('sawtooth')
)
```

## Gotchas
- `voicing()` only works after a `chord` context is set (directly or via `.set(chords)`).
- The default anchor is the highest possible note; use `anchor`/`mode` to control register.
- Different dictionaries expose different chord-quality suffixes — an unknown symbol won't voice.
- `voicing` (no `s`) is the per-pattern operation; `voicings('name')` is the legacy arg-taking form.

## See also
- `chord` — sets the symbols that `voicing` renders.
- `dict` — chooses the voicing dictionary.
- `anchor` / `mode` — control voicing register and alignment.
- `rootNotes` — extract just the chord roots instead of full voicings.
