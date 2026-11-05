# Macro water splash with thin sheets (nxFluids APIC/FLIP + nxSheeter + nxMesher Zhu-Bridson, Cycles)

- Source: NeXus for Blender Official Training — Fluid Splash — https://www.youtube.com/watch?v=eeigvIYA19Q (2026-07-02)
- Host / generation: Blender (NeXus for Blender, G3): nxEmitter, nxCollider, nxFluids APIC (FLIP compared), nxGravity, nxTurbulence + Mapping, nxSheeter, nxMesher; Cycles
- Goal: a fast jet hits a sphere and fans into continuous, tendril-edged sheets for a "high-speed macro photo" look.

## Base
- Emitter **Sphere** (default radius), direction **+X**, **Shot 20,000**, speed **17 m/s**.
- UV sphere just past the jet; **nxCollider** layer for it, bounce 0, friction 0.
- **nxFluids ▸ APIC**; bounds ~**38 × 33 × 15 m** just enclosing the emitter. Voxel size does not scale with bounds (default **0.1 m**) → set **0.15**. Display ▸ Back Only shows the grid density.
- **nxGravity** strength **4** (fake slow motion; 9.8 default).
- Floor cube (scaled past frame, hidden) as second nxCollider layer: bounce 0, small friction (~3) — a little goes a long way with FLIP/APIC.

## Steps
1. **nxTurbulence** Voronoi, strength **55**; Mapping ▸ **Age** → layer Voronoi ▸ Turbulence Strength, range **20→50 frames**, inverted curve (full → ~0), small tail optional.
2. Domain **boundary walls**: open **+X, +Z, +Y and −Y**. Escaping particles stop being solved as fluid but keep velocity, gravity and turbulence — cheap alternative to a huge domain.
3. **nxMesher** ▸ Emitter layer: radius **0.08**, coarser polygon size, surface type **Zhu-Bridson** (Spheres suits viscous folding).
4. **nxSheeter** (defaults, uses the existing emitter): fills gaps between separating fluid particles; Output ▸ Custom Display pink to see new particles. Mesher picks them up automatically.
5. APIC **Surface Tension 35** + Sheeter Output **Velocity Scale 1 → 0.9** (slight lag) → beaded leading edges and tendrils.
6. Sheeter refinement: **Min hole size 0, Max hole size ~6** (fewer sparse areas, more web-like tendrils); **Insert Spacing 2 → 1** (× particle radius, denser fill).
7. **Velocity Alignment** (on, 60° default): only particles separating within this angle are sheeted; lower (40–50°) = thinner sheet, more breakaway tendrils.
8. Solver choice: **APIC** keeps angular momentum (spray keeps its kicked-up arc); **FLIP** wraps more around the object and gives sharper tendrils, needs less surface tension; **FLIP Fraction** 66% = smoother globules, 95% = energetic/noisy.
9. Render: area light (Normalize off, large, Track To the sphere). Floor: dark glossy dielectric. Mesh material on the generated child mesh: Principled **Transmission 1, Roughness 0, IOR 1.333**; kill dark shadows by mixing with a **Transparent BSDF** using **Light Path ▸ Is Shadow Ray** as factor (darken transparent color to bring some shadow back). Sphere: smooth-shaded metal.
10. Cycles GPU, low samples + GPU denoise, fixed noise seed, **Fast GI approximation off** (dark patches on glass/water), 100 frames at 720p ≈ 7 min; **Lock Interface** on.
11. Motion blur (optional — real macro shots rarely show it): nxMesher ▸ **Export Tags ▸ Transfer Velocity** (max 10 here) + Cycles Motion Blur.
12. Optional: Mesher smoothing layer **Mean Curvature** at full, control amount with iterations.

## Gotchas
- Default fluid/mesher sizes target small scenes — scale radius/polygon size with the domain.
- Closed walls make spray bounce off invisible ceilings/walls in frame.

## Newest equivalent
2026.1 beta FLIP/APIC adds **Wall Friction**, non-Newtonian settings and a per-emitter **Mixer**; nxMesher gains Detail Aware smoothing and UV advection. In C4D (Fused 2025.4 / NeXus 2026.1) the same nxFluids APIC + nxMesher chain applies.
