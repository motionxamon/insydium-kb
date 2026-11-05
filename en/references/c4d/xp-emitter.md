# X-Particles — xpEmitter (all tabs)

Source: docs.insydium.ltd/x-particles/xpemitter/* (Fused 2025, checked 2026-11-03). Paraphrased.

Everything in X-Particles starts at an **xpEmitter** (normally under an **xpSystem** with its Emitters / Modifiers / Generators folders — created automatically). Emit from built-in shapes, any object, generator or spline.

## Object tab
- **Emitter Shape:** Rectangle (default, plane Z+), Circle, Ellipse, Sphere, Box (Random or **Grid** emit), Cylinder, Torus, **Object**, **Defined Emission** (Inline / Circular / 3D Grid / Fragmenter List — exact layouts, Static Mode = all on one frame), **Instance** (clone another emitter's settings).
- Shape options: Width/Height, H/V Angle (spread), Cone Angle, Edges/Ring/Surface/Faces Only, 3D toggle, Offset X&Y (off + Z+ = single beam), **Offset Origin** (negative = inside only, positive = outside only), **Retiming** (100%; 0 = nothing emits).
- **Object mode — Emit From:** Polygon Center (default), Polygons, Polygon Area, Points, Edges (splines: Even Distribution/Spacing, Emission Point Position %, Spread, Segments), N-gon Center, **Texture**, **Object Color**, **Illumination** (from lights), Object Position (one per child object — great for MoGraph/cloners), **Object Volume**, **Voxel Grid** (Size, Random/Ordered fill along axis, Stop on Grid Full). Vertex color / vertex map **Threshold**.
  - Selection tag / vertex map limits birth area. Particle Direction Normal / Phong / Random / axis; Invert; Perpendicular to Normal; Random Blend curve.
  - **Stick Particle to Source Object** (+ Persist While Stuck) — particles ride an animated mesh.
  - **One Particle Per Source Element** (+ Multiplier) — exact one-per-point/poly, ignores Birthrate.
  - Set Radius By Polygon Size. Object Chain for multiple objects (Connect Objects for curvature).
- Texture tab (Emit From Texture): Texture Tag or Shader; channels Emit / Color / Radius / Speed / Offset / Scale; Mode brightness or R/G/B; Invert; Contrast; Max Samples. Frontal/Camera projection not supported.
- Topology tab: Height and **Slope** limits (min/max + spline) and **Curvature** emission (Ray Angle 80°, Number of Rays 100) — e.g. snow only on flat tops, moss in crevices.
- Initial State tab: **Set State** = freeze current frame as start (pre-rolled sims), Load/Save state (.prt Partio).
- Falloff tab: Infinite / Box / Sphere — must intersect the surface.

## Emission tab
- Modes: **Rate** (default), **Pulse** (Length, Interval, Pulse Spline), **Shot** (Random/Regular/Hexagonal, Shot Time, Duration, Count, Per Frame), **Regular / Hexagonal** (packed volume fill for fluids; Jitter, Spacing), **Trigger** (Pull Trigger checkbox / Change Emitter action), **Controlled Only** (emits only when spawned into — auto-set for spawn targets).
- **Mode:** Simulate (Legacy, default — first emission frame 1), **Simulate** (emits on base frame — cloner-like), **Motion** (re-emits every frame — static-looking but has velocity).
- Emit all Frames / Start–End Emit, Full Lifespan, Lifespan + Variation, Birthrate (per second default or per frame) + Variation + Birthrate Spline + Shader-driven.
- **Subframe Emit** (on — prevents banding), No Intersection at birth, Speed, **Radius** (used by collisions/fluids), Scale (used by xpGenerator/xpSprite/xpFragmenter), death Actions list.
- **Motion Inheritance** tab: Linear / Rotational direction from moving emitter, Speed Blend.
- Thinking Particles tab: generate TP alongside (legacy MoGraph/TP pipelines).
- Gotcha: Shot Count below Duration frame count emits nothing.

## Extended Data tab
- **Rotation:** Use Rotation (off by default — needed for any oriented geometry!), modes None / **Tangential** (along travel, axis Z) / Set / Random / Face Camera / Face Object / Face Screen / Up Vector (with xpFollowSurface); Persist Orientation, Rate of Change, Up-Vector (anti-banking), Simple Spin. xpSpin overrides.
- Other data: **Rewind Data** (for xpHistory), **UV Emission Data** (needed for texture sampling/mapping), **Nearest Particle Data** (P-P distance gradients, plexus), **World Speed** (speed of stuck particles), Emission Vertex.
- **Physical:** Mass (+ Link Mass to Radius), Friction (both sides need >0), Bounce (100% = defer to collider), Temperature/Smoke/Fuel/Burn (xpExplosiaFX), User Value.
- **Fluid** (xpFluidFX only): Liquid/Granular, Density 1000, Viscosity, Vorticity L/S, Surface Tension, granular Friction/Stability/Cohesion. Keep particle sizes similar across emitters.
- **Custom Data:** Add items (ID or Name — never leave ID 0 with no name), types Integer/Float/Matrix/String/Time/Vector, Value on Emission + Variation. Read/written by xpCustomData, Questions, Actions.

## Display tab
- Editor Display Squares (default), Dots (fastest), Ticks, Axes, Box, Spheres (slowest), Lines (length by speed/radius/fixed), Circles (Filled + outline), Cylinder, Pyramid, Arrow, Plane, None. LOD, Display Size Factor, Show Particles toggle, **Display Constraints**.
- **Color Mode:** Icon color / Single / Random / Gradient Random / **Gradient (Parameter)** — by Age, Speed, Radius, Fluid Density, Mass, Temperature, Smoke, Fire, Fuel, Distance Traveled, Direction, P-P Distance, Rotation (Auto range or Min/Max) / Use Shader. Gradient (Parameter) overrides xpColor.
- HUD (particle IDs + one data value), Modifier Field visualisation (vectors of motion modifiers — great for debugging turbulence).
- Orange icon = NeXus/GPU active.

## Groups, Questions, Modifiers, Editing, Advanced
- **Modifiers tab:** by default every modifier in the scene affects every emitter. **Only in Same System** = restrict to modifiers under the same xpSystem. Drag modifiers into Objects and click to toggle yellow check (include) / blue dash (exclude). C4D deformers/effectors only apply when listed here or parented to the emitter.
- Groups tab: Groups to Use overrides display. Questions tab: per-emitter questions.
- Advanced: Threading (on; turn off if strange errors), **Random Seed** — give every emitter a different seed.
