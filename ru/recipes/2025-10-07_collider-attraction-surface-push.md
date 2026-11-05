# Пульсирующие частицы расталкивают друг друга, прижимаясь к поверхности (притяжение коллайдера)

- Источник: Top Tip Tuesday — Collision Forces — https://www.youtube.com/watch?v=PTamR793O-k (2025-10-07)
- Хост / поколение: NeXus (nxQuestion, nxPush) + CPU xpColor (шейдер Maxon) + вкладка Forces у xpCollider
- Задача: частицы на торе растут и сжимаются пятнами, расталкивают друг друга, но никогда не покидают поверхность.

## Шаги
1. Эмиттер: Object = тор, Polygon Area, **Shot 10 000**, speed 0, **без радиуса при рождении** (чтобы не было вспышки). [▶ 0:21](https://youtu.be/PTamR793O-k?t=21)
2. **xpColor** с шейдером Maxon **Noise (Voronoi)**, огромный масштаб, с клиппингом, animation speed ~7 → движущиеся чёрно-белые пятна. [▶ 1:04](https://youtu.be/PTamR793O-k?t=64)
3. **nxQuestion**: `Color Brightness < 0.1 → Set Radius 0` (низкий weight = плавное уменьшение) / `> 0.7 → Set Radius 26` (низкий weight). [▶ 2:33](https://youtu.be/PTamR793O-k?t=153)
4. **nxPush** в режиме Particle Radius, полная сила, 10 итераций. [▶ 4:36](https://youtu.be/PTamR793O-k?t=276)
5. **Тег xpCollider** на торе: Bounce 0, немного Friction (с вариацией для разнообразия скольжения) → при расталкивании частицы отскакивают… [▶ 7:04](https://youtu.be/PTamR793O-k?t=424)
6. …поэтому используй у коллайдера **вкладку Forces → Attraction**, Radius 100 cm, strength ~59 → частицы прижимаются к поверхности и при этом расталкиваются. (Не сочетай nxFollowGeo + nxPush — силы противоречат друг другу.) [▶ 6:19](https://youtu.be/PTamR793O-k?t=379)
7. xpGenerator **Render Instances** из Platonic; Extended Data **Use Rotation → Random**. [▶ 8:50](https://youtu.be/PTamR793O-k?t=530)
