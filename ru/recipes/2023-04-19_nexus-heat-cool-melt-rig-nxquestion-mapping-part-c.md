# Интерактивный риг плавления / застывания на цвете частиц (mapping Clamp Max Speed в nxSpeed + nxQuestion с fields + nxBlend + mapping вязкости SPH)

- Источник: INSYDIUM LIVE! — April 2023 - X-Particles, NeXus & MeshTools — https://www.youtube.com/watch?v=U8zISIlBq90 (2023-04-19)
- Хост / поколение: C4D; превью G2 NeXus (nxFluids SPH, nxGravity, nxSpeed, Data Mapping, nxQuestion, nxBlend на xpEmitter) — функции вышли в Fused 2023.3
- Задача: твёрдый цилиндр из жидкости плавится там, где его «нагревает» field, капает по краям и снова застывает — интерактивно во вьюпорте.

## Исходная сцена
Plane **2000 × 2000**, синий цвет, collider tag: без отскока, высокий friction. **xpEmitter** shape **Cylinder**, поворот P **90°**, Y **100** (стоит на полу). Emission **Shot**, **Hexagonal**, режим **Simulate**, speed 0, радиус **2**, **Jitter 1 cm** по X/Y/Z, цвет частиц **чёрный** (цвет — управляющий сигнал).

## Шаги
1. **nxGravity**; **nxFluids** solver **SPH**, больше substeps, Viscosity на максимум с **1000** итераций, Surface Tension **50**.
2. Заморозка чёрных частиц: **nxSpeed**, Operation Incremental → **Acceleration**, значение 0, **Clamp Max Speed 100,000**; слой Mapping **Color Brightness → Clamp Max Speed** с очень узким выходным диапазоном, чтобы чёрный = скорость ~0.
3. Опустите nxSpeed в **самый низ** списка модификаторов — он должен выполняться после gravity и fluids, иначе блок всё равно оседает.
4. **nxQuestion** «heat»: Particle **Age ≥ 0** → Action **Set Color**, значение **100%** (чуть жёлтого). Добавьте в question сферический **Field** → белеют и плавятся только частицы внутри field.
5. nxQuestion «cool» ниже: то же условие → цвет **чёрный**, **Weight** у action низкий (**3%**), чтобы остывание отставало от нагрева.
6. nxQuestion «edges»: **Particle Neighbors < 30** (поиск ~10 cm) → белый цвет — находит поверхность, так что края продолжают капать, пока ядро застывает (для проверки красьте в красный).
7. Распространение тепла: **nxBlend**, режим **Additive**, Distance **50**, Strength на максимум, время blend **60 → 90** кадров.
8. Неравномерное остывание: question cool ▸ Fields ▸ Shader field с **Noise (Blistered Turbulence)**, крупный масштаб, высокий контраст; weight до **10%**, затем **8%** (слишком сильно — частицы застывают в воздухе).
9. Mapping в nxFluids: Color Brightness → **SPH Viscosity** (чёрный — высокая, белый — низкая, кривая сглажена), затем скопируйте map для **Surface Tension** → горячие частицы текут, потом тянутся и застывают.

## Подводные камни
- Порядок выполнения решает, сработает ли ограничение скорости.
- Question нагрева и остывания с одинаковым весом гасят друг друга — уменьшайте weight у cool.
- Работало интерактивно на RTX 2080.

## Как сейчас (новые инструменты)
Связанные рецепты: «nxFluids Melt Rig» (2024-01-02) и «Hot/Cold Variable Viscosity» (2025-09-09). В Fused 2025.4 используйте **nxFluids FLIP/APIC** с переменной вязкостью и GPU **nxMesher**; в 2026.1 beta добавились non-Newtonian FLIP (Flow Index, Yield Stress), смена материала через Mixer в **nxMPM** и **nxBind** с освобождением по температуре, а также 16 режимов nxFalloff для зоны нагрева.
