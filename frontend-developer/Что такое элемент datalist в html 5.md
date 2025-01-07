### Шанс вопроса: 3%

Элемент `<datalist>` HTML5 позволяет создать предварительно определенный список вариантов для элементов управления формы, таких как `<input>`. Он используется для предоставления подсказки или автодополнения для пользователя при вводе данных.

Пример использования:
```html
<label for="city">Choose a city:</label>
<input list="cities" id="city" name="city" />
<datalist id="cities">
  <option value="New York">
  <option value="Los Angeles">
  <option value="Chicago">
  <option value="Houston">
  <option value="Phoenix">
</datalist>
```
В этом примере создается поле ввода города с предварительно определенными вариантами, которые можно выбрать пользователем.