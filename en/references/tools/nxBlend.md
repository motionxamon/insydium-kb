# nxBlend — tool card

Mentioned in **13** recipes · 2023-04-19 → 2026-09-08 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **nxBlend** ▸ Color, mode **Addition**, Distance **0.04 → 0.07**, Strength **500%** (can exceed 100) → white creeps through wet sand; set a max/stop frame (148, then **110**) to keep solid black lumps. [▶ 11:30](https://youtu.be/yp5579on6J8?t=690) — *[2026-09-08](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)*
- **nxBlend** Color, **Blend: Addition**, strength full, distance ~6 cm → white spreads into neighbours (cooling), never darkens. [▶ 5:49](https://youtu.be/VCGNxYZt21k?t=349) — *[2026-02-03](../../recipes/2026-02-03_chocolate-setting-variable-viscosity.md)*
- **nxBlend**: Color only (default), **Strength 1000%** (max), Distance **3 cm** (10 cm = muddy; 2 cm = blending only at seams). [▶ 4:27](https://youtu.be/ldpeVYB30QA?t=267) — *[2025-09-23](../../recipes/2025-09-23_paint-mix-nxblend.md)*
- **nxBlend** Color, **Addition**, Distance 15, **Strength 1000%** → white (hot) particles brighten black ones on contact = re-melting. [▶ 6:59](https://youtu.be/_k0LatnQQJw?t=419) — *[2025-09-09](../../recipes/2025-09-09_hot-cold-variable-viscosity.md)*
- **nxBlend**: mode Addition, Color only, radius 5, **Strength ~1000** → white creeps through the dark patches until everything is white. [▶ 11:56](https://youtu.be/V4mwAf8tcLk?t=716) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- **nxBlend**: blends Color by default (also scale, rotation, mass, radius). Default strength 10% is too weak → **200%**; distance 10 cm; max blend duration 300 F. [▶ 4:08](https://youtu.be/IG5GdX9U4lM?t=248) — *[2024-03-05](../../recipes/2024-03-05_nxblend-paint-mix.md)*
- Set infectors to white. **nxBlend**: mode **Addition** (only brighter values pass on), Distance 5, Strength 100, Color → smooth gradient spread. [▶ 50:51](https://youtu.be/qaso-gPGBnI?t=3051) — *[2023-11-16](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)*
- **nxBlend** (below gravity): Color, Distance **20 cm**, Strength **1000** (full), duration **40** frames (default 300) → blue/white mix = heat exchange. Heavy neighbour search, fast on GPU. [▶ 1:18:53](https://youtu.be/6WjDq_87uck?t=4733) — *[2023-07-05](../../recipes/2023-07-05_variable-viscosity-wolf-nxspeed-clamp-part-b.md)*
- Heat spreading: **nxBlend**, mode **Additive**, Distance **50**, Strength max, blend time **60 → 90** frames. [▶ 58:45](https://youtu.be/U8zISIlBq90?t=3525) — *[2023-04-19](../../recipes/2023-04-19_nexus-heat-cool-melt-rig-nxquestion-mapping-part-c.md)*

## All recipes (13)
- 2026-09-08 · [Water jet eroding clumpy sand (nxFluids SPH Granular + Mixer liquid, nxBlend color → mapped granular settings)](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)
- 2026-04-14 · [Looping color waves triggered by contact (nxQuestion variable switch + nxBlend)](../../recipes/2026-04-14_nxquestion-looping-switch-color-waves.md)
- 2026-02-03 · [Molten chocolate that sets on contact (APIC variable viscosity by color)](../../recipes/2026-02-03_chocolate-setting-variable-viscosity.md)
- 2025-11-26 · [Feature notes: Fused 2025 liquids — GPU FLIP/APIC with viscosity, nxMesher, nxSplash (Final Tech Preview)](../../recipes/2025-11-26_fused-2025-flip-viscosity-nxmesher-nxsplash-feature-notes.md)
- 2025-09-30 · [Mesh a color-blending paint sim and render vertex color (xpOpenVDBMesher → Redshift)](../../recipes/2025-09-30_paint-mix-meshing-vertex-color.md)
- 2025-09-23 · [Mixing paint from three colored emitters (nxBlend + speed mapping)](../../recipes/2025-09-23_paint-mix-nxblend.md)
- 2025-09-09 · [Hot runny / cold gloopy fluid that re-melts on contact (groups + nxBlend + mapped viscosity)](../../recipes/2025-09-09_hot-cold-variable-viscosity.md)
- 2025-04-30 · [Procedural sand-bust disintegration (nxFluids SPH Granular + nxColor/nxQuestion groups + nxWind Von Karman + distance-mapped grains)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2024-03-05 · [Mixing gloopy paint colors (nxFluids SPH + nxConstraints Viscosity + nxBlend)](../../recipes/2024-03-05_nxblend-paint-mix.md)
- 2023-11-16 · [Asteroids orbiting planets + spreading glow (nxAttract Force/Speed Limit, xpColor with particle fields, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-07-05 · [Hot/cold variable-viscosity pour over a head (nxFluids SPH + nxConstraints Viscosity + nxQuestion object distance + nxBlend + colour-mapped nxSpeed clamp)](../../recipes/2023-07-05_variable-viscosity-wolf-nxspeed-clamp-part-b.md)
- 2023-06-26 · [Feature notes: new NeXus modifiers — nxUpres, nxInfectio, nxWave, nxAvoid, nxFlock, nxBlend modes, nxFoam on caches, nxWind Von Karman (Fused 2023.3)](../../recipes/2023-06-26_feature-notes-nexus-modifiers-2023-3.md)
- 2023-04-19 · [Interactive melt / re-harden rig driven by particle color (nxSpeed Clamp Max Speed mapping + nxQuestion fields + nxBlend + mapped SPH viscosity)](../../recipes/2023-04-19_nexus-heat-cool-melt-rig-nxquestion-mapping-part-c.md)
