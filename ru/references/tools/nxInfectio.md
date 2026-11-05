# nxInfectio — карточка инструмента

Встречается в **7** рецептах · 2023-03-29 → 2025-10-14 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxInfectio** → **Add Seed Object** (объём — частицы внутри стартуют заражёнными), Search Radius 25 cm, Max Infected 3. [▶ 2:08](https://youtu.be/veRxUHtrnFA?t=128) — *[2025-10-14](../../recipes/2025-10-14_city-lights-edge-infection.md)*
- **nxInfectio** ▸ **Add Seed Object**; сдвиньте seed к краю трубки — заражение расходится оттуда (по умолчанию — просто круговой рост). [▶ 1:26](https://youtu.be/xGxf_IIIekY?t=86) — *[2025-05-22](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)*
- Режим nxInfectio **Fixed Value → Use Groups**; через Ctrl добавьте группу инкубации и группу заражённых (группа 2 = те, что будут отслаиваться). [▶ 3:14](https://youtu.be/xGxf_IIIekY?t=194) — *[2025-05-22](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)*
- **nxInfectio** с 3 **seed objects** наверху. Светлые частицы заражаются быстрее; чтобы ускорить, поднимите search radius и допустимое число заражений на частицу. [▶ 1:29](https://youtu.be/DsZ56QYQ2cY?t=89) — *[2024-06-11](../../recipes/2024-06-11_granular-crumble-infectio-groups.md)*
- **nxFluids** ниже nxInfectio, солвер **SPH** (открывает **Granular**): **Friction 100%**, **Stability 10**, **Cohesion 5**; substeps 3 для превью. [▶ 3:31](https://youtu.be/DsZ56QYQ2cY?t=211) — *[2024-06-11](../../recipes/2024-06-11_granular-crumble-infectio-groups.md)*
- **nxInfectio** ▸ **Add Seed Object** (сферический объём) — поставьте его рядом с брюхом. Оранжевые = заражённые, синие = в инкубации. [▶ 1:34](https://youtu.be/Be90jYTwF0c?t=94) — *[2023-12-12](../../recipes/2023-12-12_nxinfectio-groups-peel-constraints.md)*
- nxInfectio ▸ **Infected Lifespan 300 → 150** кадров, чтобы сдутые куски умирали. [▶ 5:47](https://youtu.be/Be90jYTwF0c?t=347) — *[2023-12-12](../../recipes/2023-12-12_nxinfectio-groups-peel-constraints.md)*

## Все рецепты (7)
- 2025-10-14 · [Огни города, расползающиеся по рёбрам зданий (nxInfectio + группы)](../../recipes/2025-10-14_city-lights-edge-infection.md)
- 2025-05-22 · [Отслаивание с поверхности, как у краски (группы nxInfectio + nxWind/nxTurbulence + nxConstraints Distance)](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)
- 2024-06-11 · [Статуя рассыпается в песок по мере распространения заражения (группы nxInfectio + nxFluids SPH Granular + nxSpeed Max Speed 0)](../../recipes/2024-06-11_granular-crumble-infectio-groups.md)
- 2023-12-12 · [Отслаивание, управляемое заражением (nxInfectio Use Groups + nxWind/nxTurbulence на группе заражённых + разрыв nxConstraints Distance)](../../recipes/2023-12-12_nxinfectio-groups-peel-constraints.md)
- 2023-11-16 · [Астероиды на орбитах планет + расползающееся свечение (nxAttract Force/Speed Limit, xpColor с полями из частиц, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-06-26 · [Обзор функций: новые модификаторы NeXus — nxUpres, nxInfectio, nxWave, nxAvoid, nxFlock, режимы nxBlend, nxFoam на кэшах, nxWind Von Karman (Fused 2023.3)](../../recipes/2023-06-26_feature-notes-nexus-modifiers-2023-3.md)
- 2023-03-29 · [Пересимуляция огня в высоком разрешении из заспавненных частиц-топлива (xpSpawn на заражённых группах, cache Include, более мелкие воксели xpExplosiaFX)](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)
