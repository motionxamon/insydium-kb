# NeXus (C4D) — modifiers reference

Source: docs.insydium.ltd/nexus/modifiers/* (Fused 2025, checked 2026-11-03). Paraphrased.
All nx modifiers share: **Groups Affected**, **Mapping** (drive any param by particle data), **Fields** tab, and most have a **layer stack processed bottom → top** with Blend modes + per-layer falloff (Box/Linear/Sphere/Noise or an nxFalloff object).

## Motion
- **nxTurbulence** — layered noise (Simplex/Curl/Turbulence/Wavy/VoroNoise/FBM/Cubic). Curl Blend/Curl Add = blend with other modifiers' velocity. Axis Direction Scale for planar noise. Octaves default 1. Full notes in nexus-dynamics-logic.md.
- **nxAttract** — pull toward objects. Type **Velocity** (default, overrides other speed modifiers) vs **Acceleration** (cooperates with others). Force 30, Acceleration, Speed Limit, Object Select (Nearest/Furthest/Average/Index/Random). Empty Attractors = no effect.
- **nxAvoid** — steer away from objects; On Detection: Change Direction / Freeze / Die. Detection Distance must exceed per-frame travel. Object Shell margin. Freeze can be undone by an Action or xpNegate.
- **nxCover** — particles land on/cover objects. Object Mode Sequence (morph between objects!) / Nearest / Furthest / Index / Random; Operation Polygon Area / Points / Edges / Volume / Texture (Resolution 128); Speed Mode Use Speed / **Time to Target** (exact frame arrival); Holding Free / Spring / Stick / Attract; Hold Time; Cycle (Sequence only). Use: particles forming logo/shape, morphs.
- **nxDirection** — layered: Direction Force (Direction/Twist/Attract ±100%), Circular (emitter on Y+, Y-Axis Kick), Ring (Loop at 360°)… Force Mode Velocity.
- **nxDrag** — medium Air (default)/water/mercury/Custom density, Drag Coefficient shape, Strength Multiplier. Depends on particle speed, radius, mass.
- **nxExplode** — burst outward; Timing Always On / at Scene Time / at Particle Age; Timing Mode Equals (fires once) / ≥ / ≤; Time 30 F; From Particle Mass Center or This Modifier; Speed, Variation; Unstick if Necessary (on).
- **nxFlock** — behaviours Cohesion / Separation / Alignment / Chaos / Swarming (needs ≥2 emitters/groups), Periphery view angle; Reactions (child objects): Pursuit / Flee / Arrive / Orbit with timing modes; Avoidance Soft/Hard; Min/Max Speed, Natural Limits (max turn angle). Use: birds, fish, insects, chase effects.
- **nxFollowGeo** — one object for surface, edge and spline following. Surface: Pull/Push/Offset/Distance/Friction/FOV, Release None (default — never leaves!) / Texture / Selection / Falloff / Time. Edge: Edge tightness, Smoothing. Spline: Guide (%) vs Force (distance), Activate Range 2 m, Attract 10%, Follow 40%, Align; Extended Data **Offset / Twists / Twist Radius / Radius Along Length** (spirals & tubes along splines); Release Spline End / Falloff / Time / Selection with On Release Loop/Reverse/Kill/Change Group; multi-segment handling. Replaces xpFollowSurface + xpFollowSpline + xpSplineFlow for NeXus.
- **nxGravity** — Strength (−Y; negative = up), Variation per-particle or per-frame (jitter), **Effect Towards** object = point gravity.
- **nxLimit** — clamp velocity/position/scale/rotation/speed/radius/mass/user value per layer.
- **nxPush** — push apart to Distance (Absolute 10 cm or Particle Radius mode), Strength, Iterations 5, Only Same Group. Anti-clumping, even spacing. Much faster than xpPushApart.
- **nxRotate** — spins whole stream around an axis (not individual particles). Force (default, spirals out; Attraction tightens) vs Velocity (tight but overrides turbulence). Escape Velocity.
- **nxSpeed** — Incremental (adds every frame in falloff — keep values tiny) / Absolute / Acceleration / Range (Time Mode Birth/Particle/Frame).
- **nxSpin** — per-particle rotation: Rotate, Facing (Face Camera), Range (by age), Incremental.
- **nxSticky** — stick to polygon objects (make parametric editable; not splines). Probability, Range, Tolerance (keep low), Outside Only, Custom Offset/Distance, Sticky Time + Falloff (very high time = permanent).
- **nxVorticity** — amplify swirls in fluids from neighbour velocities. Radius (small = fine fast detail, >100% = large swirls), Strength (cumulative — unstable if high), **Force Limit**, Exclude Emitters.
- **nxWind** — Standard or **Von Karman** (realistic gusts: Friction Velocity, Scale Length), Strength, Variation, Turbulence per axis, Local/World, Frequency.

## Particle data
- **nxBlend** — neighbours blend Color (on by default), Radius, Mass, Scale, Rotation within Distance; Blend modes; Strength; **Max Blend** (frame number to stop); Weighting per emitter (e.g. emitter A 100% dominates B 0%). Classic: two colored emitters mixing like paint.
- **nxColor** — layered recolor; Change on Birth Only; Change Rate Instant / Frame Time (fade) / Custom; Threshold = random chance; Noise / Gradient / Texture Tag layers (texture needs UV data + UV Emission Data in emitter Extended Data). Shaders are baked to GPU texture (resolution-limited).
- **nxInfectio** — growth/spread from a **Seed Object** (Add Seed Object — required). States uninfected → incubating → infected; Color Mode Fixed / Gradient / Use Groups / none; Search Radius, Max Infected (spread speed), Infected Lifespan (1 frame = kill on infection → "peel/dissolve" reveals), Search for Nearest Once (off for moving particles); Incubation by particle Color (black never infects) / Rate / Radius / Mass; Immunity.
- **nxKill** — Outside Bounds (default — size box generously!) / Inside / Objects / Outside Camera FOV (Widen FOV) / Clamp to Max Particles; Only Born.
- **nxScale** — layered radius/scale/mass: Range, Noise, Set Value, Set by Falloff, by speed/acceleration. Timing On Birth default.

## Utility
- **nxUpres** — interpolate a low-count Source emitter onto a high-count Destination emitter (e.g. 2 k → 80 k). Per-property strengths (Position, Radius, Color, Velocity, Mass, Group), Max Count (higher = smoother/slower), Limit Distance, **Push** to keep volume. Workflow: sim cheap, cache, then upres.
