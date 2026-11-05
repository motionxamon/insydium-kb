# Beading water droplets (nxFluids SPH surface tension + age-mapped nxGravity)

- Source: Top Tip Tuesday — NeXus Water Droplets — https://www.youtube.com/watch?v=DCggkQ6Mu_w (2024-04-02)
- Host / generation: C4D; NeXus GPU (nxFluids SPH, nxGravity Mapping, nxKill) + CPU **xpOpenVDBMesher**; Cycles 4D render
- Goal: water that beads into drops in mid-air before falling and beading on a surface.

## Base
xpEmitter Rectangle, Rate 100, speed 0, small radius (value garbled); default nxFluids + nxGravity; **nxKill** box kills particles leaving the area; cube collider.

## Steps
1. **nxFluids** solver **PBD → SPH** (better surface tension), **Substeps 8** (surface tension needs accuracy), **Surface Tension 100%**. [▶ 1:11](https://youtu.be/DCggkQ6Mu_w?t=71)
2. Problem: particles fall before they can bead. Fix in **nxGravity ▸ Mapping ▸ Age** layer → Gravity Strength. Default range 0–30 F ramps 0 → full; set **Range Min 59, Max 65** so particles float weightless ~2 s, bead, then drop. [▶ 3:10](https://youtu.be/DCggkQ6Mu_w?t=190)
3. Gravity strength halved to **450**. [▶ 3:38](https://youtu.be/DCggkQ6Mu_w?t=218)
4. Collider tag: raise **Friction** so droplets stick and only slide when hit by others (Bounce/Scatter also available). [▶ 4:15](https://youtu.be/DCggkQ6Mu_w?t=255)
5. **xpOpenVDBMesher**: source emitter, **Voxel size 1**, **Point Radius 3**, one **Curvature** filter, Iterations 4. [▶ 4:58](https://youtu.be/DCggkQ6Mu_w?t=298)
6. Simple materials + Cycles 4D environment; real-time preview. [▶ 5:23](https://youtu.be/DCggkQ6Mu_w?t=323)

## Newest equivalent
**nxFluids FLIP/APIC** (Fused 2025.4) adds surface-tension tendrils; mesh with GPU **nxMesher**. nxCollider (2026.1 beta) adds adhesion for sticky droplets.
