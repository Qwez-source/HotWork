### Шанс вопроса: 3%

Для того чтобы `setTimeout` выполнился позже, необходимо указать задержку в миллисекундах (мс) после которой будет выполнена функция. Эта задержка передается первым аргументом функции `setTimeout`.

Пример:
```javascript
// Функция, которая будет выполнена через 2 секунды (2000 миллисекунд)
setTimeout(() => {
  console.log("Это сообщение появится с задержкой в 2 секунды");
}, 2000);
```

В этом примере функция `console.log` будет выполнена только через 2 секунды после её вызова, так как мы указали задержку в 2000 миллисекунд (мс).