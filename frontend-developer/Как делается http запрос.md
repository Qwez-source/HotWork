### Шанс вопроса: 13%

Для выполнения HTTP-запросов на фронтенде чаще всего используются библиотеки, такие как `fetch` (доступна в браузерах) или `axios` (популярная библиотека для работы с HTTP-запросами в JavaScript).

### Использование fetch:
```javascript
// Пример GET запроса
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error('There has been a problem with your fetch operation:', error));

// Пример POST запроса
fetch('https://api.example.com/data', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({ key: 'value' })
})
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error('There has been a problem with your fetch operation:', error));
```

### Использование axios:
```javascript
// Пример GET запроса
axios.get('https://api.example.com/data')
  .then(response => console.log(response.data))
  .catch(error => console.error('There has been a problem with your axios request:', error));

// Пример POST запроса
axios.post('https://api.example.com/data', { key: 'value' })
  .then(response => console.log(response.data))
  .catch(error => console.error('There has been a problem with your axios request:', error));
```

В обоих примерах показано, как выполнять GET и POST запросы к API. `fetch` является встроенным методом браузера для работы с сетевыми запросами, а `axios` — это сторонняя библиотека, которая упрощает процесс выполнения HTTP-запросов и обрабатывает множество деталей автоматически.