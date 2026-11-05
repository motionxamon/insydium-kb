# nxCover — карточка инструмента

Встречается в **3** рецептах · 2023-06-08 → 2024-05-21 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxCover**: текстовый сплайн, **Edges**; движение использует скорость частиц; **Hold Time 0** = держит бесконечно. [▶ 1:11](https://youtu.be/dL2bCkQf5HM?t=71) — *[2024-05-21](../../recipes/2024-05-21_nxcover-turbulent-spline-reveal.md)*
- **nxTurbulence** Voronoi, strength 20 → только волны скорости, пока доминирует nxCover. [▶ 3:00](https://youtu.be/dL2bCkQf5HM?t=180) — *[2024-05-21](../../recipes/2024-05-21_nxcover-turbulent-spline-reveal.md)*
- Снизьте **strength** слоя nxCover **до ~19%**, чтобы турбулентность успевала их закрутить, прежде чем они осядут. [▶ 3:03](https://youtu.be/dL2bCkQf5HM?t=183) — *[2024-05-21](../../recipes/2024-05-21_nxcover-turbulent-spline-reveal.md)*
- Буквы потолще: удержание в nxCover **Attract** (по умолчанию, тормозит с 50 cm) → **Spring**, damping **15%**; увеличьте **spring length** для случайной осыпи вокруг краёв. Больше damping/stiffness = меньше колебаний. [▶ 6:19](https://youtu.be/dL2bCkQf5HM?t=379) — *[2024-05-21](../../recipes/2024-05-21_nxcover-turbulent-spline-reveal.md)*

## Все рецепты (3)
- 2024-05-21 · [Турбулентное появление текста из частиц (nxCover Edges + слабая сила слоя + удержание Spring, nxColor по Direction)](../../recipes/2024-05-21_nxcover-turbulent-spline-reveal.md)
- 2024-04-22 · [Обзор функций: nxFollowGeo, слоёный nxColor и nxCover (NeXus 2024.2)](../../recipes/2024-04-22_feature-notes-nxfollowgeo-nxcolor-nxcover.md)
- 2023-06-08 · [Фейковая тягучая жидкость, ползущая по логотипу (xpConstraints Forces, xpCover, Data Mapping по radius/age/temperature, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
