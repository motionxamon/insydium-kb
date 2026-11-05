# Glowing alien lily from one petal (Taiao Flower layers + Cycles 4D facing-masked emission)

- Source: INSYDIUM LIVE! — November 2023 – X-Particles, NeXus, Taiao, MeshTools & Cycles 4 — https://www.youtube.com/watch?v=qaso-gPGBnI (2023-11-16)
- Host / generation: C4D; Taiao (Flower object); Cycles 4D render. Part A of 3 (Mike Batchelor's segment of the Black Friday ad breakdown)
- Goal: an "Avatar"-style single-petal lily with hand-painted textures whose edges and dots glow.

## Steps — model
1. Insydium ▸ Taiao ▸ **Flower**. Remove the **Sepal** layer (a lily is one petal from the stem); hide Stamen + Petal while shaping.
2. **Pistil** width/height ~2, **Receptacle** width 2 so they blend, then height ~3; pull the tangent handle into a teardrop; Subdivision 1 on both. Drop the stem material on each; if seams mismatch, switch the material projection UV **+V → −V**.
3. **Petal**: Count **1**. Geometry: Width 10, Height 25, Segments 10 × 20, Subdivision 1; small Thickness, tapered with the thickness **Depth** spline (thick at base). Profile: pull handles so the tip closes to a point. **Edge Noise 200%**.
4. Orientation angle 90 to work on it upright. Modifiers (each layer has its own stack): **Fold** (preset on petals) — strong fold, raise Shape so the edges overlap, **Offset Fold** for a seam, then open it with the **Bias** + bias tangent curve (add a point to curl the bottom seam).
5. **Furling** with bias to droop the petal, a second Furling to lift the tip (boat shape), **Turbulence** for breakup — offset its bias so the tip isn't distorted.
6. **Stamen**: Count 1, untick **Fit to Pistil** (else it follows pistil normals and leans), scale up, delete two shape handles for a cone, more segments, add Furling + Turbulence; stem material.
7. Fix petal orientation with the petal **Layer Rotation 90**, then angle / radius / position to sit it in the stem.
8. Put the flower into a Taiao plant's **Custom Object** slot to place it on the plant.

## Steps — Cycles 4D material (Object material = Principled)
9. Drag the painted textures in (diffuse painted in Procreate, normal made in Photoshop). Color → Base Color; Normal Map node in **Non-Color Data** → Normal.
10. **Mix Shader** (Principled + **Emission** using the color texture). Plain 50% mix looks muddy, so drive Factor with **Layer Weight ▸ Facing** → **Color Ramp** (clamped); emission strength ~3 → glowing edges.
11. Second Mix Shader with a white Emission masked by the painted **dot alpha**, strength 8 → glowing speckles.

## Gotchas
- Textures can be painted anywhere (Substance, Procreate…) because Taiao generates UVs.

## Newest equivalent
Still Taiao — later versions add toLeaf venation + presets (2024.2); see the 2025-10-23 water-lily and 2024-05-28 stamen recipes. In Redshift the same idea is a Fresnel/facing ramp blending an emissive layer.
