---
name: dict
category: tonal
signature: "dict(name: string): Pattern"
aliases: []
tags: [tonal, voicing, dictionary, chord, harmony]
related: [voicing, chord, anchor, mode]
source: https://strudel.cc/understand/voicings/
status: verified
---

Selects which **voicing dictionary** `voicing()` draws from. A dictionary maps each chord-quality suffix to one or more candidate voicings (expressed as interval distances). Built-in dictionaries include `'lefthand'` and `'ireal'`; you can register your own with `addVoicings()`.

## Parameters
- `name` (string) — The name of a registered voicing dictionary (e.g. `'lefthand'`, `'ireal'`, `'house'`, or a custom name passed to `addVoicings`).

## Returns
Pattern — chord events bound to the chosen dictionary, resolved by a following `voicing()`.

## Examples
```js
// Use the ireal-pro style dictionary
chord("<C^7 A7b13 Dm7 G7>*2").dict('ireal').voicing()
```

```js
// A custom dictionary, then anchored and voiced
chord("<Am C D F Am E Am E>").dict('house').anchor(66).voicing().room(.5)
```

```js
// Register a custom dictionary first, then use it
addVoicings('house', {
  '': ['7 12 16', '0 7 16', '4 7 12'],
  'm': ['0 3 7']
})
chord("<C Am>").dict('house').voicing()
```

## Gotchas
- The active dictionary defines which chord-quality suffixes are valid; symbols absent from it won't voice.
- `addVoicings(name, map)` registers a dictionary before `dict(name)` can reference it. Each value is an array of voicings, each a space-separated list of semitone offsets from the root.
- An empty key `''` in a dictionary is the default (major-triad) quality; `'m'` is minor, etc.
- Without `dict`, `voicing()` uses Strudel's built-in default dictionary.

## See also
- `voicing` — consumes the selected dictionary.
- `chord` — provides the symbols to voice.
- `anchor` / `mode` — further refine voicing selection and register.
