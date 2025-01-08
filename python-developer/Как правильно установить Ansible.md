### Шанс вопроса: 6%

Для установки Ansible можно использовать различные методы в зависимости от операционной системы. Вот общие шаги для установки Ansible на основных платформах:

1. **Установка через pip (для Linux и macOS):**
   - Убедитесь, что у вас установлен Python 3 и pip:
     ```sh
     sudo apt update
     sudo apt install python3-pip
     ```
   - Установите Ansible с помощью pip:
     ```sh
     pip3 install ansible
     ```

2. **Установка через дистрибутив (для Linux):**
   - Добавьте репозиторий и установите пакет:
     ```sh
     sudo apt update
     sudo apt install software-properties-common
     sudo add-apt-repository --yes --update ppa:ansible/ansible
     sudo apt install ansible
     ```

3. **Установка на macOS:**
   - Установите Homebrew, если он не установлен:
     ```sh
     /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
     ```
   - Установите Ansible с помощью Homebrew:
     ```sh
     brew install ansible
     ```

4. **Установка на Windows:**
   - Скачайте инсталлятор для Windows из официального сайта: [Ansible Releases](https://releases.ansible.com/ansible/)
   - Запустите инсталлятор и следуйте инструкциям по установке.

5. **Проверка установки:**
   - После установки выполните команду для проверки версии Ansible:
     ```sh
     ansible --version
     ```

Эти шаги обеспечат вам базовую установку Ansible на различных операционных системах.