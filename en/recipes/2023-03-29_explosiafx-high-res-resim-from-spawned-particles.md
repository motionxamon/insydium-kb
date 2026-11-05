# Higher-res fire re-sim from spawned fuel particles (xpSpawn on infected groups, cache Include, finer xpExplosiaFX voxels)

- Source: Maintenance Training - XP Countdown - Series 3 — xpExplosiaFX High Detail — https://www.youtube.com/watch?v=xoJcz9u3c8g (2023-03-29)
- Host / generation: C4D; CPU X-Particles (xpClothFX tearing, xpInfectio, xpPhysical, xpSpawn, xpExplosiaFX, xpCache); Cycles 4D preview
- Goal: keep the existing low-res xpExplosiaFX sim (it advects the tearing cloth) but render a far more detailed fire from many smaller fuel particles.

## Base
Previous "Countdown 5 Burn" scene: xpClothFX cloth emitter; xpInfectio spreads infected/incubated groups up the cloth; xpPhysical gives those groups fuel; cached xpExplosiaFX advects the cloth. Save as a new "HQ" version + cache folder.

## Steps
1. Disable the cloth emitter's cache tag. **xpSpawn** (Generate) ▸ Add spawning emitter → "Emitter Spawn"; position = **Source Particle**, speed **Absolute** with emitter speed **0** (they're moved by advection only). [▶ 3:28](https://youtu.be/xoJcz9u3c8g?t=208)
2. Emitter Spawn ▸ Modifiers tab: **exclude xpInfectio** (it would wreck the infection setup). [▶ 4:07](https://youtu.be/xoJcz9u3c8g?t=247)
3. **xpPhysical** ▸ Groups Affected: clear the infected/incubated entries so spawned particles also get fuel. [▶ 4:49](https://youtu.be/xoJcz9u3c8g?t=289)
4. xpSpawn: rate **10 per frame** (default 300/s is too many), **Spawn Once Only**, life Absolute → emitter life **15 F, variation 5**; **Groups Affected** = incubated + infected (spawn only where the burn is). **Offset 2–3 cm** so the 10 spawns don't sit on top of each other. Spawned **Radius 1.5**. [▶ 6:29](https://youtu.be/xoJcz9u3c8g?t=389)
5. Speed-up: hide the cloth and switch off the cloth modifier — the cached advection still moves the spawns identically. [▶ 7:54](https://youtu.be/xoJcz9u3c8g?t=474)
6. New **xpCache**, Inclusion **Include** = Emitter Spawn only; path in the HQ cache folder; Build (fast). [▶ 10:19](https://youtu.be/xoJcz9u3c8g?t=619)
7. New scene: copy Emitter Spawn + its cache tag (**Copy Tag Data**), the cache object and xpExplosiaFX (right domain size); delete the old xpExplosiaFX cache tag. [▶ 12:51](https://youtu.be/xoJcz9u3c8g?t=771)
8. xpExplosiaFX: **Voxel Size 1** (finer), **Advection off**. Add an **xpExplosiaFX Source** tag to Emitter Spawn — cached fuel values ignite immediately; hide the particles. [▶ 13:44](https://youtu.be/xoJcz9u3c8g?t=824)
9. Check against the cloth (paste its cache with Copy Tag Data); stray cloth is masked later with PolyFX. [▶ 15:49](https://youtu.be/xoJcz9u3c8g?t=949)
10. Cycles 4D volume material (standard xpExplosiaFX fire/smoke) on xpExplosiaFX, real-time preview. [▶ 17:29](https://youtu.be/xoJcz9u3c8g?t=1049)
11. Cache xpExplosiaFX: same cache object, Inclusion = xpExplosiaFX only; spawn cache tag override **Hold**; 150 F timeline (demo stopped at 120). ~20 min, ~20 GB. [▶ 19:44](https://youtu.be/xoJcz9u3c8g?t=1184)
12. Import this cache into the render scene in place of the advection sim. [▶ 22:02](https://youtu.be/xoJcz9u3c8g?t=1322)

## Gotchas
- Keep xpInfectio live for the source particles but excluded from the spawns; fuel for the spawns comes from xpPhysical once its group filter is cleared.
- Without the spawn Offset, the dots display looks sparse because the spawns stack on their source particle.

## Newest equivalent
**nxExplosiaFX** (Fused 2025.4) re-sims on the GPU from cached fuel particles; **nxSpawn** (2026.1 beta 3: On Death / At Age, Rate/Burst) replaces xpSpawn, **nxInfectio** for the spreading groups; cloth is still CPU xpClothFX (GPU cloth only announced). In C4D 2025.3+, the 2026.1 Pyro link can exchange smoke/fire with nxExplosiaFX.
