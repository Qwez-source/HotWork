### Шанс вопроса: 6%

Я знаю следующие методы HTTP-запросов:

1. **GET**: Используется для получения данных с сервера. Пример:
   ```javascript
   fetch('https://api.example.com/data')
     .then(response => response.json())
     .then(data => console.log(data));
   ```

2. **POST**: Используется для отправки данных на сервер для создания или обновления ресурса. Пример:
   ```javascript
   fetch('https://api.example.com/data', {
     method: 'POST',
     headers: {
       'Content-Type': 'application/json'
     },
     body: JSON.stringify({ key: 'value' })
   })
   .then(response => response.json())
   .then(data => console.log(data));
   ```

3. **PUT**: Используется для обновления существующего ресурса на сервере. Пример:
   ```javascript
   fetch('https://api.example.com/data/1', {
     method: 'PUT',
     headers: {
       'Content-Type': 'application/json'
     },
     body: JSON.stringify({ id: 1, key: 'updatedValue' })
   })
   .then(response => response.json())
   .then(data => console.log(data));
   ```

4. **DELETE**: Используется для удаления ресурса на сервере. Пример:
   ```javascript
   fetch('https://api.example.com/data/1', {
     method: 'DELETE'
   })
   .then(response => response.json())
   .then(() => console.log('Resource deleted'));
   ```

5. **PATCH**: Используется для внесения частичных изменений в ресурс. Пример:
   ```javascript
   fetch('https://api.example.com/data/1', {
     method: 'PATCH',
     headers: {
       'Content-Type': 'application/json'
     },
     body: JSON.stringify({ key: 'updatedValue' })
   })
   .then(response => response.json())
   .then(data => console.log(data));
   ```

Эти методы являются основными для взаимодействия с серверами через HTTP-запросы в современном веб-разработке.