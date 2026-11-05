# Гранулярный текст, который разносят порывы ветра с маппингом на анимированный цвет Voronoi

- Источник: Top Tip Tuesday — Advanced Granular Sim — https://www.youtube.com/watch?v=zyN7ERz7yuw (2026-06-02)
- Хост / поколение: C4D, NeXus (nxFluids SPH Granular, nxWind Von Karman, Mapping) + CPU xpColor (для 3D-шейдеров Maxon)
- Задача: песчаные буквы, которые под порывистым ветром осыпаются неровными кусками.

## Шаги
1. Эмиттер: Object = Text (объём), **Shot – Hexagonal**, Full Lifespan, speed 0, radius 1 (~100 k для черновика). Количество частиц задаётся радиусом: 0.4 → ~1.5 M; 0.2 → 8–10 M для крупных планов.
2. **xpColor** (CPU) с **Noise shader** Maxon: **Cell Voronoi**, global scale ~330, сильный low/high clip → пятнистый чёрно-белый цвет на частицах. (CPU-модификатор взят потому, что он сэмплит шейдеры Maxon в полном 3D; у nxColor GPU-нойзы.)
3. Чтобы узор иногда перескакивал: ключи на **Seed** нойза (+1 каждые 2 кадра, linear, Track After: Continue) и ключи на **Enabled** у xpColor вкл./выкл. импульсами (кадры 0–2, 50, 100, 150) → перекраска только в нужные моменты.
4. **nxFluids SPH → Granular**; Substeps **30, adaptive выкл.**; Friction ~50, Stability ~3 (для мелких частиц поднимите до ~6), Cohesion ~7. Добавьте **nxGravity**.
5. **nxWind** в режиме **Von Karman**, диагональное направление, Strength ~3500 с высокой вариацией, турбулентность пониже, добавьте Friction Velocity.
6. **Вкладка Mapping** у nxWind: Wind Strength ← **Color (Brightness)**, Range Min 0.5 → полная сила на 0.9 → сдуваются только светлые пятна, тёмные остаются.
7. Плавное начало: ключи на Wind Strength от 0 до полной примерно за 15 кадров (дважды замаппить нельзя).
8. Рендерьте частицы (Redshift) для пыльных комков; цвет — только управляющий параметр, он не рендерится.

## Как сейчас (новые инструменты)
nxMPM Sand/Snow (2026.1 beta) даёт более физичное слипание; идея с маппингом цвета по-прежнему работает через Mapping.
