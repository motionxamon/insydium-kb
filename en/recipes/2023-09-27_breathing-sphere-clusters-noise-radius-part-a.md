# Self-organising "breathing" sphere clusters (xpColor noise → xpQuestion radius, nxPush mapped, nxConstraints Bind + Friction, Cycles 4D)

- Source: INSYDIUM LIVE! — September 2023 – NeXus, Taiao & X-Particles — https://www.youtube.com/watch?v=uS_zr-Jf178 (2023-09-27)
- Host / generation: C4D; mixed G1 CPU (xpColor, xpQuestion/Action) + G2 NeXus (nxPush, nxConstraints); render Cycles 4D
- Goal: thousands of spheres on a twisted torus that swell and shrink with an animated noise and cluster organically — no position modifiers, only constraints.

## Base
Thin **Torus** on the Z plane + C4D **Twist** deformer 180°, then **Current State to Object** (no live deformers). xpEmitter ▸ Object = torus, emit from **polygon area**; **Shot**, **10,000** particles, **Speed 0**, **Radius 1**; Display **Circles Filled**.

## Steps
1. **xpColor** ▸ Shader = **Noise**, type **Blistered Turbulence**, Global Scale **500%**, Animation Speed **0.3**; push Brightness/Contrast so only bright patches stay white — white particles will grow, dark ones stay small. [▶ 20:03](https://youtu.be/uS_zr-Jf178?t=1203)
2. **xpQuestion**: Particle ▸ Color, **Brightness = 1** → Action **Change Radius** to **10**, Weight **2** (eases the change). [▶ 21:12](https://youtu.be/uS_zr-Jf178?t=1272)
3. Ctrl-add a second question set to **Else** → Change Radius back to **1**, Weight 2 → spheres scale up and back down as the noise moves. [▶ 22:09](https://youtu.be/uS_zr-Jf178?t=1329)
4. **nxPush**: mode **Particle Radius**, maximum strength; **Mapping: Color Brightness → Strength** (white = full push, black = none) → spheres burst into little pushed groups. [▶ 22:36](https://youtu.be/uS_zr-Jf178?t=1356)
5. Stray spheres float off → **nxConstraints ▸ Bind** layer: Connection Limit **20**, big search Radius **300**, Break **None**. [▶ 23:38](https://youtu.be/uS_zr-Jf178?t=1418)
6. Springs now fight the push → add a **Friction** layer (≈20 connections, radius ~80) to damp it; the longer it plays, the more organic, creature-like the motion. [▶ 24:04](https://youtu.be/uS_zr-Jf178?t=1444)
7. Cycles 4D: INSYDIUM ▸ Cycles ▸ **Soft Box** light above the scene; emitter ▸ Cycles **Instance** tag (sphere per particle); **Object material** (Principled BSDF) on the emitter. [▶ 25:59](https://youtu.be/uS_zr-Jf178?t=1559)
8. Drag the emitter into the node editor → **Particle Info** node (particle color; a Cloner/Matrix gives a Matrix Info node the same way). [▶ 26:24](https://youtu.be/uS_zr-Jf178?t=1584)
9. **Mix Shader** between the base BSDF and an **Emission** driven by a **Blackbody** at **3000 K**; mask = a **Ramp** fed by the particle color with a narrow bright band — slide it to pick which particles glow; raise emission strength for strong glow. [▶ 26:49](https://youtu.be/uS_zr-Jf178?t=1609)
10. Optional **Subsurface** (Random Walk, yellow, ~**0.6**) so the glow reads inside the spheres. [▶ 29:01](https://youtu.be/uS_zr-Jf178?t=1741)

## Gotchas
- Push and Bind fight each other; Friction is what makes them settle into living blobs.

## Newest equivalent
Do it all on the GPU: **nxColor** (layered, 2025.4) or an **nxFalloff Noise** mode for the pattern, **nxQuestion** Change Radius (CPU questions don't drive GPU emitters reliably), **nxPush** + **nxConstraints** as here. In NeXus 2026.1 (C4D/Blender) per-layer Falloff lists and Mapping (one layer → many targets) let a single noise drive both radius and push strength.
