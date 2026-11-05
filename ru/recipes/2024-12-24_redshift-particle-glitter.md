# Праздничные блёстки из вращающихся частиц (инстансы custom-объектов в Redshift: плоские платоновые хлопья)

- Источник: Top Tip Tuesday — Particle Glitter — https://www.youtube.com/watch?v=ouo1xie_Spk (2024-12-24)
- Хост / поколение: закэшированное появление частиц NeXus (см. 2024-12-17) + инстансинг через Redshift Object tag
- Задача: искрящаяся золотая/серебряная пыль и хлопья.

## Исходная сцена
Два одинаковых закэшированных эмиттера: "small" 500 000 частиц (r 1 ± 0.5) и "large" 20 000. **Extended Data ▸ Use Rotation, Random**, **Simple Spin** понемногу + вариация — именно вращение заставляет блики мерцать.

## Шаги
1. Два длинных тонких **Redshift Area lights** (лёгкий зелёный / красный оттенок) + камера Redshift с DOF. [▶ 1:47](https://youtu.be/ouo1xie_Spk?t=107)
2. Геометрия хлопьев: **Platonic** r 3 cm → сделать редактируемым → сплющить по Y; сделать 3 копии. [▶ 2:36](https://youtu.be/ouo1xie_Spk?t=156)
3. Оба эмиттера ▸ **Redshift Object tag ▸ Particles ▸ Custom Objects**, Distribution **Random**. Scale ~0.2 (large) и ~0.05 (small). [▶ 3:04](https://youtu.be/ouo1xie_Spk?t=184)
4. Материалы: **серебро** (белый, metalness 1, очень низкая roughness); **золото** (то же, оранжевый); **diffuse** (высокая roughness, очень тёмный цвет — рассеивает блик, добавляет глубины). [▶ 6:20](https://youtu.be/ouo1xie_Spk?t=380)
5. Тег large: серебро + золото + diffuse; тег small: серебро + diffuse. [▶ 6:17](https://youtu.be/ouo1xie_Spk?t=377)
6. Оценивайте эффект в движении (на стоп-кадрах блёстки не мерцают); цвет света формирует боке. [▶ 7:48](https://youtu.be/ouo1xie_Spk?t=468)
