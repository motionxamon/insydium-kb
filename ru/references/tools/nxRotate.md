# nxRotate — карточка инструмента

Встречается в **9** рецептах · 2023-02-28 → 2026-06-05 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **+ nxRotate**: сначала Rotate Speed 75°, потом **110°**. [▶ 9:40](https://youtu.be/SLUkMBqGfZg?t=580) — *[2026-06-05](../../recipes/2026-06-05_blender-additive-particle-vortex-point-cloud.md)*
- nxRotate ▸ вкладка Falloff ▸ **Create/Add** → переключите Box на **Sphere**, увеличьте, Offset ≈ **−2** для длинного перехода — сильное вращение у кольца рождения, а дальше только турбулентность. [▶ 9:37](https://youtu.be/SLUkMBqGfZg?t=577) — *[2026-06-05](../../recipes/2026-06-05_blender-additive-particle-vortex-point-cloud.md)*
- **nxRotate**: speed 360 × большой множитель; Mapping ▸ **Radius** 1 → 2 cm управляет Rotation Speed (маленькие = неподвижны). [▶ 6:34](https://youtu.be/v63KTwt6pI4?t=394) — *[2025-06-24](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)*
- **nxRotate**: Pitch **90°**, чтобы вращение шло вокруг оси цилиндра; чтобы отцентровать, сделайте его дочерним к контейнеру, обнулите координаты и верните в стек модификаторов. Анимируйте **Rotate Speed 0 → 360 → 0** после того, как первый всплеск успокоится (снова 0 на F442) — дальше водоворот поддерживает vorticity. [▶ 17:16](https://youtu.be/_W2ivetBEPo?t=1036) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- Выключите nxFluids, nxVorticity и nxRotate (жидкость закэширована); **nxGravity оставьте** — nxFoam нужна гравитация для плавучести/адвекции. Спрячьте эмиттеры жидкости. [▶ 27:07](https://youtu.be/_W2ivetBEPo?t=1627) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*

## Подводные камни
- Вывод по результату: второй всплеск получился невыразительным — отключайте силу nxRotate раньше (или сдвиньте всплеск позже), чтобы жидкость успела успокоиться и потемнеть. — *[2024-11-04](../../recipes/2024-11-04_redshift-additive-foam-aces-after-effects-part-2.md)*

## Все рецепты (9)
- 2026-06-05 · [Аддитивный вихрь частиц, рендер как point cloud (nxEmitter Disc Edge Only, nxTurbulence, nxRotate + Sphere falloff, экспорт Point Cloud)](../../recipes/2026-06-05_blender-additive-particle-vortex-point-cloud.md)
- 2025-11-26 · [Обзор функций: жидкости в Fused 2025 — GPU FLIP/APIC с вязкостью, nxMesher, nxSplash (Final Tech Preview)](../../recipes/2025-11-26_fused-2025-flip-viscosity-nxmesher-nxsplash-feature-notes.md)
- 2025-09-11 · [Обзор функций: переписанное GPU-ядро NeXus, GPU falloffs + Data Mapping на каждом слое, вариации в nxQuestion и поиск соседей](../../recipes/2025-09-11_nexus-core-falloffs-mapping-question-variations.md)
- 2025-06-24 · [Самоподдерживающийся цикл частиц: рост / расталкивание / уменьшение (nxAttract + nxPush + поле в nxQuestion + nxRotate через mapping)](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)
- 2025-02-20 · [Бесшовный бесконечный луп из отрендеренной симуляции частиц (After Effects: дубликат + кроссфейд по opacity)](../../recipes/2025-02-20_seamless-particle-render-loop-after-effects.md)
- 2024-11-04 · [Рендер пены с цветом по скорости как аддитивного свечения в Redshift, ACEScg в After Effects + speed ramps (Color User Data → Ramp → Geometry Opacity)](../../recipes/2024-11-04_redshift-additive-foam-aces-after-effects-part-2.md)
- 2024-11-01 · [Бурлящая закрученная вода, видимая только через пену (nxFluids + nxVorticity с Force Limit + анимированный nxRotate → nxFoam с цветом по скорости)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2023-04-13 · [Кристалл, который осыпается по осколку (xpShatter + emitter, xpQuestion Inside Volume, mapped xpSpeed/xpRotator/xpSpin, xpFreeze)](../../recipes/2023-04-13_crystal-shatter-xpshatter-question-driven-breakup-part-a.md)
- 2023-02-28 · [Основы вращения частиц (Use Rotation на эмиттере: Set / Tangential / None + случайное вращение xpSpin)](../../recipes/2023-02-28_particle-rotation-tangential-random-spin.md)
