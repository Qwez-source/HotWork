### Шанс вопроса: 6%

Для того чтобы сервисы автоматически запускались при загрузке системы в RedHat Linux, можно использовать systemd. Systemd — это система управления службами и управление конфигурациями на основе интерфейса D-Bus.

1. **Создание юнита сервиса**: Создайте файл юнита для вашего сервиса в директории `/etc/systemd/system/`. Например, создадим файл для простого HTTP-сервера Apache:

   ```bash
   sudo nano /etc/systemd/system/httpd.service
   ```

2. **Заполнение юнита**: В этот файл добавьте следующие строки, чтобы определить сервис:

   ```ini
   [Unit]
   Description=Apache HTTP Server
   After=network.target

   [Service]
   ExecStart=/usr/sbin/httpd $HTTPD_OPTS -DFOREGROUND
   ExecStop=/bin/kill -s QUIT $MAINPID
   PrivateTmp=true

   [Install]
   WantedBy=multi-user.target
   ```

3. **Перезагрузка systemd**: После создания или изменения юнита, перезапустите systemd для обнаружения новых сервисов:

   ```bash
   sudo systemctl daemon-reload
   ```

4. **Включение и запуск сервиса**: Включите сервис в автозагрузку и запустите его:

   ```bash
   sudo systemctl enable httpd
   sudo systemctl start httpd
   ```

Теперь служба Apache будет автоматически запускаться при каждой загрузке системы.

**Пример для другого сервиса**: Для сервиса SSH (OpenSSH), создадим аналогичный юнит:

1. Создание файла юнита:

   ```bash
   sudo nano /etc/systemd/system/ssh.service
   ```

2. Заполнение файла:

   ```ini
   [Unit]
   Description=OpenSSH server daemon
   After=network.target

   [Service]
   ExecStart=/usr/sbin/sshd -D
   ExecStop=/bin/kill -s QUIT $MAINPID
   PrivateTmp=true

   [Install]
   WantedBy=multi-user.target
   ```

3. Перезагрузка systemd:

   ```bash
   sudo systemctl daemon-reload
   ```

4. Включение и запуск сервиса:

   ```bash
   sudo systemctl enable ssh
   sudo systemctl start ssh
   ```

Теперь служба SSH будет автоматически запускаться при каждой загрузке системы.