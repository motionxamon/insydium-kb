# nxAttract — карточка инструмента

Встречается в **13** рецептах · 2023-11-16 → 2026-06-30 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxAttract**: Force 300, Acceleration 3000, **Speed Limit 250**. [▶ 1:21](https://youtu.be/v63KTwt6pI4?t=81) — *[2025-06-24](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)*
- nxAttract ▸ Fields: та же сфера + модификатор **Invert** → притяжение только вне ядра. [▶ 5:25](https://youtu.be/v63KTwt6pI4?t=325) — *[2025-06-24](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)*
- Держим направление +Z: **nxAttract** с целью впереди потока, Mode **Velocity**, Acceleration **10**, Speed Limit **400**, Force **50**. [▶ 1:25](https://youtu.be/K2Jb2lxzgSY?t=85) — *[2025-05-08](../../recipes/2025-05-08_c4d-deformers-twist-spline-wrap-particles.md)*
- Арт-дирекшн: **nxAttract** между турбулентностью и скоростью; двигайте его, чтобы управлять направлением потока. [▶ 3:40](https://youtu.be/RUhF1pju3Wk?t=220) — *[2025-05-06](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)*
- По умолчанию выпадающая иконка показывает последний использованный инструмент; выберите нужную иконку (например inset-иконку для MeshTools, nxAttract для NeXus), ПКМ ▸ **Lock Icon**. [▶ 6:10](https://youtu.be/jzFk-veno5U?t=370) — *[2025-02-27](../../recipes/2025-02-27_custom-tool-palettes-c4d.md)*
- **nxAttract** под nxScale, режим **Object**, кидаем туда Matrix → каждая точка Matrix становится отдельной целью; каждая частица летит к **ближайшей** точке. Отображение цели выключаем. [▶ 4:28](https://youtu.be/nJpItCX8GlY?t=268) — *[2024-07-30](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)*
- **nxAttract** на машину: режим **Force** (лучше, чем Velocity, когда смешиваете модификаторы), Force ~200. [▶ 3:47](https://youtu.be/BGuwXsKofbo?t=227) — *[2024-03-26](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)*
- Ограничьте nxAttract **Box field** вокруг машины (с небольшим внутренним falloff), чтобы частицы не скапливались, когда уже проехали её. [▶ 3:57](https://youtu.be/BGuwXsKofbo?t=237) — *[2024-03-26](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)*
- Принцип **nxAttract**: притяжение vs **Speed Limit** vs инерция частиц. Лимит по умолчанию 250; при 1000 частицы улетают далеко, прежде чем развернуться. [▶ 38:33](https://youtu.be/qaso-gPGBnI?t=2313) — *[2023-11-16](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)*

## Подводные камни
- Без поля nxAttract заставляет частицы скапливаться вокруг цели. — *[2024-03-26](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)*

## Все рецепты (13)
- 2026-06-30 · [Запуск/остановка зацикленной анимации nxQuestion через action Break](../../recipes/2026-06-30_nxquestion-action-break.md)
- 2026-06-15 · [Цвет частиц в рендере Cycles и Eevee (экспорт Point Cloud из nxEmitter + атрибуты Geometry Nodes)](../../recipes/2026-06-15_blender-particle-color-to-render.md)
- 2026-05-19 · [Пульсация скорости / размера частиц через nxQuestion Math ▸ Wave](../../recipes/2026-05-19_nxquestion-sine-wave-pulsing.md)
- 2025-10-16 · [Обзор функций: GPU nxExplosiaFX (Fused 2025 Tech Preview)](../../recipes/2025-10-16_feature-notes-nxexplosiafx-tech-preview.md)
- 2025-06-24 · [Самоподдерживающийся цикл частиц: рост / расталкивание / уменьшение (nxAttract + nxPush + поле в nxQuestion + nxRotate через mapping)](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)
- 2025-05-08 · [Лента частиц, обёрнутая вокруг сплайна деформерами C4D (Spline Wrap + Twist на xpEmitter)](../../recipes/2025-05-08_c4d-deformers-twist-spline-wrap-particles.md)
- 2025-05-06 · [Проявление wireframe частицами (nxFollowGeo в режиме Edge + nxTurbulence + ограничение nxSpeed)](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)
- 2025-02-27 · [Пристыкованные палитры для инструментов INSYDIUM (C4D Command Manager, отрывные подменю, Lock Icon)](../../recipes/2025-02-27_custom-tool-palettes-c4d.md)
- 2024-07-30 · [Точки MoGraph Matrix как движущиеся цели притяжения (nxAttract в режиме Object + nxPush + age map в nxScale)](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)
- 2024-03-26 · [Стилизованные линии потока аэротрубы вокруг машины (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2024-02-06 · [Органичный колышущийся шипастый шар (mtSubdivider + mtInset на soft body через xpDynamics)](../../recipes/2024-02-06_meshtools-xpdynamics-soft-body.md)
- 2023-11-16 · [Астероиды на орбитах планет + расползающееся свечение (nxAttract Force/Speed Limit, xpColor с полями из частиц, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-11-16 · [Кристаллы, прорастающие вдоль замерших путей частиц (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
