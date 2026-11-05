# Wiggly tendrils held together by constraints (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)

- Source: Maintenance Training — Dynamics - Constraints - Dynamic Tendrils Tutorial — https://www.youtube.com/watch?v=KBktASa5O2o (2023-06-12)
- Host / generation: C4D; CPU X-Particles (xpTendril, xpTurbulence, xpConstraints, xpTrail, xpSplineMesher)
- Goal: tentacle-like tendrils under strong turbulence that keep their shape and don't pass through themselves or each other.

## Steps
1. **xpEmitter ▸ Object ▸ Emitter Shape: Defined Emission**, Inline, **Count 1** → one source point. Display: Circles. [▶ 0:40](https://youtu.be/KBktASa5O2o?t=40)
2. **xpTendril** (Generate modifiers): untick **Scene Length**, Tendril Length **90** frames. It is a steady stream of particles dying at 90 frames that reads as one tendril. [▶ 1:35](https://youtu.be/KBktASa5O2o?t=95)
3. **xpTurbulence** for wiggle. **xpTrail ▸ Algorithm: Tendrils** connections (not tracing the birth particle). **xpSplineMesher** on the trail: Subdivision 1, Size ▸ **Scale Spline** curve to taper to a point. [▶ 3:11](https://youtu.be/KBktASa5O2o?t=191)
4. Problem: high turbulence pulls tip particles apart and the trail becomes straight linear segments — trail settings can't fix it. [▶ 5:03](https://youtu.be/KBktASa5O2o?t=303)
5. Fix: **xpConstraints ▸ Connections ▸ Distance** (birth connections fail for constantly new particles). Defaults: radius **40 cm**, up to **8** connections. Turn on Display Constraints to check. [▶ 5:42](https://youtu.be/KBktASa5O2o?t=342)
6. Tuning: fewer connections (e.g. 2) = more organic but can blow up; more = stiffer. Extra accuracy: **Ctrl+D ▸ X-Particles ▸ Subframe Steps 3, Iterations 5** (10 tried). A slightly larger connection radius was the real fix, after which Iterations 5 sufficed. [▶ 7:52](https://youtu.be/KBktASa5O2o?t=472)
7. Second tendril: Ctrl-drag copy the emitter, move it. Distance links join the two → give each emitter its own **group** and enable **same group only** in Connections. Duplicate the trail (Tendril 2 emitter) and add both trails to the Spline Mesher. [▶ 12:45](https://youtu.be/KBktASa5O2o?t=765)
8. No interpenetration: Constraints ▸ **Collisions** on. With **Same Emitter** on (needed so a tendril can't cross itself) particles bounce hard and reintroduce linear artifacts — fix by adding **one more connection**. Friction also works but kills the energy, so it was left off. [▶ 15:20](https://youtu.be/KBktASa5O2o?t=920)

## Gotchas
- Same Emitter collisions off = tendrils collide with each other but can self-intersect.

## Newest equivalent
**nxDendrite** (branches/network) and nxSpawn are the NeXus growth tools; **nxConstraints** (Distance connections + Collisions layer) and **nxTrail** + **nxMesher** cover the rest on the GPU. For shaped streams, **nxWarp** Path/Helix (2026.1 beta).
