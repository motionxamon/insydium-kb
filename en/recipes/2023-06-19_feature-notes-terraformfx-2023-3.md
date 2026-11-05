# Feature notes: TerraformFX 2023.3 — tfTrace, tfRiver, tfFormula, Gradient UV shader, sunlight rig, presets

- Source: INSYDIUM Fused Release Update — July 2023 - TerraformFX Sneak Peek — https://www.youtube.com/watch?v=aPMCwaeUtvc (2023-06-19) + live demo in INSYDIUM LIVE! July 2023 (2023-07-05)
- Host / generation: C4D; TerraformFX (height-field terrain generator), Fused 2023.3 — not particle-based
- Goal: overview of the new terrain design, animation and look-dev tools.

## New operators
- **tfTrace** — ray-traces scene geometry into the height field (skull → island). Rays shoot straight up from zero altitude, so **no overhangs** (lay a model on its side). Follow with a **Blur** (Box, fast) above the noise to smooth stepping; optional **Vertex Map** output for separate texturing.
- **tfRiver** (filter) — procedural rivers: from a user spline (**Settle Spline** in the live demo) or **Perlin Worm** (start/end points flow downhill; start defaults to the highest point). **Create River Material**; **Secondary Rivers** (default 5) and secondaries of secondaries; **Export Rivers** as live splines (e.g. for particles). Width, Depth, Deform/Wiggle/Smoothing, Altitude modes (Downhill Flow / Project, reverse flow), Render ▸ **Edge Noise** strength/scale for eroded banks.
- **tfFormula** — type or paste a formula for abstract animated landscapes; variables (e.g. project time) can be keyframed.

## Look-dev and viewport
- **Gradient UV shader** — 2D gradient with four colour inputs mapped to terrain U/V; feed shaders into inputs (noise in V, **Terrain Operator** shader set to **Altitude** in U, Remap curve) for rock/grass blends.
- **tfTerrain** sunlight rig: sun pitch/heading, shadows (enable viewport Shadows), ambient haze; becomes a reusable light rig when the terrain is made editable.
- **5 preset terrains**: Mountain, Valley, Island, Canyon, River.

## Notes
Later: Fused 2024.2 added the Advanced Terrain Shader, curvature channel, tfDistribute. In C4D 2024+ Redshift bakes TerraformFX shaders at 128×128 by default — raise it.
