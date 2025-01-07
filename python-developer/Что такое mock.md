### Шанс вопроса: 3%

Mock-объекты — это объекты, которые заменяют реальные объекты или библиотеки во время тестирования. Они позволяют изолировать код от внешних зависимостей и контролируют поведение тестируемых функций. В Python популярным инструментом для создания mock-объектов является библиотека `unittest.mock`.

Пример использования `unittest.mock`:

```python
from unittest.mock import MagicMock, patch
import some_module  # Предположим, что это модуль с зависимостями

# Создаем mock-объект для заменяющего модуля или функции
some_module.dependency = MagicMock()

# Настраиваем поведение mock-объекта
some_module.dependency.return_value = "Mocked result"

# Вызываем функцию, которая зависит от dependency
result = some_module.function_that_depends_on_dependency()

print(result)  # Вывод: "Mocked result"
```

В этом примере `some_module` содержит функцию, которая зависит от `dependency`. Мы заменяем реальный объект на mock-объект с помощью `MagicMock`, а затем настраиваем его поведение. Таким образом, мы можем протестировать функцию в изолированной среде без реальных зависимостей.