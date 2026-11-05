# Choosing a Redshift particle instance mode (Redshift Object tag ▸ Particles: points, quads, spheres, custom objects)

- Source: Bite-Sized — Redshift Particle Instances — https://www.youtube.com/watch?v=qOTF_oVXI1c (2025-09-25)
- Host / generation: C4D + **Redshift**; plain **xpEmitter** (varied radius, mild spin), no modifiers
- Goal: know what each Redshift instance mode renders and when to use it.

## Steps
1. Emitter ▸ Tags ▸ Render tags ▸ **Redshift Object tag** → a **Particles** tab appears. Mode defaults to **Disabled** (nothing renders). [▶ 0:35](https://youtu.be/qOTF_oVXI1c?t=35)
2. **Point instances**: camera-facing discs. Very light on VRAM/time → best for millions of tiny particles with additive materials. [▶ 10:16](https://youtu.be/qOTF_oVXI1c?t=616)
3. **Quad instances**: camera-facing quads; ignore particle rotation. [▶ 2:34](https://youtu.be/qOTF_oVXI1c?t=154)
4. **Optimized spheres**: a shading trick, not real volume — intersections shade wrongly and transmission **depth/scatter** has no effect. [▶ 3:37](https://youtu.be/qOTF_oVXI1c?t=217)
5. **Sphere instances**: real sphere geometry → correct intersections and translucent glass (Transmission full, scatter color, **Depth ~25%** and up). Best choice for plain spheres. [▶ 5:35](https://youtu.be/qOTF_oVXI1c?t=335)
6. **Custom objects**: any scene geometry instanced per particle, respecting rotation. Size reference: a primitive Sphere **radius 1 cm** = exact particle radius. [▶ 6:58](https://youtu.be/qOTF_oVXI1c?t=418)
7. Several custom objects (e.g. three spheres with different materials) are assigned **sequentially by particle ID** (1,2,3,1…) or set Distribution to **Random**. [▶ 8:44](https://youtu.be/qOTF_oVXI1c?t=524)
8. Cube: use **2×2×2 cm** (particle size is a radius, cube size is full edge length) to match the viewport. [▶ 9:57](https://youtu.be/qOTF_oVXI1c?t=597)

## Gotchas
- In Custom objects mode the material must sit on the instanced object, not on the emitter (otherwise grey render).
