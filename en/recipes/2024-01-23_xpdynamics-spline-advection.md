# Text spline blown by an explosion (xpDynamics on a spline + xpExplosiaFX advection)

- Source: Top Tip Tuesday — Spline Advection — https://www.youtube.com/watch?v=2YkjQgmo8Ic (2024-01-23)
- Host / generation: C4D; CPU X-Particles (xpExplosiaFX + Source tag, xpDynamics tag)
- Goal: make any C4D spline dynamic and let a smoke/fire sim push it around.

## Steps
1. Source particles: **Shot**, 45 per frame for 30 F, lifespan 30 (var 10), speed 150 (var 50), radius 5 (var 3). [▶ 0:36](https://youtu.be/2YkjQgmo8Ic?t=36)
2. Emitter **Extended Data**: Temperature 1, Fuel 1; add **xpExplosiaFX Source tag** (default). [▶ 1:13](https://youtu.be/2YkjQgmo8Ic?t=73)
3. Source tag **Velocity 100% → 500%** so the fire follows the particles' direction instead of rising straight up. [▶ 1:43](https://youtu.be/2YkjQgmo8Ic?t=103)
4. Text spline ▸ **xpDynamics tag** → a particle per intermediate point. In the tag, **add an Emitter** ("emitter dynamic") — advection needs real emitter particles. [▶ 2:54](https://youtu.be/2YkjQgmo8Ic?t=174)
5. xpExplosiaFX ▸ Advection ▸ **Advect Particles** on. [▶ 3:24](https://youtu.be/2YkjQgmo8Ic?t=204)
6. Source emitter ▸ Modifiers tab: **exclude xpExplosiaFX** — otherwise it's advected by its own explosion and jitters. [▶ 4:05](https://youtu.be/2YkjQgmo8Ic?t=245)
7. Dynamics tag: **Rigidity 0**, then **Constraints ▸ add Structure** constraint (lower its strength) so letters wobble but hold together. [▶ 5:08](https://youtu.be/2YkjQgmo8Ic?t=308)
8. Procedural: change the text and it still works. Keyframe rigidity up late in the shot to snap back to the original shape. [▶ 6:14](https://youtu.be/2YkjQgmo8Ic?t=374)

## Newest equivalent
GPU smoke is **nxExplosiaFX** (Fused 2025.4); mesh/spline following particles is **nxDeformer** (2026.1 beta) — check whether NeXus advection covers this before switching.
