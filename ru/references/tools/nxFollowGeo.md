# nxFollowGeo — карточка инструмента

Встречается в **18** рецептах · 2023-03-29 → 2026-10-30 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxFollowGeo** ▸ Object = Bezier circle (сам определяет сплайн или полигоны). **Release ▸ Spline End: Loop**. **Extended Data**: удалите слой **Offset** по умолчанию (смещение ленты 0.2 m) — расстояние между частицами обеспечит солвер жидкости. [▶ 1:55](https://youtu.be/na6NGPw4XWM?t=115) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*
- Настройка nxFollowGeo: общая **Strength 50%**; больше **Attract Strength** = плотнее к кривой и глаже; **Active Range 2.5** позволяет струе разрываться и снова собираться. [▶ 8:47](https://youtu.be/na6NGPw4XWM?t=527) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*
- Cycles GPU: noise threshold выше, 1000 сэмплов, без денойза; **Fast GI Approximation** для превью; **Motion Blur shutter 1 frame** (кэшированная скорость читается автоматически). Area-светильники (Normalize выкл.; например 50/40/30, Track To на nxFollowGeo в начале координат); Principled Transmission 1, roughness ~0, **IOR 1.33**; опционально DOF (F-stop ~3.3) на объект follow-geo. **Lock Interface** перед рендером. [▶ 18:39](https://youtu.be/na6NGPw4XWM?t=1119) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*
- **nxFollowGeo** → сплайн = окружность. Режим **Force** (не Guide), чтобы жидкость и турбулентность продолжали действовать. Поднимаем Follow Strength; **Attract Strength ~400**, чтобы держать частицы на пути. [▶ 1:43](https://youtu.be/5Ra6keP2ZgE?t=103) — *[2025-11-18](../../recipes/2025-11-18_nxfollowgeo-spline-flow-pbd.md)*
- …поэтому используй у коллайдера **вкладку Forces → Attraction**, Radius 100 cm, strength ~59 → частицы прижимаются к поверхности и при этом расталкиваются. (Не сочетай nxFollowGeo + nxPush — силы противоречат друг другу.) [▶ 6:19](https://youtu.be/PTamR793O-k?t=379) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- **nxFollowGeo** с геометрией Emission, **Field of View 360**; **nxTurbulence** с noise **Voronoise** → точки блуждают по поверхности. [▶ 2:05](https://youtu.be/UXqS-dqsHiM?t=125) — *[2025-08-07](../../recipes/2025-08-07_procedural-plasma-ball-mtsplinefx.md)*
- **nxFollowGeo**: объект = голова волка, режим **Surface**, **Field of Vision 360°**, **Friction 1%**, **Distance 25**, чтобы захватить все частицы. [▶ 1:10](https://youtu.be/RUhF1pju3Wk?t=70) — *[2025-05-06](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)*
- Режим nxFollowGeo **Surface → Edge**; поднимите параметр Edge, чтобы частицы плотнее липли к рёбрам → проявление wireframe. [▶ 3:05](https://youtu.be/RUhF1pju3Wk?t=185) — *[2025-05-06](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)*
- xpEmitter ▸ Object: источник = **объект Select** (не модель), Polygons, перетащите полигональное выделение; nxFollowGeo тоже использует объект Select. [▶ 1:41](https://youtu.be/AmfN_ZlpBcE?t=101) — *[2025-01-28](../../recipes/2025-01-28_meshtools-animated-selection-emission.md)*
- Вариант с рёбрами: nxFollowGeo **Edge mode, Edge 100%, offset 2 cm**; в Select отключите polygon, включите **Edge selection**; эмиттер — emit from **Edges** с выделением рёбер. [▶ 3:23](https://youtu.be/AmfN_ZlpBcE?t=203) — *[2025-01-28](../../recipes/2025-01-28_meshtools-animated-selection-emission.md)*
- nxFollowGeo ▸ Groups Affected: только **group 1**. [▶ 1:00](https://youtu.be/wO5-UoWNTkA?t=60) — *[2025-01-14](../../recipes/2025-01-14_nxquestion-random-math-dissolve.md)*
- **nxFollowGeo** с тором (у каждого подключённого объекта свои настройки): **Field of View 360°**, чтобы частицы всегда прилипали. [▶ 1:11](https://youtu.be/dLTdpbRiG68?t=71) — *[2024-05-14](../../recipes/2024-05-14_nxfollowgeo-surface-fluid.md)*
- nxFollowGeo **Friction 4%** → дымчатый, тонкий поток. [▶ 1:57](https://youtu.be/dLTdpbRiG68?t=117) — *[2024-05-14](../../recipes/2024-05-14_nxfollowgeo-surface-fluid.md)*

## Все рецепты (18)
- 2026-10-30 · [Формируем частицы, дым и FLIP варпами (nxWarp Scroll / Bend / Helix / Twist — режимы Deform, Guide, Flow)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-06-18 · [Струя жидкости, бегущая по кругу вдоль кривой, мешинг с motion blur (сплайн nxFollowGeo + nxFluids PBD + nxMesher Transfer Velocity)](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)
- 2025-11-18 · [Тягучая жидкость, кружащая вокруг нескольких сплайнов (nxFollowGeo в режиме Force + PBD)](../../recipes/2025-11-18_nxfollowgeo-spline-flow-pbd.md)
- 2025-10-07 · [Пульсирующие частицы расталкивают друг друга, прижимаясь к поверхности (притяжение коллайдера)](../../recipes/2025-10-07_collider-attraction-surface-push.md)
- 2025-08-14 · [Обзор функций: сплайновые режимы nxFollowGeo, nxUpres по каналам, слои nxSpeed Range](../../recipes/2025-08-14_nxfollowgeo-splines-nxupres-channels-nxspeed-range.md)
- 2025-08-07 · [Процедурный плазменный шар (nxFollowGeo + nxTurbulence на частицах, дуги mtSplineFX, ответвления от пересечений mtEdgeSpline)](../../recipes/2025-08-07_procedural-plasma-ball-mtsplinefx.md)
- 2025-05-08 · [Лента частиц, обёрнутая вокруг сплайна деформерами C4D (Spline Wrap + Twist на xpEmitter)](../../recipes/2025-05-08_c4d-deformers-twist-spline-wrap-particles.md)
- 2025-05-06 · [Проявление wireframe частицами (nxFollowGeo в режиме Edge + nxTurbulence + ограничение nxSpeed)](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)
- 2025-03-13 · [Завихрения-шлейфы по касательной к поверхности (C4D Field Force + векторы Volume Builder Cross Product + nxColor ▸ xpTrail Per Vertex в Redshift)](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)
- 2025-01-28 · [Эмиссия из анимированных живых выделений (MeshTools Select + noise shader → xpEmitter + nxFollowGeo режим Edge)](../../recipes/2025-01-28_meshtools-animated-selection-emission.md)
- 2025-01-14 · [Случайное растворение по полю (nxQuestion Field + Group + Math Random)](../../recipes/2025-01-14_nxquestion-random-math-dissolve.md)
- 2024-05-14 · [Дымчатая жидкость, ползущая по тору (nxFollowGeo с FOV 360° + friction, nxTurbulence, nxFluids)](../../recipes/2024-05-14_nxfollowgeo-surface-fluid.md)
- 2024-04-22 · [Обзор функций: nxFollowGeo, слоёный nxColor и nxCover (NeXus 2024.2)](../../recipes/2024-04-22_feature-notes-nxfollowgeo-nxcolor-nxcover.md)
- 2024-03-26 · [Стилизованные линии потока аэротрубы вокруг машины (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2024-01-09 · [Живые частицы как точки, управляющие Displacer (XP Editing + C4D Fields Delay)](../../recipes/2024-01-09_xp-editing-particles-drive-deformers.md)
- 2023-11-16 · [Кристаллы, прорастающие вдоль замерших путей частиц (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-10-03 · [Частицы, органично текущие вдоль сплайна (слои xpFlowField Along Spline + Curl + To Spline)](../../recipes/2023-10-03_xpflowfield-along-spline-curl.md)
- 2023-03-29 · [Дымовой взрыв по сплайнам, который адвектит живые гранулы (xpExplosiaFX Advection + xpFlowField Along Spline + falloff эмиттера)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
