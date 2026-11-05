# Непересекающиеся ветки из частиц внутри меша (Taiao toTree volume points → spline emitter, nxQuestion Spawn, nxPush, nxScale)

- Источник: Top Tip Tuesday — Volume Particle Networks — https://www.youtube.com/watch?v=WTMgHpdgOhY (2024-09-17)
- Хост / поколение: C4D; дерево **Taiao** (вывод сплайнами) + NeXus G2 (nxPush, nxQuestion, nxScale, nxColor) на xpEmitter; поля C4D
- Задача: ветвящаяся сеть, заполняющая голову волка; частицы растут/проявляются там, где проходит поле.

## Шаги
1. Добавьте **Taiao tree**; Display ▸ включите **attraction points** (ветки конкурируют за точки внутри зелёной кроны). [▶ 0:28](https://youtu.be/WTMgHpdgOhY?t=28)
2. Volume Points: **Crown shape → Volume Objects**, перетащите меш головы; точек **100 → 1,000** (генерируется дольше). [▶ 1:05](https://youtu.be/WTMgHpdgOhY?t=65)
3. Object type **Poly → Spline**; при желании сделайте редактируемым (C) и переключите сплайн в **B-Spline**, чтобы смягчить острые углы. [▶ 1:40](https://youtu.be/WTMgHpdgOhY?t=100)
4. xpEmitter в режиме Object = этот сплайн, **emit from edges**; **Shot 15,000**, полный lifespan, speed 0, radius **1**. [▶ 2:20](https://youtu.be/WTMgHpdgOhY?t=140)
5. **nxPush**, Distance mode **Particle Radius** — затем исключите его из родительского эмиттера (вкладка Modifiers, exclude list), чтобы родители стояли на месте. [▶ 4:28](https://youtu.be/WTMgHpdgOhY?t=268)
6. **nxQuestion** + **Spherical Field**: Particle **Field > 0** → **Spawn** один раз, 1 частица, distance 0, новый spawn-эмиттер (отображение Spheres), Inherit выкл., speed 0, radius ~**1.5**. Скройте родителей. [▶ 4:14](https://youtu.be/WTMgHpdgOhY?t=254)
7. Вместо этого спавните с radius 0, затем **nxScale ▸ Value over time**, небольшой rate + variation, clamp **0 → 1.5** → частицы растут после рождения. [▶ 5:27](https://youtu.be/WTMgHpdgOhY?t=327)
8. **nxColor ▸ Gradient by Parameter**, градиент из пресета, parameter = **Field**; поле = меш головы в режиме **Surface** → внешние частицы светлые, внутренние тёмные; радиусом двигайте границу. [▶ 6:04](https://youtu.be/WTMgHpdgOhY?t=364)

## Как сейчас (новые инструменты)
**nxDendrite** (ветки/сеть/решётка) может построить сеть прямо в NeXus; **nxSpawn** (2026.1 Beta 3) — для проявления; режимы nxFalloff **Object** / **Spline** вместо полей C4D.
