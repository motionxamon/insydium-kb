# Струйки частиц, вырывающиеся из разрушающегося кристалла (cached xpShatter, xpExplosiaFX Source tag, Advection, эмиссия с внутренних граней, xpJoin collider)

- Источник: NAB 2023 - INSYDIUM Training — Crystal Shatter - Part 2 — https://www.youtube.com/watch?v=EAtbWdajZ4E (2023-04-14)
- Хост / поколение: C4D; CPU X-Particles (xpExplosiaFX, xpCache, xpJoin, xpCollider tag); только viewport
- Задача: невидимый взрыв, который запускают частицы осколков, адвектирует десятки тысяч крошечных частиц, рождённых на внутренних гранях. Продолжение 2023-04-13_crystal-shatter-xpshatter-question-driven-breakup-part-a.

## Шаги
1. Эмиттер осколков: xpShatter General ▸ **Auto Particle Radius выкл.** → у всех радиус эмиттера **2 см** (на анимацию не влияет). Extended Data ▸ Physical: **Temperature 1, Fuel 1**. [▶ 2:31](https://youtu.be/EAtbWdajZ4E?t=151)
2. **xpCache** ("Cache Shatter Objects"): во внешние файлы, Compress, Build (300 F, ~15 с). При необходимости подправьте (xpSpeed 35 → **28**) и пересоберите с перезаписью. [▶ 3:11](https://youtu.be/EAtbWdajZ4E?t=191)
3. **xpExplosiaFX**: уменьшите домен ручками; Solver ▸ **Voxel Size 4 → 1 см** (частицы с топливом — 2 см). Display: Mode Temperature, вид **Grid**, LOD ~**120%** + прозрачность (Display ▸ Grid ▸ Back показывает воксели). [▶ 9:31](https://youtu.be/EAtbWdajZ4E?t=571)
4. Эмиттер осколков ▸ Tags ▸ тег **xpExplosiaFX Source** (по умолчанию). Simulation ▸ **Gravity выкл.** → нет плавучести (buoyancy). [▶ 17:32](https://youtu.be/EAtbWdajZ4E?t=1052)
5. Source tag ▸ **Velocity 300** → температура продолжает катиться вслед за движением частиц. Затем выключите display Mode (sim нужна только для адвекции, в рендер не идёт). [▶ 9:06](https://youtu.be/EAtbWdajZ4E?t=546)
6. Геометрия для эмиссии: дублируйте xpShatter, удалите у копии тег кэша и ссылку на эмиттер (статичная), переименуйте в "Shatter Advection Particles", **Shatter Selections ▸ Inner Faces** → тег выделения полигонов. [▶ 11:29](https://youtu.be/EAtbWdajZ4E?t=689)
7. Новый эмиттер "Emitter Advection": вкладка Modifiers, пипеткой → **исключите** все модификаторы осколков (минус). Shape **Object** = статичный shatter, Selection = внутренние грани, **Polygon Area**; **Object Chain: Connected Objects** (по умолчанию Any Object эмитирует только с одного осколка). Shot на 1-м кадре, **50,000**, Speed 0, **Radius 0.1**; отображение Dots. [▶ 14:04](https://youtu.be/EAtbWdajZ4E?t=844)
8. xpExplosiaFX ▸ **Advection** вкл. (по умолчанию) → частицы закручиваются вместе со скрытой симуляцией. [▶ 14:43](https://youtu.be/EAtbWdajZ4E?t=883)
9. Дублируйте эмиттер: ~**4,000** частиц в виде квадратов — для более крупных крапинок.
10. Коллизии: положите закэшированный xpShatter под **xpJoin**, повесьте на join **xpCollider tag**, **Bounce 0**, немного Friction → частицы больше не просачиваются сквозь ещё не разрушенную геометрию. [▶ 17:38](https://youtu.be/EAtbWdajZ4E?t=1058)
11. Итоговые количества: large **6,000**, small **150,000**. Второй xpCache, Inclusion **Include** только для двух эмиттеров адвекции (xpExplosiaFX кэшировать не нужно). В демо: 3 мин 21 с, ~3 GB, 301 кадр. Затем для проигрывания отключите модификаторы, эмиттеры, статичный shatter и xpExplosiaFX. [▶ 19:03](https://youtu.be/EAtbWdajZ4E?t=1143)

## Подводные камни
- Частицы для адвекции должны быть крошечными: при радиусе по умолчанию 3 см каждая при рождении перекрывает несколько осколков → бесконечные расчёты коллизий и сломанная симуляция.

## Как сейчас (новые инструменты)
GPU **nxExplosiaFX** (Fused 2025.4; Sources перечисляются в самом объекте, а не тегами) для управляющего дыма, **nxShatter** (бета 2026.1) для разрушения, объекты **nxCollider** в NeXus 2026. Стабильный путь в C4D — по-прежнему эта CPU-схема с адвекцией через xpExplosiaFX.
