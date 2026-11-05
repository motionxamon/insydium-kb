# Обзор функций: стек модификаторов Taiao, новый toLeaf и переделанный toFlower (sneak peek, сборка гибискуса)

- Источник: INSYDIUM LIVE! — March 2023 - NeXus, TerraformFX & Taiao — https://www.youtube.com/watch?v=OVUcKWkhUFY (2023-03-16)
- Хост / поколение: C4D; Taiao (процедурные растения), рабочая dev-сборка
- Статус: превью переработки Taiao, вышедшей в **Fused 2023.3** (июль 2023); жилкование toLeaf + пресеты снова упомянуты в Fused 2024.2.

## toPlant: стек модификаторов
- Настройки формы (furling, gravity, turbulence…) вынесены из слоя растения в стек **Modifiers** на каждом слое; сам слой задаёт только базовую форму (angle, length; разрешение — в Global settings).
- Модификаторы: **Furling, Turbulence, Twist, Gravity** + новые **Aim, Profile, Displacement, Fold**. У каждого есть **Variations**, **Bias** вдоль ветки и **blend mode** (второй Furling в режиме **Add** складывается с первым — например, один у основания, другой на кончиках). Количество не ограничено.
- Каждый модификатор принимает C4D **Fields** (одно поле можно бросить в список нескольких модификаторов): spherical field — режиссировать, какие ветки гнутся; анимированное Random field = анимация в духе ветра.
- Списки INSYDIUM теперь растягиваются по вертикали (вплоть до R19).

## toLeaf (новый объект)
- Режимы вкладки geometry листа: **Basic / Custom / Emitter**; в Custom кладётся toLeaf, и растение использует процедурный лист. Кривая формы; в демо разрешение 20 × 40.
- **Veins**: профиль главной жилки (taper), **Petiole Offset** (черешок отодвигает пластину от ветки), Vein Count (~20), angle, radius; структуры **Pinnate / Palmate / Parallel** (трава); жилки подстраиваются под форму. Хорошо видны при translucency.
- Модификаторы: **Fold** со сплайном **Fold Shape** (мягкий изогнутый сгиб вместо прежнего жёсткого угла) + bias; Furling (провисание под весом, загиб кончика); Turbulence.
- Основной режим **Standard** или **Lobing** (сложные листья): ряды Pinnate с конечным листочком или веер **Palmate**; длина/профиль черешка, вариации angle/twist/size, сплайн **Size Bias** (центральные vs крайние листочки).

## toFlower (переделан, раньше был внутри toPlant)
- Готовые слои: sepals (годятся как бутон), receptacle, pistil, petals, stamen. Гибискус: sepals выкл., 5 лепестков, ширина receptacle/pistil 1, высота pistil 0.5.
- Лепестки: разрешение 20 × 40, Orientation ~60%, Fold у основания (bias вниз) обнимает receptacle, Furling + Turbulence; strength у Orientation **Twist** убирает пересечения; Main ▸ Radius придвигает их обратно к пестику.
- **Stamen на stamen** (дочерние слои через Add Parts): основная тычинка (Fit to Pistil выкл., узлы профиля для утолщения, Turbulence) → 5 кончиков с распределением **Radial** (count 5, ring count 5, сплайн Distribution, Angle, Furling) → пыльца с распределением **Spiral** (спираль Фибоначчи), сплайны bias для angle и size, **Displacement** с noise-шейдером для «корявой» детализации.
- Слой Displacement + любой шейдер заменяет Turbulence, когда нужен контроль по отдельным осям.
- Совет по материалу лепестка: gradient в Color по 2D-**V** (от основания к кончику) с небольшой turbulence.

## Как сейчас (новые инструменты)
В Fused 2024.2 у Taiao появились scatter по точкам роста и жилкование toLeaf + пресеты; ничего новее по Taiao в whats-new нет.
