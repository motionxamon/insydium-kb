# nxSpeed — карточка инструмента

Встречается в **21** рецептах · 2023-04-13 → 2026-08-25 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxSpeed** ▸ дефолтный слой Incremental с **отрицательным** значением (**−0.04**) + вариация → мягкое торможение. [▶ 1:09](https://youtu.be/I2ERiN8Vk2Q?t=69) — *[2026-08-25](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)*
- **nxSpeed** **последним** в стеке: слой Incremental со скоростью **0** — только как ограничитель, **Min 0.5, Max 4**. [▶ 6:17](https://youtu.be/na6NGPw4XWM?t=377) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*
- **Export Tags ▸ Transfer Velocity**, max speed **4** в каждом поле (совпадает с ограничением nxSpeed) → атрибут скорости вершин на меше. [▶ 14:58](https://youtu.be/na6NGPw4XWM?t=898) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*
- **nxSpeed** *ниже* турбулентности → слой **Range**: Speed Start 0 / End 300 на 0–60 кадрах. **Переверните ease-кривую**, чтобы старт был на полной скорости (300), а конец на 0 → вылет и остановка с плавным замедлением. [▶ 3:20](https://youtu.be/HvX6qaVei1o?t=200) — *[2026-03-31](../../recipes/2026-03-31_nxspeed-range-organic-stop.md)*
- **nxSpeed**: Incremental +0, **Max speed ~65** (успокаивает). [▶ 4:24](https://youtu.be/D8XcG_EuvG8?t=264) — *[2025-07-15](../../recipes/2025-07-15_dynamic-sand-flowfield-spline.md)*
- **nxSpeed** последним: Incremental 0, **Max speed 150**. [▶ 6:45](https://youtu.be/v63KTwt6pI4?t=405) — *[2025-06-24](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)*
- Успокаиваем: **nxSpeed** ниже турбулентности, Accelerate с **Force 0**, **Max Speed 80 cm** — турбулентность сильная, но скорость ограничена. [▶ 2:34](https://youtu.be/RUhF1pju3Wk?t=154) — *[2025-05-06](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)*
- Усмирить края: **nxSpeed** после ветра, операция **Acceleration** с exponential 0 (ничего не делает) + **Clamp Max Speed 500 cm**. [▶ 33:00](https://youtu.be/V4mwAf8tcLk?t=1980) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- **nxSpeed** последним в стеке: Operation Acceleration со значением **0**, включите **Clamp Max Speed** ~400 cm. [▶ 4:22](https://youtu.be/PYtRwy_bbCE?t=262) — *[2024-12-31](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)*
- nxSpeed ▸ **Mapping ▸ Radius map** (диапазон 0–3 cm) → параметр **Clamp Max Speed**; у мелких искр ниже предел скорости. Приподнимите нижний край кривой, чтобы они никогда полностью не останавливались. [▶ 5:16](https://youtu.be/PYtRwy_bbCE?t=316) — *[2024-12-31](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)*
- **nxTurbulence** *над* nxSpeed (чтобы ограничение побеждало): Curl, сильная, низкий persistence, больше octaves → крупные волнистые завихрения. Предел скорости до ~500. [▶ 6:34](https://youtu.be/PYtRwy_bbCE?t=394) — *[2024-12-31](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)*
- Порядок в стеке: **nxTurbulence → nxPush → nxSpeed**. — *[2024-11-12](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)*
- - nxSpeed: **Incremental −25** → постепенное замедление. — *[2024-11-12](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)*
- Варианты: turbulence Voronoi, больше octaves, низкий persistence; **nxSpeed** (без ускорения) **max 50** при очень сильной турбулентности → медленно меняющиеся узоры. [▶ 6:44](https://youtu.be/tantnHiZWE4?t=404) — *[2024-10-22](../../recipes/2024-10-22_instance-emitters-kaleidoscope.md)*

## Подводные камни
- Если оставить nxSpeed Incremental по умолчанию, частицы будут постоянно ускоряться. — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*

## Все рецепты (21)
- 2026-08-25 · [Шлейфы «взрыв-цветок» с толщиной от скорости и цветом по вершинам (nxTrail, nxScale + маппинг скорости в nxTurbulence)](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)
- 2026-07-06 · [Усики из слоёной curl-турбулентности (слои nxTurbulence Curl + FBM + Voronoi, привязка к возрасту по слоям, ограничение nxSpeed, плавное появление через nxScale)](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)
- 2026-06-18 · [Струя жидкости, бегущая по кругу вдоль кривой, мешинг с motion blur (сплайн nxFollowGeo + nxFluids PBD + nxMesher Transfer Velocity)](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)
- 2026-06-09 · [Случайная ориентация при рождении + повторяемые обороты на 360° (nxSpin + сброс возраста)](../../recipes/2026-06-09_advanced-spin-control.md)
- 2026-03-31 · [Выброс частиц с плавной органичной остановкой (nxSpeed Range + curl-турбулентность)](../../recipes/2026-03-31_nxspeed-range-organic-stop.md)
- 2026-02-17 · [Перекраска закэшированных частиц через nxColor (и ограничение скорости по цвету)](../../recipes/2026-02-17_recolor-after-cache.md)
- 2025-08-14 · [Обзор функций: сплайновые режимы nxFollowGeo, nxUpres по каналам, слои nxSpeed Range](../../recipes/2025-08-14_nxfollowgeo-splines-nxupres-channels-nxspeed-range.md)
- 2025-07-15 · [Песок, который собирается в форму сплайна (гранулярный SPH + слой To-Spline в xpFlowField)](../../recipes/2025-07-15_dynamic-sand-flowfield-spline.md)
- 2025-06-24 · [Самоподдерживающийся цикл частиц: рост / расталкивание / уменьшение (nxAttract + nxPush + поле в nxQuestion + nxRotate через mapping)](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)
- 2025-05-06 · [Проявление wireframe частицами (nxFollowGeo в режиме Edge + nxTurbulence + ограничение nxSpeed)](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)
- 2025-04-30 · [Процедурное рассыпание песочного бюста (nxFluids SPH Granular + группы через nxColor/nxQuestion + nxWind Von Karman + зерно с mapping по дистанции)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2024-12-31 · [Искры фейерверка от рукописного текста (nxScale + убийство через nxQuestion + ограничение nxSpeed, замапленное на Radius)](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)
- 2024-11-12 · [Распускающийся цветок из трейлов (nxTurbulence Curl Blend/Add по возрасту + сила по скорости)](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)
- 2024-10-22 · [Клонирование и отражение эмиттеров для калейдоскопа (режим Instance у xpEmitter + MoGraph Cloner)](../../recipes/2024-10-22_instance-emitters-kaleidoscope.md)
- 2024-07-23 · [Самопорождающиеся сети частиц внутри объёма (поиск соседей в nxQuestion + Spawn, удаление по объёму)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-07-16 · [Лава, которая застывает и снова плавится (цвет от анимированного поля Random → замапленные сила nxWind + максимальная скорость nxSpeed, nxFluids)](../../recipes/2024-07-16_lava-flow-color-mapped-wind-speed.md)
- 2024-06-11 · [Статуя рассыпается в песок по мере распространения заражения (группы nxInfectio + nxFluids SPH Granular + nxSpeed Max Speed 0)](../../recipes/2024-06-11_granular-crumble-infectio-groups.md)
- 2023-12-26 · [Естественный падающий снег (ограничение nxSpeed, замапленное на радиус + второй nxTurbulence Curl с Blend, замапленным на радиус)](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)
- 2023-07-05 · [Горячая/холодная жидкость с переменной вязкостью на голову волка (nxFluids SPH + nxConstraints Viscosity + nxQuestion object distance + nxBlend + nxSpeed clamp с mapping по цвету)](../../recipes/2023-07-05_variable-viscosity-wolf-nxspeed-clamp-part-b.md)
- 2023-04-19 · [Интерактивный риг плавления / застывания на цвете частиц (mapping Clamp Max Speed в nxSpeed + nxQuestion с fields + nxBlend + mapping вязкости SPH)](../../recipes/2023-04-19_nexus-heat-cool-melt-rig-nxquestion-mapping-part-c.md)
- 2023-04-13 · [Кристалл, который осыпается по осколку (xpShatter + emitter, xpQuestion Inside Volume, mapped xpSpeed/xpRotator/xpSpin, xpFreeze)](../../recipes/2023-04-13_crystal-shatter-xpshatter-question-driven-breakup-part-a.md)
