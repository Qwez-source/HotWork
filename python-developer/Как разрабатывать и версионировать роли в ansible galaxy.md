### Шанс вопроса: 6%

Для разработки и версионирования ролей в Ansible Galaxy, следуйте этим шагам:

1. **Создание структуры роли**: 
   - Создайте новую директорию для вашей роли.
   - Внутри этой директории создайте стандартные поддиректории и файлы, такие как `tasks`, `handlers`, `files`, `templates`, `vars`, `defaults`, `meta` и т.д.

2. **Заполнение роли**: 
   - Заполните каждую поддиректорию соответствующими файлами и конфигурациями. Например, в `tasks/main.yml` можно разместить все задачи, которые будут выполняться ролью.

3. **Написание метаданных**: 
   - В файле `meta/main.yml` укажите информацию о роли, такую как имя, версию, зависимости и т.д. Пример:
     ```yaml
     galaxy_info:
       author: your_name
       description: A brief description of the role
       company: Your Company
       license: MIT
       min_ansible_version: 2.9
       platforms:
         - name: CentOS
           versions:
             - "7"
     ```

4. **Тестирование роли**: 
   - Используйте тестовые сценарии (например, в `test/integration`) для проверки работы роли в различных окружениях. Например, можно создать тестовую машину и запустить туда роль с помощью Ansible.

5. **Публикация роли**: 
   - После того как роль протестирована и проверена, вы можете опубликовать её в Ansible Galaxy. Для этого зарегистрируйтесь на официальном сайте Ansible Galaxy, создайте папку для своей роли и отправьте туда ваш репозиторий.

6. **Обновление роли**: 
   - При необходимости обновите роль, увеличив номер версии в файле `meta/main.yml`. Например:
     ```yaml
     galaxy_info:
       version: 1.0.1
     ```
   - После этого повторите процесс тестирования и публикации.

Пример структуры роли:
```
my_role/
├── defaults/
│   └── main.yml
├── files/
├── handlers/
│   └── main.yml
├── meta/
│   └── main.yml
├── tasks/
│   └── main.yml
├── templates/
├── tests/
│   ├── inventory
│   └── test.yml
└── vars/
    └── main.yml
```

Пример содержимого `meta/main.yml`:
```yaml
galaxy_info:
  author: alex
  description: Installs and configures a web server on the target hosts.
  company: Example Inc.
  license: MIT
  min_ansible_version: 2.9
  platforms:
    - name: CentOS
      versions:
        - "7"
```

Этот процесс поможет вам создать качественную и управляемую роль, которая будет легко обнаруживаться и использоваться другими DevOps специалистами.