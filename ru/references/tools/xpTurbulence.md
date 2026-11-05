# xpTurbulence — карточка инструмента

Встречается в **11** рецептах · 2023-02-28 → 2024-02-06 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **xpTurbulence**: scale 150, strength 15. [▶ 3:25](https://youtu.be/3YmhMKdK0o4?t=205) — *[2024-02-06](../../recipes/2024-02-06_meshtools-xpdynamics-soft-body.md)*
- Motion ▸ **xpTurbulence**, сила **18** (щупальца выглядят неподвижными, но на деле это постоянный поток новых частиц). [▶ 1:32](https://youtu.be/M4z3kOU4YEw?t=92) — *[2023-12-19](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)*
- **xpTurbulence**: Scale **30**, Strength **8**. — *[2023-06-20](../../recipes/2023-06-20_xpfragmenter-wind-disintegration.md)*
- **xpTurbulence** для извивания. **xpTrail ▸ Algorithm: Tendrils** connections (а не след от birth-частицы). **xpSplineMesher** по трейлу: Subdivision 1, Size ▸ кривая **Scale Spline**, чтобы сузить конец в точку. [▶ 3:11](https://youtu.be/KBktASa5O2o?t=191) — *[2023-06-12](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)*
- По желанию **xpTurbulence** (маленький масштаб, большая сила) для дрожания внутри комка. — *[2023-06-08](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)*
- **xpTurbulence** (Modifiers ▸ Motion): noise **FBM**, масштаб крупнее, Strength **~24** → лёгкий дымок. [▶ 4:02](https://youtu.be/iWET6SJpDhw?t=242) — *[2023-03-28](../../recipes/2023-03-28_vertex-speed-emission-xpvertexmap.md)*
- Для сравнения (по желанию): **xpTurbulence** (Modifiers ▸ Motion) с настройками по умолчанию — красиво, но никак не связано с движением объекта. На время настройки отключите. [▶ 1:30](https://youtu.be/pwEBS2tOgNw?t=90) — *[2023-03-14](../../recipes/2023-03-14_motion-inheritance-linear-rotational.md)*

## Все рецепты (11)
- 2024-02-06 · [Органичный колышущийся шипастый шар (mtSubdivider + mtInset на soft body через xpDynamics)](../../recipes/2024-02-06_meshtools-xpdynamics-soft-body.md)
- 2023-12-19 · [Колышущиеся стеклянные щупальца с частицами на концах (xpTendril + xpTrail Tendrils + xpSplineMesher + тег xpTrailTip)](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)
- 2023-09-26 · [Крупные завихрения плюс мелкая детализация (nxTurbulence Voronoi, Octaves, Persistence, Lacunarity)](../../recipes/2023-09-26_nxturbulence-octaves-persistence-lacunarity.md)
- 2023-06-20 · [Распад модели полигон за полигоном под управлением частиц (xpFragmenter Faces Polys, xpWind с linear field, xpTurbulence с маппингом на пройденную дистанцию)](../../recipes/2023-06-20_xpfragmenter-wind-disintegration.md)
- 2023-06-12 · [Извивающиеся щупальца, которые держат констрейнты (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-06-08 · [Фейковая тягучая жидкость, ползущая по логотипу (xpConstraints Forces, xpCover, Data Mapping по radius/age/temperature, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-05-09 · [Типы отображения частиц во viewport и их рендер (вкладка Display у эмиттера + генератор Display Render)](../../recipes/2023-05-09_particle-display-modes-display-render.md)
- 2023-03-28 · [Эмиссия только с самых быстро движущихся частей меша (слой Vertex Speed в xpVertexMap + эмиссия по текстуре)](../../recipes/2023-03-28_vertex-speed-emission-xpvertexmap.md)
- 2023-03-21 · [Три поколения спавна из одного эмиттера (уровни xpMultiSpawn + группы для отображения)](../../recipes/2023-03-21_xpmultispawn-layered-spawning-groups.md)
- 2023-03-14 · [Частицы, наследующие движение объекта-эмиттера (Motion Inheritance linear + rotational, xpTurbulence)](../../recipes/2023-03-14_motion-inheritance-linear-rotational.md)
- 2023-02-28 · [Основы вращения частиц (Use Rotation на эмиттере: Set / Tangential / None + случайное вращение xpSpin)](../../recipes/2023-02-28_particle-rotation-tangential-random-spin.md)
