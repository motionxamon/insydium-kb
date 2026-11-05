# Crystals sprouting along frozen particle paths (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)

- Source: Black Friday Breakdown — Crystal Spawn — https://www.youtube.com/watch?v=yqfkRKgW1Mo (2023-11-16)
- Host / generation: C4D; mixed G1 CPU (xpFollowSurface, xpAttractor, xpAvoid, xpTrail, xpSplineMesher, xpJoin, xpCache) + G2 NeXus (nxQuestion, nxScale); TerraformFX terrain; Cycles 4D render
- Goal: control particles crawl over a terrain, stop when they hit each other's trails, and leave a path of growing glassy crystals lit by a hidden glowing trail mesh.

## Base — three copies of one TerraformFX terrain (delete TF grid + hydraulic erosion, gradient display and lights off)
- **render**: Segments 1500 × 1500; noise switched to a Wavy Turbulence type (pick a seed).
- **Sim High**: same noise, Segments 100 × 100 (fast for particle calcs).
- **Sim Low**: duplicate of Sim High with noise **Gain halved (25 cm)**, then moved down so it intersects the high one — the crystals sit on the high one, the trails on the low one, which later gives the lighting contrast.

## Steps — control sim
1. xpSystem; square emitter at the terrain side, wide and flat. Emission **Shot, 30** particles; **No Intersection radius ~16 cm**; Speed 150, Variation 60. Display Arrows filled; Extended Data ▸ Rotation **Tangential**. [▶ 5:08](https://youtu.be/yqfkRKgW1Mo?t=308)
2. Generator terrains must be wrapped in an **xpJoin** to be used as surfaces (one join per sim terrain). [▶ 7:06](https://youtu.be/yqfkRKgW1Mo?t=426)
3. **xpFollowSurface** → join of Sim Low, **Pull 99%**, raise Distance (default 10 cm misses the high particles). [▶ 7:58](https://youtu.be/yqfkRKgW1Mo?t=478)
4. **xpAttractor** on the far side (Acceleration ~50, lower strength) to drag the flow across; hide its icon. [▶ 35:41](https://youtu.be/yqfkRKgW1Mo?t=2141)
5. **xpTrail** on the emitter. **xpAvoid** ▸ object = the trail, On Detection **Freeze** → particles stop instead of crossing paths. Rename emitter "control". [▶ 10:48](https://youtu.be/yqfkRKgW1Mo?t=648)
## Steps — crystals
6. **nxQuestion** with no question, just an action set to **Spawn**; **Add Emitter** creates "crystals"; 5 per frame. [▶ 13:25](https://youtu.be/yqfkRKgW1Mo?t=805)
7. Crystal emitter ▸ Modifiers: exclude the follow surface, attractor and avoid. nxQuestion settings: don't inherit parent values, speed 0, Spread **17 cm** (lateral spread = crystal path width). [▶ 13:56](https://youtu.be/yqfkRKgW1Mo?t=836)
8. Duplicate xpFollowSurface → Sim High join, **Pull 100%** (no off-surface frames at birth); exclude it from the control emitter. [▶ 21:55](https://youtu.be/yqfkRKgW1Mo?t=1315)
9. Stop spawning when frozen: add a question **Flags ▸ Frozen** → action **Break** (ends the question cycle). [▶ 18:02](https://youtu.be/yqfkRKgW1Mo?t=1082)
10. **nxScale**: set Radius value 4.5; Mapping ▸ **Age** layer (0–30 F) on Radius; curve shoots up fast, overshoots and settles back = springy pop. [▶ 19:40](https://youtu.be/yqfkRKgW1Mo?t=1180)
11. **xpSplineMesher** on the trail, vertex colors + joints off, size 1.5. **xpCache** (external files, 90 F); then disable the control emitter and trail. [▶ 23:17](https://youtu.be/yqfkRKgW1Mo?t=1397)
## Steps — Cycles 4D look
12. Turn the two sim terrains off for render (Ctrl+Alt the traffic lights). Point light. [▶ 25:40](https://youtu.be/yqfkRKgW1Mo?t=1540)
13. Crystal emitter ▸ Cycles **Instance tag** ▸ object = Cylinder (6 rotation segments, r 2, h 20, cap fillet ~0.2) hidden under the ground. Size Multiplier 20 + large size variation; Heading offset 360 + 100% variation, Pitch/Bank 9°. All adjustable on cached particles. [▶ 26:24](https://youtu.be/yqfkRKgW1Mo?t=1584)
14. Material: Surface Extended ▸ **Glass Dispersion** group; small Roughness, IOR 2.2. Fireflies → Render Settings ▸ Integrator **Clamp Direct / Indirect 3**. [▶ 33:34](https://youtu.be/yqfkRKgW1Mo?t=2014)
15. Lights: warm burnt-orange point light kept low so it only glints in the crystals; duplicate on the other side, lower/subtler (solo each light to judge it). Cycles camera + preview lock lets you move the editor view freely. [▶ 35:47](https://youtu.be/yqfkRKgW1Mo?t=2147)
16. Spline mesher gets an **Emission** material + Cycles **Object tag** with camera visibility off — it lights floor and crystals unseen. Thinner mesh = sharper light: delete its cache tag, re-enable the trail, size 0.5. Dark blue, desaturated, strength ~7. [▶ 37:38](https://youtu.be/yqfkRKgW1Mo?t=2258)
17. Camera tag: small aperture radius, Focus Distance picked on a hero crystal. [▶ 41:31](https://youtu.be/yqfkRKgW1Mo?t=2491)

## Gotchas
- Generator objects (TF terrain) need xpJoin before xpFollowSurface accepts them.
- Clamp values are what remove the bright-glass fireflies; light count stays at two.

## Newest equivalent
nxFollowGeo + nxAttract + nxAvoid on the GPU; **nxSpawn** (2026.1 Beta 3, Rate per frame, own sub-layers) instead of an nxQuestion Spawn action; nxScale with Mapping; nxTrail and nxCache in NeXus 2026. Render with Redshift/C4D instancing via nxGenerator instead of Cycles 4D.
