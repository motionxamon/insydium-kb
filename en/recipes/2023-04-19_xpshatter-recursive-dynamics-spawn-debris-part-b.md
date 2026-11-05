# Logo shatters on time, re-shatters on impact, spawns debris and dust (xpShatter layers + xpDynamics Push + collider Spawn + xpMultiSpawn)

- Source: INSYDIUM LIVE! — April 2023 - X-Particles, NeXus & MeshTools — https://www.youtube.com/watch?v=U8zISIlBq90 (2023-04-19)
- Host / generation: C4D; G1 CPU (xpShatter, xpDynamics, xpCollider, xpDrag, xpMultiSpawn)
- Goal: an extruded logo breaks at frame 30, a keyframed cube smashing through breaks the shards again, and impacts spawn chunks plus finer dust.

## Base
Logo spline in an Extrude (fully procedural). Pre-keyframed **Cube** that passes through the logo (hidden at first). Two materials: dark inside, candy outside.

## Steps
1. **xpSystem**, delete the default emitter. Generators ▸ **xpShatter**, logo as child. Display: edge color near black. [▶ 21:34](https://youtu.be/U8zISIlBq90?t=1294)
2. Object tab: layer stack **Voronoi** + Point Generator (40 points) → **13** points, cycle Seed. [▶ 22:18](https://youtu.be/U8zISIlBq90?t=1338)
3. General tab ▸ Emitter ▸ **Add** → "emitter shatter": one particle per shard, radius sized to the shard (see with Display **Circles**). Any modifier on these particles moves the shards. [▶ 24:31](https://youtu.be/U8zISIlBq90?t=1471)
4. xpShatter ▸ Tags ▸ **xpDynamics** → particle dynamics on every vertex. Enable **Push**, Strength **max** → shards push each other apart. Accuracy: Distribution **Vertices + polygon midpoints**, Surface or Volume (slower). Chosen over Bullet so X-Particles modifiers and spawning work on the same particles; it runs near real-time. [▶ 28:39](https://youtu.be/U8zISIlBq90?t=1719)
5. Materials: black on the xpShatter first, candy second; Selections tab ▸ create **outer faces** polygon selection → into the candy material's Selection. [▶ 29:30](https://youtu.be/U8zISIlBq90?t=1770)
6. Dynamics tag ▸ Properties: add an emitter ("emitter dynamics") for more control; set the radius in the tag (it updates the emitter). [▶ 30:14](https://youtu.be/U8zISIlBq90?t=1814)
7. First Voronoi layer ▸ Trigger **Time = 30 F**. [▶ 34:07](https://youtu.be/U8zISIlBq90?t=2047)
8. Add a second **Voronoi** layer, **11** points, Trigger **Collision**: particle-particle off, Bullet off, **particle-polygon on**. [▶ 33:21](https://youtu.be/U8zISIlBq90?t=2001)
9. Cube ▸ **xpCollider** tag with **Bounce on Collision off** — it registers hits without shoving shards. [▶ 32:36](https://youtu.be/U8zISIlBq90?t=1956)
10. Collider tag ▸ **Spawn** tab: enable, add spawning emitter (into the system). At collision point, Direction **Source Particle** + spread, Speed **Relative**, Number **1**, spawn **once** per particle. Spawning emitter Speed **0**. [▶ 37:18](https://youtu.be/U8zISIlBq90?t=2238)
11. **xpDrag**, Density **Water** (also calms the shards). [▶ 38:12](https://youtu.be/U8zISIlBq90?t=2292)
12. Generate ▸ **xpMultiSpawn**; exclude it from the shatter and dynamics emitters (drag the modifier into their modifier exclusion list). [▶ 39:29](https://youtu.be/U8zISIlBq90?t=2369)
13. Spawning emitter ▸ Groups: Ctrl+Alt-click Create Group twice; mode **Use First Group Only** (group 1). xpMultiSpawn layer → **group 2**, Count **3**, at age 0 for 1 frame, Direction relative with lots of spread, Speed **inherit source**. Group 2 display **Dots**; radius variation on both groups so drag separates them. [▶ 41:09](https://youtu.be/U8zISIlBq90?t=2469)
14. Dark Sky, camera Physical with low f-stop for shallow DOF. A 200 F cache was quoted at about 3–4 min. [▶ 42:32](https://youtu.be/U8zISIlBq90?t=2552)

## Gotchas
- A Voronoi layer left on Trigger **Always** shatters immediately — set Time/Collision first.
- Intersecting shards = too few dynamic particles; raise Distribution.
- xpShatter caches fine with xpCache.

## Newest equivalent
**nxShatter** (NeXus 2026.1 beta, GPU): Voronoi/Glass/Wood/Bricks with sub-fracture and triggers; tiered debris via **nxSpawn** (On Collision, 8 sub-layers). GPU rigid bodies are only announced, so in stable Fused 2025.4 keep xpShatter with xpDynamics/Bullet as shown.
