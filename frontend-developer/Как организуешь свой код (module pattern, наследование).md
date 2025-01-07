### Шанс вопроса: 3%

Для организации кода в фронтенд-разработке я предпочитаю использовать модульный паттерн. Это позволяет создать замыкания и ограничить доступ к переменным, что делает код более чистым и безопасным. Например:

```javascript
const Module = (function() {
  let privateVariable = 'I am private';
  
  function privateMethod() {
    console.log(privateVariable);
  }
  
  return {
    publicMethod: function() {
      privateMethod();
    },
    anotherPublicMethod: function() {
      // Some other functionality
    }
  };
})();

Module.publicMethod(); // Вызов метода, доступного из внешнего кода
```

При использовании модульного паттерна можно легко управлять зависимостями и изолировать переменные, что облегчает тестирование и поддержку кода.

Наследование в JavaScript реализуется через прототипное наследование. Например:

```javascript
function Animal(name) {
  this.name = name;
}

Animal.prototype.sayName = function() {
  console.log('My name is ' + this.name);
};

function Dog(name, breed) {
  Animal.call(this, name); // Вызов родительского конструктора
  this.breed = breed;
}

Dog.prototype = Object.create(Animal.prototype); // Установка прототипа
Dog.prototype.constructor = Dog; // Восстановление конструктора

Dog.prototype.bark = function() {
  console.log('Woof!');
};

const myDog = new Dog('Buddy', 'Golden Retriever');
myDog.sayName(); // My name is Buddy
myDog.bark();    // Woof!
```

В этом примере `Dog` наследует свойства и методы от `Animal`, что позволяет добавлять специфические для собак методы, такие как `bark`.