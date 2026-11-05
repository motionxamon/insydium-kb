# Particle wireframe reveal (nxFollowGeo Edge mode + nxTurbulence + nxSpeed limit)

- Source: Top Tip Tuesday — Wireframe Reveal — https://www.youtube.com/watch?v=RUhF1pju3Wk (2025-05-06)
- Host / generation: C4D; NeXus inside X-Particles (nxFollowGeo, nxTurbulence, nxSpeed, nxAttract) + xpTrail for rendering
- Goal: particles crawling along a model's edges to trace its wireframe.

## Steps
1. Emitter: **width 50, height 0** (thin streak), Display **Dots**, placed right next to the model; **speed 0, radius 2**, emit **90 frames at 20,000/s**.
2. **nxFollowGeo**: object = wolf head, **Surface** mode, **Field of Vision 360°**, **Friction 1%**, **Distance 25** so every particle gets captured.
3. Motion: **nxTurbulence** strength **40**, add octaves, lower persistence (fine detail, keeps big curls).
4. Calm it: **nxSpeed** below the turbulence, Accelerate with **Force 0**, **Max Speed 80 cm** — strong turbulence but clamped speed.
5. nxFollowGeo mode **Surface → Edge**; raise the Edge setting to hug edges tighter → wireframe reveal.
6. Art-direct: **nxAttract** between turbulence and speed; move it to steer where the flow heads.
7. Optional: **xpTrail** on the emitter for woven line renders.

## Gotchas
Modifier order matters: turbulence → attract → speed limit last.

## Newest equivalent
2026.1 beta: nxSpeed's layer is named **Acceleration**; 2026.1 **nxWarp** (Path/Flow modes) and 16 nxFalloff modes add more steering; in NeXus 2026 use **nxTrail** instead of xpTrail.
