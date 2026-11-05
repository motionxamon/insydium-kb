# Living shatter countdown (xpShatter spline points + particle points, xpFlowField Along Spline, nxPush)

- Source: INSYDIUM LIVE! — September 2023 – NeXus, Taiao & X-Particles — https://www.youtube.com/watch?v=uS_zr-Jf178 (2023-09-27)
- Host / generation: C4D; CPU xpShatter + xpFlowField + **G2** nxPush on the same emitter
- Goal: a plane shattered around an animated 5-4-3-2-1 text spline, with drifting particles adding extra cells so the shards flow.

## Base
C4D **Text spline** keyframed to change number every second; a **plane** to shatter; a second, **orange plane** just below it; a light with shadows.

## Steps
1. Generators ▸ **xpShatter**, plane as child. Display: turn off Draw Cut Edges, temporarily on **Draw Shatter Points** (one point per shard).
2. Object tab: delete the default **Point Generator** under the **Voronoi** layer; drop the text spline under Voronoi instead.
3. Using spline vertices gives even, wrong-looking cells (Uniform 20 intermediate points) → switch to **generate points along the spline**, count **500**, then **offset** them from the spline → shards fan around the digits; stays procedural as the number changes.
4. Voronoi layer **Offset 3 cm** → gaps; enable the orange plane below and give the shards a dark material → stylised lit gaps with shadows.
5. **xpEmitter** ▸ Object = text spline, emit from **Edges**; **Shot 200**, Speed 0, Radius **2** (variation 1); Display Sphere for checking.
6. Dynamics ▸ **xpFlowField**: scale bounds to the text; Display Arrow (voxels to see all); **Cell size 15**.
7. Delete the default Random layer; add **Along Spline** layer = text spline; remove its 50 cm falloff (flat curve) and **Strength 100**.
8. Nothing moves — Flow Field is in **Direction** mode (aims, no speed) → emitter Speed **20** + variation → particles stream along the changing digits.
9. **nxPush** (Particle Radius distance) so particles shove each other; Display Squares + Display Size Factor.
10. Re-enable shatter + plane; on a frame with particles, put the **emitter under the Voronoi layer** too (use object points) → shard count and shape now flow with the particles.
11. Render with particles hidden (fluid shards only), at one size (digital look), or at full radius.

## Gotchas
- Edge-to-spline extraction of the cuts (MeshTools edge spline with the shatter as child) saw all underlying polygon edges, not the N-gon shard outlines, at the time.

## Newest equivalent
2026.1 beta: **nxShatter** (GPU Voronoi/Glass/Wood/Bricks, can be driven by an emitter) and **nxFlowField** / **nxWarp Path** for the spline stream, with nxPush. Fused 2025.4.1 states **mtEdgeSpline handles n-gons**, which should fix the cut-extraction issue.
