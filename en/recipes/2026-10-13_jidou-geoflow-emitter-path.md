# Procedurally animate an emitter along a path with jdGeoFlow

- Source: Top Tip Tuesday — Jidou Emitter Control — https://www.youtube.com/watch?v=CaiS-kcvPKs (2026-10-13)
- Host / generation: C4D, Fused 2025.4.1+ (Jidou; playback modes from 2025.4.1) + NeXus emitter (nxPush setup)
- Goal: move a particle emitter around a circle/logo spline with easing, loops and noise — a keyframe-free replacement for C4D's Align to Spline tag.

## Scene tree
```
jdGeoFlow (INSYDIUM ▸ Jidou)   Objects: xpEmitter   Mode: Path
  Path tab: Shape Circle (default) or Custom → flower/logo spline
xpEmitter (orange, nxPush setup — particles limited in Y)
```

## Steps
1. Delete any Align to Spline tag. Add **jdGeoFlow**, drag the emitter into its objects, set **Mode: Path** (not Connected Points). [▶ 1:56](https://youtu.be/CaiS-kcvPKs?t=116)
2. Path tab: default **Circle** works immediately; switch to **Custom** and link any spline (logo, flower). [▶ 5:49](https://youtu.be/CaiS-kcvPKs?t=349)
3. Main tab timing: **Auto Time** = whole timeline for one pass. Turn it off and set an **End** (e.g. 200 frames per revolution). [▶ 2:41](https://youtu.be/CaiS-kcvPKs?t=161)
4. **Easing curve** shapes speed along the path (slow-in → fast, etc.); linear = constant. [▶ 3:24](https://youtu.be/CaiS-kcvPKs?t=204)
5. **Loop modes:** Stop (default), **Ping-Pong**, Loop, **Continue** (keeps flying off along the last direction — exits frame). Cycles complete *within* the end time → when you set 2 cycles, double the end time (400) to keep the same speed. [▶ 5:24](https://youtu.be/CaiS-kcvPKs?t=324)
6. **Motion tab** → enable noise motion: amplitude per axis (here X/Z 25 cm, Y 0 because particles are locked to a plane) → organic wobble on top of the path animation. [▶ 6:45](https://youtu.be/CaiS-kcvPKs?t=405)
7. Emitter birthrate ~500 for the final look.

## Notes
- Works for any object, not just emitters (cameras → jdFlowCam is the dedicated camera tool).
- Combine with nxPush/nxTurbulence trails for "drawing" logos with particles.
