# Быстрая вязкая струя шоколада/мёда (xpFluidPBD + xpConstraints Viscosity, эмиссия Hexagonal)

- Источник: Maintenance Training — Dynamics - Constraints - Viscous Fluids Tutorial — https://www.youtube.com/watch?v=rhFYjdNe2XA (2023-06-12)
- Хост / поколение: C4D; G1 CPU X-Particles (**xpFluidPBD** + **xpConstraints** в папке Dynamics системы)
- Задача: тягучая жидкость, сохраняющая складки (шоколад на вафле для продуктового шота), без медленной высокоточной вязкости.

## Исходная сцена
Гравитация вниз; коллайдеры: плоскость пола + вытянутый куб («вафля»). Эмиттер Circle, плоскость эмиттера **−Y**. Отображение Circles filled, градиент синий→белый по **Speed**, белый на **600 cm/s**.

## Шаги
1. **xpConstraints ▸ Viscosity** включить (это тип соединения) — частицы связываются (проверка через Display Constraints).
2. Добавить **xpFluidPBD** для основной массы жидкости. Одной вязкости PBD (например, **50%**) хватает на тягучесть, но масса не держится; с включённой вязкостью constraints — держится.
3. Stiffness вязкости constraints **98** → держит форму.
4. Режим эмиссии **Hexagonal** (сделан для жидкостей: частицы рождаются без пересечений, иначе солвер их расталкивает / взрывает).
5. Щели между порциями эмиссии: Connection Limit **16** мало → **40**; и уменьшить **Spacing** в hexagonal, чтобы частицы рождались с перекрытием — constraints удерживают их против расталкивания PBD. Побочный эффект — вспучивание → уменьшить эмиттер. Stiffness снизить до **95**.
6. Ctrl+D Project Settings ▸ X-Particles: **Subframe Steps 3**, **Iterations 3** → жёстче пружины, сим медленнее.
7. Струя-лента: эмиттер **Rectangle**, очень тонкий; радиус частиц в Hexagonal **2.5** (больше частиц); spacing немного обратно вверх; Stiffness **90**, Connection Limit **20** → складывающиеся ленты (где связей мало — местами полосы).
8. Выше разрешение: больше частиц быстрее расходуют связи → Connection Limit **100–150** и меньше spacing для детальных складок и заломов.

## Подводные камни
- Мало связей = полосатые щели / полосы от subframe; слишком жёстко = нет течения.
- Жёсткость constraints зависит от substeps/iterations.

## Как сейчас (новые инструменты)
GPU: вязкость **nxFluids FLIP/APIC** (Fused 2025.4) или неньютоновские **Yield Stress / Flow Index** в 2026.1 beta — для складок, которые держатся; путь G2 = nxFluids SPH + слой Viscosity в nxConstraints (см. "Viscous Folding Ribbon", "Gloopy Fluids Mix").
