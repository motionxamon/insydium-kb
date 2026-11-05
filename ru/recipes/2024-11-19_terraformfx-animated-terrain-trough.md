# Живая, текучая ложбина рельефа (TerraformFX: анимированный scale tfNoise + tfGradient + ячеистые борозды + tfBlur)

- Источник: Top Tip Tuesday — Terrain Flow — https://www.youtube.com/watch?v=c_lxDUv1lis (2024-11-19)
- Хост / поколение: C4D; **TerraformFX** (tfTerrain, tfNoise, tfGradient, tfBlur) + Redshift
- Задача: шот из рекламы Black Friday 2024 — волнистый каньон, который постоянно меняет форму.

## Шаги
1. **tfTerrain** (для скорости начните с 1000×1000 сегментов).
2. **tfNoise ▸ Advanced**: база **Perlin**, scale 130, gain ~100 cm; fractal **Billow**, больше octaves, persistence ~85, lacunarity пониже; **Fractal warping ~90**. [▶ 0:39](https://youtu.be/c_lxDUv1lis?t=39)
3. Анимируйте base scale **130 → 220** на весь шот, ключи в **Linear** (Show Track ▸ linear) → постоянное текучее движение. [▶ 1:47](https://youtu.be/c_lxDUv1lis?t=107)
4. Ложбина: **tfGradient ▸ Linear**, gain 220, поверните на 90° по Y лицом к камере, width 2000; отредактируйте **profile spline** в форму U (добавьте низкую точку посередине). [▶ 3:42](https://youtu.be/c_lxDUv1lis?t=222)
5. Борозды: второй tfNoise **Cellular**, jitter 100 %, fractal warping вкл., **отрицательный gain −20** (врезается внутрь). [▶ 4:36](https://youtu.be/c_lxDUv1lis?t=276)
6. Поднимите сегменты рельефа до **3000×3000**; **tfBlur ▸ Gaussian**, чтобы сгладить грани. [▶ 5:24](https://youtu.be/c_lxDUv1lis?t=324)
7. Redshift: нода **Curvature** красит борозды в два тона; Sun + Sky + DOF. [▶ 6:13](https://youtu.be/c_lxDUv1lis?t=373)
