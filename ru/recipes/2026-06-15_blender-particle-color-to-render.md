# Цвет частиц в рендере Cycles и Eevee (экспорт Point Cloud из nxEmitter + атрибуты Geometry Nodes)

- Источник: NeXus for Blender Quick Guide — Render Color — https://www.youtube.com/watch?v=Hx0g1V9-HqM (2026-06-15)
- Хост / поколение: Blender (NeXus for Blender, G3); nxEmitter Export, nxScale, nxPush, nxAttract, nxColor; Cycles + Eevee
- Задача: растущие, плотно упаковывающиеся сферы со случайными цветами из градиента, которые остаются процедурными в рендере.

## Исходная сцена
**nxEmitter** Sphere минимального размера, **Shot 100**, скорость 0; режим Display **Spheres**. **nxScale** Range 0 → **0.4** (большой разброс) примерно за 8 кадров; **nxPush** Distance Mode **Particle Radius**, полная сила; **nxAttract** к центру (движение «толкай/тяни»). **nxColor** Gradient by Parameter → **Random**, градиент, например, Thermal.

## Шаги
1. Emitter ▸ Display: Show Particles выкл. (GPU-отображение только во viewport, в рендер не идёт). [▶ 3:43](https://youtu.be/Hx0g1V9-HqM?t=223)
2. Emitter ▸ **Export ▸ Point Cloud**, сдвиньтесь на кадр → point cloud следует за частицами с правильным радиусом. [▶ 3:56](https://youtu.be/Hx0g1V9-HqM?t=236)
3. Набор атрибутов **Basic** = rotation, velocity, color, radius (переключите на **Custom**, чтобы выбрать другие данные частиц). Проверьте имена в Spreadsheet/просмотре данных: атрибут цвета называется **«Color»** (с заглавной C) — написание должно совпадать точно. [▶ 4:42](https://youtu.be/Hx0g1V9-HqM?t=282)
4. Автоматически созданное дерево Geometry Nodes уже использует Named Attribute «radius» → радиус точки. [▶ 6:43](https://youtu.be/Hx0g1V9-HqM?t=403)
5. Свет: area light, **Track To** на эмиттер, Normalize выкл., strength ~150. [▶ 7:34](https://youtu.be/Hx0g1V9-HqM?t=454)
6. **Cycles**: точки автоматически рендерятся чистыми сферами. Новый материал («color sphere»); в GN добавьте **Set Material**; в shader’е — нод **Attribute** «Color» → Base Color. Вживую: правки градиента nxColor сразу обновляют рендер. [▶ 10:04](https://youtu.be/Hx0g1V9-HqM?t=604)
7. **Eevee** рисует точки ромбами → инстансьте геометрию: GN **Instance on Points** со скрытой гладкой UV sphere (Object Info), атрибут радиуса подайте в **Scale**. [▶ 12:03](https://youtu.be/Hx0g1V9-HqM?t=723)
8. Инстансы рендерятся чёрными, пока в shader’е тип нода Attribute не переключить с **Geometry** на **Instancer**. [▶ 14:40](https://youtu.be/Hx0g1V9-HqM?t=880)

## Как сейчас (новые инструменты)
В бете NeXus 2026.1 для Blender добавлен **Particle Info node** для shader’ов/Geometry Nodes, который читает данные частиц напрямую.
