# Листья, сорванные ветром с дерева Taiao (листья-эмиттер Taiao + nxWind Von Karman + nxQuestion Field/Random + xpSpin с маппингом на Speed)

- Источник: Top Tip Tuesday — Taiao Particle Leaves — https://www.youtube.com/watch?v=zG0XcLByiG4 (2025-03-04)
- Хост / поколение: C4D; растение Taiao + xpEmitter с NeXus G2 nxWind / nxQuestion и CPU **xpSpin**; сферическое поле C4D
- Задача: листья качаются вместе с анимацией ветра дерева, потом случайным образом срываются и кувыркаясь улетают.

## Шаги
1. Taiao Plant Layers ▸ тип слоя Leaf **Basic geometry → Emitter**, привяжите xpEmitter → одна частица на лист, которая по-прежнему следует ветру. Display **Plane**. [▶ 0:35](https://youtu.be/zG0XcLByiG4?t=35)
2. Для рендера инстансите геометрию листа тегом вашего рендера или через **xpGenerator**. [▶ 0:54](https://youtu.be/zG0XcLByiG4?t=54)
3. Эмиттер ▸ Extended Data: **Use Rotation** вкл., режим None (просто включает вращение). [▶ 1:10](https://youtu.be/zG0XcLByiG4?t=70)
4. **xpSpin** ▸ Random Spin **10/10/10**; Mapping: Random Spin на **Speed 0–50 cm** → неподвижные листья не крутятся, быстрые крутятся в полную силу. [▶ 1:45](https://youtu.be/zG0XcLByiG4?t=105)
5. Groups: две группы, **First Group Only**. [▶ 2:27](https://youtu.be/zG0XcLByiG4?t=147)
6. **nxWind**; Taiao Plant ▸ Forces ▸ **Direction from Object** = этот ветер, чтобы у дерева и частиц было одно направление. [▶ 3:03](https://youtu.be/zG0XcLByiG4?t=183)
7. nxWind: режим **Von Karman**, сильный, turbulence ~50, friction velocity **2.3**; Groups Affected = **group 2**. [▶ 3:20](https://youtu.be/zG0XcLByiG4?t=200)
8. **nxQuestion** ▸ вкладка Field: сферическое поле. Вопрос: Particle **Field > 0** → **Set Group 2**. [▶ 3:53](https://youtu.be/zG0XcLByiG4?t=233)
9. Дочерний вопрос **And**: **Math Random −100…100**, per frame, **> 85**; перенесите действие под него → каждый кадр срывается только часть листьев внутри поля. [▶ 4:44](https://youtu.be/zG0XcLByiG4?t=284)

## Подводные камни
Без случайного подвопроса все листья внутри поля падают разом.

## Как сейчас (новые инструменты)
Замените CPU xpSpin на **nxSpin** (со слоями в Fused 2025.4), чтобы весь эмиттер остался на NeXus; в 2026.1 beta полем срыва может быть nxFalloff.
