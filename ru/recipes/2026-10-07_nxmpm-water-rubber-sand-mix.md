# Вода, резиновые мармеладки и песок в одном solve, с мешингом и рендером (nxMPM Materials + nxMesher + point cloud, Cycles)

- Источник: NeXus Official Training — nxMPM — https://www.youtube.com/watch?v=jItRyLgdjPg (2026-10-07)
- Хост / поколение: Blender (NeXus for Blender 2026.1 beta, m, Z-up); пресет nxMaterial, nxEmitter, nxMPM, nxGravity, nxCache, nxMesher; Cycles GPU
- Задача: струя воды разбрызгивается, в ней отскакивают две резиновые Suzanne, затем падает песочная Suzanne и вытесняет жидкость.

## Быстрый старт
NeXus Hierarchy ▸ Presets ▸ **nxMaterial** = gravity + папка (эмиттер, MPM, мешер выключен), готово к проигрыванию. Материал по умолчанию **Snow**; для всплеска переключите на Liquid ▸ Water.

## Шаги (с нуля)
1. **nxEmitter** (Box) + Dynamics ▸ **nxMPM** + Modifiers ▸ **nxGravity**. Emitter ▸ **Match Solver Resolution** → MPM (автоматический радиус + упаковка по сетке). Emission **Shot** для одного сгустка.
2. MPM Display ▸ Draw Grid (Back). Resolution **120** для финала, **80** для черновиков. Domain Z = 2 m, чтобы стоял на полу; сделайте его тоньше.
3. **Use Bounds** выкл → разреженный solve, но тогда добавьте куб + **nxCollider** (friction) в качестве пола. В демо домен оставлен.
4. Эмиттер "water": Sphere r 0.2, Rate, эмиссия только на кадрах 1–30.
5. Suzanne → **Copy** эмиттера ("gummy01"): Shape Object = Suzanne01, Shot, скорость 0.
6. Глобальный материал MPM = **Elastic ▸ Rubber** (по умолчанию для всех эмиттеров, не указанных в списке). Вкладка **Materials**: добавьте "water" → **Liquid ▸ Water**.
7. MPM Display ▸ Particle Color = **Material** (жидкость синяя, elastic розовый) для проверки.
8. Дублируйте Suzanne + эмиттер → "gummy02", shot на F15.
9. Большая Suzanne + эмиттер "sand", shot на F75; вкладка Materials → **Sand ▸ Dry**.
10. **nxCache** на res 120 (~2 мин в демо).
11. По одному **nxMesher** на эмиттер. Вода: слой эмиттера, Surface **Zhu-Bridson**, Polygon mode **Quads**, Polygon Size поменьше, Radius 0.025.
12. Мармеладки: режим Spheres, Polygon Size 0.02, Radius 0.03, слой **Smoothing** Main Curvature 100%, Iterations 5 (10–15 — слишком мягко).
13. Песок: эмиттер ▸ **Export ▸ Create Point Cloud**; автоматический материал читает цвет частиц через Attribute node — или используйте Point Info Random → Color Ramp → Base Color для дешёвой вариации песчинок.
14. Рендер: большая плоскость (80×80), World **Sky Texture** strength ~0.05. Вода: Transmission 1, Roughness 0, IOR 1.33. Мармеладки: Subsurface Christensen-Burley weight 1, radius 0.5, маленький scale, немного transmission; скопируйте материал для второго цвета.
15. Motion blur на мешах с меняющейся топологией: nxMesher ▸ Export ▸ **Transfer Velocity**.

## Подводные камни
- Диапазон кадров эмиттера действует и на Shot: shot на F75 при диапазоне Emit 1–30 ничего не выпустит — снова включите Emit All Frames.
- Match Solver Resolution означает, что при большем разрешении MPM частиц автоматически становится больше и они мельче.

## Как сейчас (новые инструменты)
Это уже самый новый путь. До MPM: nxFluids FLIP/SPH для воды, SPH granular для песка, CPU xpClothFX/soft bodies для резины — три отдельных solve без двустороннего смешивания.
