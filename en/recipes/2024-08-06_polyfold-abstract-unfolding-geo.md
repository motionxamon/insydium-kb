# Abstract unfolding strips with thickness and teeth (MeshTools mtPolyFold + mtShellGen + mtInset + mtSubDivider)

- Source: Top Tip Tuesday — PolyFold Abstract Geo — https://www.youtube.com/watch?v=V6yMgNIK5B8 (2024-08-06)
- Host / generation: C4D; **MeshTools** procedural stack (mtPolyFold arrived in Fused 2024.2); no particles
- Goal: a squashed torus that unrolls/rolls up in a spiralling wave, with a thick, toothed, smoothed surface.

## Base
Editable, squashed Torus with clean quad flow (PolyFold needs good loops; messy/triangulated meshes unfold poorly). Polygon mode ▸ **Loop Selection (U~L)** a ring of polys ▸ Select ▸ **Set Selection** (polygon selection tag).

## Steps
1. Torus selected, Alt-add **mtPolyFold** (Alt = parent the generator). Default: Distribution Random, 1 point, 50 % unfold.
2. Distribution **Selection** → drag in the polygon selection tag; direction Clockwise (or Anticlockwise).
3. Keyframe the unfold: **100 % at F0 → 0 % at F119**.
4. **Variation ~4 %** offsets the fold rate per strip → spiral. Key Variation back to 0 at the end key (and 4 % at ~F80) so the shape lands cleanly.
5. Broken shading at rest = disconnected polys → **Advanced ▸ Optimize** re-welds.
6. Lower the fold **Angle** for looser curls (keyable too).
7. Alt-add **mtShellGen**, Thickness **2**. Its **Selections** tab ▸ **Caps** creates a selection of the inner faces.
8. Alt-add **mtInset**, restricted to that caps selection; amount full + some offset → raised "teeth" along the strips.
9. Alt-add **mtSubDivider** on top to smooth.

## Gotchas
- Every MeshTools object goes in as the parent of the previous one (Alt-click), so the stack evaluates in order.
