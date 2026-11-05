# Детализированный взрыв по полю через upres (nxUpres position + velocity, nxExplode, переключение групп через nxQuestion)

- Источник: Top Tip Tuesday — Particle Upres Explode — https://www.youtube.com/watch?v=rMKmeJ68yiE (2025-05-27)
- Хост / поколение: C4D; NeXus внутри X-Particles (nxUpres, nxExplode, nxTurbulence, nxQuestion, nxColor) + C4D Fields
- Задача: буква X из частиц плавно разлетается там, куда доходит растущее рваное поле.

## Исходная сцена
Исходный эмиттер из текста "X", **Shot 10,000, speed 0**, группы 1+2 **First Group Only**. nxTurbulence + nxExplode с Groups Affected только **group 2**. nxQuestion: внутри поля → действие. Fields: анимированное **Spherical (Normal)** × **Random (Multiply)** для рваного края.

## Шаги
1. Действие nxQuestion **Set Color → Set Group 2** — при входе в поле частицы отдаются турбулентности/взрыву. [▶ 2:22](https://youtu.be/rMKmeJ68yiE?t=142)
2. Дублируйте эмиттер → "emitter dest": **50,000** частиц, размер отображения **50%**; во вкладке Modifiers **исключите** turbulence и explode. Исходный скройте. [▶ 3:26](https://youtu.be/rMKmeJ68yiE?t=206)
3. **nxUpres** (ниже модификаторов движения): Source = исходный эмиттер, Destination = dest; **Groups Affected group 2**, чтобы невысвобожденные частицы оставались на месте. [▶ 5:14](https://youtu.be/rMKmeJ68yiE?t=314)
4. Blend **Velocity + Position**, Strength очень низкий (**~13%**). [▶ 5:33](https://youtu.be/rMKmeJ68yiE?t=333)
5. Убрать рывки: число ближайших частиц **3 → 10** (плавнее, медленнее).
6. Градиент **nxColor** по Speed. Двигайте/анимируйте центр nxExplode вживую, чтобы перенаправить взрыв. [▶ 5:49](https://youtu.be/rMKmeJ68yiE?t=349)

## Как сейчас (новые инструменты)
2026.1 beta: **nxFalloff** (Sphere + Noise, слоями/с ремапом через nxFalloff Modifier) заменяет стек полей C4D; **nxWarp** может добавить арт-директорское течение. nxUpres остаётся инструментом переноса детализации.
