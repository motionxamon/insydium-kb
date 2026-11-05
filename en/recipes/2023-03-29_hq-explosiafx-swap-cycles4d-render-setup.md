# Swapping in a high-detail smoke sim, final retime and Cycles 4D render setup (xpExplosiaFX, xpCache Offset, Cycles 4D)

- Source: Maintenance Training — XP Countdown - Series 3 - Combining Scenes part 2 — https://www.youtube.com/watch?v=teKbNFK3H0E (2023-03-29)
- Host / generation: C4D; CPU xpExplosiaFX + xpCache; renderer Cycles 4D (CUDA)
- Goal: replace the burn's smoke/fire with the high-quality re-sim, fix shot timing, tune the volume shader and render beauty + emission passes.

## Steps
1. Visibility gotcha: children set to green dots override a parent null's keyed "off" → **Ctrl+Alt-click** the dots back to grey so they inherit the parent.
2. From the HQ burn file copy only the **xpExplosiaFX** object + its **xpCache** (Copy Tag Data on), paste under a new "5 burn HQ" null.
3. Match the old cache: Playback **Hold**, **Offset −50**. HQ cache ≈576 MB, so scrubbing is slow.
4. **Hardware OpenGL** render 0–130 to check that the *numbers* read long enough. Result: hold the 5 ~15 F longer → both caches Offset **−65**.
5. Shift the Linear field keys (PolyFX dissolve) by the same 15 F in the **Timeline F-Curve**: select all, **Shift-drag** horizontally (F50 → F65). Nudge the Y curve so no polygons break up before the fire reaches them.
6. Cycles 4D **ExplosiaFX fire & smoke preset** node tree: Point Density (smoke density) → Math Multiply → Volume Scatter / Volume Absorption → Add; Point Density (burn) → Color Ramp → Multiply → **Emission** (Blackbody) → Add → Volume.
7. Thinner smoke: divide both multiplies by 5 (scatter **100 → 20**, absorption **13 → 2.6**). Fire brightness = emission temperature/strength, kept at **60**; unplug Blackbody to use a flat colour (e.g. green fire).
8. Fade smoke after the 4 is revealed: keyframe both multiplies, then key them to **0** a little later (gone by ~F160).
9. Samples: real-time preview at 10; **25 = 625** path-tracing samples, **22 = 484** (used; a bit noisy, 25 better for production). Check noise over several full-res frames, not only in preview.
10. Render settings ▸ Cycles 4D: Device **CUDA**; keep indirect clamping; lower **Volume Step Size** if smoke shows slicing stripes (slower); Film **Transparent Glass** on; Render Elements ▸ **Emission** (only the fire emits).
11. Output 720p, **30 fps** (match Ctrl+D project), frames 0–160. Save: **OpenEXR 16-bit**, Alpha on. **Multi-Pass** on, same path, EXR, **Multi-Layer File off**, **Layer Name as Suffix** on, and enable **Post Effects** in the multipass list or the Cycles pass won't save.
12. Save a separate "v13 render settings" scene; render took ~3 h.

## Gotchas
- Holding 1/2/3 to navigate while a field is highlighted changes its value.
- The HQ sim was spawned from the existing cloth positions, so the fire no longer lingers on the revealed 4 — only a fully higher-res original sim keeps that interaction.

## Newest equivalent
**nxExplosiaFX** (GPU, Fused 2025.4) with volumetric GPU viewport — retiming via **nxCache**; in 2026.1 beta C4D gets a default **Redshift smoke material** for nxExplosiaFX VDB and the **Pyro link** (C4D 2025.3+); **nxWarp** can reshape smoke.
