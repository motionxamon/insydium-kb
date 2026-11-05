# Скрытый логотип, видимый только в преломлениях жидкости (Redshift primary ray выкл. + material blender с лавой)

- Источник: Top Tip Tuesday — Fluid Render Reveal — https://www.youtube.com/watch?v=UGiIPXJbpMo (2025-06-17)
- Хост / поколение: закэшированная жидкость через xpOpenVDBMesher + Redshift
- Задача: логотип X невидим для камеры, но появляется в отражениях/преломлениях плещущейся воды.

## Шаги
1. Вода: Standard, reflection 1, roughness ≈0, **IOR 1.33**, transmission 1. Свет — студийный HDRI-риг.
2. Камень: **Maxon Noise** Luka, октавы повыше, scale ~850, color 2 серый → base color, шероховатый; bump: FBM noise scale ~200 → нода **Bump Map** (height 2).
3. Лава: копия материала с **Emission 10**.
4. **Material Blender**: base = камень, layer 1 = лава, Blend Color = ещё один Maxon Noise с **low clip** для контраста и насыщенным color 2; скорость анимации noise 0.1.
5. Логотип ▸ Redshift Object tag ▸ Visibility override ▸ **Primary Ray Visible выкл.** (secondary остаётся) → виден только сквозь воду.

## Как сейчас (новые инструменты)
Мешить через **nxMesher** (Fused 2025.4) вместо xpOpenVDBMesher.
