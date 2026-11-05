# Exploding planet: surface detail particles that ride the spinning sphere (displaced texture emission, Global Transform, color-driven offset)

- Source: NAB 2023 — INSYDIUM Training — NeXus Friction - Part 2 — https://www.youtube.com/watch?v=3Qd2e6ZCN6M (2023-04-17)
- Host / generation: C4D; CPU xpEmitter/xpSystem features (second system next to Part 1's NeXus system)
- Goal: a dense layer of static-looking detail particles on the planet surface that rotate with it, drift slightly outward and stand off by brightness, while Part 1's friction debris flies off.

## Base
Part 1 scene. Ctrl+Alt-click the system's enable tick to disable the whole motion system while working.

## Steps
1. Ctrl-drag a copy of the animated sphere → **sphere detail**; delete its copied Expresso tag and material tag; hide the original.
2. Geometry detail: type **Hexahedron**, Segments **1000**; child **Displacer** ▸ Shading ▸ **Noise (Stupl)**, large global scale, X stretched / Y squashed; Height **2.5 → 1.5 cm**.
3. Bake: **Current State to Object**, delete the live version. The bake loses the rotation keys → make it a **child of the original animated sphere**.
4. Ctrl-copy the Part 1 material, apply to sphere detail, set Projection **Spherical** again, change the noise Seed (similar but different pattern).
5. New **xpSystem** "system detail" ▸ Object: **Only Modifiers in Same System** (ignores Part 1's nxDrag/nxConstraints).
6. Its emitter: Shape **Object** = sphere detail, Source **Texture** (that tag): emit from Color, color from Color, **Radius from Color**.
7. Emission **Shot**, mode **Simulate** (not Simulate Legacy) → particles exist on frame 0; **50,000** particles, radius **2**, variation **0.5**, speed **1 cm**.
8. Not Stick to Source (it removes their speed). Instead make the whole system a **child of the animated sphere**, then system ▸ **Global Transform** tab: drag in the emitter → particles rotate with the sphere and still drift out.
9. Emitter ▸ Emitter sub-tab: **Offset from origin** ~**3 cm**, and in the Texture tab drive the offset by the **Color channel** → brighter particles sit further off the surface.
10. Black C4D Sky (display color custom) for checking; re-enable the motion system for the full effect.
11. Hide the texture seam: texture tag **Offset U** until the seam stays at the back for the whole shot.

## Gotchas
- Shot in Simulate Legacy mode does not show particles on frame 0.
- Without the emitter in Global Transform, the parented system moves but its particles don't.

## Newest equivalent
In NeXus 2026 an **nxEmitter** has **Stick to Source** and emission from meshes/point clouds; nxConvert brings xpEmitters over. The idea (separate system, surface detail + Part 1 debris) carries over unchanged.
