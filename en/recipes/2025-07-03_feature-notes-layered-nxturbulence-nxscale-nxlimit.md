# Feature notes: layered nxTurbulence, nxScale and the new nxLimit (Fused 2025 preview, part 1)

- Source: Fused 2025 Tech Preview — Modifier Improvements Part 1 — https://www.youtube.com/watch?v=Ec1tTKMlHBM (2025-07-03)
- Host / generation: C4D; NeXus GPU modifiers (nx…) on xpEmitters (G2); Redshift for the final look
- Status: preview of tools that shipped in **Fused 2025.4** (Dec 2025) as "layered modifiers"

## What changed
- **Layer stack in one object**: each modifier holds a list of layers; add from the layer drop-down or Ctrl-drag to duplicate. Layers blend top-over-bottom like Photoshop — **Normal at 100% hides everything below**, Strength slider mixes, **Multiply** modulates the layer below. One object replaces stacks of 5–10 separate turbulences.
- Single-layer nxTurbulence (Voronoise default) behaves like the old nxTurbulence.

## nxTurbulence
- Three-layer recipe: bottom **Curl** (large swirl: Frequency ~12, Scale ~380), middle **Voronoise** (smaller scale, lower frequency; raise Strength to add ribboning), top **FBM** (fine veins: Scale ~83, very low frequency). Set upper layers to Strength 0 while tuning the bottom one, then fade each in.
- Detail shows best in Dot display; <0.5 M particles already read as rich detail in Redshift.
- New **Mode: Direction** (vs default Acceleration): particles stay in place but their heading is animated by the noise; works with every noise type (Cubic = long languid turns, Simplex = fast smooth, Voronoise = jittery). Pair with emitter Display ▸ Color **Gradient by Parameter → Direction** for highlights.

## nxScale (radius / scale / mass)
- Classic layers kept (Set Value, Change over Time, Set by Falloff) plus two new ones:
- **Range** layer: Timing **On Birth** (Radius End + variation, overrides emitter radius) or **Particle Age** (Radius Start → End over Start/End time, e.g. 0–60 F, shaped by an ease curve; extra knot = grow then shrink). Clamp modes: **Clamp** (only inside the window), **Repeat** (pulsing), **Continue** (keeps growing at the same rate). Variation on values *and* on times.
- **Noise** layer: INSYDIUM 3D GPU noises (same set and settings as nxTurbulence, plus low/high clip, brightness, contrast) map black → Radius Start, white → Radius End. Replaces C4D Fields for noise-driven size, stays on the GPU.
- Blend example: Range layer pulses size; Noise layer above in **Multiply** with **Radius End 1** (so it only scales 0–1), Radius Start ~0.4–0.6 to make the noise subtler.

## nxLimit (new)
- Layers: velocity, position, scale, rotation, speed, radius.
- **Position** layer, World coords: Y restriction **Fixed** at 0 flattens a pushing (nxPush) cloud to a plane — replaces the old nxQuestion velocity/speed tricks. X and Z **Range** −200…200 cm (+ variation to soften edges) boxes it in; **Particle** coord mode gives a looser boundary.
- **Radius** layer: clamp max (e.g. 15, 10, 20 cm) and/or min (5) on top of a noise-driven nxScale — changes the cellular blob pattern of a push sim (birth rate 20,000/s, Square display).

## Newest equivalent
All three shipped in Fused 2025.4; in NeXus 2026.1 every layer also gets its own Falloff list and the 16 nxFalloff modes; see "nxTurbulence Direction mode clones" (2026-01-20).
