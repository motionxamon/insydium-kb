# Trippy flat push patterns (nxPush + nxQuestion velocity lock + nxScale by field)

- Source: Top Tip Tuesday — NeXus Push Particles — https://www.youtube.com/watch?v=IuaZtmg5O8o (2024-04-09)
- Host / generation: C4D; NeXus GPU (nxPush, nxQuestion, nxScale, nxTurbulence) on an xpEmitter; C4D Random field
- Goal: particles on a plane pushing each other apart in 2D as their radii animate with noise.

## Base
Plane emitter (Object, polygon area), Rate 20, radius 6, speed 0. Display Circles, Gradient Parameter mapped to **Radius**.

## Steps
1. **nxPush**: Distance mode **Particle Radius**, Strength 100%.
2. Lock to the plane: **nxQuestion** with a direct **Action ▸ Set Velocity**, X/Y/Z = 0 (no question needed). Works on any plane aligned to 90° increments.
3. **nxScale**: operation **Set by Falloff**, clamping off; Fields ▸ **Random field** — yellow = radius 0, red = emitter max radius (6).
4. Random field: noise **Gaseous**, scale 500, add animation speed (raise further later). Remapping ▸ Contour **Curve** for a contrast curve. Hide the field display.
5. Display **Squares** at 100% so all particles draw the same size regardless of radius (reads better).
6. Rate 100 → 200, display Dots.
7. **nxTurbulence** placed **below** the nxQuestion: zero its **Y** component so the lock holds; type Curl, more strength/scale, lower frequency, reduce Blend.

## Gotchas
- Any extra force with a Y component breaks the 2D lock unless zeroed.
- Turning turbulence off gives a different "growing outward" push look.

## Newest equivalent
Same modifiers in NeXus 2026; nxFalloff (16 modes, incl. Noise) can replace the C4D field on nxScale.
