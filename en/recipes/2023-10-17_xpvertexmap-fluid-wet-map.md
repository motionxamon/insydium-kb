# Dynamic wet map where fluid hits a wall (xpVertexMap X-Particles layer, Fade then Add)

- Source: Top Tip Tuesday — nxFluids Wet Maps — https://www.youtube.com/watch?v=d0Rps3gG9JI (2023-10-17)
- Host / generation: C4D; G2 nxFluids SPH + **CPU xpVertexMap** utility (also works with CPU fluids)
- Goal: a vertex map that paints wetness where liquid touches geometry and slowly dries, for a wet material at render time.

## Base
Cylindrical emitter; **nxGravity 600 cm**; **nxFluids SPH**, substeps **5**, **Check Density** on (no explosive births). Low-poly cube wall + plane floor as colliders (fast GPU collisions).

## Steps
1. Duplicate the wall: hide the low-poly collider (also non-renderable); on the copy delete the collider tag and raise segments (**X 90 / height 40**). [▶ 2:08](https://youtu.be/d0Rps3gG9JI?t=128)
2. Utilities ▸ **xpVertexMap** at the bottom, object = the dense copy. [▶ 1:24](https://youtu.be/d0Rps3gG9JI?t=84)
3. Delete the default **Polygons** layer; add an **X-Particles** layer, object = the emitter. [▶ 2:45](https://youtu.be/d0Rps3gG9JI?t=165)
4. Layer radius **25 → 5 cm** (weight falls off over that distance).
5. Effects tab: add **smoothing**. [▶ 3:58](https://youtu.be/d0Rps3gG9JI?t=238)
6. Layers ▸ Blend **Normal → Fade then Add** and raise the fade → wetness accumulates and dries over time. [▶ 4:43](https://youtu.be/d0Rps3gG9JI?t=283)
7. Use the vertex map in the wall material (wet/glossy mask). [▶ 5:02](https://youtu.be/d0Rps3gG9JI?t=302)

## Gotchas
- Paint on a dense render copy, not the low-poly collider.

## Newest equivalent
2026.1 beta: **Wet nxFalloff** mode, and in C4D **nxFalloffMap** bakes falloffs to vertex map / vertex color tags (see recipe 2026-04-07 soot damage vertex map).
