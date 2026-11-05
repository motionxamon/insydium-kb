# Wiggly animated trails turned into tapered tubes (xpTrailDeformer formula/noise + xpSplineMesher)

- Source: Top Tip Tuesday — xpTrailDeformer — https://www.youtube.com/watch?v=YaFY_HUvnug (2023-02-14)
- Host / generation: C4D; CPU X-Particles (xpEmitter, xpTrail, xpTrailDeformer, xpSplineMesher, turbulence); works on any C4D spline
- Goal: organic, wavy trail motion and quick render geometry from trails. (First Top Tip Tuesday episode.)

## Base
Spherical emitter firing particles; **xpTrail** generating straight trails.

## Steps
1. X-Particles ▸ Utilities ▸ **xpTrailDeformer**; make it a **child of the xpTrail** (like any deformer) → animated sine wiggle from the default **Formula** on Y. [▶ 1:06](https://youtu.be/YaFY_HUvnug?t=66)
2. Keep the head attached: **Strength along spline** curve (tail → particle end); pull the particle-end knot to 0 so trails don't drift off their particle. [▶ 1:45](https://youtu.be/YaFY_HUvnug?t=105)
3. Less regular motion: delete the formula; **Shader** tab ▸ Y ▸ C4D **Noise**, raise **Mix**; noise **Global Scale ~3000** + **Animation Speed** so it cycles; then lower Mix to a subtle amount. [▶ 3:03](https://youtu.be/YaFY_HUvnug?t=183)
4. Enable the scene's turbulence modifier for extra motion.
5. Generators ▸ **xpSplineMesher**; link the xpTrail → basic geometry around each trail. **Subdivisions** 1–2 → round tubes. [▶ 4:06](https://youtu.be/YaFY_HUvnug?t=246)
6. Taper: open the **Size** curve (trail start → particle) and shape it thin at the tip, fuller toward the particle. Hide the trail. [▶ 4:33](https://youtu.be/YaFY_HUvnug?t=273)
7. More deformer Mix = more wriggle in the meshes too.

## Newest equivalent
nxWarp (2026.1 beta; Noise / Wind gust wave / Helix, Deform mode) can deform particles and meshes; trails/meshing via nxTrail / nxMesher.
