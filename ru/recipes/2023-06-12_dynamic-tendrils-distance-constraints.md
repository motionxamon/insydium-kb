# Извивающиеся щупальца, которые держат констрейнты (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)

- Источник: Maintenance Training — Dynamics - Constraints - Dynamic Tendrils Tutorial — https://www.youtube.com/watch?v=KBktASa5O2o (2023-06-12)
- Хост / поколение: C4D; CPU X-Particles (xpTendril, xpTurbulence, xpConstraints, xpTrail, xpSplineMesher)
- Задача: щупальца под сильной турбулентностью, которые сохраняют форму и не проходят сквозь себя и друг друга.

## Шаги
1. **xpEmitter ▸ Object ▸ Emitter Shape: Defined Emission**, Inline, **Count 1** → одна точка-источник. Display: Circles. [▶ 0:40](https://youtu.be/KBktASa5O2o?t=40)
2. **xpTendril** (Generate modifiers): снять **Scene Length**, Tendril Length **90** кадров. Это непрерывный поток частиц, умирающих на 90-м кадре, который читается как одно щупальце. [▶ 1:35](https://youtu.be/KBktASa5O2o?t=95)
3. **xpTurbulence** для извивания. **xpTrail ▸ Algorithm: Tendrils** connections (а не след от birth-частицы). **xpSplineMesher** по трейлу: Subdivision 1, Size ▸ кривая **Scale Spline**, чтобы сузить конец в точку. [▶ 3:11](https://youtu.be/KBktASa5O2o?t=191)
4. Проблема: при сильной турбулентности частицы на кончике разлетаются, и трейл превращается в прямые отрезки — настройками трейла это не исправить. [▶ 5:03](https://youtu.be/KBktASa5O2o?t=303)
5. Решение: **xpConstraints ▸ Connections ▸ Distance** (birth connections не работают для постоянно новых частиц). Дефолты: радиус **40 cm**, до **8** связей. Для проверки включить Display Constraints. [▶ 5:42](https://youtu.be/KBktASa5O2o?t=342)
6. Настройка: меньше связей (например, 2) — органичнее, но может разнести; больше — жёстче. Дополнительная точность: **Ctrl+D ▸ X-Particles ▸ Subframe Steps 3, Iterations 5** (пробовали и 10). Реально помогло чуть увеличить радиус связей, после чего хватило Iterations 5. [▶ 7:52](https://youtu.be/KBktASa5O2o?t=472)
7. Второе щупальце: скопировать эмиттер Ctrl-перетаскиванием и сдвинуть. Distance-связи соединяют два щупальца → дать каждому эмиттеру свою **группу** и включить в Connections **только одна группа (same group only)**. Дублировать трейл (эмиттер Tendril 2) и добавить оба трейла в Spline Mesher. [▶ 12:45](https://youtu.be/KBktASa5O2o?t=765)
8. Без взаимопроникновения: Constraints ▸ включить **Collisions**. С включённым **Same Emitter** (нужно, чтобы щупальце не проходило сквозь себя) частицы сильно отталкиваются и снова появляются прямые артефакты — лечится добавлением **ещё одной связи**. Friction тоже работает, но гасит энергию, поэтому его оставили выключенным. [▶ 15:20](https://youtu.be/KBktASa5O2o?t=920)

## Подводные камни
- С выключенным Same Emitter щупальца сталкиваются друг с другом, но могут проходить сами сквозь себя.

## Как сейчас (новые инструменты)
**nxDendrite** (branches/network) и nxSpawn — инструменты роста в NeXus; **nxConstraints** (Distance connections + слой Collisions) и **nxTrail** + **nxMesher** закрывают остальное на GPU. Для формирования потоков — **nxWarp** Path/Helix (бета 2026.1).
