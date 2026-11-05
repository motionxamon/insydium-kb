# Asteroids orbiting planets + spreading glow (nxAttract Force/Speed Limit, xpColor with particle fields, nxBlend Addition)

- Source: INSYDIUM LIVE! — November 2023 – X-Particles, NeXus, Taiao, MeshTools & Cycles 4 — https://www.youtube.com/watch?v=qaso-gPGBnI (2023-11-16)
- Host / generation: C4D; G2 NeXus (nxTurbulence, nxAttract, nxBlend) mixed with CPU xpColor + xpEmitter fields. Part B of 3 (John Henderson's nebula shot)
- Goal: streams of particles whip around several planets, then a white "infection" spreads through them as a glow mask for render.

## Steps — orbit
1. Two emitters at origin, Height **1 cm** (ribbon). Speed **250, Variation 50** (200–300); Radius 2, Variation 1. Display Gradient by **Speed + Auto** to read the sim.
2. **nxTurbulence** at defaults.
3. **nxAttract** principle: attraction vs **Speed Limit** vs particle momentum. Default limit 250; at 1000 particles overshoot far before turning back.
4. Real setup: Attraction type **Force**, Force **150**, **Speed Limit 350** (above the fastest birth speed). Drop planets (default spheres) into the object list — three planets, 250 F.
5. Each planet splits the stream, so enable the second emitter for density; move planets live to rebalance.
6. Extended Data ▸ Rotation **Random**, spin 3° per axis; Box display shows orientation.

## Steps — infection
7. Display single color **black**. xpSystem ▸ only modifiers in the same system; Ctrl-drag to duplicate → "infecting" system, emitters 15 particles.
8. Main system: **xpColor** (CPU) Set Color white (not Immediate). Infecting emitters ▸ Editing ▸ **Editable** so they appear as points to Fields; drag them into xpColor Fields, mode **Max**, radius 3 → 5 (bigger = faster spread; more infectors also speeds it).
9. Set infectors to white. **nxBlend**: mode **Addition** (only brighter values pass on), Distance 5, Strength 100, Color → smooth gradient spread.
10. Black/white color is then used in Cycles 4D as an emission mask.

## Side tip (Q&A): xpDynamics objects intersecting
Enable **Push** (100) in each xpDynamics tag; if they still clip, add particles (Distribution vertices + midpoints) — the particles, not the polygons, collide.

## Gotchas
- CPU xp and GPU nx modifiers run together on the same emitter.

## Newest equivalent
**nxColor** (2024.2) with an nxFalloff (Points/Object mode in 2026.1) instead of xpColor + C4D fields; **nxInfectio** for proper spread (see 2023-12-12 recipe). Orbits: nxAttract unchanged; nxWarp Helix/Path can shape streams.
