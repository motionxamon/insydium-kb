# Турбулентное появление текста из частиц (nxCover Edges + слабая сила слоя + удержание Spring, nxColor по Direction)

- Источник: Top Tip Tuesday — Particle Spline Reveal — https://www.youtube.com/watch?v=dL2bCkQf5HM (2024-05-21)
- Хост / поколение: C4D; xpEmitter + NeXus GPU (nxCover — новинка 2024.2, nxTurbulence, nxColor)
- Задача: поток частиц закручивается и осыпает контур слова «COVER».

## Шаги
1. xpEmitter Rate, стоп на 450 F, **4000/frame**, speed 50 (вар. 10). Поставьте **width и height 0** → точечная эмиссия, детали намного тоньше и воздушнее.
2. **nxCover**: текстовый сплайн, **Edges**; движение использует скорость частиц; **Hold Time 0** = держит бесконечно.
3. **nxTurbulence** Voronoi, strength 20 → только волны скорости, пока доминирует nxCover.
4. Снизьте **strength** слоя nxCover **до ~19%**, чтобы турбулентность успевала их закрутить, прежде чем они осядут.
5. **nxColor ▸ Gradient by Parameter** (пресет сине-зелёный) с маппингом на **Direction ▸ Heading** (читается лучше, чем Age).
6. Буквы потолще: удержание в nxCover **Attract** (по умолчанию, тормозит с 50 cm) → **Spring**, damping **15%**; увеличьте **spring length** для случайной осыпи вокруг краёв. Больше damping/stiffness = меньше колебаний.

## Как сейчас (новые инструменты)
nxCover по-прежнему актуален; в 2026.1 появились списки falloff для каждого слоя, чтобы локализовать cover.
