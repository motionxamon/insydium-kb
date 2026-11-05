# Render particle color and radius as Redshift ramp color + glass weight (Change Range from xpConsole)

- Source: Top Tip Tuesday — Rendering Particle Data — https://www.youtube.com/watch?v=7BzLibj9f8U (2025-07-01)
- Host / generation: cached NeXus/XP sim + Redshift (Object tag sphere instances)
- Goal: abstract spheres: palette from particle color, big ones turn to glass.

## Steps
1. Studio HDRI from Asset Browser; big backdrop plane (+Z, 4000×4000). [▶ 0:47](https://youtu.be/7BzLibj9f8U?t=47)
2. Emitter ▸ **Redshift Object tag ▸ Particles ▸ Sphere instances**. [▶ 1:17](https://youtu.be/7BzLibj9f8U?t=77)
3. Material: **Color User Data** ▸ preset Particles ▸ Particle Color (random B/W) → **Ramp** (preset palette) → Base Color; low roughness. [▶ 2:26](https://youtu.be/7BzLibj9f8U?t=146)
4. Radius: **Scalar User Data** ▸ preset Particles ▸ **Size** → **Change Range**. Find old min/max with **xpConsole** (Data to Display ▸ Radius; double-click column = min/max; here 1 → 104). [▶ 5:57](https://youtu.be/7BzLibj9f8U?t=357)
5. Ctrl-click Transmission **Weight** to expose its port, feed the Change Range; tune old range to **35 → 60** so only large ones become glass. [▶ 6:50](https://youtu.be/7BzLibj9f8U?t=410)
6. Backdrop material = one ramp color (copy the knot), roughness 1 → coherent palette. [▶ 8:42](https://youtu.be/7BzLibj9f8U?t=522)
