# Pressure-blast text advection with 10 M particles (nxExplosiaFX)

- Source: Top Tip Tuesday — Pressure Blast — https://www.youtube.com/watch?v=N9SMgriCpAI (2026-04-21)
- Host / generation: C4D, Fused 2025.4+ (nxExplosiaFX as velocity field) + Redshift additive points
- Goal: letters burst outward into fine milky wisps.

## EFX setup (velocity only, no combustion)
1. Two text copies: render text (hidden) and an editable **sim text** (no caps, inner holes removed).
2. Sources: sim text, **Emit From Volume**, **Fuel 0**, **Temperature 4800**, **Pressure 1400**.
3. Simulation ▸ Buoyancy: **Gravity off** (no upward plume).
4. One-shot blast: source **Mapping** → Source Mesh Object, Destination **Scene Time** (0–30 F) → Temperature with a short spike curve; Ctrl-drag copy → Pressure.
5. Colliders: the same sim text → pushes fluid outward.
6. Solver for smooth advection: Pressure Iterations ×2 (20) + more accuracy; Advection **Max Substeps 6**; set smoke/temperature/velocity advection to **Fast** (smoother, less "fire detail"); lower temperature dissipation; **Adaptive Bounds off** (or more extra voxels) so particles never hit the bounds edge; open the −Y wall.

## Particles
7. xpEmitter from the sim text, Polygon Area, **Shot**, lifespan 50 ±20, speed 0. EFX ▸ Particle Advection: Mode **Position**, smoke/temperature/fuel advection off.
8. Count: 10 k → 500 k → **10 M** (Display LOD 0.1). Live sim still plays reasonably.
9. Redshift Object tag ▸ Point instances with additive (emission + opacity) material; point size 1 → 0.1 (500 k) → **0.015** (10 M). More particles, smaller points = milky wisps.
