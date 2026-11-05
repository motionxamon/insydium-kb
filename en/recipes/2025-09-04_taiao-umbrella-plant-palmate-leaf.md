# Procedural umbrella plant (Taiao Leaf palmate lobed fan + Taiao Plant leaf-on-end, Redshift translucency)

- Source: INSYDIUM Official Training — Taiao Umbrella Plant — https://www.youtube.com/watch?v=ZyRwxTk3u80 (2025-09-04)
- Host / generation: C4D; Taiao Leaf (toLeaf) + Taiao Plant (toPlant); Redshift; no particles
- Goal: indoor umbrella plant — thin kinked stems, each ending in a drooping fan of 8 leaflets, in a pot.

## Leaf (Taiao Leaf)
1. Main: **12 length / 4 width** segments; shape the half-leaf **profile spline** (add a mid point, fuller toward the tip, pointed base).
2. **Thickness 5**; thickness spline thicker in the middle, tapering to both ends; **1 subdivision**.
3. Veins ▸ **Midvein**: taper its profile; raise **Petiole offset** for a stalk.
4. Modifiers: **Fold** (curve high, lower at the tip), **Furl** (gravity droop), Main ▸ petiole **Furl** for a smooth stalk curve, **Turbulence** — set its **bias** so tip and base don't break.
5. Main ▸ Leaf type **Lobed**; Lobing ▸ structure **Pinnate → Palmate** (fan). Short stem length, **leaf count 8**.
6. Orientation: **Angle** to spread the fan all round; **Twist** to tilt leaflets up, variation on twist and angle.
7. Distribution: size variation; **size bias** curve — small leaflets at the ends, bigger in the middle.
8. Materials: leaf texture on the leaf; ramp material on stem + midvein (Redshift ramps show white in the viewport — render only).

## Plant (Taiao Plant)
9. Trunk: height **80 cm**, radius **1**; Global ▸ segment resolution **1** (more segments for branching). Modifiers **Furl** (bend top, low bias) + weak **Turbulence** (bias off the base); taper with the profile spline.
10. Add Part ▸ **Branch**: **Branch on End off**, raise branch angle, distribution curve lowered; branch length curve shorter toward the top; length + angle variation; **Furl** with low bias, then re-raise branch angle to compensate.
11. On the branch Add Part ▸ **Leaf**: **count 0** with **Leaf on End** on → only the tip leaf. Geometry mode **Custom**, drop the leaf in; size up + variation; Orientation **Y rotation** down so the fan hangs. Increase branch count to taste.
12. Parent the leaf under the plant for tidiness.

## Render (Redshift)
- Dome light with HDRI + sun & sky rig through a window for shadows.
- Leaves: create the material type with **Translucency/backlighting** (not the standard one); texture → color correct (contrast) → brighter color correct into translucency.
- Pot: Maxon Noise + many-knot ramp as bump.
