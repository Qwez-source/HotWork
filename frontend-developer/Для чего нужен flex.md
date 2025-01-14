### Шанс вопроса: 3%

Flexbox — это CSS-сетка, которая позволяет создавать гибкие и динамически расширяемые макеты. Он предназначен для создания однострочных или многострочных макетов с легкостью управления элементами внутри контейнера, включая выравнивание, размеры и порядок расположения.

### Основные свойства flexbox:
1. **`display: flex;`** - Преобразует контейнер в flex-контейнер.
2. **`flex-direction`** - Определяет направление основного (главной оси) и поперечного (побочной оси) флекс-контейнера. Возможные значения: `row`, `row-reverse`, `column`, `column-reverse`.
3. **`justify-content`** - Выравнивает элементы по главной оси.
4. **`align-items`** - Выравнивает элементы по поперечной оси.
5. **`flex-wrap`** - Определяет, будут ли элементы переноситься на новую строку или оставаться в одной строке. Возможные значения: `nowrap`, `wrap`, `wrap-reverse`.
6. **`align-content`** - Выравнивает строки по поперечной оси, если элементы перенесены на новую строку.
7. **`flex-grow`**, **`flex-shrink`**, **`flex-basis`** - Определяют, как элемент будет расти или уменьшаться в размере по сравнению с другими элементами внутри контейнера.
8. **`order`** - Управляет порядком отображения элементов в флекс-контейнере.

### Пример использования:
```css
/* Основной контейнер */
.container {
  display: flex;
  flex-direction: row; /* или column, row-reverse, column-reverse */
  justify-content: space-around; /* Выравнивание по главной оси */
  align-items: center; /* Выравнивание по поперечной оси */
  flex-wrap: wrap; /* Разрешает перенос элементов на новую строку */
}

/* Элемент контейнера */
.item {
  flex-grow: 1; /* Элемент будет расти относительно других */
  flex-shrink: 0; /* Элемент не будет уменьшаться */
  flex-basis: 200px; /* Базовый размер элемента */
  order: 0; /* Порядок отображения */
}
```

### Преимущества использования flexbox:
1. **Простота и краткость кода** - Flexbox позволяет управлять макетом с помощью небольшого набора свойств, что упрощает разработку и читаемость кода.
2. **Гибкость** - Макеты могут адаптироваться под различные разрешения экранов благодаря возможности переноса строк и динамическому изменению размеров элементов.
3. **Взаимодействие с другими технологиями** - Flexbox хорошо интегрируется с CSS-анимациями и может быть использован совместно с другими свойствами CSS для более сложных эффектов.

Использование flexbox значительно упрощает управление макетом в современном веб-дизайне, делая его одним из основных инструментов фронтенд-разработки.