# Combining cached sub-scenes into one master build (xpCache Hold/Offset, Alembic speed, PolyFX + layered fields)

- Source: Maintenance Training — XP Countdown - Series 3 - Combining Scenes Part 1 — https://www.youtube.com/watch?v=j453vKa_ay4 (2023-03-29)
- Host / generation: C4D; CPU X-Particles (xpCache, xpOpenVDBMesher, xpExplosiaFX, xpClothFX cloth, xpShatter) + Alembic + MoGraph PolyFX/Plane effector
- Goal: assemble the "6 splash → 5 fill → 5 burn → reveal 4" countdown shots from separate cached scenes and line up their timing.

## Base
Every sub-scene was already cached (xpCache) and named per shot; the splash was baked to Alembic (SDS bag + xpOpenVDBMesher in a Boole). New master file saved in its own "render builds" folder with version suffixes; one organisational null per shot (6 splash, 5 fill, 5 burn, 4 crumble).

## Steps
1. **Copy between files**: on each **xpCache tag** tick **Copy Tag Data / Copy Cache Data**, then Ctrl+C the needed objects (mesher, cache object, emitters; skip emitters whose result is already meshed/cached) and paste into the master. [▶ 4:08](https://youtu.be/j453vKa_ay4?t=248)
2. Splash too slow → Alembic object ▸ Object ▸ **Speed 180%**. Add a **Display tag ▸ Lines** to see through it. [▶ 5:40](https://youtu.be/j453vKa_ay4?t=340)
3. Disable the mesher while timing (particles play faster), re-enable afterwards. [▶ 7:05](https://youtu.be/j453vKa_ay4?t=425)
4. Retime a cached shot: **xpCache ▸ Object ▸ Playback ▸ Hold**, then **Offset** (fill: +20 frames so it starts ~F30 instead of F10). [▶ 7:37](https://youtu.be/j453vKa_ay4?t=457)
5. xpOpenVDBMesher can stick on its first frame in the viewport → keyframe **Basic ▸ Visible in Editor/Renderer** off at F29, on at F30. [▶ 24:53](https://youtu.be/j453vKa_ay4?t=1493)
6. Burn shot (xpExplosiaFX + cloth + PolyFX + Plane effector): same Hold/Offset; tested −58 → −53 → final **−50**. Keyframe the Alembic **Enabled** off and the cloth null visibility on at the hand-over frame; move those keys in the **Dope Sheet** whenever the offset changes. [▶ 26:02](https://youtu.be/j453vKa_ay4?t=1562)
7. Judge timing with a **Hardware (OpenGL) render** to Picture Viewer, 0–100 F at 30 fps — viewport playback lies. [▶ 18:34](https://youtu.be/j453vKa_ay4?t=1114)
8. Number 4 (xpShatter): untick **Display ▸ Draw Cut Edges** to compare; delete only the 4's cache tag, set an **Offset 0.3 cm** gap between shards (AO-like seams + inner colour), then xpCache **Build Cache ▸ Continue** so only the missing object is recached. Do NOT do this on the 3. [▶ 20:40](https://youtu.be/j453vKa_ay4?t=1240)
9. In the master, the 4's cache **Playback ▸ Manual Time** (holds frame 0, static); null visibility keyed on when the cloth rips. [▶ 24:08](https://youtu.be/j453vKa_ay4?t=1448)
10. Cloth dissolve: Plane effector (scale) drives PolyFX; falloff = **Linear field** + **Random field** in **Overlay** blend, so the noise only acts inside the linear gradient. Tighten the gradient, keyframe the linear field's position below → above the cloth. [▶ 27:30](https://youtu.be/j453vKa_ay4?t=1650)
11. xpExplosiaFX ▸ Display **Fuel and Smoke**; in the **Timeline F-Curve** pull Bezier handles on the field's Y keys so pieces vanish only once under the fire. [▶ 29:34](https://youtu.be/j453vKa_ay4?t=1774)

## Gotchas
- Organised folders, names and caches are what make the merge easy; render the remaining shots individually and combine in comp.

## Newest equivalent
G2/G3: **nxExplosiaFX** (Fused 2025.4) for the burn, **nxMesher** instead of xpOpenVDBMesher, **nxShatter** (2026.1 beta) for the 4; **nxCache** has a frame range. Shaping the dissolve: 16 **nxFalloff** modes + **nxFalloff Modifier** (Remap, Step, Curve, Delay, Grow) instead of stacked C4D fields.
