# Огни города, расползающиеся по рёбрам зданий (nxInfectio + группы)

- Источник: Top Tip Tuesday — Particle Edge Infection — https://www.youtube.com/watch?v=veRxUHtrnFA (2025-10-14)
- Хост / поколение: NeXus (nxInfectio, nxColor Distance from Object) + клонеры MoGraph в xpJoin
- Задача: wireframe-город, загорающийся здание за зданием.

## Шаги
1. Клонеры MoGraph с городом внутри **xpJoin**. Object эмиттера = join, **Emit From Edges**, **Shot 200 000**, speed 0, чёрные частицы. [▶ 1:06](https://youtu.be/veRxUHtrnFA?t=66)
2. **nxInfectio** → **Add Seed Object** (объём — частицы внутри стартуют заражёнными), Search Radius 25 cm, Max Infected 3. [▶ 2:08](https://youtu.be/veRxUHtrnFA?t=128)
3. По умолчанию **Incubation Mode = Use Particle Color** — чёрный никогда не заражает! → переключите на **Set From Incubation Rate**, низкий rate + высокая вариация (органичное распространение). [▶ 3:18](https://youtu.be/veRxUHtrnFA?t=198)
4. **Infected Lifespan** по умолчанию 300 F убивает частицы (удобно для стирания) → выставьте длину сцены (500). [▶ 4:30](https://youtu.be/veRxUHtrnFA?t=270)
5. **Color Mode: Use Groups** → Incubating = Group 1, Infected = Group 2; **Group Color Change: No Color Changes** (только смена группы). [▶ 5:53](https://youtu.be/veRxUHtrnFA?t=353)
6. **nxColor** с **Groups Affected 1 & 2**: слой **Distance from Object** (Null на крышах), зелёный вдали → синий вблизи на дистанции 600 cm → светящиеся рёбра с градиентом по высоте. [▶ 7:40](https://youtu.be/veRxUHtrnFA?t=460)
7. Рендерьте частицы как эмиссивные огни поверх тёмных зданий. [▶ 7:59](https://youtu.be/veRxUHtrnFA?t=479)
