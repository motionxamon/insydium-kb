# nxScale — карточка инструмента

Встречается в **26** рецептах · 2023-03-29 → 2026-09-15 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Анимация радиуса: radius эмиттера 0; слой **nxScale** **Set Value** 0.05, вариация 60%, **Clamp to Radius Limit off**; Mapping ▸ карта Speed → **Radius Value**, диапазон 0–3.5; приподними нижний край кривой, чтобы медленные частицы сохраняли немного ширины → шлейфы сужаются, но не исчезают. [▶ 10:34](https://youtu.be/I2ERiN8Vk2Q?t=634) — *[2026-08-25](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)*
- Плавное появление края эмиссии: отображение **Circles Filled** (Points игнорируют радиус); **nxScale ▸ Range**: радиус от 0 → до ~0.001 (0.01 для тестов во viewport), за 8 кадров с вариацией 50%; дольше (например 25 кадров) = мягче растушёвка. Пропустите, если форма эмиссии (логотип/текст) должна читаться чётко. [▶ 17:36](https://youtu.be/U937aVtRzMA?t=1056) — *[2026-07-06](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)*
- **nxScale** (слоистый, с режимами смешивания) ▸ слой **Range** по умолчанию: Start Radius **0**, End Radius **1 m**, время **0 → 100 кадров**; добавьте вариацию к конечному радиусу и/или таймингу. [▶ 2:46](https://youtu.be/o7b5SV4BqfM?t=166) — *[2026-06-08](../../recipes/2026-06-08_blender-nxscale-range-ease-curve.md)*
- Слой **nxScale** Range: radius 0 → End 60 cm с большой вариацией. [▶ 7:21](https://youtu.be/5OHld9QtCzI?t=441) — *[2026-05-05](../../recipes/2026-05-05_random-groups-scale-mapping.md)*
- **nxScale Range**: ось Y = Radius Start→End, ось X = время Start→End; рисуем кривую вверх, затем вниз → частица растёт и уменьшается за время жизни. [▶ 6:02](https://youtu.be/THuXYZmNZjQ?t=362) — *[2026-04-28](../../recipes/2026-04-28_nxscale-range-spawn-fade.md)*
- **nxScale** ▸ Object: **Set Value**, Radius **60 cm**. [▶ 1:12](https://youtu.be/AMCR5ciL7fw?t=72) — *[2025-04-24](../../recipes/2025-04-24_nexus-data-mapping-age-group-curves.md)*
- **nxScale** под гравитацией: отрицательное изменение во времени (Min −0.2, много вариации), **Clamp Limit выкл.** → искры уменьшаются до нуля. [▶ 2:52](https://youtu.be/PYtRwy_bbCE?t=172) — *[2024-12-31](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)*
- Анимированная ширина: **nxScale** Set by Falloff с тем же random-полем; radius эмиттера 200, без вариации; xpTrail Thickness **Use Radius Variable** → ширина прорисовывается вдоль шлейфа. [▶ 5:39](https://youtu.be/Lx6Sugl11TA?t=339) — *[2024-12-10](../../recipes/2024-12-10_trail-thickness-from-radius.md)*
- Вместо этого спавните с radius 0, затем **nxScale ▸ Value over time**, небольшой rate + variation, clamp **0 → 1.5** → частицы растут после рождения. [▶ 5:27](https://youtu.be/WTMgHpdgOhY?t=327) — *[2024-09-17](../../recipes/2024-09-17_taiao-volume-branch-particle-network.md)*
- **nxScale** (под nxPush — порядок важен): **Set Value** radius 3, **Mapping ▸ Age** 0→80 F на радиус; кривая быстро растёт от 0 до максимума, затем уменьшается к 80 F. [▶ 1:41](https://youtu.be/nJpItCX8GlY?t=101) — *[2024-07-30](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)*
- Ставим радиус эмиттера в **0**, чтобы размером целиком управлял nxScale (иначе частицы появляются сразу с 3 cm). [▶ 1:52](https://youtu.be/nJpItCX8GlY?t=112) — *[2024-07-30](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)*
- **nxAttract** под nxScale, режим **Object**, кидаем туда Matrix → каждая точка Matrix становится отдельной целью; каждая частица летит к **ближайшей** точке. Отображение цели выключаем. [▶ 4:28](https://youtu.be/nJpItCX8GlY?t=268) — *[2024-07-30](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)*
- Оба радиуса spawn поставь в **0**; отображение — залитые круги по радиусу. **nxScale** change-over-time (медленно), вариация 5%, **Clamp to radius limit** + **within range**, max **1 cm**. [▶ 4:12](https://youtu.be/nC1YyRrwY2g?t=252) — *[2024-07-23](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)*
- **nxScale**: операция **Set by Falloff**, clamping выкл.; Fields ▸ **Random field** — жёлтый = радиус 0, красный = максимальный радиус эмиттера (6). [▶ 2:51](https://youtu.be/IuaZtmg5O8o?t=171) — *[2024-04-09](../../recipes/2024-04-09_nxpush-2d-radius-animation.md)*

## Все рецепты (26)
- 2026-09-15 · [Рендер данных частиц NeXus в Octane (цвет, радиус → стекло)](../../recipes/2026-09-15_octane-particle-data.md)
- 2026-08-25 · [Шлейфы «взрыв-цветок» с толщиной от скорости и цветом по вершинам (nxTrail, nxScale + маппинг скорости в nxTurbulence)](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)
- 2026-07-06 · [Усики из слоёной curl-турбулентности (слои nxTurbulence Curl + FBM + Voronoi, привязка к возрасту по слоям, ограничение nxSpeed, плавное появление через nxScale)](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)
- 2026-06-23 · [Пузыри внутри вязкой FLIP-жидкости (поиск соседей)](../../recipes/2026-06-23_viscous-bubble-rig.md)
- 2026-06-15 · [Цвет частиц в рендере Cycles и Eevee (экспорт Point Cloud из nxEmitter + атрибуты Geometry Nodes)](../../recipes/2026-06-15_blender-particle-color-to-render.md)
- 2026-06-09 · [Случайная ориентация при рождении + повторяемые обороты на 360° (nxSpin + сброс возраста)](../../recipes/2026-06-09_advanced-spin-control.md)
- 2026-06-08 · [Анимация размера частиц через слой Range и его ease-кривую (nxScale Range)](../../recipes/2026-06-08_blender-nxscale-range-ease-curve.md)
- 2026-05-05 · [Немного крупных, много мелких: случайные подгруппы + nxScale с маппингом по группе](../../recipes/2026-05-05_random-groups-scale-mapping.md)
- 2026-04-28 · [Заспавненные частицы, которые органично растут и исчезают (кривая nxScale Range + kill)](../../recipes/2026-04-28_nxscale-range-spawn-fade.md)
- 2026-03-31 · [Выброс частиц с плавной органичной остановкой (nxSpeed Range + curl-турбулентность)](../../recipes/2026-03-31_nxspeed-range-organic-stop.md)
- 2025-09-11 · [Обзор функций: переписанное GPU-ядро NeXus, GPU falloffs + Data Mapping на каждом слое, вариации в nxQuestion и поиск соседей](../../recipes/2025-09-11_nexus-core-falloffs-mapping-question-variations.md)
- 2025-07-03 · [Обзор функций: слоёный nxTurbulence, nxScale и новый nxLimit (превью Fused 2025, часть 1)](../../recipes/2025-07-03_feature-notes-layered-nxturbulence-nxscale-nxlimit.md)
- 2025-04-24 · [Как читать кривую Data Mapping: радиус по возрасту и по группе (nxScale ▸ Mapping)](../../recipes/2025-04-24_nexus-data-mapping-age-group-curves.md)
- 2024-12-31 · [Искры фейерверка от рукописного текста (nxScale + убийство через nxQuestion + ограничение nxSpeed, замапленное на Radius)](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)
- 2024-12-10 · [Шлейфы, толщина которых следует за радиусом частиц (xpTrail Thickness: Use Radius Variable → кривые Redshift)](../../recipes/2024-12-10_trail-thickness-from-radius.md)
- 2024-09-17 · [Непересекающиеся ветки из частиц внутри меша (Taiao toTree volume points → spline emitter, nxQuestion Spawn, nxPush, nxScale)](../../recipes/2024-09-17_taiao-volume-branch-particle-network.md)
- 2024-07-30 · [Точки MoGraph Matrix как движущиеся цели притяжения (nxAttract в режиме Object + nxPush + age map в nxScale)](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)
- 2024-07-23 · [Самопорождающиеся сети частиц внутри объёма (поиск соседей в nxQuestion + Spawn, удаление по объёму)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-07-09 · [Радиус частиц управляет цветом и свечением в Redshift (Scalar User Data ▸ Change Range ▸ Ramp / Scalar Ramp)](../../recipes/2024-07-09_redshift-particle-size-color-emission.md)
- 2024-04-09 · [Психоделические плоские паттерны расталкивания (nxPush + фиксация скорости через nxQuestion + nxScale по полю)](../../recipes/2024-04-09_nxpush-2d-radius-animation.md)
- 2024-02-27 · [Расходящаяся физическая цепная реакция (nxConstraints Birth + Collisions, nxScale/nxGravity с маппингом на Distance Travelled)](../../recipes/2024-02-27_nxconstraints-chain-reaction.md)
- 2023-11-16 · [Кристаллы, прорастающие вдоль замерших путей частиц (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-10-24 · [Рост с разной скоростью, уменьшение с возрастом, затем смерть (nxScale Clamp within Range + Age map на Upper Radius Limit + kill через nxQuestion)](../../recipes/2023-10-24_nxscale-random-growth-age-mapped-shrink.md)
- 2023-08-29 · [Частицы растут и меняют цвет внутри поля, а снаружи возвращаются обратно (nxQuestion Field question, Set Color / Set Radius, Else)](../../recipes/2023-08-29_nxquestion-field-color-radius.md)
- 2023-06-08 · [Фейковая тягучая жидкость, ползущая по логотипу (xpConstraints Forces, xpCover, Data Mapping по radius/age/temperature, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-03-29 · [Дым разрывает песочную цифру без дыр (advection в xpExplosiaFX, xpFlowField, заполнение xpSpawn, xpScale + kill через Question)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
