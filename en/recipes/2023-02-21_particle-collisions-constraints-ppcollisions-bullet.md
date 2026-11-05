# Three ways to make particles collide with each other (xpConstraints Collisions, xpPPCollisions, xpBullet)

- Source: Top Tip Tuesday — xpCollisions — https://www.youtube.com/watch?v=GGI1MyewI2g (2023-02-21)
- Host / generation: C4D; CPU X-Particles dynamics + INSYDIUM Bullet tags
- Goal: pick the right particle-to-particle collision method for the shape and detail needed.

## Base
Particles falling under gravity onto ground with an **xpCollider** tag — they intersect each other.

## Steps
1. Quickest: Dynamics ▸ **xpConstraints** ▸ **Collisions** tab on. One setting — **Stiffness**. Fast, basic.
2. More control: Dynamics ▸ **xpPPCollisions**. Default already works; adds particle-particle **Bounce** (+ variation), **Friction** (stick after contact), **Scatter** (random bounce direction), plus spawn-on-collision and connect-on-collision options.
3. Limitation of both: collisions are **spherical** (radius based) — fine for sphere display; with **Box Filled** corners intersect and nothing rolls or tumbles.
4. Shape-accurate: remove xpCollider from the ground; Tags ▸ Extensions ▸ INSYDIUM Bullet ▸ **Bullet Collider** on the ground, **Bullet Rigid Body** tag on the emitter (defaults).
5. Bullet respects the display shape — boxes, **Pyramid**, even **Arrow Filled** — with rolling/bouncing; it has its own bounce/friction/scatter.

## Gotchas
Bullet uses its own collider tag; don't mix it with the xpCollider on the same ground.

## Newest equivalent
GPU spherical collisions: **nxConstraints Collisions layer** / nxPPCollisions / nxPush. Shape-accurate rigid particles have no GPU route yet (unified rigid bodies only announced Nov 2026) — keep xpBullet or C4D Rigid Body tags on xpGenerator geometry (recipe 2025-08-26).
