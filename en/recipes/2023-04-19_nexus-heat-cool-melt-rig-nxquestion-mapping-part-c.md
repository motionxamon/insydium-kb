# Interactive melt / re-harden rig driven by particle color (nxSpeed Clamp Max Speed mapping + nxQuestion fields + nxBlend + mapped SPH viscosity)

- Source: INSYDIUM LIVE! — April 2023 - X-Particles, NeXus & MeshTools — https://www.youtube.com/watch?v=U8zISIlBq90 (2023-04-19)
- Host / generation: C4D; G2 NeXus preview (nxFluids SPH, nxGravity, nxSpeed, Data Mapping, nxQuestion, nxBlend on an xpEmitter) — features shipped in Fused 2023.3
- Goal: a solid cylinder of fluid melts where a field "heats" it, drips at its edges and cools back to solid, interactively in the viewport.

## Base
Plane **2000 × 2000**, blue color, collider tag: no bounce, high friction. **xpEmitter** shape **Cylinder**, rotate P **90°**, Y **100** (sits on the floor). Emission **Shot**, **Hexagonal**, mode **Simulate**, speed 0, radius **2**, **Jitter 1 cm** on X/Y/Z, particle color **black** (color is the control signal).

## Steps
1. **nxGravity**; **nxFluids** solver **SPH**, more substeps, Viscosity max with **1000** iterations, Surface Tension **50**. [▶ 48:27](https://youtu.be/U8zISIlBq90?t=2907)
2. Freeze black particles: **nxSpeed**, Operation Incremental → **Acceleration**, value 0, **Clamp Max Speed 100,000**; Mapping layer **Color Brightness → Clamp Max Speed** with a very narrow output range so black = ~0 speed. [▶ 49:18](https://youtu.be/U8zISIlBq90?t=2958)
3. Move nxSpeed to the **bottom** of the modifier list — it must execute after gravity and fluids or the blob still sinks. [▶ 50:54](https://youtu.be/U8zISIlBq90?t=3054)
4. **nxQuestion** "heat": Particle **Age ≥ 0** → Action **Set Color**, value **100%** (a touch of yellow). Add a spherical **Field** to the question → only particles in the field turn white and melt. [▶ 52:27](https://youtu.be/U8zISIlBq90?t=3147)
5. nxQuestion "cool" below it: same condition → color **black**, action **Weight** low (**3%**) so cooling lags heating. [▶ 54:35](https://youtu.be/U8zISIlBq90?t=3275)
6. nxQuestion "edges": **Particle Neighbors < 30** (search ~10 cm) → color white — finds the surface so edges keep dripping while the core re-hardens (preview it with red). [▶ 56:23](https://youtu.be/U8zISIlBq90?t=3383)
7. Heat spreading: **nxBlend**, mode **Additive**, Distance **50**, Strength max, blend time **60 → 90** frames. [▶ 58:45](https://youtu.be/U8zISIlBq90?t=3525)
8. Varied cooling: cool question ▸ Fields ▸ Shader field with **Noise (Blistered Turbulence)**, big scale, high contrast; weight up to **10%**, then **8%** (too strong cools particles mid-air). [▶ 59:46](https://youtu.be/U8zISIlBq90?t=3586)
9. nxFluids Mapping: Color Brightness → **SPH Viscosity** (black high, white low, curve eased), then copy the map for **Surface Tension** → hot particles run, then gloop and set. [▶ 1:02:15](https://youtu.be/U8zISIlBq90?t=3735)

## Gotchas
- Execution order decides whether the speed clamp wins.
- Equal-weight heat and cool questions cancel out — weight the cool action down.
- Ran interactively on an RTX 2080.

## Newest equivalent
Related recipes: "nxFluids Melt Rig" (2024-01-02) and "Hot/Cold Variable Viscosity" (2025-09-09). In Fused 2025.4 use **nxFluids FLIP/APIC** with variable viscosity and GPU **nxMesher**; 2026.1 beta adds non-Newtonian FLIP (Flow Index, Yield Stress), **nxMPM** Mixer material change, and **nxBind** release by temperature, plus 16 nxFalloff modes for the heat zone.
