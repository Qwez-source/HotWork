### Шанс вопроса: 6%

Для установки Node.js на виртуальную машину с операционной системой Astra (предполагается, что речь идет о приложении, работающем в облаке) можно воспользоваться несколькими методами. Вот пошаговая инструкция:

1. **Использование NodeSource**:
   - Перейдите на сайт [NodeSource](https://nodesource.com/blog/installing-node-js-via-package-manager/) и выберите версию Node.js, которую хотите установить.
   - Для Ubuntu или Debian используйте команду:
     ```bash
     curl -fsSL https://deb.nodesource.com/setup_14.x | sudo -E bash -
     sudo apt-get install -y nodejs
     ```
   - Для CentOS или Fedora используйте команду:
     ```bash
     curl -sL https://rpm.nodesource.com/setup_14.x | sudo bash -
     sudo yum install -y nodejs
     ```

2. **Использование nvm (Node Version Manager)**:
   - Установите `nvm` с помощью cURL:
     ```bash
     curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
     ```
   - После установки перезагрузите терминал и используйте команду для установки нужной версии Node.js:
     ```bash
     nvm install 14
     ```

3. **Использование Docker**:
   - Создайте файл `Dockerfile` для вашего приложения и укажите нужную версию Node.js в команде `FROM`:
     ```dockerfile
     FROM node:14
     # Добавьте остальные команды для установки зависимостей и запуска приложения
     ```
   - Соберите и запустите Docker-контейнер:
     ```bash
     docker build . -t my-node-app
     docker run -it --rm my-node-app
     ```

4. **Установка через пакетный менеджер дистрибутива**:
   - Для Ubuntu или Debian:
     ```bash
     sudo apt update
     sudo apt install nodejs
     ```
   - Для CentOS или Fedora:
     ```bash
     sudo yum install epel-release
     sudo yum install nodejs
     ```

Выбор метода зависит от ваших предпочтений и специфики задачи. Если у вас есть конкретная задача, например, установка для определенного проекта или использование Docker, выберите соответствующий метод.