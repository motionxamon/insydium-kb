# X-Particles — Motion modifiers (CPU, `xp*`)

Source: docs.insydium.ltd/x-particles/modifiers/* (Fused 2025, checked 2026-11-03). Paraphrased.

**Shared pattern for all classic modifiers:** `Mode` = **Independent** (default — affects any particle in its field/falloff) or **Action-Controlled** (does nothing until an xpAction "Affect by Modifier"/question turns it on for a particle). Every modifier has Groups (include/exclude particle groups), Falloff/Fields, and a Mapping tab. `Type` **Velocity** = takes full control of motion (overrides e.g. turbulence); **Force** = adds to other modifiers.
GPU equivalent column → see legacy-vs-nexus.md.

| Modifier | What it does | Key settings / defaults | Gotchas |
|---|---|---|---|
| **xpTurbulence** | noise motion | Noise Standard (default) / Turbulence / Wavy / **Curl** (Blend, Add) / FBM / Simplex (MultiOctave/Raw); Scale, Frequency (Standard & Curl only), Octaves (not Standard), Strength; axes | Big Scale = damped; Octaves 0 = nothing; Curl boundaries must be primitives/polys. → nxTurbulence |
| **xpAttractor** | pull to itself/objects | Velocity (default) / Force; Object Select Nearest / Furthest / Average / Index / Random | Nearest target can switch mid-anim. → nxAttract |
| **xpAvoid** | steer away, or freeze / kill | Detection Distance + Variation, Object Shell 1, On Detection Change Direction | Splines use Default Thickness; too low distance = missed. → nxAvoid |
| **xpCover** | stick to surface / fill volume, follow animation | Velocity/Force; Cover/Fill or Target; Operation All Polygons, Polygon Center, Nearest Surface Point, Visible Polygons, Vertices, Volume, Texture; Max Hit Attempts 20; Braking | Target mode never sticks; Align to Normal needs Use Rotation. → nxCover |
| **xpDirection** | steer direction | Operation Absolute (default) / Relative (continuous) / Spray / Circular (emitter Y+) / Jitter / Ring / Use Modifier Rotation; Heading, Pitch; Use Strength | → nxDirection |
| **xpDrag** | medium resistance | Density Air / Custom; Drag Coefficient Sphere / Custom; Strength Multiplier | Depends on speed, radius, mass. → nxDrag |
| **xpExplode** | outward burst | Timing Always On / scene time / particle age; Equals fires once; from Mass Center; Unstick if Necessary | → nxExplode |
| **xpFollowPath** | through ordered list of closed splines (hoops) | Get AOT From Modifier/Tag, Use Min Distance, Speed Mode | Paths must be closed, coplanar, centered axis. |
| **xpFollowSpline** | along spline / xpTrail | Starting Mode Nearest Point…; At End Do Nothing / Loop / Repeat / Reverse; Speed Mode Initial / Current / **Complete Length in Time** / Set Speed; Turbulence on offset/velocity; Offset Blend 50%; Activate Range | Can't follow own emitter's trail; vertex numbering from 0. → nxFollowGeo (spline) |
| **xpFollowSurface** | flow over surfaces | Pull, Offset (+ particle radius), Distance, Friction, Accurate | → nxFollowGeo (surface) |
| **xpGravity** | gravity | Standard (−Y) or **Newton** (orbit attractor objects; Attractor Mass 0 = none, Axis Mask, Kill Distance) | Negative = up. → nxGravity |
| **xpLimit** | clamp position/speed/etc. | Limit Positions, Axis Limit % (100% locks axis), axis restriction ±, Parameter to Limit Speed | → nxLimit |
| **xpNetwork** | grid-like 90° turning paths (circuit/PCB look) | Operation Standard / Inside Volume; Change Mode Time; Change Angle 90° | Constrain Axis only if last modifier; Inside Volume needs one closed object around emitter. Pair with xpTrail. |
| **xpPushApart** | spacing | Absolute / Particle Radius, Distance, Strength, Iterations 5, Only Same Group | → nxPush (much faster) |
| **xpRotator** | spin whole stream around axis | Velocity (default) / Force (+ Attraction); Rotate Speed °/s; Escape Velocity | → nxRotate |
| **xpSoundDisplacement** | displace along axis by .WAV | Start Offset, Use Samples, Scale Down, Sensitivity, Return to Zero | WAV only. |
| **xpSpeed** | change speed | Incremental (per frame!), Use Spline (Speed Max 300), Exponential | → nxSpeed |
| **xpSpin** | per-particle spin/rotate | Spin (needs Use Rotation) / Rotate; Per Frame/Second; Increment ≤45° (0.1–0.3 best) | Overrides emitter spin. → nxSpin |
| **xpSplineFlow** | loose, fluid-like flow along spline via handles | Towards / Along / Rotate / Controls / Attraction multipliers (100%), per-handle settings; 5 handles auto | High Attraction stalls → raise Along. |
| **xpSticky** | stick to (animated) objects | Probability, Range, Tolerance (low), Outside Only, Sticky Time/Falloff | Not splines. → nxSticky |
| **xpStrangeAttractors** | chaotic math attractor paths | Lorenz (default), Rössler, Chen, Chua, Duffing, Aizawa, Rikitake; Velocity type; Max Speed 1500; Iterations 100; Use Preset Values | Force type loses the classic shape. Combine with xpTrail for "strange attractor" lines. |
| **xpVortex** | tornado swirl | Velocity / Force / **Helix**; Invert Rotation; axis from Object or emitter Z | Helix lowest in stack, blend ≥80%. |
| **xpWind** | wind drift | Strength, Turbulence (gusts), Frequency, Scale | → nxWind (Von Karman gusts) |
| **xpSpawn** *(Generate group)* | spawn new particles from source particles | needs **Spawning Emitter** (2nd emitter — becomes Controlled Only); Position Source Particle; Direction Random; Spawn Number per second; Min/Max Interval | Rotation inheritance needs Use Rotation on spawn emitter (not Tangential/Face). nxQuestion Spawn action or Blender nxSpawn on GPU. |
