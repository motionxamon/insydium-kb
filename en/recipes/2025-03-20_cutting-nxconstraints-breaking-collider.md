# Slicing a soft body with a collider knife (nxConstraints Birth + Breaking Threshold)

- Source: Bite-Sized — Cutting Constraints — https://www.youtube.com/watch?v=fzMhJobCGR0 (2025-03-20)
- Host / generation: C4D; xpEmitter + NeXus GPU nxConstraints, nxGravity; CPU xpCollider tags
- Goal: a squishy particle sphere that an animated cube cuts in two.

## Base
Disc floor with **xpCollider** friction **55%**; cube "knife" with an xpCollider (no bounce/friction/scatter settings) keyed to drop, scrape across and lift out.

## Steps
1. **xpEmitter ▸ Object**: Emitter Shape **Sphere**, raised above the floor. [▶ 0:32](https://youtu.be/fzMhJobCGR0?t=32)
2. Emission: **Shot**, mode **Simulate** (particles visible on frame 0), shot type **Regular**, speed **0**, radius **6**. Display **Spheres**, enable **Constraints** display. [▶ 0:49](https://youtu.be/fzMhJobCGR0?t=49)
3. **nxConstraints** ▸ **Birth** connection → yellow springs appear one frame in. [▶ 1:32](https://youtu.be/fzMhJobCGR0?t=92)
4. **nxGravity**, speed lowered to **150**. [▶ 1:49](https://youtu.be/fzMhJobCGR0?t=109)
5. nxConstraints: **Iterations 10** (more = stiffer) and add a **Collision** layer → bouncy soft body instead of a splat. [▶ 2:20](https://youtu.be/fzMhJobCGR0?t=140)
6. Birth connection ▸ **Breaking Threshold 50% → 20%** (break when stretched by that share of the rest distance) → the knife snaps the springs and shoves one half away. [▶ 2:42](https://youtu.be/fzMhJobCGR0?t=162)

## Newest equivalent
NeXus 2026.1 **nxMPM** (Elastic material with fracture, collider support) is the GPU route to cuttable soft solids; nxPin can anchor parts of a constraint body.
