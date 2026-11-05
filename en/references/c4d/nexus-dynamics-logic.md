# NeXus (C4D) — remaining dynamics, nxQuestion logic, Mapping, nxFalloff, Preferences

Source: docs.insydium.ltd/nexus/ (Fused 2025, checked 2026-11-03). Paraphrased.

## nxConstraints layers (continued; see nexus-core.md for global settings)
- **Custom connections** — like Distance but separate **Compression** and **Expansion** stiffness, each with Break, Rate, Falloff (Cubic), **Plastic** threshold → links keep the deformed length. Use: bend-and-stay metal/clay, dents. Expansion Break 0 = never breaks. High Connection Limit = slow.
- **Friction** — Friction strength, Connection Limit, Radius, **Static** (% of Radius with full stiffness → particles grip/stack), **Kinetic** (sliding stiffness), Falloff (Cubic). Use: piles, sand-like stacking with PBD.
- **Surface Tension** — Radius (bigger = bigger blobs), Inner (stops collapse), Tension, Falloff (Linear). Best with nxFluids PBD. High tension → raise Iterations.
- **Viscosity** — Connection Limit, Radius, Stiffness. For honey: moderate Stiffness (<100%) + higher Iterations is more stable than 100% stiffness.

## nxFoam (whitewater from fluids)
- Layers: **Surface Foam / Bubbles / Spray** (any number). Per layer Spawn (Rate, Radius, Threshold, Spawn Above/Below surface depth, After Age, Life, Velocity Scale, Radius) and Detection ramps (Kinetic Energy, Wave Curvature — main driver for foam/spray, Turbulence — main for bubbles, Fluid Density window).
- Optional dedicated xpEmitter per layer (else uses source fluid emitter) — easier to render/mesh separately.
- **Advection:** set Simulation Bounds = your nxFluids domain (particles outside are killed), Gravity = same as fluid; Drag/Buoyancy/Rotation/Push per type; Type Transition Convert/Kill with Transition Time (stops flicker); Foam **Erosion**.

## nxSplash
- Cone object with Bezier handles (Bottom/Top Radius → launch angle, Height, Handle Num, Strength >100% ok), **Start Time + Duration** (time it to the impact frame), Distance (must reach fluid particles or nothing happens), Falloff + Strength Falloff curves. Gravity reduces achieved height.

## nxWave
- Velocity field that rolls waves through a fluid. Size box, **Speed** (cm/s, default 100), Strength (wave height), Noise Type, Scale X/Z (Z = wavelength, low X = chaotic), Time Scale (0 = frozen), Low/High Clip, Brightness (lifts all), Contrast (0 = flat, negative inverts). Display only previews.

## nxQuestion (GPU logic — replaces xpQuestion/xpAction chains for NeXus emitters)
Layer list built via Add menu: **Question**, **Action**, **Folder**, **Loop**, **Variable**, **Script**. Object tab: Iterations (whole list runs N× per frame), Weight (scales Action changes, not Scripts).
- **Question:** If / Else If / Else chains (order matters: put highest threshold first). Categories:
  - Particle: Age, Color, Count, Traveled, Speed, Velocity, Position, Radius, Rotation, Mass, Life, Group, ID, **Neighbors**, Emitter, Flags (Hit Object, Hit Particle, Changed Group, Stuck, Frozen, Born), Smoke/Temperature/Fuel (from nxExplosiaFX), Fluid Density (needs nxFluids), Field (needs active field in Fields tab), UVW, Vertex Weight.
  - Document: Frame, Time, Camera Distance/FOV, Object Distance (Points/Position/Polygon/Volume).
  - Math: Value, Random, Spline (X=time), Variable, Wave.
  - Compare: <, ≤, =, ≠, ≥, >, Within/Not Within. **Check Once** = test only until it passes. Combine with child questions: AND / AND NOT / OR / OR NOT; attach Action to the last one.
- **Action:** Set, Add (accumulates every frame!), Spawn (needs its own xpEmitter — use Add Emitter button; Count, Distance, Velocity Random/Source, Life, Inherit Parent), Kill, Break (exit loop/script). Weight <100% = gradual change; **Delay + Damping** = spring easing (only Color, Mass, Radius, Speed); Set Once.
- **Variable:** Float / Integer / User Data (reads a User Data slider on the nxQuestion object — handy for exposing controls). Writeable; **Particle** = per-particle storage (costs VRAM). Unique names.
- **Script:** restricted **GLSL** run per particle in parallel on GPU. Built-ins: `particle.{age,life,speed,color,position,velocity,radius,mass,born,random,...}`, `particles[n]` (read-only), `index`, `doc.{time,delta,frame,fps}`, `emitter[n].create()` + `newparticle[n]` (n must be a literal int), `math.random(seed)`, `print()` (guard with `if(index==0)`). `particle.neighbors()` / `particle.density` need nxFluids. `particle.smoke/temperature/fuel` can be reused as custom accumulators if no nxExplosiaFX. Define functions/globals before use; test with low counts.

## Mapping tab (every nx modifier)
- Add a map layer → choose the parameter → **Map to** data: Age, Speed, Radius, Life, Mass, Distance, Color/R/G/B, Temperature, ID, Group, Vertex Weight, Shader.
- Range Min/Max (e.g. Age 0–60 F), Clamp Mode **Clamp** (default) / Cycle / Continue, Weight, curve (X = range 0→1, Y = multiplier).
- Classic uses: nxScale by Age (grow then shrink), pulse with wavy curve, turbulence stronger at high speed.

## nxFalloff (GPU falloff object)
- Modes Box / Linear (default Y+) / Sphere / Noise (Simplex, Curl, Turbulence, Wavy Turbulence, Voronoise, FBM, Cubic). Invert, Weight, Scale, Spline remap, Blend Mode/Strength for stacking.
- Does nothing until dragged into a modifier's falloff slot; one nxFalloff can drive many modifiers. Modifiers also have built-in quick falloffs (Box/Linear/Sphere/Noise) per layer.
- For NeXus emitters prefer nxFalloff over C4D Fields (Fields tab exists, but nxFalloff is the GPU-native path).

## Preferences
- GPU device (multi-GPU), **VRAM**: Max (default) / Balanced (leave room for Redshift/viewport) / Custom. If rendering on the same GPU crashes — switch to Balanced.

## nxTurbulence (template for most nx modifiers)
- Layer stack processed **bottom → top**; per layer Blend (Normal, Add, Subtract, Multiply, Difference, Screen, Overlay, Min, Max) + Strength + own falloffs.
- Noise: Simplex (default), Curl, Turbulence, Wavy Turbulence, VoroNoise, FBM, Cubic. **Curl Blend / Curl Add** = how curl velocity mixes with other modifiers' velocity (this is NeXus's answer to xpTurbulence motion inheritance; high Curl Blend locks particles to the curl). Seed, Turbulence Strength, Offset, Scale (big = smooth), **Axis Direction Scale** (kill an axis → planar turbulence), Persistence, Lacunarity (not in Simplex), Frequency (evolution speed), Octaves (default 1).
