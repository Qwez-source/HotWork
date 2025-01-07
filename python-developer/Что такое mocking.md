### Шанс вопроса: 3%

Mocking — это техника программирования, которая позволяет создавать假的 объекты или методы для тестирования. Она широко используется в юнит-тестировании для изоляции компонентов системы и обеспечения предсказуемого окружения при тестировании.

Основная цель mocking — заменить настоящие объекты или методы на假的, чтобы контролировать входные данные и ожидаемые результаты. Это позволяет тестировать только определенную функциональность без взаимодействия с другими частями системы или внешними ресурсами.

Пример использования mocking в Python можно увидеть на примере теста для функции, которая зависит от другого модуля:

```python
import unittest
from unittest.mock import Mock, patch
import my_module

class TestMyModule(unittest.TestCase):
    @patch('my_module.external_function')
    def test_my_function(self, mock_external_function):
        # Настройка mock-объекта
        mock_external_function.return_value = "Mocked Result"
        
        # Вызов функции, которая использует external_function
        result = my_module.my_function()
        
        # Проверка результата и вызовов мок-объекта
        self.assertEqual(result, "Mocked Result")
        mock_external_function.assert_called_once()
```

В этом примере `my_module.external_function` заменяется на mock-объект с помощью декоратора `@patch`. Это позволяет контролировать, что возвращает `external_function`, и проверять правильность вызовов этого метода.

Таким образом, mocking помогает в тестировании, обеспечивая изоляцию компонентов системы и контролируемое окружение для проведения тестов.