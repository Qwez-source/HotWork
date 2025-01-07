### Шанс вопроса: 20%

Декоратор Middleware в Python используется для обработки запросов или ответов между сервером и клиентом. Он позволяет выполнять дополнительные действия перед тем, как сервер отправит ответ клиенту, или после того, как он получен от клиента. Middleware может использоваться для аутентификации пользователей, логирования запросов, кэширования данных и других задач.

Пример простого middleware:
```python
def simple_middleware(get_response):
    def middleware(request):
        # Перед обработкой запроса
        print("Before request")
        
        response = get_response(request)
        
        # После обработки запроса
        print("After request")
        
        return response
    return middleware
```
Этот пример демонстрирует, как можно использовать middleware для вывода сообщений перед и после обработки запроса. Функция `simple_middleware` принимает функцию `get_response`, которая обрабатывает запрос, и возвращает обёрнутую функцию `middleware`, которая выполняет дополнительные действия.

Для использования этого middleware в Django приложении, его нужно добавить в список MIDDLEWARE в настройках проекта:
```python
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    # Другие middleware
    'your_project.middleware.simple_middleware',
]
```
Этот код добавляет ваш custom middleware в список доступных middleware для обработки запросов в Django приложении.