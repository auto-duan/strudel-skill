---
title: Euclidean Rhythm
tags: [rhythm, drums, euclidean, mini-notation]
description: Distributes a number of hits as evenly as possible across a number of steps using Euclidean notation.
source: https://strudel.cc/learn/getting-started/
---
# Euclidean Rhythm

Euclidean rhythms spread `n` onsets as evenly as possible over `k` steps — the
basis of countless world and electronic grooves. In mini-notation this is written
`sound(n,k)` or `sound(n,k,rotation)`.

## Pattern
```js
s("bd,[~ <sd!3 sd(3,4,2)>],hh*8").speed(perlin.range(.7,.9))
```

## What it demonstrates
- Euclidean notation `(3,4,2)` = 3 hits over 4 steps, rotated by 2.
- `,` inside one mini-notation string stacks layers (kick, snare, hats) into a polyrhythm.
- `*8` repeats `hh` eight times per cycle for a steady hat layer.
- `<sd!3 ...>` alternates per cycle; `!3` repeats the snare three cycles before the Euclidean variant.
- `.speed(perlin.range(.7,.9))` adds subtle organic pitch/tempo movement to the samples.

> Illustrative note: the layered snare line is taken from the official getting-started
> example; a barebones Euclidean groove is simply `s("bd(3,8)")`.
