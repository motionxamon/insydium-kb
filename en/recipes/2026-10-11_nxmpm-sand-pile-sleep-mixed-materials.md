# Tall sand piles with auto-sleep, wake-on-collision and a brittle block (nxMPM Materials + Auto Sleep + display channels)

- Source: NeXus Official Training — nxMPM Sand pile — https://www.youtube.com/watch?v=UT9_Aht5waE (2026-10-11)
- Host / generation: C4D (cm), NeXus 2026.1 beta (G3); **nxEmitter** (not the old xpEmitter), nxMPM, nxGravity, nxCollider
- Goal: poured sand that builds a steep pile (settled grains sleep but still collide), a brittle block that smashes it, and a sphere that re-wakes everything.

## Steps
1. Use the new GPU **nxEmitter** from the NeXus menu — the old xpEmitter won't work with the new tools.
2. **nxMPM** (brings a domain); raise it +200 in Y to sit on the floor. Bounds are optional (MPM object ▸ **Use Bounds** off = sparse) but a domain is easier and lighter.
3. nxEmitter: Sphere, radius ~14–17, direction −Y, Rate, speed 30 cm; **Match Solver Resolution** → nxMPM. Add **nxGravity**; long timeline (8000 F).
4. MPM Display ▸ Draw Grid (Back) to judge voxels; Resolution **80** (good viewport speed); narrow the domain width/depth.
5. MPM ▸ **Materials** tab: drag the emitter in (renamed "sand") → type **Sand**, preset **Powder Fine**. Set **Momentum** 0 (useful for liquids, causes flying grains on dry materials).
6. MPM object ▸ Bounds ▸ Boundary Walls ▸ **Wall Friction** up to full → grains start piling.
7. Emitter tag **Vibrate**: position 50 cm X and Z, frequency 8 for a wandering stream.
8. Emitter Display: size 2. **Display channels**: channel 1 = gradient, parameter Random, preset Heat 3 (render color); add channel 2 for sim data.
9. MPM object: **Auto Sleep** on, **Sleep Speed** 10 cm/s (default 5); particles fade into sleep over ~7.5 frames. Sleeping particles still act as colliders for live ones → much taller piles.
10. MPM Display ▸ Particle Color = **Sleep State** → output to channel 2; view channel 2 in the emitter: green awake, red asleep.
11. **Wake Speed** 10.5 (just above Sleep Speed), Wake Spread 0. A sphere + **nxCollider** (bounce/friction 0) pushes grains awake; they re-settle and sleep again.
12. Second **nxEmitter** "brittle": Box 50×50×50, −Y, speed 30, Shot at ~F220, Match Solver Resolution → same MPM. Stop the sand emitter (Emit All Frames off, ~200 frames).
13. Materials tab: drag "brittle" in → **Brittle ▸ Concrete** (reads like the old SPH granular look). Display gradient by Granular, 0–10.
14. Both materials collide with each other and the collider, sleep and wake in one solve.

## Gotchas
- Preset names aren't literal: "Concrete" is just a good fracturing granular look.
- Wake Speed must sit above Sleep Speed or particles flicker between states.

## Newest equivalent
Already the newest route. Legacy: xpFluidFX / nxFluids SPH granular — no sleep state, so piles slump.
