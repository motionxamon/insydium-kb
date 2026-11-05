# Три тягучие жидкости с тремя вязкостями (группы + nxConstraints Viscosity с mapping по Group)

- Источник: Top Tip Tuesday — Gloopy Fluids Mix — https://www.youtube.com/watch?v=14SqrdO1c6o (2025-08-05)
- Хост / поколение: NeXus (nxFluids SPH, nxConstraints Viscosity, Mapping) + CPU xpAttractor с field falloff
- Задача: розовая брызгучая, зелёная средняя и оранжевая очень тягучая жидкость, льющиеся на бюст.

## Исходная сцена
Три сферических эмиттера (radius 7.5, равномерная эмиссия F3–280, скорость 0, радиус частиц 0.7) едут по анимированному круговому сплайну (тег Align to Spline). nxGravity с вариацией; коллайдеры на бюсте + полу.
- Ctrl+D Project Settings ▸ **X-Particles ▸ Subframe steps 2** — для сильной гравитации без ступенчатости.

## Шаги
1. **nxFluids** (по умолчанию SPH) = брызгучая.
2. **nxConstraints ▸ слой Viscosity**: Connection Limit 8, Radius 20 cm, **Stiffness 40%**, **Iterations 2** (больше итераций = не только точнее, но и сильнее).
3. Прилипание к поверхности: **xpAttractor** на бюсте, режим Velocity, Force ~50, Acceleration 0, Speed Limit огромный; **Linear field +Y**, чтобы притяжение ослабевало ниже и частицы свободно падали.
4. Группы: Emitter 1/2/3 → **Add Group** на каждый (группы 1, 2, 3).
5. nxConstraints ▸ Mapping ▸ **Group map**: Category Viscosity, Parameter Stiffness, диапазон **1 → 3**. Кривая: группа 1 → ~0.06 (чуть-чуть связности), группа 2 → 0.5, группа 3 → 1.
6. Кэш (≈8 мин / 300 F в демо).

## Как сейчас (новые инструменты)
В FLIP/APIC (Fused 2025.4) есть mapping вязкости по частицам, а 2026.1 beta добавляет неньютоновские настройки — см. "Chocolate Setting", "Hot/Cold Variable Viscosity".
