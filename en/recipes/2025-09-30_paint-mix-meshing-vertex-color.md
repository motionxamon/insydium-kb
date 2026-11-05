# Mesh a color-blending paint sim and render vertex color (xpOpenVDBMesher → Redshift)

- Source: Top Tip Tuesday — Paint Mix Meshing — https://www.youtube.com/watch?v=oHF1dIMGtUs (2025-09-30)
- Host / generation: C4D, NeXus sim (nxBlend) + **CPU xpOpenVDBMesher** (pre-nxMesher era) + Redshift
- Goal: render the mixed paint from "Paint Mix Sim" with smooth color transitions.

## Steps
1. **xpOpenVDBMesher** with all three emitters. Vertex color needs a dense mesh → **Voxel Size 1**; **Point Radius 2** (less blobby).
2. Filters: remove default Median; **Laplacian ×2** + **Curvature ×1** (good fluid combo).
3. Tags tab: **Transfer Point Color** → color vertex map on the mesher; **Smoothing iterations ~20** removes noisy color seams.
4. Redshift: SSS material (weight 1, scale 4) → Ctrl-click Subsurface Color to add an input → **Vertex Attribute** node with the color map.

## Newest equivalent
Since Fused 2025.4 use **nxMesher** (GPU): Export Tags ▸ Transfer Color + color smoothing, Zhu-Bridson or Spheres + Mean Curvature (see "nxMesher Export Tags").
