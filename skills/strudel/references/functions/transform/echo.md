---
name: echo
category: transform
signature: "echo(times: number, time: number, feedback: number): Pattern"
aliases: []
tags: [accumulation, echo, feedback, delay, transform]
related: [echoWith, stut, off]
source: https://strudel.cc/learn/accumulation/
status: verified
---

Superimpose and offset multiple times, gradually decreasing the velocity.

## Parameters
- `times` (number) — the number of echoes
- `time` (number) — the time offset between each echo (in cycles)
- `feedback` (number) — the velocity multiplier applied with each successive echo

## Returns
Pattern — the pattern superimposed and offset `times` times, with decreasing velocity

## Examples
```js
s("bd sd").echo(3, 1/6, .8)
```

## Gotchas
- The parameter order is `times, time, feedback`. The deprecated `stut` has the last two parameters flipped (`times, feedback, time`).

## See also
- `stut` — like `echo`, but the last 2 parameters are flipped (deprecated)
- `echoWith` — like `echo`, but applies a custom function on each repetition instead of decreasing velocity
