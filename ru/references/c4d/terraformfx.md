# TerraformFX (C4D, входит в INSYDIUM Fused)

Источник: docs.insydium.ltd/terraformfx/* (Fused 2025, проверено 2026-11-03). Пересказ.

## Концепция
- **tfTerrain** = родительский объект (размер, сегменты — Lock Size/Segments Ratio, Display-пресет градиента Alpine, Tessellation Quads, Planet Radius для кривизны, Set Selection добавляет теги выделения верха/низа, Subdivide Bottom — только если террейн деформируется/симулируется). Новый террейн создаётся со стеком **tfNoise → tfGrid → tfFlood → tfErosionHydraulic** (лишнее удалите).
- Дочерние объекты = **операторы**, вычисляются в порядке иерархии, всё живое и недеструктивное.
  - **Generators** (создают высоту): tfNoise (14 noise от Maxon, по умолчанию Turbulence; Advanced Perlin/Simplex/Gabor/Cellular…; Octaves, Seed, Scale, Normalize, Warp), tfGradient, tfGrid (лепка через **tfBrush**), tfFormula, tfGroup, tfShader, **tfSpline** (Stroke = хребет/полотно дороги, Fill = плато; делайте Resample!), **tfTrace** (превращает любой 3D-mesh в террейн через raycast — логотипы/буквы в виде гор).
  - **Filters** (меняют высоту): tfAdjustment, tfBlur, tfClamp, tfCurve, tfDistribute, **tfErosion** (Hydraulic / Coastal / Snow / Thermal Weathering / Morphological), tfFlood (уровень воды), tfFold, **tfHighpass** (сохраняет мелкую детализацию — Radius 5%, Attenuate; Top Tip «precise landscapes»), tfSharpen, tfMirror, tfPath, tfQuantize (террасы), **tfRiver** (Settle Spline / Perlin Worm / вторичные притоки; Depth, Width, Inertia; Downhill Flow), tfWarp (можно рисовать кистью).
- **Вкладка Operator (общая):** Blend 0–100%; у генераторов blend-режимы Normal (нижний генератор перекрывает), Add, Subtract, Multiply (Gain 1), Lowest/Highest, Phoenix; Gain, Offset.
- **Вкладка Masking (у каждого оператора):** Altitude min/max + soften, Slope min/max + soften, **C4D Fields** (Box/Linear/Radial; 3D Sampling), Shader (включите Tile + Seamless). Time Dependent = пересчёт каждый кадр (анимированные террейны, Top Tip «Terrain Flow» с бегущим ландшафтом).
- Вкладка Preview: карты высоты/уклона/разницы по каждому оператору или общие; **экспорт карт в TIFF**.

## Эрозия
- **tfErosionHydraulic** — режим 2D Particles (быстро, по heightmap) или 3D **X-Particles** (медленнее, каналы глубже при большем числе Iterations). По умолчанию: Particle Count 10 000, Radius 3 cm, Evaporation 1%, Max Erosion 50 cm (жёсткий предел), Rain Everywhere / выше / ниже / по областям shader. Поднимайте **Inertia** для чётких русел. Меняйте по одному параметру за раз.
- **Thermal Weathering** — осыпание породы вниз по склону: Iterations 5, Threshold по уклону, Sediment Transport/Deposit.
- Coastal (береговые линии на уровне flood), Snow (накопление снега), Morphological.

## Объекты и утилиты
- **tfRoad** — дорога вдоль spline (Rail для наклона, Width/Height, Auto Banking, Clone Along Road для фонарей/ограждений; ось Y профиля смотрит на rail).
- **tfRock** — процедурные камни или «окаменение» своего mesh (Basic Shape, Detail, Contrast — высокое значение даёт трещины на поверхности, Mutate).
- **tfRiverExport** — точки tfRiver → сегментированный spline (для mesh воды/частиц).
- Commands, Presets, Grid Monitor, Preferences.

## Шейдинг
- **Advanced Terrain Shader** — один shader с деревом слоёв: слои комбинируют уклон, высоту, кривизну, AO и noise в grayscale, по которому берётся цвет из палитры; соседние слои смешиваются снизу вверх; дочерние маскируют родительские. Привяжите tfTerrain; один материал на один террейн. **Redshift (по умолчанию в C4D 2024) запекает стандартные shader в 128×128 → поднимите разрешение запекания в настройках Redshift.** Кэши не сохраняются → при открытии сцены пересобираются.
- **GradientUV Shader**, **Terrain Color Palette** (1 450+ пресетов), **Terrain Operator Shader** (вывести в материал карту отдельного оператора), шейдеры Ambient Occlusion и Curvature, New Default Terrain Material.
- Связка с X-Particles: эмиссия снега/деревьев с террейна с ограничениями Topology (высота/уклон); xpScatter для растительности; Taiao toGrass.
