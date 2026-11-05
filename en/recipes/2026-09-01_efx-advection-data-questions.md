# Particle flames from nxExplosiaFX advection data (temperature-driven kill & color)

- Source: Top Tip Tuesday — Advection Data — https://www.youtube.com/watch?v=1ERTCdQAoF0 (2026-09-01)
- Host / generation: C4D, Fused 2025.4+ (nxExplosiaFX GPU, nxQuestion)
- Goal: render only particles that ride a smoke/fire sim, colored and killed by the temperature they pick up from the grid.

## Scene tree
```
nxExplosiaFX (source: Torus)  — Dynamics ▸ Particle Advection: Emitters = xpEmitter, Mode Position
xpEmitter  (Object: same Torus, Polygon Area, Rate 50 000/s, speed 0, Full Lifespan)
  Display: Gradient (Parameter) = Temperature, Min 1000 / Max ~6100
nxQuestion
  If Age > 2 F  AND  Temperature < 1000  → Action: Kill
```

## Steps
1. Emit particles from the **same object** as the EFX source, speed 0 (they only move by advection). [▶ 0:44](https://youtu.be/1ERTCdQAoF0?t=44)
2. nxExplosiaFX → **Dynamics ▸ Particle Advection** → drop the emitter in. [▶ 1:27](https://youtu.be/1ERTCdQAoF0?t=87)
   - **Velocity** mode (default): fluid velocity is *added*; particles leaving the grid keep flying.
   - **Position** mode: particles follow the fluid exactly and stop at walls.
3. Advection also copies the voxel **smoke, temperature, fuel** values onto the particles. [▶ 3:42](https://youtu.be/1ERTCdQAoF0?t=222)
4. Find the useful temperature range from EFX Display: Flame Emit Above shows the flame threshold (here 1000) and raising it until flames vanish gives the max (~6100). [▶ 4:33](https://youtu.be/1ERTCdQAoF0?t=273)
5. Color: emitter Display → **Gradient (Parameter) → Temperature**, Min 1000 / Max 6100 (blue cool → white hot). [▶ 5:06](https://youtu.be/1ERTCdQAoF0?t=306)
6. Die with the flame instead of a fixed lifespan: **nxQuestion** — Question *Age > 2 frames* (buffer: newborn particles have 0 temperature) **AND** child Question *Temperature < 1000* → **Action Kill**. [▶ 7:31](https://youtu.be/1ERTCdQAoF0?t=451)
7. Faster dissipation in EFX (Simulation ▸ Dissipation ▸ Temperature) now shortens the particle flames automatically. [▶ 7:56](https://youtu.be/1ERTCdQAoF0?t=476)

## Notes
- You don't have to render the smoke at all — EFX is just a motion/data field here.
- Same idea works with Smoke and Fuel values (e.g. spawn soot particles where smoke is dense).
