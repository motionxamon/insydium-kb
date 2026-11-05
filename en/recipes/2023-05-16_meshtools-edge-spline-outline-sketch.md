# Dynamic 2D pencil-sketch look on an animated character (mtEdgeSpline Outline mode)

- Source: Top Tip Tuesday — MeshTools Sketch Mouse — https://www.youtube.com/watch?v=tApA-55P7FM (2023-05-16)
- Host / generation: C4D; MeshTools (no particles); standard viewport/renderer
- Goal: camera-dependent outline + hatching strokes that follow a rigged 3D model.

## Base
C4D Asset Browser ▸ Example Scenes ▸ Character Animation ▸ rigged **Mouse** scene (camera/lights removed, rig controls hidden).

## Steps
1. INSYDIUM ▸ MeshTools ▸ **mtEdgeSpline**; make the mouse its child. Default **Standard** mode = a spline per polygon edge (good for HUD/FUI looks).
2. Mode **Curvature**: Curvature Angle 0 = same as Standard; raise it to keep splines only on curvy areas (static, not view-dependent).
3. Mode **Outline**: splines follow the silhouette relative to the camera and update as the camera or rig moves.
4. 2D staging: C4D **Sky** with Basic ▸ display color custom white; mouse gets a white luminance-only material; mtEdgeSpline spline color → charcoal gray.
5. Raise **Outline Angle** → strokes creep inward like shading.
6. Cross-hatch: **Start Offset / End Offset ≈ 0.05 cm** (tiny model) so strokes overshoot and cross.

## Gotchas
Offsets are in scene units — scale them to the model size.
