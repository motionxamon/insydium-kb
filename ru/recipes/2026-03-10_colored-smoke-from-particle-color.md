# Цветной дым от анимированного цвета частиц (канал цвета nxExplosiaFX → Redshift)

- Источник: Top Tip Tuesday — Color Smoke — https://www.youtube.com/watch?v=KimysoJRI9I (2026-03-10)
- Хост / поколение: C4D, nxExplosiaFX + nxColor (Distance from Object) + Redshift
- Задача: дым, окрашенный в тот цвет, который в данный момент у частиц-источников.

## Шаги
1. Короткоживущие частицы из эмиттера-окружности + турбулентность служат источником EFX. [▶ 0:12](https://youtu.be/KimysoJRI9I?t=12)
2. nxExplosiaFX **вкладка Solver → включаем канал Color** (по умолчанию выключен ради экономии памяти). [▶ 1:26](https://youtu.be/KimysoJRI9I?t=86)
3. Sources → эмиттер → **Color 100%** (Color From: particles/object). [▶ 1:37](https://youtu.be/KimysoJRI9I?t=97)
4. Превью: Display Draw Mode **Volume Slicing**, Display Channel **Color**. (Цвет — это оттенок; в ray-marched отображении по-прежнему видна форма дыма.) [▶ 2:05](https://youtu.be/KimysoJRI9I?t=125)
5. Анимируем цвет частиц: слой **nxColor** **Distance from Object** → анимированный Null; градиент, например, оранжевый (дальше 300 cm) → жёлтый → зелёный → синий (вблизи). [▶ 4:36](https://youtu.be/KimysoJRI9I?t=276)
6. Объёмный материал Redshift: существующая связка `Volume Scalar Attribute (smoke) → Density`; добавляем **Volume Color Attribute** (пресет **EFX ▸ color**) → **Scatter Color**, Scale ~7 (сырые значения цвета тёмные). [▶ 6:53](https://youtu.be/KimysoJRI9I?t=413)

## Примечания
Работает и с цветом объекта. Тот же канал цвета может окрашивать пламя.
