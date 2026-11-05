# nxExplosiaFX → OpenVDB → Redshift with vector motion blur

- Source: Top Tip Tuesday — ExplosiaFX MotionBlur — https://www.youtube.com/watch?v=qZyBMJaN6ak (2026-09-29)
- Host / generation: C4D, Fused 2025.4+ (GPU nxExplosiaFX) + Redshift
- Goal: render a fast fire/smoke blast with correct velocity-based motion blur.

## Steps
1. **Don't use Upscaling** when you need render motion blur: upscaling adds detail only to smoke & temperature, not to velocity → blur won't match. Get detail with a **smaller Voxel Size** instead (e.g. 3.5) — slower sim. [▶ 1:07](https://youtu.be/qZyBMJaN6ak?t=67)
2. **xpCache** (INSYDIUM ▸ Cache): **EFX Format → OpenVDB**; enable **Density, Temperature, Velocity** (velocity is required for blur); Fuel can be skipped. Build (≈15 min for 200 frames in the demo). [▶ 2:14](https://youtu.be/qZyBMJaN6ak?t=134)
3. Disable nxExplosiaFX and the cache; add a Maxon **Volume Loader** and link the **first VDB frame** — it detects density, temperature, vel_x / vel_y / vel_z. [▶ 2:56](https://youtu.be/qZyBMJaN6ak?t=176)
   - The Volume Loader viewport looks much thicker than EFX — just a different calibration, ignore.
4. Material: Redshift volume (Standard Volume) with two Scalar Attribute nodes → Density and Temperature. In the EFX preset the smoke attribute is named `smoke`; for the Volume Loader change it to **`density`** (preset: Volume Loader) or smoke won't render. [▶ 4:22](https://youtu.be/qZyBMJaN6ak?t=262)
5. Add a **Redshift Object tag** on the Volume Loader → Motion Blur tab → Motion Vectors: **vel_x, vel_y, vel_z** (exact names from the loader). [▶ 6:38](https://youtu.be/qZyBMJaN6ak?t=398)
6. Render Settings ▸ Redshift ▸ Advanced: **Motion Blur on** + **Deformation Blur on**. [▶ 7:41](https://youtu.be/qZyBMJaN6ak?t=461)
7. Tune **Scale** on the tag: 0.5 = subtle, 1 = natural, 3 = exaggerated speed (loses flame detail). [▶ 10:20](https://youtu.be/qZyBMJaN6ak?t=620)

## Gotchas
- Motion vectors work only through the Volume Loader, not natively on the EFX object.
- Expect ~25–40% longer renders with blur.
- 2026.1 beta adds an automatic default Redshift smoke material when nxExplosiaFX VDB output is set to render/live — check it before building the material by hand.
