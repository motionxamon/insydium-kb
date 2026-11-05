# Stringy fluid orbiting multiple splines (nxFollowGeo Force mode + PBD)

- Source: Top Tip Tuesday — Spline Flow — https://www.youtube.com/watch?v=5Ra6keP2ZgE (2025-11-18)
- Host / generation: C4D, Fused 2025.4 (then beta: new nxFollowGeo spline mode, PBD ease-in, layered nxTurbulence)
- Goal: a ribbon of liquid particles that flows around rotating circle splines, tearing into tendrils.

## Steps
1. Emitter: Rectangle height 0 / width 30 (thin ribbon), Rate 20 000/s for 90 frames, speed 150 ±, radius 1. [▶ 0:42](https://youtu.be/5Ra6keP2ZgE?t=42)
2. **nxFollowGeo** → spline = circle. Mode **Force** (not Guide) so fluids/turbulence still act. Raise Follow Strength; **Attract Strength ~400** to keep them on the path. [▶ 1:43](https://youtu.be/5Ra6keP2ZgE?t=103)
3. Release: default **Spline End** releases at the spline's end point → set **Time (Particle Age) = 0** → never release (loop forever). [▶ 2:22](https://youtu.be/5Ra6keP2ZgE?t=142)
4. Extended Data: delete the default **Offset** layer (20 cm) to hug the spline (or add Offset/Twist layers for spirals). [▶ 2:47](https://youtu.be/5Ra6keP2ZgE?t=167)
5. **nxFluids PBD** (stringy tendrils) → **Ease In 15 frames** (prevents the density blast from overlapping newborns). **External Pressure** high; optional slight viscosity; scale Attraction & Repulsion up together (same ratio) for more strings. [▶ 3:42](https://youtu.be/5Ra6keP2ZgE?t=222)
6. **nxTurbulence** layered: Voronoi strength 18–26, scale 222, 8 octaves, low persistence, lower frequency; lower follow strength a little. [▶ 4:24](https://youtu.be/5Ra6keP2ZgE?t=264)
7. Multiple splines: **Hierarchy** on = child splines use the same settings; off = add each spline separately (e.g. reverse direction on one). Release **Spline End** again → particles jump to the nearest spline and keep circulating. [▶ 7:10](https://youtu.be/5Ra6keP2ZgE?t=430)
