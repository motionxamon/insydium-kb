# Volcanic crater terrain + low-poly collider (TerraformFX noise/gradient/erosion/curve, snow vertex map, mtRemesh)

- Source: INSYDIUM LIVE! — March 2023 - NeXus, TerraformFX & Taiao — https://www.youtube.com/watch?v=OVUcKWkhUFY (2023-03-16)
- Host / generation: C4D; TerraformFX (tfTerrain operators) + MeshTools mtRemesh; prepares the ground for the NeXus grains in part-b
- Goal: a volcano with a flat crater floor for a logo-reveal sand sim, plus a light collider and a vertex map for static scatter.

## Base
- Logo (extruded spline) keyframed up through the ground with a small **kick-back** at the end so grains get knocked off.
- Viewport: tfTerrain display gradient off, custom dark gray color; a C4D light with **soft shadows**, density ~80% to read the relief.

## Steps
1. **tfTerrain**: delete the default erosion operators, keep the noise; Noise type **Stupl** (swirly, round shapes) instead of Turbulence. [▶ 11:25](https://youtu.be/OVUcKWkhUFY?t=685)
2. Add **tfGradient** (radial): raise it to a peak, then shape the **falloff curve** (Ctrl-click to add a knot) into a rim with a central dip = crater. [▶ 12:08](https://youtu.be/OVUcKWkhUFY?t=728)
3. Add **Erosion filter ▸ Hydraulic**, the fast **2D** solver (an X-Particles full-3D one also exists). Default 10,000 particles living 30 F; Filter: rain **Above ~50 cm** so only the high parts erode. [▶ 13:32](https://youtu.be/OVUcKWkhUFY?t=812)
4. Ctrl-drag to duplicate the erosion; the second pass (**30,000** particles) runs down the first one's channels and leaves flat silt deposits. [▶ 15:05](https://youtu.be/OVUcKWkhUFY?t=905)
5. Flatten the crater: **tfCurve** — linear spline, drag both ends to the bottom then lift together (constant height); **Masking ▸ Cylinder field** sized to the crater; lower the operator **Blend** to bring back some original detail. [▶ 17:00](https://youtu.be/OVUcKWkhUFY?t=1020)
6. Another **Erosion filter ▸ Snow**: snow settles in the grooves (lower radius = less); enable **output erosion map** → a vertex map on the terrain for the static particles. [▶ 19:40](https://youtu.be/OVUcKWkhUFY?t=1180)
7. **Current State to Object**, Ctrl-drag the vertex map tag onto it, disable the tfTerrain. Duplicate: one copy for beauty, one for collision. [▶ 20:03](https://youtu.be/OVUcKWkhUFY?t=1203)
8. **mtRemesh** on the collision copy: Features Angle **180** (just triangulate, keep edges), even Delaunay triangles; Edge Length **16** still holds the shape. **C** to make editable. [▶ 21:27](https://youtu.be/OVUcKWkhUFY?t=1287)
9. Polygon mode, brush select the crater, **U ▸ I** (invert), delete → tiny collider covering only the crater. Lower the logo collider so it starts hidden. [▶ 22:36](https://youtu.be/OVUcKWkhUFY?t=1356)

## Newest equivalent
TerraformFX gained an Advanced Terrain Shader, curvature channel and tfDistribute in Fused 2024.2 (tfDistribute is an alternative to the snow-vertex-map scatter). For the collider the 2026.1 beta's **nxCollider** object replaces the xpCollider tag.
