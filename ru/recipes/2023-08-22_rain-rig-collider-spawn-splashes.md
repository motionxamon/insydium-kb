# Риг дождя с брызгами (xpCollider Spawn при столкновении, xpJoin для нескольких коллайдеров)

- Источник: Top Tip Tuesday — xpRainRig — https://www.youtube.com/watch?v=x1SAOjOSOzs (2023-08-22)
- Хост / поколение: C4D; G1 CPU X-Particles (xpEmitter, xpGravity, xpCollider tag, xpJoin)
- Задача: дождь из линий падает на пол, модели Кайдзю и утки, а при ударе рождаются короткоживущие частицы-брызги.

## Шаги
1. **xpEmitter** прямоугольник, Emitter Plane **−Y**, сильно увеличен и поднят высоко. Emission Rate, Birth Rate **250**, вариация **100**, Speed **0**. [▶ 0:55](https://youtu.be/x1SAOjOSOzs?t=55)
2. **xpGravity** (Motion modifiers), вариация **150**; выключите Visible in Editor, чтобы спрятать иконку. [▶ 1:20](https://youtu.be/x1SAOjOSOzs?t=80)
3. Emitter Display: Editor display **Lines**, Color mode **Gradient Random** с двумя серыми (тёмный → светлый, не белый). [▶ 1:34](https://youtu.be/x1SAOjOSOzs?t=94)
4. Пол: **xpCollider** tag. Добавьте вариацию отскока, немного трения с вариацией и немного **Scatter** для случайных углов отскока. [▶ 2:30](https://youtu.be/x1SAOjOSOzs?t=150)
5. Collider ▸ вкладка **Spawn**: включите; Ctrl-перетаскиванием сделайте копию эмиттера дождя, переименуйте в "spawn" и закиньте в поле. Рождение в **точке столкновения**, направление по **нормали полигона** плюс немного **Spread**; включите **kill the original** для исходной частицы. [▶ 3:17](https://youtu.be/x1SAOjOSOzs?t=197)
6. Spawn-эмиттер ▸ Emission: Speed **300**, вариация **200** (иначе брызги просто лежат на полу); снимите галку full lifespan → Life **20** кадров, вариация **10**. В градиенте отображения — серые посветлее. [▶ 4:00](https://youtu.be/x1SAOjOSOzs?t=240)
7. Больше брызг: поднимите количество spawn в коллайдере (например, **30**).
8. Несколько поверхностей: Utilities ▸ **xpJoin**, пипеткой выберите Кайдзю, утку и плоскость, затем перенесите единственный xpCollider tag на xpJoin — один тег управляет всем. [▶ 5:19](https://youtu.be/x1SAOjOSOzs?t=319)

## Как сейчас (новые инструменты)
NeXus 2026.1: слой **nxSpawn** в режиме **On Collision** (Burst, наследует направление) вместе с объектом **nxCollider**; в Fused 2025.x — nxQuestion с вопросом о столкновении и действием Spawn. Если дождь падает в жидкость, добавьте **nxSplash** (Fused 2025.4) для брызг-корон.
