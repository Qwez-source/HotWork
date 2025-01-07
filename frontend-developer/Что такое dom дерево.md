### Шанс вопроса: 13%

DOM (Document Object Model) — это представление структуры HTML-документа в виде дерева, где каждый элемент является узлом. Корень дерева — это document, а ветви и листья — это элементы и их дочерние узлы. DOM позволяет JavaScript взаимодействовать с HTML, манипулировать его содержимым, стилями, структурой и событиями.

Пример:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DOM Example</title>
</head>
<body>
    <div id="container">
        <h1>Hello, World!</h1>
        <p class="text">This is a paragraph.</p>
    </div>
</body>
</html>
```
В этом примере DOM-дерево будет выглядеть следующим образом:
```
Document
├── html
│   ├── head
│   │   ├── meta
│   │   └── title
│   └── body
│       ├── div
│       │   ├── h1
│       │   └── p
```
Каждый элемент в HTML-документе является узлом в DOM-дереве, и можно использовать JavaScript для доступа к ним, изменения содержимого, добавления новых элементов или удаления существующих.