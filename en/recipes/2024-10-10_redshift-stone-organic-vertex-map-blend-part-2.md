# Lighting and mixing stone + waxy organic materials by an animated vertex map (Redshift Material Blender, Vertex Attribute, volumetric gobo spot)

- Source: INSYDIUM Training — Organic Growth - Part 2 — https://www.youtube.com/watch?v=NS32rZns-Eo (2024-10-10)
- Host / generation: C4D + **Redshift**; input = the animated Alembic bust with growth vertex map from Part 1 (no particle tools in this part)
- Goal: stone statue overgrown by subsurface-looking organic matter, with dramatic three-point lighting and volumetric light shafts.

## Base
Animated Alembic of the bust carrying an **animated vertex map** (0 = stone, 1 = growth). Switch its smoothing deformer off while working, on again for final.

## Steps — lighting
1. **RS Area Light** + **Target tag** pointing at the bust → key light.
2. Ctrl-drag copies: **Rim** on the opposite side (Shape enlarged in Y, moved back/up); **Fill** at Intensity **20 → 10** for contrast. Check lights one at a time.

## Steps — stone material
3. RS **Standard** material. **Maxon Noise** node: type Luka, **Octaves 15** (needed for a detailed bump), Overall Scale **1200**, pick a seed.
4. Noise → **Bump Map** node (color → vector) → Standard Bump input; Height Scale **5**. Raise reflection roughness (no wet look).
5. Same noise → **Scalar Ramp** (linear; lift the black point, lower the white point) → Base Color for subtle milky variation.

## Steps — organic material
6. Ctrl-drag a second Standard node: **Transmission weight 1**, rough reflections, a transmission color.
7. **Scatter color** does nothing until **Scatter Depth** > 0: 1 = opaque, 80 = waxy/translucent; used **10**. Reflection roughness sets wet vs dry.

## Steps — blend
8. **Vertex Attribute** node, attribute = the animated vertex map → **Material Blender**: Stone = Base, organic = Layer 1 color, vertex attribute → **Layer 1 Blend Color** (black = stone, white = growth). It animates with the growth.

## Steps — volumetrics
9. Copy the key, set type **Spot**, place above and slightly behind. Add an **RS Environment** (not RS Sky) → Spot Intensity **10,000**, Exposure **2**, wider Cone Angle.
10. Spot ▸ Color ▸ Texture: a **gobo** from the Content Browser (tree leaves; any B/W image or noise works). Details: soften shadows, enable **softness affects gobo**, Softness **50**.
11. Select key/rim/fill ▸ Details: turn off **volume contribution** so only the spot lights the fog.

## Newest equivalent
If the growth mask is particle-driven, NeXus 2026.1 **nxFalloffMap** (C4D) bakes falloffs into vertex map / vertex color tags for the Vertex Attribute node; growth itself can come from **nxBioLogic** / nxDendrite.
