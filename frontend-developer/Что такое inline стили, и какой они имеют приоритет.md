### Шанс вопроса: 10%

Inline стили - это метод добавления CSS правил непосредственно в элемент HTML с помощью атрибута `style`. Они имеют наивысший приоритет по сравнению с остальными методами стилизации, такими как внешние (external) и внутренние (internal) стили. Это происходит потому, что встроенные стили являются частью самого элемента и не могут быть переопределены другими стилями.

Пример использования inline стилей:
```html
<p style="color: red; font-size: 16px;">Этот текст будет красным и размером 16px.</p>
```

В этом примере цвет текста и размер шрифта установлены с помощью inline стилей, что означает, что внешние и внутренние стили не могут изменить их.