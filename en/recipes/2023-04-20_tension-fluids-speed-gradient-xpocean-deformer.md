# Speed-gradient colours and an ocean-deformed fluid bed (Gradient Parameter by Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)

- Source: NAB 2023 - INSYDIUM Training — Tension Fluids- Part 2 — https://www.youtube.com/watch?v=VuevOvpbvJY (2023-04-20)
- Host / generation: C4D; NeXus SPH sim from Part 1 + CPU xpOcean, xpOpenVDBMesher, xpJoin, xpCache
- Goal: colour the three paint fluids by speed and ride them on a rolling ocean surface built from the hidden base particles.

## Steps
1. Colour emitters: **Start Emit 100 → 15** (the base settles quickly). Display Dots. [▶ 0:44](https://youtu.be/VuevOvpbvJY?t=44)
2. Display ▸ Color Mode **Gradient Parameter**, parameter **Speed**: dark purple when slow, darker mid knot, white when fast; raise the white threshold **100 → 150 cm/s** to cut the white. Per emitter add a cyan knot (bias pinched) or a light desaturated green for variety; rename emitters. [▶ 1:34](https://youtu.be/VuevOvpbvJY?t=94)
3. **xpOcean** (Generators): lower Wave Height and Time Scale, raise **Wind Speed** for a longer swell, add **Choppiness** only until peaks start folding. Viewport material: no reflectance, **Fresnel** shader in Color, deep blue → greyish white. [▶ 9:11](https://youtu.be/VuevOvpbvJY?t=551)
4. Switch xpOcean **Type: Primitive → Deformer** (works like any C4D deformer as child/sibling). [▶ 10:28](https://youtu.be/VuevOvpbvJY?t=628)
5. Exclude **nxTurbulence** from the base emitter so the bed just settles.
6. **xpOpenVDBMesher** source = base emitter, **Point Radius 5**. Put xpOcean as its sibling in the Generators folder → the live mesh is deformed. Move the material onto the mesher. [▶ 12:11](https://youtu.be/VuevOvpbvJY?t=731)
7. Particles ride the waves too: add the xpOcean deformer to each colour emitter's **Modifiers** list (ticked = included). [▶ 11:28](https://youtu.be/VuevOvpbvJY?t=688)
8. **xpCache** (overwrite): ~5 min with the dense mesh. [▶ 15:22](https://youtu.be/VuevOvpbvJY?t=922)
9. After caching: **untick xpOcean in the emitters' Modifiers** (else cached particles get deformed twice). [▶ 16:33](https://youtu.be/VuevOvpbvJY?t=993)
10. The VDB mesh vanishes while scrubbing: put the mesher under an **xpJoin** (Utilities) with xpOcean as its sibling. Lower the Join **Y −7 cm** so particles float on the surface. [▶ 17:37](https://youtu.be/VuevOvpbvJY?t=1057)
11. Display Squares + **Force Display**, **Display Size Factor 50%**. Use emissive shading at render. [▶ 19:04](https://youtu.be/VuevOvpbvJY?t=1144)

## Newest equivalent
**nxOcean** (2026.1 beta) with FLIP coupling, foam/spray and floating objects; **nxMesher** with **Blend into Ocean**; colour by speed via **nxColor** with Mapping. Stable Fused 2025.4: nxWave inside a FLIP sim.
