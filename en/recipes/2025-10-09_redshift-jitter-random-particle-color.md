# Random per-particle color on a cached sim (Redshift Jitter node + Particle ID user data)

- Source: Bite-Sized — Redshift Particle Jitter — https://www.youtube.com/watch?v=Dsouu1awIWc (2025-10-09)
- Host / generation: C4D + **Redshift**; cached X-Particles sim (particle-to-particle collisions in a cube); works with NeXus particles too
- Goal: give every particle a random color from a chosen palette at render time, without re-simulating.

## Base
Emitter has a **Redshift Object tag** ▸ Particles ▸ **Sphere Instances**. New Redshift Standard material on the emitter.

## Steps
1. Node editor: add a **Color Ramp**, load a pastel preset. Alone it maps the same gradient onto every sphere — not wanted. [▶ 2:28](https://youtu.be/Dsouu1awIWc?t=148)
2. Add a **Jitter** node: Hue variation off, Saturation variation 0, keep **Value** min 0 / max 1 (random black→white). [▶ 3:09](https://youtu.be/Dsouu1awIWc?t=189)
3. Jitter ▸ **Input ID mode: Name ID → User Data ID** (otherwise all particles get the same value). [▶ 4:12](https://youtu.be/Dsouu1awIWc?t=252)
4. Add a **User Data — Integer** node, preset attribute **Particles ▸ Particle ID**; wire it into the Jitter's user-data input. Solo the Jitter: random grey per particle. [▶ 5:00](https://youtu.be/Dsouu1awIWc?t=300)
5. Jitter color → **Alt input** of the Color Ramp; ramp → material Base Color. Each particle now picks a random point on the gradient. Switch ramp knots from Step to **Smooth** for more in-between hues. [▶ 5:29](https://youtu.be/Dsouu1awIWc?t=329)
6. Bias the palette: insert a **Scalar Ramp** between Jitter and Color Ramp; add a contrast-style curve so most values are dark → mostly blue/green, only a few pinks. [▶ 7:28](https://youtu.be/Dsouu1awIWc?t=448)

## Gotchas
- With User Data the ID must come from the particle attribute; Name ID mode gives no variation on a single emitter.
