# Удаляем лишнюю пену за пределами контейнера произвольной формы (nxKill + инверсия Volume поля / nxQuestion Document Object Distance)

- Источник: Top Tip Tuesday — nxKill Custom Bounds — https://www.youtube.com/watch?v=MRrkMcNyU-w (2023-10-31)
- Хост / поколение: C4D; G2 NeXus внутри X-Particles (nxFluids SPH, nxFoam, nxKill, nxQuestion) + поля C4D
- Задача: убрать частицы пены, которые рождаются чуть снаружи коллайдера-капсулы (выглядят как протечки).

## Исходная сцена
Контейнер-капсула; **nxFluids SPH** по умолчанию; **nxGravity**; **nxWind** с тегом Vibrate на вращении; сильная Voronoi **nxTurbulence**. Закэшировано (600 F примерно за 30 с).

## Шаги
1. **nxFoam** на кэш ▸ **Add Emitter** (отображение Dots). Рождение после возраста **60 → 10**, **Crest 0**, **Aerated ~20**, **Min Impact 0 / Max Impact 10** → пена от ударов.
2. Откуда «протечки»: пена рождается в радиусе вокруг краевых частиц, иногда снаружи коллайдера, и вернуться уже не может.
3. Способ A — **nxKill**: Volume **Outside Bounds**, Radius **0** (убивает всё), затем Fields ▸ перетащите коллайдер, режим слоя **Points → Volume**, Remapping ▸ **Invert** → гибнут только частицы снаружи капсулы.
4. Способ B — **nxQuestion**: тип Question **Document**, данные **Object Distance** по **объёму** коллайдера; **> 0** = снаружи → Action **Kill**.

## Как сейчас (новые инструменты)
В бете 2026.1 режим **nxFalloff Object** (один из 16) на nxKill даёт ту же произвольную форму без полей C4D; nxFoam был переписан в Fused 2025.4 (слои foam/bubbles/spray).
