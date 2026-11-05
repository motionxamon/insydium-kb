# Reveal a mesh only where smoke passes through it (Cycles 4D Point Density on the mesh, staggered xpExplosiaFX emitters)

- Source: Maintenance Training — XP Countdown - Series 2 - Cycles 4D Point Density — https://www.youtube.com/watch?v=XNLOKgKCuvU (2023-03-29)
- Host / generation: C4D; CPU xpExplosiaFX + xpFlowField + xpCache; Cycles 4D (Point Density volume node)
- Goal: the "1" appears as smoke filling its volume for ~2 s (F120–180) — smoke outside the letter stays invisible.

## Base
Copy the xpSystem EFX (+ the flow-field splines into the same folder) from the advection scene into a new file; remove the old cache tags, rename domain/emitter "smoke fill". Preview at **Voxel 4 cm / particle radius 8**; production **2 cm / 5 cm**.

## Steps
1. Quick Cycles 4D test light: plane above the scene with a **Surface ▸ Emission** material, strength **6**; open the real-time preview.
2. Create ▸ Volume preset **ExplosiaFX Smoke Basic** — put it on the **"1" mesh**, not on the EFX domain.
3. In the node graph (remove the color ramps for clarity): **Point Density** node ▸ Object = EFX domain, space **World** → density is read from the sim but drawn only inside the mesh's volume.
4. Boost the density **Math ▸ Multiply** to ~50 so the fill reads.
5. Enough smoke for 60 frames: duplicate the EFX source emitter (Ctrl-drag) and offset its keyframed emission-falloff animation → 4, then **5** staggered waves.
6. Last two emitters: Birth Rate **3000**/s — real count stays far lower because no-intersection emission is on.
7. Check intersections at production res frame by frame (F140–180) in the real-time preview.
8. **xpCache** to external files, cache mode **Include** with only the EFX domain listed; all 300 F ≈ 8 min, ~8 GB in the demo. Then disable the emitters and trim the timeline to 220 F.

## Gotchas
- Without World space the Point Density lookup is misplaced and only stray bits show.
- The reveal is a render trick: the visible "outside" smoke is rendered separately (blue) and the inside fill gets its own color (green) in comp.

## Newest equivalent
Run the smoke on GPU **nxExplosiaFX** (Fused 2025.4) and do the same in-mesh density lookup in your current renderer's volume shader; nxExplosiaFX also ships a default Redshift smoke material for its VDB (2026.1 beta).
