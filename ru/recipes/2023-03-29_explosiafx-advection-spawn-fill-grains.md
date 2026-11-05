# Дым разрывает песочную цифру без дыр (advection в xpExplosiaFX, xpFlowField, заполнение xpSpawn, xpScale + kill через Question)

- Источник: Maintenance Training — XP Countdown - Series 2 - xpExplosiaFX Advection 02 — https://www.youtube.com/watch?v=isCt2UKxPtM (2023-03-29)
- Хост / поколение: C4D; полностью CPU X-Particles (xpExplosiaFX, xpFlowField по сплайнам, xpFluidFX granular, xpSpawn, xpScale, xpQuestion/экшн Change Life, xpCache); превью через hardware OpenGL
- Задача: доработать осыпание песочной «2», чтобы струи EFX вытягивали колючие щупальца, а цифра оставалась читаемой, и потом растворить песок вместе с дымом.

## Исходная сцена
Сцена из прошлого видео: гранулярный xpFluidFX на коллайдере «2»; xpFluidFX выключается ключами на F75→76, дальше работает advection от EFX; частицы EFX летят по дугам **xpFlowField**, построенного по сплайнам. Песок в режиме Dots для быстрого плейбэка.

## Шаги
1. Ключами выключить **xpGravity** на том же кадре, что и xpFluidFX (75 вкл, 76 выкл) — иначе песок проседает, как только жидкостный солвер останавливается. [▶ 1:38](https://youtu.be/isCt2UKxPtM?t=98)
2. Чуть глубже вдвинуть объект-источник EFX в песок, чтобы струи цепляли крайние частицы. [▶ 3:06](https://youtu.be/isCt2UKxPtM?t=186)
3. **Заполнить дыры от advection через xpSpawn**: Generate ▸ xpSpawn → создать spawn-эмиттер (на время настройки розовый). Position = исходная частица, Direction относительно источника, Speed **inherit × 0.5**, Spawn Number **10**/с. Вкладка Inherit: **Color + Radius**. [▶ 18:09](https://youtu.be/isCt2UKxPtM?t=1089)
4. Тайминг через **Mapping** (а не ключи): параметр Spawn Number, источник **Scene Time**, диапазон **75 → 116**; кривая сразу вверх, затем спад до 0 к F116. [▶ 42:11](https://youtu.be/isCt2UKxPtM?t=2531)
5. Spawn-эмиттер ▸ Modifiers: переключить **Exclude → Include** и оставить только xpExplosiaFX + xpFlowField (позже xpScale) — сам spawn-модификатор не включаем, чтобы не было рекурсивного спавна. [▶ 46:01](https://youtu.be/isCt2UKxPtM?t=2761)
6. У spawn-модификатора **Falloff ▸ Box field** вокруг цифры, чтобы уже падающий песок не спавнил (экономия расчёта). [▶ 15:46](https://youtu.be/isCt2UKxPtM?t=946)
7. Подвох: частицы источника EFX застревали на коллайдере «2» для песка → в теге коллайдера **Exclusions** = эмиттер источника EFX. [▶ 22:14](https://youtu.be/isCt2UKxPtM?t=1334)
8. Дуги плотнее: выделить точки малоточечных сплайнов flow field и отмасштабировать их внутрь. [▶ 23:38](https://youtu.be/isCt2UKxPtM?t=1418)
9. Сходящиеся векторы давали тонкую линию дыма по −Z → **xpFlowField Falloff ▸ Box field** в центре, Remapping **Invert**, чтобы потоки проходили сквозь друг друга. [▶ 26:41](https://youtu.be/isCt2UKxPtM?t=1601)
10. Продакшн-разрешение: EFX **Voxel Size 6 → 2 см** (для финального качества советуют 1 см); радиус частиц источника 8 (вариация 2) → **5**. Display только Smoke, LOD 80. [▶ 29:58](https://youtu.be/isCt2UKxPtM?t=1798)
11. EFX Simulation ▸ **Smoke Dissipation**: ключи 0 на F130 → 0.5 на F150 (малые значения действуют сильно). **Vorticity 15%**, радиус **2.5** для мелких завихрений (перебор = «пушистый» дым). [▶ 36:29](https://youtu.be/isCt2UKxPtM?t=2189)
12. Растворение песка: **xpScale** с отрицательным Radius Change (по умолчанию +0.2 см/с увеличивает радиусы → давление жидкости разбрасывает песок), Variation **75%**. Смотреть в Display Circles Filled (Dots не показывают радиус). [▶ 40:52](https://youtu.be/isCt2UKxPtM?t=2452)
13. Удалять сжавшиеся песчинки: на эмиттере **Questions ▸ Particle Radius = 0** → **Action ▸ Change Life (Kill)**; тот же question перетащить в spawn-эмиттер и добавить xpScale в его список Include. Счётчик в HUD теперь падает. [▶ 45:05](https://youtu.be/isCt2UKxPtM?t=2705)
14. Radius Change замапить по **Scene Time 120 → 160** (возраст у песка и заспавненных частиц разный); уменьшить максимум (≈ −0.1) и сгладить кривую, чтобы песок исчезал постепенно. [▶ 47:04](https://youtu.be/isCt2UKxPtM?t=2824)
15. Варианты: сменить **Advanced ▸ Seed** у эмиттера EFX. Щупальца сильнее: уменьшить источник EFX и сильнее утопить его в песок. [▶ 55:17](https://youtu.be/isCt2UKxPtM?t=3317)
16. **xpCache** (сначала уникальные имена объектов), 220 F → ~6.5 мин, ~5 GB в демо; у закэшированных эмиттеров включить **Force Display**, чтобы сменить режим отображения. Тайминг оценивать по **Hardware OpenGL** рендеру (720p, frame rate = проектные 30 fps). [▶ 58:05](https://youtu.be/isCt2UKxPtM?t=3485)

## Подводные камни
- Разные системы + теги коллайдеров: всегда проверять исключения, иначе частицы другой системы тоже сталкиваются.
- Mapping по Scene Time держит спавн/растворение синхронно у эмиттеров с разным возрастом частиц.

## Как сейчас (новые инструменты)
GPU **nxExplosiaFX** (Fused 2025.4) с **Dynamics ▸ Particle Advection**, **nxSpawn** (2026.1 beta) или Spawn в nxQuestion для заполнения, nxScale + Kill в nxQuestion для растворения; **nxWarp** Path/Flow (2026.1 beta) может формировать потоки дыма вместо flow field по сплайнам; сам песок — через nxMPM. См. 2026-09-01 и 2023-08-15.
