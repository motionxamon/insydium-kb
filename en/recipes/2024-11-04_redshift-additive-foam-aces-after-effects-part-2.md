# Rendering speed-colored foam as additive glow in Redshift, ACEScg into After Effects + speed ramps (Color User Data → Ramp → Geometry Opacity)

- Source: INSYDIUM Training — Particle Vorticity - Part 2 — https://www.youtube.com/watch?v=hK1BxHqw4QU (2024-11-04)
- Host / generation: C4D 2025 + Redshift; cached foam from Part 1 (xpEmitter + NeXus nxFoam/nxColor); After Effects (OCIO/ACES)
- Goal: render ~4M cached foam particles as colored self-lit points inside a reflective container, then slow-mo and speed-ramp the 60 fps render in AE.

## Base
All NeXus modifiers off (reading the cache), fluid emitters hidden, foam Display LOD 15%. Project and Render Settings both **60 fps**. C4D 2025 default color management **ACEScg** — great for additive particles; match it in comp.

## Steps — Redshift
1. Render Settings ▸ Redshift ▸ Advanced ▸ Globals: turn off the **default light** (particles light the scene themselves).
2. Foam emitter ▸ **Redshift Object tag ▸ Particles**: **Point** instances (cheapest, no rotation needed); Scale Multiplier **0.5** (1 = overlapping white mess). Hide the container from render while tuning.
3. **RS Standard material** on the emitter: base color, reflection, transmission and coat off; **Emission** weight **5**, later **10**.
4. Node editor: **Color User Data** node, preset **Particle Color** (the greyscale speed color from Part 1) → **Ramp** node (any gradient; a saved "vorticity" preset here) → material **Geometry ▸ Opacity**. Colored opacity + emission = additive glow, overlaps burn toward white.
5. Container material: base almost black, low reflection Roughness for crisp reflections, **IOR 3** (from 2.5) to carry reflections higher up the walls.
6. Hide the low-poly collider rocks (xpJoin); show the high-res tfRocks; one rough material on their null, dark desaturated red.
7. **RS camera** parented to the container: zero X/Z and Heading, Pitch **−90°**, Focal Length **25 mm**, dolly on Y. Optical: pick focus on a rock, Aperture ~1, **Bokeh** on → blurs the upper reflections.

## Steps — render settings
8. Sampling: stay **Automatic** (no caustics/volumes/SSS). Test the noise **Threshold**: 1 → 7 s but speckly DOF/reflections; default 0.01 → 57 s clean; intermediate value → **28 s** acceptable. Check several consecutive frames for flicker, not one still.
9. Advanced ▸ System ▸ **Bucket size 128 → 512** with a single strong GPU: 28 → **24 s/frame**. With several GPUs keep buckets smaller so no card idles on a last bucket.
10. Output: all frames, start at **F35** (first foam), 60 fps, **OpenEXR**, default 16-scanline compression, **16-bit float**. (~5 h for the sequence.)

## Steps — After Effects
11. Project Settings: OCIO color managed, config **ACEScg** (default is ACES 1.2) → working space scene-linear ACEScg, display sRGB ACES SDR Video — matches the RS render view.
12. Interpret Footage: frame rate **30 fps** (half speed = smooth slow-mo; 60 = real time); Color tab media space ACEScg.
13. Speed ramps: Layer ▸ Time ▸ **Enable Time Remapping**; add key pairs around the slow-mo passages and keep their spacing (real speed), pull the next pair closer to speed up the gaps; Keyframe Assistant ▸ **Easy Ease Out** on ramps; final ramp-up and cut to black.
14. Render Queue ▸ Output Module ▸ Color: output space **sRGB ACES SDR Video** (Show All), not ACES — otherwise the file won't match the viewport.

## Gotchas
- Lesson from the result: the second splash wasn't prominent — kill nxRotate's power sooner (or delay the splash) so the fluid calms to dark before it.

## Newest equivalent
Render chain is unchanged. Upstream, Fused 2025.4's rewritten nxFoam (foam/bubbles/spray layers) and FLIP/APIC can replace the SPH/PBD + legacy foam setup; NeXus 2026.1 adds up to 8 emitter display channels for checking data in the viewport.
