# Многослойный ч/б цвет → перекрашенное аддитивное пламя (nxColor Age × Heading × Pitch, Redshift Color User Data)

- Источник: Top Tip Tuesday — Particle Color Layers — https://www.youtube.com/watch?v=VHGhFAwDypM (2024-09-10)
- Хост / поколение: C4D; NeXus G2 (nxTurbulence, слои **nxColor**) на xpEmitter; xpCache; **Redshift** (point instances, аддитивно)
- Задача: закрученное пламя, где цвет меняется в зависимости от направления, а не просто плоский градиент по возрасту.

## Исходная сцена
xpEmitter Rectangle **50 × 0**; Rate, life **70** (var 15), **2,000/frame**, speed **100**, radius **3**. Камера сверху.
**nxTurbulence Wavy**, Strength **11**, Octaves на максимум, Persistence **20** → мелкая детализация плюс крупные завихрения.

## Шаги
1. Эмиттер: **Redshift Object tag ▸ Particles ▸ Point instances** (маленький масштаб). [▶ 1:04](https://youtu.be/VHGhFAwDypM?t=64)
2. Материал RS Standard: base color выкл., reflection выкл., Emission **2**. **Color User Data** (пресет Particle ▸ Color) → **Geometry Opacity** = аддитивно, чёрный = невидимо. [▶ 1:40](https://youtu.be/VHGhFAwDypM?t=100)
3. Слой **nxColor** "age": Gradient by Parameter **Age**, ч/б от чёрного к белому; сдвиньте белый узел пораньше. [▶ 2:28](https://youtu.be/VHGhFAwDypM?t=148)
4. В материале вставьте **Color Ramp** (цвет частицы → alt input → opacity); загрузите цветной пресет; добавьте чёрный узел в начале, чтобы линия эмиссии плавно проявлялась. [▶ 3:33](https://youtu.be/VHGhFAwDypM?t=213)
5. Дублируйте слой → "heading": параметр **Direction**, ось **Heading**; белый узел подтяните внутрь, чёрный осветлите до серого; Blend **Multiply** поверх age. [▶ 6:10](https://youtu.be/VHGhFAwDypM?t=370)
6. Дублируйте → "pitch": Direction по оси **Pitch**, Multiply → дополнительные цветовые вспышки. [▶ 6:12](https://youtu.be/VHGhFAwDypM?t=372)
7. Финал: кэш на **30,000/frame** (миллионы); сильно уменьшите **Scale Multiplier** в RS-теге — чем больше аддитивных частиц, тем меньше должен быть их размер при рендере. [▶ 6:46](https://youtu.be/VHGhFAwDypM?t=406)

## Подводные камни
- Чисто чёрный узел в слое Multiply пробивает дыры (полная прозрачность); оставляйте его серым.

## Как сейчас (новые инструменты)
В nxColor версии 2026.1 появился слой **Cyclic** и falloff на каждый слой; слои nxFalloff Modifier — для дополнительного маскирования.
