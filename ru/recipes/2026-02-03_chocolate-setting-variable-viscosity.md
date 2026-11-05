# Расплавленный шоколад, застывающий при контакте (переменная вязкость APIC по цвету)

- Источник: Top Tip Tuesday — Chocolate Set — https://www.youtube.com/watch?v=VCGNxYZt21k (2026-02-03)
- Хост / поколение: C4D, Fused 2025.4+ (nxFluids APIC, nxQuestion object distance, nxBlend, nxMesher) + Redshift
- Задача: шоколад льётся на модель мороженого, густеет там, где касается, и остаётся глянцевым там, где ещё жидкий.

## Шаги
1. Тонкий эмиттер проходит над коллайдером; в Project Settings **Subframe Steps 3**, чтобы убрать ступенчатость. [▶ 0:40](https://youtu.be/VCGNxYZt21k?t=40)
2. **nxFluids APIC**, Voxel **5**, небольшой домен, **Viscosity 50** → лента складывается. [▶ 3:28](https://youtu.be/VCGNxYZt21k?t=208)
3. Цвет = температура: **nxQuestion** `Document ▸ Object Distance (mode Polygons, object = cube) < 3 cm → Set Color white` с **уменьшенным Weight** (плавно уходит в белый = постепенно остывает). [▶ 2:58](https://youtu.be/VCGNxYZt21k?t=178)
4. **nxBlend** Color, **Blend: Addition**, сила на максимум, distance ~6 cm → белый расходится на соседей (остывание) и никогда не темнеет. [▶ 5:49](https://youtu.be/VCGNxYZt21k?t=349)
5. nxFluids **Mapping ▸ Color Brightness → Viscosity** (source FLIP/APIC). Поднимите базовую вязкость до **150** и поставьте чёрный узел на **1/3 (0.33)** → чёрный сохраняет исходные 50, белый уходит в 150 (застывает). [▶ 3:47](https://youtu.be/VCGNxYZt21k?t=227)
6. Кэш (≈1 мин). **nxMesher**: Polygon Size 1.3, радиус 1.6, Smoothing **Mean Curvature** 100%, 5 итераций (сохраняет гребни, убирает плоские участки). **Export Tags ▸ Transfer Color**. [▶ 8:33](https://youtu.be/VCGNxYZt21k?t=513)
7. Шоколад в Redshift: **Vertex Attribute (color map) → Ramp → Reflection Roughness** → жидкий = глянец, застывший = мат. [▶ 9:16](https://youtu.be/VCGNxYZt21k?t=556)

## Как сейчас (новые инструменты)
В бете 2026.1 FLIP Mixer добавляет вязкость по эмиттеру/группе, **Yield Stress / Flow Index** (неньютоновские жидкости) и Recolor by Viscosity — но трюк с mapping по-прежнему даёт больше всего контроля.
