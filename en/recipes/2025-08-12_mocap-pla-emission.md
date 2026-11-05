# Clean particle emission from a mocap character (xpJoin → Alembic → PLA bake)

- Source: Top Tip Tuesday — X-Particles and Mocap — https://www.youtube.com/watch?v=Qd_kEHZ-4JY (2025-08-12)
- Host / generation: C4D (Maxon asset-browser mocap + character solver) + X-Particles emitter / xpTrail (works the same for nxEmitter)
- Goal: particles locked to a skinned mocap character without the one-frame lag.

## Steps
1. Asset Browser ▸ Motion Capture: mocap clip (e.g. "Fireball") + matching puppet model; on the puppet's **Character Solver** tag set Source = the clip's **Character Definition** tag. [▶ 0:40](https://youtu.be/Qd_kEHZ-4JY?t=40)
2. Alt + **xpJoin** over the mesh null → body parts become one object. [▶ 1:24](https://youtu.be/Qd_kEHZ-4JY?t=84)
3. Emitting directly from the skinned / joined object **lags one frame** (C4D order of operations — can't fix in place). [▶ 2:51](https://youtu.be/Qd_kEHZ-4JY?t=171)
4. Fix: right-click xpJoin ▸ **Bake as Alembic** → still a generator, still lags → drag into the Timeline Dope Sheet ▸ Functions ▸ **Bake Objects** with **Create Copy + PLA** → polygon object with point-level animation. [▶ 4:30](https://youtu.be/Qd_kEHZ-4JY?t=270)
5. Emitter: Object mode, **Polygon Area**, **Stick Particles to Source**, Shot ~3000 → rock-solid. [▶ 6:08](https://youtu.be/Qd_kEHZ-4JY?t=368)
6. Baked mesh keeps separate parts → select hands in polygon mode ▸ Set Selection → feed the **polygon selection tag** to the emitter → emit only from hands. [▶ 5:55](https://youtu.be/Qd_kEHZ-4JY?t=355)
7. Example effect: emission 25/frame + **xpTrail** (length 25, variation 12) → light trails following the moves. [▶ 6:23](https://youtu.be/Qd_kEHZ-4JY?t=383)

## Gotchas
Keep the Alembic / original as backup in production; PLA files are heavy.

## See also
"Mocap Sim Proxy" (2026) for using a proxy for sims.
