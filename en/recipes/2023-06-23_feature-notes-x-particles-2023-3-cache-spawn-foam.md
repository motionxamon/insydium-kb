# Feature notes: X-Particles 2023.3 — live spawn/foam from caches, multi-instances, stuck rotation, xpSplineMesher Planar (Fused 2023.3)

- Source: INSYDIUM Fused Release Update — July 2023 - X-Particles Sneak Peek — https://www.youtube.com/watch?v=VDzTxgva3dc (2023-06-23)
- Host / generation: C4D; G1 CPU X-Particles (xp*), interchangeable with NeXus caches
- Goal: overview of the CPU X-Particles additions in July 2023.

## Live effects from cached scenes
- **xpSpawn** from a cached sim: cached xpExplosiaFX (velocity) + cached advected particles → add xpSpawn with a spawning emitter, play → spawned particles still advected by the cached smoke. Raise Spread and add speed → up-res of a low-count cache. Same for **xpFluidFLIP** caches.
- **xpFoam** on a cached fluid with none of the original modifiers: add xpFoam + foam emitter + gravity → live foam. Also works with NeXus fluids; CPU and GPU caches/foam are interchangeable.

## Other additions
- **xpScatter** and **xpGenerator** support **multi-instances** → heavy instanced detail stays playable.
- **xpEmitter** new rotation mode for correct orientation of **stuck** particles (enable **Local Rotation**).
- **xpSplineMesher ▸ Planar** mode: ribbons from xpTrail splines or any spline; **Plane Up** orients faces, size, pointed end; works live while trails draw; **Growth** slider for animation.

## Newest equivalent
GPU: **nxUpres** / **nxSpawn** (2026.1 beta) for up-res and spawning, nxFoam layers (2025.4), nxTrail for trails; xpSplineMesher remains the CPU ribbon mesher.
