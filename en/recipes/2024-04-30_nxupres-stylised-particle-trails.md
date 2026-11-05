# Organic particle-trail swarm from a low-res cache (nxConstraints + nxTurbulence → nxUpres)

- Source: Top Tip Tuesday — NeXus Particle Trails — https://www.youtube.com/watch?v=kDZyYaCgHb8 (2024-04-30)
- Host / generation: C4D; NeXus inside X-Particles (G2: xpEmitter + nxConstraints, nxTurbulence, nxUpres) + xpCache
- Goal: use nxUpres as a stylistic tool, not just for resolution — a coherent, ribbon-like body of trails instead of noise-scattered dots.

## Base
Sphere with a **Vibrate tag** (regular pulse, X amplitude) as the emitter source; xpEmitter Object mode, polygon area; Rate 50/frame, lifespan 60, speed 0. **Motion Inheritance** on, Speed Blend 50 — the only motion source.

## Steps
1. **nxConstraints**: Iterations 3; **Birth** layer — up to 13 connections within radius 30, very low stiffness (stretchy), **Break Type: None**. Particles now move as one body. [▶ 1:39](https://youtu.be/kDZyYaCgHb8?t=99)
2. **nxTurbulence** Voronoi: strong, smaller scale, very low frequency, octaves way up; then **lower Persistence** to bring back the large swirls lost to high octaves. [▶ 2:45](https://youtu.be/kDZyYaCgHb8?t=165)
3. **xpCache** to external files with **Compress Cache on Build off** (faster build, bigger files). ~700 F cached in seconds. Optionally delete/disable the modifiers after caching. [▶ 3:11](https://youtu.be/kDZyYaCgHb8?t=191)
4. Duplicate the emitter as the **destination** (remove its cache): lifespan 40 (var 10), Rate 1000, display Dots, color **Gradient Parameter** mapped to Speed. [▶ 4:18](https://youtu.be/kDZyYaCgHb8?t=258)
5. **nxUpres**: Source = cached emitter, Destination = new emitter. Particles-to-blend default 3 nearest (velocity blend); raised to ~7 for smoother results. [▶ 4:39](https://youtu.be/kDZyYaCgHb8?t=279)
6. Enable **Position** blending too — at full strength the sim collapses inward; lower its strength to restore volume. [▶ 5:32](https://youtu.be/kDZyYaCgHb8?t=332)
7. Raise destination Rate 1000 → 5000 and rebuild the cache with **Continue** so the cached base particles aren't re-simulated (≈5 min in the demo). [▶ 6:05](https://youtu.be/kDZyYaCgHb8?t=365)

## Gotchas
- Without Continue the cache tries to rebuild the base sim too.
- Higher blend count = smoother but slower.

## Newest equivalent
Same nxUpres workflow in NeXus 2026 (nxEmitter + nxCache, C4D 2026.1 beta / Blender). nxTrail can turn the upres'd particles into splines.
