### Шанс вопроса: 6%

В Python переменные являются ссылками на объекты. Когда вы присваиваете значение переменной, вы создаёте ссылку на этот объект. Давайте рассмотрим основные аспекты работы с переменными в Python:

1. **Имена переменных**: Имена переменных должны следовать правилам именования идентификаторов, которые включают буквы (как латинского, так и национального алфавита), цифры и символ подчеркивания. Однако имя не может начинаться с цифры или содержать пробелов.

2. **Типы данных**: Переменные в Python могут хранить различные типы данных, такие как целые числа (int), вещественные числа (float), строки (str), списки (list), словари (dict) и т.д.

3. **Пример кода**:
   ```python
   # Пример переменной целого типа
   a = 10
   print(a)  # Вывод: 10

   # Пример переменной строкового типа
   b = "Hello, World!"
   print(b)  # Вывод: Hello, World!

   # Пример списка
   c = [1, 2, 3, 4, 5]
   print(c)  # Вывод: [1, 2, 3, 4, 5]

   # Пример словаря
   d = {"name": "Alice", "age": 25}
   print(d)  # Вывод: {'name': 'Alice', 'age': 25}
   ```

4. **Область видимости переменных**: Переменные могут иметь разную область видимости, в зависимости от контекста их использования:
   - **Глобальные переменные**: Определяются вне функций или блоков кода и доступны во всем коде.
     ```python
     x = 10  # Глобальная переменная

     def func():
         print(x)

     func()  # Вывод: 10
     ```
   - **Локальные переменные**: Определяются внутри функций или блоков кода и доступны только в этом контексте.
     ```python
     def func():
         y = 20  # Локальная переменная
         print(y)

     func()  # Вывод: 20
     ```

5. **Изменение и мутабельность**: Некоторые типы данных являются изменяемыми (мутабельными), а некоторые — неизменяемыми (имутабельными). Например:
   - **Неизменяемые объекты**: Строки, целые числа, вещественные числа и т.д. При изменении такого объекта создаётся новый объект, а старая ссылка пере指向 нового объекта.
     ```python
     a = 10
     a = 20  # Создаём новый объект и меняем ссылку на него
     ```
   - **Изменяемые объекты**: Списки, словари, множества и т.д. Изменения в таких объектах изменяют сам объект.
     ```python
     lst = [1, 2, 3]
     lst.append(4)  # Изменяем список на месте
     ```

Эти основные аспекты помогают понять, как работают переменные в Python и различия между ними.