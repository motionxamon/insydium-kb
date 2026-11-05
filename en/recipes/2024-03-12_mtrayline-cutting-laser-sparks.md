# Cutting laser with sparks (mtRayline contact-point emitter + xpTrail + xpSpawn)

- Source: Top Tip Tuesday — mtRayline Lasers — https://www.youtube.com/watch?v=PpDwpKu8478 (2024-03-12)
- Host / generation: C4D; MeshTools **mtRayline** + **CPU** X-Particles (xpEmitter, xpTrail, xpSpawn, xpGravity)
- Goal: animated laser rays scorching a trail on the floor and throwing white-hot sparks where they hit.

## Base
Floor plane; a null animated on Z position and Heading.

## Steps
1. **mtRayline** (default) ▸ Object tab: add the floor to the collision geometry. Rays bounce until **Max Length** (500 cm default); switch to **Single Shot** so each ray ends at the first hit and leaves a contact point. [▶ 1:04](https://youtu.be/PpDwpKu8478?t=64)
2. Rotate it to aim down and parent it to the animated null.
3. Display: gradient display off, contact/start points hidden; Basic colour orange. [▶ 1:53](https://youtu.be/PpDwpKu8478?t=113)
4. **Points tab ▸ Contact Points ▸ Add Emitter** → "emitter contact" gets a particle at each hit. [▶ 2:07](https://youtu.be/PpDwpKu8478?t=127)
5. **xpTrail** with the contact emitter, colour orange → the burnt cutting path. [▶ 3:06](https://youtu.be/PpDwpKu8478?t=186)
6. **xpSpawn** ▸ Add Emitter ("emitter spawn"); spawn at source particle position, Direction **Random Spherical**, spawned speed **Absolute** (taken from the new emitter). Spawn emitter speed **100** (var 80); spawn rate **75** per frame (var 15) instead of 300. [▶ 3:59](https://youtu.be/PpDwpKu8478?t=239)
7. **xpGravity** (default) pulls the sparks down.
8. Spawn emitter display: **Lines**, Color Mode **Gradient Parameter** mapped to **Age**: near-white at birth → rich orange soon after → fade to black (cooling metal). [▶ 4:50](https://youtu.be/PpDwpKu8478?t=290)

## Newest equivalent
NeXus 2026.1: **nxSpawn** (Instant / At Age / On Collision / On Death, Rate/Burst/Pulse) for the sparks, nxGravity and **nxTrail** on a NeXus emitter; nxColor Gradient by Parameter for the age colouring. See also "mtRayline particle lasers" (2024-04-23).
