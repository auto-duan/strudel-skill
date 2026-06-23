---
name: mask
category: transform
signature: "mask(pattern: string | Pattern): Pattern"
aliases: []
tags: [gate, mute, silence, binary, conditional]
related: [struct, when, hush, reset]
source: https://strudel.cc/learn/conditional-modifiers/
status: verified
---

Gates the source pattern using a binary pattern: events are kept when the mask is truthy (`1`, `x`) and silenced when it is falsy (`0`, `~`).

## Parameters
- `pattern` (string | Pattern) — a binary pattern; `0` or `~` produces silence, any other value passes the event through.

## Returns
Pattern — source pattern with events silenced wherever the mask is `0` or `~`.

## Examples
```js
note("c [eb,g] d [eb,g]").mask("<1 [0 1]>")
// every other two cycles the first beat is silenced
```

## Gotchas
- Unlike `struct`, `mask` preserves the source pattern's original timing; it only removes events, not adds them.
- The mask alternates over cycles using `<>` angle brackets.
- Useful for creating call-and-response or drop-out effects.

## See also
- `struct` — replaces source timing with the binary pattern's structure.
- `hush` — silences the entire pattern unconditionally.
- `when` — applies a function (not just silence) based on a binary pattern.
- `reset` — resets the source pattern on each onset of another pattern.
