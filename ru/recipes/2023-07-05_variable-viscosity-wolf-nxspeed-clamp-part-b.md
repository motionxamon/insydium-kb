# Горячая/холодная жидкость с переменной вязкостью на голову волка (nxFluids SPH + nxConstraints Viscosity + nxQuestion object distance + nxBlend + nxSpeed clamp с mapping по цвету)

- Источник: INSYDIUM LIVE! — July 2023 – NeXus, Taiao, TerraformFX & MeshTools — https://www.youtube.com/watch?v=6WjDq_87uck (2023-07-05)
- Хост / поколение: C4D; G2 NeXus внутри X-Particles (Fused 2023.3 Data Mapping + вопросы Document в nxQuestion) — GPU
- Задача: горячая жидкая масса остывает и липнет там, где касается головы волка, затем снова тает под свежей горячей струёй; отставшие частицы стекают вниз.

## Исходная сцена
xpEmitter Circle, radius **20 cm**, плоскость эмиттера **−Y**, эмиссия **Hexagonal**, скорость 0, радиус частиц **1 cm**, все белые (цвет = температура, поэтому без раскраски по скорости). **nxGravity**; теги коллайдера на волке и полу.

## Шаги
1. **nxFluids** SPH, всё по умолчанию, кроме **Viscosity 100**, **Surface Tension 40** (образуются капли; пока не тягуче).
2. **nxConstraints** под nxFluids (порядок в иерархии важен: сначала решается жидкость). Iterations **3** (обычная стартовая точка автора). Слой **Viscosity** (не пружинные connections): Connection Limit **3**, Radius **20 cm** → уже как мёд и быстро; огромные substeps / итерации вязкости не нужны.
3. **nxQuestion** ▸ категория **Document** ▸ **Object Distance** (полигоны волка) **< 3 cm** → **Set Color** чистый синий = холодная. Убрать friction у коллайдера волка.
4. **nxBlend** (под гравитацией): Color, Distance **20 cm**, Strength **1000** (максимум), длительность **40** кадров (по умолчанию 300) → смешение синего/белого = теплообмен. Тяжёлый поиск соседей, на GPU быстро.
5. **nxSpeed** (blend держать последним в стеке): операция **Acceleration** с **Exponential off** (скорость не меняется) и включённым **Clamp Max Speed**.
6. nxSpeed Mapping ▸ **Color ▸ Red channel → Max Speed**: red 0 (синие/холодные) → 0 cm/s, red 1 (белые/горячие) → **10000** (никогда не ограничивает). Берём красный, а не синий — у белого и синего синий канал полный, только красный проходит 0–1.
7. Исправление «зависших»: в эмиттере Groups ▸ две группы, режим **First Group Only**; в nxSpeed Groups Affected так, чтобы **группа 2 не ограничивалась**.
8. Копия вопроса расстояния: **Object Distance > 11 cm** дочерним к вопросу **Particle Age > 15 frames** (оператор **And**; 30 F оказалось слишком долго) → Action **Set Group 2**. Без условия по возрасту все новорождённые сразу попадают в группу 2, и ограничение пропадает.
→ Холодная масса липнет, горячие струи её растапливают, освобождённые частицы стекают на пол.

## Как сейчас (новые инструменты)
Fused 2025.4 **nxFluids FLIP/APIC** с mapping переменной вязкости; 2026.1 beta добавляет неньютоновские Flow Index / Yield Stress, Wall Friction и **Mixer** по группам. Более поздние версии в Top Tip: "Hot/Cold Variable Viscosity" (2025-09-09), "Chocolate Setting" (2026-02-03). В 2026.1 слой nxSpeed называется **Acceleration**.
