### Шанс вопроса: 20%

Entrypoint и cmd - это параметры, которые определяют команду или скрипт, который будет выполняться при запуске контейнера Docker. 

Entrypoint используется для задания основного команды или скрипта, который будет запущен при создании контейнера. Он позволяет переопределить команду по умолчанию при каждом запуске контейнера. Entrypoint может быть как одиночным значением, так и массивом значений (например, ["/bin/bash", "-c"]).

Cmd используется для задания аргументов по умолчанию для entrypoint. Он позволяет передать параметры в основную команду или скрипт при запуске контейнера. Если cmd не определен, то значение из entrypoint будет использоваться как есть.

Пример использования:
```dockerfile
FROM ubuntu:latest

ENTRYPOINT ["/bin/bash", "-c"]
CMD ["-l"]
```
В этом примере, когда контейнер запускается с командой `docker run -it <image_name>`, будет выполнена команда `/bin/bash -c -l`.