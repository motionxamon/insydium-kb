# Micro-cell look in Redshift (Fresnel-opacity emissive spheres inside a dispersive glass mesh)

- Source: Top Tip Tuesday — Redshift Cellular Particles — https://www.youtube.com/watch?v=t6WmbzfNxGU (2025-04-22)
- Host / generation: C4D; X-Particles cached sim + CPU **xpOpenVDBMesher**; Redshift (object tag sphere instances)
- Goal: glowing, rim-lit "cells" seen through a refractive, colour-split skin.

## Base
Cached particle cell animation; emitter has a **Redshift Object tag ▸ Particles ▸ Sphere instances**; xpOpenVDBMesher meshing the same particles. No lights needed in the end (particles emit).

## Steps
1. Particle material (Standard): **Base Color weight off, Reflection off, Emission weight 2** (raised later). [▶ 1:22](https://youtu.be/t6WmbzfNxGU?t=82)
2. **Fresnel** node, **Use IOR off**, curve **3** → output into **Geometry ▸ Opacity**: facing = transparent, edges = opaque rings. [▶ 2:55](https://youtu.be/t6WmbzfNxGU?t=175)
3. Redshift tag ▸ instance **Scale Multiplier 0.5** so spheres sit inside the mesh. [▶ 3:16](https://youtu.be/t6WmbzfNxGU?t=196)
4. **Color User Data** ▸ preset **Particles ▸ Particle Color** → Emission Color (Ctrl-click the port button to expose the input). [▶ 3:42](https://youtu.be/t6WmbzfNxGU?t=222)
5. Mesher material: Base Color off, **Transmission weight 1**, Reflection roughness 0, **IOR 1.1** (edge-only reflections). [▶ 4:55](https://youtu.be/t6WmbzfNxGU?t=295)
6. Magic: **Dispersion (Abbe) 0.1** — lower = stronger colour separation (1 barely visible). [▶ 5:53](https://youtu.be/t6WmbzfNxGU?t=353)
7. Tune: thinner rims with Fresnel curve **5–7**, then raise particle **Emission to ~4–10** to compensate. [▶ 6:14](https://youtu.be/t6WmbzfNxGU?t=374)

## Gotchas
Particles inside the mesh render black until the mesher material is transmissive.

## Newest equivalent
Swap xpOpenVDBMesher for GPU **nxMesher** (Fused 2025.4; flicker-free, outputs colour/velocity) — the Redshift shading is unchanged.
