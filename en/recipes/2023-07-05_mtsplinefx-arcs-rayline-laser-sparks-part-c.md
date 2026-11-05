# Electric arcs, cables and laser burn sparks (mtSplineFX + mtRayline + nxQuestion Spawn)

- Source: INSYDIUM LIVE! — July 2023 – NeXus, Taiao, TerraformFX & MeshTools — https://www.youtube.com/watch?v=6WjDq_87uck (2023-07-05)
- Host / generation: C4D; MeshTools **mtSplineFX** and **mtRayline** (new in Fused 2023.3) + G2 NeXus (nxQuestion, nxGravity) on xpEmitters
- Goal: lightning arcing between flashing particles with sparks and grounded forks; procedural cables; lasers that spawn sparks where they touch a model.

## A — Arcs between particles (mtSplineFX)
1. Torus with a Vibrate tag; **emitter A** on the torus, **emitter B** on the ground plane (particles flashing on/off).
2. **mtSplineFX** ▸ Objects: Start = emitter A, End = emitter B. Connection type **Points** (default **Origin** only works for objects, not particles).
3. Spline tab **Points 100** (detail). Motion: raise the **large noise** scale, then add **small noise** for fine jitter. Display tweak; white core arc.
4. Sparks: **nxQuestion** placed only in emitter B's modifier list (excludes emitter A): **Age > 0** → **Spawn**, Inherit Parent off, higher count. **nxGravity** ~150 with 20 variation. Spawn emitter: Lines display, Heat gradient, Life **15** F, variation **10**.
5. Grounded forks: Sphere cloned by **xpGenerator** on emitter B (Scale = Source), combined into one object (caption: "XP join"); hide it. mtSplineFX ▸ Connections ▸ add **Fork** layer (count, length, angle, distribution like Taiao), count **2**, Connect To **Custom Object** = that combined geometry.
6. Enable the question on emitter A too for sparks at both ends.

## B — Cables
Cylinder → cylinder connections chained (1→2→3), connection type **Surface**, amount as needed; turn all Motion deformation off, enable **Gravity** with some variation → live hanging cables.

## C — Laser contact sparks (mtRayline)
1. **mtRayline** ▸ Object tab: add colliders (wolf, floor). Rays bounce until Ray Length runs out (default **500**). Enable **Single Shot** (one contact, no bounce).
2. Keyframe **Angle** 0 → **46** (mid-scene) → back so the beams sweep the head and floor. Display: points off, laser gradient.
3. Points tab: contact points ▸ **add emitter** ("emitter contact"), display None.
4. **nxQuestion**: **Emitter** question = emitter contact (isolates the effect when several emitters exist) → **Spawn**, Inherit Parent off, Velocity Random, Speed **64** (lowered afterwards), Radius **1**, count **20**, Distance **1**. nxGravity; spawn display Dots, white→black Age gradient. Lower wolf collider friction.
5. Stays procedural: move/animate mtRayline (e.g. parent to an animated null) and the sparks follow.

## Newest equivalent
mtSplineFX and mtRayline are still the MeshTools tools (see recipes "mtSplineFX Lightning", "mtRayline Particle Lasers"). For the spark spawning, 2026.1 beta **nxSpawn** replaces the nxQuestion Spawn action.
