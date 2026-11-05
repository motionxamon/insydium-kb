# Render NeXus particle data in Octane (color, radius → glass)

- Source: Top Tip Tuesday — Octane Particle Data — https://www.youtube.com/watch?v=9xKGBGKNyvc (2026-09-15)
- Host / generation: C4D, NeXus particles (cached) + Octane
- Goal: drive Octane materials per particle from baked particle color and animated radius.

## Steps
1. Cached NeXus sim (rotating/scaling spheres). In Octane, particles don't render until you add an **Octane Object tag** on the **xpEmitter** → Particle Rendering tab → enable **Geometry**. [▶ 1:08](https://youtu.be/9xKGBGKNyvc?t=68)
2. For correct size, make a **Sphere of 1 cm** (low segments) and drag it into the tag's geometry slot → instance size = particle radius. [▶ 1:27](https://youtu.be/9xKGBGKNyvc?t=87)
3. Put the material on the **instanced sphere**, not on the emitter. [▶ 2:28](https://youtu.be/9xKGBGKNyvc?t=148)
4. Node editor: **Generator ▸ Instance Color** → Source: Particle, link the **xpEmitter**. Color Mode: [▶ 3:20](https://youtu.be/9xKGBGKNyvc?t=200)
   - **Display Color** (default) → the baked viewport particle color (here random grayscale per particle). Remap with **Mapping ▸ Gradient Map** (e.g. a turquoise→orange preset) → base layer color.
   - **Radius** → set Min/Max radius of your sim (here 1–70 cm); outputs a gradient (or remap).
5. Glass for big particles: duplicate Instance Color in Radius mode with **Min 50 / Max 60** → black below 50, white above 60 → plug into **Transmission ▸ Weight** of the Standard Surface. Big spheres turn to glass and back as their radius animates. [▶ 10:16](https://youtu.be/9xKGBGKNyvc?t=616)
6. Specular roughness 0 for shiny balls.

## Notes
- Same idea in Redshift: RS Particle/User Data nodes (see "Particle Data in Redshift" / "Rendering Particle Data" recipes).
- Bake whatever you want to render into particle color or radius in the sim (nxColor, nxScale, nxQuestion) — renderers can read those reliably.
