# Частицы, разрастающиеся по процедурному проволочному мешу (mtEdgeSpline, mtSplineFX, xpSplineMesher, xpVertexMap Seed, nxQuestion Set Radius, nxPush)

- Источник: Bite-Sized — Wired Growth — https://www.youtube.com/watch?v=rDSSeIZUl08 (2025-11-06)
- Хост / поколение: C4D; MeshTools + CPU xpEmitter/xpVertexMap с NeXus nxQuestion/nxPush (G2)
- Задача: процедурный проволочный каркас, соединяющий два вложенных платоника, и сферы, которые органично разрастаются по нему от seed-точек.

## Шаги
1. Два объекта **Platonic**, второй — увеличенная копия. Два объекта **mtEdgeSpline** (display gradient выкл), под каждый вложить по платонику; платоники скрыть. [▶ 1:37](https://youtu.be/rDSSeIZUl08?t=97)
2. **xpEmitter** ▸ Emitter Source Object = платоник 1, Emit From **Points**, включить **One Particle per Source Element**; Emission **Shot**, mode Simulate, speed выкл; поднять display size factor. Дублировать для платоника 2. [▶ 1:20](https://youtu.be/rDSSeIZUl08?t=80)
3. **mtSplineFX**: Start Emitter / End Emitter = два эмиттера, Connection Type Origin → **Points** (дуги между соответствующими точками); амплитуды motion-noise 0; gradient выкл. [▶ 2:07](https://youtu.be/rDSSeIZUl08?t=127)
4. **xpSplineMesher** (X-Particles ▸ Generators): objects = оба edge-сплайна + сплайн SplineFX; Joins выкл, Size **2**. Сгруппировать сплайны в null (Alt+G) и скрыть — риг остаётся процедурным. [▶ 3:09](https://youtu.be/rDSSeIZUl08?t=189)
5. **xpVertexMap** (X-Particles ▸ Utilities) на spline mesher: mode Polygon → **Seed Object**, добавить 3 seed-объекта, пересекающих меш (увеличить их); **Search Radius 5** → карта разрастается при проигрывании. [▶ 3:45](https://youtu.be/rDSSeIZUl08?t=225)
6. Разбиваем рост: добавить шейдер **Noise** в vertex map; Effects ▸ немного **Contrast**. [▶ 4:51](https://youtu.be/rDSSeIZUl08?t=291)
7. Второй **xpEmitter**: поверхность spline mesher, Selection = vertex map, **Polygon Area**, speed выкл, radius **0**; отображение Spheres. [▶ 5:54](https://youtu.be/rDSSeIZUl08?t=354)
8. **nxQuestion**: Age > 0 → Action **Set Radius 5** (позже **3**), Weight ≈ **10%**, чтобы радиус нарастал плавно. [▶ 6:50](https://youtu.be/rDSSeIZUl08?t=410)
9. **nxPush**: mode **Particle Radius**, сила на максимум → сферы при росте расталкивают друг друга. [▶ 7:23](https://youtu.be/rDSSeIZUl08?t=443)

## Подводные камни
- Seed-объекты должны реально пересекать геометрию, иначе ничего не растёт.
- При эмиссии с radius 0 ничего не видно, пока question не начнёт их растить.

## Как сейчас (новые инструменты)
Тот же риг работает в Fused 2025.4.x (mtEdgeSpline обрабатывает n-gon'ы начиная с 2025.4.1). В 2026.1 beta управлять ростом вместо xpVertexMap могут режимы nxFalloff Wet / Points или nxFalloff Modifier Grow/Decay, а **nxBioLogic** (differential growth, кораллы) — GPU-путь к полностью органическому росту по поверхности.
