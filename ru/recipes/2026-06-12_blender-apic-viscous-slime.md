# Вязкая слизь, укладывающаяся кольцами на голове (nxFluids APIC viscosity + surface tension, nxMesher Spheres + Mean Curvature)

- Источник: NeXus for Blender Official Training — Liquid Slime — https://www.youtube.com/watch?v=pz6LDGGeD5A (2026-06-12)
- Хост / поколение: Blender (NeXus for Blender, G3); GPU nxFluids **APIC**, nxGravity, nxCollider, nxMesher; Cycles GPU
- Задача: густая слизь льётся на Suzanne, тянется, рвётся и укладывается кольцами на полу; рендер с подповерхностным рассеиванием.

## Исходная сцена
Suzanne, применённый Subdivision 1, shade smooth, масштаб **0.3** (≈3 m — слишком крупно).

## Шаги
1. **nxFluids**, solver **APIC** (FLIP/APIC — voxel-солверы с границами; PBD без границ). Автор выбирает APIC для очень вязких жидкостей. Плотно сожмите bounds вокруг действия (меньше voxel). Display ▸ draw grid (только задние) — чтобы видеть voxel; отображение пола выключите. [▶ 1:33](https://youtu.be/pz6LDGGeD5A?t=93)
2. **nxEmitter** Sphere, радиус **0.05**, над головой, Rate **20,000**, speed 0, радиус частиц **0.006** (от радиуса потом зависит mesh). [▶ 4:08](https://youtu.be/pz6LDGGeD5A?t=248)
3. **nxGravity** (в Blender обязателен — гравитации сцены нет). [▶ 4:28](https://youtu.be/pz6LDGGeD5A?t=268)
4. nxFluids **Voxel size 0.02** для точности. [▶ 11:02](https://youtu.be/pz6LDGGeD5A?t=662)
5. **nxCollider**: слой Suzanne (bounce 0, немного friction, потом меньше); плюс **куб**-пол внутри bounds отдельным слоем (bounce 0, friction) — voxel-солверам нужны объёмные коллайдеры, а не плоскости. [▶ 7:19](https://youtu.be/pz6LDGGeD5A?t=439)
6. **Viscosity ~75** → сразу начинает укладываться кольцами, медленно тянется и падает. [▶ 7:52](https://youtu.be/pz6LDGGeD5A?t=472)
7. Покачайте emitter: keyframe Location X/Y, в Graph Editor F-модификатор **Noise** (увеличьте scale, чтобы успокоить), скопируйте на Y со сдвигом → складки вместо одной кучи. [▶ 9:30](https://youtu.be/pz6LDGGeD5A?t=570)
8. Точность: substeps солвера **Min 2, Max 5**. [▶ 11:14](https://youtu.be/pz6LDGGeD5A?t=674)
9. **Surface Tension**: начинайте с малого (0.1 → 0.5 → **2**) — подтягивает нити и капли; если перебрать, всё схлопывается в капли-блобы. [▶ 13:28](https://youtu.be/pz6LDGGeD5A?t=808)
10. **nxMesher** ▸ слой эмиттера, wireframe + **Quads**. Проверяйте настройки на сложных кадрах (тонкие рвущиеся нити). **Polygon Size 0.008**, **Radius 0.013** (чуть толще, чтобы сглаживание могло истончить; на 0.012 терялись частицы). [▶ 17:36](https://youtu.be/pz6LDGGeD5A?t=1056)
11. Surface Type **Spheres** (сохраняет чёткие складки); Zhu-Bridson красиво сглаживает воду, но даёт артефакты на резких изломах. Добавьте слой сглаживания **Mean Curvature 100%, 5 iterations** (потом **8**) — сглаживает плоские участки, сохраняет складки. [▶ 19:28](https://youtu.be/pz6LDGGeD5A?t=1168)
12. Рендер Cycles GPU: плоскость совмещена со скрытым кубом-полом; три area-лампы с Track To на Suzanne (сильный key, мягкий fill, сильный rim). Материал: фиолетовая база, довольно шероховатый, **Subsurface Random Walk** weight 1, radius 1,1,1, scale ~1; **Coat** IOR ~1.4 для эффекта влажности. [▶ 21:22](https://youtu.be/pz6LDGGeD5A?t=1282)

## Подводные камни
- Слишком маленький радиус мешера относительно polygon size = мерцание/пропадающие куски mesh.
- SSS/transmission скрывает часть неровностей — проверьте в рендере, прежде чем пересглаживать.

## Как сейчас (новые инструменты)
В 2026.1 beta у FLIP/APIC появились **non-Newtonian** настройки (Flow Index, **Yield Stress**), **Wall Friction** и Mixer для viscosity по эмиттерам; в nxMesher — сглаживание **Detail Aware**. Для желеобразных твёрдых тел используйте **nxMPM**.
