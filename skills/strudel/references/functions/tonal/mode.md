---
name: mode
category: tonal
signature: "mode(strategy: string | Pattern): Pattern"
aliases: []
tags: [tonal, voicing, mode, anchor, harmony]
related: [anchor, voicing, chord, dict, rootNotes]
source: https://strudel.cc/understand/voicings/
status: verified
---

Controls how `voicing()` aligns the chosen voicing relative to the `anchor` note. The strategy decides whether the voicing sits below, above, strictly below (ducked), or is rooted on the closest root to the anchor.

## Parameters
- `strategy` (string | Pattern) — One of:
  - `below` — top note stays at or below the anchor (default).
  - `above` — bottom note stays at or above the anchor.
  - `duck` — top note strictly below the anchor.
  - `root` — bottom note is always the closest root to the anchor.

  The anchor may be appended after a colon: `"below:c5"`, `"root:g2"`.

## Returns
Pattern — chord events tagged with an alignment mode, resolved by a following `voicing()`.

## Examples
```js
// Cycle through alignment strategies against a fixed anchor
mode("<below above duck root>").chord("C").anchor("c5").voicing().room(.5)
```

```js
// Anchor embedded directly in the mode string
mode("<below above duck root>:c5").chord("C").voicing().room(.5)
```

```js
// 'root' mode builds a bass voice anchored to g2
n("0 - 1 -").set(chords).mode("root:g2").voicing()
```

## Gotchas
- `mode` only matters together with `voicing` and an `anchor` (explicit or embedded).
- `root:gN` is a handy idiom for generating a bass register from chord symbols.
- `duck` differs from `below` only at the boundary: `duck` is *strictly* below the anchor.
- If you embed the anchor in `mode` (`"below:c5"`), you don't need a separate `anchor()` call.

## See also
- `anchor` — sets the reference note that `mode` aligns to.
- `voicing` — applies the mode to render chords.
- `rootNotes` — alternative way to get just chord roots without voicing.
