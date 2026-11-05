# X-Particles — xpSystem, xpCache, Project Settings, Questions/Actions, Data Mapping, QuickTools, xpPainter

Source: docs.insydium.ltd/x-particles/* (Fused 2025, checked 2026-11-03). Paraphrased.

## xpSystem
- Created from the INSYDIUM menu; builds folders: **Emitters, Generators, Dynamics, Utilities, Modifiers (Control / Motion / Sprites / Generate), Actions**. Sub-folders allowed. A default emitter is added (turn off in INSYDIUM Preferences).
- Object tab: Auto-Disable XP Objects, icon color (tell systems apart), **Only Modifiers in Same System**, **Only Deformers in Same System**. Without these, with several systems every modifier hits every particle.
- Cloth Object slot (Create Cloth from Dynamics menu builds the setup).
- Global Transform: list emitters whose already-emitted particles should move with the system.
- Trails behave differently inside vs outside the emitter's system.

## xpCache (put it inside the xpSystem)
- Icon: green = no cache, amber = built but off, **red = in use**.
- Cache Type **External (Files)** default (one file per frame, network-render safe) or Internal (Memory) (short tests only — bloats .c4d). Particle Format; Scale (external only, to match other apps); xpExplosiaFX → X-Particles or **OpenVDB** (rename channels). Folder / Alt Folder / Use Folders.
- Record: Sync (button) or Playback mode; Auto Time or Start/Stop; Record Data All / Basic (velocity only!) / Custom. Padlock objects to protect from re-cache (not from Empty cache). Compress Cache on Build.
- Playback: Hold (freeze at last frame, else sim continues live), Wrap (loop), Local Coords, **Retiming** Disabled (Offset + Scale %, e.g. 200% = 2× speed) / Frame / Time / Custom spline (speed ramps!). Custom Play.
- Inclusion tab: which object types to cache; EFX include/exclude.
- Workflow: set range → Build Cache → check red icon → scrub → retime.
- Speed ramps tip: cache, then Retiming → Custom spline (meshes from xpOpenVDBMesher/nxMesher follow the cached particles).

## Project Settings (Ctrl/Cmd+D → X-Particles)
- **Subframe Steps** — smaller steps for collisions, fluids, constraints; changes results (raise gradually). Also affects PBD/nx viscosity.
- **Collisions** (max per particle per step), **Iterations** (constraints & PBD fluids stiffness), **Accuracy** (early-exit).
- Bullet: Max Steps, Gravity, World Density, Collision Algorithm GImpact (default) / Triangle, Random Seed, **Scene Size** (match your objects), contact point display.

## Classic control system: xpQuestion + xpAction (CPU)
- Add questions in the emitter's **Questions** tab (one question can be shared across emitters). If a particle passes → runs listed **Actions** or switches listed modifiers via **Modifiers to Activate / Deactivate** (no Action needed).
- Categories: Particle Data (age, speed, radius…), Position, Flags (events like hit/collided), Fluid Data, Geometry, Physical Data (temperature, mass, bounce), Other.
- Sub-questions combine AND / OR (create with Create Sub-Question; can't hold actions). Copying sub-questions loses links.
- Gotcha: particle age ≠ scene frame.
- For NeXus/GPU emitters use **nxQuestion** instead (see nexus-dynamics-logic.md).

## Data Mapping (CPU modifiers' Mapping tab)
- Layers: Parameter → Map to (~30 sources: Age, Speed, Distance Traveled, Lifespan, Radius, Scale, Mass, Temperature, Fluid Density, Custom Data, modifier-specific e.g. Segment Length for xpFollowSpline) → Range Min/Max → curve (Y multiplies the parameter). Remove deletes without warning.

## xpQuickTools (menu → dockable dialog) — fastest starting points
- Particle FX: Emit From Object/Selection/Texture/Vertex Map, presets Curl Noise, Dust, Fireworks, Simple Rain, Simple Snow.
- Fluids & Grains: Condensation, Fluid Filaments, Fluid FX Water Body.
- Smoke/Fire: EFX Basic Flame, Basic Smoke, Camp Fire, Fire From Particles (+ Cycles 4D smoke).
- Trails: Create Branches, Nearest By Distance, Network Trails, Tendrils.
- Workflow: Create Cloth, System Sort, **Quick Cache** (Shift = internal), **Assign Groups to Modifiers**.
- Most need a selected object (some fall back to a Figure/Sphere/Torus).

## xpPainter
- Paint particles onto geometry (not on frame 0). Modes Create / Delete / Paint Life, Color, Speed, Radius, Rotation; Ctrl reverses. Brush Radius, Strength, Spacing, **Check Overlaps** (even coverage), Count, Offset, Life 90 F, Radius 5 cm, Direction, Rotation Mode, pen pressure. Creates a Spawn-Only emitter if none linked.
