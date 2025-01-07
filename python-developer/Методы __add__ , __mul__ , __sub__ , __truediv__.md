### Шанс вопроса: 3%

Методы `__add__`, `__mul__`, `__sub__` и `__truediv__` являются специальными методами в Python, которые позволяют перегрузить базовые арифметические операции для пользовательских классов. Давайте рассмотрим каждый из этих методов с примерами их использования.

1. **Метод `__add__`**: Перегружает операцию сложения.
   ```python
   class Vector:
       def __init__(self, x, y):
           self.x = x
           self.y = y

       def __add__(self, other):
           return Vector(self.x + other.x, self.y + other.y)

   v1 = Vector(2, 3)
   v2 = Vector(4, 5)
   v3 = v1 + v2  # Вызов v1.__add__(v2)
   print(v3.x, v3.y)  # Вывод: 6 8
   ```

2. **Метод `__mul__`**: Перегружает операцию умножения.
   ```python
   class Vector:
       def __init__(self, x, y):
           self.x = x
           self.y = y

       def __mul__(self, scalar):
           return Vector(self.x * scalar, self.y * scalar)

   v1 = Vector(2, 3)
   v2 = v1 * 5  # Вызов v1.__mul__(5)
   print(v2.x, v2.y)  # Вывод: 10 15
   ```

3. **Метод `__sub__`**: Перегружает операцию вычитания.
   ```python
   class Vector:
       def __init__(self, x, y):
           self.x = x
           self.y = y

       def __sub__(self, other):
           return Vector(self.x - other.x, self.y - other.y)

   v1 = Vector(4, 5)
   v2 = Vector(2, 3)
   v3 = v1 - v2  # Вызов v1.__sub__(v2)
   print(v3.x, v3.y)  # Вывод: 2 2
   ```

4. **Метод `__truediv__`**: Перегружает операцию деления (деление на число).
   ```python
   class Vector:
       def __init__(self, x, y):
           self.x = x
           self.y = y

       def __truediv__(self, scalar):
           return Vector(self.x / scalar, self.y / scalar)

   v1 = Vector(10, 20)
   v2 = v1 / 2  # Вызов v1.__truediv__(2)
   print(v2.x, v2.y)  # Вывод: 5.0 10.0
   ```

Эти методы позволяют сделать ваши классы более гибкими и удобными для работы с арифметическими операциями, что может быть полезно при моделировании математических объектов или других пользовательских структур данных.