# Three gloops with three viscosities (groups + nxConstraints Viscosity mapped to Group)

- Source: Top Tip Tuesday — Gloopy Fluids Mix — https://www.youtube.com/watch?v=14SqrdO1c6o (2025-08-05)
- Host / generation: NeXus (nxFluids SPH, nxConstraints Viscosity, Mapping) + CPU xpAttractor with field falloff
- Goal: pink splashy, green medium, orange very gloopy liquid poured over a bust.

## Base
Three spherical emitters (radius 7.5, regular emission F3–280, speed 0, particle radius 0.7) riding an animated circle spline (Align to Spline tag). nxGravity with variation; colliders on bust + floor.
- Ctrl+D Project Settings ▸ **X-Particles ▸ Subframe steps 2** for strong gravity without stepping.

## Steps
1. **nxFluids** (SPH default) = splashy. [▶ 1:17](https://youtu.be/14SqrdO1c6o?t=77)
2. **nxConstraints ▸ Viscosity layer**: Connection Limit 8, Radius 20 cm, **Stiffness 40%**, **Iterations 2** (more iterations = stronger as well as more accurate). [▶ 2:36](https://youtu.be/14SqrdO1c6o?t=156)
3. Hug the surface: **xpAttractor** at the bust, Velocity mode, Force ~50, Acceleration 0, Speed Limit huge; **Linear field +Y** so the pull fades lower down and particles drop freely. [▶ 4:14](https://youtu.be/14SqrdO1c6o?t=254)
4. Groups: Emitter 1/2/3 → **Add Group** each (groups 1, 2, 3). [▶ 5:03](https://youtu.be/14SqrdO1c6o?t=303)
5. nxConstraints ▸ Mapping ▸ **Group map**: Category Viscosity, Parameter Stiffness, range **1 → 3**. Curve: group 1 → ~0.06 (a touch of binding), group 2 → 0.5, group 3 → 1. [▶ 5:49](https://youtu.be/14SqrdO1c6o?t=349)
6. Cache (≈8 min / 300 F in the demo).

## Newest equivalent
FLIP/APIC (Fused 2025.4) has per-particle viscosity mapping, and the 2026.1 beta adds non-Newtonian settings — see "Chocolate Setting", "Hot/Cold Variable Viscosity".
