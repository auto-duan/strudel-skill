# Strudel Gotchas & Common Mistakes

A collection of common mistakes and counterintuitive behaviors in Strudel.
Verified against the per-function docs in this repo and official sources
(<https://strudel.cc/>, fetched 2026-06-23). When this disagrees with the latest
official page, the official page wins.

## Mini-Notation

- **Single quotes are NOT parsed**: Only double quotes `"..."` and backticks `` `...` `` are parsed as mini-notation patterns. Single quotes are plain JS strings.
  - Wrong: `note('c e g')` — treated as the literal string, not a pattern.
  - Right: `note("c e g")` or `note(`c e g`)`.

- **`*` is repeat/fill, NOT pitch multiplication**: `note("c*2")` repeats `c` twice within its slot; it does not multiply or raise the pitch. Change pitch with `note`, `add`, `transpose`, or scale degrees.
  - Wrong: expecting `"c*2"` to mean "c an octave up".
  - Right: `note("c").add(12)` or `note("c c")`.

- **`@` (elongation) vs `!` (replicate) are easy to confuse**: `@n` changes the *time share*; `!n` *repeats* the event as equal-length copies.
  - `note("c@3 e")` → c takes 3/4 of the cycle, e takes 1/4.
  - `note("c!3 e")` → `note("c c c e")` (four equal events).

- **`*n` vs `!n` give different rhythms**: `*n` *compresses* repeats into the original slot (faster); `!n` *adds* equal-length events (longer total). They are not interchangeable.

- **`[ ]` vs `< >` vs space**: space packs everything into one cycle split evenly; `[ ]` compresses events into a single sub-slot; `< >` plays only ONE of its events per cycle (alternation across cycles). `<a b>` is equivalent to `[a b]/2`.
  - Wrong: expecting `<c e g>` to play all three notes in one cycle.
  - Right: `[c e g]` plays all three in one cycle; `<c e g>` plays one per cycle.

- **`,` inside brackets is a chord, not top-level stacking**: `note("[c,e,g]")` sounds the three notes simultaneously (a chord). Don't confuse it with stacking independent top-level patterns via `stack()`.

- **Euclidean argument order matters**: `(pulses, steps, offset?)`. `bd(3,8)` ≠ `bd(8,3)`. First number is sounding pulses, second is total steps; swapping them produces a completely different rhythm.

- **`?` degrade is pseudo-random and cycle-dependent**: `note("c*8?")` drops ~50% of events, but *which* events differ per cycle. Output is not reproducible across cycles without seeding. `?0.3` sets a 30% drop chance.

- **`:` selects a sample index, 0-indexed, and wraps**: `s("bd:3")` is the 4th sample in the `bd` bank (index 0 is the first). Indices beyond the available count wrap around (modulo), so a "too big" index won't error — it silently picks something else.

## Pattern Composition

- **`stack` vs `cat`/`seq` is the #1 confusion**: `stack` plays patterns *simultaneously* (layered); `cat`/`slowcat` plays them *one full cycle each* in sequence; `seq`/`fastcat` plays them *all within one cycle*.
  - Wrong: using `cat` when you wanted layers playing together.
  - Right: `stack(drums, bass, melody)` for simultaneous parts.

- **`off` vs `superimpose`**: both layer a transformed copy on top of the original, but `off(time, fn)` *delays* the copy by `time` cycles while `superimpose(fn)` adds it with no time offset.
  - `"c3 eb3 g3".off(1/8, x=>x.add(7))` — copy is shifted later by 1/8 cycle.

- **`fast` / `slow` change the whole pattern; `*` / `/` are local**: `.fast(2)` applies to the entire chained pattern, whereas `*2` only affects the event(s) it's attached to inside the string.

- **`fast`/`slow` do NOT change pitch**: they are time operations only. A value `< 1` for `fast` slows down (equivalent to `slow(1/factor)`). For pitch-shifting on speed change, use `hurry` (raises sample playback speed too).

- **`ply` repeats each event, `fast` repeats the whole pattern**: `s("bd sd").ply(2)` → `bd bd sd sd`; `s("bd sd").fast(2)` → `bd sd bd sd`. Different results.

- **`rev` reverses per cycle, not the whole tune**: each cycle is reversed independently — it does not play the entire piece backwards end-to-end. Classic stereo trick: `.jux(rev)`.

## Audio / Effects

- **You must press play / re-evaluate to hear changes**: editing code does nothing until you run it (Ctrl/Cmd+Enter to update, Ctrl/Cmd+. to stop). The REPL does not auto-evaluate on every keystroke.

- **Samples are lazy-loaded — first hit can be silent**: the very first trigger of a sample may produce no sound while the file downloads. It plays correctly on subsequent cycles.

- **`s` selects the bank, `n` (or `:N`) selects the variant**: `s("hh:2")` is shorthand for `s("hh").n(2)`. Don't expect `n` alone to choose a drum; pair it with `s` (or use `n` with `scale` for melodies).

- **`n` is overloaded**: with `s` it picks a sample variant index; with `scale` it means scale degree. Same function name, very different meaning depending on context.

- **Filter param names**: `lpf`/`cutoff` is the low-pass cutoff, `hpf` the high-pass; `lpq`/`resonance` controls filter resonance. Mixing these up (or forgetting resonance defaults) is a common source of "why does my filter do nothing" confusion.

## Timing & Tempo

- **Continuous signals must be sampled before they make events**: `sine`, `saw`, `rand`, `perlin` are continuous (every point in time has a value). They produce no discrete events until you call `.segment(n)` (or use them to modulate a param).
  - Wrong: `n(sine).scale("C:major")` — no discrete steps.
  - Right: `n(sine.segment(16).range(0,15)).scale("C:major")`.

- **Signals output 0..1 by default**: remap with `.range(min, max)`. There are `sine2`/`saw2` etc. variants that output -1..1 instead.

- **`scale` works with `n`, not `note`**: feed scale *degrees* (numbers) via `n` into `scale`. Calling `.scale()` on a pattern of note *names* quantizes them to the scale instead of mapping degrees — usually not what you want.

- **Scale defaults to octave 3**: `"C:major"` roots at C3 when no octave is given. Negative degrees wrap backwards (`-1` = one step below root, octave down); degrees past the scale length auto-octave up (degree 7 in a 7-note scale = root one octave higher).

- **Multi-word scale/chord names use `:` not spaces**: `"bebop major"` must be written `"bebop:major"` (e.g. `"C:bebop:major"`).

- **`< >` slows things down relative to a sequence**: putting alternation `<a b>` where you expected both per cycle effectively halves how often each value appears. Use it deliberately for per-cycle variation, not for packing notes.
