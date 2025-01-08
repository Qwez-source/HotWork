### Шанс вопроса: 6%

Для обеспечения отказоустойчивости PostgreSQL я бы рекомендовал использовать кластерное решение, такое как PostgreSQL High Availability (HA) с помощью технологий, таких как Streaming Replication или Logical Replication. Эти методы позволяют создать несколько узлов в разных зонах доступности и обеспечивают автоматическое переключение на резервный узел при сбое основного узла.

Пример конфигурации для Streaming Replication:
1. Создайте основной сервер PostgreSQL:
```sql
initdb -D /path/to/primary
pg_ctl start -D /path/to/primary
createuser replicator
createdb repldb
psql -d repldb -c "CREATE ROLE replicator WITH LOGIN REPLICATION PASSWORD 'password';"
```
2. Настройте файл postgresql.conf на основном сервере:
```conf
wal_level = 'hot_standby'
max_connections = 100
synchronous_commit = on
```
3. Настройте pg_hba.conf для разрешения репликации:
```conf
host replication replicator repldb password
```
4. Создайте резервного сервера PostgreSQL и настройте его для присоединения к основному через rsync или другие методы:
```sh
initdb -D /path/to/standby
pg_basebackup -U replicator -D /path/to/standby -F t -X stream -P
pg_ctl start -D /path/to/standby
```
5. Настройте файл postgresql.conf на резервном сервере:
```conf
primary_conninfo = 'host=primary port=5432 user=replicator password=password'
hot_standby = on
```
6. Используйте pg_rewind для быстрого восстановления в случае сбоя:
```sh
pg_rewind --source-server='host=primary port=5432 user=replicator password=password' /path/to/standby
```
Таким образом, вы получаете отказоустойчивую конфигурацию PostgreSQL с автоматическим переключением на резервный узел в случае сбоя основного узла.