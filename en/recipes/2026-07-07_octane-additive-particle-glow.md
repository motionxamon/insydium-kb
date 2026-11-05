# Additive glowing particles in Octane (1 M vs 10 M particles)

- Source: Top Tip Tuesday — Octane Particle Glow — https://www.youtube.com/watch?v=AjAFehv2dRs (2026-07-07)
- Host / generation: C4D, cached nxExplosiaFX advection sim + Octane
- Goal: wispy, self-lit "additive" particle look.

## Steps
1. Emitters (cached advection sim, 1 M and 10 M versions) → **Octane Object tag** → Particle Rendering → enable **Geometry**, link a tiny instance sphere: **Hexahedron type, few segments, radius 0.05** (1 M) / **0.015** (10 M). [▶ 0:44](https://youtu.be/AjAFehv2dRs?t=44)
2. Black world: **Octane Texture Environment**, color black → no light in the scene. [▶ 1:39](https://youtu.be/AjAFehv2dRs?t=99)
3. **Universal Material** on the instance sphere: Specular 0; **Emission** = Texture Emission (Surface Brightness on) with a blue color texture; **Opacity** = mid-gray (0.5) → overlaps add up and get brighter. [▶ 4:30](https://youtu.be/AjAFehv2dRs?t=270)
4. Render settings: Direct Lighting is fine; Max Samples ~3000; **Adaptive Sampling** on (min 512, noise threshold 0.005). With DOF + denoise enable **Static Noise** to avoid flicker. [▶ 6:16](https://youtu.be/AjAFehv2dRs?t=376)
5. More particles + smaller instances = smoother wisps. 1 M looks grainy (not render noise — too few particles); 10 M at radius 0.015 is smooth. Denoising can fake it but never matches a higher count. (Demo: 720p, 70 frames ≈ 17 min.) [▶ 7:51](https://youtu.be/AjAFehv2dRs?t=471)

## Rule of thumb
Each ×10 particle count → shrink instance radius ~3×, otherwise hot spots blow out.
