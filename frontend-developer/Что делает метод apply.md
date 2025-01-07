### Шанс вопроса: 6%

Метод `apply` в JavaScript позволяет вызывать функцию с указанным контекстом (`this`) и передавать массив аргументов. Его сигнатура следующая:

```javascript
function.apply(thisArg, [argsArray])
```

- `thisArg`: Значение для `this` внутри функции.
- `argsArray`: Массив аргументов, которые будут переданы в функцию.

Пример использования:

```javascript
function greet(name) {
  console.log(`Hello, ${this.prefix} ${name}`);
}

const person = {
  prefix: 'Mr.'
};

greet.apply(person, ['Alice']); // Вывод: Hello, Mr. Alice
```

В этом примере `this` внутри функции `greet` будет ссылаться на объект `person`, благодаря чему мы получаем корректное сообщение.