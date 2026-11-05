# Statue crumbling into sand as an infection spreads (nxInfectio groups + nxFluids SPH Granular + nxSpeed Max Speed 0)

- Source: Top Tip Tuesday — Granular Crumble — https://www.youtube.com/watch?v=DsZ56QYQ2cY (2024-06-11)
- Host / generation: C4D; xpEmitter + NeXus GPU (nxInfectio, nxFluids SPH Granular, nxGravity, nxSpeed)
- Goal: a statue collapses in clumps, top-down, as the infection travels over it.

## Base
xpEmitter from the statue **volume**, Shot hexagonal, speed 0, radius 1. Display colored by a C4D Noise shader (light/dark values). Emitter ▸ Groups ▸ **birth group 1**.

## Steps
1. **nxInfectio** with 3 **seed objects** at the top. Lighter particles infect faster; raise search radius and allowed infections per particle to speed it up. [▶ 1:29](https://youtu.be/DsZ56QYQ2cY?t=89)
2. Mode **Use Groups**: add **incubating** and **infected** groups; Group color change **None** (only group membership matters). [▶ 2:29](https://youtu.be/DsZ56QYQ2cY?t=149)
3. **nxFluids** below nxInfectio, solver **SPH** (unlocks **Granular**): **Friction 100%**, **Stability 10**, **Cohesion 5**; substeps 3 for previews. [▶ 3:31](https://youtu.be/DsZ56QYQ2cY?t=211)
4. **nxGravity** below, slight variation.
5. **nxSpeed** at the bottom: mode **Acceleration**, acceleration 0, **Max Speed 0**, **Groups Affected = group 1** → uninfected particles hold the shape; they fall only once infected. [▶ 4:47](https://youtu.be/DsZ56QYQ2cY?t=287)
6. For clumpy sand raise nxFluids **substeps** much higher and cache (2 min 16 s for 300 F in the demo). [▶ 5:09](https://youtu.be/DsZ56QYQ2cY?t=309)

## Newest equivalent
NeXus 2026.1 **nxMPM** sand/snow (or **nxMaterial** presets) with material change by age/damage, pinned with **nxPin** until released.
