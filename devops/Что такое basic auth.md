### Шанс вопроса: 6%

Basic Auth — это метод аутентификации, который использует HTTP для передачи учетных данных пользователя в заголовке запроса. Учетные данные кодируются с помощью Base64 и отправляются вместе с запросом, что делает этот метод уязвимым для атак, так как учетные данные передаются в открытом виде.

Пример использования Basic Auth в HTTP-запросе:
```http
GET /protected_resource HTTP/1.1
Host: example.com
Authorization: Basic dXNlcjpwYXNzd29yZA==
```
В этом примере `dXNlcjpwYXNzd29yZA==` является кодированными учетными данными "user:password".