# Reading the Data Mapping curve: radius by age and by group (nxScale ▸ Mapping)

- Source: Bite-Sized — NeXus Data Mapping — https://www.youtube.com/watch?v=AMCR5ciL7fw (2025-04-24)
- Host / generation: C4D; xpEmitter + NeXus GPU nxScale (Mapping tab works the same in other nx modifiers/dynamics and in X-Particles)
- Goal: understand range (X) vs parameter multiplier (Y) by growing particles with age and sizing them per group.

## Base
xpEmitter **Shot ▸ Hexagonal**, static particles; three xpGroups, emitter Groups tab uses all three in **Random** mode (colors show the group).

## Steps
1. **nxScale** ▸ Object: **Set Value**, Radius **60 cm**.
2. Mapping ▸ add **Age** layer; Parameter = **Radius Value** (Map To is Age automatically).
3. Read the graph: **X axis = range** (Range Min 0 F → X 0, Range Max 30 F → X 1); **Y axis = multiplier of the set value** (Y 0 → 0 cm, Y 1 → 60 cm). After the max age they keep 60 cm.
4. Range Max **100** → slower growth. Right-click ▸ Spline Presets ▸ **Linear**, Ctrl-click a knot at X 0.5 / Y 0.5 → at 50 frames old the radius is 30 cm.
5. Cubic preset = slow start then fast growth; an inverted curve = born full size, shrinking to 0 at 100 F.
6. Per group: delete the Age layer, add a **Group** layer, same parameter. **Range Min 1, Range Max 3** (there is no group 0 here) → group 1 at X 0, group 2 at X 0.5, group 3 at X 1.
7. Groups are integers, so only the knot values at those exact X positions count; curve shape between knots is irrelevant. E.g. Y 0 / 0.5 / 1 → 0 / 30 / 60 cm; nudge each knot to size each group.

## Newest equivalent
Fused 2025.4 adds Data Mapping with looping; NeXus 2026.1 Mapping lets one layer drive many targets, and every modifier layer also has its own falloff list.
