# Органичный рой частиц-trail'ов из низкополигонального кэша (nxConstraints + nxTurbulence → nxUpres)

- Источник: Top Tip Tuesday — NeXus Particle Trails — https://www.youtube.com/watch?v=kDZyYaCgHb8 (2024-04-30)
- Хост / поколение: C4D; NeXus внутри X-Particles (G2: xpEmitter + nxConstraints, nxTurbulence, nxUpres) + xpCache
- Задача: использовать nxUpres как стилистический инструмент, а не только для разрешения — цельное, похожее на ленты тело из trail'ов вместо разбросанных noise'ом точек.

## Исходная сцена
Сфера с **Vibrate tag** (равномерная пульсация, амплитуда по X) как источник эмиттера; xpEmitter в режиме Object, по площади полигонов; Rate 50/кадр, lifespan 60, speed 0. **Motion Inheritance** вкл, Speed Blend 50 — единственный источник движения.

## Шаги
1. **nxConstraints**: Iterations 3; слой **Birth** — до 13 связей в радиусе 30, очень низкая жёсткость (тянущиеся), **Break Type: None**. Теперь частицы движутся единым телом.
2. **nxTurbulence** Voronoi: сильная, scale поменьше, очень низкая frequency, octaves сильно выше; затем **понизьте Persistence**, чтобы вернуть крупные завихрения, потерянные из-за высоких octaves.
3. **xpCache** во внешние файлы с **Compress Cache on Build выкл** (быстрее сборка, больше файлы). ~700 F кэшируются за секунды. По желанию после кэширования удалите/отключите модификаторы.
4. Дублируйте эмиттер как **destination** (уберите его кэш): lifespan 40 (var 10), Rate 1000, display Dots, цвет **Gradient Parameter** по Speed.
5. **nxUpres**: Source = закэшированный эмиттер, Destination = новый эмиттер. Particles-to-blend по умолчанию 3 ближайших (velocity blend); поднято до ~7 для более гладкого результата.
6. Включите также блендинг **Position** — на полной силе симуляция схлопывается внутрь; снизьте его strength, чтобы вернуть объём.
7. Поднимите Rate у destination 1000 → 5000 и пересоберите кэш с **Continue**, чтобы закэшированные базовые частицы не пересчитывались (≈5 мин в демо).

## Подводные камни
- Без Continue кэш пытается пересобрать и базовую симуляцию.
- Больше blend count = глаже, но медленнее.

## Как сейчас (новые инструменты)
Тот же workflow с nxUpres в NeXus 2026 (nxEmitter + nxCache, C4D 2026.1 beta / Blender). nxTrail может превратить upres'нутые частицы в сплайны.
