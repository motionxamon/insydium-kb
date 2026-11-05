# Стилизованные линии потока аэротрубы вокруг машины (nxAvoid + nxAttract + nxDirection + xpTrail)

- Источник: Top Tip Tuesday — NeXus Wind Tunnel — https://www.youtube.com/watch?v=BGuwXsKofbo (2024-03-26)
- Хост / поколение: C4D; NeXus GPU (nxAvoid, nxAttract, nxDirection) на xpEmitter + CPU xpOpenVDBMesher, xpJoin, xpTrail
- Задача: частицы-стрелки обтекают кузов машины и оставляют аэродинамические линии-шлейфы.

## Исходная сцена
xpEmitter в режиме Rate, lifespan 200, 60 частиц/с, speed 240, отображение Arrow. Машина = множество объектов в null под **xpJoin**.

## Шаги
1. Лоупольный дамми: **xpOpenVDBMesher** с xpJoin; в записи объекта поставьте режим меша **Surface → Points**; **Voxel size 6**; фильтры: удалите Median по умолчанию, добавьте **Curvature** (несколько итераций) + **Offset** (сжимайте, пока настоящая машина не начнёт чуть проступать). **C** — сделать редактируемым, назовите «dummy car», скройте.
2. **nxAvoid** с дамми-машиной, режим по умолчанию **Change Direction**.
3. Эмиттер **Extended Data ▸ Rotation: Tangential**, чтобы стрелки смотрели по направлению движения.
4. **nxAttract** на машину: режим **Force** (лучше, чем Velocity, когда смешиваете модификаторы), Force ~200.
5. Ограничьте nxAttract **Box field** вокруг машины (с небольшим внутренним falloff), чтобы частицы не скапливались, когда уже проехали её.
6. **nxDirection**: по умолчанию берёт поворот модификатора и толкает вдоль его **+Z** — выпрямляет поток на выходе. Снизьте силу для большей вариативности.
7. **xpTrail** (по умолчанию) на эмиттер → линии-шлейфы.

## Подводные камни
- Без поля nxAttract заставляет частицы скапливаться вокруг цели.

## Как сейчас (новые инструменты)
Те же модификаторы в NeXus 2026 (nxEmitter + nxTrail); для направления потоков — **nxWarp Wind gust / Path** (2026.1 beta) или nxFollowGeo.
