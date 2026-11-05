# Water, rubber gummies and sand in one solve, meshed and rendered (nxMPM Materials + nxMesher + point cloud, Cycles)

- Source: NeXus Official Training — nxMPM — https://www.youtube.com/watch?v=jItRyLgdjPg (2026-10-07)
- Host / generation: Blender (NeXus for Blender 2026.1 beta, m, Z-up); nxMaterial preset, nxEmitter, nxMPM, nxGravity, nxCache, nxMesher; Cycles GPU
- Goal: a water stream splashes, two rubber Suzannes bounce in it, then a sand Suzanne drops in and displaces the liquid.

## Quick start
NeXus Hierarchy ▸ Presets ▸ **nxMaterial** = gravity + folder (emitter, MPM, mesher off) ready to play. Default material **Snow**; switch to Liquid ▸ Water for a splash.

## Steps (from scratch)
1. **nxEmitter** (Box) + Dynamics ▸ **nxMPM** + Modifiers ▸ **nxGravity**. Emitter ▸ **Match Solver Resolution** → MPM (auto radius + grid packing). Emission **Shot** for one blob. [▶ 2:35](https://youtu.be/jItRyLgdjPg?t=155)
2. MPM Display ▸ Draw Grid (Back). Resolution **120** for final, **80** for drafting. Domain Z = 2 m to sit on the floor; make it thinner. [▶ 3:20](https://youtu.be/jItRyLgdjPg?t=200)
3. **Use Bounds** off → sparse solve, but then add a cube + **nxCollider** (friction) as the floor. Demo keeps the domain. [▶ 4:57](https://youtu.be/jItRyLgdjPg?t=297)
4. "water" emitter: Sphere r 0.2, Rate, emit frames 1–30 only. [▶ 6:25](https://youtu.be/jItRyLgdjPg?t=385)
5. Suzanne → **Copy** the emitter ("gummy01"): Shape Object = Suzanne01, Shot, speed 0. [▶ 7:39](https://youtu.be/jItRyLgdjPg?t=459)
6. MPM global material = **Elastic ▸ Rubber** (default for any unlisted emitter). **Materials** tab: add "water" → **Liquid ▸ Water**. [▶ 9:52](https://youtu.be/jItRyLgdjPg?t=592)
7. MPM Display ▸ Particle Color = **Material** (liquid blue, elastic pink) to check. [▶ 10:24](https://youtu.be/jItRyLgdjPg?t=624)
8. Duplicate Suzanne + emitter → "gummy02", shot at F15. [▶ 12:46](https://youtu.be/jItRyLgdjPg?t=766)
9. Big Suzanne + emitter "sand", shot at F75; Materials tab → **Sand ▸ Dry**. [▶ 13:28](https://youtu.be/jItRyLgdjPg?t=808)
10. **nxCache** at res 120 (~2 min in the demo).
11. One **nxMesher** per emitter. Water: emitter layer, Surface **Zhu-Bridson**, Polygon mode **Quads**, smaller Polygon Size, Radius 0.025. [▶ 16:52](https://youtu.be/jItRyLgdjPg?t=1012)
12. Gummies: Spheres mode, Polygon Size 0.02, Radius 0.03, **Smoothing** layer Main Curvature 100%, Iterations 5 (10–15 too soft). [▶ 19:02](https://youtu.be/jItRyLgdjPg?t=1142)
13. Sand: emitter ▸ **Export ▸ Create Point Cloud**; auto material reads particle color via Attribute node — or use Point Info Random → Color Ramp → Base Color for cheap grain variation. [▶ 25:07](https://youtu.be/jItRyLgdjPg?t=1507)
14. Render: big plane (80×80), World **Sky Texture** strength ~0.05. Water: Transmission 1, Roughness 0, IOR 1.33. Gummies: Subsurface Christensen-Burley weight 1, radius 0.5, small scale, a little transmission; copy the material for a second color. [▶ 27:06](https://youtu.be/jItRyLgdjPg?t=1626)
15. Motion blur on the changing-topology meshes: nxMesher ▸ Export ▸ **Transfer Velocity**. [▶ 28:43](https://youtu.be/jItRyLgdjPg?t=1723)

## Gotchas
- Emitter frame range still applies to Shot: a shot at F75 with Emit range 1–30 emits nothing — re-enable Emit All Frames.
- Match Solver Resolution means more MPM resolution = more, smaller particles automatically.

## Newest equivalent
Already the newest route. Before MPM: nxFluids FLIP/SPH for water, SPH granular for sand, CPU xpClothFX/soft bodies for rubber — three separate solves with no two-way mixing.
