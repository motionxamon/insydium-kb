# Art-directed crown splash (FLIP + nxSplash handles)

- Source: Top Tip Tuesday — Crown Splash — https://www.youtube.com/watch?v=S4Bfw_hb9AI (2025-12-09)
- Host / generation: C4D, Fused 2025.4 (nxSplash new, FLIP, nxMesher)
- Goal: a stylised crown with N even peaks and clean thin sheets.

## Steps
1. **nxGravity 700**; **nxFluids FLIP** (domain). Emitter: **Torus** inner 8 / outer 12 cm near the floor, **Shot** over 10 frames, 5 000/frame (→ 15 000/frame final), speed 0, color by speed (max 350). [▶ 0:22](https://youtu.be/S4Bfw_hb9AI?t=22)
2. **nxSplash**: in ortho views put its **Bottom Radius at the torus' middle** (10 cm). **Duration 5 F** (default 30 is far too harsh), Strength ~75%. [▶ 2:24](https://youtu.be/S4Bfw_hb9AI?t=144)
3. Accuracy for sheets: **Voxel 4** (default 10), Solver **Min/Max substeps 2/4**, particle **radius 1** (keep the default voxel:radius ratio ~10:3). [▶ 3:48](https://youtu.be/S4Bfw_hb9AI?t=228)
4. Shape: lower **Top Radius** → more upward cone. **Handle Num = 2 × peaks** (14 for 7 peaks), drag every other power handle down → peaks/troughs. Top/bottom radius handles + Bezier tangents for irregular shapes. Duplicate the splash to look-dev alternatives. [▶ 5:12](https://youtu.be/S4Bfw_hb9AI?t=312)
5. Sheets tearing → more particles (150 k total), **Surface Tension ~1%** (10% = blobs; little is needed at high accuracy), optional **Weak Particle Repulsion** for consistent sheets. [▶ 9:09](https://youtu.be/S4Bfw_hb9AI?t=549)
6. **nxMesher** radius 1.3, Polygon Size 1, **Zhu-Bridson** (smooth without smoothing layers) → water material. [▶ 10:12](https://youtu.be/S4Bfw_hb9AI?t=612)
