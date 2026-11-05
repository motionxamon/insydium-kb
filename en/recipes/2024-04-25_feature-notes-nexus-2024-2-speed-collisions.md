# Feature notes: NeXus 2024.2 core rebuild — faster GPU solve and animated-geometry collisions

- Source: NeXus Sneak Peek — GPU Particles Speed Boost, Release Update Coming Soon 2024.2 — https://www.youtube.com/watch?v=uZ3pdgC6qOw (2024-04-25)
- Host / generation: C4D; NeXus GPU (nx…) inside X-Particles (orange xpEmitters) — G2
- Status: preview of **Fused 2024.2** (9 May 2024)

## What changed
- NeXus core rebuilt: **faster GPU sorting**, smarter shader execution, **less VRAM**.
- New **particle-to-object collisions**: dense meshes (and a Subdivision Surface quadrupling the poly count) collide with almost no slowdown and no leakage through the volume (checked from a camera inside the mesh).
- **Animated colliders** (deforming wolf head) no longer slow the sim much.
- Fluids, constraints and **nxPush** are faster too.

## Benchmarks shown (old release vs new, 200 frames unless noted)
| Scene | Old | New |
|---|---|---|
| Dense static collider (Kaiju) | 61 s | 5.6 s (>10×) |
| Low-poly animated collider | 26 s | 10.5 s (~2.5×) |
| nxPush radius packing | 32 s | 24.8 s |
| nxFluids + static and animated colliders (100 frames) | 144 s | 26 s |
- nxPush on GPU is far faster than the old CPU push-apart.

## Newest equivalent
Fused 2025.4 rewrote the GPU core again (faster, less VRAM), and NeXus 2026.1 runs one engine in C4D and Blender with **nxCollider** objects (adhesion, attraction, Fill Hollows).
