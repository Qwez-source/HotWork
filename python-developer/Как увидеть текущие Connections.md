### Шанс вопроса: 6%

В Python, для просмотра текущих соединений в приложении, можно использовать инструменты, такие как библиотеку `psutil` или модуль `socket`. Ниже приведен пример кода на Python с использованием `psutil`, который может помочь в отслеживании текущих соединений:

```python
import psutil

def list_connections():
    connections = []
    for proc in psutil.process_iter(['pid', 'name']):
        try:
            # Получаем список сокетов, связанных с процессом
            pconn = proc.connections(kind='inet')
            for conn in pconn:
                if conn.status == psutil.CONN_ESTAB:  # Проверяем, что соединение активно
                    connections.append({
                        'pid': proc.pid,
                        'name': proc.name(),
                        'local_address': conn.laddr,
                        'remote_address': conn.raddr
                    })
        except (psutil.AccessDenied, psutil.NoSuchProcess):
            pass
    return connections

# Вызов функции для просмотра текущих соединений
current_connections = list_connections()
for conn in current_connections:
    print(conn)
```

Этот скрипт перебирает все запущенные процессы, получает их идентификаторы (PID), имена и список сокетов, связанных с ними. Для каждого сокета проверяется статус `CONN_ESTAB`, что указывает на активное соединение. Результат выводится в консоль в виде списка словарей, где каждый словарь содержит информацию о PID процесса, его имени, а также локальном и удаленном адресе соединения.

Этот пример можно расширить для включения дополнительных сведений о сокетах, таких как порты, если это необходимо для вашего приложения.