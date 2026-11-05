# Вода, собирающаяся в капли (поверхностное натяжение nxFluids SPH + nxGravity по возрасту)

- Источник: Top Tip Tuesday — NeXus Water Droplets — https://www.youtube.com/watch?v=DCggkQ6Mu_w (2024-04-02)
- Хост / поколение: C4D; NeXus GPU (nxFluids SPH, nxGravity Mapping, nxKill) + CPU **xpOpenVDBMesher**; рендер Cycles 4D
- Задача: вода, которая собирается в капли прямо в воздухе, затем падает и снова собирается в капли на поверхности.

## Исходная сцена
xpEmitter Rectangle, Rate 100, speed 0, маленький радиус (значение неразборчиво); nxFluids + nxGravity по умолчанию; бокс **nxKill** убивает частицы, покидающие область; коллайдер-куб.

## Шаги
1. **nxFluids**: солвер **PBD → SPH** (лучше поверхностное натяжение), **Substeps 8** (поверхностному натяжению нужна точность), **Surface Tension 100%**. [▶ 1:11](https://youtu.be/DCggkQ6Mu_w?t=71)
2. Проблема: частицы падают раньше, чем успевают собраться в капли. Решение — в **nxGravity ▸ Mapping ▸ Age** слой → Gravity Strength. По умолчанию диапазон 0–30 F плавно ведёт от 0 до полной силы; поставьте **Range Min 59, Max 65**, чтобы частицы ~2 s висели в невесомости, собирались в капли и потом падали. [▶ 3:10](https://youtu.be/DCggkQ6Mu_w?t=190)
3. Силу гравитации уменьшите вдвое, до **450**. [▶ 3:38](https://youtu.be/DCggkQ6Mu_w?t=218)
4. Тег коллайдера: поднимите **Friction**, чтобы капли прилипали и скатывались, только когда в них врезаются другие (Bounce/Scatter тоже доступны). [▶ 4:15](https://youtu.be/DCggkQ6Mu_w?t=255)
5. **xpOpenVDBMesher**: источник — эмиттер, **Voxel size 1**, **Point Radius 3**, один фильтр **Curvature**, Iterations 4. [▶ 4:58](https://youtu.be/DCggkQ6Mu_w?t=298)
6. Простые материалы + окружение Cycles 4D; превью в реальном времени. [▶ 5:23](https://youtu.be/DCggkQ6Mu_w?t=323)

## Как сейчас (новые инструменты)
**nxFluids FLIP/APIC** (Fused 2025.4) добавляет усики от поверхностного натяжения; мешите GPU-**nxMesher**. nxCollider (бета 2026.1) добавляет адгезию для липких капель.
