### Шанс вопроса: 3%

Запрос HTTP — это сообщение, отправленное клиентом (браузер, мобильное приложение или другой агент пользователя) серверу для взаимодействия с ним. Обычно он включает в себя метод запроса, URI (Uniform Resource Identifier), версию протокола HTTP и заголовки запроса. Вот пример простого GET-запроса:

```http
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
```

В этом примере:
- `GET` — метод запроса, указывающий на получение данных с сервера.
- `/index.html` — URI (Uniform Resource Identifier), который определяет ресурс, к которому нужно получить доступ.
- `HTTP/1.1` — версия протокола HTTP, используемая для этого запроса.
- Заголовки `Host`, `User-Agent` и `Accept` предоставляют информацию о клиенте и типе данных, которые клиент может принять от сервера.

Для POST-запроса пример будет выглядеть так:

```http
POST /login HTTP/1.1
Host: www.example.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 27

username=admin&password=secret
```

В этом примере:
- `POST` — метод запроса, указывающий на отправку данных на сервер.
- `/login` — URI, который определяет ресурс для отправки данных.
- `Content-Type: application/x-www-form-urlencoded` — заголовок, указывающий на формат данных в теле запроса.
- Тело запроса содержит параметры `username` и `password`, которые отправляются на сервер для аутентификации пользователя.