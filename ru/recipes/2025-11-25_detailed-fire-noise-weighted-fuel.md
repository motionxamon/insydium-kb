# Детализированный огонь вокруг вращающегося логотипа (первый туториал по GPU nxExplosiaFX)

- Источник: Top Tip Tuesday — Detailed Fire — https://www.youtube.com/watch?v=WLqEdMEyd0M (2025-11-25)
- Хост / поколение: C4D, Fused 2025.4 beta → release (nxExplosiaFX) + Redshift
- Задача: порывистое, детализированное пламя, облизывающее вращающийся логотип.

## Шаги
1. Размер домена изменён, черновой **Voxel 2.5**. Sources: логотип, эмиссия Surface с увеличенным **Surface Width**; **Temperature 0**, только топливо → выставьте Simulation ▸ Burning **Ignition Temperature 0** (по умолчанию 600 требует нагрева). **Pressure 1** (спокойно). Colliders: тот же логотип.
2. Fuel **Weight by Noise** (67%, length scale 30, анимирован) → неравномерная, детализированная эмиссия; Fuel ~0.06.
3. Burning: **Burn Rate 10**, Temperature Production ~6000 (пламя выше), меньше дыма, **Gas Expansion 10**.
4. Dissipation: Temperature **~63** (пламя доходит до верха), dissipation дыма выше. Smoke Buoyancy слегка отрицательная.
5. Dynamics: Turbulence **Simplex strength 30, Octaves 0**, частота ниже (крупные порывистые завихрения); Vorticity по умолчанию 2 (высокие значения отлично смотрятся в черновом разрешении, но размываются в высоком) **mapped to Position Y** (сильнее внизу, слабее вверху).
6. Финал **Voxel 1** (>300 M вокселей), cache ~170 кадров (~2 мин).
7. В файле сцены есть Redshift-материалы «fire basic» и «fire detail» (стилизованное пламя, полое, со светящимися краями).
