### Шанс вопроса: 3%

CGI (Common Gateway Interface) — это протокол связи между веб-сервером и динамическим веб-приложением на стороне сервера. Он позволяет серверу передавать данные в виде переменных командной строки или через тело HTTP-запроса, а приложение отвечает данными в стандартном выходе.

**Плюсы:**
1. **Взаимодействие с внешними системами:** CGI позволяет взаимодействовать с базами данных, внешними API или другими сторонними приложениями через командную строку.
2. **Гибкость:** Приложение может быть написано на любом языке программирования и выполняться в среде CGI, что делает его универсальным решением для различных задач.
3. **Модульность:** CGI-скрипт может быть написан так, чтобы он мог обслуживать только определенные типы запросов или обрабатывать данные специфическим образом.

**Минусы:**
1. **Производительность:** Каждый раз при получении запроса сервер запускает новый процесс CGI, что может быть неэффективно для ресурсоемких задач или больших нагрузок.
2. **Безопасность:** Использование сторонних скриптов через CGI может представлять угрозу безопасности, так как они могут быть легко подменены или взломаны.
3. **Техническая сложность:** Настройка и управление CGI-скриптами может потребовать определенных навыков в области системного администрирования.

**Пример использования Python с CGI:**
```python
#!/usr/bin/env python
print("Content-Type: text/html")    # HTML is following
print()                             # blank line, end of headers
print("<html>")
print("<head><title>CGI Script</title></head>")
print("<body>")
print("<h1>Hello, World!</h1>")
print("</body>")
```
Этот простой скрипт на Python, размещенный в корне виртуального хоста веб-сервера (например, Apache), будет выполняться как CGI-скрипт и возвращать HTML-страницу с приветствием.