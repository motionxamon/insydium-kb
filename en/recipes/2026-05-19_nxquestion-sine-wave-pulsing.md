# Pulsing particle speed / size with nxQuestion Math ▸ Wave

- Source: Top Tip Tuesday — Sine Wave Action — https://www.youtube.com/watch?v=XiexaAsk03g (2026-05-19)
- Host / generation: NeXus (nxQuestion, nxTurbulence curl, nxPush, nxAttract) — C4D & Blender
- Goal: repeating on/off animation of any particle property (speed, radius, color).

## How Wave works
Math ▸ **Wave** = sine from **−100 to +100**, X = particle life or document time; one cycle per second at Frequency 1 (2 = faster, 0.5 = 2 s per cycle). Born at 0, rises to 100, down to −100, back.

## Speed pulse (trails)
- Curl nxTurbulence (direction only) + trails.
- `If Wave > 0 → Set Speed 68–100` / `Else → Set Speed 0`.
- Action **Weight < 100%** (~45%) → accelerate/brake smoothly instead of snapping; lower weight on the stop action = longer braking.
- Variation on Set Speed; **variation on the Wave comparison** (e.g. ±30) → particles out of sync.

## Size pulse (shot of static spheres)
- Emitter radius 0; `If Wave (freq 0.5) > 0 → Set Radius 59 ±53` / `Else → Set Radius 2–3`, weights < 100%.
- **nxPush** (Particle Radius mode, full strength) *below* the question → grown spheres push apart; **nxAttract** pulls them back when small.
- **Delay + Damping** on Set Radius → springy overshoot.

## Related
- Stop/start the loop: "Action Break" recipe. Repeat Range layers on each pulse: "Advanced Spin Control" (age reset).
