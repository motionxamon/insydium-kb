# xpDynamics — tool card

Mentioned in **5** recipes · 2023-04-19 → 2024-02-06 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- Disable MeshTools; on the sphere add **xpDynamics tag ▸ add Emitter** (one particle per vertex). [▶ 3:02](https://youtu.be/3YmhMKdK0o4?t=182) — *[2024-02-06](../../recipes/2024-02-06_meshtools-xpdynamics-soft-body.md)*
- Text spline ▸ **xpDynamics tag** → a particle per intermediate point. In the tag, **add an Emitter** ("emitter dynamic") — advection needs real emitter particles. [▶ 2:54](https://youtu.be/2YkjQgmo8Ic?t=174) — *[2024-01-23](../../recipes/2024-01-23_xpdynamics-spline-advection.md)*
- On the torus: Tags ▸ X-Particles ▸ **xpDynamics** — births dynamic particles on every vertex. [▶ 2:20](https://youtu.be/3cWjs6bgjBI?t=140) — *[2023-11-07](../../recipes/2023-11-07_xpdynamics-floating-object-nxfluids-tag.md)*
- xpDynamics ▸ Properties ▸ **Add Emitter** → rename "emitter dynamic", Display ▸ Draw Emitter off, hide its particles; Ctrl-drag a copy of the nxFluids tag onto it. [▶ 4:41](https://youtu.be/3cWjs6bgjBI?t=281) — *[2023-11-07](../../recipes/2023-11-07_xpdynamics-floating-object-nxfluids-tag.md)*
- xpShatter ▸ Tags ▸ **xpDynamics** → particle dynamics on every vertex. Enable **Push**, Strength **max** → shards push each other apart. Accuracy: Distribution **Vertices + polygon midpoints**, Surface or Volume (slower). Chosen over Bullet so X-Particles modifiers and spawning work on the same particles; it runs near real-time. [▶ 28:39](https://youtu.be/U8zISIlBq90?t=1719) — *[2023-04-19](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)*

## All recipes (5)
- 2024-02-06 · [Organic wobbling spiky ball (mtSubdivider + mtInset on an xpDynamics soft body)](../../recipes/2024-02-06_meshtools-xpdynamics-soft-body.md)
- 2024-01-23 · [Text spline blown by an explosion (xpDynamics on a spline + xpExplosiaFX advection)](../../recipes/2024-01-23_xpdynamics-spline-advection.md)
- 2023-11-16 · [Asteroids orbiting planets + spreading glow (nxAttract Force/Speed Limit, xpColor with particle fields, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-11-07 · [Floating / sinking object in a NeXus fluid (xpDynamics tag + per-emitter nxFluids tag density)](../../recipes/2023-11-07_xpdynamics-floating-object-nxfluids-tag.md)
- 2023-04-19 · [Logo shatters on time, re-shatters on impact, spawns debris and dust (xpShatter layers + xpDynamics Push + collider Spawn + xpMultiSpawn)](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)
