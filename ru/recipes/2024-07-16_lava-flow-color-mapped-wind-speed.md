# Лава, которая застывает и снова плавится (цвет от анимированного поля Random → замапленные сила nxWind + максимальная скорость nxSpeed, nxFluids)

- Источник: Top Tip Tuesday — Lava Flow Fluids — https://www.youtube.com/watch?v=bslBFptQSSM (2024-07-16)
- Хост / поколение: C4D; xpEmitter + NeXus GPU (nxWind Von Karman, nxColor, nxGravity, nxFluids, nxSpeed) + поле C4D Random
- Задача: капля жидкости, которая остывает и застывает гребнями там, где noise чёрный, и снова течёт там, где он становится белым.

## Исходная сцена
Plane 1000×1000 с xpCollider (friction 20, bounce 0). xpEmitter **Cylinder** r 25 / h 50, Shot hexagonal, speed 0, radius 1.

## Шаги
1. **nxWind**, повёрнутый по направлению потока, режим **Von Karman**, strength **250**, турбулентность ветра пока выключена.
2. **nxColor ▸ Gradient by Parameter**, оттенки серого (удали цветные точки), замапленный на поле **Field ▸ Random**: Perlin, **scale 500**, **animation speed 25%**; Remapping ▸ contour-кривая для контраста.
3. nxWind ▸ **Mapping ▸ Color Brightness** → **Wind Strength**, диапазон 0 (чёрный) → 1 (белый): на чёрных ветра нет.
4. **nxGravity** strength 200 (отображение выключено).
5. **nxFluids** по умолчанию, **substeps 5**.
6. **nxSpeed** в самом низу: Incremental, speed 0, **Max Speed clamp 200**; Mapping ▸ Color Brightness → **Maximum Speed** → чёрные частицы застывают, белые текут → образуются гребни, которые потом плавятся по мере анимации noise.
7. Варианты вида: смени noise в поле Random (**Electric** = замирает, потом резко рвётся вперёд; **Displaced Voronoi** = крупные тёмные гребни). Много **surface tension** → выпуклые щупальца.

## Как сейчас (новые инструменты)
FLIP/APIC с переменной/замапленной вязкостью (Fused 2025.4) или non-Newtonian (Yield Stress) и Mixer в 2026.1 — см. «Hot/Cold Variable Viscosity»; управляй этим анимированным **nxFalloff Noise** вместо поля C4D.
