# MeshTools (C4D, part of INSYDIUM Fused)

Source: docs.insydium.ltd/meshtools/* (Fused 2025, checked 2026-11-03). Paraphrased.

**Concept:** non-destructive procedural generators. Put an `mt*` object as the **parent** of the source geometry; nest several to stack (order in hierarchy = order of operations). Almost all tools are driven by a **Selection Map** (selection tag / vertex map), a **Texture Source** (shader / texture tag / video — needs a C4D material when using Texture Tag mode) with **Tolerance** (brightness cutoff: lower = more area), or **C4D Fields**. Everything is keyframable → animate growth by animating a field/shader/vertex map (e.g. from xpVertexMap). **Optimize** removes duplicate points.

| Tool | What it does | Notes |
|---|---|---|
| **mtInset** | procedural inner extrusions per face | Inset Mode % of face or fixed length, Variation, Offset, Twist, Shape; animate offset/variation or a shader → growing tech panels ("inset growth" Top Tip) |
| **mtPolyScale** | shrink individual polygons | Amount, Variation, Seed → dissolve/grow-in effects |
| **mtPolyFold** | origami unfold of polygons along a path | Unfold 100% flat/0% folded; Distribution Random/Selection/Texture; Remove Offset makes polys "disappear" |
| **mtShellGen** | extrude polygons into shells with hull/caps | Thickness, Steps, Max Angle, Bevel |
| **mtSubDivider** | subdivide where map/texture says | levels, Bilinear Offset mode (axis offset, probability) |
| **mtSelect** | generate point/edge/poly selections from maps/textures | Hide Faces (generated or not) → reveal/hide by animated shader |
| **mtDualGraph** | dual-graph topology (hex/voronoi-like cells) | Quads / Quads-Tris |
| **mtRemesh** | uniform or adaptive triangle remesh | Features Angle (0° = nothing), Edge Length / Min-Max + Gradation; good before cloth/sim |
| **mtPointProject** | project points onto colliders by rays | Offset, Blend, Distance Falloff (shrink-wrap) |
| **mtEdgeSpline** | splines from mesh: Standard / Curvature / **Contour** / **Outline** (camera-dependent toon lines) / Intersection | Join Segments |
| **mtShortestPath** | splines along edges between start/end vertices | each start → every end; Avoid; **Spline Growth** rate % per frame (circuit/vein growth) |
| **mtSplineFX** | spline connections between start & end objects/particles | Connection Origin/Points/Surface; noise Motion; **Growth Start/End**; Gravity/Tension; **Forks** (count/length/angle) → procedural **lightning rig**; avoid objects |
| **mtSplineSample** | resample splines evenly | Uniform / Natural / Distance; Growth Start/End |
| **mtRayline** | raycast splines that bounce off colliders | Shape Center/Circle/Line/Custom Object/**X-Particles** (rays from particles); Single Shot vs bounce; Ray Count/Length; keyframe Start/End → **lasers / light beams** (Top Tip "mtRayline Lasers", "Rayline Particles"); turn off Display Gradient |
| **mtFractal** | scatter child clones on fractal patterns: Tree (default), Dragon, Fern, Fibonacci, Koch, Sphere | Clone Type Render Instance; Mesh center = one fractal per polygon; Fern explodes with iterations |

Render splines from mtEdgeSpline/mtSplineFX/mtRayline with Sweep, xpSplineMesher, or renderer hair/spline objects. Combine with X-Particles: emit from MeshTools output, or use xpDynamics/cloth on mt-generated meshes ("dynamic MeshTools" Top Tip).
