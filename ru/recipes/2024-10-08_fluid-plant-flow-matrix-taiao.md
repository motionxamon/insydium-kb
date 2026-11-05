# Растения, плывущие на вязкой жидкости (editable-частицы → MoGraph Matrix → Cloner с растениями Taiao)

- Источник: Top Tip Tuesday — Fluid Plant Flow — https://www.youtube.com/watch?v=j8YPLZGWPBw (2024-10-08)
- Хост / поколение: C4D; закэшированная вязкая жидкость NeXus + MoGraph + **Taiao**
- Задача: текущий поток листвы/цветов, следующий за густой непрерывной жидкостью.

## Шаги
1. Жидкость должна быть густой и непрерывной (без разрывов от брызг). [▶ 0:18](https://youtu.be/j8YPLZGWPBw?t=18)
2. **Matrix** ▸ режим Object = эмиттер, distribution **Vertex**, Align Clone выкл. Эмиттер ▸ **Editing ▸ Editable** вкл. → матрица обновляется каждый кадр. [▶ 1:04](https://youtu.be/j8YPLZGWPBw?t=64)
3. Прореживание точек: **Random effector** с выключенной position и включённой **Visibility**; настройте Min/Max (переименуйте в "random vis"). [▶ 2:36](https://youtu.be/j8YPLZGWPBw?t=156)
4. Растения: **Taiao preset browser** (пак пресетов из аккаунта клиента; например, кислица), Global ▸ **Organ mode Polygons**; меньше цветов (4) / листьев (~42), радиус поменьше. [▶ 6:50](https://youtu.be/j8YPLZGWPBw?t=410)
5. **Cloner** в режиме Object = Matrix, **Multi-Instance**, align выкл.; растения — дочерние объекты (добавьте ещё пресет с ярко-оранжевым цветком). [▶ 6:50](https://youtu.be/j8YPLZGWPBw?t=410)
6. **Plain effector**: position 0, rotation P 90 (вертикально), uniform scale −0.5. Второй Random effector: большой heading, маленькие pitch/bank, scale −0.2. [▶ 6:08](https://youtu.be/j8YPLZGWPBw?t=368)
