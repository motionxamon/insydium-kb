# Рендер данных частиц NeXus в Octane (цвет, радиус → стекло)

- Источник: Top Tip Tuesday — Octane Particle Data — https://www.youtube.com/watch?v=9xKGBGKNyvc (2026-09-15)
- Хост / поколение: C4D, частицы NeXus (закэшированные) + Octane
- Задача: управлять материалами Octane для каждой частицы по запечённому цвету частиц и анимированному радиусу.

## Шаги
1. Закэшированная симуляция NeXus (вращающиеся/масштабирующиеся сферы). В Octane частицы не рендерятся, пока не добавить **Octane Object tag** на **xpEmitter** → вкладка Particle Rendering → включить **Geometry**.
2. Для правильного размера сделайте **Sphere радиусом 1 cm** (мало сегментов) и перетащите её в слот geometry тега → размер инстанса = радиус частицы.
3. Материал вешайте на **инстансируемую сферу**, а не на эмиттер.
4. Node editor: **Generator ▸ Instance Color** → Source: Particle, привяжите **xpEmitter**. Color Mode:
   - **Display Color** (по умолчанию) → запечённый цвет частиц во viewport (здесь случайный оттенок серого на частицу). Перемапьте через **Mapping ▸ Gradient Map** (например, пресет бирюзовый→оранжевый) → цвет base layer.
   - **Radius** → задайте Min/Max радиуса вашей симуляции (здесь 1–70 cm); на выходе градиент (или перемапьте).
5. Стекло для крупных частиц: продублируйте Instance Color в режиме Radius с **Min 50 / Max 60** → чёрный ниже 50, белый выше 60 → в **Transmission ▸ Weight** у Standard Surface. Большие сферы становятся стеклом и обратно по мере анимации радиуса.
6. Specular roughness 0 для блестящих шаров.

## Заметки
- То же самое в Redshift: ноды RS Particle/User Data (см. рецепты "Particle Data in Redshift" / "Rendering Particle Data").
- Всё, что хотите рендерить, запекайте в симуляции в цвет или радиус частиц (nxColor, nxScale, nxQuestion) — рендереры читают их надёжно.
