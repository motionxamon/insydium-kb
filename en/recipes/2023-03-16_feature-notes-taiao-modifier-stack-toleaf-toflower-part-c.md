# Feature notes: Taiao modifier stack, new toLeaf and rebuilt toFlower (sneak peek, hibiscus build)

- Source: INSYDIUM LIVE! — March 2023 - NeXus, TerraformFX & Taiao — https://www.youtube.com/watch?v=OVUcKWkhUFY (2023-03-16)
- Host / generation: C4D; Taiao (procedural plants) work-in-progress build
- Status: dev preview of the Taiao overhaul that shipped in **Fused 2023.3** (Jul 2023); toLeaf venation + presets listed again in Fused 2024.2.

## toPlant: modifier stack
- Shaping options (furling, gravity, turbulence…) moved out of the plant layer into a per-layer **Modifiers** stack; the layer itself only sets the base shape (angle, length; resolution in Global settings).
- Modifiers: **Furling, Turbulence, Twist, Gravity** + new **Aim, Profile, Displacement, Fold**. Each has **Variations**, a **Bias** along the branch and a **blend mode** (a second Furling set to **Add** stacks on the first — e.g. one at the base, one at the tips). Unlimited count.
- Each modifier takes C4D **Fields** (drag a field into the list for several modifiers): spherical field to art-direct which branches bend; animated Random field = wind-like animation.
- INSYDIUM list views can be resized vertically (back to R19).

## toLeaf (new object)
- Leaf geometry tab modes **Basic / Custom / Emitter**; Custom takes a toLeaf so plants use the procedural leaf. Shape curve; demo res 20 × 40.
- **Veins**: main vein profile (taper), **Petiole Offset** (stalk pushes the blade off the branch), Vein Count (~20), angle, radius; structures **Pinnate / Palmate / Parallel** (grass); veins adapt to the shape. Visible under translucency.
- Modifiers: **Fold** with a **Fold Shape** spline (soft curved fold instead of the old hard angle) + bias; Furling (gravity droop, tip curl); Turbulence.
- Main mode **Standard** or **Lobing** (compound leaves): Pinnate rows with end leaf, or **Palmate** fan; stem length/profile, angle/twist/size variations, **Size Bias** spline (center vs outer leaflets).

## toFlower (rebuilt, was inside toPlant)
- Preset layers: sepals (useful as a bud), receptacle, pistil, petals, stamen. Hibiscus: sepals off, 5 petals, receptacle/pistil width 1, pistil height 0.5.
- Petals: res 20 × 40, Orientation ~60%, Fold at the base (bias down) wraps them round the receptacle, Furling + Turbulence; Orientation **Twist** strength fixes intersections; Main ▸ Radius pulls them back to the pistil.
- **Stamen on stamen** (child layers via Add Parts): main stamen (Fit to Pistil off, profile knots for a bulb, Turbulence) → 5 tips with **Radial** distribution (count 5, ring count 5, Distribution spline, Angle, Furling) → pollen with **Spiral** (Fibonacci helix) distribution, angle + size bias splines, **Displacement** with a noise shader for gnarly detail.
- Displacement layer + any shader replaces Turbulence when you need per-axis control.
- Petal material tip: gradient in Color on 2D-**V** (base→tip) with a little turbulence.

## Newest equivalent
Fused 2024.2 added Taiao growth-point scatter and toLeaf venation + presets; whats-new lists nothing newer for Taiao.
