# Motion blur on a meshed fluid in Redshift (xpOpenVDBMesher Transfer Velocity → Redshift Object tag motion vectors)

- Source: Top Tip Tuesday — Motion Blur On Volume Meshes — https://www.youtube.com/watch?v=zZxnTC2jJm0 (2025-01-21)
- Host / generation: C4D; NeXus G2 nxFluids (high surface tension) + CPU **xpOpenVDBMesher**; Redshift
- Goal: real deformation blur on a volume mesh whose point count changes every frame.

## Base
Cached nxFluids sim (≈3.5 min cache). **xpOpenVDBMesher** ▸ General meshing that emitter, light curvature smoothing; Redshift material.

## Steps
1. Mesher ▸ **Tags** tab ▸ enable **Transfer Velocity** → creates a color map plus X/Y/Z vertex maps carrying particle velocity. [▶ 1:50](https://youtu.be/zZxnTC2jJm0?t=110)
2. Mesh ▸ **Redshift Object tag ▸ Motion Blur**: enable **Motion Vector**, drop the X, Y, Z maps into their link fields. [▶ 2:34](https://youtu.be/zZxnTC2jJm0?t=154)
3. Render Settings ▸ Redshift ▸ Advanced ▸ Motion Blur: **Motion Blur on** + **Deformation Blur on**. [▶ 2:51](https://youtu.be/zZxnTC2jJm0?t=171)
4. Render to Picture Viewer (IPR doesn't show it). Default is barely visible → Redshift tag **Scale ~20**; 25 is a sensible final. [▶ 3:31](https://youtu.be/zZxnTC2jJm0?t=211)
5. Very high scales (e.g. 60) give speckly artefacts: neighbouring vertices have wildly different velocities. Fix with mesher Tags ▸ velocity **Smoothing ~20**. [▶ 4:48](https://youtu.be/zZxnTC2jJm0?t=288)

## Gotchas
Standard object motion blur fails on volume meshes because vertices can't be tracked frame to frame — use the velocity maps.

## Newest equivalent
GPU **nxMesher** (Fused 2025.4) outputs color/velocity/emitter IDs directly — mesh with it and wire its velocity into the Redshift tag the same way.
