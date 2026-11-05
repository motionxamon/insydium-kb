# xpConstraints — tool card

Mentioned in **6** recipes · 2023-02-21 → 2024-01-30 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **xpConstraints ▸ Viscosity** tab on (a connection type) — particles bind together (check with Display Constraints). [▶ 1:14](https://youtu.be/rhFYjdNe2XA?t=74) — *[2023-06-12](../../recipes/2023-06-12_viscous-pour-xpconstraints-fluidpbd.md)*
- **xpConstraints ▸ Connections ▸ Birth Connections** on with defaults → instant netting look. [▶ 4:14](https://youtu.be/WeuXOmENNXA?t=254) — *[2023-06-12](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)*
- Fix: **xpConstraints ▸ Connections ▸ Distance** (birth connections fail for constantly new particles). Defaults: radius **40 cm**, up to **8** connections. Turn on Display Constraints to check. [▶ 5:42](https://youtu.be/KBktASa5O2o?t=342) — *[2023-06-12](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)*
- **xpConstraints ▸ Forces** on. Default attraction radius 20 cm is tiny for a 400 cm logo → **Attraction Radius 400**, connection **Limit 16 → 50**. [▶ 3:42](https://youtu.be/dnyn6Lrj8-A?t=222) — *[2023-06-08](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)*
- Quickest: Dynamics ▸ **xpConstraints** ▸ **Collisions** tab on. One setting — **Stiffness**. Fast, basic. [▶ 0:47](https://youtu.be/GGI1MyewI2g?t=47) — *[2023-02-21](../../recipes/2023-02-21_particle-collisions-constraints-ppcollisions-bullet.md)*

## All recipes (6)
- 2024-01-30 · [Bullet-dented metal sign (xpClothFX plasticity + damping)](../../recipes/2024-01-30_xpcloth-plastic-dents.md)
- 2023-06-12 · [Fast viscous chocolate/honey pour (xpFluidPBD + xpConstraints Viscosity, Hexagonal emission)](../../recipes/2023-06-12_viscous-pour-xpconstraints-fluidpbd.md)
- 2023-06-12 · [Tearing constraint net peeled off a logo (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-12 · [Wiggly tendrils held together by constraints (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-06-08 · [Fake gloopy fluid crawling over a logo (xpConstraints Forces, xpCover, radius/age/temperature Data Mapping, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-02-21 · [Three ways to make particles collide with each other (xpConstraints Collisions, xpPPCollisions, xpBullet)](../../recipes/2023-02-21_particle-collisions-constraints-ppcollisions-bullet.md)
