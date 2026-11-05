# Water collapsing a snow sculpture (nxFluids SPH granular + liquid tag, age-mapped nxGravity, xpOpenVDBMesher)

- Source: INSYDIUM Training — Snow and Water — https://www.youtube.com/watch?v=Siw3tkJepaU (2025-05-14)
- Host / generation: C4D; G2 NeXus inside X-Particles (xpEmitters + GPU nxFluids SPH, nxGravity, NeXus Mapping) + **CPU xpOpenVDBMesher** and xpCache; Redshift; After Effects for motion blur
- Goal: a jet of water slides across the floor, smashes a granular (snow/sand) bust and it crumbles into chunks, both fluids interacting in one solver.

## Base
Floor = cube 6000 × 6000 cm; C4D content-browser bust scaled to ~160 cm tall (hidden after linking).
- Ctrl+D Project Settings ▸ **X-Particles ▸ Subframe steps 4** (full gravity on sub-cm particles plus very fast water).

## Steps
1. **Emitter granular**: Object mode, shape = bust; Emission **Shot** on frame 1, **Hexagonal** grid, speed 0, draft radius **1.2 cm** (~100k particles; check with Display ▸ HUD).
2. **nxGravity** (defaults). Floor gets an INSYDIUM **Collider tag**: bounce 0, **friction 90%** so grains grip.
3. **nxFluids**: **SPH**, Fluid type **Granular**, Substeps **6** (×4 scene subframes ≈ 24 per frame — enough because the sculpture does not need to stand by itself). Granular: Friction **90**, Stability **20** at draft (5 crumbles more at draft size).
4. Viewport check: emitter Display ▸ Color **Gradient Parameter** mapped to the granular value (~30), blue → white.
5. Fake the stand-up: nxGravity ▸ **Mapping** ▸ **Age → gravity strength**, min/max age a 2-frame window (28–30 first, later **21–23**) so gravity only switches on when the water hits. Disable the map while timing the water.
6. **Emitter liquid**: Box shape, thin (~17 cm tall), Direction **−X**, placed off-screen low near the floor and banked ~25° down so it splashes onto the floor first; Hexagonal emission, **same radius as the grains** (SPH needs identical radii or it explodes), speed **800**.
7. One solver for both: on the liquid emitter add an **nxFluids tag** ▸ SPH ▸ Fluid type **Liquid** (the nxFluids object stays Granular).
8. nxFluids ▸ **Check Density** on (default: a newborn particle above 110% of the fluid density is killed) — stops overlapping births blasting out.
9. Separate friction: duplicate the floor → *floor granular* (collider **Exclusions** = liquid emitter, friction 90%) and *floor liquid* (excludes granular emitter, friction **1%** so the water slides).
10. Separate gravity: the mapped one = *gravity granular*; duplicate as *gravity liquid* with the map deleted. Each emitter's **Modifiers** tab excludes (minus) the other's gravity.
11. Flow variation: **Vibrate tag** on the liquid emitter — Regular pulse, Rotation on, Heading ~5°, Frequency 1.
12. Liquid emission frames **0–50** only (untick Emit all frames); residual water keeps pushing the collapse.
13. Production: both radii **0.4 cm** (~3M grains, ~6M liquid by frame 50; 24 GB VRAM handled ~13–14M fluid particles). Raise granular Stability back to **20** for similar chunk size. Cache a 40-frame test (~13 min, 12 GB) to re-check gravity timing, then the full 120 F (~2 h 40 min). Viewport: Display **Dots**, Force display, Level of detail ~21%.
14. **xpOpenVDBMesher granular**: Voxel size **0.5**, Point Radius **1.9** (default 10× is bloated), Filters: delete Median, add **Curvature**, iterations **2** (SSS hides the rest).
15. **xpOpenVDBMesher liquid** (duplicate): Voxel **0.6**, Point Radius ~**2**, Curvature **10** iterations. If splashes vanish: smaller voxels or larger Point Radius.
16. Cache meshes: xpCache ▸ Build ▸ **Continue** (not Overwrite) reads cached particles and adds meshes (~1 h 20 min); then hide both emitters.
17. Redshift: snow = SSS **weight 1**, slight blue scatter color, **Scale 100**, Radius as a grey value to pull it back, raise roughness for packed snow (less ice). Water = IOR **1.33**, Transmission 1, roughness ~0.
18. Render 1080p, unified sampling threshold **0.02**, denoising off + random noise pattern, Bucket size **512** (~1 h). After Effects: adjustment layer **Pixel Motion Blur**, Shutter Samples **20**.

## Gotchas
- SPH mixing: all particles must share one radius and one nxFluids object.
- Stability depends on particle size — re-tune it after dropping the radius.
- Never Overwrite when adding meshes to an existing particle cache.

## Newest equivalent
**nxMPM** (2026.1 beta) solves snow/sand and liquid in one multi-material GPU sim (nxMaterial presets like Snow packed/sticky; Auto Sleep with Wake Speed can keep the sculpture still until struck); in Fused 2025.4 mesh with GPU **nxMesher** instead of xpOpenVDBMesher. FLIP & MPM respect collider group filters (Beta 3) for per-fluid floors.
