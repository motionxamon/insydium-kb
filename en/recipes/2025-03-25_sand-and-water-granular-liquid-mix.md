# Sand + water in one sim (nxFluids SPH Granular + per-emitter nxFluids tag, stability mapped to age)

- Source: Top Tip Tuesday — Simulating Sand and Water — https://www.youtube.com/watch?v=JvAcrBQDDvw (2025-03-25)
- Host / generation: C4D; NeXus inside X-Particles (nxFluids SPH, nxGravity, nxFluids tag, Mapping) + CPU xpCollider tag on the ground
- Goal: a sand torus that stands on its own, then crumbles when a water stream hits it.

## Base
Ground plane with **xpCollider**; torus as volume source. Sand emitter: Object (torus) volume, **Shot Hexagonal, radius 1.5**. Water emitter: small sphere, Hexagonal continuous, **radius 1.5**. Default nxGravity + nxFluids.

## Steps
1. **nxFluids ▸ fluid type Granular**. Raise **Substeps to 20** (granular needs it to clump). [▶ 0:00](https://youtu.be/JvAcrBQDDvw?t=0)
2. Granular settings: **Friction ~79–80%** (default 3% won't stand), **Stability 20** (5 cracks immediately; 20 settles solid). [▶ 4:57](https://youtu.be/JvAcrBQDDvw?t=297)
3. Water emitter ▸ Tags ▸ INSYDIUM ▸ **nxFluids tag**: override type to **Liquid**, add a little Surface Tension → it ignores the solver's Granular setting. [▶ 3:35](https://youtu.be/JvAcrBQDDvw?t=215)
4. Stop the pressure "explosion" at the water source: nxFluids ▸ check density of new particles, **kill if born above 105%** density. [▶ 4:01](https://youtu.be/JvAcrBQDDvw?t=241)
5. Make the sand breakable on impact: nxFluids ▸ **Mapping ▸ Age map**, Category **SPH**, Parameter **Stability**, range **0–30 frames**; curve full stability at birth, dropping to ~0 by ~frame 20. Lower the floor further for more crumbling. [▶ 5:24](https://youtu.be/JvAcrBQDDvw?t=324)

## Gotchas
- SPH mixing requires **identical particle radius** on every emitter.
- High friction/stability alone makes the sand immune to the water — the age mapping is what lets it fail.

## Newest equivalent
2026.1 beta **nxMPM** is multi-material (liquid + sand in one solver; Mixer can change material by age/speed/damage) and **nxMaterial** has a "Sand wet" preset — the more physical route to wet sand. Stable Fused 2025.4: this SPH Granular + tag setup.
