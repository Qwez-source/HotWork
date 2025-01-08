### Шанс вопроса: 6%

В Python для получения тела запроса можно использовать библиотеку `requests`. Ниже приведен пример кода, который демонстрирует, как это сделать:

```python
import requests

# Пример GET-запроса
response = requests.get('http://example.com')
body_data = response.text
print(body_data)

# Пример POST-запроса
data = {'key': 'value'}
response = requests.post('http://example.com', json=data)
body_data = response.json()  # Если сервер возвращает JSON, можно использовать .json() метод
print(body_data)
```

В этом примере показано, как выполнить GET и POST запросы и получить тело ответа в виде строки или словаря.