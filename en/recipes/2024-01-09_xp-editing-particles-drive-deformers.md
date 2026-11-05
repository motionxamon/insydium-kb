# Live particles as points driving a Displacer (XP Editing + C4D Fields Delay)

- Source: Top Tip Tuesday — Particle Deformation — https://www.youtube.com/watch?v=oVePtsodRBs (2024-01-09)
- Host / generation: C4D; CPU xpFollowSurface mixed with NeXus GPU nxFluids SPH + nxTurbulence; C4D Displacer, Fields, Smoothing
- Goal: particles crawling on a sphere bulge a high-poly copy of it organically.

## Steps
1. **xpFollowSurface** with the sphere (hide it).
2. **nxFluids SPH**, +1 substep (CPU and GPU modifiers can be mixed on one emitter).
3. **nxTurbulence** Voronoi, strength high, large scale.
4. Lost particles: follow-surface distance 10 → **200 cm** (emitter already inside it), **Pull 100%**, a little **Surface Friction** to calm it.
5. Emitter ▸ **XP Editing** tab on → in Point mode each particle is a selectable point that Fields can read.
6. Copy the sphere, 350 segments, reflective material; child **Displacer**: Shading = **Color white**, Height 10 cm (later 30).
7. Displacer ▸ Fields: drag in the **emitter** → bumps wherever particles are. Lower emitter radius for finer detail.
8. Add a **Delay** field layer (Smooth, reduced) for organic lag; stack more delays if wanted.
9. **Smoothing** deformer below the Displacer, raise stiffness.

## Newest equivalent
**nxFollowGeo** replaces xpFollowSurface; nxFalloff **Points** mode and C4D-only **nxFalloffMap** (falloffs → vertex maps) in the 2026.1 beta.
