### Шанс вопроса: 13%

`let` и `const` являются двумя новыми способами объявления переменных в современном JavaScript, представленными с ECMAScript 2015 (ES6). Основное различие между ними заключается в области видимости и том, могут ли их значения изменяться после инициализации.

- **let**: Переменные, объявленные с помощью `let`, имеют блочную область видимости (block scope). Это означает, что переменная ограничена той областью кода, в которой она была объявлена. Пример:
  ```javascript
  function testLet() {
    let x = 1;
    if (true) {
      let x = 2; // Разные переменные с тем же именем, но в разных областях видимости
      console.log(x); // Выведет 2
    }
    console.log(x); // Выведет 1
  }
  ```

- **const**: Переменные, объявленные с помощью `const`, также имеют блочную область видимости, но их значения не могут быть изменены после инициализации. Если попытаться присвоить новое значение уже объявленной константе, будет выдана ошибка. Пример:
  ```javascript
  function testConst() {
    const y = 10;
    // y = 20; // Ошибка: Assignment to constant variable.
    if (true) {
      const y = 20; // Разные переменные с тем же именем, но в разных областях видимости
      console.log(y); // Выведет 20
    }
    console.log(y); // Выведет 10
  }
  ```

Таким образом, `let` используется для переменных, которые могут изменять свое значение в течение срока жизни переменной, а `const` - для констант, значения которых не должны меняться.