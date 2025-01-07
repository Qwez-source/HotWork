### Шанс вопроса: 3%

Когда клиент инициирует соединение с сервером по протоколу WebSocket, он отправляет специальный HTTP-запрос с определенными заголовками. Этот запрос имеет метод `GET` и URI, который обычно начинается с `/ws`. Например:

```
GET /ws HTTP/1.1
Host: example.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: s3ch3r4zërs3cr37k3y==
Sec-WebSocket-Version: 13
```

После этого сервер отвечает с кодом состояния `101 Switching Protocols`, устанавливая заголовки `Upgrade` и `Connection` в значение `websocket`. В ответе может также присутствовать поле `Sec-WebSocket-Accept`, которое является хеш-кодом, сгенерированным на основе ключа из запроса. Например:

```
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: k94sm8dljsdfklsdjflksjf==
```

После этого соединение между клиентом и сервером переключается в режим WebSocket, и данные могут передаваться по бинарным или текстовым каналам.