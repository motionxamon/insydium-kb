# Melting blob from the outside in (nxDrag hold + nxQuestion Neighbors → group switch + nxConstraints Viscosity)

- Source: Top Tip Tuesday — nxFluids Melt Rig — https://www.youtube.com/watch?v=Tz60lfoe-hw (2024-01-02)
- Host / generation: C4D; G2 NeXus inside X-Particles (xpEmitter + nxFluids, nxDrag, nxQuestion, nxConstraints, nxGravity)
- Goal: a sphere of fluid that stays put, then its surface particles melt, drip and gloop onto the floor automatically.

## Base
Floor plane with collider tag; **xpEmitter** shooting a sphere in **Shot – Hexagonal** fill, radius 3 cm; default **nxGravity** and **nxFluids**.

## Steps
1. **nxFluids**: Solver **PBD → SPH**, raise substeps for accuracy.
2. Freeze the blob: **nxDrag** placed **below nxGravity**, Density preset set to the thickest option (**Mercury**) — drag cancels gravity completely.
3. Emitter ▸ Groups: Ctrl+Alt-click the add button twice → groups 1 and 2; mode **Random → First Group Only** (everything born into group 1).
4. nxDrag ▸ Groups Affected: **group 1** only.
5. **nxQuestion** ▸ add Question: **Particle Neighbors less than 15** (each particle searches ~10 cm around itself; surface particles have fewer neighbours). Action: **Set Group → group 2**. Outer shell now escapes the drag and falls.
6. **nxConstraints**, Groups Affected **group 2**: type **Viscosity**, more iterations, **3 connections** per particle, stiffness lowered → gloopy drips.
7. Order: put nxConstraints **under nxFluids** so the fluid solves first.
8. Too fast? Lower the neighbour threshold to **12**. The question keeps re-evaluating, so new surface layers keep melting until the blob is gone.

## Gotchas
- Modifier order matters: nxDrag after gravity, constraints after fluids.

## Newest equivalent
In Fused 2025.4 run the liquid on **nxFluids FLIP/APIC** (variable viscosity) and mesh with GPU **nxMesher**. In the 2026.1 beta, **nxMPM** with a Mixer can change material by age/speed, and **nxBind** can hold particles in a volume and release them by age/life/speed/temperature — an alternative to the drag-hold trick.
