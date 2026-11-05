# Infection-driven peel-away (nxInfectio Use Groups + nxWind/nxTurbulence on infected group + nxConstraints Distance break)

- Source: Top Tip Tuesday — nxInfectio Peel — https://www.youtube.com/watch?v=Be90jYTwF0c (2023-12-12)
- Host / generation: C4D; G2 NeXus inside X-Particles (xpEmitter + nxInfectio, nxWind, nxTurbulence, nxConstraints) + collider tag
- Goal: an organic infection spreads over a model; infected particles get blown off while still springy-linked, stretching and ripping into chunks.

## Base
Model with a **collider tag**; **xpEmitter** Polygon Area, **Random Shot 40,000**, radius **2 cm**, speed 0. Display ▸ Color mode **Shader** with a black/white noise (gaseous) — infection spreads faster through white particles.

## Steps
1. **nxInfectio** ▸ **Add Seed Object** (spherical volume) — place it near the belly. Orange = infected, blue = incubating. [▶ 1:34](https://youtu.be/Be90jYTwF0c?t=94)
2. Switch the color mode to **Use Groups**: add an **Incubating group** (group 1) and an **Infected group** (group 2). [▶ 2:34](https://youtu.be/Be90jYTwF0c?t=154)
3. **nxWind** rotated outward/upward, Groups Affected **group 2**. [▶ 3:34](https://youtu.be/Be90jYTwF0c?t=214)
4. **nxTurbulence**, Voronoi, strength **7**, Groups Affected **group 2**. [▶ 3:56](https://youtu.be/Be90jYTwF0c?t=236)
5. **nxConstraints**: **Distance** constraint (not Birth), **6 connections** within **40 cm**, lower stiffness, Groups Affected **group 2** → peeling sheets. [▶ 4:38](https://youtu.be/Be90jYTwF0c?t=278)
6. Break: snap when stretched to **300%** of rest length → chunks tear away. [▶ 5:33](https://youtu.be/Be90jYTwF0c?t=333)
7. nxInfectio ▸ **Infected Lifespan 300 → 150** frames so blown pieces die. [▶ 5:47](https://youtu.be/Be90jYTwF0c?t=347)
8. When the look works, set group color change to **No Color Changes** and show the model again. [▶ 6:23](https://youtu.be/Be90jYTwF0c?t=383)

## Newest equivalent
2026.1 beta: every modifier layer has its own **Falloff** list (incl. Wet/Curvature) for extra masking, and **nxDeformer** can tear a mesh driven by particles if you want a skin rather than points.
