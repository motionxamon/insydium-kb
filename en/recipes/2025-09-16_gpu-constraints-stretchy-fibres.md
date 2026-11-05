# Stretching and snapping fibres (nxConstraints Birth + constraint trails + xpTrailDeformer)

- Source: Top Tip Tuesday — GPU Constraints Sim — https://www.youtube.com/watch?v=_7bYCGydqXo (2025-09-16)
- Host / generation: NeXus (nxConstraints, nxFluids SPH, nxKill) + CPU xpTrail / xpTrailDeformer
- Goal: gooey strands that stretch between particles and snap, rendered as soft curvy fibres.

## Steps
1. Animated emitter spraying onto a tube collider; **nxGravity 400**; **nxFluids SPH** substeps 6 (P-P interaction); **nxKill** bounds. [▶ 0:27](https://youtu.be/_7bYCGydqXo?t=27)
2. **nxConstraints → Connections Birth**: Connection Limit 8, Radius ~20. Show links: emitter Display ▸ **Display Constraints**. [▶ 1:21](https://youtu.be/_7bYCGydqXo?t=81)
3. Links snap at the default **Break 50% (Relative Connected)** → **Break 500%**, lower **Stiffness** (stretchier). [▶ 2:22](https://youtu.be/_7bYCGydqXo?t=142)
4. Renderable lines: **xpTrail** → **Algorithm: Constraints → Birth** (instead of tracing paths). [▶ 3:27](https://youtu.be/_7bYCGydqXo?t=207)
5. Constraints are straight point-to-point → soften: xpTrail Spline **Intermediate Points Uniform 8** + child **xpTrailDeformer** (formula on Y, small **Amplitude ~1 cm**, tuned Wavelength); use the deformer's spline so the ends don't move (0 at start/end, full in the middle). [▶ 5:12](https://youtu.be/_7bYCGydqXo?t=312)
