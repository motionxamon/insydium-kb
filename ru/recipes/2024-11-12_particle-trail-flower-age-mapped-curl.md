# Распускающийся цветок из трейлов (nxTurbulence Curl Blend/Add по возрасту + сила по скорости)

- Источник: Top Tip Tuesday — Particle Trail Flower — https://www.youtube.com/watch?v=tMeuIDssUxI (2024-11-12)
- Хост / поколение: NeXus (nxTurbulence Curl, nxPush, nxSpeed, mapping) + xpTrail + Redshift
- Задача: шот из рекламы Black Friday 2024 — три кольца частиц закручиваются в лепестки и успокаиваются.

## Шаги
1. Три **ring**-emitter (быстрый жёлтый 150, медленнее фиолетовый, самый медленный синий), вариация радиуса. [▶ 0:25](https://youtu.be/tMeuIDssUxI?t=25)
2. Порядок в стеке: **nxTurbulence → nxPush → nxSpeed**.
   - nxPush: режим **Particle Radius**, полная сила (без перекрытий).
   - nxSpeed: **Incremental −25** → постепенное замедление.
   - nxTurbulence: **Curl**, scale ~200, больше октав, persistence ~31.
3. Blend vs Add: **Blend** смешивает скорость частицы и noise (100 % = только noise); **Add** складывает их (слишком много = хаос). [▶ 2:49](https://youtu.be/tMeuIDssUxI?t=169)
4. Mapping ▸ **Age 0 → 90**: Curl **Blend** нарастает (чуть поднимите первый узел, чтобы начиналось позже); второй Age map — для **Add**, вступает немного раньше. [▶ 3:43](https://youtu.be/tMeuIDssUxI?t=223)
5. Mapping ▸ **Speed 0 → 75** → **Strength** турбулентности → неподвижные частицы не получают noise и могут остановиться. [▶ 5:41](https://youtu.be/tMeuIDssUxI?t=341)
6. Три объекта **xpTrail** (по одному на emitter, в цвет) → рендер в Redshift.
