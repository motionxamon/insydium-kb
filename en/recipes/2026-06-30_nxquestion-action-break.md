# Start/stop a looping nxQuestion animation with the Break action

- Source: Top Tip Tuesday — Action Break — https://www.youtube.com/watch?v=CqeOLYEiaKg (2026-06-30)
- Host / generation: NeXus (C4D; same in Blender) — nxQuestion, nxColor (distance), nxAttract/nxPush
- Goal: particles pulse in size forever (sine-wave question), but stop on demand — after a time, at a chosen size, or while an object is near.

## Base loop
nxQuestion: **If Math ▸ Wave > 0 → Set Radius 70 cm** (variation, Delay + Damping for springiness) / **Else → Set Radius 2**. Wave goes −100…100 over time → endless pulsing.

## Stopping it
1. **Break must be first in the stack** (top of the question list), otherwise the wave question runs before the break is reached.
2. Stop after time: `If Age > 150 → Action Break`.
3. Stop at a chosen state: make the Break a child of a second question with operator **AND**: `Age > 150 AND Radius < 5 (±3)` → freeze small; or `Radius > 60 (±10)` → freeze big.
4. Stop while an object is near (interactive): **nxColor** layer *Distance from Object* (link a Null, black→white over ~1000 cm). Then `If Color Brightness < 0.2 → Break` at the top. Break only applies while the question passes → move the null away and the loop resumes. Add `AND Radius < 5` to shrink first, then freeze.

## Notes
- Break exits the remaining questions for that particle on that frame — it's a per-frame gate, not permanent.
- Use case: medical/cell animations reacting to a probe.
