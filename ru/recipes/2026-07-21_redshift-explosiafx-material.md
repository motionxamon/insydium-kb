# Материал Redshift для nxExplosiaFX, совпадающий с viewport

- Источник: Top Tip Tuesday — Redshift ExplosiaFX — https://www.youtube.com/watch?v=udP2NcPK3xw (2026-07-21)
- Хост / поколение: C4D, Fused 2025.4+ (nxExplosiaFX) + Redshift
- Задача: правильные диапазоны плотности дыма и температуры огня в Redshift, плюс управление через рампы для дымчатых клубов и хвостов пламени.

## Сначала измерить (EFX Display ▸ Flame)
- **Flame Emit Above T** = 1000 по умолчанию → огонь начинается с 1000.
- Поднимайте, пока пламя не исчезнет → это максимальная температура (здесь ≈3000 → берём 3500).
- В EFX Simulation ▸ **Ambient Conditions** температура окружения **300** — если её не отсечь, весь домен будет светиться красным.

## Дерево нод (материал Redshift на объекте EFX)
```
Volume Scalar Attribute (preset EFX ▸ smoke) — Old Max ≈ 7 (EFX smoke isn't 0–1 like Pyro)
   → RS Ramp (cubic bias; black knot ~0.1 removes wisps) → Standard Volume ▸ Scatter/Density
Volume Scalar Attribute (preset EFX ▸ temperature) — Old Min 1000, Old Max 3500, New 0–1
   → RS Ramp (shape flame tails) → Change Range (0–1 → 0–3500) → Standard Volume ▸ Emission ▸ Temperature
Standard Volume → Output Volume
```

## Шаги
1. Используйте **Standard Volume** (не ноды Volume или Pyro Volume) — максимум контроля. [▶ 2:38](https://youtu.be/udP2NcPK3xw?t=158)
2. Не используйте встроенные пресетные каналы volume — читайте каналы нодами **Volume Scalar Attribute**. [▶ 3:35](https://youtu.be/udP2NcPK3xw?t=215)
3. Дым: пресет **EFX ▸ smoke** → Density. Поставьте **Old Max ~5–10** (начните с 7), чтобы плотность совпала с viewport. Добавьте **Ramp**: белый узел влево — плотнее, чёрный узел чуть вправо (0.1) — убрать дымку. [▶ 6:37](https://youtu.be/udP2NcPK3xw?t=397)
4. Огонь: режим Emission — Temperature (blackbody). Второй Scalar Attribute, пресет **EFX ▸ temperature**, Old Min **1000** (не 0 и не 300), Old Max 3500 → Temperature. Emission **Scale** 10–20 для светящегося дыма (больше шума → больше сэмплов). [▶ 10:02](https://youtu.be/udP2NcPK3xw?t=602)
5. Рампа на температуре: сначала переведите в 0–1, рампа, затем **Change Range** обратно в 0–3500 — если подать рампу прямо в Temperature, огонь пропадёт. [▶ 13:23](https://youtu.be/udP2NcPK3xw?t=803)

## Главная мысль
Всегда находите и вводите реальные **диапазоны smoke** и **temperature** своей симуляции; дефолты рассчитаны на 0–1 как в Pyro.
