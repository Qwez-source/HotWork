### Шанс вопроса: 6%

Init процесс является первым процессом, запускаемым при старте операционной системы. Его основная роль — инициализация остальной части системы. В Linux это процесс с PID (Process ID) равным 1. Init использует файл конфигурации /etc/inittab или более современный файл /etc/systemd/system/, чтобы определить, как система должна быть запущена и какие сервисы необходимо активировать.

Пример использования systemd в Ubuntu:
```bash
# /etc/systemd/system/example.service
[Unit]
Description=Example Service
After=network.target

[Service]
ExecStart=/usr/bin/example-app
Restart=always
User=nobody
Group=nogroup

[Install]
WantedBy=multi-user.target
```
После создания такого файла можно управлять сервисом через `systemctl`:
```bash
sudo systemctl start example.service  # Запуск службы
sudo systemctl stop example.service   # Остановка службы
sudo systemctl status example.service # Проверка статуса службы
```
Это позволяет легко управлять сервисами, их запуском, остановкой и мониторингом в Linux-системах, использующих systemd.