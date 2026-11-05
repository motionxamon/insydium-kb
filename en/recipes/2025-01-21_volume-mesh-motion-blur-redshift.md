# Motion blur on a meshed fluid in Redshift (xpOpenVDBMesher Transfer Velocity → Redshift Object tag motion vectors)

- Source: Top Tip Tuesday — Motion Blur On Volume Meshes — https://www.youtube.com/watch?v=zZxnTC2jJm0 (2025-01-21)
- Host / generation: C4D; NeXus G2 nxFluids (high surface tension) + CPU **xpOpenVDBMesher**; Redshift
- Goal: real deformation blur on a volume mesh whose point count changes every frame.

## Base
Cached nxFluids sim (≈3.5 min cache). **xpOpenVDBMesher** ▸ General meshing that emitter, light curvature smoothing; Redshift material.

## Steps
1. Mesher ▸ **Tags** tab ▸ enable **Transfer Velocity** → creates a color map plus X/Y/Z vertex maps carrying particle velocity.
2. Mesh ▸ **Redshift Object tag ▸ Motion Blur**: enable **Motion Vector**, drop the X, Y, Z maps into their link fields.
3. Render Settings ▸ Redshift ▸ Advanced ▸ Motion Blur: **Motion Blur on** + **Deformation Blur on**.
4. Render to Picture Viewer (IPR doesn't show it). Default is barely visible → Redshift tag **Scale ~20**; 25 is a sensible final.
5. Very high scales (e.g. 60) give speckly artefacts: neighbouring vertices have wildly different velocities. Fix with mesher Tags ▸ velocity **Smoothing ~20**.

## Gotchas
Standard object motion blur fails on volume meshes because vertices can't be tracked frame to frame — use the velocity maps.

## Newest equivalent
GPU **nxMesher** (Fused 2025.4) outputs color/velocity/emitter IDs directly — mesh with it and wire its velocity into the Redshift tag the same way.
