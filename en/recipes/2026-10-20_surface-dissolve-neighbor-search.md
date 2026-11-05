# Outside-in disintegration of a particle volume (nxQuestion Neighbors → Set Group, speed-mapped forces)

- Source: Top Tip Tuesday — Surface Dissolve — https://www.youtube.com/watch?v=yOPa8oM_KXE (2026-10-20)
- Host / generation: Blender (NeXus for Blender); nxEmitter groups, nxQuestion, nxGravity, nxTurbulence, nxColor, nxConstraints Forces, nxCollider
- Goal: a solid particle sphere that peels away layer by layer from its surface, the grains sliding off and settling on the floor.

## Base
- **nxEmitter** sphere radius 1.7, lifted up; Shot, random, **250,000** particles, speed 0, radius **0.01**. Born color black.
- Plane + **nxCollider** (some bounce, high friction, a little scatter); hide the plane.
- **nxGravity**, variation 1.

## Steps
1. Emitter ▸ Groups: **Create & Add** two groups, tick **Inherit from Emitter** on each. Group mode **First Group Only** → everything is born in group 1. [▶ 2:37](https://youtu.be/yOPa8oM_KXE?t=157)
2. Gravity ▸ Groups Affected = **group 2** only (nothing falls yet). [▶ 3:33](https://youtu.be/yOPa8oM_KXE?t=213)
3. **nxQuestion** ▸ question **Neighbors**: search distance **0.1** (0.05 = every particle counts as surface), **less than 30**, variation 7. Test first with a Set Color action (yellow) — only the outer shell should light up. [▶ 6:14](https://youtu.be/yOPa8oM_KXE?t=374)
4. Swap the action to **Set Group → group 2**. The check re-runs every frame, so the shell keeps eroding inward. [▶ 8:02](https://youtu.be/yOPa8oM_KXE?t=482)
5. Speed of dissolve = the neighbour threshold: 20 barely moves, 30 slow, 40 medium, 50 fast.
6. **nxColor** (group 2): gradient by parameter (Magma), mapped to Y direction. [▶ 8:44](https://youtu.be/yOPa8oM_KXE?t=524)
7. **nxTurbulence** (group 2): strength 30, larger scale. **Mapping** ▸ Speed layer → turbulence Strength, range 0–1 m/s, so grains at rest on the floor stop jittering. [▶ 10:07](https://youtu.be/yOPa8oM_KXE?t=607)
8. Fake inter-particle collision cheaply: **nxConstraints ▸ Forces** layer — Attraction 0, Repulsion 20%, Radius 0.05, Falloff Flat, max ~5 neighbours. Map Repulsion strength to **Speed** (range 0–0.5) so the static core isn't pushed apart. Falling grains now roll over the outside instead of dropping through. [▶ 13:17](https://youtu.be/yOPa8oM_KXE?t=797)

## Gotchas
- Surface particles always have fewer neighbours — the search distance must be several times the radius or everything reads as surface.
- Real P-P collisions would work but are heavier than the speed-mapped repulsion trick.
