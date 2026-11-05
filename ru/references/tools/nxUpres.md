# nxUpres — карточка инструмента

Встречается в **8** рецептах · 2023-06-23 → 2025-08-14 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxUpres** (ниже модификаторов движения): Source = исходный эмиттер, Destination = dest; **Groups Affected group 2**, чтобы невысвобожденные частицы оставались на месте. [▶ 5:14](https://youtu.be/rMKmeJ68yiE?t=314) — *[2025-05-27](../../recipes/2025-05-27_upres-explode-position-velocity-blend.md)*
- **nxUpres**: Source = эмиттер с поверхности, Destination = объёмный эмиттер; снимите Velocity, отметьте **Color**. Каждая частица объёма смешивает цвета 3 ближайших частиц поверхности. Скройте частицы поверхности, шагните на один кадр. [▶ 4:12](https://youtu.be/N32nQXnqMLE?t=252) — *[2025-04-29](../../recipes/2025-04-29_textured-particle-volume-nxupres-color.md)*
- Объёмный эмиттер ▸ **Initial State ▸ Set State**; Emission → **Controlled Only**. Отключите эмиттер поверхности и nxUpres. [▶ 5:35](https://youtu.be/N32nQXnqMLE?t=335) — *[2025-04-29](../../recipes/2025-04-29_textured-particle-volume-nxupres-color.md)*
- Добавьте **nxUpres**: Source = закэшированный низкодетальный эмиттер, Destination = живой высокодетальный эмиттер, передавать **только Velocity**. [▶ 3:51](https://youtu.be/GU37kEW507c?t=231) — *[2025-04-15](../../recipes/2025-04-15_upres-granular-sim-nxupres-velocity.md)*
- **nxUpres**: Source = закэшированный эмиттер, Destination = новый эмиттер. Particles-to-blend по умолчанию 3 ближайших (velocity blend); поднято до ~7 для более гладкого результата. [▶ 4:39](https://youtu.be/kDZyYaCgHb8?t=279) — *[2024-04-30](../../recipes/2024-04-30_nxupres-stylised-particle-trails.md)*
- NeXus ▸ **nxUpres**: Source = закешированный base-эмиттер, **Destination** = upres-эмиттер. С настройками по умолчанию зелёные частицы следуют за розовыми закешированными (скорость подмешивается). [▶ 1:29](https://youtu.be/RfvvtXkG8Y0?t=89) — *[2023-07-11](../../recipes/2023-07-11_nxupres-cached-low-res-sim.md)*

## Все рецепты (8)
- 2025-08-14 · [Обзор функций: сплайновые режимы nxFollowGeo, nxUpres по каналам, слои nxSpeed Range](../../recipes/2025-08-14_nxfollowgeo-splines-nxupres-channels-nxspeed-range.md)
- 2025-05-27 · [Детализированный взрыв по полю через upres (nxUpres position + velocity, nxExplode, переключение групп через nxQuestion)](../../recipes/2025-05-27_upres-explode-position-velocity-blend.md)
- 2025-04-29 · [Объёмное облако частиц, окрашенное UV-текстурой объекта (эмиттер с поверхности по текстуре + nxUpres Color + Initial State)](../../recipes/2025-04-29_textured-particle-volume-nxupres-color.md)
- 2025-04-15 · [Upres гранулярной симуляции с сохранением формы (кэш в низком разрешении + смешивание velocity через nxUpres)](../../recipes/2025-04-15_upres-granular-sim-nxupres-velocity.md)
- 2024-04-30 · [Органичный рой частиц-trail'ов из низкополигонального кэша (nxConstraints + nxTurbulence → nxUpres)](../../recipes/2024-04-30_nxupres-stylised-particle-trails.md)
- 2023-07-11 · [Апрез закешированного сима с малым числом частиц в плотный (xpCache + nxUpres Velocity / Position / Push)](../../recipes/2023-07-11_nxupres-cached-low-res-sim.md)
- 2023-06-26 · [Обзор функций: новые модификаторы NeXus — nxUpres, nxInfectio, nxWave, nxAvoid, nxFlock, режимы nxBlend, nxFoam на кэшах, nxWind Von Karman (Fused 2023.3)](../../recipes/2023-06-26_feature-notes-nexus-modifiers-2023-3.md)
- 2023-06-23 · [Обзор функций: X-Particles 2023.3 — живой spawn/foam из кэшей, multi-instances, вращение прилипших частиц, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
