# Рендер nxExplosiaFX в Octane через OpenVDB

- Источник: Top Tip Tuesday — Octane EFX — https://www.youtube.com/watch?v=gfcEhBMSgkI (2026-05-12)
- Хост / поколение: C4D, Fused 2025.4+ (nxExplosiaFX) + Octane
- Задача: дым и огонь в Octane, совпадающие с тем, что видно в viewport EFX.

## Шаги
1. **xpCache** → EFX Format **OpenVDB**; только каналы **Smoke (density) + Temperature**. Velocity — только если нужен motion blur или адвекция (≈3× размер файлов).
2. Объект Octane **VDB Volume** → вкладка VDB → выбери первый файл → **Calculate** (находит все кадры). Он покажет grid 0 = density, grid 1 = temperature; Grid mapping сам назначит Absorption/Scatter = density, Emission = temperature.
3. **Отрази по Z**: VDB Volume Coordinates → Scale Z = −1 (соглашение об осях отличается от EFX).
4. Medium: переключи пресет **Fog → Fire**; правь в нодовом редакторе Octane:
   - **Texture Emission Power** ≈ 0.01 (по умолчанию пересвечено); 0.1 = ярче, подсвечивает пол.
   - **Volume Gradient** → Emission Ramp: поставь **Max ≈ 6500** (максимальная температура твоей симуляции; дефолтные 35 обрезают всё в жёлтый). Добавь **чёрную точку** на холодном конце → выгоревший дым не светится; используй пресет «flame» или любой цвет (фиолетовый = магический огонь).
   - Volume Medium **Volume Step % ≈ 7** (меньше = плотнее/детальнее, но медленнее).
5. Тонкий дымок: новый Volume Gradient (чёрный→белый, Max 1) → **Absorption Ramp + Scattering Ramp**; выключи **Invert Absorption**; чуть сдвинь чёрную точку к ~0.5.

## Правило
Узнай реальный максимум температуры своей симуляции (проверка через EFX Display ▸ Flame Emit Above T) и впиши его в Max градиента.
