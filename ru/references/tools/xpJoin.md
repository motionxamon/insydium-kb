# xpJoin — карточка инструмента

Встречается в **17** рецептах · 2023-04-14 → 2025-11-04 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Параметрические сферы внутри **xpJoin**; эмиттер Object = join, **Offset Origin 3 cm**, Polygon Area, **Shot 60 000**, скорость 0, **radius 0** (отображение Squares игнорирует радиус). [▶ 0:39](https://youtu.be/Xe1seJC3g0k?t=39) — *[2025-11-04](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)*
- Клонеры MoGraph с городом внутри **xpJoin**. Object эмиттера = join, **Emit From Edges**, **Shot 200 000**, speed 0, чёрные частицы. [▶ 1:06](https://youtu.be/veRxUHtrnFA?t=66) — *[2025-10-14](../../recipes/2025-10-14_city-lights-edge-infection.md)*
- Alt + **xpJoin** над null'ом меша → части тела становятся одним объектом. [▶ 1:24](https://youtu.be/Qd_kEHZ-4JY?t=84) — *[2025-08-12](../../recipes/2025-08-12_mocap-pla-emission.md)*
- Решение: ПКМ по xpJoin ▸ **Bake as Alembic** → это всё ещё генератор, всё ещё отстаёт → перетащите в Timeline Dope Sheet ▸ Functions ▸ **Bake Objects** с **Create Copy + PLA** → полигональный объект с анимацией на уровне точек. [▶ 4:30](https://youtu.be/Qd_kEHZ-4JY?t=270) — *[2025-08-12](../../recipes/2025-08-12_mocap-pla-emission.md)*
- Поместите плоскость в **X-Particles ▸ Utilities ▸ xpJoin**; выключите **Hide Source**, чтобы снова видеть веса. [▶ 1:17](https://youtu.be/yAZ7aY8Ed4Y?t=77) — *[2025-04-10](../../recipes/2025-04-10_vertex-map-emission-density.md)*
- Спрячьте low-poly камни-коллайдеры (xpJoin); покажите high-res tfRocks; один шершавый материал на их null, тёмно-красный приглушённый. [▶ 11:03](https://youtu.be/hK1BxHqw4QU?t=663) — *[2024-11-04](../../recipes/2024-11-04_redshift-additive-foam-aces-after-effects-part-2.md)*
- Дешёвые коллайдеры камней: Ctrl-перетаскиванием скопируйте null с tfRock в Utilities, спрячьте high-res набор, у копии снизьте **Subdivisions tfRock до 1** (форма та же, полигонов в разы меньше). Положите копию в **xpJoin** и повесьте на join один тег xpCollider (Bounce 0). [▶ 7:26](https://youtu.be/_W2ivetBEPo?t=446) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- **xpJoin** с растением и цветком в качестве дочерних; у xpEmitter Object = join, **Polygon Area**. [▶ 1:58](https://youtu.be/ZgUIL-udXks?t=118) — *[2024-05-28](../../recipes/2024-05-28_taiao-flower-stamen-pollen-emission.md)*
- Лоупольный дамми: **xpOpenVDBMesher** с xpJoin; в записи объекта поставьте режим меша **Surface → Points**; **Voxel size 6**; фильтры: удалите Median по умолчанию, добавьте **Curvature** (несколько итераций) + **Offset** (сжимайте, пока настоящая машина не начнёт чуть проступать). **C** — сделать редактируемым, назовите «dummy car», скройте. [▶ 1:22](https://youtu.be/BGuwXsKofbo?t=82) — *[2024-03-26](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)*
- Ответвления могут целиться только в геометрию: **xpSprite** (Cube) на конечном эмиттере внутри **xpJoin**; слой Fork ▸ connect to **Custom Object** = этот join. Скройте join и частицы. [▶ 4:24](https://youtu.be/sctuPLrOw60?t=264) — *[2024-01-16](../../recipes/2024-01-16_mtsplinefx-lightning.md)*
- **tfTrace** (высота по объектам через трассировку лучей): object = xpJoin. [▶ 1:40](https://youtu.be/jQlOjJUVaoI?t=100) — *[2023-11-21](../../recipes/2023-11-21_tftrace-text-landscape-reveal.md)*
- Тег **xpCollider** на terrain sim (Bounce 0, Friction 0). Ступени и камни — каждые в свой **xpJoin** (один тег коллайдера на join); у камней Bounce 10, Friction 5. Цвет отображения всех коллайдеров — чёрный. [▶ 6:29](https://youtu.be/t-1ZIIRF8Jg?t=389) — *[2023-11-20](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)*
- Террейны-генераторы нужно обернуть в **xpJoin**, чтобы использовать их как поверхность (по одному join на каждый sim-террейн). [▶ 7:06](https://youtu.be/yqfkRKgW1Mo?t=426) — *[2023-11-16](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)*
- Несколько поверхностей: Utilities ▸ **xpJoin**, пипеткой выберите Кайдзю, утку и плоскость, затем перенесите единственный xpCollider tag на xpJoin — один тег управляет всем. [▶ 5:19](https://youtu.be/x1SAOjOSOzs?t=319) — *[2023-08-22](../../recipes/2023-08-22_rain-rig-collider-spawn-splashes.md)*

## Подводные камни
- Объекты-генераторы (TF terrain) нужно положить в xpJoin, иначе xpFollowSurface их не примет. — *[2023-11-16](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)*

## Все рецепты (17)
- 2025-11-04 · [Частицы, распускающиеся в щелях геометрии (соседи в nxQuestion + поле)](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)
- 2025-10-14 · [Огни города, расползающиеся по рёбрам зданий (nxInfectio + группы)](../../recipes/2025-10-14_city-lights-edge-infection.md)
- 2025-08-12 · [Чистая эмиссия частиц с mocap-персонажа (xpJoin → Alembic → запекание PLA)](../../recipes/2025-08-12_mocap-pla-emission.md)
- 2025-04-10 · [Плотность эмиссии по процедурной vertex map (Vertex Map + Linear field ▸ xpJoin ▸ xpEmitter Selection)](../../recipes/2025-04-10_vertex-map-emission-density.md)
- 2024-11-04 · [Рендер пены с цветом по скорости как аддитивного свечения в Redshift, ACEScg в After Effects + speed ramps (Color User Data → Ramp → Geometry Opacity)](../../recipes/2024-11-04_redshift-additive-foam-aces-after-effects-part-2.md)
- 2024-11-01 · [Бурлящая закрученная вода, видимая только через пену (nxFluids + nxVorticity с Force Limit + анимированный nxRotate → nxFoam с цветом по скорости)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-07-23 · [Самопорождающиеся сети частиц внутри объёма (поиск соседей в nxQuestion + Spawn, удаление по объёму)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-05-28 · [Пыльца с кончиков тычинок цветка Taiao (custom object в tiPlant, xpJoin, выделение слоя, nxWind)](../../recipes/2024-05-28_taiao-flower-stamen-pollen-emission.md)
- 2024-03-26 · [Стилизованные линии потока аэротрубы вокруг машины (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2024-01-16 · [Процедурная ветвящаяся молния с искрами (mtSplineFX + xpSplineMesher + xpSpawn)](../../recipes/2024-01-16_mtsplinefx-lightning.md)
- 2023-11-21 · [Логотип/текст из ландшафта, который вырастает в кадре (tfTrace + tfBlur + эрозия Snow + маскированный noise + tfAdjustment с linear field)](../../recipes/2023-11-21_tftrace-text-landscape-reveal.md)
- 2023-11-20 · [Режиссируемые slow-mo всплески частиц над ступенями и песком (nxFluids SPH, скрытые tfRock-«отбойники», xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-11-16 · [Кристаллы, прорастающие вдоль замерших путей частиц (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-08-22 · [Риг дождя с брызгами (xpCollider Spawn при столкновении, xpJoin для нескольких коллайдеров)](../../recipes/2023-08-22_rain-rig-collider-spawn-splashes.md)
- 2023-05-30 · [Тягучая жидкость без флюидного солвера (пружины nxConstraints при рождении → алгоритм xpTrail Constraints → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-04-20 · [Цвет по скорости и подложка жидкости, деформированная океаном (Gradient Parameter по Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)
- 2023-04-14 · [Струйки частиц, вырывающиеся из разрушающегося кристалла (cached xpShatter, xpExplosiaFX Source tag, Advection, эмиссия с внутренних граней, xpJoin collider)](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)
