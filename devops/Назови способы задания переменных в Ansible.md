### Шанс вопроса: 13%

В Ansible можно задавать переменные несколькими способами, включая:

1. **Переменные через аргументы командной строки**:
   Переменные можно передавать непосредственно при вызове playbook или команды `ansible` с помощью флага `--extra-vars`. Например:
   ```bash
   ansible-playbook my_playbook.yml --extra-vars "my_variable=value"
   ```

2. **Переменные через файл**:
   Переменные можно хранить в отдельном YAML-файле и загружать их при выполнении playbook с помощью флага `--vars-file`. Например:
   ```bash
   ansible-playbook my_playbook.yml --vars-file=variables.yml
   ```

3. **Переменные в playbook**:
   Переменные можно задавать прямо внутри playbook, используя ключ `vars`. Например:
   ```yaml
   ---
   - name: Example playbook
     hosts: localhost
     vars:
       my_variable: value
     tasks:
       - name: Task using the variable
         debug:
           msg: "{{ my_variable }}"
   ```

4. **Переменные через динамические inventory**:
   Используя динамические inventory, можно генерировать переменные на лету. Например, с помощью AWS API для EC2 инвентори:
   ```yaml
   plugin: aws_ec2
   aws_access_key: YOUR_ACCESS_KEY
   aws_secret_key: YOUR_SECRET_KEY
   regions:
     - us-east-1
   filters:
     instance-state-name: running
   ```

5. **Переменные через группы и хосты**:
   Переменные можно задавать для групп или отдельных хостов, используя ключ `vars` в inventory файле:
   ```ini
   [webservers]
   web1.example.com vars:
     http_port: 80
   web2.example.com vars:
     http_port: 8080
   ```

Эти методы позволяют гибко управлять переменными в Ansible playbook'ах, обеспечивая удобство и модульность настроек.