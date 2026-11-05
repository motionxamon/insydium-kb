# Искры фейерверка от рукописного текста (nxScale + убийство через nxQuestion + ограничение nxSpeed, замапленное на Radius)

- Источник: Top Tip Tuesday — Particle Sparks — https://www.youtube.com/watch?v=PYtRwy_bbCE (2024-12-31)
- Хост / поколение: C4D; NeXus G2 (nxGravity, nxScale, nxQuestion, nxSpeed, nxTurbulence) на xpEmitter + CPU-утилита xpSplineGrowth; аддитивный материал + motion blur в рендере
- Задача: горячие искры, которые слетают с надписи "Happy New Year", уменьшаются, замедляются в зависимости от размера и гаснут.

## Исходная сцена
- Текстовый сплайн как направляющая; во фронтальной ортопроекции (F5) обведите его инструментом **Sketch** (один объект-сплайн, небрежные штрихи — норм).
- **xpEmitter ▸ Object** mode, нарисованный сплайн, эмиссия с **Edges**; Rate 1000/s, Speed 100 (var 50), Radius 2 (var 1).
- Display Circle + Gradient by Parameter ← Radius (авто): крупные = белые, мелкие = оранжевые.

## Шаги
1. **nxGravity**, чтобы частицы падали.
2. **nxScale** под гравитацией: отрицательное изменение во времени (Min −0.2, много вариации), **Clamp Limit выкл.** → искры уменьшаются до нуля. [▶ 2:52](https://youtu.be/PYtRwy_bbCE?t=172)
3. **nxQuestion**: если **Radius = 0** → Action **Kill** (вместо Set Color по умолчанию). [▶ 3:32](https://youtu.be/PYtRwy_bbCE?t=212)
4. **nxSpeed** последним в стеке: Operation Acceleration со значением **0**, включите **Clamp Max Speed** ~400 cm. [▶ 4:22](https://youtu.be/PYtRwy_bbCE?t=262)
5. nxSpeed ▸ **Mapping ▸ Radius map** (диапазон 0–3 cm) → параметр **Clamp Max Speed**; у мелких искр ниже предел скорости. Приподнимите нижний край кривой, чтобы они никогда полностью не останавливались. [▶ 5:16](https://youtu.be/PYtRwy_bbCE?t=316)
6. Увеличьте эмиссию (~50,000), переключите отображение на **Lines** (растягиваются по скорости) — получится вид искр. [▶ 6:22](https://youtu.be/PYtRwy_bbCE?t=382)
7. **nxTurbulence** *над* nxSpeed (чтобы ограничение побеждало): Curl, сильная, низкий persistence, больше octaves → крупные волнистые завихрения. Предел скорости до ~500. [▶ 6:34](https://youtu.be/PYtRwy_bbCE?t=394)
8. Проявление/стирание: **xpSplineGrowth** дочерним к сплайну; ключи 0% F0 → 100% F60, держим до F100, обратно 0% F160. [▶ 7:37](https://youtu.be/PYtRwy_bbCE?t=457)

## Подводные камни
- Порядок важен: gravity → scale → turbulence → speed clamp последним.
- Параметр ограничения в Mapping — это "Clamp Max Speed", а не экспоненциальное значение рядом с ним.

## Как сейчас (новые инструменты)
Тот же стек на объектах G3 (nxEmitter + модификаторы; **nxConvert** в бете 2026.1). Учтите переименование в 2026.1 Beta 3: слой nxSpeed теперь называется **Acceleration**.
