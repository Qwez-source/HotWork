### Шанс вопроса: 13%

REST API (Representational State Transfer Application Programming Interface) — это стандартный способ взаимодействия между различными компонентами программного обеспечения. Он позволяет создавать распределенные приложения, которые могут взаимодействовать друг с другом через интернет. Основные принципы REST включают использование ресурсов, методы HTTP (GET, POST, PUT, DELETE и т.д.), а также формат данных в виде JSON или XML.

Вот пример запроса к API с использованием метода GET:
```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data));
```
Этот код отправляет запрос к API по URL `https://api.example.com/data` и получает данные в формате JSON, которые затем выводятся в консоль.