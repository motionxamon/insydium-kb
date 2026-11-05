# Particles growing over a procedural wire mesh (mtEdgeSpline, mtSplineFX, xpSplineMesher, xpVertexMap Seed, nxQuestion Set Radius, nxPush)

- Source: Bite-Sized — Wired Growth — https://www.youtube.com/watch?v=rDSSeIZUl08 (2025-11-06)
- Host / generation: C4D; MeshTools + CPU xpEmitter/xpVertexMap with NeXus nxQuestion/nxPush (G2)
- Goal: a procedural wire cage linking two nested platonics, then spheres that grow organically across it from seed points.

## Steps
1. Two **Platonic** objects, the second a scaled-up copy. Two **mtEdgeSpline** objects (display gradient off), one platonic parented under each; hide the platonics.
2. **xpEmitter** ▸ Emitter Source Object = platonic 1, Emit From **Points**, enable **One Particle per Source Element**; Emission **Shot**, mode Simulate, speed off; raise display size factor. Duplicate it for platonic 2.
3. **mtSplineFX**: Start Emitter / End Emitter = the two emitters, Connection Type Origin → **Points** (arcs between matching points); motion-noise amplitudes 0; gradient off.
4. **xpSplineMesher** (X-Particles ▸ Generators): objects = both edge splines + the SplineFX spline; Joins off, Size **2**. Group the splines in a null (Alt+G) and hide — the rig stays procedural.
5. **xpVertexMap** (X-Particles ▸ Utilities) on the spline mesher: mode Polygon → **Seed Object**, add 3 seeds intersecting the mesh (scale up); **Search Radius 5** → the map grows on play.
6. Break up the growth: add a **Noise** shader to the vertex map; Effects ▸ a little **Contrast**.
7. Second **xpEmitter**: Surface of the spline mesher, Selection = the vertex map, **Polygon Area**, speed off, radius **0**; display as Spheres.
8. **nxQuestion**: Age > 0 → Action **Set Radius 5** (later **3**), Weight ≈ **10%** so radius eases in.
9. **nxPush**: mode **Particle Radius**, maximum strength → spheres jostle apart as they grow.

## Gotchas
- Seeds must actually intersect the geometry or nothing grows.
- Emitting at radius 0 means nothing shows until the question grows them.

## Newest equivalent
Same rig works in Fused 2025.4.x (mtEdgeSpline handles n-gons from 2025.4.1). In the 2026.1 beta, nxFalloff Wet / Points modes or nxFalloff Modifier Grow/Decay can drive the growth instead of xpVertexMap, and **nxBioLogic** (differential growth, coral) is the GPU route to fully organic surface growth.
