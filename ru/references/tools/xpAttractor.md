# xpAttractor — карточка инструмента

Встречается в **3** рецептах · 2023-11-16 → 2025-08-05 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Прилипание к поверхности: **xpAttractor** на бюсте, режим Velocity, Force ~50, Acceleration 0, Speed Limit огромный; **Linear field +Y**, чтобы притяжение ослабевало ниже и частицы свободно падали. [▶ 4:14](https://youtu.be/14SqrdO1c6o?t=254) — *[2025-08-05](../../recipes/2025-08-05_gloopy-mix-group-mapped-viscosity.md)*
- В теге динамики **Rigidity** 0.5 → 0.1 (рыхлая). **xpAttractor** (по умолчанию) держит её по центру; **Pressure 0.5**; rigidity обратно до **0.4**, чтобы держала форму. [▶ 3:43](https://youtu.be/3YmhMKdK0o4?t=223) — *[2024-02-06](../../recipes/2024-02-06_meshtools-xpdynamics-soft-body.md)*
- **xpAttractor** с дальней стороны (Acceleration ~50, strength пониже), чтобы протянуть поток через террейн; скройте его иконку. [▶ 35:41](https://youtu.be/yqfkRKgW1Mo?t=2141) — *[2023-11-16](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)*

## Все рецепты (3)
- 2025-08-05 · [Три тягучие жидкости с тремя вязкостями (группы + nxConstraints Viscosity с mapping по Group)](../../recipes/2025-08-05_gloopy-mix-group-mapped-viscosity.md)
- 2024-02-06 · [Органичный колышущийся шипастый шар (mtSubdivider + mtInset на soft body через xpDynamics)](../../recipes/2024-02-06_meshtools-xpdynamics-soft-body.md)
- 2023-11-16 · [Кристаллы, прорастающие вдоль замерших путей частиц (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
