# Самоподдерживающийся цикл частиц: рост / расталкивание / уменьшение (nxAttract + nxPush + поле в nxQuestion + nxRotate через mapping)

- Источник: Top Tip Tuesday — Dynamic Push Particles — https://www.youtube.com/watch?v=v63KTwt6pI4 (2025-06-24)
- Хост / поколение: NeXus (nxAttract, nxPush, nxQuestion, nxRotate, nxSpeed, fields, mapping)
- Задача: абстрактный моушн — частицы стягиваются, раздуваются, выталкивают друг друга, уменьшаются и возвращаются.

## Шаги
1. Ring emitter больше кадра, Shot 30/F в течение 50 F, speed 0; Display Spheres, Gradient Random Ч/Б.
2. **nxAttract**: Force 300, Acceleration 3000, **Speed Limit 250**.
3. **nxPush**: режим Distance **Particle Radius**, strength 100%, итераций ~20.
4. **nxQuestion** со **Spherical field**: `Field > 0.7 → Add to Radius` (большое значение, **низкий weight** = медленный рост); `Field < 0.3 → Set Radius 1` (низкий weight).
5. nxAttract ▸ Fields: та же сфера + модификатор **Invert** → притяжение только вне ядра.
6. **nxRotate**: speed 360 × большой множитель; Mapping ▸ **Radius** 1 → 2 cm управляет Rotation Speed (маленькие = неподвижны).
7. **nxSpeed** последним: Incremental 0, **Max speed 150**.
