# nxFollowGeo — tool card

Mentioned in **18** recipes · 2023-03-29 → 2026-10-30 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **nxFollowGeo** ▸ Object = Bezier circle (auto-detects spline vs polygon). **Release ▸ Spline End: Loop**. **Extended Data**: delete the default **Offset** layer (0.2 m ribbon offset) — the fluid solver handles spacing. [▶ 1:55](https://youtu.be/na6NGPw4XWM?t=115) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*
- nxFollowGeo tuning: overall **Strength 50%**; **Attract Strength** up = tighter to the curve and smoother; **Active Range 2.5** lets it break up and rejoin. [▶ 8:47](https://youtu.be/na6NGPw4XWM?t=527) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*
- Cycles GPU: noise threshold up, 1000 samples, no denoise; **Fast GI Approximation** for previews; **Motion Blur shutter 1 frame** (reads cached velocity automatically). Area lights (Normalize off; e.g. 50/40/30, Track To the nxFollowGeo at origin); Principled Transmission 1, roughness ~0, **IOR 1.33**; optional DOF (F-stop ~3.3) on the follow-geo object. **Lock Interface** before rendering. [▶ 18:39](https://youtu.be/na6NGPw4XWM?t=1119) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*
- **nxFollowGeo** → spline = circle. Mode **Force** (not Guide) so fluids/turbulence still act. Raise Follow Strength; **Attract Strength ~400** to keep them on the path. [▶ 1:43](https://youtu.be/5Ra6keP2ZgE?t=103) — *[2025-11-18](../../recipes/2025-11-18_nxfollowgeo-spline-flow-pbd.md)*
- …so use the collider's **Forces tab → Attraction**, Radius 100 cm, strength ~59 → particles hug the surface while pushing apart. (Avoid nxFollowGeo + nxPush — opposing forces.) [▶ 6:19](https://youtu.be/PTamR793O-k?t=379) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- **nxFollowGeo** with the Emission geometry, **Field of View 360**; **nxTurbulence** noise **Voronoise** → points wander over the surface. [▶ 2:05](https://youtu.be/UXqS-dqsHiM?t=125) — *[2025-08-07](../../recipes/2025-08-07_procedural-plasma-ball-mtsplinefx.md)*
- **nxFollowGeo**: object = wolf head, **Surface** mode, **Field of Vision 360°**, **Friction 1%**, **Distance 25** so every particle gets captured. [▶ 1:10](https://youtu.be/RUhF1pju3Wk?t=70) — *[2025-05-06](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)*
- nxFollowGeo mode **Surface → Edge**; raise the Edge setting to hug edges tighter → wireframe reveal. [▶ 3:05](https://youtu.be/RUhF1pju3Wk?t=185) — *[2025-05-06](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)*
- xpEmitter ▸ Object: source = **the Select object** (not the model), Polygons, drop the polygon selection in; nxFollowGeo also uses the Select object. [▶ 1:41](https://youtu.be/AmfN_ZlpBcE?t=101) — *[2025-01-28](../../recipes/2025-01-28_meshtools-animated-selection-emission.md)*
- Edge version: nxFollowGeo **Edge mode, Edge 100%, offset 2 cm**; in Select switch polygon off, **Edge selection on**; emitter emit from **Edges** with the edge selection. [▶ 3:23](https://youtu.be/AmfN_ZlpBcE?t=203) — *[2025-01-28](../../recipes/2025-01-28_meshtools-animated-selection-emission.md)*
- nxFollowGeo ▸ Groups Affected: **group 1** only. [▶ 1:00](https://youtu.be/wO5-UoWNTkA?t=60) — *[2025-01-14](../../recipes/2025-01-14_nxquestion-random-math-dissolve.md)*
- **nxFollowGeo** with the torus (each linked object gets its own settings): **Field of View 360°** so particles always stick. [▶ 1:11](https://youtu.be/dLTdpbRiG68?t=71) — *[2024-05-14](../../recipes/2024-05-14_nxfollowgeo-surface-fluid.md)*
- nxFollowGeo **Friction 4%** → smoky, wispy flow. [▶ 1:57](https://youtu.be/dLTdpbRiG68?t=117) — *[2024-05-14](../../recipes/2024-05-14_nxfollowgeo-surface-fluid.md)*

## All recipes (18)
- 2026-10-30 · [Shaping particles, smoke and FLIP with warps (nxWarp Scroll / Bend / Helix / Twist — Deform, Guide, Flow modes)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-06-18 · [Liquid stream looping round a curve, meshed with motion blur (nxFollowGeo spline + nxFluids PBD + nxMesher Transfer Velocity)](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)
- 2025-11-18 · [Stringy fluid orbiting multiple splines (nxFollowGeo Force mode + PBD)](../../recipes/2025-11-18_nxfollowgeo-spline-flow-pbd.md)
- 2025-10-07 · [Pulsing particles pushing each other while hugging a surface (collider attraction)](../../recipes/2025-10-07_collider-attraction-surface-push.md)
- 2025-08-14 · [Feature notes: nxFollowGeo spline modes, per-channel nxUpres, layered nxSpeed Range](../../recipes/2025-08-14_nxfollowgeo-splines-nxupres-channels-nxspeed-range.md)
- 2025-08-07 · [Procedural plasma ball (nxFollowGeo + nxTurbulence on particles, mtSplineFX arcs, mtEdgeSpline intersection forks)](../../recipes/2025-08-07_procedural-plasma-ball-mtsplinefx.md)
- 2025-05-08 · [Wrapping a particle ribbon around a spline with C4D deformers (Spline Wrap + Twist on an xpEmitter)](../../recipes/2025-05-08_c4d-deformers-twist-spline-wrap-particles.md)
- 2025-05-06 · [Particle wireframe reveal (nxFollowGeo Edge mode + nxTurbulence + nxSpeed limit)](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)
- 2025-03-13 · [Surface-tangent swirl trails (C4D Field Force + Volume Builder Cross Product vectors + nxColor ▸ xpTrail Per Vertex in Redshift)](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)
- 2025-01-28 · [Emit from animated live selections (MeshTools Select + noise shader → xpEmitter + nxFollowGeo Edge mode)](../../recipes/2025-01-28_meshtools-animated-selection-emission.md)
- 2025-01-14 · [Randomised field-triggered dissolve (nxQuestion Field + Group + Math Random)](../../recipes/2025-01-14_nxquestion-random-math-dissolve.md)
- 2024-05-14 · [Wispy fluid crawling over a torus (nxFollowGeo 360° FOV + friction, nxTurbulence, nxFluids)](../../recipes/2024-05-14_nxfollowgeo-surface-fluid.md)
- 2024-04-22 · [Feature notes: nxFollowGeo, layered nxColor and nxCover (NeXus 2024.2)](../../recipes/2024-04-22_feature-notes-nxfollowgeo-nxcolor-nxcover.md)
- 2024-03-26 · [Stylised wind-tunnel flow lines around a car (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2024-01-09 · [Live particles as points driving a Displacer (XP Editing + C4D Fields Delay)](../../recipes/2024-01-09_xp-editing-particles-drive-deformers.md)
- 2023-11-16 · [Crystals sprouting along frozen particle paths (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-10-03 · [Particles flowing organically along a spline (xpFlowField Along Spline + Curl + To Spline layers)](../../recipes/2023-10-03_xpflowfield-along-spline-curl.md)
- 2023-03-29 · [Spline-directed smoke blast that advects live grains (xpExplosiaFX Advection + xpFlowField Along Spline + emitter falloff)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
