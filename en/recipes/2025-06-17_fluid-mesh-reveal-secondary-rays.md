# Reveal a hidden logo only through fluid refractions (Redshift primary-ray off + lava material blender)

- Source: Top Tip Tuesday — Fluid Render Reveal — https://www.youtube.com/watch?v=UGiIPXJbpMo (2025-06-17)
- Host / generation: cached xpOpenVDBMesher fluid + Redshift
- Goal: the X logo is invisible to camera but appears in the splashing water's reflections/refractions.

## Steps
1. Water: Standard, reflection 1, roughness ≈0, **IOR 1.33**, transmission 1. Studio HDRI rig light.
2. Rock: **Maxon Noise** Luka, octaves up, scale ~850, color 2 grey → base color, rough; bump: FBM noise scale ~200 → **Bump Map** node (height 2).
3. Lava: copy of the material with **Emission 10**.
4. **Material Blender**: base = rock, layer 1 = lava, Blend Color = another Maxon Noise with **low clip** for contrast and saturated color 2; noise animation speed 0.1.
5. Logo ▸ Redshift Object tag ▸ Visibility override ▸ **Primary Ray Visible off** (secondary stays) → seen only through the water.

## Newest equivalent
Mesh with **nxMesher** (Fused 2025.4) instead of xpOpenVDBMesher.
