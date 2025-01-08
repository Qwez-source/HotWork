### Шанс вопроса: 20%

Факты в Ansible — это данные, которые собираются о конкретной машине или группе машин. Они хранятся в памяти Ansible под названием "fact" и могут быть использованы для настройки поведения playbook'ов или задач. Факты включают информацию о системе, такую как операционная система, архитектура, сетевые интерфейсы, доступные диски и многое другое.

Пример использования фактов в Ansible:
1. **Сбор информации о хосте**: Вы можете собрать информацию о системе с помощью модуля `setup`, который возвращает все доступные факты о машине. Эти данные можно использовать для настройки playbook'ов или задач.
    ```yaml
    - name: Gather facts about the host
      hosts: localhost
      gather_facts: yes
      tasks:
        - name: Display all gathered facts
          debug:
            var: ansible_facts
    ```
2. **Использование фактов в задачах**: Вы можете использовать факты для принятия решений в задачах. Например, вы можете проверить операционную систему хоста и настроить задачу только для определенных ОС.
    ```yaml
    - name: Check OS and configure accordingly
      hosts: all
      tasks:
        - name: Install packages for Debian-based systems
          apt:
            name: "{{ item }}"
            state: present
          when: ansible_os_family == "Debian"
          loop:
            - curl
            - vim
    ```
3. **Использование переменных на основе фактов**: Вы можете создавать переменные, которые зависят от фактов о системе. Это удобно для конфигурации приложений в зависимости от среды выполнения.
    ```yaml
    - name: Configure application based on OS type
      hosts: all
      vars:
        app_config: "{{ 'default' if ansible_os_family == 'Windows' else 'advanced' }}"
      tasks:
        - name: Set configuration for Windows
          win_regedit:
            path: HKLM\Software\MyApp\Config
            name: ConfigType
            data: "{{ app_config }}"
          when: ansible_os_family == "Windows"
    ```
4. **Группировка узлов по фактам**: Вы можете использовать факты для группировки хостов в плейбуках. Это позволяет вам применять различные настройки к разным группам хостов.
    ```yaml
    - name: Group hosts by OS type
      hosts: all
      gather_facts: yes
      tasks:
        - name: Print facts for each host
          debug:
            var: ansible_facts
        - name: Create group based on OS family
          add_host:
            hostname: "{{ inventory_hostname }}"
            groups: "{{ ansible_os_family | default('default', True) }}"
    ```

Таким образом, факты в Ansible являются мощным инструментом для сбора и использования информации о конфигурации хостов, что позволяет создавать гибкие и точные playbook'ы.