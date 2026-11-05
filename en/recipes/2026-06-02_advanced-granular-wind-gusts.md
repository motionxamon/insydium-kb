# Granular text blown apart by gusts mapped to animated Voronoi color

- Source: Top Tip Tuesday — Advanced Granular Sim — https://www.youtube.com/watch?v=zyN7ERz7yuw (2026-06-02)
- Host / generation: C4D, NeXus (nxFluids SPH Granular, nxWind Von Karman, Mapping) + CPU xpColor (for Maxon 3D shaders)
- Goal: sand letters that erode in irregular chunks under gusty wind.

## Steps
1. Emitter: Object = Text (volume), **Shot – Hexagonal**, Full Lifespan, speed 0, radius 1 (~100 k draft). Particle count is set by radius: 0.4 → ~1.5 M; 0.2 → 8–10 M for close-ups. [▶ 0:37](https://youtu.be/zyN7ERz7yuw?t=37)
2. **xpColor** (CPU) with a Maxon **Noise shader: Cell Voronoi**, global scale ~330, strong low/high clip → patchy black/white per particle. (CPU modifier used because it samples Maxon shaders in full 3D; nxColor has GPU noises.) [▶ 1:18](https://youtu.be/zyN7ERz7yuw?t=78)
3. Make the pattern jump occasionally: keyframe the noise **Seed** (+1 every 2 frames, linear, Track After: Continue) and keyframe xpColor **Enabled** on/off pulses (frames 0–2, 50, 100, 150) → recolor only at chosen moments. [▶ 2:42](https://youtu.be/zyN7ERz7yuw?t=162)
4. **nxFluids SPH → Granular**; Substeps **30, adaptive off**; Friction ~50, Stability ~3 (raise to ~6 for smaller particles), Cohesion ~7. Add **nxGravity**. [▶ 4:08](https://youtu.be/zyN7ERz7yuw?t=248)
5. **nxWind** mode **Von Karman**, diagonal direction, Strength ~3500 with high variation, lower turbulence, add Friction Velocity. [▶ 5:25](https://youtu.be/zyN7ERz7yuw?t=325)
6. **Mapping tab** on nxWind: Wind Strength ← **Color (Brightness)**, Range Min 0.5 → full strength at 0.9 → only light patches blow away; darker stay. [▶ 6:05](https://youtu.be/zyN7ERz7yuw?t=365)
7. Ease in: keyframe Wind Strength 0 → full over ~15 frames (can't map it twice). [▶ 7:53](https://youtu.be/zyN7ERz7yuw?t=473)
8. Render particles (Redshift) for dusty clumps; color is only a driver, not rendered. [▶ 9:38](https://youtu.be/zyN7ERz7yuw?t=578)

## Newest equivalent
nxMPM Sand/Snow (2026.1 beta) gives more physical clumping; the color-mapping idea still applies via Mapping.
