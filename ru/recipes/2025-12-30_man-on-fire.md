# Бегущий горящий человек (nxExplosiaFX: наследование движения, топливо с весом по нойзу, бюджет на апскейл)

- Источник: Top Tip Tuesday — Man On Fire — https://www.youtube.com/watch?v=jNrr7gboaHo (2025-12-30)
- Хост / поколение: C4D, Fused 2025.4 (первый релиз GPU EFX) + Redshift
- Задача: пламя, срывающееся с бегущего мокап-персонажа.

## Шаги
1. Источник = **лоупольный** бегущий персонаж (рендерится хайполи). Voxel **2** для черновика.
2. Buoyancy **Gravity выкл.**; Forces: добавьте **Wind** 150 со **100% variation** (порывисто); направление по умолчанию +Z (Add Wind Object, чтобы повернуть).
3. Sources: **Surface Width 0**, Temperature 1200, больше Fuel, Fuel **Weight by Noise** (GPU-нойз, высокая strength = высокий контраст, length scale ~20) → пламя пятнами; немного **Pressure** (отталкивает топливо от поверхности, добавляет шума); **Velocity from Object Motion 100%** (>100% утрирует рывок).
4. Burning: Temperature Production ~2000, **Burn Rate** выше, Smoke Production 2 (тонкие струйки), Gas Expansion 3, Ignition Temperature 0.
5. Dissipation: диссипацией температуры регулируется длина пламени.
6. Финал: Voxel **1.3**, потом **Upscaling 3**. Бюджет по Memory Stats: RTX 3090 тянет ≈ **550 M вокселей** (здесь база 148 M → ×2 = 296 M → ×3 нормально, ×4 слишком много).
