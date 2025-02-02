### Шанс вопроса: 3%

**Что такое RESTful**

REST (Representational State Transfer) — это архитектурный стиль, который используется для создания веб-сервисов. Он основан на шести принципах:

1. **Клиент-Сервер**: Клиентский компонент запрашивает данные у сервера, не хра няя состояние между запросами.
2. **Статус без состояния (Stateless)**: Каждый запрос должен содержать всю необходимую информацию для выполнения задачи. Сервер не хранит информацию о предыдущих запросах клиента.
3. **Кэшируемость**: Результаты ответа могут быть кэшированы, что позволяет улучшить производительность и снизить нагрузку на сервер.
4. **Единообразие интерфейса**: Использование стандартных методов HTTP (GET, POST, PUT, DELETE) для доступа к ресурсам.
5. **Слои (Layered system)**: Архитектура может быть организована в несколько слоев, каждый из которых выполняет определенные функции.
6. **Код по требованию (Code-On-Demand)** (необязательный): Клиент может динамически загружать код для выполнения задач, если это необходимо.

**Примеры кода**: В Python можно использовать библиотеку `requests` для выполнения HTTP-запросов к RESTful веб-сервисам. Например:
```python
import requests

response = requests.get('https://api.example.com/items')
if response.status_code == 200:
    data = response.json()
    print(data)
```
В этом примере мы выполняем GET-запрос к API и получаем данные в формате JSON.

**Пример использования RESTful API**: Предположим, у нас есть сервис для управления задачами (ToDo list), который предоставляет RESTful API:
- **Создание задачи**: `POST /tasks`
- **Получение всех задач**: `GET /tasks`
- **Получение конкретной задачи**: `GET /tasks/{id}`
- **Обновление задачи**: `PUT /tasks/{id}`
- **Удаление задачи**: `DELETE /tasks/{id}`

Таким образом, RESTful архитектура позволяет создавать масштабируемые и гибкие веб-сервисы.