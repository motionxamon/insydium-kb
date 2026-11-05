# Капля, тающая снаружи внутрь (удержание nxDrag + nxQuestion Neighbors → смена группы + nxConstraints Viscosity)

- Источник: Top Tip Tuesday — nxFluids Melt Rig — https://www.youtube.com/watch?v=Tz60lfoe-hw (2024-01-02)
- Хост / поколение: C4D; G2 NeXus внутри X-Particles (xpEmitter + nxFluids, nxDrag, nxQuestion, nxConstraints, nxGravity)
- Задача: шар жидкости висит на месте, а потом его поверхностные частицы автоматически тают, стекают и тягуче шлёпаются на пол.

## Исходная сцена
Плоскость пола с тегом коллайдера; **xpEmitter** выстреливает сферу с заполнением **Shot – Hexagonal**, радиус 3 cm; **nxGravity** и **nxFluids** по умолчанию.

## Шаги
1. **nxFluids**: Solver **PBD → SPH**, поднимите substeps для точности. [▶ 0:48](https://youtu.be/Tz60lfoe-hw?t=48)
2. Замораживаем каплю: **nxDrag** **под nxGravity**, пресет Density — самый густой (**Mercury**): сопротивление полностью гасит гравитацию. [▶ 1:44](https://youtu.be/Tz60lfoe-hw?t=104)
3. Эмиттер ▸ Groups: Ctrl+Alt-клик по кнопке добавления дважды → группы 1 и 2; режим **Random → First Group Only** (все рождаются в группе 1). [▶ 2:20](https://youtu.be/Tz60lfoe-hw?t=140)
4. nxDrag ▸ Groups Affected: только **группа 1**. [▶ 2:36](https://youtu.be/Tz60lfoe-hw?t=156)
5. **nxQuestion** ▸ добавьте Question: **Particle Neighbors less than 15** (каждая частица ищет соседей в радиусе ~10 cm; у поверхностных соседей меньше). Action: **Set Group → группа 2**. Внешняя оболочка выходит из-под drag и падает. [▶ 3:51](https://youtu.be/Tz60lfoe-hw?t=231)
6. **nxConstraints**, Groups Affected **группа 2**: тип **Viscosity**, больше итераций, **3 связи** на частицу, stiffness пониже → тягучие капли. [▶ 4:47](https://youtu.be/Tz60lfoe-hw?t=287)
7. Порядок: поставьте nxConstraints **под nxFluids**, чтобы жидкость считалась первой. [▶ 5:31](https://youtu.be/Tz60lfoe-hw?t=331)
8. Тает слишком быстро? Опустите порог соседей до **12**. Вопрос переоценивается постоянно, так что новые поверхностные слои продолжают таять, пока капля не исчезнет. [▶ 5:28](https://youtu.be/Tz60lfoe-hw?t=328)

## Подводные камни
- Порядок модификаторов важен: nxDrag после гравитации, constraints после жидкости.

## Как сейчас (новые инструменты)
В Fused 2025.4 считайте жидкость на **nxFluids FLIP/APIC** (переменная вязкость) и мешите GPU-**nxMesher**. В бете 2026.1 **nxMPM** с Mixer умеет менять материал по возрасту/скорости, а **nxBind** удерживает частицы в объёме и отпускает их по возрасту/жизни/скорости/температуре — альтернатива трюку с удержанием через drag.
