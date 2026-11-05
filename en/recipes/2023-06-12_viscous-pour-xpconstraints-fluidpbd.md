# Fast viscous chocolate/honey pour (xpFluidPBD + xpConstraints Viscosity, Hexagonal emission)

- Source: Maintenance Training — Dynamics - Constraints - Viscous Fluids Tutorial — https://www.youtube.com/watch?v=rhFYjdNe2XA (2023-06-12)
- Host / generation: C4D; G1 CPU X-Particles (**xpFluidPBD** + **xpConstraints** in the system's Dynamics folder)
- Goal: gloopy liquid that keeps its folds (product-shot chocolate on a wafer) without slow high-accuracy viscosity.

## Base
Gravity pulling down; colliders: floor plane + elongated cube ("wafer"). Emitter Circle, emitter plane **−Y**. Display Circles filled, gradient blue→white mapped to **Speed**, white at **600 cm/s**.

## Steps
1. **xpConstraints ▸ Viscosity** tab on (a connection type) — particles bind together (check with Display Constraints).
2. Add **xpFluidPBD** for the bulk fluid. PBD viscosity alone (e.g. **50%**) gets gloopy but doesn't hold together; with constraint viscosity back on it does.
3. Constraint viscosity **Stiffness 98** → holds shape.
4. Emission mode **Hexagonal** (made for fluids: particles born non-intersecting, otherwise the solver pushes them apart / explodes).
5. Gaps between emission batches: Connection Limit **16** too low → **40**; and reduce the hexagonal **Spacing** so particles are born overlapping — constraints hold them against PBD's push. Side effect: bulging → make the emitter smaller. Stiffness down to **95**.
6. Ctrl+D Project Settings ▸ X-Particles: **Subframe Steps 3**, **Iterations 3** → stiffer springs, slower sim.
7. Ribbon pour: emitter **Rectangle**, very thin; Hexagonal particle radius **2.5** (more particles); spacing back up a little; Stiffness **90**, Connection Limit **20** → folding ribbons (some striping where too few links).
8. Higher resolution: more particles use up links fast → Connection Limit **100–150** and lower spacing for detailed folds and creases.

## Gotchas
- Too few links = stripy gaps / subframe banding; too stiff = no flow.
- Constraint stiffness depends on substeps/iterations.

## Newest equivalent
GPU: **nxFluids FLIP/APIC** viscosity (Fused 2025.4) or the 2026.1 beta non-Newtonian **Yield Stress / Flow Index** for folds that hold; G2 route = nxFluids SPH + nxConstraints Viscosity layer (see "Viscous Folding Ribbon", "Gloopy Fluids Mix").
