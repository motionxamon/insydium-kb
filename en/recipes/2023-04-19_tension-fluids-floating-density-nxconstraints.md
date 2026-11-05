# High-tension paint tendrils floating on a fluid bed (nxFluids SPH, nxFluids tag density, per-emitter nxConstraints Forces, nxDrag)

- Source: NAB 2023 - INSYDIUM Training — Tension Fluids - Part 1 — https://www.youtube.com/watch?v=UQvPo7CCcIc (2023-04-19)
- Host / generation: C4D; NeXus GPU (nxFluids SPH, nxGravity, nxConstraints, nxDrag, nxTurbulence) inside X-Particles with xpEmitters; CPU xpCache
- Goal: three colored fluids spat onto a hidden water layer, each clumping into its own gloopy tendrils (mixed-paint look).

## Base
Cube **700 × 50 × 700 cm**, made editable, top polygon deleted → open tray. Display tag (Lines). **xpCollider tag**: Bounce 0, normals set to point **inside** (otherwise the tray leaks).

## Steps
1. **Base emitter**: Box shape fitted just inside the tray (use ortho views), then halved in height and lowered — far fewer particles still give a full surface. **Shot**, Shot type **Hexagonal**, speed 0, **radius 2 cm**, Dots, Draw Emitter off.
2. **nxGravity** (default) + **nxFluids** solver **SPH**, **Substeps 4**.
3. **Colour emitters** (green, then copies blue, red): thin box emitters, **Hexagonal** (continuous), Emit All Frames off, start **F100**, end **F300**, timeline 500 F, speed 0, **same 2 cm radius** (mixed radii make SPH unstable).
4. **nxFluids tag** on every emitter: base Density **1000**, viscosity way down; colour emitters **Density 50**, Viscosity 1, Surface Tension 1 → they float on top.
5. Motion: **Vibrate tag** on the colour emitters (position + rotation). Regular Pulse: ~20 cm X/Z, heading 60° → 40°. Without Regular Pulse (noise, per-emitter Seed, e.g. 73) push amplitude to 60–100 at frequency 0.6. Rotate each copy differently.
6. **nxConstraints ▸ Forces**, one per colour ("constraints green/blue/red"). In every other emitter's **Modifiers** list add the constraints that must not affect it (minus = excluded), incl. the base emitter. Repulsion and Inner off at first; raise Attraction (≈76), radius **13**, limit 16 → particles clump only with their own colour.
7. Refine: Inner radius **2**, Repulsion **10** at radius **4** keeps blobs from collapsing. Smaller radius / lower limit / lower attraction = thinner, less blobby detail.
8. **nxDrag** (exclude base): Density Water, Drag Coefficient **Fighter Aircraft**, strength multiplier 110 → later **150** (Sphere in water is far too strong).
9. **nxTurbulence** Simplex, strength **15**, slightly larger scale, limited by a **Spherical field** in the pool centre; exclude the base emitter.
10. **xpCache** to external files, all emitters: ~3 min for 500 F in the demo.

## Gotchas
- Inverted collider normals make an open container leak.
- Re-enable the base emitter's cache before re-caching.

## Newest equivalent
Fused 2025.4 **nxFluids FLIP/APIC** with surface-tension tendrils; in the 2026.1 beta the FLIP **Mixer** sets density, viscosity and surface tension per emitter/group, and **nxFalloff** replaces C4D fields. Mesh with **nxMesher**.
