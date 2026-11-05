# Firework sparks off hand-drawn text (nxScale + nxQuestion kill + nxSpeed clamp mapped to Radius)

- Source: Top Tip Tuesday — Particle Sparks — https://www.youtube.com/watch?v=PYtRwy_bbCE (2024-12-31)
- Host / generation: C4D; NeXus G2 (nxGravity, nxScale, nxQuestion, nxSpeed, nxTurbulence) on an xpEmitter + CPU xpSplineGrowth utility; additive material + motion blur for the render
- Goal: hot sparks that shed off a written "Happy New Year", shrink, slow down by size and die.

## Base
- Text spline as a guide; in the front ortho view (F5) trace it with the **Sketch** spline tool (one spline object, loose strokes are fine).
- **xpEmitter ▸ Object** mode, the sketched spline, emit from **Edges**; Rate 1000/s, Speed 100 (var 50), Radius 2 (var 1).
- Display Circle + Gradient by Parameter ← Radius (auto): big = white, small = orange.

## Steps
1. **nxGravity** so particles fall.
2. **nxScale** below gravity: negative change over time (Min −0.2, lots of variation), **Clamp Limit off** → sparks shrink to nothing. [▶ 2:52](https://youtu.be/PYtRwy_bbCE?t=172)
3. **nxQuestion**: if particle **Radius = 0** → Action **Kill** (replace the default Set Color). [▶ 3:32](https://youtu.be/PYtRwy_bbCE?t=212)
4. **nxSpeed** last in the stack: Operation Acceleration with value **0**, enable **Clamp Max Speed** ~400 cm. [▶ 4:22](https://youtu.be/PYtRwy_bbCE?t=262)
5. nxSpeed ▸ **Mapping ▸ Radius map** (range 0–3 cm) → parameter **Clamp Max Speed**; small sparks get a lower speed cap. Lift the curve's low end so they never fully stop. [▶ 5:16](https://youtu.be/PYtRwy_bbCE?t=316)
6. Raise emission (~50,000), switch display to **Lines** (stretch with speed) for a spark look. [▶ 6:22](https://youtu.be/PYtRwy_bbCE?t=382)
7. **nxTurbulence** placed *above* nxSpeed (so the clamp wins): Curl, strong, low persistence, higher octaves → big wavy swirls. Speed cap up to ~500. [▶ 6:34](https://youtu.be/PYtRwy_bbCE?t=394)
8. Write-on/wipe-off: **xpSplineGrowth** as child of the spline; key 0% F0 → 100% F60, hold to F100, back to 0% F160. [▶ 7:37](https://youtu.be/PYtRwy_bbCE?t=457)

## Gotchas
- Order matters: gravity → scale → turbulence → speed clamp last.
- The clamp parameter in Mapping is "Clamp Max Speed", not the exponential value next to it.

## Newest equivalent
Same stack with G3 objects (nxEmitter + modifiers; **nxConvert** in the 2026.1 beta). Note the 2026.1 Beta 3 rename: nxSpeed's layer is now **Acceleration**.
