# Управляемая тягучая струя жидкости (PBD + nxDirection + nxMesher)

- Источник: Top Tip Tuesday — Direction Force — https://www.youtube.com/watch?v=pbO2aDK4to8 (2026-03-17)
- Хост / поколение: C4D, Fused 2025.4+ (nxDirection — новинка 2025.4, nxFluids PBD, nxMesher, поиск соседей в nxColor)
- Задача: хаотичная струя жидкости с щупальцами, которую можно точно направлять и мешить почти в реальном времени.

## Дерево сцены
```
nxDirection (Direction Force layer)  ← rotate/animate to steer
  └─ xpEmitter (stream)   (child → emitter follows the direction)
nxTurbulence (Voronoi layer)
nxFluids PBD: External Pressure 100%, Attraction ↓, Repulsion ↑, **Smoothing Radius 150%** (gloopy tendrils)
nxColor: Gradient (Parameter) = Neighbors within 15 cm, 20 → purple … 200 → yellow
nxMesher: emitter, smaller radius, Polygon Size 3, **Zhu-Bridson**, Export Tags ▸ Transfer Color, Smoothing iterations 5 (color)
```

## Шаги
1. PBD — наименее «физичный» солвер, но идеален для стилизованных струй; ключ к тягучести — **Smoothing Radius ~150%** плюс полное внешнее давление.
2. Под турбулентностью струя теряет инерцию → **nxDirection** Direction Force (красная стрелка = направление), **Direction strength ~180**.
3. **Twist strength** закручивает частицы спиралью вокруг линии (отрицательное значение — в другую сторону); закрутка выталкивает их наружу, поэтому добавьте **Attract strength ~250**, чтобы притянуть обратно к линии.
4. Анимируйте nxDirection, чтобы направить струю куда угодно — случайность турбулентности сохраняется.
5. Мешите через **nxMesher Zhu-Bridson** (гладко без слоёв сглаживания), переносите цвет частиц в vertex color tag; итерации сглаживания смешивают цветовые пятна.
