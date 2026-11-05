# Building-block flower from custom models (Taiao Flower Custom Object parts, Profile spline preset, Furling)

- Source: Bite-Sized — Taiao Custom Flower — https://www.youtube.com/watch?v=DQti40NwwSY (2025-02-06)
- Host / generation: C4D; **Taiao** (Fused) Flower + Plant objects; Redshift default materials
- Goal: a stylised toy-brick flower on a stem, every part swapped for a pre-modelled component.

## Base
Pre-modelled parts: petal, leaf, sepal, pistil, receptacle and a small cylinder. Petals are a rotation-ready hierarchy so their curl can be tweaked/animated later. **Orientation matters: each part's Z axis must point outwards**, otherwise it attaches wrongly.

## Steps — flower head
1. INSYDIUM ▸ Taiao ▸ **Flower**. Per part, drop your model into its **Custom Object** link: Receptacle (Main tab), Sepal, Pistil and Petal (Geometry tab). Disable the stamen for now. [▶ 1:45](https://youtu.be/DQti40NwwSY?t=105)
2. Fix fit part by part (hide others to see): Receptacle **Position** so it meets the pistil; sepals far too big → size **0.4**, then Radius and **Orientation** slider; petals smaller, raised, Radius pulled in, adjust **Count** and Orientation. [▶ 4:40](https://youtu.be/DQti40NwwSY?t=280)
3. Stamen ring: keep Taiao's own geometry, Distribution **Wall** (ring) + Radius; reset the profile curve to flat; raise **height/width segments**; load a saved **Profile spline preset** that dents the surface into stud-like bumps. [▶ 6:05](https://youtu.be/DQti40NwwSY?t=365)
4. **Add Parts ▸ Stamen** as a child: Distribution **Radial** (single, centred), move it to the very top, Geometry ▸ custom **cylinder**, size up slightly; add a **Furling** modifier and re-adjust the angle. [▶ 12:20](https://youtu.be/DQti40NwwSY?t=740)
5. **Rebuild** all components.

## Steps — stem and leaves
6. INSYDIUM ▸ Taiao ▸ **Plant** ▸ Trunk: height **20 cm**, thickness **2 cm**; reset its spline to a single thickness. [▶ 9:14](https://youtu.be/DQti40NwwSY?t=554)
7. Finer mesh: Global settings value **0.1** and more **Ring Segments** for clean quads; load the same Profile preset → brick studs on the stem. [▶ 9:45](https://youtu.be/DQti40NwwSY?t=585)
8. **Add Part ▸ Custom Object** → link the finished Flower on top. [▶ 10:11](https://youtu.be/DQti40NwwSY?t=611)
9. **Add Part ▸ Leaf**: top leaf off, Geometry ▸ Custom Object = leaf model; Scale **1.5**, Distribution kept away from top and bottom, raise Count, tune Orientation (lower base leaves). [▶ 10:44](https://youtu.be/DQti40NwwSY?t=644)
10. Trunk ▸ **Furling** modifier to bend the stem; rescale the flower head if needed. Drop copies into a Taiao growth/scatter object for a flower patch. [▶ 12:20](https://youtu.be/DQti40NwwSY?t=740)

## Gotchas
- Stamens lost their material once nested on the plant → assign a material to the Plant (or the trunk) to fix it.
- Taiao size/orientation sliders interact; retune orientation after changing angles or sizes.
