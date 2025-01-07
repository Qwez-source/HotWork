### Шанс вопроса: 16%

Декоратор `property` в Python позволяет определять методы класса так, чтобы они могли быть вызываемыми как атрибуты. Это означает, что вместо вызова метода через скобочки (как это обычно делается), его можно использовать напрямую как атрибут объекта. Декоратор `property` позволяет создать свойство (get, set и delete) для метода класса.

Пример использования:

```python
class Person:
    def __init__(self, name):
        self._name = name

    @property
    def name(self):
        return self._name

    @name.setter
    def name(self, value):
        if isinstance(value, str) and len(value) > 0:
            self._name = value
        else:
            raise ValueError("Name must be a non-empty string")

    @name.deleter
    def name(self):
        del self._name

# Создание объекта класса Person
person = Person("Alice")

# Получение значения свойства name
print(person.name)  # Вывод: Alice

# Установка нового значения для свойства name
person.name = "Bob"
print(person.name)  # Вывод: Bob

# Удаление свойства name
del person.name
print(person.name)  # Вызовет AttributeError, так как _name было удалено
```

В этом примере `@property` создает метод `name`, который можно использовать как атрибут класса. Метод `name.setter` позволяет устанавливать значение свойства, а метод `name.deleter` позволяет удалять его. Это делает код более чистым и удобным для использования, так как клиентский код может обращаться к свойству напрямую, не беспокоясь о том, что это метод класса.