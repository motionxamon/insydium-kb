# Скрытый логотип, видимый только в преломлениях жидкости (Redshift primary ray выкл. + material blender с лавой)

- Источник: Top Tip Tuesday — Fluid Render Reveal — https://www.youtube.com/watch?v=UGiIPXJbpMo (2025-06-17)
- Хост / поколение: закэшированная жидкость через xpOpenVDBMesher + Redshift
- Задача: логотип X невидим для камеры, но появляется в отражениях/преломлениях плещущейся воды.

## Шаги
1. Вода: Standard, reflection 1, roughness ≈0, **IOR 1.33**, transmission 1. Свет — студийный HDRI-риг. [▶ 1:07](https://youtu.be/UGiIPXJbpMo?t=67)
2. Камень: **Maxon Noise** Luka, октавы повыше, scale ~850, color 2 серый → base color, шероховатый; bump: FBM noise scale ~200 → нода **Bump Map** (height 2). [▶ 3:00](https://youtu.be/UGiIPXJbpMo?t=180)
3. Лава: копия материала с **Emission 10**. [▶ 4:04](https://youtu.be/UGiIPXJbpMo?t=244)
4. **Material Blender**: base = камень, layer 1 = лава, Blend Color = ещё один Maxon Noise с **low clip** для контраста и насыщенным color 2; скорость анимации noise 0.1. [▶ 4:55](https://youtu.be/UGiIPXJbpMo?t=295)
5. Логотип ▸ Redshift Object tag ▸ Visibility override ▸ **Primary Ray Visible выкл.** (secondary остаётся) → виден только сквозь воду. [▶ 7:21](https://youtu.be/UGiIPXJbpMo?t=441)

## Как сейчас (новые инструменты)
Мешить через **nxMesher** (Fused 2025.4) вместо xpOpenVDBMesher.
