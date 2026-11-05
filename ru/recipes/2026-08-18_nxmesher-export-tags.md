# Export-теги nxMesher: ID эмиттеров, цвет частиц, motion blur по velocity (Redshift)

- Источник: Top Tip Tuesday — nxMesher Export Tags — https://www.youtube.com/watch?v=Aqa8DG6jrA8 (2026-08-18)
- Хост / поколение: C4D, Fused 2025.4+ (GPU nxMesher) + Redshift (для Octane/Cycles 4D принцип тот же)
- Задача: один mesh жидкости из двух эмиттеров, рендер с двумя материалами, цветами частиц и векторным motion blur.

## Настройки мешинга, которые сработали
- Layers: оба эмиттера. **Surface Size: Source** (mesh = размер частиц) → нужен маленький **Polygon Size** (~1.5–2 cm).
- **Surface Type: Zhu-Bridson** (естественная гладкая жидкость) вместо Spheres; Source scale **200%** для запаса, чтобы мешились мелкие сгустки.
- Добавьте слой **Smoothing** → переключите Gaussian на **Laplacian** (сохраняет объём — хорошо для флюидов), поднимите Strength, **3 iterations** → тонкие тягучие нити без потери разрешения.

## Вкладка Export Tags
1. Кнопки **Emitter ID** → vertex map на каждый emitter (при двух эмиттерах хватит одной карты: чёрный = A, белый = B).
2. **Transfer Color** → тег vertex color с цветами частиц.
3. **Transfer Velocity** → карты vel X/Y/Z + одна карта **color velocity**; задайте **Max Velocity** равной реальной максимальной скорости (по умолчанию 200 cm/s).

## Материал Redshift
- Два материала Standard (синий subsurface; оранжевый металл) → **Material Blender**: base = subsurface, layer = металл, **Blend Color = Vertex Attribute (карта Emitter ID)**.
- Цвет частиц: нода **Vertex Attribute** с тегом цвета → цвет subsurface / base color металла; добавьте **Color Correct** (Level) для подстройки.
- Motion blur: **Redshift Object tag** на мешере → Motion Blur → Motion Vector: перетащите единственную карту **color velocity** в X (Y/Z оставьте пустыми; или используйте три отдельные карты). Scale ~5–20, если Max Velocity ниже реальной скорости. Render Settings ▸ Advanced ▸ включите **Motion Blur + Deformation Blur**. В живом IPR не видно — делайте полноценный render.

## Подводные камни
- Для финального рендера закэшируйте мешер (первый кадр долго «готовится»).
- В 2026.1 beta в nxMesher добавлены UV advection, сглаживание Detail Aware и nxGroups в качестве источника.
