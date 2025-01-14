### Шанс вопроса: 10%

CSS (Cascading Style Sheets) — это технология, которая позволяет создать визуально привлекательные веб-страницы. Она используется для описания внешнего вида документа, написанного с помощью языка разметки (обычно HTML). CSS осуществляет разделение содержимого и представления, что упрощает внесение изменений в дизайн сайта без необходимости менять его содержание.

Основные функции CSS включают:
1. **Стилизация элементов**: Возможность задавать шрифты, цвета, размеры, отступы и другие стилистические свойства для HTML-элементов.
2. **Расположение элементов**: Использование позиционирования (static, relative, absolute, fixed, sticky), флексбоксов (flexbox) и грид-макета (grid layout) для управления расположением элементов на странице.
3. **Анимации и трансформации**: Создание плавных переходов между состояниями элементов с помощью CSS-анимаций и трансформаций.
4. **Медиа-запросы**: Реагирование на размеры экрана устройства, что позволяет адаптировать дизайн под разные разрешения.

**Пример использования CSS:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Пример использования CSS</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }
        h1 {
            color: #333;
            text-align: center;
        }
        p {
            font-size: 16px;
            line-height: 1.5;
            color: #666;
            margin: 20px;
        }
    </style>
</head>
<body>
    <h1>Заголовок страницы</h1>
    <p>Это пример текста с использованием CSS для стилизации.</p>
</body>
</html>
```
В этом примере CSS задает шрифт, цвет и отступы для элементов `h1` и `p`.