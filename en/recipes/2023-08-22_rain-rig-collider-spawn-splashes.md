# Splashing rain rig (xpCollider Spawn on collision, xpJoin for many colliders)

- Source: Top Tip Tuesday — xpRainRig — https://www.youtube.com/watch?v=x1SAOjOSOzs (2023-08-22)
- Host / generation: C4D; G1 CPU X-Particles (xpEmitter, xpGravity, xpCollider tag, xpJoin)
- Goal: line-drawn rain falling on a floor plus Kaiju and duck models, spawning short-lived splash particles on impact.

## Steps
1. **xpEmitter** rectangle, Emitter Plane **−Y**, scaled large and raised high. Emission Rate, Birth Rate **250**, variation **100**, Speed **0**. [▶ 0:55](https://youtu.be/x1SAOjOSOzs?t=55)
2. **xpGravity** (Motion modifiers), variation **150**; Visible in Editor off to hide the icon. [▶ 1:20](https://youtu.be/x1SAOjOSOzs?t=80)
3. Emitter Display: Editor display **Lines**, Color mode **Gradient Random** with two greys (dark → light, not white). [▶ 1:34](https://youtu.be/x1SAOjOSOzs?t=94)
4. Floor: **xpCollider** tag. Add bounce variation, a little friction with variation, and some **Scatter** for random rebound angles. [▶ 2:30](https://youtu.be/x1SAOjOSOzs?t=150)
5. Collider ▸ **Spawn** tab: enable; Ctrl-drag a copy of the rain emitter, rename it "spawn", drop it in. Born at the **collision point**, direction **face normal** plus some **Spread**; enable **kill the original** particle. [▶ 3:17](https://youtu.be/x1SAOjOSOzs?t=197)
6. Spawn emitter ▸ Emission: Speed **300**, variation **200** (else splashes just sit on the floor); untick full lifespan → Life **20** frames, variation **10**. Lighter greys in its display gradient. [▶ 4:00](https://youtu.be/x1SAOjOSOzs?t=240)
7. More splash: raise the collider's spawn count (e.g. **30**).
8. Several surfaces: Utilities ▸ **xpJoin**, eyedropper the Kaiju, duck and plane, then move the single xpCollider tag onto the xpJoin — one tag drives all. [▶ 5:19](https://youtu.be/x1SAOjOSOzs?t=319)

## Newest equivalent
NeXus 2026.1: **nxSpawn** layer **On Collision** (Burst, inherits direction) with an **nxCollider** object; in Fused 2025.x use an nxQuestion collision question with a Spawn action. Add **nxSplash** (Fused 2025.4) for crown splashes if rain falls into liquid.
