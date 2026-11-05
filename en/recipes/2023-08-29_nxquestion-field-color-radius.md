# Grow and recolor particles inside a field, revert outside (nxQuestion Field question, Set Color / Set Radius, Else)

- Source: Top Tip Tuesday — nxQuestion Fields — https://www.youtube.com/watch?v=c1-Os0yoIgg (2023-08-29)
- Host / generation: C4D; G2 NeXus nxQuestion (Fused 2023.3 redesign) on an xpEmitter; C4D Spherical field
- Goal: particles on a wolf-head surface swell and turn blue while a keyframed field passes over them, then shrink back.

## Base
Particles born on the head surface, radius **2 cm**.

## Steps
1. **nxQuestion** with only an **Action** (no question) = affects all particles at once. Default **Set Color** → blue.
2. Lower the action **Weight** for a gradual change over several frames instead of instant.
3. Ctrl-drag to copy the action, switch it to **Set Radius**, **20 cm**; it inherits the low weight (~4%) → gradual growth; 100% = instant.
4. Link the keyframed field on the nxQuestion **Fields** tab.
5. Add a **Question** and make both actions its children. Default is Age > 30 frames (actions fire from frame 30) → change data type to **Field**.
6. Field value runs 0–1: 1 inside the inner sphere, 0 outside the outer, falloff between. Default test **> 0.5** triggers only from mid-falloff inwards; **> 0** triggers as soon as a particle touches the outer sphere.
7. Revert: add a second Question **below** the first (evaluated in order), switch it from **If** to **Else**; copy the two actions under it: Set Color back to the original purple, Set Radius back to **2**.
8. Raise the Else Set Radius weight to shrink back faster (too high = abrupt).

## Newest equivalent
Identical logic in NeXus 2026.1 / Blender with an **nxFalloff** (16 modes) instead of C4D fields; for a pure falloff-driven look without logic, map Radius/Color from a falloff in the modifiers' Mapping tab or use **nxScale**/**nxColor** with per-layer Falloff lists. Quill (Blender) can draft such question trees.
