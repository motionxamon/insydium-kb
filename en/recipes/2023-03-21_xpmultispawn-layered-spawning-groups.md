# Three generations of spawning from one emitter (xpMultiSpawn levels + groups for display)

- Source: Top Tip Tuesday — xpMultiSpawn — https://www.youtube.com/watch?v=XwQyDoAPNa4 (2023-03-21)
- Host / generation: C4D; CPU X-Particles (xpEmitter, xpMultiSpawn, xpTurbulence, groups)
- Goal: arrows burst into squares, which burst into short-lived dots — exploding/disintegrating streams.

## Base
xpEmitter with **Arrow** display particles and a turbulence modifier.

## Steps
1. Modifiers ▸ Generate ▸ **xpMultiSpawn** (unlike xpSpawn it needs no separate spawn emitter). Default level: 10 new per source particle at age 0, for one frame.
2. **Level 1**: at source age **50**, count **5**; direction **Random Spherical → Relative to Source Particle** + a little spread (reads like motion inheritance); **Kill Source Particle**.
3. Groups: emitter ▸ Groups tab, Ctrl+Alt-click the add button to create **3 groups**; emitter mode **First Group Only** (originals → group 1).
4. **Level 2**: age **30**, count **5**, Relative + lots of spread, kill source, new particles → **group 2** (group display: **Squares**).
5. **Level 3**: age **20**, count **100**, kill source, set life **20 F** (variation ~5), Relative + lots of spread, → **group 3** (display: **Dots**).

## Gotchas
Without a group assigned, spawned particles keep the emitter's display (arrows).

## Newest equivalent
**nxSpawn** (2026.1 Beta 3: Instant / At Age / On Collision / On Death, 8 sub-layers); stable Fused: nxQuestion Spawn action.
