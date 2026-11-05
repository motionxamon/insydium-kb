# Particles → C4D rigid bodies, colored by nxColor (xpGenerator + Simulation tags + Redshift Object Color)

- Source: Top Tip Tuesday — Particle Rigid Bodies — https://www.youtube.com/watch?v=eBnMW0v43Ac (2025-08-26)
- Host / generation: C4D; NeXus emitters + **CPU xpGenerator** + C4D **Rigid Body / Collider** simulation tags + Redshift
- Goal: accurate object-object collisions (skulls in a box) using C4D's solver, while NeXus still drives the color.

## Steps
1. Start from a NeXus scene; **disable nxGravity and nxConstraints** and the xpCollider on the box — C4D's solver takes over physics. [▶ 0:51](https://youtu.be/eBnMW0v43Ac?t=51)
2. XP System ▸ Generators ▸ **xpGenerator** per emitter (rename "generator main", "generator lights"); the geometry to copy is a **child** of the generator. [▶ 1:30](https://youtu.be/eBnMW0v43Ac?t=90)
3. On each generator: **Tags ▸ Simulation ▸ Rigid Body**. On the box: **Collider Body**, Collider ▸ **Back** side (traps objects inside). [▶ 2:30](https://youtu.be/eBnMW0v43Ac?t=150)
4. Particles become rigid bodies at birth (emitter speed is ignored, C4D gravity applies). Late emitter (frame 150) adds more. [▶ 2:45](https://youtu.be/eBnMW0v43Ac?t=165)
5. Small objects too light to push big ones → Rigid Body ▸ Mass ▸ **Density ~15**. [▶ 4:42](https://youtu.be/eBnMW0v43Ac?t=282)
6. Color: **nxColor** layers → *Gradient by Parameter* mapped to **Random** (random color per particle) + a top layer black→white mapped to **Age** in **Multiply** blend → objects are born black and fade to their random color. Color passes into the generated objects. [▶ 8:56](https://youtu.be/eBnMW0v43Ac?t=536)
7. Redshift: in the material, Ctrl-click the Subsurface Color (or Base) port → **Color User Data** node ▸ preset **Object ▸ Object Color** (not Particle Color — this is geometry). [▶ 8:11](https://youtu.be/eBnMW0v43Ac?t=491)

## Gotchas
- Pause in playback when new objects spawn (solver rebuild).
- Use Object Color, not Particle Color, for xpGenerator geometry.

## Newest equivalent
The next NeXus beta (announced 2026-11-03) adds native **unified rigid bodies** with two-way coupling; until then this C4D-solver bridge is the accurate way. See whats-new.md.
