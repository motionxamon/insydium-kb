# Feature notes: new NeXus modifiers — nxUpres, nxInfectio, nxWave, nxAvoid, nxFlock, nxBlend modes, nxFoam on caches, nxWind Von Karman (Fused 2023.3)

- Source: INSYDIUM Fused Release Update — July 2023 - NeXus Modifiers Sneak Peek — https://www.youtube.com/watch?v=c-Xh7p3xq-g (2023-06-26)
- Host / generation: C4D; G2 NeXus inside X-Particles (GPU) — Fused 2023.3
- Goal: overview of the GPU modifiers added/updated in July 2023.

## New
- **nxUpres** — Source = cached low-count emitter, Destination = high-count emitter; live high-count result driven by the source velocity; interpolates Velocity, Radius, Color and more, so the original modifiers aren't needed.
- **nxInfectio** — virus-style spread to neighbouring particles, now on the GPU (organic growth, driving modifiers in fluid sims).
- **nxWave** — live velocity field that makes animated waves in fluid sims; display modes for tuning; **6 custom noise types**.
- **nxAvoid** — GPU particle-to-object avoidance; any objects/generators in the list (e.g. xpShatter pieces between walls); on detection **change direction**, **freeze** or **die**.
- **nxFlock** — GPU flocking; layered behaviours (e.g. chaos, cohesion), **pursuit** objects to chase, **enemy** particles to flee.

## Updated
- **nxFoam** generates live foam from **cached** fluid sims (just add a foam emitter).
- **nxWind** new **Von Karman** mode — physically plausible gusting.
- **nxBlend** blend modes (**Multiply, Screen, Overlay**…) and a new **Weighting** tab with per-emitter layer weighting.

## Replaces
CPU xpUpres-style spawning from caches, xpInfectio, xpAvoid, xpFlock on GPU emitters. Today: nxUpres and nxFlock remain current; spawning → **nxSpawn** (2026.1 beta); nxFoam rewritten with foam/bubbles/spray layers (2025.4); nxWave coupling → **nxOcean** with FLIP coupling (2026.1 beta).
