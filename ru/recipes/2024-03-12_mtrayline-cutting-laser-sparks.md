# Режущий лазер с искрами (эмиттер в contact points mtRayline + xpTrail + xpSpawn)

- Источник: Top Tip Tuesday — mtRayline Lasers — https://www.youtube.com/watch?v=PpDwpKu8478 (2024-03-12)
- Хост / поколение: C4D; MeshTools **mtRayline** + **CPU** X-Particles (xpEmitter, xpTrail, xpSpawn, xpGravity)
- Задача: анимированные лазерные лучи выжигают след на полу и выбрасывают раскалённые добела искры в точках попадания.

## Исходная сцена
Плоскость пола; null, анимированный по позиции Z и Heading.

## Шаги
1. **mtRayline** (по умолчанию) ▸ вкладка Object: добавьте пол в collision geometry. Лучи отражаются до **Max Length** (по умолчанию 500 cm); переключите на **Single Shot**, чтобы каждый луч заканчивался на первом попадании и оставлял contact point.
2. Поверните его вниз и сделайте дочерним к анимированному null.
3. Display: gradient display выкл., contact/start points скрыты; цвет в Basic — оранжевый.
4. **Вкладка Points ▸ Contact Points ▸ Add Emitter** → «emitter contact» получает частицу в каждой точке попадания.
5. **xpTrail** с contact-эмиттером, цвет оранжевый → выжженный след резки.
6. **xpSpawn** ▸ Add Emitter («emitter spawn»); спаун в позиции исходной частицы, Direction **Random Spherical**, скорость спауна **Absolute** (берётся из нового эмиттера). Скорость spawn-эмиттера **100** (var 80); спаун **75** в кадр (var 15) вместо 300.
7. **xpGravity** (по умолчанию) тянет искры вниз.
8. Отображение spawn-эмиттера: **Lines**, Color Mode **Gradient Parameter** по **Age**: почти белый при рождении → вскоре насыщенный оранжевый → затухание в чёрный (остывающий металл).

## Как сейчас (новые инструменты)
NeXus 2026.1: **nxSpawn** (Instant / At Age / On Collision / On Death, Rate/Burst/Pulse) для искр, nxGravity и **nxTrail** на эмиттере NeXus; nxColor Gradient by Parameter для раскраски по возрасту. См. также «mtRayline particle lasers» (2024-04-23).
