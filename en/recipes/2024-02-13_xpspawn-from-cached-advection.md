# Densify a cached advected sim by spawning (xpCache + xpExplosiaFX Advection + xpSpawn)

- Source: Top Tip Tuesday — xpCache Spawning — https://www.youtube.com/watch?v=XtaaaiKtl_w (2024-02-13)
- Host / generation: C4D; CPU X-Particles (xpExplosiaFX, xpCache, xpSpawn)
- Goal: re-use an old cached smoke/particle sim and pump in near a million new advected particles without re-simulating.

## Steps
1. Default **xpExplosiaFX** + sphere with **xpExplosiaFX Source tag** (default); view Temperature channel. [▶ 0:24](https://youtu.be/XtaaaiKtl_w?t=24)
2. New emitter on the same sphere (Object, polygon area): Rate, frames **0–50**, lifespan 50 (var 20), **10/frame**, speed 0. [▶ 0:54](https://youtu.be/XtaaaiKtl_w?t=54)
3. xpExplosiaFX **Advection** tab active → the smoke moves the particles. [▶ 1:41](https://youtu.be/XtaaaiKtl_w?t=101)
4. **xpCache** to external files (caches both particles and the smoke). [▶ 1:48](https://youtu.be/XtaaaiKtl_w?t=108)
5. **xpSpawn** (Generate modifiers) ▸ **Add Emitter** → "emitter spawn": Draw Emitter off, **Dots**, Gradient Parameter (purple preset) mapped to **Speed**, min 10 / max 200; speed 0, lifespan 50 (var 25). [▶ 3:22](https://youtu.be/XtaaaiKtl_w?t=202)
6. xpSpawn: spawn from source particle positions, defaults otherwise; amount 300 → **10/frame**, then **50** — spawned particles are advected by the same cached smoke. [▶ 4:23](https://youtu.be/XtaaaiKtl_w?t=263)
7. Display ▸ **HUD** shows ~900k particles; raise spawn amount for millions, then re-cache. [▶ 5:36](https://youtu.be/XtaaaiKtl_w?t=336)

## Newest equivalent
**nxSpawn** (2026.1 beta) for the children and GPU **nxExplosiaFX** (Fused 2025.4) for the smoke; in Fused 2025 the nxQuestion Spawn action.
