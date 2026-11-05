# Высокие кучи песка с auto-sleep, пробуждением от столкновения и хрупким блоком (nxMPM Materials + Auto Sleep + каналы отображения)

- Источник: NeXus Official Training — nxMPM Sand pile — https://www.youtube.com/watch?v=UT9_Aht5waE (2026-10-11)
- Хост / поколение: C4D (см), бета NeXus 2026.1 (G3); **nxEmitter** (не старый xpEmitter), nxMPM, nxGravity, nxCollider
- Задача: сыплющийся песок, который собирается в крутую кучу (осевшие песчинки засыпают, но продолжают сталкиваться), хрупкий блок, который её разбивает, и сфера, которая снова всё будит.

## Шаги
1. Используйте новый GPU **nxEmitter** из меню NeXus — старый xpEmitter с новыми инструментами не работает. [▶ 1:57](https://youtu.be/UT9_Aht5waE?t=117)
2. **nxMPM** (создаёт домен); поднимите его на +200 по Y, чтобы он стоял на полу. Границы не обязательны (MPM object ▸ **Use Bounds** выкл. = разреженный режим), но с доменом проще и легче. [▶ 2:39](https://youtu.be/UT9_Aht5waE?t=159)
3. nxEmitter: Sphere, радиус ~14–17, направление −Y, Rate, скорость 30 см; **Match Solver Resolution** → nxMPM. Добавьте **nxGravity**; длинный таймлайн (8000 F). [▶ 3:36](https://youtu.be/UT9_Aht5waE?t=216)
4. MPM Display ▸ Draw Grid (Back), чтобы оценить воксели; Resolution **80** (нормальная скорость во viewport); сузьте домен по ширине/глубине. [▶ 5:08](https://youtu.be/UT9_Aht5waE?t=308)
5. MPM ▸ вкладка **Materials**: перетащите туда эмиттер (переименован в «sand») → тип **Sand**, preset **Powder Fine**. Поставьте **Momentum** 0 (полезен для жидкостей, а на сухих материалах даёт разлетающиеся песчинки). [▶ 7:00](https://youtu.be/UT9_Aht5waE?t=420)
6. MPM object ▸ Bounds ▸ Boundary Walls ▸ **Wall Friction** на максимум → песчинки начинают собираться в кучу. [▶ 7:59](https://youtu.be/UT9_Aht5waE?t=479)
7. Тег эмиттера **Vibrate**: position 50 см по X и Z, frequency 8 — для блуждающей струи. [▶ 8:39](https://youtu.be/UT9_Aht5waE?t=519)
8. Emitter Display: size 2. **Каналы отображения**: канал 1 = gradient, параметр Random, preset Heat 3 (цвет для рендера); добавьте канал 2 для данных симуляции. [▶ 9:22](https://youtu.be/UT9_Aht5waE?t=562)
9. MPM object: **Auto Sleep** вкл., **Sleep Speed** 10 cm/s (по умолчанию 5); частицы плавно засыпают примерно за 7.5 кадра. Спящие частицы продолжают работать как коллайдеры для активных → кучи получаются намного выше. [▶ 11:37](https://youtu.be/UT9_Aht5waE?t=697)
10. MPM Display ▸ Particle Color = **Sleep State** → вывод в канал 2; смотрите канал 2 в эмиттере: зелёный — активные, красный — спящие. [▶ 12:21](https://youtu.be/UT9_Aht5waE?t=741)
11. **Wake Speed** 10.5 (чуть выше Sleep Speed), Wake Spread 0. Сфера + **nxCollider** (bounce/friction 0) расталкивает и будит песчинки; они снова оседают и засыпают. [▶ 14:21](https://youtu.be/UT9_Aht5waE?t=861)
12. Второй **nxEmitter** «brittle»: Box 50×50×50, −Y, скорость 30, Shot примерно на F220, Match Solver Resolution → тот же MPM. Остановите эмиттер песка (Emit All Frames выкл., ~200 кадров). [▶ 15:15](https://youtu.be/UT9_Aht5waE?t=915)
13. Вкладка Materials: перетащите «brittle» → **Brittle ▸ Concrete** (смотрится как старый гранулярный SPH). Display gradient по Granular, 0–10. [▶ 16:52](https://youtu.be/UT9_Aht5waE?t=1012)
14. Оба материала сталкиваются друг с другом и с коллайдером, засыпают и просыпаются в одном расчёте. [▶ 18:22](https://youtu.be/UT9_Aht5waE?t=1102)

## Подводные камни
- Названия preset’ов не стоит понимать буквально: «Concrete» — просто удачный вид раскалывающегося гранулярного материала.
- Wake Speed должен быть выше Sleep Speed, иначе частицы будут мерцать между состояниями.

## Как сейчас (новые инструменты)
Это уже самый новый способ. Legacy: xpFluidFX / гранулярный nxFluids SPH — состояния сна нет, поэтому кучи оплывают.
