### Шанс вопроса: 6%

В Python иерархия исключений организована следующим образом: базовым классом для всех исключений является `BaseException`, от которого наследуются более конкретные типы исключений. Основные типы исключений включают в себя:

1. **Базовый класс для всех исключений**: `BaseException`
2. **Класс для стандартных исключений**: `Exception` (является подклассом `BaseException`)
3. **Исключения, связанные с системными вызовами**: `SystemExit`, `KeyboardInterrupt`, `GeneratorExit`
4. **Исключения, связанные с ошибками ввода-вывода**: `IOError` (в Python 3 заменено на `OSError`)
5. **Исключения, связанные с типами данных**: `TypeError`, `ValueError`, `NameError`, `AttributeError` и т.д.
6. **Исключения, связанные с ошибками синтаксиса или модулей**: `ImportError`, `SyntaxError`, `RuntimeError`
7. **Исключения, специфичные для определенных библиотек**: Например, в `math` можно встретить `MathError`

Пример иерархии:
```
BaseException
 +-- Exception
      +-- ArithmeticError
      |    +-- ZeroDivisionError
      +-- AssertionError
      +-- AttributeError
      +-- EOFError
      ... (множество других классов)
```

В Python исключения можно передавать в конструкторах, создавая свою иерархию исключений. Например:

```python
class CustomException(Exception):
    def __init__(self, message="Custom exception occurred"):
        super().__init__(message)

try:
    raise CustomException("An error happened")
except CustomException as ce:
    print(ce)
```

Таким образом, можно создавать пользовательские исключения, которые будут наследоваться от `Exception` или другого базового класса в зависимости от требований приложения.