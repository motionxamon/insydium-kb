# Emit by height and slope — snow caps, settled dust (xpEmitter Object ▸ Topology)

- Source: Bite-Sized — Topology Emission — https://www.youtube.com/watch?v=uA6Eo2v_9hs (2025-10-30)
- Host / generation: C4D; plain **xpEmitter** (no modifiers), TerraformFX terrain + a C4D Torus as sources
- Goal: place particles only where a surface is high enough and/or flat enough (snow on peaks, dust on top of objects).

## Base
**xpEmitter** ▸ Object: emit from the TerraformFX island, **Polygon Area**. Emission: **Shot**, **Simulate** (particles on frame 0), speed 0, ~100,000 particles. Set the source's Basic ▸ Display Color to a custom black so the particles read clearly.

## Steps
1. Emitter ▸ Object ▸ **Topology** sub-tab ▸ enable **Height**: default range 0–200 cm. Lower Max until the top particles vanish to find the terrain's real height (~81 cm in the demo). [▶ 1:18](https://youtu.be/uA6Eo2v_9hs?t=78)
2. Snow caps: Max a bit above the peak (~90), then raise **Min Height** to the snowline. [▶ 2:15](https://youtu.be/uA6Eo2v_9hs?t=135)
3. Soft snowline: the **height spline** is the emission amount across the range — pull the low-end knot down so particles thin out towards Min instead of a hard cut. [▶ 2:31](https://youtu.be/uA6Eo2v_9hs?t=151)
4. Turn Height off, enable **Slope**: default 0–90°. Lower **Max Slope** to strip particles from the steepest faces (exposed cliffs). [▶ 3:45](https://youtu.be/uA6Eo2v_9hs?t=225)
5. Combine Height + Slope: only high, not-too-steep areas, thinning lower down. [▶ 3:58](https://youtu.be/uA6Eo2v_9hs?t=238)
6. Scene geometry (dust): emit from a Torus, Topology ▸ Slope only, Max 90°, then use the slope spline to thin particles on steeper parts where dust would have slid off. [▶ 3:45](https://youtu.be/uA6Eo2v_9hs?t=225)

## Gotchas
- Visible steps in the gradient = too few polygons (slope is per face). Raise the Torus **Pipe Segments** (or subdivide) for a smooth falloff.

## Newest equivalent
On GPU/NeXus 2026 the same masking can be built with nxFalloff modes such as **Curvature**, **AO** or **Attribute** on emission/modifier layers; the xpEmitter Topology tab stays the quickest CPU route.
