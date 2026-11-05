# Swaying glass tendrils with particles on the tips (xpTendril + xpTrail Tendrils + xpSplineMesher + xpTrailTip tag)

- Source: Top Tip Tuesday — xpTrail Tip — https://www.youtube.com/watch?v=M4z3kOU4YEw (2023-12-19)
- Host / generation: C4D; **CPU G1 X-Particles** (xpEmitter, xpTendril, xpTurbulence, xpTrail, xpSplineMesher, xpColor)
- Goal: stylised underwater look — curly glassy tendrils growing from a terrain, each with a coloured sphere stuck to its end.

## Base
**xpEmitter** from a TerraformFX terrain, Polygon Area; **Shot 50**, No Intersection radius **15 cm**, speed **150 cm**, radius **3**.

## Steps
1. Modifiers ▸ Generate ▸ **xpTendril**: Full Scene Length **off**, Tendril Length **16 frames ±4**.
2. Motion ▸ **xpTurbulence** strength **18** (tendrils look fixed but are a constant stream of new particles).
3. Emitter ▸ Groups: Ctrl+Alt-click twice → groups 1 & 2, **First Group Only**. xpTendril ▸ **Tendril Group = group 2**.
4. Group 1 (sources) Editor Display **None**; group 2 radius very small (~0.7).
5. **xpTrail** with the emitter, **Algorithm: Tendrils** → one dynamic trail per tendril.
6. **xpSplineMesher** on the trail: Joints and Vertex Colors off, **1 subdivision**, Size **1.5**, taper with the **Scale Along Spline** graph to a point. Hide the trail, apply a glass material.
7. Trail ▸ Tags ▸ X-Particles ▸ **xpTrailTip** tag → new emitter "emitter tip". In that emitter's Modifiers list **exclude xpTendril**; display Spheres.
8. **xpColor**, mode **Immediate**, Shader **Gradient** (Spherical) with a preset, **Turbulence 20%**.
9. Camera with depth of field; background plane.

## Newest equivalent
Tendril/branch effects map to **nxDendrite** in NeXus 2026 (G3) and trails to **nxTrail**; the xpTrailTip/xpTendril combo itself is still a CPU-only trick in Fused.
