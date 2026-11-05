# Micro-cell look in Redshift (Fresnel-opacity emissive spheres inside a dispersive glass mesh)

- Source: Top Tip Tuesday — Redshift Cellular Particles — https://www.youtube.com/watch?v=t6WmbzfNxGU (2025-04-22)
- Host / generation: C4D; X-Particles cached sim + CPU **xpOpenVDBMesher**; Redshift (object tag sphere instances)
- Goal: glowing, rim-lit "cells" seen through a refractive, colour-split skin.

## Base
Cached particle cell animation; emitter has a **Redshift Object tag ▸ Particles ▸ Sphere instances**; xpOpenVDBMesher meshing the same particles. No lights needed in the end (particles emit).

## Steps
1. Particle material (Standard): **Base Color weight off, Reflection off, Emission weight 2** (raised later).
2. **Fresnel** node, **Use IOR off**, curve **3** → output into **Geometry ▸ Opacity**: facing = transparent, edges = opaque rings.
3. Redshift tag ▸ instance **Scale Multiplier 0.5** so spheres sit inside the mesh.
4. **Color User Data** ▸ preset **Particles ▸ Particle Color** → Emission Color (Ctrl-click the port button to expose the input).
5. Mesher material: Base Color off, **Transmission weight 1**, Reflection roughness 0, **IOR 1.1** (edge-only reflections).
6. Magic: **Dispersion (Abbe) 0.1** — lower = stronger colour separation (1 barely visible).
7. Tune: thinner rims with Fresnel curve **5–7**, then raise particle **Emission to ~4–10** to compensate.

## Gotchas
Particles inside the mesh render black until the mesher material is transmissive.

## Newest equivalent
Swap xpOpenVDBMesher for GPU **nxMesher** (Fused 2025.4; flicker-free, outputs colour/velocity) — the Redshift shading is unchanged.
