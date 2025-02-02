### Шанс вопроса: 3%

Flexbox — это CSS-модуль, который предоставляет удобный способ для создания гибкой (отзывчивой) сетки для расположения элементов на веб-странице. Он позволяет управлять размещением, выравниванием и распределением пространства между элементами в контейнере даже при изменяющихся размерах экрана или устройствах.

Основные свойства flexbox включают:
1. **display**: задает контейнеру режим отображения как `flex`.
2. **flex-direction**: определяет направление основного (главной)轴, которое может быть горизонтальным (`row`), вертикальным (`column`) или обратно пропорциональным (`row-reverse`, `column-reverse`).
3. **justify-content**: задает выравнивание элементов вдоль главной оси.
4. **align-items**: задает выравнивание элементов вдоль поперечной оси.
5. **flex-wrap**: определяет, будут ли элементы переноситься на новую строку, если контейнеру не хватает места.
6. **align-content**: выравнивание строк вдоль поперечной оси при наличии свободного пространства.
7. **flex-grow**: задает коэффициент роста элементов при распределении доступного пространства.
8. **flex-shrink**: задает коэффициент сжатия элементов при недостатке пространства.
9. **flex-basis**: определяет базовую ширину элемента перед расчетом flex-grow и flex-shrink.
10. **order**: задает порядок отображения элементов в контейнере.

Пример использования Flexbox:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flexbox Example</title>
    <style>
        .container {
            display: flex;
            justify-content: space-around;
            align-items: center;
            height: 300px;
            background-color: #f0f0f0;
        }
        .item {
            padding: 20px;
            background-color: #e0e0e0;
            border: 1px solid #ccc;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="item">Item 1</div>
        <div class="item">Item 2</div>
        <div class="item">Item 3</div>
    </div>
</body>
</html>
```
В этом примере создается контейнер с flex-свойством `display: flex;` и располагаются три элемента внутри него, каждый из которых занимает доступное пространство.