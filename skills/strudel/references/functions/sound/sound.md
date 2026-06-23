---
name: sound
category: sound
signature: "sound(source: string | Pattern): Pattern"
aliases: [s]
tags: [sound, synth, oscillator, sample, source]
related: [note, freq, n, vowel]
source: https://strudel.cc/learn/synths/
status: verified
---

Selects the sound source — either a synth oscillator waveform or a sample name.

## Parameters
- `source` (string | Pattern) — the oscillator type or sample name. Built-in synth waveforms include `"sine"`, `"sawtooth"`, `"square"`, `"triangle"`, plus noise sources `"white"`, `"pink"`, `"brown"`, `"crackle"`, and `"user"`.

## Returns
Pattern — the pattern using the chosen sound source.

## Examples
```js
// from official docs
note("c e g").sound("<sawtooth square triangle sine>")
// cycles the bass/lead through the four basic waveforms
```

## Gotchas
- `s` is the common alias: `s("sawtooth")` ≡ `sound("sawtooth")`.
- When `note` is set without a `sound`, the default oscillator is `triangle`.
- The same function selects samples (e.g. `s("bd")`) — strings that aren't a known waveform are looked up as sample names.

## See also
- `note` — set the pitch for the chosen oscillator.
- `n` — select a specific sample from a multi-sample bank.
- `vowel` — formant-filter a waveform to sound vowel-like.
