# Shrink trails away before particles die (xpTrailsMod via xpQuestion, or Change Trails action)

- Source: Top Tip Tuesday — Shrink Trails — https://www.youtube.com/watch?v=WqfbeF2OQOk (2023-04-04)
- Host / generation: C4D; CPU X-Particles (xpEmitter, xpTrail, xpTrailsMod, Questions/Actions)
- Goal: trails retract smoothly instead of vanishing when their particle dies.

## Base
Sphere emitter + **xpTrail** (Full Scene Trail off, **Trail Length 30**). A plain lifespan of 110 F makes trails vanish abruptly — a trail can't exist without its particle — so keep full lifespan.

## Steps — method A (adjustable)
1. Modifiers ▸ Control ▸ **xpTrailsMod** (operation **Shrink**). It's always on by default, so trails shrink before they grow — it needs a trigger. [▶ 1:32](https://youtu.be/WqfbeF2OQOk?t=92)
2. Emitter ▸ Questions ▸ add question: **Particle Data ▸ Age**, every frame, **greater than 110** frames → **Activate Modifier**: xpTrailsMod. [▶ 2:16](https://youtu.be/WqfbeF2OQOk?t=136)
3. Mod options: Shrink / Expand / Grow / Pulse; **Interval** (e.g. 10 = shrink only every 10th frame → slower); **Rate of Change** high = near-instant. [▶ 3:07](https://youtu.be/WqfbeF2OQOk?t=187)
4. Kill at zero: in the mod's action slot (trail reaches zero) add **Direct Action ▸ Change Life** (default = kill). [▶ 3:59](https://youtu.be/WqfbeF2OQOk?t=239)

## Steps — method B (quick)
5. Delete the mod and Change Life; on the same Age > 110 question add a **Direct Action ▸ Object Action ▸ Emitter/Generator ▸ Change Trails**, link the xpTrail, enable **Shrink Trails** and **Kill particles at zero**. Fewer options, same result. [▶ 5:06](https://youtu.be/WqfbeF2OQOk?t=306)

## Newest equivalent
For GPU (nx) emitters, rebuild the Age trigger in **nxQuestion** — CPU questions don't drive GPU emitters reliably; this exact shrink-trail action is a CPU xpTrail feature.
