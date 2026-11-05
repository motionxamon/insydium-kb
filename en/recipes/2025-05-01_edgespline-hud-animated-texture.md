# Animated HUD scan lines from a texture (mtEdgeSpline Texture Tag mapping, Planes, Dashes)

- Source: Bite-Sized — EdgeSpline HUD — https://www.youtube.com/watch?v=LTAiSYatydQ (2025-05-01)
- Host / generation: C4D; MeshTools **mtEdgeSpline** (no particles); Redshift for the source scan
- Goal: turn an animated luminance texture into flickering layered HUD-style spline graphics.

## Base
A plane with a standard material carrying an animated texture in the **Luminance** channel (in the demo a fake MRI scan made with the Redshift camera **Clipping Plane** moved through an object). Hide it once the texture is ready.

## Steps
1. New **Plane** as the input mesh; raise Width/Height Segments to ~80–90 for detail.
2. INSYDIUM ▸ MeshTools ▸ **mtEdgeSpline**, plane as child → splines along the quad edges. Turn off the gradient display and hide the mesh.
3. Object tab ▸ Mapping ▸ **Texture Source: Texture Tag**, drop in the texture tag of the source plane (its projection is reused as-is).
4. Set the channel from Color (default) to **Luminance** → only edges where the texture is bright survive, so the scan animates through the splines.
5. Tweak **Tolerance** (how much comes through), **Growth** (wipe the result across) and its offsets.
6. **Planes**: U only / V only gives single-direction scan lines; Combined = grid. Offsets stretch the lines; enable **dash lines** for a crosshatch / crosshair pattern.
7. Layering: duplicate the setup, scale/offset the base plane, change colour (blue, then red), lower segment counts, vary dash/plane settings per copy — each layer flickers differently.

## Gotchas
- Too few segments on the input plane = coarse, blocky spline response.

## Newest equivalent
Same tool today; Fused 2025.4.1 lets mtEdgeSpline handle n-gons, so non-quad input meshes also work.
