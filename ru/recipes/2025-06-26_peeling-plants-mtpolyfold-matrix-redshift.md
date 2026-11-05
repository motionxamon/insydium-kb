# Растения, растущие на отслаивающейся поверхности (разворот по выделению в mtPolyFold + MoGraph Matrix + RS Object tag, растения Taiao)

- Источник: Bite-Sized — Peeling Plants — https://www.youtube.com/watch?v=TGK5vMt8nj0 (2025-06-26)
- Хост / поколение: C4D; MeshTools **mtPolyFold**, растения Taiao (заранее анимированные), MoGraph Matrix, Redshift
- Задача: капсула отслаивается/разворачивается снизу вверх, покрытая маленькими анимированными растениями Taiao.

## Шаги
1. Сделайте несколько небольших абстрактных анимированных растений **Taiao** (сброс на кадр 0).
2. Капсула → оставьте скрытую копию; другую сделайте editable, выделите полигоны основания ▸ **Store Selection**.
3. MeshTools ▸ **mtPolyFold**, капсула дочерним объектом. Distribution **Random → Selection** (использует сохранённое выделение), чтобы складывание начиналось с основания. Для неровных mesh переключите направление с Clockwise на **Axis** (+Y).
4. Добавьте немного вариативности; поставьте keyframe на разворот с кадра 0 по 150, чтобы он отслоился до самого верха.
5. Положите PolyFold под **Subdivision Surface** (более гладкая поверхность для клонов) и скройте его.
6. MoGraph ▸ **Matrix**, Mode **Object** = Subdivision Surface; количество ~2,000 (20,000 — слишком много).
7. Matrix ▸ **RS Object tag** ▸ Mode **Custom Objects**, выберите растения. Matrix Transform ▸ **Pitch −90°**, чтобы стебли смотрели наружу.
8. **Random effector** на Matrix: небольшая позиция (2/2/2), вращение по heading, **Uniform Scale**; итоговый размер усмирите через **scale multiplier** в RS-теге.
9. Свет — RS Dome, тёплый фон.

## Подводные камни
- Matrix рендерится только после того, как в RS Object tag назначены объекты; после изменений жмите refresh на Random effector.
