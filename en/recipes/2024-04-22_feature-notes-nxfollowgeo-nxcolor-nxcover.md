# Feature notes: nxFollowGeo, layered nxColor and nxCover (NeXus 2024.2)

- Source: NeXus Sneak Peek – Modifiers, Release Update Coming Soon 2024.2 — https://www.youtube.com/watch?v=xT2xM7jM4Pc (2024-04-22)
- Host / generation: C4D; NeXus GPU modifiers on orange xpEmitters (G2), with nxTurbulence and nxFluids
- Status: preview of **Fused 2024.2** (9 May 2024)

## nxFollowGeo (new)
- Particles follow an object's **surface** (with **Offset**) or its polygon **edges** (with edge smoothing for tighter motion); nxTurbulence supplies the movement.
- Add **nxFluids** (default) for a fluid sim hugging the surface, or a water-droplet sim on edges; surface ↔ edge mode can be animated.
- **Multiple objects in one modifier, each with its own settings** (duck in Edge mode, wolf in Surface pulling the droplets as it approaches) — keeps the Object Manager tidy.
- Works with **splines** (Offset Variation for a spread) and with animated objects/splines (e.g. Vibrate tag).
- Replaces CPU xpFollowSurface / xpFollowSpline.

## nxColor (new GPU colour modifier, layer stack)
- Layers: **Gradient by Parameter** (e.g. **Speed**: fast = yellow, slow = black; **Distance travelled**; random **Noise** for grain), **Set Color** (single colour or a **shader**, e.g. a logo bitmap with tiling off).
- Each layer has a **blend mode** (Normal, Multiply, Minimum, Overlay…) and Strength; upper layers override/blend with lower ones.

## nxCover (new)
- Covers objects or **splines** with particles (text spline as a layer, mode set to particle speed, for stylish write-on).
- Object modes: **Points, Edges, Polygon area, Volume**, and **Particle Ray** — particles only cover points they can see directly (back faces stay empty).
- Several objects in the list: **Sequence** mode runs through them; **Hold Time** and variation set when they switch; **Object Index** picks a list entry (0 = first) and can be animated.

## Newest equivalent
nxColor became part of the Fused 2025.4 layered modifiers (per-layer GPU falloff/mapping, Noise layer); nxFollowGeo gained multi-spline and Guide/Force modes. For path-shaped streams in 2026.1 also consider **nxWarp** (Path/Helix/Flow). See "nxFollowGeo surface fluid" (2024-05-14) and "nxCover turbulent spline reveal" (2024-05-21).
