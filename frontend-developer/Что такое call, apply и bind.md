### Шанс вопроса: 6%

Call, Apply и Bind являются методами в JavaScript, которые позволяют контролировать контекст вызова функции. Они полезны для управления тем, кто будет использовать `this` внутри функции.

1. **Call**: Метод `call()` вызывает функцию с указанным значением this и аргументами, переданными по отдельности.
   ```javascript
   const person = {
     name: "Alice"
   };

   function greet(age) {
     console.log(`Hello, my name is ${this.name} and I am ${age} years old.`);
   }

   greet.call(person, 25); // Вывод: Hello, my name is Alice and I am 25 years old.
   ```

2. **Apply**: Метод `apply()` похож на `call()`, но аргументы передаются как массив (или псевдомассив).
   ```javascript
   const person = {
     name: "Bob"
   };

   function greet(age, city) {
     console.log(`Hello, my name is ${this.name} and I am ${age} years old, from ${city}.`);
   }

   greet.apply(person, [28, 'New York']); // Вывод: Hello, my name is Bob and I am 28 years old, from New York.
   ```

3. **Bind**: Метод `bind()` создает новую функцию, которая при вызове устанавливает `this` в указанное значение и имеет предопределенные аргументы. Это полезно для создания функций с фиксированным контекстом или аргументами.
   ```javascript
   const person = {
     name: "Charlie"
   };

   function greet(age) {
     console.log(`Hello, my name is ${this.name} and I am ${age} years old.`);
   }

   const boundGreet = greet.bind(person, 30); // Создаем новую функцию с фиксированным this и аргументом age
   boundGreet(); // Вывод: Hello, my name is Charlie and I am 30 years old.
   ```

Использование этих методов позволяет гибко управлять контекстом выполнения функции и аргументами, что делает код более модульным и переиспользуемым.