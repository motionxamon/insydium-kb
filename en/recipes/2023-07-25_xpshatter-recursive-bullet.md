# Recursive shattering on impact (xpShatter Voronoi layers with Collision trigger, Bullet rigid bodies)

- Source: Top Tip Tuesday — xpShatter Recursion — https://www.youtube.com/watch?v=oY_h7s9RyVI (2023-07-25)
- Host / generation: C4D; G1 CPU (xpShatter + INSYDIUM Bullet tags)
- Goal: a wolf model breaks into big chunks when it lands, and those chunks break again (and again) on later hits, fully procedural.

## Steps
1. Lift the model; select it and the floor plane ▸ Tags ▸ INSYDIUM Bullet ▸ **Rigid Body**. Floor tag ▸ Simulation ▸ mode **Collider**.
2. X-Particles Generators ▸ **xpShatter**; make the wolf its child, and **move the Bullet tag up to the xpShatter** → dynamic shards.
3. Display: untick **Draw Cut Edges**.
4. UVs: move the material to the xpShatter; Selections ▸ create a **polygon selection of outer faces**, drag that tag into the material's Selection field → outside keeps the UV map, inner faces get their own material.
5. First **Voronoi** layer's point generator: **40 → 12** points (fewer, bigger chunks).
6. Add Layer ▸ second **Voronoi** layer, point generator **10** points (each chunk can split into 10).
7. Its Trigger: Always → **Collision**; disable particle-particle and particle-polygon, keep **xpBullet collisions**. **Collision Speed 4**, variation **2** (3/2 broke too much; 5/3 kept many big pieces).
8. Third Voronoi layer: **10** points, trigger Collision (Bullet), speed **2**, variation **2** → a third tier of fragments.

## Newest equivalent
**nxShatter** (NeXus 2026.1 beta, GPU): Voronoi/Glass/Wood/Bricks with sub-fracture and triggers, driven by an emitter or by nxMPM damage. Stable Fused 2025.4: xpShatter + Bullet as shown. Note the GPU rigid-body dynamics are only announced (next beta), so collisions here still need Bullet.
