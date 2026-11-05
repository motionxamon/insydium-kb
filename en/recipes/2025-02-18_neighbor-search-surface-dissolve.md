# Peel-away volume disintegration (nxQuestion Neighbor Count → Group → nxWind/nxColor)

- Source: Top Tip Tuesday — Surface Particle Dissolve — https://www.youtube.com/watch?v=35Yxc9a2QOU (2025-02-18)
- Host / generation: C4D; NeXus G2 nxQuestion (neighbour search), nxWind, nxColor on an xpEmitter
- Goal: a particle-filled model that erodes layer by layer from its outer surface.

## Base
xpEmitter ▸ Object (balloon dog) ▸ **Volume**; Emission Shot **500,000**, full lifespan, Speed 0, Radius 1. Hide the model.

## Steps
1. Groups: Ctrl-click **Add Group** twice, **First Group Only**.
2. **nxWind** and **nxColor** (direction-based color) ▸ Groups Affected = **group 2** — nothing happens yet.
3. **nxQuestion**: Particle **Neighbors** within **10 cm** **less than 70** → test with Set Color yellow; only the outer shell lights up (surface particles have fewer neighbours).
4. Raise the threshold (80, 100) for a thicker shell; 100 used.
5. Swap the action to **Set Group = group 2**; enable wind + color.
6. The question re-evaluates every frame, so each newly exposed layer becomes "surface" and blows away until the object is gone.
7. Speed control: lower threshold (70) = thinner shell = slower erosion.

## Gotchas
Neighbour threshold depends on radius/density — guess, preview with a color action, then switch to the group action.
