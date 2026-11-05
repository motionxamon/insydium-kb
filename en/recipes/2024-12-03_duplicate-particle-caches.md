# Populate a scene from one particle cache (xpCache local coordinates, Copy Tag Data, per-tag offset)

- Source: Top Tip Tuesday — Duplicate Particle Caches — https://www.youtube.com/watch?v=dA4cn2wx47A (2024-12-03)
- Host / generation: C4D; emitter + nxTurbulence sim, **xpCache** (CPU caching system, works for NeXus too)
- Goal: many varied smoke-like plumes for backgrounds from a single cache.

## Steps
1. **xpCache**: external files, compress on build → Build (2000 F ≈ 1.5 min here).
2. Moving a cached emitter does nothing → xpCache ▸ **Playback ▸ Local Coordinates** → cache follows the emitter; in Object mode you can **scale** (even non-uniformly) and rotate it.
3. Duplicates: on the emitter's cache tag enable **Copy Tag Data** before Ctrl-dragging → the copy's tag stays linked (red) to the same cache (otherwise green = no data).
4. Per-copy variation on each **cache tag**: **Override cache object settings** → Local Coordinates on + **Offset** (e.g. 100, 200, 250 frames) so plumes are at different stages.
5. Move / rotate / scale each copy → a full background from one sim.
