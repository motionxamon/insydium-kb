# Тягучая жидкость в меше с переносом цветов частиц (nxFluids SPH + nxConstraints Viscosity, xpOpenVDBMesher Transfer Point Color)

- Источник: Top Tip Tuesday — nxFluids Vertex Color — https://www.youtube.com/watch?v=fvS3h7uk35s (2023-09-05)
- Хост / поколение: C4D; G2 NeXus (nxFluids, nxConstraints, nxGravity) + **CPU xpOpenVDBMesher**; Standard-материал (подойдёт любой рендер)
- Задача: цветная вязкая струя, меш которой сохраняет градиентные цвета частиц для шейдинга.

## Исходная сцена
xpEmitter с тегом Vibrate, эмиссия **Hexagonal**, скорость 0, радиус частиц **1 cm**; **nxGravity strength 400 cm**; коллайдеры на реквизите. Цвет: emitter Display ▸ Color mode **Shader** → шейдер Gradient, **3D Linear**, **Cycle** включён.

## Шаги
1. **nxFluids**, солвер **SPH**, остальное по умолчанию.
2. **nxConstraints**: Iterations **3**, добавьте constraint **Viscosity**, Radius поиска **20**, максимум связей **3** → тягучесть. [▶ 1:21](https://youtu.be/fvS3h7uk35s?t=81)
3. Generators ▸ **xpOpenVDBMesher**, перетащите xpEmitter в его список. Voxel size **3** для большего числа полигонов. [▶ 2:09](https://youtu.be/fvS3h7uk35s?t=129)
4. Point Radius (по умолчанию 10 = 10× радиуса частицы): понижайте по шагам, пока меш не станет тоньше; на **2** он исчезает, **5** оставляет достаточно толщины, чтобы пережить сглаживание. [▶ 2:39](https://youtu.be/fvS3h7uk35s?t=159)
5. Filters: удалите стандартный Median; вместо Gaussian (слишком агрессивный, съедает мелкие капли) используйте **Curvature**, подняв iterations — сглаживает бугры, сохраняет плоские участки и детали. [▶ 3:47](https://youtu.be/fvS3h7uk35s?t=227)
6. Скройте частицы. Mesher ▸ Tags ▸ **Transfer Point Color** → на мешере появляется тег vertex color; добавьте немного **color smoothing** в настройках тега мешера, чтобы убрать артефакты по рёбрам полигонов. [▶ 4:43](https://youtu.be/fvS3h7uk35s?t=283)
7. Материал: слой Reflectance **Beckmann** + **Dielectric Fresnel** с IOR как у воды; текстура канала Color ▸ Effects ▸ **Vertex Map**, закиньте туда тег цвета вершин. Работает вживую при проигрывании и в сторонних рендерах через их vertex-color ноду. [▶ 5:47](https://youtu.be/fvS3h7uk35s?t=347)

## Подводные камни
- Больше частиц = чище меш; слишком низкий Point Radius при грубом voxel size убивает меш.

## Как сейчас (новые инструменты)
GPU **nxMesher** (Fused 2025.4) сразу выдаёт теги цвета/скорости со слоёным сглаживанием; FLIP/APIC с переменной вязкостью или настройки non-Newtonian в 2026.1 заменяют трюк SPH + viscosity constraint. См. «Speed-stretched meshes and vertex color» (2024-11-05).
