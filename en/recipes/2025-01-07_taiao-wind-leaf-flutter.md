# Wind on animated Taiao plants — per-leaf forces vs faked flutter (Taiao Plant Forces tab)

- Source: Top Tip Tuesday — Taiao Animated Wind — https://www.youtube.com/watch?v=LxuCKvd1b5g (2025-01-07)
- Host / generation: C4D; Taiao (taPlant) only — no particles
- Goal: realistic swaying trunk/branches plus fluttering leaves, cheaply.

## Base
Taiao plant: trunk, four branch layers, basic leaf layer. **Forces** tab enabled with defaults already animates the branches.

## Steps
1. Forces ▸ global **Wind Strength ~150**; global turbulence adds independent sway on top.
2. Each plant layer has its own Strength, Frequency, Turbulent Frequency and a **Layer Weight** curve (zero force at the thick base, more toward the tip).
3. Hero option: leaf layer ▸ enable **individual per-leaf forces** → unlocks Wind Bend Strength (bend leaves along the wind) and Curl options (per-leaf animated deformation).
4. Cheap fake (keep multi-instances): turn per-leaf forces off; leaf Strength/Frequency to 0.
5. Plant Layers ▸ Leaf ▸ **Orientation**: angle near 100% so leaves point downwind, add Twist with heavy variation and some Angle variation.
6. Back in Forces, leaf **Strength ~25, Frequency 100**; raise global turbulence for sway.
7. For frantic flutter push leaf Frequency to **500** (up to **800** for a gale) and pull global turbulence back if it gets messy; tame branches in their own layer options if needed.

## Gotchas
Per-leaf forces disable multi-instances (every leaf becomes its own object) → slow; reserve for hero trees.
