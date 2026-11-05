# Убираем гексагональную сетку в закэшированной сыпучей симуляции (Create Point Cloud + jitter в Geometry Nodes)

- Источник: Top Tip Tuesday — Grid Emission Offset — https://www.youtube.com/watch?v=M2yxZlZQBec (2026-10-06)
- Хост / поколение: Blender (NeXus for Blender 2026.0) — nxEmitter Hexagonal volume shot, nxFluids SPH Granular, nxCache; Cycles (GPU)
- Задача: обрушение песчаной скульптуры на небольшом числе частиц, у которой на рендере не видно правильной гексагональной упаковки.

## Исходная сцена
Suzanne, приподнятая над полом. **nxEmitter**: Object ▸ Suzanne, Emit From **Volume**, Emission **Shot**, Mode **Hexagonal** (плотная упаковка без пересечений = стабильный старт для зёрен), **Subframe Emit выключен**, Speed 0. В режиме Hex количество задаётся радиусом: по умолчанию 0.03 m → ~14k; **0.015 m** → ~100k (только для демо — в продакшене нужны миллионы).

## Шаги
1. Большая плоскость + **nxCollider**: Bounce 0, приличный Friction. **nxGravity** по умолчанию.
2. **nxFluids** ▸ SPH ▸ Fluid Type **Granular**; Substeps: **Adaptive выключен**, **20**; Granular Friction **~70**.
3. Превью трещин: у эмиттера Display ▸ Color **Gradient**, параметр **Granular**, Auto Scale выключен, диапазон **0–20**.
4. **nxCache** ▸ Build Cache (здесь ~40 s), затем отключите солверы/модификаторы.
5. Эмиттер ▸ **Export ▸ Create Point Cloud** → автоматически создаётся сетап Geometry Nodes (точки из частиц, радиус частиц → радиус точек) + материал (Principled BSDF, цвет из **NeXus Particle Info**). Если цвет нужен был только для превью, разорвите эту связь.
6. World: **Sky Texture** в Background, strength **~0.05**; солнце поверните по вкусу.
7. В дереве GN point cloud перед выходом: **Set Position** ▸ Offset ← **Combine XYZ** из трёх **Random Value** (float, −1…1, у каждого свой Seed) → **Vector Math ▸ Scale**. Scale 0 = сетка видна; очень маленькое значение (**~0.01**) ломает сетку, сохраняя форму. Сгруппируйте эти ноды (Make Group), чтобы остался один слайдер. Mute (M) — для сравнения.
8. Более грубые зёрна: **Instance on Points** с низкополигональной **Ico Sphere**, Instance Scale ← тот же радиус частиц, что и для точек, Rotation ← **Random Rotation**. По желанию варьируйте масштаб или инстансируйте несколько вручную смоделированных гранёных зёрен.

## Подводные камни
- Частицы во viewport только для отображения; рендерится лишь экспортированный point cloud.
- Jitter работает поверх кэша, поэтому скраб и рендер остаются почти в реальном времени.

## Как сейчас (новые инструменты)
**nxMPM** из беты 2026.1 (Sand или **nxMaterial** ▸ пресет Sand wet) — более новый GPU-путь к песку; трюк с jitter/инстансами на стороне рендера по-прежнему подходит для любого экспорта point cloud.
