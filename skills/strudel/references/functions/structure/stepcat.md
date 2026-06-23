---
name: stepcat
category: structure
signature: "stepcat(...items: ([number, Pattern] | Pattern)[]): Pattern"
aliases: [timeCat, timecat]
tags: [combination, concatenation, stepwise, proportional]
related: [cat, seq, stack, pace, expand, stepalt, arrange]
source: https://strudel.cc/learn/factories/
status: verified
---

Concatenates patterns like `seq`/`fastcat` but proportional to their step counts instead of equal time-slices; accepts optional `[length, pattern]` pairs to set explicit step weights.

## Parameters
- `...items` ([number, Pattern] | Pattern) — either bare patterns (step count inferred from mini-notation top-level events) or `[length, pattern]` pairs that explicitly set the step weight.

## Returns
Pattern — a single-cycle pattern whose items are time-proportional to their step counts.

## Examples
```js
stepcat([3, "e3"], [1, "g3"]).note()
// equivalent to "e3@3 g3".note()
// e3 takes three-quarters of the cycle, g3 takes one quarter
```

```js
stepcat("bd sd cp", "hh hh").sound()
// equivalent to "bd sd cp hh hh".sound()
// 3 steps + 2 steps → 3/5 and 2/5 of the cycle
```

```js
// stepcat respects inferred steps, unlike fastcat which splits equally
fastcat("bd hh hh", "bd hh hh cp hh").sound()
// each pattern gets exactly 1/2 cycle regardless of event count

stepcat("bd hh hh", "bd hh hh cp hh").sound()
// 3-step pattern gets 3/8 cycle; 5-step pattern gets 5/8 cycle
```

## Gotchas
- Step count is inferred from the **top-level** event count in mini-notation. `"a [b c] d e"` is 4 steps (the sub-pattern `[b c]` counts as one step). Use `^` inside a sub-pattern to change the metrically-counted level: `"a [^b c] d e"` counts as 8 steps.
- The aliases `timeCat` and `timecat` are identical; `stepcat` is the preferred modern name.
- Without `pace`, the combined pattern still fits in one cycle — steps only affect the relative proportions, not playback speed.
- `expand` and `contract` interact with step counts and are designed to be used alongside `stepcat`.

## See also
- `cat` — concatenation where each item occupies **one full cycle**.
- `seq` / `fastcat` — concatenation with equal time-slices inside one cycle.
- `pace` — sets the playback rate in steps-per-cycle after stepwise combination.
- `expand` — scales step size of a pattern up by a factor.
- `stepalt` — like `stepcat` but alternates through list arguments.
