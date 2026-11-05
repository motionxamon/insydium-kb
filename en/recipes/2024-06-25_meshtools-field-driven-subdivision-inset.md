# Animated field-driven subdivided extrusions (mtSubdivider + mtInset with layered Fields)

- Source: Top Tip Tuesday — Dynamic Subdivisions — https://www.youtube.com/watch?v=5g0K2rUBWlk (2024-06-25)
- Host / generation: C4D; MeshTools only (mtSubdivider, mtInset) + C4D Fields
- Goal: a plane breaks into noise-driven tiles that extrude in a moving, stepped wave.

## Steps
1. Plane with **1×1** segments → child of **mtSubdivider**, **levels 7**.
2. Subdivider **Shader ▸ Noise**: **low clip 35** and crushed for contrast; lower the **Tolerance**; cycle seeds.
3. **mtInset** with the subdivider as child: **Amount 33**, **Offset 100** → every face gets an inner face pushed out.
4. Inset Fields: **Linear** field, length 180, Remapping contour curve with ease. Set Inset **Sampling** from Per Point to **Centered** → inner faces stay flat (stepped).
5. **Random** field in **Overlay** to break the linear transition.
6. Animate: **Vibrate** tag on the linear field, rotation on (large heading amplitude, ~100 on others).
7. **Delay** field, **Spring** mode, 30% → lagging settle.
8. **Spherical** field in **Multiply** with an eased curve to restrict the effect to the center. Remove fields from the viewport filter to hide them.
9. Subdivider modes: **Bilinear** (default), **Bilinear Offset** (random rectangular tiling), **Shards**, **Whirl** (inner + outer polys; Strength gives thin/thick strips) — all animatable.
