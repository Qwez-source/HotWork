### Шанс вопроса: 3%

Методы `__getitem__`, `__setitem__` и `__delitem__` являются специальными методами в Python, которые позволяют вам перегружать поведение операторов индексации. Эти методы используются для реализации поддержки доступа к элементам объекта по индексу, присваивания значений по индексу и удаления элементов по индексу.

1. **Метод `__getitem__(self, key)`**:
   - Этот метод вызывается при доступе к элементу объекта по его ключу (индексу).
   - Пример использования:
     ```python
     class MyList:
         def __init__(self, data):
             self.data = data
         
         def __getitem__(self, index):
             return self.data[index]
     
     my_list = MyList([1, 2, 3, 4, 5])
     print(my_list[2])  # Вывод: 3
     ```

2. **Метод `__setitem__(self, key, value)`**:
   - Этот метод вызывается при присваивании значения элементу по его ключу (индексу).
   - Пример использования:
     ```python
     class MyList:
         def __init__(self, data):
             self.data = data
         
         def __setitem__(self, index, value):
             self.data[index] = value
     
     my_list = MyList([1, 2, 3, 4, 5])
     my_list[2] = 10
     print(my_list.data)  # Вывод: [1, 2, 10, 4, 5]
     ```

3. **Метод `__delitem__(self, key)`**:
   - Этот метод вызывается при удалении элемента по его ключу (индексу).
   - Пример использования:
     ```python
     class MyList:
         def __init__(self, data):
             self.data = data
         
         def __delitem__(self, index):
             del self.data[index]
     
     my_list = MyList([1, 2, 3, 4, 5])
     del my_list[2]
     print(my_list.data)  # Вывод: [1, 2, 4, 5]
     ```

Эти методы позволяют создавать пользовательские объекты, которые могут быть использованы в циклах `for`, индексировании и присваивании значений.