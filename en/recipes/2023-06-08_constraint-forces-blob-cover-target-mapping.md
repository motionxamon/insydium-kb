# Fake gloopy fluid crawling over a logo (xpConstraints Forces, xpCover, radius/age/temperature Data Mapping, xpOpenVDBMesher)

- Source: Maintenance Training — Dynamics - Constraints - Forces Tutorial — https://www.youtube.com/watch?v=dnyn6Lrj8-A (2023-06-08)
- Host / generation: C4D; CPU X-Particles (xpConstraints, xpCover, xpTurbulence, xpScale, xpOpenVDBMesher)
- Goal: particles grow on a MoText, cluster with attraction/repulsion forces and slither toward a movable target, meshed as slime/honey.

## Base
MoText "XP" bold, height **400 cm**, depth **80 cm**, Fillet Caps front and back (3 steps). Move it **Z −40** so its centre sits at world origin.

## Steps
1. **xpEmitter ▸ Object**, Polygon Area, **Offset Origin 1 cm**; **Shot 500**, speed 0; **Radius 6 cm, variation 6** → 0–12 cm. Display Circles Filled. [▶ 2:39](https://youtu.be/dnyn6Lrj8-A?t=159)
2. **xpConstraints ▸ Forces** on. Default attraction radius 20 cm is tiny for a 400 cm logo → **Attraction Radius 400**, connection **Limit 16 → 50**. [▶ 3:42](https://youtu.be/dnyn6Lrj8-A?t=222)
3. **xpCollider tag** on the MoText: Bounce 0, Friction 25 (later lowered so particles slip over). [▶ 4:47](https://youtu.be/dnyn6Lrj8-A?t=287)
4. Raise repulsion radius/strength; also enable **Collisions** in the Constraints object to stop overlaps. [▶ 5:37](https://youtu.be/dnyn6Lrj8-A?t=337)
5. Map **Repulsion** to particle **Radius** (min 0, max 12 cm), curve inverted: smallest particles get full repulsion → small ones swarm round the outside of the blobs. [▶ 6:20](https://youtu.be/dnyn6Lrj8-A?t=380)
6. **xpCover** (Motion modifiers): Target = a Null (star display), Modifier Type Target, effect Attract, **Speed Mode: Gravity**, Gravity Strength **10**. Move the null to steer. Lower **Acuteness of Turn** for arcing, circling paths; high = straight at the target. [▶ 9:54](https://youtu.be/dnyn6Lrj8-A?t=594)
7. Cover ▸ Mapping: **Gravity Strength by Radius** 0–12, curve so only particles above ~6 cm are pulled; constraints drag the small ones along. Raise strength a little. [▶ 13:23](https://youtu.be/dnyn6Lrj8-A?t=803)
8. Optional **xpTurbulence** (small scale, high strength) for jitter inside the clump.
9. Grow-on: **xpScale** ▸ Set Value, **12 cm**; Mapping **Radius by Age** (0 → 90 frames, shorten the ramp). [▶ 15:55](https://youtu.be/dnyn6Lrj8-A?t=955)
10. Restore randomness: emitter ▸ Extended Data ▸ Physical ▸ **Temperature 50, variation 50** (just a number holder, 0–100) → second xpScale map **Radius by Temperature**. [▶ 17:35](https://youtu.be/dnyn6Lrj8-A?t=1055)
11. Mesh: **xpOpenVDBMesher** source = emitter; raise Voxel Size, lower Point Radius, add **Gaussian** smoothing filters. [▶ 20:26](https://youtu.be/dnyn6Lrj8-A?t=1226)

## Newest equivalent
**nxConstraints** Forces + **nxCover** with NeXus Mapping and **nxScale** (layered, Fused 2025.4), meshed with **nxMesher**. For real liquids use **nxFluids FLIP/APIC** with variable viscosity; for sticky/elastic solids, **nxMPM** (2026.1 beta).
