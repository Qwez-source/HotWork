### Шанс вопроса: 14%

`self` и `super` являются ключевыми в Python для управления объектами и наследованием.

- **`self`:** В методах класса, `self` представляет экземпляр класса. Он используется для доступа к атрибутам и методам объекта. Пример:
  ```python
  class MyClass:
      def __init__(self, value):
          self.value = value

      def display(self):
          print(self.value)

  obj = MyClass(10)
  obj.display()  # Вывод: 10
  ```

- **`super`:** `super()` используется для вызова методов родительского класса. Это позволяет избежать прямой ссылки на родительский класс и упрощает код при переопределении методов в дочерних классах. Пример:
  ```python
  class ParentClass:
      def __init__(self, value):
          self.value = value

  class ChildClass(ParentClass):
      def __init__(self, value, additional_value):
          super().__init__(value)  # Вызов конструктора родительского класса
          self.additional_value = additional_value

  child_obj = ChildClass(10, 20)
  print(child_obj.value)       # Вывод: 10
  print(child_obj.additional_value)  # Вывод: 20
  ```

Использование `self` и `super()` делает код более гибким, читаемым и поддерживаемым, особенно при работе с наследованием.