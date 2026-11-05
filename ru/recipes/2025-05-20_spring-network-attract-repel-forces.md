# Органичная пружинящая сеть частиц (birth springs в nxConstraints + слои Forces, переключение групп и пиннинг через nxQuestion)

- Источник: Top Tip Tuesday — Particle Forces — https://www.youtube.com/watch?v=PIgXQtSgnMY (2025-05-20)
- Хост / поколение: C4D; NeXus внутри X-Particles (nxConstraints, nxQuestion, nxDrag) + Fields C4D + xpTrail
- Задача: mesh из связанных частиц в форме цветка, который раздувается там, где проходит поле, с закреплёнными краями.

## Исходная сцена
Крышка Extrude из Flower spline с 3 лепестками; emitter Object/область полигонов, **Shot 10,000**. Группы **initial** + **repulsion**, режим **First Group Only**. nxQuestion: внутри движущегося поля → цвет красный + **Set Group repulsion**.

## Шаги
1. **nxConstraints «birth»**: birth springs, поиск **40 cm**, **Limit 6**, **Stiffness 90**, разрыв **None**. Emitter ▸ Display ▸ **Display Constraints**, чтобы их видеть. [▶ 1:57](https://youtu.be/PIgXQtSgnMY?t=117)
2. В том же объекте ▸ добавьте слой **Forces**: притяжение дальше ~20 cm, отталкивание ближе ~10 cm, **Limit 32** → покачивание «тяни-толкай». [▶ 2:42](https://youtu.be/PIgXQtSgnMY?t=162)
3. Порядок: вопрос со сменой группы — вверху стека. **nxQuestion «pin»** — последним (после constraints), Groups Affected **initial**: если значение Field > 0 → **Set Speed 0**. Field = Flower spline, режим Distance **Radius 20** → периметр зафиксирован. [▶ 3:47](https://youtu.be/PIgXQtSgnMY?t=227)
4. **nxConstraints «repel»** под birth: радиус слоя Forces **80/80**, отталкивание примерно на **20% сильнее**, Groups Affected **repulsion** → частицы раздуваются по мере того, как поле переводит их в группу. [▶ 5:27](https://youtu.be/PIgXQtSgnMY?t=327)
5. Опционально: **nxDrag** последним, Multiplier **~100,000**, чтобы всё успокоилось после взрыва. [▶ 6:07](https://youtu.be/PIgXQtSgnMY?t=367)
6. Рендер: **xpTrail**, Algorithm **Constraints**, тип = birth springs. [▶ 6:59](https://youtu.be/PIgXQtSgnMY?t=419)

## Как сейчас (новые инструменты)
2026.1 beta: **nxPin** закрепляет частицы по falloff/группе (чище, чем пиннинг через speed 0); **16 режимов nxFalloff**, включая Spline, заменяют Fields C4D; в NeXus 2026 используется **nxTrail**.
