# Feature notes: mtPointProject and new mtSubdivider modes (MeshTools 2024.2)

- Source: MeshTools Sneak Peek — Project Objects and Splines onto Scene Geo, Release Update Coming Soon — https://www.youtube.com/watch?v=LPsWJoXKhQk (2024-05-02)
- Host / generation: C4D; MeshTools (procedural modelling); one demo emits NeXus particles from the result
- Status: preview of **Fused 2024.2** (9 May 2024)

## mtPointProject (new)
- Projects the points of any child object or **spline** (e.g. text spline) onto a **Surface** object (rock).
- Modes include **+Z** and **Parallel +Y / −Y** (push up or down onto the surface).
- **Blend** slider: 0 = original position, 100 = fully projected (e.g. 97 to keep a hint of the source shape).
- Live: surface can be keyframed or deformed, source can be animated (animated cross on a deforming surface) — projection stays consistent.
- An emitter can emit straight from the mtPointProject object → NeXus particles born from the letters on the rock surface.

## mtSubdivider — four extra modes besides Bilinear
- **Bilinear Offset**: offsets subdivided polygons for tiling patterns.
- **Shards**: splits each parent polygon into adjustable shards with a detail control spline.
- **Whirl**: interlocking outer polygons; Strength sets the inner polygon size.
- **Catmull-Clark**: smoothing mode, e.g. a second subdivider over an animated mtInset for rounded offsets.
- Driven by Fields/shaders (linear or circular gradient = subdivision radiating from the centre); stackable with mtInset and the rest of MeshTools; all parameters keyframable.

## Newest equivalent
Shipped in Fused 2024.2; see "Projected spline emission on an animated surface" (2024-07-02). Emitting from the projected geometry works the same with an nxEmitter in NeXus 2026.
