### Шанс вопроса: 6%

Конечно! Zabbix — это распределенная система мониторинга с открытым исходным кодом, которая предназначена для контроля различных сетевых устройств и сервисов. Linux — одна из наиболее популярных операционных систем для развертывания Zabbix. Постановка Zabbix на Linux осуществляется через установку пакета, который обычно доступен в репозиториях дистрибутива.

### Шаги по установке Zabbix на Linux:

1. **Обновите список пакетов**:
   ```sh
   sudo apt update
   или
   sudo yum update
   ```

2. **Установите Zabbix репозиторий**:
   Для Debian/Ubuntu:
   ```sh
   wget https://repo.zabbix.com/zabbix/5.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_5.4-1+ubuntu20.04_all.deb
   sudo dpkg -i zabbix-release_5.4-1+ubuntu20.04_all.deb
   sudo apt update
   ```

   Для CentOS/RHEL:
   ```sh
   wget https://repo.zabbix.com/zabbix/5.4/rhel/7/x86_64/zabbix-release-5.4-1.el7.noarch.rpm
   sudo rpm -Uvh zabbix-release-5.4-1.el7.noarch.rpm
   sudo yum update
   ```

3. **Установите Zabbix Agent**:
   Для Debian/Ubuntu:
   ```sh
   sudo apt install zabbix-agent2
   ```

   Для CentOS/RHEL:
   ```sh
   sudo yum install zabbix-agent2
   ```

4. **Настройте Zabbix Agent**:
   Откройте конфигурационный файл `/etc/zabbix/zabbix_agent2.conf` и измените следующие параметры:
   - `Server`: IP-адрес или имя вашего сервера Zabbix.
   - `ServerActive`: Тоже самое, что и `Server`.
   - Пример конфигурации:
     ```sh
     Server=192.168.1.100
     ServerActive=192.168.1.100
     ```

5. **Запустите и включите Zabbix Agent**:
   Для Debian/Ubuntu:
   ```sh
   sudo systemctl start zabbix-agent2
   sudo systemctl enable zabbix-agent2
   ```

   Для CentOS/RHEL:
   ```sh
   sudo systemctl start zabbix-agent2
   sudo systemctl enable zabbix-agent2
   ```

6. **Проверьте статус Zabbix Agent**:
   ```sh
   sudo systemctl status zabbix-agent2
   ```

### Заключение:
Установка Zabbix на Linux включает обновление списка пакетов, установку пакета Zabbix Agent, настройку конфигурационного файла и запуск службы. Этот процесс можно автоматизировать с помощью скриптов, что делает его удобным для масштабирования в больших инфраструктурах.