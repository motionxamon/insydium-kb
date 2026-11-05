# X-Particles — Generators, Dynamics, Tags (CPU)

Source: docs.insydium.ltd/x-particles/{generators,dynamics,tags}/* (Fused 2025, checked 2026-11-03). Paraphrased.

## Generators (turn particles into renderable things)
- **xpGenerator** — instance child objects on particles. Link an emitter first. Clone Type **Duplicate** (default) / Instances / **Render Instances** / Multi Instances (use RI/MI for 10k+). Multiple children Sequentially / Randomly / by Index / Gradient. Rotate Using Particle Rotation (needs **Use Rotation** on emitter!). Scale Using Particle Radius (default) / Scale / Source / Set. Draw Mode Particles Only for heavy scenes. Exclude from cache if Geometry on Render Only.
- **xpSprite** — lightweight primitives (cube, cross, placard, sphere, cylinder, capsule, cone, pyramid, disc, 3-plane), Light (adds Lens Effects), Points, **Text**, Rubble. Scale default 1 → size accordingly. Driven by xpSpriteControl / xpLight / xpText.
- **xpTrail** — splines from particle (or object) paths. Length Mode Time, Trail Length frames, Freeze When Complete. **Algorithm:** No Connections (classic trails), Straight Sequence, Nearest by Index / **by Distance** (plexus), Cluster, Tendrils, Constraints, Infectio. **Draw Splines** must be on. Render with X-Particles Material, C4D Hair, Sweep, or xpSplineMesher. Inside/outside system matters.
- **xpSplineMesher** — renderable tubes from xpTrail/splines, merges xpBranch segments; Growth 100%, Plane Up Free; Render Only for speed.
- **xpOpenVDBMesher** — voxel mesher: modes **Mesh / Spheres / ExplosiaFX / Fog / Voxels**; Voxel Size, Point Radius, Filters stack (Median on by default; Gaussian, etc. — order matters), CSG with objects, Transfer Velocity (trails/motion blur), Transfer Foam (from xpFoam), Object ID/color blending. CPU counterpart of nxMesher.
- **xpPlanarMesher** — triangles between nearby particles (match distance with xpTrail Nearest by Distance for plexus surfaces).
- **xpShatter** — fracture meshes: Volume (solid) or Surface (skin) modes; **recursive layers** (each layer breaks previous fragments) with point generators (bounding box, surface, point container, shader, radial); triggers Always / Time / Speed / **Collision** (with xpBullet: Rigid Body tag on shatter + Collider tag on obstacles) / Volume; Explode, Offset (gaps). Collision Speed defaults to 0.
- **xpFragmenter** — break emitter source polygons into flying faces (Faces Objects / Faces Polys) or move objects with particles. Emitter must emit from Polygon Center.
- **xpElektrix** — lightning: To Object / Spherical / To Particles / Particle to Particle; Divisions, forks, Bend, Displacement. Works without an emitter.
- **xpScatter** — scatter child objects on surfaces by texture, illumination, topology (height/slope/curvature), spacing Kill/Push.
- **xpOcean** — Tessendorf ocean mesh or deformer: Wind Speed/Direction/Alignment, Smallest Wave, Choppiness, **Foam Map** vertex map, Ocean Size > object to avoid tiling.
- **xpCellAuto** — cellular automata growth: Diffusion Limited Aggregation (coral/crystal growth), Elementary (Rule No.), Game of Life. Linked emitter locked to Controlled Only.
- **xpDisplayRender** — make viewport particle display / field vectors / collider bounds renderable (techy HUD looks).

## Dynamics
- **xpExplosiaFX (CPU smoke/fire)** — objects need **xpExplosiaFX Source tag** (Fuel 0 = no burning; Heat, Smoke, Pressure, Velocity, Color From; emitters need Temperature + fuel; cloners under a Join; dense meshes for texture sampling) and sit inside the solver box. Voxel Size, **Upres** (draft low → upres keeps look), Burning Chemical/Custom, Dissipation, built-in wind +Z, Modifiers tab (e.g. xpFlowField), adaptive bounds. Cache to OpenVDB via xpCache. Prefer **nxExplosiaFX** on GPU for speed.
- **xpFluidFX** — CPU SPH (medium–large). Accuracy Fast/Custom; Mode **Velocity** (default, fights other modifiers) or Position (cooperates, slower, more viscous); Velocity Correction; Check Density. Fluid props live in emitter Extended Data → Fluid.
- **xpFluidPBD** — CPU PBD fluid; Damping 1%; Treat Collision As None; Check Density; lower Strength if it explodes.
- **xpFluidFLIP** — CPU grid fluid; Type **APIC** (default) or FLIP (calmer); **voxel ≈ 3–4× particle radius**; Sticky Objects on; walls; unstable → lower CFL, raise substeps, Solid Objects.
- **xpFoam** — foam/spray from (cached) fluids: Crest, Air, Speed, Life, Radius; Surface ≈50%; After Age.
- **xpSheeter** — fill holes in thin fluid sheets (films).
- **xpSplash / xpWave** — CPU versions of nxSplash/nxWave.
- **xpConstraints** — same layer set as nxConstraints (birth/distance/custom connections, collisions, forces, viscosity, friction, surface tension). Stiff → raise Project Settings iterations/subframes. Display Constraints on emitter.
- **xpPPCollisions** — particle–particle collisions; Spawn / Kill / **Connect on Collision**; separate spawning emitter.
- **xpFlock** — CPU flocking (Velocity overrides turbulence; Force mixes).
- **xpFlowField** — velocity-vector grid from random/shader/object/splines/polygons/turbulence/curl layers; Cell Size, Strength, affects Direction/Velocity/Acceleration; Animate Flow is slow. Also works as a modifier inside xpExplosiaFX.
- **xpClothFX** — **Create Cloth** (Dynamics menu) builds: cloth object + xpEmitter (from points, one per vertex, Shot, speed 0) + **xpClothDeformer** (needed for primitives) + **xpClothModifier** (no settings, must be active) + optional **xpSurface** (thickness, subdivision, better tearing). Settings live on the **xpCloth tag** (on the deformer if used): Iterations (stiffness), Structure/Shear/Bend; **Plasticity** Start/Limit (permanent dents — metal); **Tearing** strength, stress break count, tear map; Pinning vertex map; Collisions Simulate/Connect; Sticky (polygon only). xpPin tag pins to another object. Higher subframes stiffen cloth.
- **Bullet:** **xpBullet Rigid Body** tag (Activate Immediate / On Collision / After Time; shape Auto/Box/Sphere/Cylinder/Capsule/Convex Hull (+Full Hull)/Triangulated Mesh; density World/Custom/Mass; Bounce, Friction), **Soft Body** tag, **Collider** tag, Forces/Modifiers tabs; **xpBulletConstraints** (Fixed, 6DOF, Cone, Hinge, Point to Point, Slider, Spring, Sticky; Break on Impulse). Scene Size in Project Settings.

## Tags
- **xpCollider** — required for particles to hit an object: Bounce/Variation, Friction, Scatter, collision engine (adaptive bounds), Actions on collision (no question needed; speed actions don't work → use xpSpeed), **Connect on Collision** (sticky goo). Groups list limits colliders.
- **xpDynamics** — make an object soft/rigid via attached particles (vertices/surface/volume): Rigidity, Pressure, Volume Pressure, constraint strengths, initial Linear/Angular velocity. Don't keyframe + simulate.
- **xpExplosiaFX Source / Collider** tags — see above.
- **xpWetMap** — wetness vertex map where particles hit (Distance, Wetness, Fade = drying, Spread); object must be editable; uncheck Render Only to preview. Use: wet sand/footprint darkening, rain-soaked surfaces.
- **xpPin**, **xpLink**, **xpTrailTip**, **xpPathData**, **xpNewtonGravity**, **xpFreeze**, **xpLight**, **xpCache** tag — small helper tags (pinning cloth, linking objects to particles, trail tips, path data, gravity sources, freeze, lights, per-object cache enable).
