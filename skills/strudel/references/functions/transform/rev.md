---
name: rev
category: transform
signature: "rev(): Pattern"
aliases: []
tags: [time, reverse, order]
related: [palindrome, iter, jux]
source: https://strudel.cc/learn/time-modifiers/
status: verified
---

Reverse the order of events within each cycle of a pattern.

## Parameters
None.

## Returns
Pattern — the pattern with each cycle reversed.

## Examples
```js
note("c d e g").rev()
// each cycle becomes g e d c
```

## Gotchas
- `rev` reverses **per cycle**, not the whole tune end-to-end; each cycle is reversed independently.
- Commonly combined with `jux` for a stereo effect: `.jux(rev)` reverses the right channel.

## See also
- `palindrome` — applies rev every other cycle (forward/backward alternation).
- `jux` — `.jux(rev)` is the classic stereo technique.
