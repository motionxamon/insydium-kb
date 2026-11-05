# Статуя рассыпается в песок по мере распространения заражения (группы nxInfectio + nxFluids SPH Granular + nxSpeed Max Speed 0)

- Источник: Top Tip Tuesday — Granular Crumble — https://www.youtube.com/watch?v=DsZ56QYQ2cY (2024-06-11)
- Хост / поколение: C4D; xpEmitter + NeXus GPU (nxInfectio, nxFluids SPH Granular, nxGravity, nxSpeed)
- Задача: статуя обрушивается комьями сверху вниз, по мере того как по ней идёт заражение.

## Исходная сцена
xpEmitter из **объёма** статуи, Shot hexagonal, скорость 0, радиус 1. Display окрашен C4D Noise shader (светлые/тёмные значения). Emitter ▸ Groups ▸ **birth group 1**.

## Шаги
1. **nxInfectio** с 3 **seed objects** наверху. Светлые частицы заражаются быстрее; чтобы ускорить, поднимите search radius и допустимое число заражений на частицу. [▶ 1:29](https://youtu.be/DsZ56QYQ2cY?t=89)
2. Режим **Use Groups**: добавьте группы **incubating** и **infected**; Group color change **None** (важна только принадлежность к группе). [▶ 2:29](https://youtu.be/DsZ56QYQ2cY?t=149)
3. **nxFluids** ниже nxInfectio, солвер **SPH** (открывает **Granular**): **Friction 100%**, **Stability 10**, **Cohesion 5**; substeps 3 для превью. [▶ 3:31](https://youtu.be/DsZ56QYQ2cY?t=211)
4. **nxGravity** ниже, с небольшой вариацией.
5. **nxSpeed** в самом низу: режим **Acceleration**, acceleration 0, **Max Speed 0**, **Groups Affected = группа 1** → незаражённые частицы держат форму и падают, только когда заразятся. [▶ 4:47](https://youtu.be/DsZ56QYQ2cY?t=287)
6. Для комковатого песка сильно поднимите **substeps** в nxFluids и закэшируйте (в демо 2 мин 16 с на 300 F). [▶ 5:09](https://youtu.be/DsZ56QYQ2cY?t=309)

## Как сейчас (новые инструменты)
Песок/снег на **nxMPM** в NeXus 2026.1 (или пресеты **nxMaterial**) со сменой материала по возрасту/повреждению, закреплённый через **nxPin** до момента отпускания.
