# Вращение офсетов edge-сплайнов с задержкой (mtEdgeSpline Scale Offsets + тег Vibrate + XPresso)

- Источник: Bite-Sized — EdgeSpline Offset — https://www.youtube.com/watch?v=2i4ui9lCuYo (2025-04-03)
- Хост / поколение: C4D; MeshTools **mtEdgeSpline**, XPresso (без частиц)
- Задача: вложенные копии edge-сплайнов платоника, которые повторяют его вращение с управляемым запаздыванием.

## Шаги
1. **Platonic** дочерним к **mtEdgeSpline** (режим **Standard** = по сплайну на каждое ребро); Display ▸ gradient выкл.; скройте платоник. [▶ 0:29](https://youtu.be/2i4ui9lCuYo?t=29)
2. **Scale Offsets**: количество **5**, увеличьте **Offset Size**; у офсетов есть и значения Rotation — ими и будем управлять. [▶ 1:03](https://youtu.be/2i4ui9lCuYo?t=63)
3. Анимация: на платоник тег **Vibrate**, rotation вкл., **360°** по каждой оси, frequency **0.1**. [▶ 1:28](https://youtu.be/2i4ui9lCuYo?t=88)
4. **Null** с именем «Xpresso» как контроллер (место под user data) ▸ Programming Tags ▸ **XPresso**. [▶ 2:12](https://youtu.be/2i4ui9lCuYo?t=132)
5. В XPresso: нода платоника ▸ выходы **Coordinates ▸ Rotation H, P, B**; нода mtEdgeSpline ▸ входы через синий порт ▸ Object Properties ▸ **Rotation H, P, B** офсетов (это вектор, поэтому компоненты выбираются там). [▶ 3:15](https://youtu.be/2i4ui9lCuYo?t=195)
6. Между каждой парой — нода **Math** (копии через Ctrl-перетаскивание), функция **Multiply**, второй вход = управляющее значение. [▶ 3:45](https://youtu.be/2i4ui9lCuYo?t=225)
7. Значение **1** → каждый офсет чуть отстаёт от вращения родителя; **2** → сильно разбросанные вращения; **−1** → в обратную сторону. [▶ 4:33](https://youtu.be/2i4ui9lCuYo?t=273)

## Как сейчас (новые инструменты)
С Fused 2025.4.1 mtEdgeSpline работает с n-gon, так что входной меш не обязательно триангулировать или держать в квадах.
