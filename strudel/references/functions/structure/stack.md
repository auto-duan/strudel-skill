---
name: stack
category: structure
signature: "stack(...items: Pattern[]): Pattern"
aliases: [polyrhythm, pr]
tags: [combination, layering, polyphony, simultaneous]
related: [cat, seq, fastcat, polymeter, arrange]
source: https://strudel.cc/learn/factories/
status: verified
---

Plays all given patterns simultaneously, layered on top of each other at the same length.

## Parameters
- `...items` (any) — the patterns (or values) to layer; all play at the same time and at the same cycle length.

## Returns
Pattern — a single pattern that is the superimposition of all inputs.

## Examples
```js
stack("g3", "b3", ["e4", "d4"]).note()
// equivalent to "g3,b3,[e4 d4]".note()
// all notes sound together each cycle
```

```js
// As a chained method — layers a second pattern on top of an existing one
s("hh*4").stack(
  note("c4(5,8)")
)
```

```js
// Mixing different timbres — impossible to express with mini-notation comma alone
stack(
  note("c2 eb2(3,8)").s("sawtooth").cutoff(800),
  s("bd(5,8), hh*8")
)
```

## Gotchas
- `stack` plays patterns **simultaneously**; `cat` and `seq` play them **one after another**. This is the most important distinction.
- `stack` is aliased `polyrhythm` / `pr` but these names carry no extra semantics — they are pure synonyms.
- Mini-notation equivalent: `"x,y"` (comma-separated). The JS form is preferable when patterns use different audio types (e.g., mixing `.s()` with `.note()`).
- All items share the same cycle length — there is no automatic length adjustment. If lengths differ naturally, the cycle still resets together.

## See also
- `cat` / `slowcat` — serialises patterns, one full cycle each.
- `seq` / `fastcat` — serialises patterns, all within one cycle.
- `polymeter` / `pm` — aligns patterns by step count, allowing true polymetric looping.
