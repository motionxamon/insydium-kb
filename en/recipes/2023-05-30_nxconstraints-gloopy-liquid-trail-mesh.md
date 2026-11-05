# Gloopy liquid without a fluid solver (nxConstraints birth springs → xpTrail Constraints algorithm → xpOpenVDBMesher)

- Source: Top Tip Tuesday — NeXus Gloopy Liquid — https://www.youtube.com/watch?v=mWdb1K0R0FU (2023-05-30)
- Host / generation: C4D; G2 NeXus (nxConstraints, nxGravity on an orange xpEmitter) + CPU xpTrail, xpOpenVDBMesher, xpJoin + xpCollider
- Goal: stretchy, stringy liquid pouring over vibrating spheres, built from spring-connected particles.

## Base
Spheres with Vibrate tags inside an **xpJoin** carrying one **xpCollider** tag. xpEmitter **Circle**, plane **−Y**, **Ring Only**, **Cone Angle 90** (sprays outward first). **nxGravity 200 cm**.

## Steps
1. **nxConstraints**, Iterations **3**. Add a **Connection** constraint, click **B** = **Birth** connections (vs distance/custom). [▶ 1:35](https://youtu.be/mWdb1K0R0FU?t=95)
2. Defaults are up to 8 connections within 40 cm → set **3** connections, Radius **30** → particles clump. [▶ 1:50](https://youtu.be/mWdb1K0R0FU?t=110)
3. Emitter Display ▸ **Display Constraints** to see the yellow springs. [▶ 2:19](https://youtu.be/mWdb1K0R0FU?t=139)
4. Springs snap at Break **50% relative**: raise to **200**. Stiffness **80% → 23%** → long stretchy strands. [▶ 2:43](https://youtu.be/mWdb1K0R0FU?t=163)
5. Generators ▸ **xpTrail**, link the emitter, **Algorithm: Constraints**, type **Birth** → green trails along the springs; hide the emitter. [▶ 3:43](https://youtu.be/mWdb1K0R0FU?t=223)
6. Generators ▸ **xpOpenVDBMesher** meshing the **trail** (hide the trail). Too blobby → xpTrail ▸ Spline options ▸ **Intermediate Points Uniform 10** → smooth strands. [▶ 4:43](https://youtu.be/mWdb1K0R0FU?t=283)
7. Material on the mesher. Filters: remove Median, add **Gaussian** (width 1; 2 was too soft), then an **Offset** filter to thin it slightly. [▶ 5:25](https://youtu.be/mWdb1K0R0FU?t=325)

## Newest equivalent
Viscous liquid today: **nxFluids FLIP/APIC** with variable viscosity, or 2026.1 non-Newtonian (Flow Index, Yield Stress) + GPU **nxMesher**; or SPH + nxConstraints Viscosity (see "Three gloops with three viscosities", 2025-08-05). For string-like strands nxConstraints + **nxTrail** still apply; collisions via **nxCollider** in NeXus 2026.
