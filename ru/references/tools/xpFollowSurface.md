# xpFollowSurface — карточка инструмента

Встречается в **4** рецептах · 2023-11-16 → 2025-03-13 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **xpFollowSurface** со сферой (скройте её). — *[2024-01-09](../../recipes/2024-01-09_xp-editing-particles-drive-deformers.md)*
- **xpFollowSurface** → join от Sim Low, **Pull 99%**, увеличьте Distance (с 10 cm по умолчанию высокие частицы не цепляются). [▶ 7:58](https://youtu.be/yqfkRKgW1Mo?t=478) — *[2023-11-16](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)*
- Дублируйте xpFollowSurface → join от Sim High, **Pull 100%** (никаких кадров над поверхностью при рождении); исключите его из управляющего эмиттера. [▶ 21:55](https://youtu.be/yqfkRKgW1Mo?t=1315) — *[2023-11-16](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)*

## Подводные камни
- Объекты-генераторы (TF terrain) нужно положить в xpJoin, иначе xpFollowSurface их не примет. — *[2023-11-16](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)*

## Все рецепты (4)
- 2025-03-13 · [Завихрения-шлейфы по касательной к поверхности (C4D Field Force + векторы Volume Builder Cross Product + nxColor ▸ xpTrail Per Vertex в Redshift)](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)
- 2024-04-22 · [Обзор функций: nxFollowGeo, слоёный nxColor и nxCover (NeXus 2024.2)](../../recipes/2024-04-22_feature-notes-nxfollowgeo-nxcolor-nxcover.md)
- 2024-01-09 · [Живые частицы как точки, управляющие Displacer (XP Editing + C4D Fields Delay)](../../recipes/2024-01-09_xp-editing-particles-drive-deformers.md)
- 2023-11-16 · [Кристаллы, прорастающие вдоль замерших путей частиц (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
