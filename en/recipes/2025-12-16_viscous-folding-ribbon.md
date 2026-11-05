# Viscous folding ribbon (FLIP from a thin spinning emitter)

- Source: Top Tip Tuesday — Viscous Folding — https://www.youtube.com/watch?v=uadAsfGPo1Y (2025-12-16)
- Host / generation: C4D, Fused 2025.4 (new GPU FLIP + nxMesher) + Redshift
- Goal: a colorful ribbon of goo folding over itself like honey.

## Steps
1. xpEmitter **Rectangle width 0** (thin strip), spinning animation; **Rate 1000**, speed 0, radius **1.4**; color via a gradient **shader** in Display. [▶ 1:24](https://youtu.be/uadAsfGPo1Y?t=84)
   (Breaks the usual "even particles per voxel" FLIP rule, but the solver handles it.)
2. **nxFluids FLIP**, Voxel **2**, **FLIP Fraction 35** (default 95 = noisy surface; lower = smoother). **nxGravity**. [▶ 1:52](https://youtu.be/uadAsfGPo1Y?t=112)
3. Stepping → Project Settings **Subframe Steps 5** (10 is cleaner; smaller scenes need more). [▶ 3:05](https://youtu.be/uadAsfGPo1Y?t=185)
4. **Viscosity 30** + Solver Accuracy **Min/Max substeps 3/5** → ribbon coils. [▶ 4:17](https://youtu.be/uadAsfGPo1Y?t=257)
5. Keep folds: nxGravity **Mapping ▸ Age** → strength full until 80 F, fading to 0 by 105 F. [▶ 5:13](https://youtu.be/uadAsfGPo1Y?t=313)
6. Cache (~3 min).
7. **nxMesher**: radius **0.8**, Polygon Size **0.2** (removes fold artifacts); Smoothing **Gaussian** (Influence Range **0.8**, not the default 5 cm — too slow), strength full; second layer **Mean Curvature** 5–10 iterations (removes faceting/striping, check folds survive). **Transfer Color**. [▶ 9:18](https://youtu.be/uadAsfGPo1Y?t=558)
8. Redshift: Vertex Attribute (color map) → **Subsurface color**. [▶ 10:20](https://youtu.be/uadAsfGPo1Y?t=620)
