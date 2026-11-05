# nxPush — карточка инструмента

Встречается в **25** рецептах · 2023-02-21 → 2026-10-13 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxPush**: mode **Particle Radius**, сила на максимум → сферы при росте расталкивают друг друга. [▶ 7:23](https://youtu.be/rDSSeIZUl08?t=443) — *[2025-11-06](../../recipes/2025-11-06_wired-growth-spline-mesh-vertex-map.md)*
- **nxPush** в режиме Particle Radius, сильный → выросшие частицы расталкивают друг друга. [▶ 5:28](https://youtu.be/Xe1seJC3g0k?t=328) — *[2025-11-04](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)*
- **nxPush** в режиме Particle Radius, полная сила, 10 итераций. [▶ 4:36](https://youtu.be/PTamR793O-k?t=276) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- …поэтому используй у коллайдера **вкладку Forces → Attraction**, Radius 100 cm, strength ~59 → частицы прижимаются к поверхности и при этом расталкиваются. (Не сочетай nxFollowGeo + nxPush — силы противоречат друг другу.) [▶ 6:19](https://youtu.be/PTamR793O-k?t=379) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- **nxPush**: режим Distance **Particle Radius**, strength 100%, итераций ~20. [▶ 1:49](https://youtu.be/v63KTwt6pI4?t=109) — *[2025-06-24](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)*
- **nxPush**: Distance = **Particle Radius**, Strength 100, **Iterations 1000**. Под ним **nxKill**, Volume = Objects ▸ куб пола, Inside → убивает зёрна, вдавленные в пол. [▶ 24:39](https://youtu.be/fxJI8py9BzU?t=1479) — *[2025-05-07](../../recipes/2025-05-07_granular-collapse-sand-snow.md)*
- Сломать hex-сетку: **отключите коллайдер**, в эмиссии **Jitter X/Y/Z = 0.225** (≤ радиуса), затем **nxPush** Particle Radius, полная сила, тысячи итераций (≈3 мин на кадр 1), чтобы убрать пересечения; потом **nxKill** box (size 100, Y −100, чтобы верх совпал с полом, убивать внутри границ) **после** push — удаляет зёрна, продавленные под пол. [▶ 36:40](https://youtu.be/V4mwAf8tcLk?t=2200) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- Отключите гравитацию и флюиды. Добавьте **nxPush**: режим **Particle Radius**, **Strength 100**, **Iterations ~200** (всё расталкивание должно произойти за один кадр; больше частиц → больше итераций). [▶ 3:15](https://youtu.be/XwX71yF7O5M?t=195) — *[2025-04-01](../../recipes/2025-04-01_jitter-grid-push-apart-initial-state.md)*
- Запеките: эмиттер ▸ Object ▸ **Initial State ▸ Set State** после кадра с push; режим Emission → **Controlled Only**, чтобы ничего нового не эмитилось. Удалите/отключите nxPush. [▶ 6:19](https://youtu.be/XwX71yF7O5M?t=379) — *[2025-04-01](../../recipes/2025-04-01_jitter-grid-push-apart-initial-state.md)*
- Порядок в стеке: **nxTurbulence → nxPush → nxSpeed**. — *[2024-11-12](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)*
- - nxPush: режим **Particle Radius**, полная сила (без перекрытий). — *[2024-11-12](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)*
- **nxPush**, Distance mode **Particle Radius** — затем исключите его из родительского эмиттера (вкладка Modifiers, exclude list), чтобы родители стояли на месте. [▶ 4:28](https://youtu.be/WTMgHpdgOhY?t=268) — *[2024-09-17](../../recipes/2024-09-17_taiao-volume-branch-particle-network.md)*
- **nxPush** ставим **ниже** nxQuestion (порядок меняет лук), режим Distance **Particle Radius**, Strength **100 %** → нет начального разлёта, усики вытягиваются. [▶ 4:29](https://youtu.be/LB-aA-N-2b0?t=269) — *[2024-08-27](../../recipes/2024-08-27_nxquestion-spawning-particle-tendrils.md)*
- **nxPush** в режиме **Particle Radius**, больше итераций. [▶ 1:09](https://youtu.be/nJpItCX8GlY?t=69) — *[2024-07-30](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)*

## Все рецепты (25)
- 2026-10-13 · [Процедурная анимация emitter по пути с jdGeoFlow](../../recipes/2026-10-13_jidou-geoflow-emitter-path.md)
- 2026-06-30 · [Запуск/остановка зацикленной анимации nxQuestion через action Break](../../recipes/2026-06-30_nxquestion-action-break.md)
- 2026-06-15 · [Цвет частиц в рендере Cycles и Eevee (экспорт Point Cloud из nxEmitter + атрибуты Geometry Nodes)](../../recipes/2026-06-15_blender-particle-color-to-render.md)
- 2026-05-19 · [Пульсация скорости / размера частиц через nxQuestion Math ▸ Wave](../../recipes/2026-05-19_nxquestion-sine-wave-pulsing.md)
- 2025-11-06 · [Частицы, разрастающиеся по процедурному проволочному мешу (mtEdgeSpline, mtSplineFX, xpSplineMesher, xpVertexMap Seed, nxQuestion Set Radius, nxPush)](../../recipes/2025-11-06_wired-growth-spline-mesh-vertex-map.md)
- 2025-11-04 · [Частицы, распускающиеся в щелях геометрии (соседи в nxQuestion + поле)](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)
- 2025-10-07 · [Пульсирующие частицы расталкивают друг друга, прижимаясь к поверхности (притяжение коллайдера)](../../recipes/2025-10-07_collider-attraction-surface-push.md)
- 2025-07-03 · [Обзор функций: слоёный nxTurbulence, nxScale и новый nxLimit (превью Fused 2025, часть 1)](../../recipes/2025-07-03_feature-notes-layered-nxturbulence-nxscale-nxlimit.md)
- 2025-06-24 · [Самоподдерживающийся цикл частиц: рост / расталкивание / уменьшение (nxAttract + nxPush + поле в nxQuestion + nxRotate через mapping)](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)
- 2025-05-07 · [Взрывающийся гранулярный бюст: рендер как песок и как снег (nxFluids SPH Granular, nxExplode, stability через Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2025-04-30 · [Процедурное рассыпание песочного бюста (nxFluids SPH Granular + группы через nxColor/nxQuestion + nxWind Von Karman + зерно с mapping по дистанции)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-04-01 · [Как спрятать гексагональную сетку в сыпучих симуляциях (Jitter эмиттера + nxPush на один кадр + Initial State)](../../recipes/2025-04-01_jitter-grid-push-apart-initial-state.md)
- 2024-11-12 · [Распускающийся цветок из трейлов (nxTurbulence Curl Blend/Add по возрасту + сила по скорости)](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)
- 2024-10-15 · [Одинаковый размер на рендере при симуляции, завязанной на радиус (каналы xpCache Custom Playback, сферы частиц в Redshift)](../../recipes/2024-10-15_xpcache-custom-playback-uniform-radius.md)
- 2024-09-17 · [Непересекающиеся ветки из частиц внутри меша (Taiao toTree volume points → spline emitter, nxQuestion Spawn, nxPush, nxScale)](../../recipes/2024-09-17_taiao-volume-branch-particle-network.md)
- 2024-08-27 · [Самопрорастающие усики по полю (nxQuestion Variable + Spawn + Set Age/Life, nxPush по радиусу)](../../recipes/2024-08-27_nxquestion-spawning-particle-tendrils.md)
- 2024-07-30 · [Точки MoGraph Matrix как движущиеся цели притяжения (nxAttract в режиме Object + nxPush + age map в nxScale)](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)
- 2024-07-23 · [Самопорождающиеся сети частиц внутри объёма (поиск соседей в nxQuestion + Spawn, удаление по объёму)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-07-09 · [Радиус частиц управляет цветом и свечением в Redshift (Scalar User Data ▸ Change Range ▸ Ramp / Scalar Ramp)](../../recipes/2024-07-09_redshift-particle-size-color-emission.md)
- 2024-04-25 · [Обзор функций: перестроенное ядро NeXus 2024.2 — быстрее на GPU и коллизии с анимированной геометрией](../../recipes/2024-04-25_feature-notes-nexus-2024-2-speed-collisions.md)
- 2024-04-09 · [Психоделические плоские паттерны расталкивания (nxPush + фиксация скорости через nxQuestion + nxScale по полю)](../../recipes/2024-04-09_nxpush-2d-radius-animation.md)
- 2023-09-27 · [«Живой» shatter-обратный отсчёт (xpShatter spline points + particle points, xpFlowField Along Spline, nxPush)](../../recipes/2023-09-27_xpshatter-countdown-flowfield-particles-part-c.md)
- 2023-09-27 · [Самоорганизующиеся «дышащие» кластеры сфер (xpColor noise → xpQuestion radius, nxPush mapped, nxConstraints Bind + Friction, Cycles 4D)](../../recipes/2023-09-27_breathing-sphere-clusters-noise-radius-part-a.md)
- 2023-07-05 · [Рекурсивный рост по полю через спавн в nxQuestion (nxQuestion Neighbors + Spawn, nxPush, nxTurbulence с mapping)](../../recipes/2023-07-05_nxquestion-recursive-growth-rig-part-a.md)
- 2023-02-21 · [Три способа заставить частицы сталкиваться друг с другом (xpConstraints Collisions, xpPPCollisions, xpBullet)](../../recipes/2023-02-21_particle-collisions-constraints-ppcollisions-bullet.md)
