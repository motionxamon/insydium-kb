# Светящаяся от скорости лава на закэшированных инстансах частиц (Redshift User Data Vector velocity → Vector Length → Incandescent)

- Источник: Top Tip Tuesday — Redshift Particle Velocity — https://www.youtube.com/watch?v=8A0hvOpOscU (2024-08-13)
- Хост / поколение: C4D; закэшированный эмиттер X-Particles (только данные во время рендера); нодовый материал **Redshift**
- Задача: быстрые частицы раскаляются добела, медленные остаются блестящими/тёмными, хотя цвет частиц в кэше — это noise-паттерн.

## Исходная сцена
Закэшированная симуляция плавления/застывания; на эмиттере **Redshift Object tag ▸ Custom Objects**, инстансящий куб, платоновое тело и пирамиду. Один RS area light. С инстансной геометрией **материал вешается на инстансируемые объекты**, а не на эмиттер.

## Шаги
1. Стандартный RS Material (отражения по умолчанию дают блики). Откройте node editor. [▶ 1:09](https://youtu.be/8A0hvOpOscU?t=69)
2. Нода **User Data Vector**, атрибут из пресетов ▸ Particle ▸ **Velocity** (атрибут скорости XP). [▶ 2:21](https://youtu.be/8A0hvOpOscU?t=141)
3. **Vector Length** (Vector Math) → превращает вектор в скалярную скорость. [▶ 2:56](https://youtu.be/8A0hvOpOscU?t=176)
4. **Change Range**: old min 0, old max = потолок скорости в симуляции (**70** — модификатор скорости ограничил её 70 cm в этом кэше) → 0–1. [▶ 3:28](https://youtu.be/8A0hvOpOscU?t=208)
5. **Scalar Ramp** с контрастной кривой, затемнённой так, чтобы светились только самые быстрые куски. [▶ 4:38](https://youtu.be/8A0hvOpOscU?t=278)
6. Материал **Incandescent**, режим **Temperature**, понизьте температуру для диапазона белый→оранжевый; Ctrl-клик по Intensity Multiplier, чтобы вывести его вход, и подайте туда ramp. [▶ 5:26](https://youtu.be/8A0hvOpOscU?t=326)
7. **Material Blender** → Surface: base = Standard material, Layer 1 = Incandescent, blend color белый, **Additive** on. [▶ 6:14](https://youtu.be/8A0hvOpOscU?t=374)
8. Ползунок силы: **Math Multiply** между ramp и intensity; input 2 = сила (**2** — погорячее). [▶ 6:54](https://youtu.be/8A0hvOpOscU?t=414)

## Подводные камни
- Знайте свою максимальную скорость (проверьте ограничение скорости в симуляции), иначе ремап обрежет диапазон или использует его не полностью.
- При необходимости glow добавьте на композе.

## Как сейчас (новые инструменты)
Та же цепочка Redshift работает с кэшами NeXus; в Blender (NeXus 2026) путь к данным отдельных частиц — шейдерная нода **Particle Info**.
