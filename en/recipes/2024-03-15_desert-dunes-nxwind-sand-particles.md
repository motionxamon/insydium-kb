# Wind-blown sand off a desert dune (TerraformFX tfSpline dune + nxWind Von Karman, nxAvoid, field-limited nxTurbulence)

- Source: INSYDIUM Content Repository breakdown — Easy Desert Dunes and GPU Sand Particles — https://www.youtube.com/watch?v=0ZZRRg4WbBc (2024-03-15)
- Host / generation: C4D; TerraformFX + xpEmitter driven by NeXus GPU modifiers (nxWind, nxAvoid, nxTurbulence) — G2; xpSplineMesher + xpCache; Cycles 4D render
- Goal: a sharp-crested dune in low sun with sand streaming off the ridge and kicking up at the lip.

## Dune terrain
1. **tfTerrain** (delete Hydraulic Erosion and tfGrid, disable the noise, hide coloration). Add **tfSpline** above the noise, link the dune spline.
2. tfSpline: **Resample off** (use the spline's own intermediate points, else the height field gets dotted); Radius **110**.
3. Curves (x = along the spline): **Radius** and **Gain** curves dipped at both ends so the dune tapers at the terrain edges; **Falloff** curve pulled down to make a crisp crest. Operator Gain **40 cm**.
4. tfTerrain lighting: low **Pitch**, rotate **Heading** so the windward side is lit and the lee in shadow.
5. tfNoise on: blend **Screen**, very low gain (~0.1), Wavy Turbulence, larger scale, cycle seeds → subtle ripples.
6. Duplicate the terrain twice: **render** copy with Segments **1500** → Make Editable (C) — this also extracts a light rig; **sim** copy with lighting off, Segments **100** → Make Editable. Keep the live original grouped (Alt+G) for tweaks.

## Sand particles
7. **xpSystem**, low-poly terrain in Utilities. **xpEmitter** ▸ Object = low-poly terrain, emit from **Texture**: C4D material on the terrain with a **Luka** noise, strong low/high clip, Y scale squashed (stratified stripes), Animation Speed **0.2** (enable Animate Preview to see it). Texture tab = that texture tag, Emit channel Color.
8. Emission: speed 0, radius 0.5, Birth Rate **100,000**, display Dots; Lifespan **150** (var 20); timeline 500 frames. Falloff tab: **Sphere** around the hero area.
9. **nxWind** rotated 90° to blow along +X, mode **Von Karman** (natural gusts), Strength **20 cm** (10 also works); default turbulent swirls.
10. **nxAvoid** = low-poly terrain, detection distance 15; emitter ▸ **Origin Offset 2 cm** so particles aren't born inside the surface.
11. Lip kick: **nxTurbulence** type Turbulence, Strength 10, Scale 90, Octaves **4**, Persistence **27**, Frequency **170**.
12. Custom volume: duplicate the dune spline, move its points (Right view, X-ray) to hug the ridge; **xpSplineMesher** with Caps on, joins and vertex colours off. Drop it in nxTurbulence **Fields** as a **Volume** layer and hide it → turbulence only at the crest.
13. **xpCache** to external files: 500 frames took ~3 min 50 s, ~5 GB.

## Render (Cycles 4D)
14. Cycles 4D camera with a long **100 mm** lens (helicopter look). **Cycles Instance tag** on the emitter: sphere Segments **8**, Size Multiplier **16%** (var 20%). Replace the light rig with a **Cycles 4D Sky** (low elevation, rotate the sun). Hide the low-poly terrain and spline mesh from render; simple diffuse materials (sand on the high-poly terrain, slightly rougher on particles).

## Newest equivalent
In NeXus 2026.1 the spline-mesh volume can be a **Spline nxFalloff** mode on the nxTurbulence layer, nxAvoid/collision via an **nxCollider** object and the cache via **nxCache**; settling or piling sand would now be **nxMPM** sand presets.
