# Add rock and crack detail without changing the terrain silhouette (tfGroup + High Pass filter)

- Source: Top Tip Tuesday — TerraformFX HighPass — https://www.youtube.com/watch?v=di7_ZIst1Ws (2023-08-01)
- Host / generation: C4D; TerraformFX (tfTerrain, tfGrid, tfWarp, tfNoise, tfGroup, High Pass filter)
- Goal: keep a precisely matched background hill shape (e.g. from a plate) and layer in only high-frequency desert detail.

## Base
tfTerrain sculpted with **tfGrid** + **tfWarp** — the shape that must not change.

## Steps
1. Problem: tfTerrain ▸ Add Operator ▸ **tfNoise** (switched to a billowy type, more octaves, lower Blend) adds detail but shifts the overall elevation — toggle it to see. [▶ 1:04](https://youtu.be/di7_ZIst1Ws?t=64)
2. Add Operator ▸ **tfGroup**, put the noise inside (group toggles everything beneath it). [▶ 2:01](https://youtu.be/di7_ZIst1Ws?t=121)
3. Inside the group add a **High Pass** filter → only the high-frequency part of the noise survives; toggling the group no longer changes the silhouette. [▶ 2:31](https://youtu.be/di7_ZIst1Ws?t=151)
4. High Pass **Radius**: small = only the finest detail; larger lets more frequencies through; **100** ≈ no filter (and slow). Demo used **26.5**, then lowered the noise amplitude/gain so spikes don't lift the landscape. [▶ 3:17](https://youtu.be/di7_ZIst1Ws?t=197)
5. Cracks: second **tfGroup** with a **tfNoise** set to **Voronoi**, Scale **~20**, operator Gain **~10**, **Invert** in properties, plus its own **High Pass** → crack network. Gain **20** for deeper cracks. [▶ 5:09](https://youtu.be/di7_ZIst1Ws?t=309)
6. Mask the crack group by **Altitude** (only below **20 cm**) so cracks sit in the low areas. [▶ 5:42](https://youtu.be/di7_ZIst1Ws?t=342)
7. Disabling both groups returns the exact original shape. [▶ 6:00](https://youtu.be/di7_ZIst1Ws?t=360)

## Gotchas
- Large high-pass radii are expensive to evaluate.

## Newest equivalent
Same in Fused 2025.x; Fused 2024.2's **Advanced Terrain Shader** and curvature channel can texture the new detail. In Redshift (C4D 2024+) raise the baked-shader resolution above the 128×128 default for TerraformFX shaders.
