# nxVorticity — карточка инструмента

Встречается в **4** рецептах · 2024-03-19 → 2025-09-11 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxVorticity**: radius 150, strength 2000, **limit 100** (vorticity накапливается); Mapping ▸ **Age 0 → 150** → сила нарастает = кипение. [▶ 2:17](https://youtu.be/u2MiqeckNaQ?t=137) — *[2025-06-10](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)*
- **nxVorticity** под солвером жидкости: Strength **600%** уже держит завихрения; немного поднимите **Radius** (вихри крупнее). Очень высокая сила (~1500%) заставляет воду «кипеть» — сочетайте её с **Force Limit 20**, чтобы эффект был сильным, но под контролем. [▶ 12:23](https://youtu.be/_W2ivetBEPo?t=743) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- Выключите nxFluids, nxVorticity и nxRotate (жидкость закэширована); **nxGravity оставьте** — nxFoam нужна гравитация для плавучести/адвекции. Спрячьте эмиттеры жидкости. [▶ 27:07](https://youtu.be/_W2ivetBEPo?t=1627) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- Добавьте **nxVorticity** — он измеряет уже существующую закрутку и усиливает её. — *[2024-03-19](../../recipes/2024-03-19_nxvorticity-choppy-water.md)*

## Все рецепты (4)
- 2025-09-11 · [Обзор функций: переписанное GPU-ядро NeXus, GPU falloffs + Data Mapping на каждом слое, вариации в nxQuestion и поиск соседей](../../recipes/2025-09-11_nexus-core-falloffs-mapping-question-variations.md)
- 2025-06-10 · [Жидкая сфера: оседает → кипит → взрывается → плещется (initial state + nxVorticity / nxWind с маппингом по возрасту)](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)
- 2024-11-01 · [Бурлящая закрученная вода, видимая только через пену (nxFluids + nxVorticity с Force Limit + анимированный nxRotate → nxFoam с цветом по скорости)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-03-19 · [Неспокойная, закручивающаяся вода (nxVorticity на PBD и SPH)](../../recipes/2024-03-19_nxvorticity-choppy-water.md)
