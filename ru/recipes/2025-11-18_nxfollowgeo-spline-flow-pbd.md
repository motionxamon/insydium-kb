# Тягучая жидкость, кружащая вокруг нескольких сплайнов (nxFollowGeo в режиме Force + PBD)

- Источник: Top Tip Tuesday — Spline Flow — https://www.youtube.com/watch?v=5Ra6keP2ZgE (2025-11-18)
- Хост / поколение: C4D, Fused 2025.4 (тогда beta: новый сплайновый режим nxFollowGeo, ease-in в PBD, слоёный nxTurbulence)
- Задача: лента из жидких частиц обтекает вращающиеся сплайны-окружности и рвётся на нити.

## Шаги
1. Эмиттер: Rectangle высота 0 / ширина 30 (тонкая лента), Rate 20 000/s в течение 90 кадров, speed 150 ±, radius 1. [▶ 0:42](https://youtu.be/5Ra6keP2ZgE?t=42)
2. **nxFollowGeo** → сплайн = окружность. Режим **Force** (не Guide), чтобы жидкость и турбулентность продолжали действовать. Поднимаем Follow Strength; **Attract Strength ~400**, чтобы держать частицы на пути. [▶ 1:43](https://youtu.be/5Ra6keP2ZgE?t=103)
3. Release: по умолчанию **Spline End** отпускает частицы в конечной точке сплайна → ставим **Time (Particle Age) = 0** → не отпускать никогда (бесконечный цикл). [▶ 2:22](https://youtu.be/5Ra6keP2ZgE?t=142)
4. Extended Data: удаляем стандартный слой **Offset** (20 cm), чтобы частицы прижимались к сплайну (или добавляем слои Offset/Twist для спиралей). [▶ 2:47](https://youtu.be/5Ra6keP2ZgE?t=167)
5. **nxFluids PBD** (тягучие нити) → **Ease In 15 frames** (не даёт выбросу плотности накрыть новорождённые частицы). **External Pressure** повыше; по желанию немного вязкости; для большего количества нитей поднимаем Attraction и Repulsion вместе (в той же пропорции). [▶ 3:42](https://youtu.be/5Ra6keP2ZgE?t=222)
6. **nxTurbulence** слоями: Voronoi strength 18–26, scale 222, 8 octaves, низкая persistence, пониже frequency; follow strength немного уменьшаем. [▶ 4:24](https://youtu.be/5Ra6keP2ZgE?t=264)
7. Несколько сплайнов: **Hierarchy** включено = дочерние сплайны используют те же настройки; выключено = добавляем каждый сплайн отдельно (например, на одном разворачиваем направление). Снова Release **Spline End** → частицы перескакивают на ближайший сплайн и продолжают циркулировать. [▶ 7:10](https://youtu.be/5Ra6keP2ZgE?t=430)
