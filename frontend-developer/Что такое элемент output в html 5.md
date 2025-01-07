### Шанс вопроса: 3%

Элемент `<output>` в HTML5 используется для представления результата вычислений или значения, произведенного пользователем. Он может быть ассоциирован с элементами формы и обновляться при изменении данных в поле ввода.

Пример использования:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Output Example</title>
</head>
<body>
    <form oninput="output.value = parseInt(a.value) + parseInt(b.value)">
        <input type="number" id="a" name="a" value="0"> +
        <input type="number" id="b" name="b" value="0"> =
        <output for="a b" name="output" style="background-color: lightblue;">0</output>
    </form>
</body>
</html>
```
В этом примере, когда пользователь вводит значения в поля `input` с идентификаторами `a` и `b`, значение суммы будет отображаться в элементе `<output>` с именем `output`. Это позволяет пользователю видеть результат вычислений мгновенно, не отправляя форму.