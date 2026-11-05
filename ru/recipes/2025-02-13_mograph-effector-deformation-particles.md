# Деформация мешей и статичных облаков частиц эффектором MoGraph Random (режим Deformer + список Modifiers у xpEmitter)

- Источник: Bite-Sized — Effector Deformation — https://www.youtube.com/watch?v=P9mLMWa6XKQ (2025-02-13)
- Хост / поколение: C4D, эффекторы MoGraph + Fields; CPU **xpEmitter** (G1)
- Задача: турбулентная анимированная деформация меша собачки из шариков, а затем тот же эффектор двигает статичное облако частиц, не разрывая его.

## Шаги — меш
1. MoGraph ▸ Effectors ▸ **Random effector**; вкладка Deformer ▸ Deformation **Point** (есть также режимы Polygon и Object). [▶ 0:39](https://youtu.be/P9mLMWa6XKQ?t=39)
2. Вкладка Parameter: Position **15 cm** по X/Y/Z; сделайте эффектор **дочерним к геометрии**, чтобы он работал как деформер. [▶ 1:01](https://youtu.be/P9mLMWa6XKQ?t=61)
3. Положите меш (с эффектором внутри) под **Subdivision Surface**, чтобы сгладить результат. [▶ 1:15](https://youtu.be/P9mLMWa6XKQ?t=75)
4. Анимация: вкладка Effector ▸ Random Mode **Turbulence** (больше всего деталей), Animation Speed **20%**; поднимите Position до **30 cm** по каждой оси. [▶ 1:40](https://youtu.be/P9mLMWa6XKQ?t=100)

## Шаги — частицы
5. Вытащите эффектор из меша. **xpEmitter** ▸ Emitter Source **Object**, перетащите Subdivision Surface, эмиссия с **Polygon Area**. [▶ 2:32](https://youtu.be/P9mLMWa6XKQ?t=152)
6. Emission **Shot**, **100,000** частиц, настроено так, чтобы они уже были на кадре 0; Speed 0; Display **Dots**; спрячьте исходный меш. [▶ 2:50](https://youtu.be/P9mLMWa6XKQ?t=170)
7. Эмиттер ▸ вкладка **Modifiers**: перетащите туда Random effector → статичные частицы смещаются той же анимированной турбулентностью. [▶ 3:08](https://youtu.be/P9mLMWa6XKQ?t=188)
8. Локализуйте эффект: добавьте **Linear Field** (Z) в фоллоф эффектора и анимируйте его через собачку → волна турбулентности проходит по облаку. [▶ 3:34](https://youtu.be/P9mLMWa6XKQ?t=214)

## Подводные камни
- Частицы остаются статичными и лишь смещаются, поэтому облако никогда не разваливается — никаких сил и скорости.

## Как сейчас (новые инструменты)
Бета NeXus 2026.1: **nxWarp** (Noise и другие cage-варпы, режим **Deform**) деформирует частицы и меши напрямую, а вместо C4D Fields — режимы nxFalloff. В C4D 2025.3+ связка с Pyro/нативными частицами позволяет модификаторам NeXus управлять нативными частицами.
