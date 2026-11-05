# Upside-down crystal "tree" (Taiao Plant spline branches + Custom Object, stacked mtInset animation)

- Source: INSYDIUM LIVE! — November 2023 – X-Particles, NeXus, Taiao, MeshTools & Cycles 4 — https://www.youtube.com/watch?v=qaso-gPGBnI (2023-11-16)
- Host / generation: C4D; Taiao Plant + MeshTools mtInset; two-light glints (Cycles 4D in the final). Part C of 3
- Goal: thousands of faceted animated crystals sprouting from invisible curled branches.

## Steps
1. Taiao ▸ **Plant** ▸ **Trunk**: Radius 3, Height 90.
2. Branch layer 1: long, angled up; **Furling** modifier curl down with **Bias 0** (default 50% starts halfway).
3. Branch layer 2: untick end branch, some angle/length, Furling (bias kept).
4. Branch layer 3 (crystal carrier): many branches (~90), angled up, no end branch. **Distribution** ▸ Position curve raised to full at the base so they run the whole parent length. Soften the first furling if too strong.
5. Global: Object Type **Spline** (no branch polys), Organ Mode **Multi Instances** for viewport speed.
6. Layer 3 ▸ Add Part ▸ **Custom Object** (its Profile tab can shape simple crystals, but here real geometry).
7. Crystal: Oil Tank primitive — height/cap segments 1, rotation 6–7, r 2, h 20. Custom Object ▸ Main ▸ drag it in; Materials ▸ **Phong angle 0** for facets.
8. Plant pitch **180°** (flip instead of an upside-down camera). Two lights, red + blue, for glints.
9. **mtInset** with the oil tank as child: keyframe Amount up to **100% at F90**, Offset **−0.2** (pushes inner faces in). Stack a second mtInset (100%, Offset −0.2) → animated multi-faceted crystal. Reference the top inset in Custom Object instead of the tank.
10. Custom Object Rotation **45°** → spiral arrangement. Layer 3 ▸ Distribution **Twist** keyed 0 → 25° over the shot.
11. Growth tab per layer: first branch layer Growth **99.6 → 100%** gives subtle growth + parallax (tiny range because everything hangs off it). Twist and growth have Variation values.
12. Viewport check: GGX reflectance with Dielectric Fresnel; camera DOF.

## Gotchas
- The emissive "inner wire" flashes in the final come from a Cycles 4D metallic + emission mix with an outline shader — not shown.

## Newest equivalent
Same Taiao/MeshTools route today. For a particle-driven version, nxDendrite or **nxBioLogic** (2026.1, coral/growth with tube meshes) grow branching structures on the GPU.
