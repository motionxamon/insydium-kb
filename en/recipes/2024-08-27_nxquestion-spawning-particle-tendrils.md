# Field-triggered self-growing tendrils (nxQuestion Variable + Spawn + Set Age/Life, nxPush by radius)

- Source: Top Tip Tuesday — Spawning Particle Tendrils — https://www.youtube.com/watch?v=LB-aA-N-2b0 (2024-08-27)
- Host / generation: C4D; NeXus G2 (**nxQuestion**, nxPush) on xpEmitters; C4D Spherical Field; xpCollider on the source sphere
- Goal: wherever a field passes over a particle-covered sphere, non-intersecting tendrils grow out for a set time.

## Steps
1. Parent particles emitted from a primitive sphere (sphere has an xpCollider tag).
2. **nxQuestion ▸ Variable** layer: Integer, Writable, Particle variable, name **spawn**, value 0.
3. nxQuestion Field tab: add a **Spherical Field**, place/scale it over part of the sphere.
4. Question (below the variable): Particle ▸ **Field > 0** → Action **Set Variable** spawn = 1.
5. Second Question: **Math ▸ Variable** "spawn" **= 1** → test with Set Color (yellow), then swap to **Spawn** action: 1 particle, within ~**0.3 cm**, new spawn emitter (placed above), Inherit off, full lifespan, speed 0, radius **3**.
6. **nxPush** placed **below** the nxQuestion (order changes the look), Distance mode **Particle Radius**, Strength **100 %** → no initial blow-apart, tendrils extrude.
7. Kill stragglers: **Neighbor Search** question — fewer than **2** neighbours within **5 cm** → **Set Speed 0**.
8. Limit growth per tendril: on the spawn = 1 question, after Spawn add **Set Age 0 (once)** and **Set Life 90 (once)** on the parent — only triggered parents die after 90 F, others stay available for new tendrils.

## Gotchas
- Don't give the parent emitter a 90 F lifespan — then every parent dies and no new tendrils can start.

## Newest equivalent
2026.1 Beta 3 **nxSpawn** (On Age / Rate etc.) can replace the Spawn action; **nxDendrite** covers branching growth; nxFalloff replaces the C4D field.
