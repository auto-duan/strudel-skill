---
name: mini-notation
category: syntax
source: https://strudel.cc/learn/mini-notation/
status: verified
---

# Mini-Notation Syntax Reference

Mini-notation is Strudel's DSL for describing rhythms and sequences inside strings. Content inside `"..."` (double quotes) or `` `...` `` (backticks, multi-line) is **parsed** as a pattern. Single quotes `'...'` are plain strings and are **not parsed**.

Almost every function that takes a pattern accepts mini-notation, e.g. `note("c e g")`, `s("bd hh sd hh")`, `n("0 2 4")`.

## Operators / Symbols

| Symbol | Meaning | Example |
|---|---|---|
| space | Separates events within one cycle; events split time evenly | `note("c e g b")` |
| `~` or `-` | Rest / silence | `note("c ~ e ~")` |
| `[ ]` | Sub-sequence group: the bracket occupies one event slot, subdivided internally | `note("c [e g] c")` |
| `< >` | Per-cycle alternation: plays one event per cycle, cycling through | `note("<c e g>")` |
| `*` | Speed up / repeat N times (compressed into the original duration) | `note("c*2 e")`, `note("[c e]*2")` |
| `/` | Slow down: takes N cycles to play through once | `note("[c e g d]/2")` |
| `,` | Parallel / chord (sounds simultaneously) | `note("[c,e,g]")` |
| `@` | Elongation (temporal weight): takes a larger share of time | `note("c@3 e")` (c takes 3 parts, e takes 1) |
| `!` | Replicate: repeats the event WITHOUT compressing duration | `note("c!3 e")` = `note("c c c e")` |
| `?` | Degrade (random drop): default 50%, `?0.3` = 30% drop chance | `note("c*8?")`, `note("c*8?0.3")` |
| `\|` | Random choice: picks one of the options per cycle | `note("[c\|e\|g]")` |
| `( , , )` | Euclidean rhythm: `(pulses, steps, offset?)` | `s("bd(3,8)")`, `s("bd(3,8,2)")` |
| `:` | Select the Nth sample in a sample bank (sample index) | `s("bd:3 hh:1")` |

## Key rules & semantics

### Time is split evenly per cycle
Events in a sequence **split the current time slot evenly**. `note("c e g")` plays three notes across one cycle; `note("c [e g]")` gives `c` half a cycle and `e`, `g` a quarter each.

### `< >` vs `[ ]` vs space
- space sequence: everything packs into **one** cycle, split evenly.
- `[ ]`: compresses multiple events into **one** event slot (used for nested subdivision).
- `< >`: plays only **one** of its events per cycle (alternates across cycles), equivalent to `[...]/n`.

### `*` and `/`
- `*n` repeats n times within the same duration (faster). Accepts non-integers, e.g. `*1.5`.
- `/n` stretches one event over n cycles (slower).
- Both can apply to a single event or a `[ ]` group: `"[c e]*2"`.

### `@` vs `!` (easy to confuse)
- `@n` changes the **time share**: `"c@3 e"` → c takes 3/4, e takes 1/4.
- `!n` **repeats the event** (each equal length): `"c!3"` → `"c c c"`.
- Note `*n` *compresses* repeats into the original slot, while `!n` *adds* equal-length events — different rhythmic results.

### Euclidean `(beats, steps, offset?)`
`s("bd(3,8)")` distributes 3 pulses as evenly as possible across 8 steps (the famous tresillo / "Pop Clave"); the third argument is a rotation offset.

### Sample index `:`
`s("bd:3")` selects the 4th sample (0-indexed) in the `bd` sample bank.

## Gotchas
- **Single quotes don't parse**: `note('c e g')` is not treated as a pattern — use double quotes or backticks.
- `*` is "repeat/fill", NOT "multiply pitch"; change pitch with `note`/`add`/`transpose`, don't expect arithmetic inside mini-notation.
- `?` degradation is **pseudo-random** and cycle-dependent; the same snippet can differ per cycle. Use seed-related functions for reproducibility.
- `,` inside `[ ]` means a chord; don't confuse it with stacking multiple top-level patterns via `stack()`.
- Use backticks `` ` `` for multi-line complex rhythms instead of double quotes to avoid escaping and newline issues.

> Source: <https://strudel.cc/learn/mini-notation/> (fetched 2026-06-23). If this disagrees with the latest official page, the official page wins.
