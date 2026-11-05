# Feature notes: redesigned nxQuestion and NeXus Data Mapping (Fused 2023.3)

- Source: INSYDIUM Fused Release Update — July 2023 - NeXus Control Sneak Peek — https://www.youtube.com/watch?v=_imkCRS1vqI (2023-07-03)
- Host / generation: C4D; G2 NeXus inside X-Particles (GPU, Vulkan) — Fused 2023.3 (5 Jul 2023)
- Goal: trigger effects from particle/scene data with a GPU logic hierarchy, and map any modifier parameter to particle data.

## nxQuestion — object-hierarchy logic
- Questions and Actions are layers in one **nxQuestion** object; Actions sit as children of the Question they answer. Example: **Age = 30 F** → **Set Radius 10 cm**; switch the data to **Distance Traveled 150 cm** for a distance trigger.
- Actions have a **Weight** (blend toward the value over time instead of snapping) and a **Delay**; questions/actions stack without limit.
- C4D **Fields** can be used as a question source; **Object Volume** question restricts effects to inside a mesh (recursive spawning kept inside letters).
- **Loop** layer, e.g. **Time Cycle** with Position + Velocity on → particles return to their start positions.
- Fast GPU **neighbour search** drives recursive spawning growth.
- **Script** layer: custom GLSL (Vulkan) code. INSYDIUM provides a pre-prompt so ChatGPT can write scripts (demo: colour over time + radius 3 → 40); paste into an empty nxQuestion Script layer.
- **Variable** layers in **User Data** mode → build a custom UI in C4D User Data → effectively a custom GPU modifier (flock-in-groups example with 4 variables).

## Data Mapping (new Mapping tab on every modifier and dynamic modifier)
- Add map layers: source (Age, Color, Distance…) → parameter, shaped by a curve. Example: **nxGravity** Color map → gravity Strength, lighter particles get full pull.
- Layers stack: **nxWind** with Color Brightness → wind Strength plus a **Distance** map → Turbulence (full after **150 cm** travelled).
- Dynamics too: **nxFluids SPH** Age map, category SPH ▸ **Viscosity** 0 at 0.5 s → full at 0.6 s; duplicate for **Surface Tension**.

## Replaces
CPU xpQuestion/xpAction and the CPU Data Mapping on xp modifiers for GPU emitters. Today: nxQuestion is still the logic system (2026.1 adds Quill AI in Blender, Sleep/Bind); Mapping now supports one layer → many targets and looping (2025.4).
